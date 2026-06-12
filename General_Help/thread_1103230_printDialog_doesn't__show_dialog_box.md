---
title: "printDialog doesn't  show dialog box"
date: 2009-03-22
forum: General Help
---

### Post by hill0093 on 2009-03-22
I have not yet been successful enough on 
Ubuntu to convert to it, but I want to try again 
since Ubuntu 64bit takes only about 2/3 as 
long as the Vista 32bit, available to me, 
to run a plot program under the exact same 
screen size of 1280x1024. A 64bit Vista is not 
available to me without risking a lot of money. 

I have an ASUS M3A78EM mainboard, 
AMD940X4 64bit processor, 4GB memory, 
Hanns-G JW199D 1440x900 lcd monitor w/weak spkrs.
Vista 32bit ultimate on slave IDE, 
press f8 to choose boot, DVD on SATA, 
Ubuntu 8.04.2 64bit 2.6.24-23 on master IDE. 
I installed Ubuntu connected to the Ethernet 
internet cable, and after installation I 
allowed it to install about 50 
updates from the internet.
Ethernet Internet worked on both Vista and 
Ubuntu immediately upon system installation. 
The 1440x900 screen is not automatically used
by either system, but Vista gives that option.
Ubuntu does not show the 1440x900 option, the
closest being 1280x1024 and 1152x864.

On Ubuntu, I then changed the 
Synaptic Package Manager settings: adding 
Preferences: recommended packages as dependencies, 
and Repositories: ubuntu hardy partner,
and Repositories: ubuntu 8.04.2 cdrom.
I clicked reload and installed 
vlc and sun.java6.jdk, and reinstalled hplip.
On Vista I downloaded an .exe of java6, 
clicked it and it installed.

I installed on each system the HP4350n printer 
that resides on the local Ethernet network. 
Ubuntu: System>Printing> . . . . . . . . .
Vista: ControlPanel>Printer>addprinter>network>IPaddress.
It works on both Vista’s Word and Ubuntu’s Writer 
immediately without further install.

So Sun Java 6 installs and runs on both Ubuntu and Vista.
But I made a test folder of my Java plotting program 
and data. It runs on Java 6 in both Vista and Ubuntu. 
However, the very same program prints 
from Vista but does not print from Ubuntu. 
Is the java6 under ubuntu different from the 
downloaded jdk-6u12-windows-i586-p.exe version?

I extracted the following test code:
//####TestPDia show of printDialog only ####
import java.awt.print.PrinterJob; 
public class TestPDia { 
  TestPDia testPDia; 
  public static void main(String[]args) { 
    TestPDia testPDia=new TestPDia(); 
    testPDia.testPDia=testPDia; 
    testPDia.main2(); //escape static 
  } 
  protected void main2() { //escapes static 
    PrinterJob prJ;
    prJ=PrinterJob.getPrinterJob();
    System.out.println("LOOK FOR & CLICK PRINT DIALOG");
    if(prJ.printDialog()) { 
      //Doesn't show window in Ubuntu, 
      //but it does show in Windows 
    } System.out.println("after printDialog"); 
  } 
} 
On Ubuntu it errors with the following output:
LOOK FOR & CLICK PRINT DIALOG
Exception in thread "main" java.lang.NullPointerException: null attribute
at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
at sun.print.RasterPrinterJob.printDialog(RasterPrinterJob.java:856)
at sun.print.PSPrinterJob.printDialog(PSPrinterJob.java:421)
at TestPDia.main2(TestPDia.java:14)
at TestPDia.main(TestPDia.java:8)
But runs correctly on Vista as follows:
LOOK FOR & CLICK PRINT DIALOG
after printDialog

I think I had the same trouble when I tried 
about a year ago and I think it was due to 
a sun error and I thought it was resolved, 
so I am surprised.

DVDs play on Vista with no further adjustment
(but not on previous XP & Vista versions I used)
but Ubuntu’s movie player has you search for codecs, 
then after you install, it still encounters an error.
Ubuntu’s installed vlc allows opening the disk, 
but then when OK is clicked most everything 
goes away without playing the DVD.

My immediate problems on Ubuntu 8.04.2 x64 are 
1) Java doesn’t bring up the print dialog
2) cannot play DVD movies on vlc or totem
3) 1440x900 screen size is not a choice.
I need to resolve each of these problems so 
that I can use ubuntu. Can someone help me?

---

### Post by hill0093 on 2009-03-22
I rediscovered the work-around.
Set page orientation manually in Menu: System -> Administration -> Printing, Choose correct printer, Job Options tab, Change Orientation to one of the others, e.g., “Portrait (no rotation)”, Apply. (“Automatic rotation” doesn’t work) See: [https://bugs.launchpad.net/ubuntu/+source/](https://bugs.launchpad.net/ubuntu/+source/)
sun-java6/+bug/156191/comments/18

I still have the remaining two problems:
2) cannot play DVD movies on vlc or totem
3) 1440x900 screen size is not a choice.

---

