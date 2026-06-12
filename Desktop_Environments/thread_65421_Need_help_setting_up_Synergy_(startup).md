---
title: "Need help setting up Synergy (startup)"
date: 2005-09-13
forum: Desktop Environments
---

### Post by FlameboyC11 on 2005-09-13
Well, I've compiled and done "make install" and synergy runs fine, except I have one problem. How to I get it to run on startup? I've searched through google and these forums and the terms are too generic to get anything of any use. I feel quite stupid but the faq for synergy doesn't really help due to the fact that the files it says to edit aren't there. I need synergy running at the login screen as well as for my session due to it's nature (it's a KM switch using a network). Here's a link to the way they suggest setting up synergy:

[http://synergy2.sourceforge.net/autostart.html](http://synergy2.sourceforge.net/autostart.html)

Thanks so much!

---

### Post by rgrosz on 2005-11-04
Did you ever get it working?

I am having the same problem - I hate having to drag out the second keyboard to login, then run synergy. I'm thinking of installing VNC as a workaround.

I have Googled, searched all sorts of Q&A, and no answers for doing this on Ubuntu. I found one fairly specific thread (very long), but it was mostly on Fedora. The directory structure seems quite different than Ubuntu:
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=163113](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=163113)

EDIT:
I am SURE the answer is in the Wiki:
[https://wiki.ubuntu.com/SynergyHowto](https://wiki.ubuntu.com/SynergyHowto)

It will take a while to digest this ...

---

### Post by Dragon5000 on 2008-05-06
Hey guys! Apologize in advance for any n00bz-worthy mistake, but that's what I am: a n00b!!!! However, I did follow the instructions from [https://wiki.ubuntu.com/SynergyHowto](https://wiki.ubuntu.com/SynergyHowto) (thanks a bunch rgrosz!), and everything is just peachy! Synergy starts when X starts (so you can use the server's mouse/kb to login) and then it quits/restarts for the user session. What you want to do is follow the instruction under the section titled "Server Autostart at login screen, GDM" and apply the first part (On the client) to your client box. I followed those steps-by-step, and now I'm happy!:) 
This is my setup:
Windows XP SP2 - Server 
Ubuntu Gutzy - Client 
I haven't tried the "For the Server" part because the server is my Windows box. I've tried restarting X a few times and restarting the whole client: synergy kicked back in as it was supposed to every time!
Hope this helps!
-Dethklok rules!-:guitar::lolflag:

---

