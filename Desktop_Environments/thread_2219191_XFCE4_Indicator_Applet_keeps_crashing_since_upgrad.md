---
title: "XFCE4 Indicator Applet keeps crashing since upgrade to Trusty"
date: 2014-04-23
forum: Desktop Environments
---

### Post by halfbeing on 2014-04-23
Since upgrading to Trusty yesterday my XFCE Indicator Applet no longer works. I can insert it in the panel and get it to work for a few seconds (all my indicators show up), but then it crashes. Anyone any idea what's going on?

---

### Post by Krytarik on 2014-04-23
> **halfbeing said:**
> all my indicators show up
Does that include Indicator AppMenu? Bug report here:

[https://bugs.launchpad.net/ubuntu/+source/unity-gtk-module/+bug/1307657](https://bugs.launchpad.net/ubuntu/+source/unity-gtk-module/+bug/1307657)

Regards.

---

### Post by halfbeing on 2014-04-23
Thanks for replying to my post :)

> **Krytarik said:**
> Does that include Indicator AppMenu? Bug report here:

[https://bugs.launchpad.net/ubuntu/+source/unity-gtk-module/+bug/1307657](https://bugs.launchpad.net/ubuntu/+source/unity-gtk-module/+bug/1307657)

Regards.

I'm not sure what I'm supposed to be looking for. I had trouble understanding that bug report. I have just enabled the Indicator Applet again and this time it has been going for a few minutes and hasn't crashed yet. However I also, earlier today, logged into as different user account that I just keep for troubleshooting problems like these, and all the indicators that were supposed to be there showed up without the help of the Indicator Applet. So there is obviously something specific about the way my own user account is set up that makes it slightly incompatible with XFCE in Trusty.

---

### Post by gabbello on 2014-04-30
I have the same problem. I've added Indicator Applet because several icons (skype, network manager, etc) are missing from the Notification Area applet so I was hoping I could use this one to have the icons there. Unfortunately it does not work.

---

### Post by halfbeing on 2014-04-30
> **gabbello said:**
> I have the same problem. I've added Indicator Applet because several icons (skype, network manager, etc) are missing from the Notification Area applet so I was hoping I could use this one to have the icons there. Unfortunately it does not work.

I have got my indicators working now. What you need to do is to go into the indicator applet properties and hide application menus. Obviously once the indicator applet is working it is easy to get into the properties by right-clicking. What I can't remember is how I managed to get to the properties while the applet wasn't working. Perhaps it was during the brief window between launching the panel and the indicator applet crashing. Presumably there's a config file somewhere that you can edit.

---

### Post by gabbello on 2014-04-30
It seems I managed to make this to not crash by installing all xfce-goodies package: **apt-get install xfce4-goodies**.

Now the indicator-applet seems stable (but I just did this 5 minutes ago). Yes, once it is stable enough you can hide the app. menus from applet config. section. Also, for me in order for the config to be applied I had to logout/login.

---

