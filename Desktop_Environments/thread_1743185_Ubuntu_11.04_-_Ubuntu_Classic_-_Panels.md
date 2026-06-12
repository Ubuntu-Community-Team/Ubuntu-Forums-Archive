---
title: "Ubuntu 11.04 - Ubuntu Classic - Panels"
date: 2011-04-29
forum: Desktop Environments
---

### Post by peshko-lnx on 2011-04-29
I have a simple question. I moved from Maverick to Natty and everything was flawless. I didn't like Unity, so I am running Ubuntu Classic.

What I noticed is that at the bottom panel I cannot re-arrange the open programs. For example if I have FF, TB and Text Editor ope in that order, I'd like to reorder it in the panel, so that TB is first, FF next and Text Editor last. I was able to do that in Maverick with no problem.

How can I do that?

---

### Post by peshko-lnx on 2011-04-29
Anybody?

---

### Post by ankspo71 on 2011-04-29
Hi,
This is working for me, but I think it seems to be a little different from before. I'm not normally a Gnome user anymore, so maybe I am confusing how things are supposed to be in Gnome and KDE. 

Anyways, I noticed that in Ubuntu 11.04 with Ubuntu Classic, I have to drag one window button on top of the other window button to be able to change the application order in the window list applet... but it doesn't work for me if I try to drag a window button 'before' the other window buttons.

So if I have Gedit, Firefox and Chromium open, and then I want to have the chromium button first in the window list applet, I need to drag chromium's panel button on top of gedit's panel button.

Hope this helps.

---

### Post by Krytarik on 2011-04-30
Usually it's like *ankspo71* described it, however I noticed that sometimes you need to drop it right or left of the middle of the button you are dropping it on, in terms of the mouse pointer position. So, it's not really predictable if and how it works. I'm running Lucid, like my profile states.

Greetings.

---

### Post by alexanda on 2011-05-01
Similar problem here.  I have tried the suggestions listed, and it doesn't matter where I drop the item, they do not rearrange.

I realize it may be a bit compulsive, but there are numerous programs that are running 24x7 and always having them accessible from the same place on the bottom of the screen speeds up usability, so I would really like to be able to rearrange them to be in the expected locations.

---

### Post by peshko-lnx on 2011-05-01
Thanks guys, in Lucid I didn't have any problems. In Nutty thou, no matter where you place it, they never move...Maybe I'll open a bug

---

### Post by peshko-lnx on 2011-05-01
Submitted a bug - [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/774876](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/774876)

---

### Post by alexanda on 2011-05-02
A little additional information, on a separate machine I just did a clean install of 11.04 x86 and within Ubuntu Classic I can rearrange the running programs without incident.  The machine where I identified the error is an x64, upgraded from 10.10.

So, this is either:

- An issue with the x64 build, but not x86

- An issue with upgraded systems, but not clean installs

or

- An artifact from some unexpected change we made to our systems that hasn't yet been identified

---

### Post by Krytarik on 2011-05-02
@alexanda: Since it seems like the cause of that is a conflict between Gnome-Panel and Compiz, can you please confirm if Compiz is running in that particular install, by either testing the special features of it, or by running:
```
ps ax |grep -v grep |grep compiz
```

---

### Post by fmarcoz on 2011-05-05
Hi,
I have this same exact problem, upgrading from Ubuntu 10.10 x64 and using Ubuntu Classic.

ps ax |grep -v grep |grep compiz
1590 ?        Sl     0:23 /usr/bin/compiz
1688 ?        Ss     0:00 /bin/sh -c /usr/bin/compiz-decorator

Thanks.

---

### Post by ErikJanVens on 2011-05-05
> **Krytarik said:**
> @alexanda: Since it seems like the cause of that is a conflict between Gnome-Panel and Compiz, can you please confirm if Compiz is running in that particular install, by either testing the special features of it, or by running:
```
ps ax |grep -v grep |grep compiz
```

I have the same problem and when I test for compiz the result is
```
/bin/sh -c /usr/bin/compiz-decorator
```
So I guess compiz is running. I cannot find anywhere to turn it on or off, or change settings. What to do now? I like to rearrange the panel.

---

### Post by Krytarik on 2011-05-05
@fmarcoz: I take that you already found a temporary workaround for the bug reported here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/697358](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/697358)

@ErikJanVens: Try the workarounds mentioned in the bug report, and possibly enlist yourself as affected.

---

