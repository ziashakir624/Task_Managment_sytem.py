tasks = []

def add_task():
    task_name = input("Enter task name: ")
    task_priority = input("Enter task priority (High, Medium, Low): ")
    task_status = "Not Done"
    due_date = input("Enter task due date (YYYY-MM-DD): ")
    task = (task_name, task_priority, task_status, due_date)
    tasks.append(task)
    print(f"Task '{task[0]}' has been added.")

def list_task():
    if not tasks:
        print("Task list is empty.")
    else:
        print("Current Tasks: ")
        for i, task in enumerate(tasks, start=1):
            print(f"{i}. Name: {task[0]} (Priority: {task[1]}, Status: {task[2]}, due_date: {task[3]})")

def mark_task_complete():
    if not tasks:
        print("Task list is empty.")
    else:
        task_status = int(input("Enter the task number to mark as completed: "))
        if 1 <= task_status <= len(tasks):
            tasks[task_status - 1] = (tasks[task_status - 1][0], tasks[task_status - 1][1], "Done", tasks[task_status - 1][3])
            print(f"Task '{tasks[task_status - 1][0]}' has been marked as completed.")
        else:
            print("Invalid task number.")

def delete_task():
    task_name = input("Enter task name to delete: ")
    updated_tasks = []
    task_found = False
    for task in tasks:
        if task[0] == task_name:
            print(f"Task '{task_name}' has been deleted.")
            task_found = True
        else:
            updated_tasks.append(task)
    if not task_found:
        print(f"{task_name} not found in the list.")
    tasks[:] = updated_tasks

def quit_task():
    print("Thanks for using our task management app.")
    exit()

while True:
    print("Task Management Menu: ")
    print("1. Add Task")
    print("2. List Tasks")
    print("3. Mark Task as Completed")
    print("4. Delete Task")
    print("5. Quit")

    choice = input("Enter your choice: ")

    if choice == '1':
        add_task()
    elif choice == '2':
        list_task()
    elif choice == '3':
        mark_task_complete()
    elif choice == '4':
        delete_task()
    elif choice == '5':
        quit_task()
    else:
        print("Invalid input. Please choose from the given options.")
