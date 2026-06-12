---
title: "Wireless with 600m &amp; XFCE"
date: 2008-01-04
forum: Dell  Ubuntu Support
---

### Post by wmgobuffs on 2008-01-04
Hello,
I am running 7.04 and GNOME on my Inspiron 600m with 1GB RAM, and wanted to experiment with using the XFCE environment when I need to maximize my battery life.  Only thing is, I can't figure out how to connect via WiFi in XFCE.  I can't check 'on' the wireless card from Network Manager, and I also get no response from Fn+F2.  Is this a known problem?  Wireless works swimmingly from the GNOME side, so should I really look into installing new drivers for the XFCE environment? 
Thanks for your advice.

---

### Post by luisg on 2008-01-04
I'm having a similar problem with Gutsy and Gnome, Fn+F2 doesn't work (it used to work in Feisty). Try this: while in Grub menu, press once Fn+F2, then start Ubuntu.

---

### Post by ugm6hr on 2008-01-05
> **wmgobuffs said:**
> Hello,
I am running 7.04 and GNOME on my Inspiron 600m with 1GB RAM, and wanted to experiment with using the XFCE environment when I need to maximize my battery life.  Only thing is, I can't figure out how to connect via WiFi in XFCE.  I can't check 'on' the wireless card from Network Manager, and I also get no response from Fn+F2.  Is this a known problem?  Wireless works swimmingly from the GNOME side, so should I really look into installing new drivers for the XFCE environment? 
Thanks for your advice.

Try adding this to your autostarted applications in XFCE:
```
nm-applet --sm-disable
```

---

### Post by wmgobuffs on 2008-01-05
> **ugm6hr said:**
> Try adding this to your autostarted applications in XFCE:
```
nm-applet --sm-disable
```

This did the trick!  Could you explain why I need this and/or what is going on under the surface?  And do you think that running the XFCE desktop will help conserve laptop battery?

---

### Post by ugm6hr on 2008-01-05
> **wmgobuffs said:**
> This did the trick!  Could you explain why I need this and/or what is going on under the surface?  And do you think that running the XFCE desktop will help conserve laptop battery?

Network Manager is the wifi GUI for Ubuntu Feisty (Gnome), but Xubuntu Feisty only has Network Monitor, which can't scan for wifi networks (have to manually enter details) and does not have WPA support.  I gather Xubuntu Gutsy now uses Network Manager as well (but I haven't used it).  Since you installed Ubuntu Gnome first, you have Network Manager on your installation, but it was not being run when you used a XFCE session.  The command merely ensures that XFCE starts network manager (nm-applet) as well.  As for *sm-disable*, I have no idea what that does, but it is the option used to run NM in Ubuntu Gnome.

As for laptop battery, I don't think it will give you any longer battery time, although since everything should run a little faster, you might get more done in the same amount of time!

---

