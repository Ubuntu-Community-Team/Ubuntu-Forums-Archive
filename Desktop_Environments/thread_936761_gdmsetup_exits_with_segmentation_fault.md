---
title: "gdmsetup exits with segmentation fault"
date: 2008-10-03
forum: Desktop Environments
---

### Post by thomasyen on 2008-10-03
Today while trying to make adjustments to my login theme using System -> Administration -> Login Window, the gdmsetup window opened for about two seconds and then crashed. I tried invoking it from the command line, but it also exited two seconds later with a segmentation fault. Never had this happen to me before. Any ideas on how to fix this?

---

### Post by Sycron on 2008-10-03
What version of ubuntu are you using ?

---

### Post by thomasyen on 2008-10-03
I use 8.04 Hardy.

---

### Post by Sycron on 2008-10-03
On my computer, and on the liveCD also gdmsetup just works. Can you reset the settings to default somehow ? Or could you tell us what you've changed ?

---

### Post by thomasyen on 2008-10-03
I'm not sure what I changed. Maybe you could tell me how to revert to default? (I tried reinstalling gdm - didn't work)

---

### Post by Sycron on 2008-10-03
```
sudo apt-get --purge remove gdm
sudo apt-get install gdm
```

---

### Post by thomasyen on 2008-10-03
After doing what you said and rebooting, I found that gdm behaved strangely - every word of the filenames and system responses (every single letter) had been replaced with small rectangles! I had no choice but to reinstall. So now there is no problem with my computer. But for future reference, purging then reinstalling gdm is probably not a good idea.

---

### Post by drshields on 2008-10-04
I'm also getting the same problem.  

System->Accessories->Login Window, it disappears after 1 second.

So I try to do it via terminal and get this:

```
$ sudo /usr/sbin/gdmsetup
Fontconfig error: "~/.fonts.conf", line 2: no element found
Segmentation fault

```
This just started today from what I can tell... One other thing I'm noticing that's weird, System->Preferences->Appearance, Click on the Customize button I'm not seeing any preview icons (except for a question mark indicating the icon is missing) for the Controls and Icons tabs.  I'm not sure if it's related, but this wasn't happening prior either.  

The only thing I've installed recently is Cairo dock and some fonts.  I'm on 8.04...

---

### Post by thomasyen on 2008-10-10
Now that you mention it, I also seem to have installed Cairo-dock prior to having this problem. Maybe you could file a bug?

---

