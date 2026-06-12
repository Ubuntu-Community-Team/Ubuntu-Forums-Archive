---
title: "Compiz Settings driving me crazy"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by breakerr on 2007-09-17
__ I hope this post don't get erased by moderators since I think is not a duplicate.....
.... I'm a new guy/user in Linux/Ubuntu and I'm very exciting and about to make the switch from Xp to Ubuntu for good and ever :p as soonest I feel wet enough about knowledge to run/manage and control Ubuntu/Linux properly.

( _Using Metacity and Nvidia 6100 also have emerald installed but not in use or working/enabled with compiz._)
* My most urgent concern right now is about Compiz Fusion: I have _System - Preferences - GL Desktop_ and also  _System - Preferences - CompizConfig Settings Manager_ I wonder if both should be running because it seems that sometimes the Compiz turns off by itself or some plugins/effects lose their settings or stop working when I use the keybindings in my keyboard..even while having the checkmark but when entering directly into the specific settings for a particular effect/plugin I dont know how very well how to set or enable that effect..so far Ive been doing it with luck....Also I don't know very well how to enabled or set the keybindings on the *CompizConfig Settings Manager* so far I searched some forums and google about setting up properly all the Fx and Key Commands and haven't found the answer yet, also I would like to know what or which is the Button key...already set my Windows key to be Super tho....HELP ME OUT GUYS, Please.....

* My second concern is that I get a little window when I enter a DVD disc in my DVD Player saying that I cant play that or unable to mount unit but my AVI and other media format works well.

Thanks a lot in advance......

---

### Post by Forlong on 2007-09-17
Hi and welcome to Ubuntu,

please tell us how you installed Compiz Fusion first.

Then I recommend removing **gnome-compiz-manager** (GL Desktop) - you don't need this with Compiz Fusion anymore and it can't take care of all the plugins anyway.


As for your second concern: [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd)

---

### Post by breakerr on 2007-09-17
> **Forlong said:**
> Hi and welcome to Ubuntu,

please tell us how you installed Compiz Fusion first.

Then I recommend removing **gnome-compiz-manager** (GL Desktop) - you don't need this with Compiz Fusion anymore and it can't take care of all the plugins anyway.

As for your second concern: [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd)

Thanks a lot for the welcome and how do I remove/uninstall GL Desktop ????? I followed this guide here: [forlong best way to install compiz]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") this guide makes you uninstall all Compiz so I don't know why I have GL Desktop and compiz setting manager.

THANKS and hope that somebody write how to manage and control compiz settings properly cause I think a lot of new guys will be lost like me. ( maybe I'm dumb :p)

---

### Post by Forlong on 2007-09-17
> **breakerr said:**
> how do I remove/uninstall GL Desktop ?
```
sudo apt-get remove gnome-compiz-manager
```

Or you go to Synaptic and look for the package and remove it how I described in the installation guide.
> **breakerr said:**
> hope that somebody write how to manage and control compiz settings properly cause I think a lot of new guys will be lost like me.
I did write an additional guide for that: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)


If you have any further questions about either guide, you can use [this thread](http://ubuntuforums.org/showthread.php?t=536149), so I will notice it right away.

---

### Post by breakerr on 2007-09-17
Thanks a lot...I didnt realize till now that you were the same guy who wrote the guide I used to install compiz >p LOL shame on me hehehehe.

I got rid of GL Desktop as you told me and so far seems to works better the compiz and all...but Im still confuse about something...... when you enabled on the checkmark any compiz plugin/effect it takes certain amount of time to start running or someting like that ???? because Ive been trying to use either Ring Switcher or Shift Switcher and none of them works right after I put a checkmark on them, one at a time cause I know one overwrite the other.  Also...how do you activate/enabled on the actions tab of any plugin/effect ????

while writing this I just noticed that I dont have Wobbly Windows with a checkmark but is working...can you explain me that behavior ????  Sorry for all the newbie questions and THANKS A BUNCH

Ill try to gather more questions as longest I use this wonderful Compiz thing. and if you can link me to a Compiz Profile already set that I can import into mine it would save a lot of answers and time cause I rather use that and stop playing with the settings right away :p  THANKS AGAIN.

---

### Post by Yasumoto on 2007-09-18
Yeah, I'm playing around with it too breakerr. I have a lot of sweet stuff working, except my terminal font size is so small I can't even see it. But I can just switch back to metacity if I need that for now.

Thanks a bunch for the guide Forlong :)

---

### Post by breakerr on 2007-09-20
Im wondering how can I make my 3D Cube get farther when I switch sides/desktops...I mean in all the YouTube Videos Ive seen when they usethe cube I can see it father or smaller than the default one I have. And also I wonder how can I resize with constrained proportions my right click menu because I fidn it to big ?????

---

### Post by Forlong on 2007-09-20
> **breakerr said:**
> Im wondering how can I make my 3D Cube get farther when I switch sides/desktops...I mean in all the YouTube Videos Ive seen when they usethe cube I can see it father or smaller than the default one I have. 
ccsm &#8594; Rotate Cube &#8594; Zoom
> **breakerr said:**
> And also I wonder how can I resize with constrained proportions my right click menu because I fidn it to big ?????
Sorry, I don't know what you are talking about there... you mean the context menu of Nautilus (the one of the desktop and in the file manager)?

---

### Post by breakerr on 2007-09-21
Yes...I mean the menu when you right click on the desktop...how can I resize or shrink that menu the *create folder* *create launcher* etc... and in order to skin the desktop what is your best suggestion ???? enlightment or blackbox or maybe fluxbox ????

Thanks for all so far you had help me a lot and I appreciate that. sincere THANKS forlong.

---

### Post by Forlong on 2007-09-21
Enlightment, Blackbox and Fluxbox are all window managers - just like Compiz.
So those are out of the question, when you want to stick to Compiz.

And like I said, the context menu is provided by Nautilus in GNOME. If you want to use any other application for that, you would have to disable Nautilus to draw your desktop - and that would leave you without any Icons on the desktop (it's basically like a fullscreen window of the file manager).

---

### Post by breakerr on 2007-09-23
Roger on that sir...thanks again....I'm just curios now....the checkmark on every effect/plugin of Compiz Fusion I noticed that sometimes they don't start right away when I check them or enable them do I need to restart the desktop/video with Ctrl+Alt+BackSpace once I do a simple change in compiz or maybe if I change profile or its supposed to work right away ??????? Also noticed that sometimes when I boot into my Ubuntu desktop even with the backend set as GConf Configuration Backend selected the cube don't load and instead I get compiz working as if it was flat file configuration backend, do you know why ???? ( this happens even with the desktop cube General as On Big Cub and also general options - desktop size set to 4desktops)

---

### Post by Forlong on 2007-09-23
I recommend using the flat file only. And with that, it's supposed to work right away.

---

### Post by breakerr on 2007-09-23
> **Forlong said:**
> I recommend using the flat file only. And with that, it's supposed to work right away.

Now let mw know if I got this right or wrong.....Compiz Fusion in Gconf Backend and 4desktops have a failure to load and thats why I cant get the cube right away on every session or even with the Flat File selected I will be able to have the cube working ????:confused::confused:

---

### Post by Forlong on 2007-09-23
Sorry, I can't follow you there.

---

### Post by breakerr on 2007-09-30
> **Forlong said:**
> Sorry, I can't follow you there.

No worries and thanks for all the help forlong....I just wonder if you know about an odd behavior from Compiz Fusion....sometimes...randomly I noticed it turns off without any apparent reason....I mean...maybe Ill go to open system on the panel and BoOm some window borders blinks and no compiz on or enabled anymore but as soonest I restart or reset it comes back normally...this also happens after certain amount of time with the ubuntu sessions opened :confused: wEiRd 

Thanks again.

---

