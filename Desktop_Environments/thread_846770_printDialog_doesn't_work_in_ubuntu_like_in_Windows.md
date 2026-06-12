---
title: "printDialog doesn't work in ubuntu like in Windows"
date: 2008-07-01
forum: Desktop Environments
---

### Post by hill0093 on 2008-07-01
A java program I commonly use in windows gives error when run in ubuntu linux,
so I extracted a demonstration program from it that gives the same kind of error.
Sun used to say that java is “write once, run anywhere”. 
PROGRAM CODE:

[HTML]//################### Test show of printDialog only ############ 
import java.awt.print.PrinterJob; 
public class Test { 
  Test test; 
  public static void main(String[]args) { 
    Test test=new Test(); test.test=test; test.main2(); //escape static 
  } 
  protected void main2() { //escapes static 
    PrinterJob prJ;
    prJ=PrinterJob.getPrinterJob();
    System.out.println("------------------LOOK FOR & CLICK PRINT DIALOG");
    if(prJ.printDialog()) { //Doesn't show window in Linux, but does in Windows 
    } 
  } 
}
[/HTML]
I.e., the print dialog doesn’t work on any of my programs.
It is perhaps an install problem for ubuntu linux.
Try it and tell me if it works.
What is wrong and how do I fix it?

---

