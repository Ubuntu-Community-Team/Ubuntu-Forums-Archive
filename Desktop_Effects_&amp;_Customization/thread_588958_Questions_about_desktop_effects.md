---
title: "Questions about desktop effects"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by wrongOne on 2007-10-23
I use an Acer Aspire 5600 laptop for school and work, I recently made the switch to Linux via Ubuntu 7.04, from WinXP. I am glad to say I am enjoying the community support system and wonderful documentation about ....well everything and anything, and with a little more education I am confident I can make the move permanent. 

I have 1 problem that I cant seem to figure out yet, when I enable desktop effects, the wobble and ability to 'pull' down portions of windows works....but the option for workspaces on a cube doesnt seem to do anything. In fact, once desktop effects are enabled my multiple workspaces (in task bar) turn into 1 mini window that has no effect upon clicking or right clicking it. I was talking to a friend online that casually told me to press windows key + tab to check out how "awsome it was", but upon pressing it nothing seems to happen. It is as if i am not pressing the windows key at all, simply tabbing across functions on any given page. Anyone know if the windows+tab is related to the workspaces on cube, or what might be going wrong with the workspaces on a cube effect?

Thanks

---

### Post by Gwijde on 2007-10-24
I had this problem too. What you could do is go to dektop effects, uncheck the "windows on cube" option, change the number of desktops to eg 4, and then check the box again.

for a more permanent solution, check [http://ubuntuforums.org/showthread.php?p=3617169]("http://ubuntuforums.org/showthread.php?p=3617169")
btw, i tried this, didnt work for me

another option: upgrade to gutsy, mine works perfectly now :)

---

### Post by Perpetual on 2007-10-24
Make sure that you have compizconfig-settings-manager installed so that you can enable the effects.

```
sudo apt-get install compizconfig-settings-manager
```

Once installed, go to System>Preferences>Advanced Desktop Effects.  Then you can enable cube and other options related.

---

### Post by wrongOne on 2007-10-24
I tried that install but:

E: Couldn't find package compizconfig-settings-manage

is there anywhere i can manually dl/compile?

---

### Post by Perpetual on 2007-10-24
unless you typoed in your post, it should be manager, not manage.  Otherwise, open Synaptic (System>Advanced>Package Management) and search Compiz.  Then install it from there.

---

### Post by wrongOne on 2007-10-24
Which one should i install from the package manager?

There is no listing specifically for "compizconfig-settings-manager" 

The closest listed is Gnome-Compiz-Manager, or libgnome-compiz-manager0/-d

---

### Post by Perpetual on 2007-10-24
Booted my lappy, it's compizconfig-settings-manager.  Gnome-Compiz-Manager is for Compiz, not Compizfusion AFAIK.  Do you have Universe enabled in your Repos?

---

### Post by picopir8 on 2007-10-24
compizconfig-settings-manager is not in the feisty repository (7.04).   Gnome-Compiz-Manager is what you want for feisty.  There are tutorials to get compizfusion running under feisty but you have to tap into other repositories or just upgrade to gutsy.

---

### Post by Perpetual on 2007-10-24
> **picopir8 said:**
> compizconfig-settings-manager is not in the feisty repository (7.04).   Gnome-Compiz-Manager is what you want for feisty.  There are tutorials to get compizfusion running under feisty but you have to tap into other repositories or just upgrade to gutsy.

Ah, I apologize.  I forget not everyone is using 7.10.  My mistake.

---

### Post by wrongOne on 2007-10-24
ok i will try that, should i be using 7.10? is it a fresh install or just upgrade that it requires? or is it the same principle as windows...if you fresh install its simply cleaner (though i get the impression that updates might actually serve a purpose with ubuntu :P)

---

### Post by rundee_f on 2007-10-24
ah okay, i guess i can help u..

firstly, in 7.04, desktop effect is an experimental project, so wouldnt work perfectly
secondly, if u want to find "how awesome it was" Ubuntu desktop effects, do a complete removal of compiz (which come along in Feisty), then install CompizFusion (a brand new merger product between Compiz and Beryl, 2 best ever-known desktop effects in ubuntu)...

find the steps in [http://forlong.blogage.de/#blogentry_451](http://forlong.blogage.de/#blogentry_451) (scroll down till u find "The Best Way to Install CompizFusion in Feisty)

hope this helps...

---

