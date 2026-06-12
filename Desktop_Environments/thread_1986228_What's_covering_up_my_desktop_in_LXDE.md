---
title: "What's covering up my desktop in LXDE?"
date: 2012-05-24
forum: Desktop Environments
---

### Post by Kansasguy on 2012-05-24
On two computers, a Dell with Ubuntu 12.04, and my ASUS netbook with Kubuntu 10.04, I have installed LXDE core, it's Great, especially for my friend with the old Dell, very intuitive, simple and fast.

Last night I was trying to modify mine and ended up with (what I think is) the unity desktop on mine, and want to get rid of it.  I can't see the beautiful (and simple) blue desktop.  What is on top can be seen at the Google image located at:


[http://www.google.com/imgres?um=1&hl=en&sa=N&biw=1117&bih=513&tbm=isch&tbnid=KnIBugfzNhgbIM:&imgrefurl=http://www.ghacks.net/2010/10/26/install-and-use-ubuntu-unity-before-its-released/&docid=1j2zqBjCL9xTiM&imgurl=http://cdn.ghacks.net/wp-content/uploads/2010/10/unity.png&w=1280&h=800&ei=pHG-T6S-Msisgwf74b39Aw&zoom=1&iact=hc&vpx=110&vpy=223&dur=4167&hovh=177&hovw=284&tx=183&ty=134&sig=113720459057540563216&page=1&tbnh=149&tbnw=224&start=0&ndsp=8&ved=1t:429,r:4,s:0,i:83](http://www.google.com/imgres?um=1&hl=en&sa=N&biw=1117&bih=513&tbm=isch&tbnid=KnIBugfzNhgbIM:&imgrefurl=http://www.ghacks.net/2010/10/26/install-and-use-ubuntu-unity-before-its-released/&docid=1j2zqBjCL9xTiM&imgurl=http://cdn.ghacks.net/wp-content/uploads/2010/10/unity.png&w=1280&h=800&ei=pHG-T6S-Msisgwf74b39Aw&zoom=1&iact=hc&vpx=110&vpy=223&dur=4167&hovh=177&hovw=284&tx=183&ty=134&sig=113720459057540563216&page=1&tbnh=149&tbnw=224&start=0&ndsp=8&ved=1t:429,r:4,s:0,i:83)

(or put unity desktop in Google images and find the one with the leaf on the desktop)

What did I do?   and how can I get rid of it.  Thanks

---

### Post by wilee-nilee on 2012-05-24
> **Kansasguy said:**
> On two computers, a Dell with Ubuntu 12.04, and my ASUS netbook with Kubuntu 10.04, I have installed LXDE core, it's Great, especially for my friend with the old Dell, very intuitive, simple and fast.

Last night I was trying to modify mine and ended up with (what I think is) the unity desktop on mine, and want to get rid of it.  I can't see the beautiful (and simple) blue desktop.  What is on top can be seen at the Google image located at:


[http://www.google.com/imgres?um=1&hl=en&sa=N&biw=1117&bih=513&tbm=isch&tbnid=KnIBugfzNhgbIM:&imgrefurl=http://www.ghacks.net/2010/10/26/install-and-use-ubuntu-unity-before-its-released/&docid=1j2zqBjCL9xTiM&imgurl=http://cdn.ghacks.net/wp-content/uploads/2010/10/unity.png&w=1280&h=800&ei=pHG-T6S-Msisgwf74b39Aw&zoom=1&iact=hc&vpx=110&vpy=223&dur=4167&hovh=177&hovw=284&tx=183&ty=134&sig=113720459057540563216&page=1&tbnh=149&tbnw=224&start=0&ndsp=8&ved=1t:429,r:4,s:0,i:83](http://www.google.com/imgres?um=1&hl=en&sa=N&biw=1117&bih=513&tbm=isch&tbnid=KnIBugfzNhgbIM:&imgrefurl=http://www.ghacks.net/2010/10/26/install-and-use-ubuntu-unity-before-its-released/&docid=1j2zqBjCL9xTiM&imgurl=http://cdn.ghacks.net/wp-content/uploads/2010/10/unity.png&w=1280&h=800&ei=pHG-T6S-Msisgwf74b39Aw&zoom=1&iact=hc&vpx=110&vpy=223&dur=4167&hovh=177&hovw=284&tx=183&ty=134&sig=113720459057540563216&page=1&tbnh=149&tbnw=224&start=0&ndsp=8&ved=1t:429,r:4,s:0,i:83)

(or put unity desktop in Google images and find the one with the leaf on the desktop)

What did I do?   and how can I get rid of it.  Thanks

You choose the desktop at the login window, from the gear dropdown next to where the password goes.

---

### Post by rai4shu2 on 2012-05-24
Have a look at /var/log/apt/history.log and see if anything looks suspicious (especially toward the bottom of that file).

---

### Post by Kansasguy on 2012-05-24
Thanks to you both.  I understand that I choose the session type at the login screen (it worked great for a while, and is doing well on my friends old Dell).  I'm sure I messed it up somehow trying to be "creative" and experimenting.  Did I open "openbox" or whatever it's called?

from the history below, I did try to fix the problem by uninstalling it last night at about 11pm and re installing it about 2 minutes later.

Thanks again,

Start-Date: 2012-05-19  21:31:12
End-Date: 2012-05-19  21:31:26

Start-Date: 2012-05-19  21:32:48
End-Date: 2012-05-19  21:32:52

Start-Date: 2012-05-19  21:33:57
End-Date: 2012-05-19  21:34:02

Start-Date: 2012-05-22  17:37:31
Install: libobrender21 (3.4.10-1ubuntu0.1), lxsession (0.4.3-0ubuntu1), libobparser21 (3.4.10-1ubuntu0.1), openbox-themes (1.0.2), xscreensaver (5.10-3ubuntu4), lxde-common (0.5.0-3ubuntu2), pcmanfm (0.5.2+svn20091029-1ubuntu3.1), lxde-core (0.5.0-3ubuntu2), openbox (3.4.10-1ubuntu0.1), lxmenu-data (0.1.1-1), lxpanel (0.5.5-0ubuntu2), libjpeg-progs (7+really6b-15ubuntu1), libmenu-cache1 (0.3.2-0ubuntu1)
End-Date: 2012-05-22  17:38:21

Start-Date: 2012-05-23  13:31:35
Upgrade: python-libxml2 (2.7.6.dfsg-1ubuntu1.4, 2.7.6.dfsg-1ubuntu1.5), libxml2 (2.7.6.dfsg-1ubuntu1.4, 2.7.6.dfsg-1ubuntu1.5), libxml2-utils (2.7.6.dfsg-1ubuntu1.4, 2.7.6.dfsg-1ubuntu1.5)
End-Date: 2012-05-23  13:32:01

Start-Date: 2012-05-23  18:57:34
Upgrade: libsnmp-base (5.4.2.1~dfsg0ubuntu1-0ubuntu2.1, 5.4.2.1~dfsg0ubuntu1-0ubuntu2.2)
End-Date: 2012-05-23  18:57:51

Start-Date: 2012-05-23  18:58:51
Upgrade: libsnmp15 (5.4.2.1~dfsg0ubuntu1-0ubuntu2.1, 5.4.2.1~dfsg0ubuntu1-0ubuntu2.2)
End-Date: 2012-05-23  18:58:56

Start-Date: 2012-05-23  23:00:40
Remove: lxde-common (0.5.0-3ubuntu2), lxde-core (0.5.0-3ubuntu2)
End-Date: 2012-05-23  23:00:54

Start-Date: 2012-05-23  23:02:14
Install: lxde-common (0.5.0-3ubuntu2), lxde-core (0.5.0-3ubuntu2)
End-Date: 2012-05-23  23:02:25

---

### Post by Frogs Hair on 2012-05-24
Lubuntu has a netbook option and you may have enabled it . The picture at the link is the old Unity net book launcher. Normally you would select that from the login screen on a Lubuntu installation.

---

### Post by Kansasguy on 2012-05-24
It's been Kubuntu since I dual booted this netbook (with XP which came with it) several years ago.  Always updated.  I think the current kernel is 2.6.32.41 if I've got the numbers in the right order.  I was messing around with the panel settings on the bottom panel, and now there is no icon for the two desktops, the "buttons" don't show up in the panel when I have one or more windows of Firefox open (so I can't go back to one if I open another (so this is the second time I'm typing this).  Neither Firefox nor Konqueror have the three boxes at the top:  X, minimize, or maximize.  And I still can't see the blue LXDE desktop (it comes on at first, but then the Unity goes right on top of it.   Somehow I did get the Unity to only cover up part of the desktop, and then finally got it to go away so I could see the icons, but when I logged out and in again, the Unity thing was back full screen.  I would be up for removing LXDE and installing it again, but it didn't work last night.   AARRRGGGGHHH        TIA

---

### Post by kansasnoob on 2012-05-24
Not sure how helpful this might be after so much playing around but here it is:

[http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

I highly recommend learning to actually dual/multi-boot if you're going to play around a lot ;)

---

### Post by Kansasguy on 2012-05-24
KSnoob, are you by chance in NE Kansas?  I've been dual booted for several years.

PARTIALLY SOLVED:  I got rid of the Unity DE by going:    "start"> Preferences>System Settings> Advanced> Autostart, and one at a time un-checking UNR launcher, Plasma Desktop Workspace, and UME Dedsktop Launcher.    Now I get the desktop

BUT,  none of the programs I open have the three little boxes that minimize, maximize, or close a programs,  and there are no "buttons." in the tray to show what programs are open.  Thanks again and again

---

### Post by kansasnoob on 2012-05-25
South Central Kansas ;)

---

