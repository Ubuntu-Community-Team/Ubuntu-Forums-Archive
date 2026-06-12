---
title: "Missing System, Administration, Network menu"
date: 2009-02-25
forum: General Help
---

### Post by petersfreeman on 2009-02-25
I was reading through the documentation for 8.10 and in this page:

[https://help.ubuntu.com/8.10/internet/C/networking-changecompname.html](https://help.ubuntu.com/8.10/internet/C/networking-changecompname.html)

It said:

```
Change the name of your computer

When connected to a network, your computer can be referred to by its host name. It is possible to change the host name of your computer.
[Important] 	

You must be a member of the admin group in order to change the computer host name.

   1.

      Open System &#8594; Administration &#8594; Network.
   2.

      Press Unlock and enter your password in the Password for (username): field.
   3.

      Press the Authenticate button.
   4.

      Click the General tab. Enter the name of the computer in the Host name field.

Restart the computer for the change to take effect.
```

When I select the System/Administration menu, I do not see the Network item.

Why is it missing and is there another way to change my computer name?

Thanks,

Peter

---

### Post by iaculallad on 2009-02-25
Open your terminal and edit the (2) files below:

```
gksudo gedit /etc/hostname
```

and

```
gksudo gedit /etc/hosts
```

Change your existing hostname on this files. Make sure the new hostname will be identical on both files.

---

### Post by nelskurian on 2009-02-25
1)Network item is a deafult one in system-administration menu.So if it was missing try clicking system icon near to the power butten on the top right.then unlock it and change hostname.
2)You can set the host name using the command line by giving the command 
sudo vim /etc/hosts 
then edit this change the localhost name to something you preferred.

if it worked.then add the network item to the default meny by simply right click on the top panel above the system tab.then edit menus.then add network item manually.

---

### Post by mb_webguy on 2009-02-25
I'm not sure why you don't have Network in the menu (and I'm not using Gnome right now to see if *I* actually have it), but here's another way to change your computer's hostname.

Open the terminal.  Type "sudo nano /etc/hostname".  Change what you see to what you want your new hostname to be (just don't use spaces or any weird characters).  Save and exit.  That's it.  When you reboot, your computer will be named whatever you put in this file

HOWEVER, in order to prevent some serious problems, we need to edit one more file first.  Type "sudo nano /etc/hosts".  You should see a line that starts with "127.0.1.1", and ends with your old hostname.  Replace the old hostname with your new hostname, then save and exit.

*Now* you can reboot.

---

### Post by petersfreeman on 2009-03-30
Thanks iaculallad, nelskurian and mb_webguy.  I have the new host name now.

Cheers,

Peter

---

