---
title: "Launchnig program at startup from its directory"
date: 2009-04-29
forum: General Help
---

### Post by lampak on 2009-04-29
I have written a program I want to have launched at every startup. It is not installed, it's in a subfolder of my home directory. But it obviously uses some files which are in this folder too. I don't know how to force Ubuntu to run it from there. I've been trying adding commands to startup programs like these:

```

cd ~/miernik && ./miernik
cd /home/lampak/miernik && ./miernik
```

Location of my program here is ~/miernik/miernik

They work fine in terminal, but give no result when added to list of startup programs. Any ideas?

---

### Post by spiderbatdad on 2009-04-29
this is a binary program? Not an expert, but i would try making the program owned by root with permissions 755. Put the folder in /usr/local/sbin/ then point to it in /etc/rc.local

Actually what should work better is to simply create the directory /bin in your home folder...I think this is automatically added to $PATH, if not, you will need to edit .bashrc. Then point rc.local to home/user/bin/folder/script

---

### Post by spiderbatdad on 2009-04-29
edited previous post

---

### Post by VCoolio on 2009-04-29
What about using this command as startup launcher:
sh /home/you/subfolder/program.sh

---

### Post by lampak on 2009-04-30
> **spiderbatdad said:**
> this is a binary program?
Yes, it is. 
> **spiderbatdad said:**
> Not an expert, but i would try making the program owned by root with permissions 755. Put the folder in /usr/local/sbin/ then point to it in /etc/rc.local

Actually what should work better is to simply create the directory /bin in your home folder...I think this is automatically added to $PATH, if not, you will need to edit .bashrc. Then point rc.local to home/user/bin/folder/script
Sorry, I'm a noob, I don't understand exactly (especially the first paragraph). But I think the problem is not that the program is not running, but that it uses relative paths and it produces errors when system tries to launch it from some other folder than the one with my app. 

> **VCoolio said:**
> What about using this command as startup launcher:
sh /home/you/subfolder/program.sh
As I said it's a binary program, so I don't think it would work. 


I tried also to compile it in Anjuta, do make install and run as a single command. The program doesn't work then either.

---

### Post by brandon88tube on 2009-04-30
Never really tried so don't hate me if I'm wrong, but have you tried going to System>Preferences>Startup Applications and then click add. From there you could just click browse for the command and then navigate to the file you want to run.

---

### Post by lampak on 2009-04-30
> **brandon88tube said:**
> Never really tried so don't hate me if I'm wrong, but have you tried going to System>Preferences>Startup Applications and then click add. From there you could just click browse for the command and then navigate to the file you want to run.
I have. But then the program is run from my home directory and if I want to open some file it looks for it in home, not in the folder the program is in. 

I temporally solved the problem by placing all files of my app in home, but I don't want to make too much mess there, so I would appreciate any suggestions what I can do about it?

---

### Post by spiderbatdad on 2009-04-30
I was trying to suggest: create a folder in your home directory called bin, and put the program files in there. Then locate the root file /etc/rc.local. Read the instructions in the file and add the path to your program at the end of rc.local. When I did this I had to edit the first line of rc.local, as well, removing -e (I think) after #!/bin/bash on the first line.
When you restart, you program should run.

---

### Post by lampak on 2009-04-30
Strangely my program didn't run even though the script launched manually worked well, as well as a simple test program run by the same script at startup. 

But you've given me an idea with those scripts to write one to run my program and to add the script to startup applications. Now it's working fine, so my problem is solved. Thank you all :)

---

