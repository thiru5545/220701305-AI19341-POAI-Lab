# 220701306-AI19341-POAI-Lab-



def dfs_solution(jug1, jug2, target):
    visited = set()  # To keep track of visited states
    stack = [(0, 0)]  # Start with both jugs empty

    while stack:
        x, y = stack.pop()  # Current state: x liters in Jug 1, y liters in Jug 2

        if (x, y) in visited:
            continue
        visited.add((x, y))

        # If we reach the target amount in either jug, return the solution
        if x == target or y == target:
            return f"Solution: Jug 1: {x}, Jug 2: {y}"

        # Generate all possible states
        next_states = [
            (jug1, y),             # Fill Jug 1
            (x, jug2),             # Fill Jug 2
            (0, y),                # Empty Jug 1
            (x, 0),                # Empty Jug 2
            (max(0, x + y - jug2), min(jug2, x + y)),  # Pour Jug 1 -> Jug 2
            (min(jug1, x + y), max(0, x + y - jug1))   # Pour Jug 2 -> Jug 1
        ]

        for next_state in next_states:
            if next_state not in visited:
                stack.append(next_state)

    return "No solution."

# Input from user
jug1 = int(input("Enter capacity of Jug 1: "))
jug2 = int(input("Enter capacity of Jug 2: "))
target = int(input("Enter target amount: "))

# Call the function and print the result
print(dfs_solution(jug1, jug2, target))



from collections import defaultdict

# jug1 and jug2 contain the value for max capacity in respective jugs 
# and aim is the amount of water to be measured. 
jug1, jug2, aim = 4, 3, 2

# Initialize dictionary with default value as false.
visited = defaultdict(lambda: False)

# Recursive function which prints the intermediate steps to reach 
# the final solution and returns boolean value (True if solution is 
# possible, otherwise False). amt1 and amt2 are the amount of water 
# present in both jugs at a certain point of time.
def waterJugSolver(amt1, amt2): 

    # Checks for our goal and returns true if achieved.
    if (amt1 == aim and amt2 == 0) or (amt2 == aim and amt1 == 0):
        print(amt1, amt2)
        return True
    
    # Checks if we have already visited the combination or not.
    # If not, then it proceeds further.
    if visited[(amt1, amt2)] == False:
        print(amt1, amt2)
    
        # Marks the combination as visited.
        visited[(amt1, amt2)] = True
    
        # Check for all the 6 possibilities and 
        # see if a solution is found in any one of them.
        return (waterJugSolver(0, amt2) or
                waterJugSolver(amt1, 0) or
                waterJugSolver(jug1, amt2) or
                waterJugSolver(amt1, jug2) or
                waterJugSolver(amt1 + min(amt2, (jug1 - amt1)),
                               amt2 - min(amt2, (jug1 - amt1))) or
                waterJugSolver(amt1 - min(amt1, (jug2 - amt2)),
                               amt2 + min(amt1, (jug2 - amt2))))
    
    # Return False if the combination is already visited to avoid repetition.
    else:
        return False

print("Path from initial state to solution state:")

# Call the function and pass the initial state (0, 0) as both jugs are empty initially.
result = waterJugSolver(0, 0)

# If the result is True, print that the solution is possible; otherwise, it's not.
if result:
    print("Solution is possible!")
else:
    print("No solution exists!")





    from sklearn import tree 
#Using DecisionTree classifier for prediction 
clf = tree.DecisionTreeClassifier() 

#Here the array contains three values which are height,weight and shoe size 
X = [[181, 80, 91], [182, 90, 92], [183, 100, 92], [184, 200, 93], [185, 300, 94], [186, 400, 95], [187, 500, 96], [189, 600, 97], [190, 700, 98], [191, 800, 99], [192, 900, 100], [193, 1000, 101]] 
Y = ['male', 'male', 'female', 'male' , 'female', 'male', 'female' , 'male' , 'female', 'male' , 'female' , 'male' ] 
clf = clf.fit(X, Y) 

#Predicting on basis of given random values for each given feature 
predictionf = clf.predict([[181, 80, 91]])
predictionm = clf.predict([[183, 100, 92]])

#Printing final prediction 
print(predictionf)
print(predictionm)














                        g[m] = g[n] + weight
                else:
                        if g[m] > g[n] +  weight:
                            g[m] = g[n] + weight
                            parents[m]=n
                            
                            if m in closed_set:
                                closed_set.remove(m)
                                open_set.add(m)
        if n==None:
            print("path does not exist!")
            return None
                
        if n==stop_node:
            path=[]
                    
            while parents[n]!=n:
                path.append(n)
                n=parents[n]
                        
            path.append(start_node)
                    
            path.reverse()
                    
            print("Path found: {}".format(path))
            return path
                
                
        open_set.remove(n)
        closed_set.add(n)
    print("Path does not exist!")
    return None

        
def get_neighbors(v):
    if v in Graph_nodes:
        return Graph_nodes[v]
    
    else:
        return None
    
def heuristic(n):
    H_dist = {
        'A' : 11,
        'B' : 6,
        'C' : 99,
        'D' : 1,
        'E' : 7,
        'G' : 0,
    }  
    return H_dist[n]


Graph_nodes = {
    'A' : [('B',2),('E',3)],
    'B' : [('C',1),('G',9)],
    'C' : None,
    'E' : [('D',6)],
    'D' : [('G',1)],
}
astaralgo('A','G')









