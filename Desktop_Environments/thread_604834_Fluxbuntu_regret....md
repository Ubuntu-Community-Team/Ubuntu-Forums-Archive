---
title: "Fluxbuntu regret..."
date: 2007-11-06
forum: Desktop Environments
---

### Post by sargonious on 2007-11-06
I just installed Fluxbuntu and though it's very fast I'm somewhat dissapointed by it. How do you make icon shortcuts on the desktop and how come when you install programs it doesn't go on the fluxbox menu? Can I install Xubuntu-desktop from Synaptic and just use that instead of having to do a fresh install?

I can now say I've used All the 'buntus from Ubuntu to Kubuntu to Xubuntu from versions 6.06 to 7.10. I like the quickness of Fluxbox but find it a little complex. Someone help!

I also have used DesktopBSD and PC-BSD [better of the two], Mandriva, Zenwalk, and I messed a little with FreeDOS. Of course I know the evil Microsoft Windows from 3.1 to Vista and I like Mac OSX because of it's BSD upbringing.

---

### Post by deserthowler on 2007-11-06
> **sargonious said:**
> Ihow come when you install programs it doesn't go on the fluxbox menu? .

Not having used fluxbox, I will hazard a guess you need to run 'update-menus'.  You might need to install menu and menu-xdg.
You will then need to sign out and sign back in.

Earl

---

### Post by maybeway36 on 2007-11-06
```
sudo update-menus
```

---

### Post by sargonious on 2007-11-06
How can I customize the menus to my liking?

---

### Post by ugm6hr on 2007-11-07
The fluxbox docs:
[http://fluxbox.org/docbook/en/html/c741.html](http://fluxbox.org/docbook/en/html/c741.html)
[http://fluxbox.org/docbook/en/html/x758.html](http://fluxbox.org/docbook/en/html/x758.html)

---

### Post by rjmdomingo2003 on 2007-11-07
> **sargonious said:**
> How do you make icon shortcuts on the desktop and how come when you install programs it doesn't go on the fluxbox menu?
For icons, I believe you can try idesk (think it's on the repos). You need to configure the ideskrc and idesktop files for each icon. Here's a link: [http://packages.ubuntu.com/feisty/x11/idesk](http://packages.ubuntu.com/feisty/x11/idesk)

For installed programs, you need to edit the ~/.fluxbox/menu to add the program. Sometimes, it's automagically added to the debian menu.

Hope this helps.

---

### Post by TeaSwigger on 2007-11-07
> **sargonious said:**
> I just installed Fluxbuntu and though it's very fast I'm somewhat dissapointed by it. How do you make icon shortcuts on the desktop and how come when you install programs it doesn't go on the fluxbox menu? Can I install Xubuntu-desktop from Synaptic and just use that instead of having to do a fresh install?

I can now say I've used All the 'buntus from Ubuntu to Kubuntu to Xubuntu from versions 6.06 to 7.10. I like the quickness of Fluxbox but find it a little complex. Someone help!

I also have used DesktopBSD and PC-BSD [better of the two], Mandriva, Zenwalk, and I messed a little with FreeDOS. Of course I know the evil Microsoft Windows from 3.1 to Vista and I like Mac OSX because of it's BSD upbringing.

Hello, 

I use Fluxbox. Fluxbuntu is lovely. It is quirky until you learn it. Once you do however, you just may love it!

There are two elements at work: Fluxbox and ROX-Filer. You don't need ROX-Filer. What ROX-Filer does in this case is provide the file manager, the desktop background, and the icons. You could use another file manager; the whole Ubuntu repositories are at your fingertips! For instance Thunar or even faster, pcmanfm, or emelfm2 if you want a light dual-pane file manager. You could use idesk for icons. Fluxbox can handle desktop backgrounds by itself (automatically using a light image manager like feh for instance). Understand ROX-Filer is blazing fast, feature rich and configurable, that's why Fluxbuntu uses it. It seems to "go with" Fluxbox. But it's probably extremely quirky to most folks. 

One way Fluxbox is so fast is not having big menu systems. It mostly uses the "Debian auto-generated menu." You can also make your own menu top to bottom - it's just a text file with easy syntax you can have in your home folder. At first I found it very frustrating and a big pain in the neck... but now I know how it works, enjoy making my own menu so easily. Check this very informative thread:
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

No matter the distro, enjoy yourself :)

---

### Post by RedSquirrel on 2007-11-07
> **TeaSwigger said:**
> You could use another file manager; the whole Ubuntu repositories are at your fingertips! For instance Thunar or even faster, pcmanfm, or emelfm2 if you want a light dual-pane file manager.

I don't really use a file manager, but just out of curiosity, has pcmanfm gotten any better? The last time I played with it, it seemed buggy and consumed a lot of resources.

---

### Post by yabbadabbadont on 2007-11-07
> **RedSquirrel said:**
> I don't really use a file manager, but just out of curiosity, has pcmanfm gotten any better? The last time I played with it, it seemed buggy and consumed a lot of resources.

I didn't notice an issue with resources, but it did have trouble updating a pane after deleting something.  Sometimes a manual refresh would work, and sometimes I would have to select a different directory and then go back in order for the deleted item to be removed from the listing.  I'm using xfe now.

---

### Post by RedSquirrel on 2007-11-07
> **yabbadabbadont said:**
> I didn't notice an issue with resources, but it did have trouble updating a pane after deleting something.  Sometimes a manual refresh would work, and sometimes I would have to select a different directory and then go back in order for the deleted item to be removed from the listing.  I'm using xfe now.
Thanks for the info. I might give pcmanfm another try then (just for something to do...). I tried xfe a while ago. Maybe it's time for another spin.

---

### Post by TeaSwigger on 2007-11-08
> **RedSquirrel said:**
> I don't really use a file manager, but just out of curiosity, has pcmanfm gotten any better? The last time I played with it, it seemed buggy and consumed a lot of resources.

> **yabbadabbadont said:**
> I didn't notice an issue with resources, but it did have trouble updating a pane after deleting something.  Sometimes a manual refresh would work, and sometimes I would have to select a different directory and then go back in order for the deleted item to be removed from the listing.  I'm using xfe now.

Hi Red. Yeah I have the same observation as yabbadabbadont. Sometimes it doesn't refresh, which can be annoying. There's no "trashcan" support if that's an issue for you. I haven't had any serious errors though. It is amazingly fast, there's tabs and even a side panel you can have show a tree or favorites views (F9), and it provides an easy option to open an instance in a current directory as root or in a terminal of one's choice. File associations are easy to edit in a text file in your home folder. xfe is interesting but something about the GUI just doesn't seem to agree with me. When I'm not in KDE I often use it (or emelfm2 if I'm in a dual-pane Midnight Commander mode ;) ). pcmanfm doesn't seem to be developed much lately, and I had to compile emelfm2, but they work so I'm grateful. :)

---

### Post by RedSquirrel on 2007-11-08
Thanks for the info. I installed xfe last night, but so far I've barely touched it. My file management needs are rather simple so I can get by on my knowledge of the command line. ;)

---

### Post by sargonious on 2007-11-13
Holy Christ did I screw things up... I installed xubuntu-desktop because I did the Linux install of Fluxbuntu for my cousin Pete's old IBM thinkcenter laptop so I figured he'd have a hard time adjusting to Fluxbox which he did. He didn't like it so I installed xubuntu-desktop thru synaptic and a lot of programs I'm installing, specifically games aren't showing up on the games menu under applications for some reason. When I do run them from the comman line it seems to crash. Is Fluxbuntu missing something the other 'buntus have?

---

