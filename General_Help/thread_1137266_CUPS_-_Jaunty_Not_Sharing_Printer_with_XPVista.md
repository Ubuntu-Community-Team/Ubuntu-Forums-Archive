---
title: "CUPS - Jaunty Not Sharing Printer with XP/Vista"
date: 2009-04-25
forum: General Help
---

### Post by rkane1226 on 2009-04-25
I have already visited many threads related to this topic.  My goal is to share the HP Photosmart 7960 connected to my Ubuntu box with the various XP and Vista machines used by the rest of my family.  I simply can not do it.

I have a desktop set up as a personal workstation (not a server installation) with Juanty on it.  I've been trying to setup network print services since Gutsy but I give up.

I have been here: [http://ohioloco.ubuntuforums.org/showthread.php?p=6978623](http://ohioloco.ubuntuforums.org/showthread.php?p=6978623)

I have also been here: [http://www.swerdna.net.au/linhowtosambaprint_1.html](http://www.swerdna.net.au/linhowtosambaprint_1.html)

I've gotten to the point where I can go to [http://localhost:631/](http://localhost:631/) and get the admin pages.

I have done various things in an attempt to get to the point where I could change the above line to:  [http://ubuntu_machine_name:631/](http://ubuntu_machine_name:631/) or to [http://ip_address_of_ubuntu_machine:631/](http://ip_address_of_ubuntu_machine:631/) but I can not get that to work at all, not even from a web browser ON the ubuntu machine.  Instead all I get is:

426 Upgrade Required

You must access this page using the URL [https://192.168.0.100:631/admin](https://192.168.0.100:631/admin).

If I go to a Vista machine I get the same message.

Now, keep in mind that all of the previous only allows me to MANAGE the printer from a web interface.  I have not even gotten to actually printing.

When attempting to add the printer on a Vista machine here is what works:

1. I can see the ubuntu machine on the network by name
2. I can open the ubuntu machine from the Vista machine and see the shared folders and printer.
3. I can right click on the printer and "connect" to it.
4. I can print to that printer for a while - like until I log out.

Here is what doesn't work:
1. I can not add the printer using [http://machine_name/printers/printer_name](http://machine_name/printers/printer_name).
2. I can not print to the printer previously added using "connect".
3. I don't even get prompted for a password.

I suppose the windows users could simply be required to navigate to the ubuntu box and connect to the printer every time they log on.  But that is a really sad solution.

I am frustrated that, after 4 releases, I still can not get this to work on Ubuntu.

I apologize if I've hit a "solved" problem but I would appreciate any suggestions or pointers.

---

### Post by DenysT on 2009-04-25
> **rkane1226 said:**
> 
1. I can see the ubuntu machine on the network by name
2. I can open the ubuntu machine from the Vista machine and see the shared folders and printer.
3. I can right click on the printer and "connect" to it.
4. I can print to that printer for a while - like until I log out.



Even though you are running Ubuntu, Vista had (and still has this problem to some extent) with XP shared printers. Here is the solution that worked for Vista connecting to XP. You might try this and see if it works. Just mentally replace XP with Ubuntu in the instructions.

1.) Verify that File and print sharing is turned on and properly configured 

on the XP machine. 

2.) Locate and notate the Win XP computer name (i.e. "Desktop") (Found in 

System Properties in the Computer Name tab) 

3.) Locate and notate the printer share name on the XP computer (i.e. 

"Printer") (Found under the Sharing tab on the Printer Properties page) 

4.) On the Vista machine launch the "Add a Printer" wizard 

5.) Choose "Add a local printer" 

6.) Select "Create a new port" radio button and choose "Local Port" from the 

drop down menu 

7.) Press Next 

8.) In the "Enter Port Name:" box enter the following: \\Desktop\Printer 

where "Desktop" = the computer name from step 2 and "Printer" = the printer 

share name from step 3. 

9.) Select the Printer driver from the list provided or use the "Have Disk" 

button to install the correct Vista driver if it is not in the built-in list. 

It is critical that the driver you use is Vista compatible. 

10.) Press next 

11.) Give the printer a distinct name and choose whether to set as the 

default. 

12.) Press Next 

13.) Print a test page to verify functionality. 

14.) Press Finish

---

### Post by rkane1226 on 2009-04-26
> **DenysT said:**
> Even though you are running Ubuntu, Vista had (and still has this problem to some extent) with XP shared printers. 

Am I mis-reading your help here?  The shared printer is connected to the Ubuntu machine not an XP machine.

Are you saying, "Suceed in getting the Ubuntu shared printer to work on XP, then copy information to Vista?"

I'm pretty sure I can't get this to work from Vista ____OR____ XP.

---

### Post by rkane1226 on 2009-04-26
> **rkane1226 said:**
> Am I mis-reading your help here?  The shared printer is connected to the Ubuntu machine not an XP machine.

Are you saying, "Suceed in getting the Ubuntu shared printer to work on XP, then copy information to Vista?"

I'm pretty sure I can't get this to work from Vista ____OR____ XP.

In fact, I can't get a different Ubuntu machine on the network to print to this queue, although the printer shows up when I use the "server" menu to "show" available printers.

---

### Post by DenysT on 2009-04-27
> **rkane1226 said:**
> Am I mis-reading your help here?  The shared printer is connected to the Ubuntu machine not an XP machine.

Are you saying, "Suceed in getting the Ubuntu shared printer to work on XP, then copy information to Vista?"

I'm pretty sure I can't get this to work from Vista ____OR____ XP.

No you are not mis-reading. This solution was provided by MS Tech support for connecting XP shared printers to Vista. Since Vista had a problem connecting to XP shares (Only MS knows why) the solution could work with Ubuntu shared printers too. Since you're doing it on the Vista machine it will either work or not but it will not affect the Ubuntu machine. All you are doing is mapping a network location to a local port on the Vista machine, it'll either take or it won't. I have used this myself connect many Vista laptops to shared XP printers on desktops so I know it works. Try it, the worst that can happen is Vista will reject the connection if no drivers are available in Vista.

---

### Post by rkane1226 on 2009-04-27
> **DenysT said:**
> No you are not mis-reading. This solution was provided by MS Tech support for connecting XP shared printers to Vista. Since Vista had a problem connecting to XP shares (Only MS knows why) the solution could work with Ubuntu shared printers too. Since you're doing it on the Vista machine it will either work or not but it will not affect the Ubuntu machine. All you are doing is mapping a network location to a local port on the Vista machine, it'll either take or it won't. I have used this myself connect many Vista laptops to shared XP printers on desktops so I know it works. Try it, the worst that can happen is Vista will reject the connection if no drivers are available in Vista.

Okay, gotcha, thanks.  I'll try it, although I'm now concerned that a second Ubuntu machine can not print to the printer on Ubuntu machine #1.

---

