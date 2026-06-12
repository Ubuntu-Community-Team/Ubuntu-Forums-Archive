---
title: "Where is my software?"
date: 2009-06-17
forum: General Help
---

### Post by Javijavi on 2009-06-17
Ok, so after learning how most linux software under ubuntu is installed through this synaptic package manager thing, I can browse and click on various programs to install. But then what? Where does it go? Under windows after you download something, you are usually given a desktop icon or at the very least, could browse to the folder you installed it to. But no such options appear when I install these "packages". They just kinda go off, do their thing, and then Im just left staring at the package manager. How can I find what I just installed so I can begin using it?

---

### Post by synapsys on 2009-06-17
When you install software from synaptic it is listed under the Applications menu (like the start menu in winblows) on the top left of the screen.

---

### Post by Hobgoblin on 2009-06-17
Most packages will appear on the relevant menu, some will not, especially those which are invoked only through the command line.

---

### Post by jbruced on 2009-06-17
#1, Most applications end up in the menu system by default. If it doesn't, just ask anyone here and name the application, we're all glad to help.

#2, You usually don't have to reboot or anything like that, it's ready to run as soon as it's installed. 

#3, It's not windows, and will never work like windows, that's a benefit you'll soon enjoy if you spend a little time with Ubuntu.

Welcome to Ubuntu!

---

### Post by Javijavi on 2009-06-18
Is there a more elegant manner to find what exactly has been installed? It seems as of now, the standard procedure is to just install software, and take a random guess that whatever pops up in your system menu's might happen to be what you installed. For instance, I downloaded something called Logical Volume Manager. I found it under applications->system tools->LVM. 

However then I downloaded GParted, and found that in a totally different menu hierarchy with a totally different name associated with it. This one was located under system->administration->partition editor. The program is universally known as GParted, yet rather than keeping true to this name once it is installed, it just took a generic "partition editor" name. Point is, I glanced over it about 5x looking for "Gparted" before I realized that a partition editor was probably what I was looking for. Also kind of a waste of time when you dont already know which programs came pre-installed, so I dont know if what I am overlooking was something I installed or something that came with ubuntu.

---

### Post by tomd123 on 2009-06-18
> **Javijavi said:**
> Is there a more elegant manner to find what exactly has been installed? It seems as of now, the standard procedure is to just install software, and take a random guess that whatever pops up in your system menu's might happen to be what you installed. For instance, I downloaded something called Logical Volume Manager. I found it under applications->system tools->LVM. 

However then I downloaded GParted, and found that in a totally different menu hierarchy with a totally different name associated with it. This one was located under system->administration->partition editor. The program is universally known as GParted, yet rather than keeping true to this name once it is installed, it just took a generic "partition editor" name. Point is, I glanced over it about 5x looking for "Gparted" before I realized that a partition editor was probably what I was looking for. Also kind of a waste of time when you dont already know which programs came pre-installed, so I dont know if what I am overlooking was something I installed or something that came with ubuntu.

Ubuntu tries to help beginning users. Most beginners probably don't know what gparted is, but they know what a partition editor is if anything. And the menu items are placed to where the developers think makes the most sense. You shouldn't think that the default is perfect.

**HINT** you can edit the menu quite easily and rearrange the menu items to your choosing if it really bothers you, heck you can even rename the "partition editor" to gparted if you would like.

---

### Post by Therion on 2009-06-18
If you'd like to see all the applications you have installed, and JUST those applications (along with a short description of what they do), go to Applications > Add/Remove and in the "Show" box/filter at the top left, change it to read "Installed applications only" and... *Voila!*

From there you can click on the sidebar on the left and further filter things by Application *type* (e.g. Office, Graphics, Sound and Video, etc.) so you can get a grip on *what* you have installed, *where* it's installed and an idea of what it *does*, all with just a few clicks of your mouse.

In addition... If the application has a web site, you'll be provided with the direct link.

---

### Post by rushikesh988 on 2009-06-18
> **Javijavi said:**
> Is there a more elegant manner to find what exactly has been installed? It seems as of now, the standard procedure is to just install software, and take a random guess that whatever pops up in your system menu's might happen to be what you installed. For instance, I downloaded something called Logical Volume Manager. I found it under applications->system tools->LVM. 

However then I downloaded GParted, and found that in a totally different menu hierarchy with a totally different name associated with it. This one was located under system->administration->partition editor. The program is universally known as GParted, yet rather than keeping true to this name once it is installed, it just took a generic "partition editor" name. Point is, I glanced over it about 5x looking for "Gparted" before I realized that a partition editor was probably what I was looking for. Also kind of a waste of time when you dont already know which programs came pre-installed, so I dont know if what I am overlooking was something I installed or something that came with ubuntu.
BRo I think you should read something about Ubuntu on Internet You will find lot of about Ubuntu and its application on the internet just make a simple google search

---

### Post by oldos2er on 2009-06-18
"Is there a more elegant manner to find what exactly has been installed?"

 Synaptic can show you where each file in a package has been installed. Right-click on an installed package, choose Properties, Installed Files.

---

