---
title: "New desktop LnF is utterly HORRIBLE!!! - How do I go back to Oxygen?"
date: 2016-06-09
forum: Desktop Environments
---

### Post by scunacc on 2016-06-09
Hi all,

OK. I've been a long time Linux user - since 1993. 

I have been a Kubuntu user for years. I have a finely honed desktop that I have tweaked to be exactly how I want it in look and feel on 14.10 (and coming from earlier releases too).

I am using a customized Oxygen / Oxygen-GTK LnF. I'm using Plastik window decorations. I have shadows and curves and roundness in my LnF. Life is good. Great in fact. 

***_I DO NOT WANT TO CHANGE IT!_*** :P OK. Call me a dinosaur, but there we have it.

I cannot ***_STAND_*** the flat look and feel that is becoming trendy. I love skeuomorphism. I hate flat. Did I mention I hate flat? The world is not flat.

So, imagine my horror when I installed 16.04 in a VM the other day to help a colleague out by matching what they were doing in a 16.04 install and seeing this *_**HORRIBLE UGLY FLAT**_* look and feel that is there for the window manager / desktop. 

I would ***_NEVER_*** want or use that Look and Feel. It's *atrocious*. 

My current desktop is stable. I am content with 14.10 for the time being, (I only updated from **11** *last* year! :o ), and have no desire or need to update to 16.04 on my main desktop yet.

However, if and when I do move or have to move to 16.04 on my desktop, how would I be able to retain my current look and feel? 

I did look through various posts and people were saying that GTK support was dead. I looked over the settings in the 16.04 VM and could see very little customization for look and feel. None of the desktop themes I saw at all would work for me, and I did look, and over at kde-look as well. 


OK. I may be missing something obvious. I didn't spend a great deal of time investigating the LnF in the VM since I was more concerned about logging in to it via ssh and doing some actual work via the CLI. 

But I would want to change this LnF to something I would be happy with. And, yes, it's hard perhaps to convey the depth of revulsion I have to the flatness that's becoming trendy, but I ***really*** do hate it!!! :)

This is eminently possible to change. This is Linux!!! Anything's possible! :D So, how have you folks managed to overcome this backwards move in LnF? What's the recommended path to restoring sanity in LnF?

Kind regards

Derek.

---

### Post by buzzingrobot on 2016-06-09
The bits and pieces needed to get that traditional look are, I think, in the 16.04 repos and can be added. Searching in Synaptic, say, for "oxygen" should find most of them.

KDE4, though, is dead and essentially unmaintained and the shovels are filling the grave. You can stay with it via LTS distros like 14.04 (or Mint 17.3, based on 14.04), or the current Debian stable, etc.  But, those distros will have no choice but to move to the new KDE when they move on themselves. It's directly analogous to what happen when the Gnome project moved from Gnome 2 to Gnome 3.

---

### Post by scunacc on 2016-06-09
> **buzzingrobot said:**
> The bits and pieces needed to get that traditional look are, I think, in the 16.04 repos and can be added. Searching in Synaptic, say, for "oxygen" should find most of them.

KDE4, though, is dead and essentially unmaintained and the shovels are filling the grave. You can stay with it via LTS distros like 14.04 (or Mint 17.3, based on 14.04), or the current Debian stable, etc.  But, those distros will have no choice but to move to the new KDE when they move on themselves. It's directly analogous to what happen when the Gnome project moved from Gnome 2 to Gnome 3.

Ha! :) I'd already started down that route this morning - no success thus far, but I'll keep pursuing it. Have to do some hunting to find what's needed.

There *must* be a better way than to give in though to the new flatness! :D

Kind regards

Derek.

---

### Post by scunacc on 2016-06-09
Well, I've made some progress

Installed: 

apt-get install oxygen-*
apt-get install fonts-oxygen gtk2-engines-oxygen kde-style-oxygen kde-style-oxygen-qt5 kwin-decoration-oxygen liboxygenstyle5-5 liboxygenstyleconfig5-5 plasma-theme-oxygen ttf-oxygen-font-family

.... and here's the result:

[https://app.box.com/s/3snyeb9t482i4fs0kbkvu37jfna6bh3q]("https://app.box.com/s/3snyeb9t482i4fs0kbkvu37jfna6bh3q")
[https://app.box.com/s/o6budpyq4mefdm5yfsbna3dkmtpmez08]("https://app.box.com/s/o6budpyq4mefdm5yfsbna3dkmtpmez08")

so, ... I'm a bit happier now... A tad :)

---

