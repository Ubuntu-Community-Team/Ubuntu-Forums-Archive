---
title: "Not able to use features in the menus"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Crochetchick on 2006-01-05
I just installed Ubuntu and this is my first linux experience. I also have Ubuntu installed on the same partition as Win Xp.

I read through the beginer primer in the lifeboat icon. I was trying to install the plugins for firefox, but it won't let me do it. Where it says to go to Applications - System Tools - Terminal, well there is no terminal choice to pick. Also I can't get updates and load many System - Administration tools.

I really don't know what to do, can anyone help?

---

### Post by nalmeth on 2006-01-05
[http://ubuntuforums.org/showthread.php?t=64629](http://ubuntuforums.org/showthread.php?t=64629) ---> Easy Ubuntu

Do you have internet connection? Assuming you are using Gnome, there should be a window that pops up at the bottom right, saying updates are available. You need to enter the password you set up during install. 

If you don't mind the terminal (command line) open one up and type

sudo apt-get update
sudo apt-get upgrade

EDIT: Terminal is found in:
Applications --> Accessories

---

### Post by Crochetchick on 2006-01-05
I did try to get the updates. When I click on it, a bar on the bottom of the screen will say it's loading then after a few seconds, nothing comes up. This also happens when trying to use certain choices in the main menus.

---

### Post by nalmeth on 2006-01-05
Hmm.

I don't really understand your problem..
How fast is your computer?
Did you watch Ubuntu install all the way through? Do you have an internet connection?! If not, many packages that are part of ubuntu won't install. Do you have a direct internet connection to a router, or are you using wireless?

Try the terminal update that I suggested. Also, post any and all information that may be relevant. People here are smart and intuitive, but their ability to help depends on all the info available. 

If you know you have an internet connection, try the terminal update as I said, and then get Easy Ubuntu. It will install basically everything you need. Automatix is better I think, but for a fresh intro, easy ubuntu will suit you.

EDIT: What do you mean the same partition as XP? You mean same harddrive different partition I hope? :)

Keep us posted :)

---

### Post by Crochetchick on 2006-01-05
I do have internet connection to a wireless router and am online with the computer running ubuntu.
Ran the script you had in the last post and a black screan flashed  quick then nothing.
When I installed ubutnu with advanced installation options so I could repartion my drive that has Xp on, and ubutnu is on it's own partition.
I have pentium 4 with 256 mb ram, not too bad.

I am ultimately trying to install java, flash and adobe. This won't let me do anything to install.

---

### Post by nalmeth on 2006-01-05
No, not bad at all. It is certainly not a hardware problem. I'm sorry to question your computer performance!

Anyway, these are indeed strange problems. So long as you are patient they will be resolved.

I don't know if you have yet, but go to Applications --> Accessories ---> Terminal

type:
```
sudo apt-get update
``` 
(you will be prompted for password) - post the output here (a shortcut for copying and pasting in linux --> highlight the text with left mouse button, and paste with middle button, or left and right together if you don't have a mouse wheel)
```
sudo apt-get upgrade
```
post this output too

EDIT:
also, type:
sudo gedit /etc/apt/sources.list
and let us know if this file is empty. If it has a bunch of websites (repositories) then it is fine.

if you were unable to install updates when you first loaded Gnome, this might not work. Here's why. To perform administrative duties (installing/uninstalling programs, modifiying integral files), you must be the root user (administrator). For safety from malicious sources, and accidental operations, this root user is off by default. The "sudo" command allows you to temporarily perform administrative duties, without browsing your computer as a full-fledged root user. This is a HUGE safety component. 
Sudo is actually a program, and is installed with the first update when you load Gnome. If this is not installed yet, don't worry, you don't have to reinstall. You can still setup the root user, and then setup sudo later. 
I have a feeling now this is the problem. 
apt-get is a program that installs all your programs, and their dependencies for you. When you have it working, it will impress you. 
There are graphical frontends to apt, such as synaptic, kynaptic, kpackage. Gnome comes with one in the application menu ---> Add applications.

Anyway, sorry to ramble, especially if you know all this. It is important information. 

If easy ubuntu didn't work, then you can try automatix.
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
instructions are included, and it will create a root user for you for it to work. 

I hesitated to refer you to this if you are totally new to linux, but it is pretty self-explanitory. It is really kick-ass. It will give you java/flash, and a lot more.

I still don't exactly understand the nature of your problem. Try to look around for a screenshot taker, and post some pics here for visual reference.

I will be away for a couple hours, as I am on vacation, and touring NYC, but will be back later this evening. Keep posting info as it comes up, and ppl will help.

---

### Post by Crochetchick on 2006-01-05
I am totally new to Linux.
I found the terminal and put in the commands you said to and nothing happened.
I need to take a rest for a bit because I'm very frustrated.

ubuntu will not let me install anything because I don't have administration privilages to do it. That is the error that comes up, if it gives me an error. I can't look at alot of the menu choices because they don't load up when I press them.

---

### Post by tpotato on 2006-01-05
I had a problem like that where sudo didn't work 
due to not having the system name in the /etc/hosts 
file. Somehow this occurred via the install program. There needed to be an entry something like :
127.0.0.1 localhost mysystem 
Where "mysystem" is what you called it. 
If only "127.0.0.1 localhost" is in there,  
that causes sudo to refuse to recognize you as 
an administrator. There may be other ways that sudo 
can decide to not allow you to do root things and that
causes an effect that the menus don't work. 
In my case I needed to edit /etc/hosts and the only
way I could do that was via the recovery console. 
That would be a good thing for an faq.

---

### Post by Crochetchick on 2006-01-05
tpotato, that is my problem. When I went to /etc/hosts this is what it says:

127.0.0.1	localhost.localdomain	localhost	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

So how do go about changing it?

---

### Post by nalmeth on 2006-01-05
tpotato, in what way did you edit /etc/hosts? Or anyone else for that matter? I'm sorry I can't help you myself crochetchick, but I have no experience with this problem.

---

### Post by Crochetchick on 2006-01-06
Thank you, Nalmeth and Tpotato, for all your help so far. 

Does anyone know how to fix this problem?

I am very excited to make the conversion from xp final!

---

### Post by Crochetchick on 2006-01-11
Well, I have reinstalled Ubuntu using the standard instalation and now I running everything fine. Thanks anyways.

---

