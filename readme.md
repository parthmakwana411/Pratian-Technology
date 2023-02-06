import java.util.Scanner;
public class Main {

	public static void main(String[] args) {
	Scanner sc = new Scanner(System.in);
	
     System.out.print("Enter the string to encrypt: ");
     String text = sc.nextLine();
     sc.close();

     String[] words = text.split(" ");
     int[] encrypted = new int[text.length()];
     
     int k = 0;
     for (String word : words) {
         int wordLength = word.length();
         int increment = wordLength * 100;
         for (int i = 0; i < wordLength; i++) {
             char c = word.charAt(i);
             int code = 0;
             if (c == '.') {
                 code = 99;
             } else if (c == '\'') {
                 code = 0;
             } else if (Character.isLowerCase(c)) {
                 code = c - 96;
             } else if (Character.isUpperCase(c)) {
                 code = c - 38;
             }
             encrypted[k++] = code + increment;
         }
     }

     int sumBeforeIncrement = 0;
     for (int i : encrypted) {
         sumBeforeIncrement += i;
     }

     System.out.println("Encrypted string after increment: " + printArray(encrypted));
     System.out.println("Sum of encrypted digits after increment: " + sumBeforeIncrement);
 }

 private static String printArray(int[] arr) {
     StringBuilder sb = new StringBuilder();
     for (int i : arr) {
         sb.append(i).append(" ");
     }
     return sb.toString().trim();
	}
}

