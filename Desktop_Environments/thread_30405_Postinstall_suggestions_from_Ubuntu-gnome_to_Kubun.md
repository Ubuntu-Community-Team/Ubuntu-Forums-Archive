---
title: "Postinstall suggestions from Ubuntu-gnome to Kubuntu-kde?"
date: 2005-04-28
forum: Desktop Environments
---

### Post by crazybill on 2005-04-28
From reading through Kubuntu, I decided to convert some of my Gnome desktop Ubuntu machines to Kubuntu machines... which I have done on serveral and am doing with a few more via **apt-get install kubuntu-desktop**.

**_Background:_**
There must be quite a few folks who visit this forum who have done this before me. I have not used KDE before. Mostly I have used  Linux/BSD/Unix with barebones processes on the 18 servers on our  networks (primarily openBSD and freeBSD -- used them for years). Most of my work on Unix-type computers has been though SSH connections with Putty and WinSCP. I set up the servers and seldom thereafter ever visited the machine except for remote administration. I have given my annual try to  some Linux flavors each year (there are about 300 of them now), but I was never really satisfied. I then gave Ubuntu a try as server and workstation with -- wow!--  nice results... but I have been using the Gnome desktop. I am now jumping into Kubuntu.

**_Inquirey_**:
Being totally ignorant of KDE at this point.  A few questions if anyone can give me an answer:
1. What is the equivalent on KDE with Gnome's "killall gnome-desktop"?
2. After rebooting into KDE, I noticed the overall superficial appearance of my KDE desktop in Kubuntu looks the same as Gnome in Ubuntu.  The Applications/Places/System menus are still in the upper bar with some KDE apps added with no icons.
      a.  Can icons in that list that KDE added be changed? How?
      b.  What modifications to the old Gnome appearance do most of you do?
      c.   Are there any other finishing touches that should be done (deleting, adding, editing) to finish the conversion from Ubuntu-Gnome to Kubuntu-KDE.

I look forward to reading your replies.

---

### Post by philipacamaniac on 2005-04-28
Whoops - it sounds like you're still in Gnome, but now you have KDE apps on the Applications menu. KDE doesn't look at all like Gnome. It has a panel at the bottom of the screen, with a "K" menu. In the login screen, make sure you choose a "KDE" session.

If you want to remove Gnome, you should **apt-get remove ubuntu-desktop**. 

When you are using KDE, the "K" menu can be directly edited with the K Menu Editor (simply right click it).

---

### Post by crazybill on 2005-04-28
KDE was selected as the default when I set up **apt-get install kubuntu-desktop**. On reboot before logging in, I made sure KDE was selected. However,  since there is no K-panel on the bottom, I am taking your suggestion and doing:
**apt-get remove ubuntu-desktop. ** 

followed by:

 **apt-get install kubuntu-desktop** again.

I will post the results.

---

### Post by crazybill on 2005-04-28
It worked to do 
**apt-get remove ubuntu-desktop** .

Without doing that KDE would not setup.

Now that I actually see what KDE is like, that brings more post-setup questions.

1.  My sound no longer works, on bootup, it says it can not find /dev/dsp    Does KDE change that?

2. Firefox still works fine, but Konqueror will not show flash. When I try to install macromedia flash for conqueror, I do not know the path. It rejects /usr/lib/kde3. Does anyone know the lib path for konqueror ... or where the flashplugin should be installed?

3. Where in KDE can I change my static network addressing? ... or do I have to use the terminal and go to the /etc files?  (In Gnome it was easy to do, so it must be so in KDE. I just don't know what it is.)

Thanks for any replies

---

### Post by philipacamaniac on 2005-04-29
2. I just tried the Flash installer from macromedia.com, and it does the same thing for me when installing as root. It doesn't recognize any path! So it seems there is a problem with their installer and (k)ubuntu. IMHO, you should use Firefox anyway. I don't want to start a flame war, but there are a lot of sites that won't render correctly in Konqueror, but look great in Firefox. Even Gmail has problems in Konqueror (it can only open in plain HTML mode). KHTML is good, but has a long way to go. (Safari uses the same engine, but Apple has added a ton of code that hasn't been backported into Konqueror.)

3. In the Control Center, go to Internet & Network --> Network Settings. You'll have to click Administrator Mode*, and then click the "Configure Interface..." button.


*Sometimes pressing the Administrator Mode button doesn't work in Control Center. I haven't figured out the problem (possible bug), but to get where you need to go, run Control Center as root instead. On the K Menu, choose "Run Command" and select "Options". Highlight "Run as a different user" and type in your sudo password. Then in the command box type "kcontrol" and click "Run". This will open an Administrator Mode Control Center (owned by root).

---

### Post by fdejkmtruds on 2005-05-03
[QUOTE=crazybill]
1. What is the equivalent on KDE with Gnome's "killall gnome-desktop"?
[/QUOTE]
Don't know. I've never needed to kill KDE before

[QUOTE=crazybill]
      a.  Can icons in that list that KDE added be changed? How?
[/QUOTE]
the "K" menu can be directly edited with the K Menu Editor (simply right click it). Don't forget to save the changes


[QUOTE=crazybill]
for konqueror ... or where the flashplugin should be installed?
[/QUOTE]

The files flashplayer.xpt and libflashplayer.so can be installed in
~/.netscape/plugins/ or /usr/lib/netscape/plugins or /usr/lib/mozilla/plugins 

OR

You can open up a new konqueror window. 
In the menubar select Settings -> Configure Konqueror. 
Scroll down to plugins
Inside the Netscape Plugins area click the "New" button.
Type in the location where you placed the flashplayer.xpt and libflashplayer.so files

---

