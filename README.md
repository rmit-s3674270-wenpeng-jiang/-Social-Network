# -Social-Network
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.Scanner;

public class MiniNet {
	public static void main(String[] args) {
		   
		Scanner sc = new Scanner(System.in);
		int input = 0;
		do {
			System.out.println(" ");
			System.out.println("MiniNet Menu");
			System.out.println("=================================");
			System.out.println("1. List everyone");
			System.out.println("2. Add a person");
			System.out.println("3. Select a person");
			System.out.println("4. Are these two friends?");
			System.out.println("5. Exit");
			
			input = sc.nextInt();
			
			if (input == 1) {
				display(Person.profile);
			}
			
			else if (input == 2) {
				Person.addperson();
			}
		
			else if (input == 3) {
				select(Person.profile);
				int selection;
				Scanner sc2 = new Scanner(System.in);
				selection = sc2.nextInt();
				
				
				do {
				System.out.println("1. Update the profile of the selected person");
				System.out.println("2. Delete selected person");
				System.out.println("3. Display the profile of selected person");
				System.out.println("4. Add friends ");
				System.out.println("5. Show friends list");
				System.out.println("6. Add family members");
				System.out.println("7. Show family list");

				
				int choice;
				choice = sc2.nextInt();
				if (choice == 1) {
					Person.profile.remove(selection-1);
					Person.addperson();
					}
				
				else if (choice == 2) {
					Person.profile.remove(selection-1);
					System.out.println("The person has been successfully deleted");
					}
				else if (choice == 3) {
					System.out.println(Person.profile.get(selection-1));
				}
				else if (choice == 4) {
					if(Person.profile.get(selection-1) instanceof Teenager) {
						Teenager.addfriends();
						}
					
					if(Person.profile.get(selection-1) instanceof Adults) {
						Adults.addfriends();
						}
					
					if(Person.profile.get(selection-1) instanceof Baby) {
						System.out.println("You cannot add friends");
						}
					}
				else if (choice == 5) {
					if(Person.profile.get(selection-1) instanceof Teenager) {
						display(Teenager.friend);
						}
				
					if(Person.profile.get(selection-1) instanceof Adults) {
							display(Adults.friend);
						}
				
					if(Person.profile.get(selection-1) instanceof Baby) {
						System.out.println("You cannot add friends");
						}	
					}
				else if (choice == 6) {
					if(Person.profile.get(selection-1) instanceof Teenager) {
						Teenager.addfamily();
						}
			
					if(Person.profile.get(selection-1) instanceof Adults) {
						Adults.addfamily();
						}
			
					if(Person.profile.get(selection-1) instanceof Baby) {
						Baby.addfamily();
						}
					}
				else if (choice == 7) {
					if(Person.profile.get(selection-1) instanceof Teenager) {
						display(Teenager.family);	
						}
			
					if(Person.profile.get(selection-1) instanceof Adults) {
						display(Adults.family);
						}
			
					if(Person.profile.get(selection-1) instanceof Baby) {
						display(Baby.family);
						}
					}
				}while(input != 1 && input != 2 && input !=3 && input != 4 && input !=5 && input != 6 && input != 7);
			}

			else if (input == 5) {
				
			}
			
			else if (input != 1 && input != 2 && input !=3 && input != 4 && input != 0) {
				System.out.println("Invalid option");
			} 
		} while(input != 0);
	
}


	public static void display(List list) {
		for (Iterator it = list.iterator(); it.hasNext();) {
			Person p = (Person)it.next();	
			System.out.println(p);
		}
	}

	public static void select(List list) {
		for (int i = 0; i < list.size(); i++) {
			System.out.println(i + 1 +"-------------" + list.get(i));
		}
	}

}

