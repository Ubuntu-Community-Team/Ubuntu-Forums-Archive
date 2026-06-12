---
title: "Really need help installing things"
date: 2009-03-22
forum: General Help
---

### Post by Slim. on 2009-03-22
Well so far I've downloaded AWN, COMPIZ, and a few other basic apps. / programs on the latest version of Ubuntu. But recently I've been trying to download things like "GoogleEarth-Package" and also "Wine" and when I install them I have no clue where they are located or if they even actually downloaded. 
If it helps, this always is displayed at the end of installation "ldconfig deferred processing now taking palce"

Can someone please tell me how to locate installed files, and what that "ldconfig deferred processing now taking palce" means? Thanks a lot.

Slim. :o

---

### Post by issih on 2009-03-22
Hopefully you are downloading things using add/remove or synaptic package manager rather than just grabbing things from websites.

[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

That should help you out if not.

Once something is installed, you shouldn't really need to know where it is under normal usage. Most packages make a menu item as part of the installation, so they can be launched easily. Those that don't are mostly command line applications, and when using the terminal, the system has a default PATH which is a list of all the directories likely to contain executable files, which it searches automatically. Consequently you don't need to type anything more than "firefox" in order to run the web browser, despite the fact that it actually lives in usr/bin/firefox.

Having said that, there are various tools to find the files if you really need to:
Running
```
whereis firefox
```
in a terminal window produces a list of locations of files named firefox.

You can also (provided you installed in the approved of way :)) open synaptic package manager, navigate to the package in question, and in that package's properties will be a list of where the installer put various files for that package.

As for those messages, you are getting, that is just the system taking the necessary steps to install the software, don't worry about it.

[https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/15849](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/15849)

---

### Post by oldos2er on 2009-03-22
'man ldconfig' says in part: 
       ldconfig  creates,  updates,  and removes the necessary links and cache
       (for use by the run-time linker,  ld.so)  to  the  most  recent  shared
       libraries  found  in  the directories specified on the command line, in
       the file /etc/ld.so.conf, and in the trusted directories (/usr/lib  and
       /lib).   ldconfig  checks the header and file names of the libraries it
       encounters when determining which  versions  should  have  their  links
       updated.   ldconfig ignores symbolic links when scanning for libraries.

 Check in Synaptic Package Manager, right-click on an installed package and choose Properties, Installed file, for where each file in the package is installed.

---

### Post by Slim. on 2009-03-22
Thank you for the reply, but I still have three more questions. 
1 - Is there any way that I can find a program , for example Firefox, without typing it in terminal and icons. Like can I go through a "My Computer" type search and find it? Because for example, like when I downloaded "GoogleEarth-package" I didn't know where to find it after I downloaded it. I tryed in terminal running things like "Google Earth", "GoogleEarth" , and even "GoogleEarth-Package" and got nothing.
2 - It's about the program Conky, I have downloaded it and put the ".conkyrc" file in "/home/username" but everytime I hit Alt + F2 and type Conky, it doesn't load at all. Do you know how to solve this?
3- Is it ok that at the end of when it installs it says 
"ldconfig deferred processing now taking palce" 
then underneath it it says this as if it's done installing and the ld config isn't happening
UserName@ubuntu:~$

---

### Post by issih on 2009-03-22
1) There is a file browser, and a search utility under the places menu, you can find any file on the system from the gui using those.
As we said the easiest way is probably to go look at the google earth package's properties in synaptic package manager.

Also note that you can usually get the name of an unknown package using tab completion in the terminal, just type goo and hit the tab key, and any program names starting with goo will be listed.

2) I'd guess that "conky" all in lowercase is the executable name, the case matters. you can check with tab completion as suggested above.

3) Don't really follow, unless it states that something went wrong, I'd just ignore it, its just giving you a running commentary on the installation.

---

### Post by Slim. on 2009-03-22
Thank you very much Issih.

---

### Post by oldos2er on 2009-03-23
If you're running Tracker, use that for GUI search. Or, there's a program called catfish that's handy too.

 When you say you downloaded conky, did you use a package manager? or download source code? Probably best to stick with a package manager for now.

 That ldconfig output is perfectly normal.

---

### Post by issih on 2009-03-23
I don't think tracker indexes large chunks of the file system by default, including the bin directories..I might be wrong though.

---

### Post by oldos2er on 2009-03-24
> **issih said:**
> I don't think tracker indexes large chunks of the file system by default, including the bin directories..I might be wrong though.

 I don't know either--tracker's one of the first things I remove on an Ubuntu installation. I'm pretty sure it can be configured to look at any directory tho'.

---

