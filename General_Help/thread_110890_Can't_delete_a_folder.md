---
title: "Can't delete a folder"
date: 2005-12-31
forum: General Help
---

### Post by one2one on 2005-12-31
I've tested Mandriva, Mepis, and Ubuntu. Really like Ubuntu's desktop best and webpages looks better on my pc than the other two. Don't like the "Activate modem" and required password everytime I want to go online, but hey...

Anyhow, my problem is, I went into System>Admin>Disks and created a folder in "Home."  Now I want to delete it but can't. Say's I'm not the owner. I can create and rename them, but not delete them. They show up as locked. 

Installing Ubuntu I get only one option for Username and Password. Only one user and only one password. So, if I am not the owner of any folder I create, who is? 

All I can sign in with is my chosen Username and Password. How can I delete these folders I created?

---

### Post by Svictor on 2005-12-31
with sudo, from command line
```
sudo rmdir /name/of/your/folder
``` It will ask you for your password (the one you use for login). This is the standard way to do admin tasks in ubuntu. Mor info here [https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo")

---

### Post by manicka on 2005-12-31
You can't delete them because you have created them with root privileges. 

To create a folder in your home directory just start nautilus then

File-->Create Folder

To delete the folders you created with the disk admin tool

```
sudo rmdir *foldername*
```

---

### Post by taurus on 2005-12-31
And if the folder (we call directory) is not empty, then this command should work,

sudo rm -rf /path_to_that_directory

---

### Post by one2one on 2006-01-01
So, it's not quite impossible with a little help. 
Thanks a lot guys, that was about to drive me nuts.

---

### Post by Canuckelhead on 2006-01-01
There is also a way to do this using the gui....  You can go thru it this way...

Applications/run as different user/   then run nautilus as root.... works every time.  Not as fast as command line but its a nice way to do things for people uncomfortable with the command line.  (**** I can hear the BOOing already***)

---

### Post by one2one on 2006-01-01
I don't have nautilus in my app list. I'll see if I can add it later today and check it out.

Right now I'm testing on a single boot HDD, would like to dual boot on another HDD with XP as soon as I'm a little more comfortable with it. I have a hardware hdd switch where I can choose from 3 different hdd's to boot to.

One other problem is that the Ubuntu clock can't seem to keep the same time with XP. If I set the correct time with Ubuntu then my pc shows 6 hours behind when I switch HDD's to XP. Then If I do the same in XP, Ubuntu shows 6 hours behind. Using the same Time Zones in both. I'm near St. Louis and use CST. Is this a common glitch?

---

### Post by grte on 2006-01-01
[QUOTE=one2one]I don't have nautilus in my app list. I'll see if I can add it later today and check it out.[/QUOTE]

Nautilus is your file manager GUI, if you're using the standard install.

Try

```
sudo nautilus
```

Then inputting your password to open up nautilus with root privilidges.

---

