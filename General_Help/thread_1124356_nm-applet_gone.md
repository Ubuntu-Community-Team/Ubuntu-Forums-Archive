---
title: "nm-applet gone"
date: 2009-04-13
forum: General Help
---

### Post by tpost001 on 2009-04-13
I am using Ubuntu 8.04.2 LTS.

Somehow I lost the nm-applet on my upper panel.  It is the one with the 4 bars that tell you how strong your wireless internet connection is.  It also has a list of networks so you can select what you want and lets you know what your network IP address is.  

When I right click the panel and select Add to Panel I get a window called Add to Panel.  There is a huge list of applets to choose from.  There is one called Network Monitor, but its not the same.  It tells me I have a connection, but no selector.  I cannot switch between networks (I have two at my home/office).

In Applications -> Internet I added Network Selector.  When I click on that nothing happens.  When I click on its Properties, I see that it is activated by netapplet.  So in a terminal window (as root) I typed netapplet and I got:

root@hp-laptop:~# netapplet

(netapplet:6852): Gtk-WARNING **: cannot open display: 
root@hp-laptop:~# 

I noticed that someone had this same problem in 2006 "nm-applet gone awol" but the solution was to right click the upper panel, select Add to Panel, and the select Utilites and more.  I am assuming that 8.04 is different because when I add to panel, I just get that window I mentioned above.

Can anyone help me get the 4 bars back?

---

### Post by 3rdalbum on 2009-04-13
The actual network manager is a program called "nm-applet" that sits inside a Gnome panel applet called "Notification Area".

So, try running "nm-applet" in the Alt-F2 run dialog, and if that doesn't appear to do anything then you might need to add the Notification Area applet to your panel.

---

### Post by tpost001 on 2009-04-13
I tried your suggestion.  Nothing happened.  How do I reinstall the Notification Area?

---

### Post by tpost001 on 2009-04-13
I found it.  Thanks.  When I installed the Notification Area, I got three nm-applets; probably from every time I tried before.  HOw do I get rid of the extras?  It does not allow me to right-click and "remove from panel".

---

### Post by plucky on 2009-04-13
> **tpost001 said:**
> I found it.  Thanks.  When I installed the Notification Area, I got three nm-applets; probably from every time I tried before.  HOw do I get rid of the extras?  It does not allow me to right-click and "remove from panel".

**System > Administration > System Monitor** and select **Processes** tab and kill two of the nm-applet processes.


Good Luck

---

### Post by tpost001 on 2009-04-13
Great idea!  Why didn't I think of that?  Elegant.  I could not see the forest for all the trees in the way.  Well, it is solved.  Thanks to all.  I also wrote a How-To in this forum:  [ubuntu] network manager applet...

---

