---
title: "How do i install Beryl"
date: 2007-03-14
forum: Desktop Effects &amp; Customization
---

### Post by naossoan on 2007-03-14
I'm trying to install Beryl and I'm really confused.

I'm a pretty noob Linux user.

I was reading a howto on this forum and it said to add the beryl repositories. i have no idea what that means or how to do that.

can someone please explain?

thanks!

---

### Post by steveneddy on 2007-03-14
> **naossoan said:**
> I'm trying to install Beryl and I'm really confused.

I'm a pretty noob Linux user.

I was reading a howto on this forum and it said to add the beryl repositories. i have no idea what that means or how to do that.

can someone please explain?

thanks!

For Dapper try [here]("http://forum.beryl-project.org/viewtopic.php?f=43&t=70").

For Edgy go [here]("http://forum.beryl-project.org/viewtopic.php?f=43&t=51").

You will have to open a file and edit a line - add a line to the bottom of the file.

Do this in terminal:

```
sudo gedit /etc/apt.sources.list
```

you will have to enter your log in password in terminal, then after you make the change, save the file.

Good Luck

---

### Post by naossoan on 2007-03-14
Ok, when I try to run the last command on that other forum post

```
sudo apt-get update && sudo apt-get install beryl
```

 I get this at the end.

```
W: Duplicate sources.list entry http://archive.ubuntu.com edgy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com edgy-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_edgy-commercial_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl
```

EDIT:: By the way, sorry forgot to say im running 6.10 Ubuntu Edgy

---

### Post by naossoan on 2007-03-17
can someone please help? I can't get it installed. I added the repository via the System > Administration > Synaptic Package Manager

but when I try to get into the Add/Remove software, it gives me this error message:

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.


I checked the sources.list file and it looks fine to me its the same as before.

If I try to run 

```
sudo apt-get update
``` 

It tells me there's an error in the file 
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)

So i went into that file and commented out everything and tried to run the command again

and it tells me the same thing....

I'm so lost because now not only can I not install beryl, but I can't open up my Add/Remove application anymore...

can someone please help?

This is the contests of the last file I just mentioned

```
# automatically added by gnome-app-install on 2007-03-06 09:46:40.585006
deb http://archive.ubuntu.com/ubuntu/ edgy
deb http://security.ubuntu.com/ubuntu edgy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates
```

---

### Post by old_geekster on 2007-03-19
I installed Beryl using Automatix Bleeder; not Automatix2.

It is actually running the way that it should for the first time.

Add this to your /etc/apt/sources.list:

#AUTOMATIX BLEEDER REPOS START
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
#AUTOMATIX BLEEDER REPOS END

---

### Post by jmoro on 2007-03-19
hey i just installed beryl. only problem im having is i know that my card supports 3d graphics but i have the theme i want program in i have beryl set to start when i start my computer but the 3d graphics and theme still arn't working. im running a dell inspirion b120 any help that anyone can give would be appreciated.

---

