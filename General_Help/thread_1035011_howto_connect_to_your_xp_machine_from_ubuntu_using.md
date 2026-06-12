---
title: "howto connect to your xp machine from ubuntu using gnome-rdp - what works for me"
date: 2009-01-09
forum: General Help
---

### Post by Old Jimma on 2009-01-09
Hi Ubuntu Community:

I see alot of discussion on problems with connecting to an xp machine from ubuntu. Everytime I upgrade my machine, I run into problems with it also, and have to start from scratch learning how to connect to my xp machine from my dear Ubuntu machine.

Here is the step-by-step instructions on what works for me.

To set up remote desktop on xp:
[http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx](http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx) and follow instructions to 
1.allow remote desktop on xp, 
2.allow exceptions on xp firewall, and 
3.learn what your xp computer name is.
4.Open a command window with c: prompt
5.type: ipconfig
6.write down the ip address of the xp computer

To set up gnome-rdp on ubuntu:
1.install gnome-rdp from synaptic
2.applications > internet > gnome-rdp
3.click NEW.
4.In session name, put a nice name for the computer, like “xp machine” or the name of your high-school mascot... the choice here doesn't seem to matter too much.
5.In the computer box type in the ip address of the xp machine
6. leave the computer name and password BLANK.
7.click ok.
8.In the gnome-rdp box, highlight the session name you just created by clicking once on it.
9.Click connect.

This should get you into your xp machine. At this point, you may need to provide xp with your username and password to start an xp session.

In the gnome-rdp window, if you click on your session name > properties > RDP icon, you can adjust the size of the window size of your session. I set remote desktop size to custom and select 1270x920 for my terminal. You probably will want to experiment with this to customize it exactly to your own preferences.

I sure hope this helps somebody. The forums have helped me alot in my journey!

Best regards,
Phil Smith
Duluth, GA

---

### Post by lazyart on 2009-01-09
Or, just go to Applications>Internet>Terminal Server Client

Select RDP as your protocol and connect away.

---

### Post by HunterK on 2009-01-09
is gnome-rdp just a GUI for rdesktop?

---

