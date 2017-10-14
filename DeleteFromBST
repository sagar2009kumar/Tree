import java.io.*;
import java.util.*;

/********************************************************************************************************
*																										*
*									Deletion from the binary Tree										*
*																										*
********************************************************************************************************/

public class TreeDel {
	
	public static void main(String args[]) throws IOException {
		
		// Hope so it does not contain any bug.. 
		// if found i would be pleased
		// Just make it yourself.. you will learn
		
		int arr[] = {10, 11, 13, 6, 3, 2, 8, 7, 9};
		
		Node root = null;
		
		// making the BST from the array..
		for (int i = 0; i < arr.length; i++) {
			root = makeBST(root, arr[i]);
		}
		// you can print the preOrder traversal of the tree uncomment
		// preOrder(root);
		
		// you can try all the deletion one by one.. just see the structure
		// all are of different type  uncomment for action one by one
		// root = delete(root, 2|9, false) // leaf node
		// root = delete(root, 3, false) // delete the left child
		// root = delete(root, 11, false) // delete the right child
		// root = delete(root, 6, false) // delete the node having both child
		// root = delete(root, 10, false);
		preOrder(root);
	}
	
	static class Node {
		int data;
		Node left;
		Node right;
		Node parent;
		Node(int d) {
			this.data = d;
			left = null;
			right = null;
			parent = null;
		}
		
	}
	
	static Node makeBST(Node root, int datum) {
		
		if(root == null) {
			// making of the first node
			root = new Node(datum);
			return root;
		}
		
		Node temp = root, prevTemp = null;
		
		while(temp!=null) {
			prevTemp = temp;
			
			if(temp.data == datum) {
				// No need to insert the element into the binary tree
				// It is already present
				return root;
			}else if(temp.data < datum) {
				// If the data to be inserted is less than the Node data
				// move to the left
				temp = temp.right;
			}else {
				// If the data to be inserted is greater than Node data
				// move to the right
				temp = temp.left;
			}
		}
		
		if(prevTemp.data < datum) {
			// If the right child is to be inserted
			prevTemp.right = new Node(datum);
			prevTemp.right.parent = prevTemp;
		}else {
			// If the left child is to be inserted
			prevTemp.left = new Node(datum);
			prevTemp.left.parent = prevTemp;
		}
		
		return root;
	}
	
	static void preOrder(Node temp) {
		if(temp==null) {
			return ;
		}
		System.out.print(temp.data+" ");
		preOrder(temp.left);
		preOrder(temp.right);
		System.out.println();
	}
	
	static Node search(Node root, int datum) {
		Node temp = root;
		while(temp!=null) {
			if(temp.data == datum) {
				return temp;
			}else if(temp.data < datum) {
				temp = temp.right;
			}else {
				temp = temp.left;
			}
		}
		
		return temp;
	}
	
	static Node inorderSuccessor(Node head) {
		Node prevTemp = null;
		while(head!= null) {
			prevTemp = head;
			head = head.left;
		}
		return prevTemp;
	}
	
	static Node delete(Node root, int datum, boolean isRecur) {
		
		Node temp;
		if(!isRecur) 
			temp = search(root, datum);
		else
			temp = root;
			
		
		if(temp== null) {
			System.out.println("Nothing to be deleted data not found");
			return root;
		} else if(temp.left == null && temp.right==null) {
			// the node to be deleted is a leaf node
			// check whether it is the right child or left child
			if(temp.parent == null) {
				// It is the only root in the tree then delete it.
				return null;
			}else if(temp.parent.left != null && temp.parent.left.data == datum) {
				temp.parent.left =  null;
			}else if (temp.parent.right!= null && temp.parent.right.data == datum) {
				temp.parent.right = null;
			}
		} else if (temp.left == null && temp.right != null) {
			// the node to be deleted has the right child but not left child
			// you can play smartly here just copy the node in the upper node
			// and delete its child
			temp.data = temp.right.data;
			temp.right = null;
		} else if (temp.left!= null && temp.right == null) {
			// the node to be deleted has only the left child 
			// you can play same as above 
			temp.data = temp.left.data;
			temp.left = null;
		}else if (temp.left!= null && temp.right!= null) {
			// getting the inorder successor on the right child 
			// and then recur on the node to delete
			Node temp2 = inorderSuccessor(temp.right);
			temp.data = temp2.data;
			delete(temp2, temp.data, true);
		}
		
		return root;
		
	}
	
}
