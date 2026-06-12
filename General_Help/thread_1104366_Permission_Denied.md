---
title: "Permission Denied"
date: 2009-03-23
forum: General Help
---

### Post by firewarrior on 2009-03-23
Hi all. I have cairo-dock for my desktop launcher. For some reason when I try to import a new theme it tells me that permission is denied. I am the only one who uses my computer and can not figure out how to disable this or get rid of it. If anyone can help that would be awesome.

---

### Post by DeMus on 2009-03-23
> **firewarrior said:**
> Hi all. I have cairo-dock for my desktop launcher. For some reason when I try to import a new theme it tells me that permission is denied. I am the only one who uses my computer and can not figure out how to disable this or get rid of it. If anyone can help that would be awesome.

When it says permission denied, does it also say you have to be logged in as Root? If yes, then open a terminal and work from there, writing sudo for every command you give in the termial. At the first sudo command you have to type a password, which is your password. Ubuntu does not have a password for Root.
Maybe you can write down the entire error so others can have a good look at it.

---

### Post by shao on 2009-03-23
well maybe if oyu run it from the terminal as > sudo cairo-dock  
if that dosent work maybe also chagin the theme folder permissions > chmod 755 /dirname/
hope it works ;)

---

### Post by Nano_ext3 on 2009-03-23
The most simple way is to do "**chmod +rwx /path/to/folder**

Cheers!

_Nano

---

### Post by bodhi.zazen on 2009-03-23
> **Nano_ext3 said:**
> The most simple way is to do "**chmod +rwx /path/to/folder**

Cheers!

_Nano

No , please do not change permissions to system files and directories like that as it is likely to cause breakage.

---

### Post by firewarrior on 2009-03-23
Hi all. I have cairo-dock for my desktop launcher. For some reason when I try to import a new theme it tells me that permission is denied. I am the only one who uses my computer and can not figure out how to disable this or get rid of it. If anyone can help that would be awesome.

---

### Post by Nano_ext3 on 2009-03-23
Then **chmod 700 /path/to/folder/** would be appropriate Bodhi, or what way is best ?

:P

---

### Post by bodhi.zazen on 2009-03-23
It depends on the directory.

If it is a directory in your home directory, well then I do not care (well I care a little, 700 is probably best or most directories in /home , unless you want to share).

Perhaps I was not clear,

It is a system directory, in /usr /bin /etc /var then it depends on the directory and what you are wanting to do.

I am just objection to using 

chmod +rwx foo (and chwon).

to solve permissions problems.

---

### Post by firewarrior on 2009-03-23
The import says nothing about the Root all it says is this: There was an error moving the file into /usr/share/cairo-dock/themes. Under details it just says permission denied. Don't know what to do from here. I tried the terminal thing and that didn't work either. :(

---

### Post by kanikilu on 2009-03-23
> **firewarrior said:**
> The import says nothing about the Root all it says is this: There was an error moving the file into /usr/share/cairo-dock/themes. Under details it just says permission denied. Don't know what to do from here. I tried the terminal thing and that didn't work either. :(

I think everything in /usr/share/ is owned by root, so you would need to copy or move the files either using *sudo mv* on the commandline, or just start a root-owned nautilus window with *gksudo nautilus* and move the files to that directory.

---

### Post by VCoolio on 2009-03-23
I think cairo-dock is somewhere in /usr/share or /usr/lib or where-ever so it needs root privileges to copy files there. You should find out in what folder the cairo-dock themes are stored and copy your theme manually in a root nautilus (run gksudo nautilus) or by sudo cp [/location/of/theme] [/folder/of/cairodockthemes]. Hope that helps.

---

### Post by Nano_ext3 on 2009-03-24
Bodhi , my bad haha, of course for user you would want "chmod u+rwx" 

Silly me :P

_Nano

---

### Post by firewarrior on 2009-03-24
The files are located in the file: /usr/share/cairo-dock/themes
This is where all the themes are located. I'm not sure where to move them to, to make them non-root.

---

