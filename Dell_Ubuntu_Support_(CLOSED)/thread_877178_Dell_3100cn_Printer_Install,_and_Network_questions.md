---
title: "Dell 3100cn Printer Install, and Network questions"
date: 2008-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Spops on 2008-08-01
Can anyone help me figure out how to install a Dell 3100cn printer on Ubuntu 8.04.1 (this is a wubi install version).  Ubuntu recognizes the printer, but nothing will print.  I tried to use the Dell install CD but it only has drivers for Red Hat Linux (same for dell's website).  

Also is there anyway to get Ubuntu to connect to my existing Windows network?  This printer is one of my network printers through windows.  It is connected to this Dell computer through a Firewire to USB cable.  If not it is not a HUGE deal.  I can always just boot up into windows if I need to print something from another computer.

Thanks for any help.

---

### Post by linux_tech on 2008-08-02
Connect wirelessly or by wire? 
Windows? what version? Is this a client server active directory network 
or is this another windows client that you want to connect with to share a printer or some files.  Thanks for clarifying

---

### Post by linux_tech on 2008-08-02
Step 1- Install Ubuntu 
Step 2 - Create a folder in Ubuntu to become visible (later) on the network

You could think of this new folder becoming your Ubuntu equivalent of the 'Shared Documents' folder in Windows.
Right-click on the Ubuntu desktop & create the new folder called, say, for simplicity,  Ubuntu Shared

===========================================================================

Step 3 - Prepare the folder for sharing on the network
Right-click on the Ubuntu Shared folder, and select Share Folder
Ubuntu will ask for your login password
 After a short delay, a dialog saying' Sharing Services are not installed' will appear
Leave both the Unix & Windows network support options ticked, and click Install Services
This caused a program called Samba to be downloaded from the internet & installed
Wait for the installation to complete with the message Changes Applied, then close the dialog.
A Share Folder dialog appears - from the Share through drop-down, select Windows Networks.
The Share Folder dialog box then expands, showing the folder name.
Remove the tick in the 'Read Only' box, and click on OK
At this point, the Ubuntu PC will become visible to Windows PCs on the network:
On a Windows XP PC, go to 'My Network Places' > 'View Workgroup Computers'
The Ubuntu PC icon will be shown, and when clicking on it a password is requested.

But no password will be accepted until completion of the following final steps in the process.

===========================================================================

Step 4 - Configure SAMBA to accept your password

You have to add yourself as a user in Samba.     Open the Ubuntu Terminal :

When Terminal asks for passwords, no typing is displayed at all, & the cursor does not move in reponse to key presses, but the password DOES go in when you press enter !!

When Terminal has opened,  type the following:

sudo smbpasswd -L -a logname   and press 'enter'      

(Use your own Ubuntu log-in name instead of logname )

You will be asked for a password - be sure to use the same as you use for your Ubuntu login, & enter 

It then asks for 'New SMB password' - again, type the same as you use for your Ubuntu login & enter

It then asks you to re-type it, & enter

You are then returned to the command line

Then type the following:
sudo smbpasswd -L -e logname  (Use your own Ubuntu log-in name instead of logname )

It responds with the message 'Enabled user logname'
Close the terminal dialog (x in top-right), & Re-start the Ubuntu PC (an old Windows habit...)

===========================================================================

Step 5 - Access the Ubuntu pc from a Windows pc.
On a Windows XP PC, go to 'My Network Places' > 'View Workgroup Computers'
The Ubuntu PC icon will be shown, and when clicking on it a password is requested.
Enter the login name & password from the Ubuntu PC you are connecting to:
You can then see & access the Ubuntu shared folder you created in step 2.

---

### Post by linux_tech on 2008-08-02
Linux planet has some easy use tutorials to get samba set up
[http://www.linuxplanet.com/linuxplanet/tutorials/6495/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6495/1/)

---

