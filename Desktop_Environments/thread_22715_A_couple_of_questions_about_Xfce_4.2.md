---
title: "A couple of questions about Xfce 4.2"
date: 2005-03-29
forum: Desktop Environments
---

### Post by Ruediger on 2005-03-29
I really like Gnome, but it is kinda of slow. I heard Xfce is quite fast and I am willing to try it.

1. Do I need Gnome installed to install Xfce?

2. Can I change the position of the bars, so they will look like more KDE (the open applications bar on the bottom of the screen and the menu on the left of the bar)?

---

### Post by Leif on 2005-03-29
1) I don't think you need Gnome, but you do need GTK. If you install it with apt you don't have to worry about it tho, dependencies should be resolved.

2) Yes.

---

### Post by Ruediger on 2005-03-29
[QUOTE=Leif]1) I don't think you need Gnome, but you do need GTK. If you install it with apt you don't have to worry about it tho, dependencies should be resolved.

2) Yes.[/QUOTE]

Thanks, I've installed Xfce and it is pretty good. I have more questions about it.

1. How to remove the taskbar from the desktop? 

2. Why my wallpaper won't show on the desktop?

---

### Post by taygan on 2005-03-30
Try playing around with the settings (found on the panel at the bottom of your screen).  You can add wallpaper through settings>desktop.  Or, you can get your gnome wallpapaer by starting nautilus.  To avoid nautilus taking over the desktop run "nautilus --no-desktop."

You can hide the taskbar through settings>taskbar, from the panel or from the desktop>right click>settings>xfce4 taskbar settings.

I've removed both the xffm file manager and rox file manager and am using nautilus with xfce.  The benefits of gnome with the speed and layout of xfce.

---

### Post by kkathman on 2005-03-30
I initially installed Warty 4.10 on a very memory constrained computer (only 96 MB!!) so Gnome ran, but fairly poorly. So I bit the bullet and installed XFCE.  It installed with some dependency issues, but was definitely more performant for me on my little box, but not without some issues. I didnt have luck with the apt-get under Warty, but it might be better with Hoary. I followed a path here and it stepped me through all the dependencies tho.

Two things happened that you probably need to be careful of. While Gnome isnt required, there is something that happens (at least with Warty) if you install XFCE and attempt to go back to Gnome (at least on my box). When I was under Gnome only I installed Samba because I had several Win boxes I needed to share with. When I installed xfce, I had all kinds of problems with xfsamba seeing all the boxes, but never had that problem under Gnome. 

When I tried to go back to Gnome on a sign in (Sessions menu), it stopped. It didnt freeze, because I could move the mouse, but it never was able to get back to Gnome again.

All that being said, if you have memory issues, xfce is what you definitely need to get by.  But, as for me, Im just buying another computer with 512MB and bringing up Kubuntu I think :)

Best of luck!

---

### Post by Ruediger on 2005-03-30
[QUOTE=taygan]Try playing around with the settings (found on the panel at the bottom of your screen).  You can add wallpaper through settings>desktop.  Or, you can get your gnome wallpapaer by starting nautilus.  To avoid nautilus taking over the desktop run "nautilus --no-desktop."

You can hide the taskbar through settings>taskbar, from the panel or from the desktop>right click>settings>xfce4 taskbar settings.

I've removed both the xffm file manager and rox file manager and am using nautilus with xfce.  The benefits of gnome with the speed and layout of xfce.[/QUOTE]

I found the wallpaper setting and selected a file, but it won't show on the desktop :/

I am using nautilus too, but I can't remove xffm, since to remove it I need to remove Xfce4.

---

### Post by Ruediger on 2005-03-30
[QUOTE=kkathman]I initially installed Warty 4.10 on a very memory constrained computer (only 96 MB!!) so Gnome ran, but fairly poorly. So I bit the bullet and installed XFCE.  It installed with some dependency issues, but was definitely more performant for me on my little box, but not without some issues. I didnt have luck with the apt-get under Warty, but it might be better with Hoary. I followed a path here and it stepped me through all the dependencies tho.

Two things happened that you probably need to be careful of. While Gnome isnt required, there is something that happens (at least with Warty) if you install XFCE and attempt to go back to Gnome (at least on my box). When I was under Gnome only I installed Samba because I had several Win boxes I needed to share with. When I installed xfce, I had all kinds of problems with xfsamba seeing all the boxes, but never had that problem under Gnome. 

When I tried to go back to Gnome on a sign in (Sessions menu), it stopped. It didnt freeze, because I could move the mouse, but it never was able to get back to Gnome again.

All that being said, if you have memory issues, xfce is what you definitely need to get by.  But, as for me, Im just buying another computer with 512MB and bringing up Kubuntu I think :)

Best of luck![/QUOTE]

After using XFce I don't think I want to go back to Gnome. My computer is decent enough (XP-M 2400 @ 2.2 GHz and 512 MB RAM) to run Gnome, but Xfce is a lot more responsive.

KDE also seems to be faster than Gnome, but for some reason I never liked it.

---

### Post by taygan on 2005-03-30
hmm..  I don't have problems switching between xfce, gnome and fluxbox.  xfce is my primary desktop, but I like to see what's going on with ubuntu gnome.

I'm also running gnome-volume-manager and nautilus, with xfce I can install what I want and leave out the rest, balancing speed with features.

I bypass the sessions manager, saving (hopefully) some speed and memory and startup gnome-volume-manager, evolution and run fetchyahoo from an autostart.sh script in $HOME/Desktop/Autostart/autostart.sh

the script is darn easy:

```
#!/bin/bash
evolution & gnome-volume-manager & fetchyahoo & 
```

be sure to chmod a+x to the script so it wil run.  There are other ways to do the same thing, but this works for me.

---

### Post by bored2k on 2005-03-30
I like XFCE, its fast, simple and productive. But its just that there is too much cooking in Gnome camp for me to ignore and go XFCE completely. Xfce 4.2 is great though. And their upcoming file explorer will rock .

---

### Post by Whiffle on 2005-03-30
I'm loving XFCE, one of the first things I installed, I used it in gentoo, it actually seems faster under ubuntu... 


When you run nautilus, what options are you running it with?  If you run it without the --no-desktop it will take over your desktop and you won't see your XFCE wallpaper.

Nautilus is my file manager at the moment, and I have gnome-volume-manager running to take care of my camera and stuff when I plug that in.  One of these days I'll take out the gnome stufF I don't need.  I don't mind having it though, my entire ubuntu install is only 6 gigs, leaving me 76gigs free on my dedicated linux partition :D

---

### Post by bored2k on 2005-03-30
[QUOTE=Whiffle]I'm loving XFCE, one of the first things I installed, I used it in gentoo, it actually seems faster under ubuntu... 


When you run nautilus, what options are you running it with?  If you run it without the --no-desktop it will take over your desktop and you won't see your XFCE wallpaper.

Nautilus is my file manager at the moment, and I have gnome-volume-manager running to take care of my camera and stuff when I plug that in.  One of these days I'll take out the gnome stufF I don't need.  I don't mind having it though, my entire ubuntu install is only 6 gigs, leaving me 76gigs free on my dedicated linux partition :D[/QUOTE]
 you can install gtweakui and with it make nautilus -not- draw the desktop .

---

### Post by Mlehliw on 2005-04-03
I have a couple questions about this newfangled desktop.

1. I see a lot of screenshots of the taskbar separated from the window list. Is it possible to combine these two entities into one extreme uberelite taskbar.

2. How does autohide work on xfce? Is it slick like KDE where the entire bar disappears or is it ugly and slow like gnome where it sticks out about 10 pixels?

3. Would it be possibly now to completely forego gnome or kde completely on an ubuntu install and solely use xfce?

---

### Post by taygan on 2005-04-03
1. Mmmm.. I haven't figured out how to separate them.  Xfce isn't a superlight desktop, it's a lighter one.  A balance between features and speed/memory.

2. Autohide is appear and disappear, and you can just see a few pixels sticking out.

3. Mmmm.. you could forgo gnome, but then you'd be forgoing the ubuntu-desktop metapackage, associated upgrades, and basically have a debian xfce system.  

Xfce is lighter, and doesn't have all the good stuff gnome has.  It is friendly with gnome (and kde I'm told), so using gnome applications mixed in with xfce works great.   I like it as the base of a system with a good helping of specific gnome applications to round it out.  (gnome-terminal, gnome-volume-manager, nautilus, rhythmbox - xfce has its own versions but I like the extra features of the gnome ones)  As an example of fitting well together, you can minimize rhythmbox or gnome-cd into the notification tray on the xfce taskbar.

---

### Post by eric71 on 2005-04-06
[QUOTE=Mlehliw]I have a couple questions about this newfangled desktop.

1. I see a lot of screenshots of the taskbar separated from the window list. Is it possible to combine these two entities into one extreme uberelite taskbar.

2. How does autohide work on xfce? Is it slick like KDE where the entire bar disappears or is it ugly and slow like gnome where it sticks out about 10 pixels?

3. Would it be possibly now to completely forego gnome or kde completely on an ubuntu install and solely use xfce?[/QUOTE]

1. There is a taskbar plugin for the main panel.  I use that and type killall xftaskbar4 in a terminal to kill the regular separate taskbar.  You can save your session and it stays gone.  I love the taskbar plugin - it is more flexible than Gnomes, and you can leave out the labels and just have icons.  I fill my panel up with application launchers and only leave  a bit of room for the taskbar plugin and I can still manage everything I have open.  It also has an option to expand to fit the screen, so the taskbar is very similar to windows or KDE.

2.  The autohide is quick and does not leave the edge showing like in gnome.

3.  I have sort of done this 2 or 3 times since Xfce4.2 was released.  After a normal install, I've stripped all of gnome/metacity/nautilus out.  If you use xdm of wdm (very nice) you can get rid of GDM.  you can pretty much do everything else with GTK based apps.  I use graveman for burning, ripperx for CD ripping, mplayer for videos.  The ubuntu FIrefox seems to have had some Gnome integration done, so it hade gnome library dependancies.  TO get rid of them you'll  have to look elsewhere for another non-ubuntu .deb. I had a nice 1 GB system that still had OpenOffice.org, Skype, and Firefox.

It takes a little bit more effort to set things up the way you want in Xfce, but in the end you have more choice than in GNome.  I still keep coming back to Gnome, though,  because I miss certain things - the volume manager, the system-tools (gui user, network, grub setup tools).  I've tried replacing them, but nothing gives me the ease of use that the Gnome apps do.  I've only got about 4.5 gigs of space to work with and I don't want to have Xfce and half of GNome installed.  I can only see doing either or.

I love the way Xfce 4.2 looks and feels.  I know how to configure my jumpdrive to show up in fstab, and how to add my wireless information to etc/network/interfaces.  I've just got an annoying wish to prove to my wife that Ubuntu can do everything that the Windows XP taking up the other 35 gigs of our hardrive can do and just as easily.

So if anyone can suggest some good gui system configuration apps for network and wireless cards, user management, something like gnome-volume manager, I'd be willing to take the plunge again and strip Gnome from my sytem and go with a completely Xfce 4.2/GTK system. (although the Xfce desktop does seem to have some dependencies like gnome-canvas that you can't get rid of).

---

