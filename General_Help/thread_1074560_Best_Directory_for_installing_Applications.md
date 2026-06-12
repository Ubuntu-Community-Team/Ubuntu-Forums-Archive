---
title: "Best Directory for installing Applications"
date: 2009-02-19
forum: General Help
---

### Post by Ciwan on 2009-02-19
Hi Guys

I was wondering .. is there a specified folder (directory) for installing your linux applications into ?

On Windows for example, you have the C://Program Files/

Is there anything equivalent for Ubuntu ?

And why is it that some Linux programs give you the option of where to install, but others don't !!

And finally .. My NetBeans IDE was installed into /usr/local/netbeans-6.5/bin/netbeans

When I try to install a different software into that location (like so: /usr/local/borland/) I get an error saying I don't have rights to save anything in that location !!!

I'd **greatly appreciate** any help given.

Thank You.

---

### Post by mixmaster on 2009-02-19
Generally anything in the ubuntu repositories will decide where it wants to be installed without user intervention.  If you are installing something which does not do this (or building from source) there are a few traditional locations.

Most software will install in or under /usr/bin, /usr/local/bin or /opt.  However, there may be links to other parts of the filesystem.  Occasionally software will install in your home directory if it is for your use only but generally this is not ideal.

This link explains the basic filesystem location conventions : [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

If you try to manually install in /usr/local you will need root permissions (ie use sudo).

---

### Post by Ciwan on 2009-02-20
Hi Mixmaster

Thanks for your nice explanation, I now know how to install programs to different directories :)

However there is a slight problem, The program I installed is Borland Together, which is a Modelling Software. I was expecting to see the program (as a link) in Applications > Programming > ....

I have NetBeans there, but I don't have the Borland Together !!

How can I make it display there ?

Thank You

---

### Post by Ciwan on 2009-02-20
anyone ? :(

---

### Post by jeffjanzen on 2009-02-20
well, i'm a little apprehensive, because i may be wrong, but since no one else is replying:

right-click on the Applications menu and select "Edit menus" and i think you should be able to browse around and add and remove "shortcuts" (that's windows language; not sure if ubuntu people say it differently) to suit your needs.

---

### Post by fragos on 2009-02-20
A properly designed deb package for Ubuntu will place a link in the applications menu. If it doesn't you can add it yourself. To find the physical location of your package If you know the name of the executable use the "which" command to find where the executable is located. Otherwise I suggest you use "locate {name}". You might try "borland" as a name. Right click "Applications" and select Edit menus. This is where you can modify the menus.

---

### Post by Ciwan on 2009-02-20
Thanks Guys

The application is installed at this location:

```
darwin@darwin-desktop-linux:/usr/local/Borland/Together/Architect2006 
```

Inside that directory there is an executable file called [ TogetherArchitect.sh ]

How do I go about combining the two pieces of info above in order to place them inside the command for the Create launcher dialog box (right click applications > edit menus)

I'd greatly appreciate any help.

Thanks

---

### Post by fragos on 2009-02-20
After selecting edit menu choose the menu group you wish to use. For example "Programming" then click "New item button. Create launcher window pops up. In the Command: prompt enter "/usr/local/Borland/Together/Architect2006/TogetherArchitect.sh". You can also select a Name: and icon.

---

### Post by Ciwan on 2009-02-21
Thanks Fargos that was exactly what I needed to know !

But now I'm getting a more serious problem, I don't know if this is a result of me putting a shortcut in the Programming Menu or if it has been like this since the day I installed the program (because I've only just tried running the program)

But when I launch the program I get a pop-up window saying the following:

```
============= Workspace Cannot be locked =================

Could not launch the product because the associated workspace is currently in use.
```

Please help :(

Thank You.

---

### Post by fragos on 2009-02-21
I'm at a bit of a lose with this since I've no experience with your application. You can lock a screen but I don't know if your locking a particular workspace or all access to the monitor. I'm not even sure what I'm saying relates to your problem. I suggest you contact Borland the developer. They may have a web site with forums for users of your package.

---

