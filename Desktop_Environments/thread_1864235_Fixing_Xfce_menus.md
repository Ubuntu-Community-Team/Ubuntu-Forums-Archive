---
title: "Fixing Xfce menus?"
date: 2011-10-18
forum: Desktop Environments
---

### Post by MarjaE on 2011-10-18
A few things bug me about the Xfce menus, and I'd like advice on fixing/tweaking them:

1. There is an Applications menu, and it's pretty useful, but it tends to put the Applications in the wrong categories - Pointing Devices doesn't show up, Synaptiks will show up but in Accessories not Settings, Evolution will show up in Office, etc.

2. The Applications window can be nonresponsive at times - it used to stop responding for as long as an hour, but closing system settings and any terminal windows, and maybe opening and closing some other windows can sometimes get it to start responding again. Also, it could use a wider strip of the top panel.

3. A Places menu would be very useful. As it is, I have to use the side panel to open my home folder, and navigate from there to the other partition where I keep my projects.

4. I just don't like the bottom/side panel. I don't use it for much, and I'd rather use the top panel for that. Aesthetically, the style of the bottom/side panel clashes with the style of the top panel.

5. The top panel tries to do most of what the Gnome 2 top and bottom panels did. It's awfully crowded. Given the [wide] screen dimensions, the Gnome bottom panel got in the way, but it would be nice to move the window switcher or the status icons to a separate side panel.

And some other issues:

6. My system clock is just broken. I can reset the Orage clock, but the system clock messes with things like time zones. I try to set it to the current time zone, and it might end up eight hours off instead of four hours off.

7. Is it just me or has the minimum screen brightness gone up when switching from Ubuntu to Xubuntu? I prefer the dimmest screen I can get, and then dimmer, because bright screens hurt my eyes.

8. LibreOffice ought to be included standard. And Evolution ought to be included at least until they sort out import from Evolution to Thunderbird; following the official directions from the Mozilla website broke Thunderbird the first time and just didn't work the second time.

9. Also, can anyone suggest a good data cd/dvd burner? I installed Xfburn but it doesn't work.

---

### Post by Rodney9 on 2011-10-18
I am usung Xubuntu 11.10 and Synaptics is in 'System' and Thunderbird is in 'Internet'

You can change the size of the panels in 'Settings' 'Panel'

Right click on the panel and Add New Items you can add Places.

You usually change brightness with the monitor controls, though I can also do it in the nvidia xserver settings.

Libre Office is pre-installed but no Evolution, only Thunderbird 7.

There are several burning programs you can try, Brasero gets good reports plus K3B.

The other problems I can't help with but it sounds like a perfect time to back-up and install the latest Xubuntu 11.10, it is very good they have given it a good polish, looks great now.

---

### Post by MarjaE on 2011-10-18
First of all, thanks for the tip about the places menu; I'm glad to have one.

> **Rodney9 said:**
> The other problems I can't help with but it sounds like a perfect time to back-up and install the latest Xubuntu 11.10, it is very good they have given it a good polish, looks great now.

I did that on Sunday.

I don't have Synaptics. I installed Synaptiks, with the k, because Xubuntu does not include its own touchpad settings. I installed the psmouse patch first, and then Pointing Devices, but Pointing Devices does not show up, and Synaptiks only shows up in Accessories. Um, I take it you didn't spend the previous several months trying to stop a touchpad gone haywire?

Thunderbird is gone, and I'm not reinstalling it until they get import working. Unfortunately, before I deleted it, it messed up one of my email accounts. I reinstalled Evolution, at first because I was trying to get Thunderbird to import properly, and later because I just couldn't get Thunderbird to do so. Evolution is in Office for some bizarre reason.

The official instructions here: [http://support.mozillamessaging.com/en-US/kb/switching-thunderbird?](http://support.mozillamessaging.com/en-US/kb/switching-thunderbird?) can either break Thunderbird or leave Thunderbird working but unable to read the imported emails.

---

### Post by gsmanners on 2011-10-18
1) Editing appmenu is a bit of a pain (cp /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu ~/.config/menus, then modify that file in a text editor). I think lxmed can edit it, but it's a java app so I haven't tried it.

2) I like to "Show button title" in the appmenu. That makes it quite a big target.

4) Everything is optional in Xfce, so just configure it however you want.

5) Right-click on the panel app, select Move, then move it where you want.

7) Sorry. I use my monitor to adjust brightness. Maybe there's something in the driver config options (if the video driver lets you set options).

8 ) LO is nice, but I like the choice of Abiword. That makes a lot of sense to me. I personally use Abiword more than an big office suite. Xubuntu has never had Evolution (and that's a good thing IMHO).

Not sure about the other issues. I think I'd have some idea what it was if I was looking at it IRL, but there's just too many variables to say for sure from here.

---

### Post by MarjaE on 2011-10-18
One more thing... language support, keyboard options, and the compose key. I had a keyboard toggle and compose key set up in Gnome 2 but still had to mess around with two character selectors - KCharSelect and one other - at times. I understand I'm supposed to use the command line to set up the compose key, but I intend to avoid the command line this time around. I already messed up enough of this installation without it. (See clock, applications menu, screwing up one of my email accounts when I tried to use Thunderbird.)

P.S. Character Map was already installed under Accessories. I added KCharSelect, but it isn't showing up in the Applications menu. So far that's two applications that aren't showing up.

---

### Post by ankspo71 on 2011-10-19
Hi,
When I right click on the panel to add applets I see an applet called "Directory Menu" and an applet called "Places". The places applet resembles the places menu in Gnome2x the most. I installed the 'xfce4-goodies' package though, so I'm not sure if both applets were there in Xubuntu by default.

XFCE 4.8 supports having a menu editor but there isn't one installed by default. Gnome's menu editor 'alacarte' is good and integrates with the start menu but it requires alot of Gnome dependencies, and there is another menu editor called 'lxmed' that only requires java.
[http://lxmed.sourceforge.net/screenshots.html](http://lxmed.sourceforge.net/screenshots.html)
To run lxmed you will need to open the LXMenuEditor.jar file with 'java -jar'. Right click on the file, choose open with other application, then select choose a custom command, then enter 'java -jar' into the box. (I have not tried running the install script it comes with.)

There is an keyboard switching applet for the xfce4 panel called xfce4-xkb-plugin. If you install that package it will install a "Keyboard Layouts" plugin/applet that you can add to the panel. It has options for keyboard shortcuts / compose keys too. It is also a part of the xfce4-goodies package.

I use K3B for all of my cd burning (on any desktop I use). For me it has been the most reliable, but it requires alot of additional packages though (KDE libraries and such). Currently XFburn isn't working for me either. I liked using Gnomebaker before I liked using K3B. 

It's possible to save some room in the panel by editing the properties of the clock and properties of the applications menu (and places menu too, if on the panel) to shorten the titles of the applets. The session menu doesn't seem necessary so I removed it. The application menu, places menu, and 'Window Buttons' applet can all be inconified(?) instead of showing the text in the panel too. 

The bottom panel only serves as a basic application launcher, and not so much serves as dock. I kind of like it though but I wish it had more hiding options like intellihide. I think the bottom panel looks much better with different icon sets like "awoken" and "faenza" and "ACYL" too. 

If you no longer want the bottom panel at all then it can be removed by going to the panel preferences by right clicking on the panel or go to Settings > Settings Manager > Panel.

---

### Post by KBD47 on 2011-10-19
R-Click on your desktop and go to desktop settings to adjust brightness and saturation. The bottom launcher is highly configurable and I added an Applications Menu down there as I felt the menu at the top left was a bit small. I also added a shut down button on the bottom launcher. I also download Everything using Synaptic Package Manager and seem to have fewer problems, downloading Thunderbird that way worked flawlessly as did the other programs I downloaded, Ubuntu Software Center is a snail and pretty much worthless in my view. I would run the update manager and install any updates, they will likely be catching and fixing any bugs that show up right after a release. But so far Xubuntu has been bug free for me.
KBD47

---

### Post by gsmanners on 2011-10-19
> **KBD47 said:**
> ... But so far Xubuntu has been bug free for me.
KBD47

That Desktop Settings/Brightness and Saturation only affects the desktop background, you know?

I agree with that last part, though.

---

### Post by Kilarin on 2011-10-25
I'm still on Ubuntu 11.04.  I dont want to upgrade until I have a way to have a real desktop, not unity.

So, I installed the xubuntu-desktop through the software center. (xfce 4.8.0)
trying to figure my way around it.

[quote="Rodney9"]Right click on the panel and Add New Items you can add Places.[/quote]
When I right click on the panel and select panel, add new items, there isn't a "places" app.  Do I have to upgrade to 11.10 before that is available?

Also another newbie xubuntu question.  In Gnome 2.x I could re-arrange windows buttons on the bottom panel.  Is that impossible in xubuntu?  The buttons are grababble, and you can drag them around, but as soon as you drop them, they go back to where they were.

thanks!

---

### Post by Kilarin on 2011-10-25
My apologies.  I searched on the places issue, but didn't search long enough.  Found the entry with the answer shortly after I posted.

[http://ubuntuforums.org/showthread.php?t=1763652&highlight=xubuntu+places](http://ubuntuforums.org/showthread.php?t=1763652&highlight=xubuntu+places)

Just install xfce4-places-plugin from the software center.

---

### Post by KBD47 on 2011-10-26
> **Kilarin said:**
> My apologies.  I searched on the places issue, but didn't search long enough.  Found the entry with the answer shortly after I posted.

[http://ubuntuforums.org/showthread.php?t=1763652&highlight=xubuntu+places](http://ubuntuforums.org/showthread.php?t=1763652&highlight=xubuntu+places)

Just install xfce4-places-plugin from the software center.

There is a small learning curve with Xubuntu/Xfce but soon you will find it as comfortable as gnome 2.

---

