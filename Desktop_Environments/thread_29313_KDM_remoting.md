---
title: "KDM remoting"
date: 2005-04-23
forum: Desktop Environments
---

### Post by AcynoniX on 2005-04-23
Greetings.

i want to log in my new linux Kubuntu from my Windows Desktop, and my Mac Desktop...

VNC is not a solution for me, it's slow and well colors suck.

I used to be able to log in to my Redhat remotely using an X server for windows, i wish i could configure Kubuntu to od the same. i cant seem to find the configuration files do do this 
 can anyone help me out ? \\:D/ 

thank you all . 
AcynoniX

---

### Post by moopere on 2005-04-23
[QUOTE=AcynoniX]Greetings.

i want to log in my new linux Kubuntu from my Windows Desktop, and my Mac Desktop...

VNC is not a solution for me, it's slow and well colors suck.

I used to be able to log in to my Redhat remotely using an X server for windows, i wish i could configure Kubuntu to od the same. i cant seem to find the configuration files do do this 
 can anyone help me out ? \\:D/ 
AcynoniX[/QUOTE]

What we/KDE needs is a nice KDM configuration program like gdmsetup.  The Control Center thing (system administration->login manager) seems to always have been full of stuff I don't care about but ont have any of the interesting settings I want to use (like xdmcp, and various root settings)

Anyway, I'm getting distracted, the file(s) you want are located in /etc/kde3/kdm/kdmrc

Its a big huge messy text file full of a zillion options of which only a handful will interest most tweakers.

Cheers,
Craig

---

### Post by AcynoniX on 2005-04-24
moopere, 

Thank you for the info! and I totaly agree with you.

I dont understand how any distro out there can claim to be ready for the Desktop
when they lack such simple power tools. I understand that practicaly no one will have a need for this feature, BUT, being on the desktop also means providing tools for the advance users with the most weird setups.

Mac does it, Windows does it, GNOME does it
I dont see why KDE cant do it.

(Providing a simple configuration interfaces to the power features provided by your own software seems to fall into simple logic to me)

But hey, i'm just a programmer, dont take my word for it.

---

