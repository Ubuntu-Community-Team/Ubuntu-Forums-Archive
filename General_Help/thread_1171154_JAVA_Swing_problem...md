---
title: "JAVA Swing problem.."
date: 2009-05-27
forum: General Help
---

### Post by arapollo on 2009-05-27
I cannot close JFrames in Java. I alway have to force quit. I have been trying to debug this simple procedure for about an hour. Here is the source.
> package crawler;
/*
 * This is the GUI for the web crawler.
 */
import javax.swing.*;
import java.awt.*;

public class GUI extends JFrame {
	
	public GUI(){
		super("Brown University Crawler"); //Sets the title of the GUI.
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		this.setSize(400,300);
		
		JButton close = new JButton("Close");
		this.add(close);
		this.setVisible(true);
	}


}

The program is opened up in a Main class like so:
> package crawler;
/*
 * This is the main class. The function of this class is put everything together.
 */
public class Main {
	 
	public static void main(String args[]){
		GUI gui = new GUI();
				
	}

}

I found some literature about this problem from an older post:
[http://ubuntuforums.org/showthread.php?t=889719](http://ubuntuforums.org/showthread.php?t=889719)

Does anyone know if there is a fix or if I am just a terrible terrible terrible programmer? Thanks.

---

