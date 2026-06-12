---
title: "Remote GUI &quot;sudo&quot; password entry"
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by beanlover on 2007-04-27
I'm not even sure what to call this but here goes:

I'm trying to disable the effect of the desktop being "grayed out" when linux needs my password to perform administrative tasks.  What takes a fraction of a second on a local desktop can turn into a 15-30 second ordeal when connected remotely.

Is there any way to change how the system prompts me for my password in Gnome?  What would be nice is to just have the dialog box pop up with out the effect if possible.

Hope this makes sense.

I'm running 6.10 32 bit.

Thanks!

B

---

### Post by garlik42 on 2007-04-27
There may be another way, but this is how I do it. First off, I use VNC almost exclusivly I am almost never actually at the machine.

I login remotly as root, to perform functions that require superuser access. No prompting at all.

Then when I am just doing normal day to day stuff I login as my user id.

---

### Post by Aetherius on 2007-04-27
one *messy* way of doing it is

```
sudo apt-get install kdebase
```

and then use "kdesu" instead of "gksudo" on whatever launcher you are using

---

### Post by beanlover on 2007-04-27
Hmm...thanks for the replies (super fast!) but neither of those options sound like something I want to try.

I have already managed to disable a lot of animiations (the last of which was the throbbers on firefox) which has increased the responsiveness of the remote gui quite a bit.   This is the last thing I think I need to conquer to make it how I want it.

Is the version of GKSUDO on Ubuntu a customized version for Ubuntu or does it act the same way on other distros?  If it's custom maybe I could get the code and alter it for myself or grab a generic debian build of it.

---

