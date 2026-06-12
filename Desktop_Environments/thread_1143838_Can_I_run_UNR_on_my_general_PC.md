---
title: "Can I run UNR on my general PC?"
date: 2009-04-30
forum: Desktop Environments
---

### Post by Dragonbite on 2009-04-30
Curious about if I can download the UNR, can I install it on my Pentium (M) laptop?  

TuxRadar has an [[COLOR="Blue"]article [/COLOR]]("http://www.tuxradar.com/content/ubuntu-netbook-remix-904-hands")and lists what needs to be done to convert a general desktop to a UNR but ***will it work on non-Atom chip systems?***

-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~-~
According to the article, to get UNR from a normal desktop by
[LIST=1][*]Turn Compiz off. UNR doesn't need them, and in fact it may collide with its own deskop effects system.
[*]Bring up a terminal window and run ```
sudo apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```
[*]Reboot your PC, and you should come back to a desktop that has the two largest parts of UNR working - the netbook-launcher app (the thing that now owns your desktop) and maximus, the window maximiser. 
[/LIST]To get the full effect, you should do the following-[LIST=1]
[*]Remove from the top panel the Ubuntu menu (Applications/Places/System) from the left and the switch user applet from the right, plus any app launchers you don't want. Just right-click on things and choose Remove From Panel to get rid of them.
[*]Right-click on the top panel, choose Add to Panel, then add Go Home and Window Picker, moving them to the left and centre of the panel respectively.
[*]Remove the bottom panel entirely - right-click and choose Delete This Panel.
[*]Now go to System > Preferences > Appearance and choose the Human-Netbook theme.
[/LIST]

---

### Post by snowpine on 2009-04-30
Yes, UNR is an interface that goes on top of your existing Ubuntu install (following the instructions in your post), so it does not require an Atom processor.

Or, you can do a fresh install of UNR; this uses the i386 kernel, so it should work OK on your pentium.

---

### Post by Rinzwind on 2009-04-30
I had it running on my normal notebook. There is also a desktop-switcher.

Just be aware: UNR does NOT play nice with wicd. It will reinstall network-manager. It will also delete gnome-themes iirc.  


The 2 packages I marked to install UNR are:

desktop-switcher
> desktop-switcher allows the user to switch between two desktop modes.
It currently supports switching between Ubuntu Netbook Remix mode and
"Classic Ubuntu" (two panels, gnome-like) mode.

netbook-launcher> Netbook Launcher is a desktop launcher that uses the clutter UI library.
It is commonly being used on netbook desktops with a resolution of
1024x600 pixels and also supposed to support usage on touchscreens.
It follows the xdg spec standards from freedesktop.org
for the Desktop menu layout. Originally this application is used in
the Ubuntu Netbook Remix.

See [https://launchpad.net/netbook-remix-launcher](https://launchpad.net/netbook-remix-launcher) for more information.

And here a screenshot of my notebook (1900x1200):

[http://img144.imageshack.us/img144/9196/screenshotkls.png](http://img144.imageshack.us/img144/9196/screenshotkls.png)

edit: sorry picture was a bit large to show in this topic :)

---

### Post by Dragonbite on 2009-04-30
Cool.  I think I'm going to try it on my test hard drive once I get my production laptop moved over to Jaunty (probably this weekend).  It's a 12" screen laptop so it isn't THAT far of a stretch from a netbook! :lolflag:

---

### Post by kalos on 2009-11-01
> **Rinzwind said:**
> 
The 2 packages I marked to install UNR are:

desktop-switcher
...

It doesn't look like desktop-switcher is available? Or did you have to add additional repositories?

I followed Dragonbite's steps and now I have a netbook remix-like desktop on my inspiron 1545. We'll see how long I keep it...  : D

The only difference I've noticed from my testing of the UNR 9.10 beta are the icons are different (switch the icon set to Humanity-Dark and only Empathy still looks weird).

---

### Post by Oranges10e on 2009-11-02
Hi, I just wanted to verify this. I am using UNR 9.10 (Jaunty before) on a 15" Lenovo 3000 n100 Laptop - works good. I had a 100% CPU netbook-launcher prob. with Karmic but got it fixed with the help here on the forum. Now everything is running good. I am thinking on buying a touchscreen and using the UNR on it, I'll report back and give you feedback on how it goes. 

I guess you actually can use the UNR on a normal computer. I read the MINIMUM system req. yesterday, minimum, which means you should be able to use it on more than that -> [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)  at the bottom of the page. I also read an article with an interview with one of the Ubuntu guys, saying, that the UNR is possible on other systems, but they have to find out if it's worth it on bigger screens. Well, like I said, I installed the normal UNR image and it's working great so far.

Oranges

---

### Post by phersotty on 2009-11-18
> **Dragonbite said:**
> ...Turn Compiz off. UNR doesn't need them, and in fact it may collide with its own deskop effects system.

Actually you can use them both.  Here is what my desktop looks like

[http://ubuntuforums.org/attachment.php?attachmentid=135340&d=1257714361](http://ubuntuforums.org/attachment.php?attachmentid=135340&d=1257714361)

---

### Post by jolan on 2009-12-28
> **Oranges10e said:**
> Hi, I just wanted to verify this. I am using UNR 9.10 (Jaunty before) on a 15" Lenovo 3000 n100 Laptop - works good. I had a 100% CPU netbook-launcher prob. with Karmic but got it fixed with the help here on the forum. Now everything is running good. I am thinking on buying a touchscreen and using the UNR on it, I'll report back and give you feedback on how it goes. 

I guess you actually can use the UNR on a normal computer. I read the MINIMUM system req. yesterday, minimum, which means you should be able to use it on more than that -> [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)  at the bottom of the page. I also read an article with an interview with one of the Ubuntu guys, saying, that the UNR is possible on other systems, but they have to find out if it's worth it on bigger screens. Well, like I said, I installed the normal UNR image and it's working great so far.

Oranges


Hi. How did you solve the 100% CPU netbook-launcher problem? I seem to be having the same problem but I cant find any solution. 
Thank you.

---

### Post by kalos on 2010-05-13
> **jolan said:**
> Hi. How did you solve the 100% CPU netbook-launcher problem?

I think I saw this problem before. I was also having that problem with gnome-do. I ended up writing a script to launch both of them. I run it manually when I start up. I think eventually netbook-launcher wouldn't start on boot at all either...


Now I've got all of this running on Lucid. (Haven't rebooted to see if I still need my script...)

---

