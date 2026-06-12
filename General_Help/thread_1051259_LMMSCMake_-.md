---
title: "LMMS/CMake - ?"
date: 2009-01-26
forum: General Help
---

### Post by vaughnm on 2009-01-26
Ok, whats the deal here. I want to use LMMS because I heard it was a great piece of software. 
I'm terrible with manual installs though. I read the readme text and it said I CMake which I also got from sourceforge but i have no idea how to install either program.
First off why do I need CMake to run LMMS?
Secondly I need step instructions on how to install this baby. 

If you help I will send you the mad beats I make with this baby!

---

### Post by mc4man on 2009-01-26
If your running Intrepid a .deb is available here
[https://launchpad.net/~tobydox/+archive](https://launchpad.net/~tobydox/+archive) (change the source list drop down to intrepid

Some claim you can use the intrepid packages on hardy, I don't know.

Otherwise here is recent thread (for building on hardy

[http://ubuntuforums.org/showthread.php?t=1046909](http://ubuntuforums.org/showthread.php?t=1046909)

---

### Post by vaughnm on 2009-01-26
I really have no idea how to do any of this. I looked at sources.list but they are just folders. I don't know which folders to download and why!

Plus I have no idea how to build on hardy. 
 
I just want to run this program, why does it have to be so complicated? and why isn't is the add/remove terminal? It would be so much easier if it self installed. 

A noobie in need. Thanks

---

### Post by Patrick793 on 2009-01-26
Do the following.

Open a terminal.

enter this:
```
gksudo gedit /etc/apt/sources.list
```
At the end of the file, add this.
```
deb http://ppa.launchpad.net/tobydox/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tobydox/ubuntu intrepid main
```
Save the file, and close Gedit. Back in the terminal enter this.
```
sudo apt-get update
```
```
sudo apt-get install lmms-common lmms lmms-extras
```
LMMS is now installed.

---

### Post by mc4man on 2009-01-26
Just to double ck. You are running hardy? (8.04)

If so there is a hardy version available, why don't you try it first and  then if you want the updated, current 0.4.2 version we'll set you up.

To install lmms
Open a terminal (Applications -> Accessories -> Terminal

Copy and paste this into the terminal box and press enter

```
sudo apt-get install lmms
```


If your running Intrepid (8.10) say so and I'll show you how to add the repo from the link (or if you want to try to install the intrepid version on hardy

Edit : above post shows how to add repo for intrepid (8.10

---

### Post by vaughnm on 2009-01-26
Ok, thats great
I went to the terminal and put in the code

It installed but I can't find it to run.
Is there a way I can make a icon for it? 
I don't even know where it installed to.

Sorry for being such a noob I just get confused when you have to manual install because I can never find it in my applications. Thanks

And yes it is Hardy I'm using

---

### Post by vaughnm on 2009-01-26
Hey, great news... I got it working now! 

I read some other posts and got the shortcut problem solved. 
Pretty simple but I just needed some guidance. 

Thanks a lot for all your help guys. I'll come back to post a link to my beats once I got some down :p

for now check out 
[www.myspace.com/whyremember]("www.myspace.com/whyremember")

:guitar:

---

### Post by mc4man on 2009-01-27
If you decide you want to upgrade to the latest stable 0.4.2 release there's a mediafire link in the other post for a .deb. You have to do 3 specific things first before installing. It's all laid out there. (if so, any questions about how, ask first.

There's also a method to create a proper menu item if needed. (the copy and paste into text file way would be best.

Wouldn't know the difference between the hardy 0.3.2 version and the 0.4.2 one but the gui/setup for 0.4.2 looks 'better'

[http://ubuntuforums.org/showthread.php?p=6595852#post6595852](http://ubuntuforums.org/showthread.php?p=6595852#post6595852)

---

### Post by simtaalo on 2009-01-27
stability is a big difference between 0.3.2 and 0.4.2.

join us in the irc room on freenode ##lmms

see you in there :)

---

### Post by renesisspeed on 2009-02-09
Woohoo! Source list :-) thnx mc4man. That did the trick. Was lookin for that.

---

