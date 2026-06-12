---
title: "Use gui to set up and then run without later?"
date: 2013-01-23
forum: Desktop Environments
---

### Post by Norsehound on 2013-01-23
I am brand new to using linux(migrated from OS X and WIndows 7). I decided to use an old computer to set up a minecraft server for my friends and I. I am currently running ubuntu server without gui(hopefully for better speed). So far so good, but the command prompt really takes some getting used to (not to worry, I plan on learning it. Picked up some books and am well on my way). My questions are; can you install a gui in ubuntu server, and can you use a gui to set up the computer the way you like (ie static ip, etc) and then run the os in command line only(no gui mode, or something) when i get everything set up right? If so will it be as efficient as if you never installed the gui in the first place? Thank you for the responses in advance! Much appreciated =)

---

### Post by drdos2006 on 2013-01-23
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. Based on Debian so just change the OS name to Ubuntu as you already have Ubuntu set up.

Allows your local browser to connect and modify your server settings on your network, start and stop processes, change permissions etc.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.610_all.deb

Install with :
sudo dpkg -i webmin_1.610_all.deb

Add extra libraries with :
sudo apt-get -f install

```


regards

---

### Post by TheFu on 2013-01-23
> **Norsehound said:**
> I am brand new to using linux(migrated from OS X and WIndows 7). I decided to use an old computer to set up a minecraft server for my friends and I. I am currently running ubuntu server without gui(hopefully for better speed). So far so good, but the command prompt really takes some getting used to (not to worry, I plan on learning it. Picked up some books and am well on my way). My questions are; can you install a gui in ubuntu server, and can you use a gui to set up the computer the way you like (ie static ip, etc) and then run the os in command line only(no gui mode, or something) when i get everything set up right? If so will it be as efficient as if you never installed the gui in the first place? Thank you for the responses in advance! Much appreciated =)

You can setup a desktop to be a server and you can setup a server to  be a desktop. There are slight differences in the way each starts other  programs occasionally. Sometimes - probably most of the time, there isn't any difference.

This is a tough question - especially when it comes to network stuff.  The normal desktop handles networking using something called *Network Manager.* The server does not use this, though if you load a desktop GUI, like Unity, onto your server, then you will get it.  Whether that is a good idea or not is up to personal opinion.  I don't even know if it will work on a server install. The initialization scripts are different after all.  

Even on desktops, I prefer to not use NM - seems like too much black magic to me. I want to absolutely KNOW what my networking does on a server. 100%, no questions, KNOW.  I think many of those desktop configured settings only get run after the user logs in. That is bad for a server. Most of my servers automatically run all the things I need at boot - i.e. no need to login at all.  I have servers that have been running for months that I haven't logged into manually the entire time.  Their patching and backups all happen automatically. As long as there isn't any issue, I don't login.

For server configuration, I think that you will find there aren't many GUI tools. There are web-interface tools like **webmin**, but I find those extremely dangerous since any bug in the tool or if you accidentally allow the interface onto the internet, then your entire infrastructure could be at risk.  You need to decide where convenience and security meet for yourself.

I would suggest that you find a mentor to help you learn to setup servers. Everyone does it just a little differently based on their personal history. Some companies use "golden images" to handle things.  I might setup 20 servers a year, to spending time to have an image isn't worth it to me.  Setting up a static IP is one of the first things I do on every server ... just after I purge, **with all possible prejudice**, nano.  vi is the editor to be used on a server. I consider nano a security risk - for a "script kiddie."

Also learn to use the **man **command to get help.  Man pages are available for almost every command on the system. Knowing how to find them and read them IS A CRITICAL skill.  **man man** will explain everything, but **man ls** is a good into. **man ssh** will blow you away. It is THAT good. I learn something new every time.

Here's a guide that lists the first things I do to setup servers: [http://blog.jdpfu.com/2012/04/28/first-look-at-ubuntu-12-04-server-into-virtualbox-vm](http://blog.jdpfu.com/2012/04/28/first-look-at-ubuntu-12-04-server-into-virtualbox-vm) . I hope it helps.

I have loaded a limited desktop onto a server install a few times.  This was because I wanted to use the system as a desktop for development, but avoid the normal desktop packaged bloat, especially all the extra stuff that gets loaded automatically.  On a server, I'll often only have 512MB of RAM. That really isn't enough for a desktop.  I have used LXDE, but the controls for networking don't seem to exist in that GUI, so it isn't what you probably want.  Sometimes I'll load just **fvwm **when I need a really light GUI - but that only provides a limited X/Windows environment with a tiny window manager, none of the extra, Unity-like, stuff or all those apps that I'll never use.  I doubt you are ready for that based on your question.

Hopefully, some smart people will respond with different opinions. It is good to hear from lots of people on stuff like this.

---

### Post by Ranko Kohime on 2013-01-24
A good halfway point that I am using for my server, (which was running Ubuntu-desktop until I purged all of the Unity, LightDM and Xorg packages), is to keep GUI configuration programs, and run them via X11 forwarding on SSH from my laptop.

Best of both worlds.  :)

If you're unfamiliar with X11 forwarding, check out [this page]("http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html"), and [this one]("http://anarchic-order.blogspot.com/2011/03/ssh-x11-and-you.html").

---

### Post by Norsehound on 2013-01-24
Awesome stuff so far guys. Truly appreciated! I will delve further into those man pages and continue plugging away until I get this all figured out!

---

### Post by dannyboy79 on 2013-01-24
to answer your original question, YES. simple install a desktop manager of your choice. if you want something lightweight go with xubuntu-desktop. then you can make remove it if you want or even have it so that it doesn't start a desktop manager like my server.

---

### Post by Norsehound on 2013-01-24
Thanks dannyboy79. That is exactly what I was looking for. You wouldn't happen to know where I may look for a tutorial or walkthrough on that? I attempted something similar on my first install. After i attempted to uninstall the gui, the system would no longer boot into the command line or the gui(it had obviously been removed)

---

### Post by TheFu on 2013-01-24
> **Norsehound said:**
> Thanks dannyboy79. That is exactly what I was looking for. You wouldn't happen to know where I may look for a tutorial or walkthrough on that? I attempted something similar on my first install. After i attempted to uninstall the gui, the system would no longer boot into the command line or the gui(it had obviously been removed)

To install xfce with all the bells and whistles:
```
sudo apt-get update
sudo apt-get install xubuntu-desktop

```
But that is a bunch of bloat.
Instead of the 2nd command (the first is needed every day before installing anything), use 
```
sudo apt-get install xfce
```

These are all terminal commands and assume your user account has sudo privileges. I've use xfce and it is not bad, though I prefer LXDE, which would be
```
sudo apt-get install lxde
```
Do you see the pattern here?

How to disable it later will be a different question. I simply don't know right now, but you can change the startup to be anything you like by modifying a few text files.

I think you will be disappointed. Server controls don't really come with GUIs.  Desktop stuff does.

---

### Post by dannyboy79 on 2013-01-24
after you're done using xubuntu GUI and what not, you can choose to remove it using the following website as a guide.
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

OR you can just set runlevels so that the desktop manager isn't even started but it's there in case you want to boot to a GUI in the future.

Currently my Xubuntu 10.04 server is headless, meaning I administer it thru ssh BUT when I do have tasks that require a gui I can attach a monitor, log into tty1 terminal command line, then just issue startx and it fires up my desktop manager. Good luck

---

### Post by Norsehound on 2013-01-24
That is brilliant stuff guys! A big thanks to all involved, particularly dannyboy79 and TheFu! I am currently installing LXDE using "sudo apt-get install lxde" and will investigate using runlevels to keep the gui nearby if needed, but not sucking resources on the day to day.

---

### Post by dannyboy79 on 2013-01-24
i think there's some more help here if interested. [http://ubuntuforums.org/showthread.php?t=1193204](http://ubuntuforums.org/showthread.php?t=1193204)

---

