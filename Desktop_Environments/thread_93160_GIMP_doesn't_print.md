---
title: "GIMP doesn't print"
date: 2005-11-21
forum: Desktop Environments
---

### Post by Alex99 on 2005-11-21
When I print from the GIMP, I receive a lot of empty pages with just one line of random characters. Sometimes this line says "Creator: Print plug-in V4.2 for GIMP/Gimp-Print". I tried printing images with "Eye of GNOME", but either the prints were way too big or the results were the same as with GIMP. Creating a pdf with Eye of GNOME and then printing it doesn't work either.
My printer is an HPLaserJet 5L
plus: in GIMP the images appear way too big, although the absolute measurements as shown for the mouse-pointer are alright (when displayed as a 100%, a DIN A 6 / 104.99X148.51 mm / 4.133X5.847 inches is bigger than my 17" monitor).
I appreciate your help!

---

### Post by piecom on 2005-11-22
I have exactly the same problem with a Samsung CLP 550 postscript printer. Prints like a charme from all other applications including Openoffice.org Versions 1.1.x and 2. I tried in principle to follow the howto concerning the canon IP 1000 printer. But that doesnt work. Maybe this is related with an open bug concerning correct recognition/wrapping of CUPS ppd's within gimp-print 4.2.7? Is there any workaround. I could print the fotos from Openoffice but the quality of gimp-print is what I desire and dont want to miss.

Thank you in advance for any hint.

---

### Post by martinbriscoe on 2005-11-26
Wierd
Have the same problem with epson rx500.  Works well printing from open office. But just get garbage when try and print from GIMP. If we get the same problem with 3 different printers doesnt it suggest that problem isnt printer specific? 

So is it something to do with GIMP?

Anybody printing ok using gimp and my printer?

Martin
v5.10

---

### Post by sb73542 on 2005-11-26
GIMP has its own printer drivers.  If you happen to be lucky and have a supported printer, you will get excellent print quality.  Otherwise, save your pictures to disk and then print them from another program.

---

### Post by martinbriscoe on 2005-11-27
>>>>>
GIMP has its own printer drivers. If you happen to be lucky and have a supported printer, you will get excellent print quality
<<<<<

Thanks, gimprint (4.2.7 = the one that ships with ubuntu 5.10) has a driver for my epson rx500 printer and I am using it but it still prints garbage. In suse 10, Gimp does indeed print with very good quality on the same printer. but no luck so far with ubuntu.

In another forum I have seen that gimp print 5.0 is better. I have downloaded it, but I dont understand enough about linux to get it installed on my machine, if anyone finds this version better - let me know.

Martin

---

### Post by piecom on 2005-11-29
I installed the all the gutenprint-Packages from the Debian unstable distribution and printing from within GIMP works like a charme with Samsung CLP-550 PS and gutenprint driver 'Postscript 2' as well as with Epson Stylus Photo R200 and gutenprint driver 'Epson Stylus Photo R200', so all problems were obviously related to buggy 4.2.7-10 version of gimp-print!

by the way gutenprint (5.x) can be installed parallel to gimp-print 4.2.7-10.

Hope this helps others with the same problems as well.

---

### Post by Biased turkey on 2005-11-29
I had the same problem with  a Samsung ML-1740 printer. I could print from any application except from Gimp.
When printing a Gimp document, You can edit the command line sent to the printer.
After various trials I could have gimp documents printed if I changed the last parameter of the command line to "-ijs".
I'm at work and I'll post later the exact command to edit.

From Linuxprinting.org:
The GIMP uses the Gimp-Print plug-in to print. If it is installed you can click into the window with your image using the right mouse button and then choose "File" and "Print". In the printing dialog choose your printer queue (if it is not listed, click "New Printer ..." to create a list entry) and click on "Setup Printer ...". If your printer is listed, it is supported by Gimp-Print and you do not need a PPD file for using it with GIMP. If it is not listed, choose "PostScript Level 2". Then an input field for a PPD file will appear. Enter the path and name under which you have saved your PPD file or choose it with the "Browse" button. Adapt the printing command to your spooler, especially remove the "-oraw" option, because it is important that print jobs for non-PostScript printers are going through the filters of the print queue. After closing the dialog with "OK" the fields for the options ("Media Size", "Media Source", ...) will contain the choices according to your printer. Click "Save Settings" to make your setup permanent.

So it looks like the culprit is the "-oraw"

---

### Post by buldir on 2005-11-29
My post (second one) in [http://ubuntuforums.org/showthread.php?t=62011]("http://ubuntuforums.org/showthread.php?t=62011") may help.

---

### Post by martinbriscoe on 2005-11-29
[QUOTE=buldir]My post (second one) in [http://ubuntuforums.org/showthread.php?t=62011]("http://ubuntuforums.org/showthread.php?t=62011") may help.[/QUOTE]

Many thanks buldir your suggestion has worked - I have no idea why?
I was just about to throw in the towel so thanks very much.

Downloading gimp print 5 sounds like it might also be a solution I tried this but I dont think I have grasped the way to do this. 

Martin

---

### Post by buldir on 2005-11-30
I'm glad I could help, martinbriscoe! I have reached for the towel many times.

---

### Post by piecom on 2005-12-05
[QUOTE=Biased turkey]...

So it looks like the culprit is the "-oraw"[/QUOTE]

That didn't help in my case!

---

### Post by piecom on 2005-12-05
[QUOTE=buldir]My post (second one) in [http://ubuntuforums.org/showthread.php?t=62011]("http://ubuntuforums.org/showthread.php?t=62011") may help.[/QUOTE]

That didn't help resp. (Turboprint) wasn't necessary after installation of gutenprint 5.

---

