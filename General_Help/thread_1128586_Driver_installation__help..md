---
title: "Driver installation  help."
date: 2009-04-17
forum: General Help
---

### Post by katsrevenge on 2009-04-17
Hello. I am a complete newb to Linux, I will state that beforehand. I'm not a computer newb... but I am a Linux newb.

I installed the most recent Ubuntu OS on a 10 year old HP computer. (Off-topic, I love how it runs as fast as my 2 yr old gaming XP comp, is this normal?) It was a clean install, I had wiped ME off the disk long ago. 

So, clean install, OS from the webpage, no issues. It does what a computer is supposed to do. However, the wireless card I have for it does not have Linux support. I read that I need ndiswrapper to make it work. 

First, I attempt to use the inbuilt help. While I am able to find the kernel it claims I should use (right term?) I am unable to figure how to install it. I was using the visual installer at this point. The inbuilt kernel would show up in the search result, but there would be no option to install it or do anything with it. Insert much swearing and wishing I still smoked ciggies.

I go to the interweb and find (and DL) ndiswrapper. I follow these directions from step 5..as that comp has no interweb:

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper)) 

Here is where I screw up in the terminal... From:
user@ubuntu:~$ tar xvzf ndiswrapper-1.28.tar.gz 

(please note I updated the release, I think it was 1.54.. it's the latest on sourceforge) 

It tells me it does not exist. It is right on my desktop... just sitting there... I unzipped it, no dice. I messed with the zip file.. nothing. Tried to put it in the system files.. nothing... swore at it... 

I have no clue what I am doing wrong. I've the driver for the Linksys card and ndiswrapper on my desktop and I can't figure out how to make them play nice. I know the computer sees the USB wireless card, I got it to display in the terminal. 

Help? Please?

If this is in the wrong area, I apologize.

---

### Post by cariboo on 2009-04-17
Ndiswrapper is included on the LiveCD, Go to System-->Administration-->Software Sources, and make sure the cd is enabled (the cdrom has to be in the drive). Next go to System-->Administraion-->Synaptic Package Manager, and click the search button and enter ndiswrapper in the text box. It should find ndiswrapper, ndiswrapper-common and ndisgtk. I would suggest you have a look at this [sticky]("http://ubuntuforums.org/showthread.php?t=885847").

Jim

---

### Post by katsrevenge on 2009-04-17
Thanks, I will try that after I finish this post.

I saw that, but I couldn't get ndiswrapper to install from the file I have. That assumes it installed. That is my issue at this point.

---

### Post by katsrevenge on 2009-04-17
All righty. The box marked Installable from CDROM is blued in. The CD is in the drive.

> In System-->Administraion-->Synaptic Package Manager, and click the search button and enter ndiswrapper in the text box. It should find ndiswrapper, ndiswrapper-common and ndisgtk

I find ndiswrapper. I cannot manipulate the package with the "Package" prompt in the Synaptic Package Manager. All options are greyed out.

How do I install it? What am I doing wrong?

Edit: I'm back in the terminal editor. The visual editor will not do anything. I get prompted to install ndiswrapper when using ndiswrapper -l.

I type in the suggested line from the terminal, it claims that it cannot find ndiswrapper-common. I have the disk in the drive. I am really lost at this point.

I am following directions given in the how tos and I don't have a friend who uses this OS. I've never used this OS. Feel free to talk to me like a 5 year old, I don't know what I am doing. What am I doing wrong?

---

### Post by oldos2er on 2009-04-17
Open a terminal, and run these commands one at a time:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper
``` You'll need to have the LiveCD in your CD drive. If there are any errors, please copy and paste them from the terminal to a post here.

---

### Post by katsrevenge on 2009-04-17
Thanks. :)

I think I figured out what was wrong, I needed to get the supporting packages, then it showed up to be installed. I have it installed from CD, now I am attempting to actually install the driver itself. 

Wish me luck because I am sure I will need it. :P

---

