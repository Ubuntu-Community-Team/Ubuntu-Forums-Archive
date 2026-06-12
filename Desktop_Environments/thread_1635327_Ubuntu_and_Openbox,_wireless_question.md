---
title: "Ubuntu and Openbox, wireless question"
date: 2010-12-01
forum: Desktop Environments
---

### Post by politenessman on 2010-12-01
I am running ubuntu 10.04 with Gnome, but just for kicks I loaded openbox and found that actually I prefer it to Gnome, however, there are two problems:

1. I have no wireless connectivity when using openbox (works fine with Gnome)

2. Can't figure out how to edit the openbox menus, although I seem to be able to edit the gnome menus from openbox just fine.

I'm certain I am missing something trivial but I have no idea what. Can anyone point me in the right direction please?

---

### Post by Liverbones on 2010-12-01
Absolutely. I happen to use Openbox quite a bit myself, it's a very nice window manager. :)

For the menus, you can use a simple program called obmenu. Openbox stores all of the information for its root menu in XML format, under ~/.config/openbox/menu.xml, if I recall correctly. You can either edit this XML file by hand with any text editor (if you're that crazy :P), or you can use the previously mentioned obmenu to do it a little less painfully. Unfortunately, Openbox doesn't come with obmenu (or another really handy Openbox application called obconfig), but both can be installed from a terminal by typing [FONT="Monospace"]sudo apt-get install obmenu obconfig[/FONT]. Then, you can run them within Openbox to adjust your menus and some common Openbox settings.

So, assuming that you installed Ubuntu with the default GNOME desktop, getting wireless connectivity is also pretty simple. Each time the Openbox window manager is started, it runs an autostart shell script which can contain any shell commands you would like. The file you need is ~/.config/openbox/autostart.sh. If it doesn't exist, you can create the file and then mark it as executable. In the file, all you need is this:

```

(sleep 2s && nm-applet) &

```

This will tell the autostart script to wait two seconds, then load the Network Manager applet in the background, which comes by default with the Ubuntu GNOME desktop and provides your internet connectivity.

You might also want to install some other nice programs for use with Openbox that provide a system tray or panel. If you'd like, you can feel free to PM me and I can tell you how I have things set up for myself.

Good luck, and I hope this was helpful!

---

### Post by politenessman on 2010-12-02
Wireless is now working! Thank you so much.
I did install obmenu but I guess I just don't know how to drive it because I see the top level menu but nothing other than that. It certainly isn't intuitive, but I guess I need to play with it more.

What I really like about this desktop is the right click and menu, and the lack of crap on the desktop. I played with linux for a while in the late 90s and there was a desktop I used then (can't remember what) that had the right click > menus, and I found that so intuitive and fast, so I am very excited to find one that does the same now.


I'd love to know how you have yours set up, so PM inbound!

Edit - you aren't accepting PMs.

---

### Post by smokineasy on 2012-01-13
just wanted to say thanks Liverbones for your help in getting my wifi to work :) Thank You :)

---

