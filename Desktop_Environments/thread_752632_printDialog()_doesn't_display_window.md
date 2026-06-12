---
title: "printDialog() doesn't display window"
date: 2008-04-11
forum: Desktop Environments
---

### Post by hill0093 on 2008-04-11
I am a beggar asking that someone with linux and Sun's 
standard java try to compile and run this standalone program.

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
    } //pause("after printDialog"); 
  } 
}

javac Test.java
java Test
My installed ubuntu prints from OpenOffice.org 2.3
but the java Test produces 
------------------LOOK FOR & CLICK PRINT DIALOG
Exception in thread "main" java.lang.NullPointerException: null attribute
at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
at sun.print.RasterPrinterJob.printDialog(RasterPrinterJob.java:855)
at sun.print.PSPrinterJob.printDialog(PSPrinterJob.java:421)
at Test.main2(Test.java:12)
at Test.main(Test.java:6)

but on windows it displays the printDialog window.
I thought java was a "write once, run anywhere".
If I can solve this, it looks like I have a 
couple of other computers for data analysis. 

No one on the java programming forum answered this question.

---

### Post by trippinnik on 2008-04-11
In the Sun Java tutorial it recommends initializing the Desktop class: [http://www.google.com/search?q=java+tutorials+desktop+class+printing&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=java+tutorials+desktop+class+printing&ie=UTF-8&oe=UTF-8)
This is a problem if you want to print when running older versions of Java, but for 1.6 and maybe 1.5 it's no problem.

---

### Post by hill0093 on 2008-04-11
Thanks very much for the hope.
I looked at the link and it frightens me.
Out of that tutorial,
could you suggest some simple code that 
would make it work like it does in windows?
Or is it really as complicated as it looks?
I don't think I can do it.
The code should work in Windows also.
I wonder why no one solved this for 
me in the java.Sun forum.
In the if braces, I just have a try prj.print() with a catch.

---

### Post by trippinnik on 2008-04-12
Just tried it again.  The program I had written using the Desktop class isn't working and also the sun example code isn't working.  I'm getting the NullPointerException.  I'm really not sure what's going on with this, but it was working a few months ago last time I was working on that project.  
I tried with a few different versions of Java (OpenJDK 1.6, sun 1.6, and gcj 1.5).  
Not sure what's up with this.  Maybe I'll file a bug report, I just tested it on my laptop.  I don't have a printer but it does what it's supposed to and reports no printing service found. But that's on Debian 4.  I'm running the Hardy Beta right now.  Which Ubuntu are you using?

---

### Post by hill0093 on 2008-04-13
I installed ubuntu-7.10-desktop-amd64.iso and
I accepted all updates it offered me so far.
For my case, it seems that if something so 
simple works on windows, it shouldn't take 
much, if anything, to make it work on ubuntu.
Is it a sun problem, or is it an ubuntu problem?
Obviously, it is my problem.

---

### Post by trippinnik on 2008-04-19
I've found a better part of the tutorial now: [http://java.sun.com/docs/books/tutorial/2d/printing/index.html](http://java.sun.com/docs/books/tutorial/2d/printing/index.html)

I'm working on adding printing to my java program now too.  Adapting their example I've been able to get printing to work (I'm running the app in java 1.4 since the computers I am deploying on are only 1.4).  This method seems to work pretty well.
I really recommend downloading the whole tutorial it's quite good and has lots of example programs too.

---

### Post by hill0093 on 2008-07-01
I wanted to try it again.I installed ubuntu 8.04 64-bit, and it gives the same problem with the same program.
Thanks for all the help, but I am too dumb to understand it.
Works on Windows, not on Ubuntu.
I really would appreciate someone fixing it so I can print my BufferedImage from ubuntu, not just Windows.

---

