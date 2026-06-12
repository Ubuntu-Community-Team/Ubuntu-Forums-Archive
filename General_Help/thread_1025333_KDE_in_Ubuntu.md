---
title: "KDE in Ubuntu"
date: 2008-12-30
forum: General Help
---

### Post by maddog46113 on 2008-12-30
I installed KDE in Ubuntu by using this guide.

[http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html)

When I log out and change sessions KDE freezes. My computer doesnt freeze I know this because i can still operate the num lock. The desktop freezes completely. I was gonna try out KDE being as I havent messed with KDE since Mandriva a long time ago. Any ideas on whats going on? It logs in and seems fine but after about 10 seconds it just freezes.:(

Thanks ahead of time!

---

### Post by maddog46113 on 2008-12-30
***Bump*** anyone?

X just kinda freezes when KDE starts...

---

### Post by RichardLinx on 2008-12-30
What's your hardware? It could be that running KDE and GNOME simultaneously is more then your computer can handle. Although this is unlikely if your just running a KDE only session. It sounds to me like your having kernel panics, a common problem with Ubuntu from what I've heard.

---

### Post by RichardLinx on 2008-12-30
When you log out of your KDE session do you have Compiz enabled? If you do try disabling it and then logging out to see if this has any effect on the problem. It could also be that you have some unnecessary or "old" packages that are causing some errors if that is the case then these two commands may fix the issue.

```
sudo apt-get autoremove
```

```
sudo apt-get autoclean
```

---

### Post by maddog46113 on 2008-12-30
2.4 ghz Celeron overclocked to 2.69
1.5gb RAM
Radeon 9200

I use compiz fusion icon. I disabled compiz no fix. I gave the auto rem and clean a try ill see if that does anything.

---

### Post by Liviu-Theodor on 2008-12-30
Try with the CPU running at normal speed, not overclocked. Sometimes, overclocking leads to weird results and behaviour.

---

### Post by maddog46113 on 2008-12-30
No fix yet. I did try knocking down the clock. Didnt work. It seems KDE is still trying to load compiz when it does it freezes. I disabled Compiz in gnome. Didnt have any affect in kde.


**EDIT* if i didnt have so much data at stake i would just try a reformat.

---

### Post by RichardLinx on 2008-12-30
Did a quick search just now:
[http://ubuntuforums.org/showthread.php?t=107291](http://ubuntuforums.org/showthread.php?t=107291) This thread hints that it might be a problem with your soundcard, It's unlikely though since the problem is from 2005.


[http://ubuntuforums.org/archive/index.php/t-203046.html](http://ubuntuforums.org/archive/index.php/t-203046.html) This thread has a more simple solution - Uninstall Kopete, It might fix your problem.

It could just be a problem with your graphics card though, check all possibilities. :)

---

### Post by maddog46113 on 2008-12-30
removing and purging kopete. Hopefully its not the sound card >.>

---

### Post by maddog46113 on 2008-12-30
Nope that didnt work. Im guessing it could be the sound. It never makes a sound before it locks.. I guess I'll stickl with gnome it hasnt done me wrong yet.

---

### Post by RichardLinx on 2008-12-30
Yeah GNOME's the way to go. Since you can't get KDE to work with Ubuntu (Kubuntu) you might want to try out openSUSE which is, in my opinion, the best KDE distro available. You might also like the 'gnome slab' (similar to the gnome slab openSUSE uses) you can install it by typing in terminal:

```
sudo apt-get install gnome-main-menu
```
and then right clicking on the panel>select "Add to Panel">Add Gnome main menu.
Then again maybe I'm just rambling out useless suggestions. :D It's a shame you couldn't get KDE to work though, hopefully a future update will fix the problem for you. KDE 4.2 isn't far off - you never know It might just fix whatever problems you experienced.

---

