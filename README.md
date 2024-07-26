# organizing-music-concert-
Hacckerearth code
you are organizing music concert and want to arrange performers on stage on visually appeling manner 
to acheive this each performar will be represented by a distint integer and you want to ensure the positioning 
of the performers on stage. to do this, you have list of performers in the order of their appearance .
the list is already asscending order based on based on their popularity,however you need to rearrange 
the performers in such way that when they are appear on stage one after the other
their popularity alternates between high and low.
 
 for example ,suppose you have sorted list of performers [1,2,3,4,5,6,7] and desired arrangement would be [2,1,4,3,6,5,7]
 where each element at an even index is greater than its adjuscent element at odd indices.
 
 sample input: 
 5
 1 2 3 4 5 
 
 sample output:
 2 1 4 3 5 



 import java.util.*;

public class ConcertArrangement {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Read the number of performers
        int n = sc.nextInt();
        
        // Read the popularity list of performers
        int[] performers = new int[n];
        for (int i = 0; i < n; i++) {
            performers[i] = sc.nextInt();
        }
        
        // Create result array
        int[] result = new int[n];
        
        // Split performers into two halves
        int mid = n / 2;
        int[] smallerHalf = Arrays.copyOfRange(performers, 0, mid);
        int[] largerHalf = Arrays.copyOfRange(performers, mid, n);
        
        // Interleave them such that each element at an even index is greater than its adjacent odd index
        int left = 0, right = 0;
        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) {
                result[i] = largerHalf[right++];
            } else {
                result[i] = smallerHalf[left++];
            }
        }
        
        // Output the result
        for (int i = 0; i < n; i++) {
            System.out.print(result[i] + " ");
        }
    }
}
