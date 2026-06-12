---
title: "add/remove problems"
date: 2006-10-02
forum: Desktop Environments
---

### Post by the.phantom on 2006-10-02
i am a old guy and installed ubunto on my system last night.
I used the add/remove to install t-bird without any trouble. i got all to work and it was late but i tried to download firestarter and a virus scanner
with add/remove


it asked if i want multiverse and i said yes
it found and started to install both

but it was way past my bedtime so i clicked "cancel"

this morning i tried and get a message that 
not available on any software channel

what did i do wrong, can it be fixed?
if they are not available what will work for a newbie that needs a firewall and av and best way to install  ( i looked in the advanced setting of add/remove and nothing there like firestarter or av?
( i see clamav but it is command line ( so maybe later)

---

### Post by Fass on 2006-10-02
Go into System -> Administration -> Synaptics, "Settings -> Repositories." Make sure multiverse and universe are enabled there and then run a "Reload." Then "Search" for firestarter. Does it find it now? If so, right click it and choose "Install" and then click the icon with the little tick - might be called something like "execute" or whatever (my Synaptics is in Swedish and I don't know what they've named it in English.) That should install it.

---

### Post by the.phantom on 2006-10-02
thank you very much fass !!
you saved my day
I do have one more problem with add/remove if you can help
i have the firewall but
virus scanner is playing hard to get !

i did add it and watched it install in the small terminal window
and it said it put it in Applications /accessories

well not there i did a search for agis virus scanner, virus scanner and no results
but it thinks it is installed and looked through the program list and it is not there
any ideas? or know of a good virus scanner that a newbie could install?

---

### Post by Fass on 2006-10-03
> **the.phantom said:**
> well not there i did a search for agis virus scanner, virus scanner and no results
but it thinks it is installed and looked through the program list and it is not there
any ideas?

If you right click the package in Synaptics and look at its properties, there is a section in there about "Installed files" or something like that. You'll be able to see what files it installed where by looking at it. Although, while a firewall is a nice thing to have, anti-virus for Linux is not all that needed (I've never used it) if you're planning on just using it to "scan and protect" your Linux box. It's more useful if you're planning on running a server of some sort and want to scan mail or files it handles, or have a windows network you want to keep clean.

---

### Post by the.phantom on 2006-10-04
i got it installed, but buggy so uninstalled it !

it would say a new update do you want to update, i  could click yes, and about 30 sec later it would say it is now current, but there was no traffic on the web ;-(
"
i' looking at avast for linux and will have to "deb" it so that is in the future
thanks for the help!

---

