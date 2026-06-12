---
title: "Chromium Browser Update"
date: 2022-06-19
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2022-06-19
I have used the Chromium Browser for a while, I moved from Chrome to get away from a lot of Google things. I have Firefox, but it has gotten bogged down over time. At some point  my Chromium was update to a snap and this week among other things all of my saved passwords were lost. It appears that the browser no longer saves the passwords but they are saved in you Google account. 

I'm probably missing something.

Is it possible to get a .deb package or to not log into a Google account to save passwords?

---

### Post by pantazi on 2022-06-19
I'd give Brave browser a try, no problems for me over one year of use.

---

### Post by grahammechanical on 2022-06-19
In the Ubuntu 20.04 software store Brave is also a snap package. I also understand that Chromium has been a snap package for a while. It was one of the first main applications to be packaged as a snap. 

Regards

---

### Post by rsteinmetz70112 on 2022-06-19
Thanks, I've used Brave on Windows and may try it. I'm not sure when Chromium went to a snap package, I've used it for a while. It recently "updated" and blew away all of my saved passwords and as far as I can tell I can only save them with google sync, something I don't want to do. Fortunately I still have them in Firefox.

---

### Post by philhughes on 2022-06-20
Chromium is able to save passwords locally, without being logged into a Google account. There was a bug when Chromium was first migrated to a snap that meant it couldn't see stored passwords. May be this is your issue? There is a fix in the bug report (or you can do the same by opening Ubuntu Software, selecting chromium, clicking permissions and making sure "Read, add, change or remove saved passwords" is enabled).

[1] [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1849160](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1849160)

---

### Post by guiverc on 2022-06-20
I'd suggest scanning the bug report @philhughes mentioned, whilst I don't think it impacts systems today, I still think it contains useful knowledge.

I've had my chromium configuration lost three times since it moved to *snap* (*in 2019, **not counting issues with the mentioned bug report*) and on each occasion I got them back rather easily.

As I understand it, if a *profile *is deemed to *invalid or faulty*, a new one is created, meaning all your prior settings *can *disappear (*esp. if corruption is discovered*). However they still exist on disk, and you can just exit the program, then copy them from the prior directory to the new ***current* **profile directory.

I can't find my *fix* notes; nor find a useful command in my .bash_history, but as I recall it was just copying files from one directory in ~/snap/chromium/ to the new ~/snap/chromium/current/ directory.  (*the first time I copied everything, the subsequent times I only copied what I wanted... I can't recall why I was more selective on subsequent times but there was likely a reason*).

I'd have a look at what's in your **~/snap/chromium/** directory; and would hope you can spot your past, and current profile and work it out from there. 

If you can't work it out, I can install chromium on a *QA-test* or *support* box, muck up its profile so it'll create another and work out how I'd fix it, and thus, hopefully, create more precise instructions than this ***vague*** reply..  (*or I'll look again and hopefully find my text file describing what I did*), but be aware you can (*in my experience*) get passwords back, or at least I have.

*Note:  I am aware google change the ABI/API on passwords meaning they can only be saved on google servers, but I've never used their servers for that, and got the passwords back at least three times using chromium.. but as it wasn't recently (why I'm vague) it was also likely before the ABI/API change, though I don't think that will impact it.*

---

### Post by rsteinmetz70112 on 2022-06-20
Thanks, That seems likely what happened, the profile got corrupted. 

The computer is at home so I'll look at it this evening and report back. 

One odd thing is I have a bookmark bar of my most common websites. That remained and still works. But when I enter a password I get prompted to save it but it doesn't save or if it does I get asked the next time I visit the site.

---

