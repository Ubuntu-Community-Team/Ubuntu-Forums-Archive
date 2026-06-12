---
title: "gnome-rdp does display group names in Lucid Lynx"
date: 2010-05-10
forum: Desktop Environments
---

### Post by MSPdwalt on 2010-05-10
Hey all,

I recently updated to Ubuntu Lucid Lynx from Karmic (fresh install though).  All of the packages I used in Karmic seem to work nicely in Lucid, with one exception gnome-rdp.  

I'm a sysadmin in several windows environments so as you can imagine I love the session storage and grouping features.  Unfortunately gnome-rdp is not displaying the group names. it stores my session and creates the group structure just fine, it just doesn't show me the group names in the app or the right-click menu on the top panel icon.

[IMG]http://www.imagebanana.com/view/ff5qdsbx/GnomeRDP_002.png[/IMG]

My gut says it has something to do with the new Lucid theme, but I like the new theme.  Does anyone know of a config file I can edit, or something I can do to disable theme integration, just for gnome-rdp?

Thanks in advance,

DW

---

### Post by thirdgen88 on 2010-05-10
The solution to your problem might very well be found through the use of Remmina instead.

```
sudo apt-get install remmina remmina-gnome
```

This program gives you the ability to group your sessions (and two modes for visualization, I prefer the Tree view).  It also gives you much better control over your session once it is started.  Once you use it, you'll wonder how you ever managed with anything else.  Plus, with remmina-gnome, you get a nice panel applet for quick access to your stored sessions.

---

### Post by MSPdwalt on 2010-05-10
Dude...this is awesome, you are a life saver, come to Minneapolis and I will buy you a beer.  I am having one problem with it though, the applet doesn't seem to be showing up....any suggestions there?

And while I'm picking your brain can you recommend an ssh/telnet app or terminal emulator that can store sessions and turn text capture on/off on the fly?

I also manage a ton of cisco devices, our change control procedures require us to capture show version, show vlan, and show run before and after any changes.  When I ran windows I used SecureCRT and visionapp RDP.  remmina replaces visionapp quite nicely, but I have yet to find something close to secureCRT.

Currently I have putty sessions saved and set to log output.  I log in with putty, take my caps, login with ssh from gnome-terminal make my changes because copy paste is much easier than putty, then I login with putty again and take my caps.  (not very efficient)

Apparently SecureCRT runs well through WINE, but my goal with this "project" is to run as many apps as I can natively.

Thanks again for the help,

DW

---

### Post by MSPdwalt on 2010-05-10
Ok, scratch that part about the applet not working, you just have to manually add it to the panel.

---

