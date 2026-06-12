---
title: "[SOLVED] Xmonad and NetworkManager"
date: 2008-06-28
forum: Desktop Environments
---

### Post by angry_johnnie on 2008-06-28
I like big, fancy DE's quite a bit, but my laptop is beginning to grow old, and I'd rather stay away from GNOME/KDE/XFCE until I can, at least, add some more ram (it crawls sometimes).

So I've been using Xmonad lately.  And I like it. :-) It's fast and very responsive.  However, there is still one thing I haven't figured out:

What do I have to add to the startup script so that NetworkManager starts as soon as I log in?  While in gnome, there's nm-applet... but that's a panel thing, isn't it?  Some time last week, after I logged in, I launched fbpanel, and then nm-applet.  I thought I'd be able to do it from there, but it told me NetworkManager wasn't running. :confused:

For now, what I have to do is log into gnome, let nm-applet do its thing, then log out and back into xmonad to get my wireless connection... I'd rather not have to do that.

EDIT:  Nevermind... I got a bunch of updates, and now it worked... just like that... I didn't even have to launch anything, it just worked. :o I don't know whether it has anything to do with the updates, or the fact that gdm is now enabled again, or whether it's just plain luck.  The thing is, it's working.  So feel free to remove this thread, or close it, or whatever it is you mods do when a thread has no reason for being.

---

### Post by pwerner2 on 2009-10-28
I know you said you've got your fix, but just in case you were wondering, I'm running xmonad as well, and nm-applet is not necessary. When you boot up, you can connect to a wireless network with the following commands:

1) sudo ifconfig eth1 (or whatever your wireless interface is) up
2) iwlist eth1 scanning (doesn't need to be run as root, only displays available networks, and their stats, encryption, signal strength, etc)
3) sudo eth1 essid <network_name> ex. sudo eth1 essid netgear
4) sudo dhclient eth1
5) ping [www.google.com](www.google.com) (to check that the connection is working)

And boom, you're connected. Useful if you want to save 5mb of ram or just want a cooler way to go wireless.

Cheers

---

### Post by anelephant on 2010-04-24
> **pwerner2 said:**
> I know you said you've got your fix, but just in case you were wondering, I'm running xmonad as well, and nm-applet is not necessary. When you boot up, you can connect to a wireless network with the following commands:

1) sudo ifconfig eth1 (or whatever your wireless interface is) up
2) iwlist eth1 scanning (doesn't need to be run as root, only displays available networks, and their stats, encryption, signal strength, etc)
3) sudo eth1 essid <network_name> ex. sudo eth1 essid netgear
4) sudo dhclient eth1
5) ping [www.google.com](www.google.com) (to check that the connection is working)

And boom, you're connected. Useful if you want to save 5mb of ram or just want a cooler way to go wireless.

Cheers
I think 3 should be 
 sudo iwconfig eth1 essid <network_name>

---

### Post by nuvolari_ on 2010-05-10
Ok, so that should work for a normal wireless network. Did anyone manage to get onto a encrypted network? It's not fun having to switch between GNOME at work and xmonad at home :'(

---

### Post by 42f87d89 on 2011-08-11
I know this thread is old but I cant find it anywhere else, how to connect to password protected wireless connection?

---

### Post by joee92 on 2011-10-01
To connect to a new wpa/wpa2 network (which, as far as I know, requires network-manager), I do this:

```
trayer &
nm-applet
```

Then use the applet as normal to connect.  This adds the network to network-manager's permanent list, which you can see with:

```
nmcli con list
```

From then on, I can switch networks (say, when I move from home to the office) by doing this:

```
sudo service network-manager restart
```

Seems a little drastic, but I haven't found an nmcli command that tells network-manager to rescan and switch networks.

---

