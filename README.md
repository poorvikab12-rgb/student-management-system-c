#include <stdio.h>
#include <string.h>

#define MAX 100

struct Student {
    int id;
    char name[50];
    float marks;
};

struct Student s[MAX];
int count = 0;

// ADD STUDENT
void addStudent() {
    printf("\nEnter Student ID: ");
    scanf("%d", &s[count].id);

    printf("Enter Name: ");
    scanf(" %[^\n]", s[count].name);

    printf("Enter Marks: ");
    scanf("%f", &s[count].marks);

    count++;
    printf("Student Added Successfully!\n");
}

// DISPLAY STUDENTS
void displayStudents() {
    if (count == 0) {
        printf("\nNo Records Found!\n");
        return;
    }

    printf("\n--- Student List ---\n");
    for (int i = 0; i < count; i++) {
        printf("ID: %d | Name: %s | Marks: %.2f\n",
               s[i].id, s[i].name, s[i].marks);
    }
}

// UPDATE STUDENT
void updateStudent() {
    int id, found = 0;

    printf("\nEnter ID to Update: ");
    scanf("%d", &id);

    for (int i = 0; i < count; i++) {
        if (s[i].id == id) {
            printf("Enter New Name: ");
            scanf(" %[^\n]", s[i].name);

            printf("Enter New Marks: ");
            scanf("%f", &s[i].marks);

            printf("Student Updated Successfully!\n");
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("Student Not Found!\n");
    }
}

// DELETE STUDENT
void deleteStudent() {
    int id, found = 0;

    printf("\nEnter ID to Delete: ");
    scanf("%d", &id);

    for (int i = 0; i < count; i++) {
        if (s[i].id == id) {
            for (int j = i; j < count - 1; j++) {
                s[j] = s[j + 1];
            }
            count--;
            printf("Student Deleted Successfully!\n");
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("Student Not Found!\n");
    }
}

// MAIN MENU
int main() {
    int choice;

    while (1) {
        printf("\n===== Student Management System =====\n");
        printf("1. Add Student\n");
        printf("2. Display Students\n");
        printf("3. Update Student\n");
        printf("4. Delete Student\n");
        printf("5. Exit\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: addStudent(); break;
            case 2: displayStudents(); break;
            case 3: updateStudent(); break;
            case 4: deleteStudent(); break;
            case 5: printf("Exiting...\n"); return 0;
            default: printf("Invalid Choice!\n");
        }
    }

    return 0;
}

