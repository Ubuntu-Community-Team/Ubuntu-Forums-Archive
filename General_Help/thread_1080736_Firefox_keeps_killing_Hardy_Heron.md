---
title: "Firefox keeps killing Hardy Heron"
date: 2009-02-25
forum: General Help
---

### Post by johnuk on 2009-02-25
I'm running on a minimalistic system with 256mb of ram and some slow 1 ghz processor or similar.

I'm not running any memory intensive applications. Most of the time I'm only in firefox doing some browsing with a few tabs open and have pidgin going.

I've been having really, really annoying problems with browsing where when I click a tab, it'll just hang. It'll sometimes do it if I click a java action, like send on a post, it'll do the same. I've also wondered, but not been able to identify, if it hangs when people try to send me a message on pidgin sometimes.

It seems almost random when it will and won't do this. Sometimes I'll have some tabs open with flash running in them, which I know is memory hungry, and it'll be okay. Then I'll be running very little and it'll go.

This is driving me nuts! Yes I've updated.

---

### Post by Yashiro on 2009-02-25
It's the browser plugins. Most likely flash, it's garbage on Linux.
Is this Ubuntu 32 or 64? I assume 32 with that spec.

---

### Post by taurus on 2009-02-25
How big is your swap partition?

Applications -> Accessories -> Terminal
```
free -m
```
On the other hand, maybe you should consider using Xubuntu (XFce4 window manager) since it's a little lighter on system resources compare to Gnome.

---

### Post by johnuk on 2009-02-25
It's 32 yep.

Xubuntu could be an idea. Can I swap over to it without having to reinstall?

Here's the memory reply;

             total       used       free     shared    buffers     cached
Mem:           502        451         51          0          7         85
-/+ buffers/cache:        358        143
Swap:         1466          7       1459

Free = 51mb? I'm not running flash atm, only text / forum tabs and pidgin. Will the plugins (flash) continue assigning it's self memory even if I'm not running any videos? I don't think any of the pages I have open are running ads with flash either. I may have to look into that firefox plugin for blocking flash content I don't allow. It really does rip through the ram as if it's trying to get all of it to one tab.

I do frequently see the cursor with a load symbol on it when it hangs, so I expect the memory is the issue.

---

### Post by Yashiro on 2009-02-25
Enter about:plugins in Firefox.

Paste the list of crud here.

---

### Post by taurus on 2009-02-25
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
At the GUI login screen, choose which session you want to log in.  Make XFce4 as your default if you wish.

---

### Post by johnuk on 2009-03-02
Thanks guys, I think this is about solved. I've had one crash with firefox in Xunbuntu, but was running a whole lot of tabs. So far, all seems good; if not quite as good looking atm.

Is it possible / worth wiping the gnome desktop to clear some disk space? This computer is a good five or so years old.

---

### Post by taurus on 2009-03-02
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by johnuk on 2009-03-03
Thanks, problem solved!

---

