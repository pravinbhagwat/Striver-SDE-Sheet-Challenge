import java.util.* ;
import java.io.*; 
public class Solution {
    // 1st Approach (m*n)+(m+n)
    public static void firstApproch(int matrix[][]){
        int r = matrix.length;
        int c = matrix[0].length;
        for(int i = 0; i < r; i++){
            for(int j = 0; j < c; j++){
                if(matrix[i][j] == 0){
                    for(int idx = 0; idx < c; idx++){
                        if(matrix[i][idx] != 0){
                            matrix[i][idx] = -1;
                        }
                    }
                    for(int idx = 0; idx < r; idx++){
                        if(matrix[idx][j] != 0){
                            matrix[idx][j] = -1;
                        }
                    }
                }
            }
        }
        
        for(int i = 0; i < r; i++){
            for(int j = 0; j < c; j++){
                if(matrix[i][j] == -1){
                    matrix[i][j] = 0;
                }
            }
        }
    }
    
    // Second Approach
    public static void secondApproach(int matrix[][]) {
        int r = matrix.length;
        int c = matrix[0].length;
        int[] row = new int[r];
        int[] col = new int[c];
        
        for(int i = 0; i < r; i++){
            for(int j = 0; j < c; j++){
                if(matrix[i][j] == 0) {
                    row[i] = 1;
                    col[j] = 1;
                }        
            }
        }
        
        for(int i = 0; i < r; i++){       
            for(int j = 0; j < c; j++){
                if((row[i]==1) || (col[j] == 1)) {
                    matrix[i][j] = 0; 
                }        
            }
        }
    }
    
    // Third Approach O(m*n) space - O(1)
    public static void thirdApproach(int matrix[][]){
        int r = matrix.length;
        int c = matrix[0].length;
        int[] row = new int[r];
        int[] col = new int[c];
        int column0  = 1;
        
        for(int i = 0; i < r; i++){
            if(matrix[i][0] == 0) column0 = 0;
            for(int j = 1; j < c; j++){
                if(matrix[i][j] == 0) {
                    matrix[i][0] = matrix[0][j] = 0;
                }        
            }
        }
        
        for(int i = r - 1; i >= 0; i--){       
            for(int j = c - 1; j > 0; j--){
                if((matrix[i][0] == 0) || (matrix[0][j] == 0)) {
                    matrix[i][j] = 0; 
                }        
            }
            if(column0 == 0){
                matrix[i][0] = 0;
            }
        }
    }
    
    public static void setZeros(int matrix[][]) {
        //firstApproch(matrix);
       //secondApproach(matrix);
        thirdApproach(matrix);
       
        
    }

}