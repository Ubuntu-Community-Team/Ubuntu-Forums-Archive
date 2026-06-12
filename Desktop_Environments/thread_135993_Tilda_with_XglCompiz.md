---
title: "Tilda with Xgl/Compiz"
date: 2006-02-25
forum: Desktop Environments
---

### Post by saads on 2006-02-25
Does anyone have tilda running with Xgl/compiz?

---

### Post by Athropos on 2006-02-25
I do :)

It works like a charm, except the first time tilda is displayed where I sometimes get a blank window. This happens only the first time.

It seems also that the gnome-panel on top of the desktop is not taken into account by Compiz, some of my windows appear behind it. This happens also for Tilda, so I just changed the "Y pixel position to start" to 25 (the height of my gnome-panel).

---

### Post by saads on 2006-02-26
I'm getting 100% CPU usage and then nothing... i installed tilda from the repos.

---

### Post by Athropos on 2006-02-26
Mine comes from the Dapper Flight CD 4, I didn't upgrade since I installed it.
Did you already have some configuration files? Perhaps something is wrong with them. I just tried to rename ~/.tilda in order to start with an empty configuration, it still works.

---

### Post by madjo on 2006-05-31
[QUOTE=Athropos]I do :)

It works like a charm, except the first time tilda is displayed where I sometimes get a blank window. This happens only the first time.[/QUOTE]
I get this issue every other time. And I can't get it set to true transparancy, is there some trick to do that?

---

### Post by WiLLiE on 2006-05-31
Never heard of this one before, great!
One irritating thing though:
It doesn't stay at one place, it moves around everytime I hide/show it. (usually it pops up where the mousepointer is)

---

### Post by someusernoob on 2006-06-13
[QUOTE=WiLLiE]Never heard of this one before, great!
One irritating thing though:
It doesn't stay at one place, it moves around everytime I hide/show it. (usually it pops up where the mousepointer is)[/QUOTE]
Yes, i got that too, very anoying. Im glad im not the only one. Did you found a fix for it yet? Coz it's seems like a great program :D

---

### Post by mrvw0169 on 2006-06-13
I'm not sure what I did, but after one of the updates to compiz-quinn and xserver-xorg-air somehow made tilda stay put at the top... and to make it have "true transparency," I just place my mouse cursor above it and <alt>+Scroll...

tilda is nice, but yakuake is much much better, though for KDE...

---

### Post by mogmog on 2007-10-30
UPDATE: See my reply on page 2 for the final workaround.


I got here by a google search for "tilda xgl". I got this problem when upgrading to ubuntu gutsy and getting the Xgl desktop by default.

Deleting tilda's settings directory (~/.tilda) solved the problem of tilda showing up blank for me.
rm -r ~/.tilda


Hope this helps someone!

---

### Post by SeanHodges on 2007-11-24
> **mogmog said:**
> I got here by a google search for "tilda xgl". I got this problem when upgrading to ubuntu gutsy and getting the Xgl desktop by default.

Deleting tilda's settings directory (~/.tilda) solved the problem of tilda showing up blank for me.
rm -r ~/.tilda


Hope this helps someone!

mogmog you are a legend! I've been stuck without Tilda for ages because of this blanking problem, clearing the tilda dir did the trick!

For those who are worried about the recent malicious "rm" commands being posted these days, this one is safe (assuming you type the entire command correctly), but if you wish to be safe you can do the same operation without using the terminal:

1. Open your Home directory in Nautilus (Places->Home Folder)
2. Select View->"Show Hidden Files" in the menu bar
3. Find the directory called ".tilda" (note the "." prefix)
4. Delete it.

---

### Post by mogmog on 2007-11-27
When disabling the animated pulldown on a fresh configuration the problem returned. I'm returning now to post the correct solution which i found in Ubuntu's bug tracker ([https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/144175](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/144175))

> Enable animated pulldown from Right or Left, set delay to 1 usec. The result is about the same as without pulldown animation and it works correctly.


Also here's another forum thread on the topic where someone has provided a fixed .deb from CVS: [http://ubuntuforums.org/showthread.php?p=3605907#post3605907](http://ubuntuforums.org/showthread.php?p=3605907#post3605907)

---

