---
title: "Applications Menu Not Showing"
date: 2006-03-16
forum: Desktop Environments
---

### Post by blakegrover on 2006-03-16
I initially installed Kubuntu 5.10 Breezy on my machine.  I was wondering how gnome would perform so I ran the following:
```
apt-get install gnome
```

I let it install all the packages and restarted the computer.  I changed the default session to Gnome and logged in.  Everything seems to be working great and it is a lot better than kde was performing so I would like to use gnome instead.  But I have one problem.  For some reason when I click on the application menu it displays it for half of a second and then disapears.  I can see the places and system menu just fine and all the programs seem to work great but I would really like to get my application menu working.

Blake

---

### Post by Xian on 2006-03-16
Try installing the ubuntu envrionment and see if that helps:

$ sudo apt-get install ubuntu-desktop

---

### Post by blakegrover on 2006-03-17
I tried installing the ubuntu enviroment (ubuntu-desktop) and still nothing.  Another problem I noticed was the first time I rebooted I could run kmail, konqueror, etc. in gnome which was nice because I have all my mail in kmail.  But after I installed the ubuntu-desktop and rebooted it won't run my kmail or anything k*.  I would really like tu use both applications under gnome.  Any suggestions? If I have to I guess I could install ubuntu and erase all my stuff on my hard drive but I think that would be a last resort.

Blake

---

### Post by blakegrover on 2006-03-17
After loggin in to kde and logging out and then loging in under gnome I can run kmail.  But the menu still is only showing for a plit second.

---

### Post by OMRebel on 2006-03-17
blakegrover - drop out to a terminal and try 'sudo smeg' and see if it'll load.  I had the exact same problem.  It's a bug in Breezy with permissions not being set correctly.

---

### Post by blakegrover on 2006-03-17
I ran sudo smeg and it poped up the menu editor.  It ran fine, then I ran just smeg under my user and I got some errors in the terminal window and I got a permission error:
```
Permission denied: u'/home/blake/.local/share/desktop-directories/Test.directory'
```
I tried to create a new menu
I noticed that everything under .local is owned by root.  So I changed the ownership to my name and group but the menu still is bad.  Do I need to reboot?

---

