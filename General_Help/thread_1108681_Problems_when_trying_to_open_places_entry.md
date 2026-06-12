---
title: "Problems when trying to open places entry"
date: 2009-03-28
forum: General Help
---

### Post by Roanoke on 2009-03-28
When I try and open an entry in the 'Places' menu, I get this entry. This only happens for file:// urls, it seems.

---

### Post by pastalavista on 2009-03-28
I'm sure there is more information about why this might be happening but it appears Nautilus is broken. What happens when you try and launch Nautilus (Alt-F2) type nautilus..?

---

### Post by Roanoke on 2009-03-28
Nautilus launches without a problem.

---

### Post by Bucky Ball on 2009-03-28
You just don't have an application set or that can open that kind of file. What kind is it? Find out, find some software that can open that type of file.

---

### Post by Roanoke on 2009-03-28
You do realize it's a location on my hard disk?

---

### Post by Bucky Ball on 2009-03-28
Same applies. You don't have an application set to open that location, like it says. You need to find one and set it. Are you figuring it should open with Firefox or a browser, is that it?

---

### Post by Roanoke on 2009-03-28
I'm figuring it should open with nautilus, like it always has.

---

### Post by Roanoke on 2009-03-30
Bump

---

### Post by pastalavista on 2009-03-30
I would try ```
sudo aptitude reinstall ubuntu-desktop
``` and then log out and back in

---

### Post by Roanoke on 2009-03-30
Nope, didn't work.

---

### Post by pastalavista on 2009-03-30
well, not knowing what you did to your system prior to the loss of functionality leaves me at a loss. greater minds than mine are called for.. or more investigation and explanation from you.

---

### Post by Roanoke on 2009-03-30
Well, I really don't know what to say. Maybe I removed a package I shouldn't have? Does apt keep logs somewhere?

---

### Post by pastalavista on 2009-03-30
> **Roanoke said:**
> Well, I really don't know what to say. Maybe I removed a package I shouldn't have? Does apt keep logs somewhere?
yes it does... it is called Synaptic Package Manager. It can tell you if you have any missing dependencies. But if you or some program you have run has changed any configuration files, it could be difficult to find. ( try: gconf-editor)

It's good, when using any OS, to pay attention and remember what you do to it. Good-luck with your problem. Sorry I was so snippy... too much coffee

---

### Post by Bucky Ball on 2009-03-31
[https://bugs.launchpad.net/ubuntu/+bug/208181](https://bugs.launchpad.net/ubuntu/+bug/208181)

Check the posts, something might jog your memory. Or it could be a bug which you could report. Try pasting, in a terminal:

```
sudo apt-get autoremove
```

This should clear anything that is 'half there' if you follow me. If you have accidentally (or intentionally) uninstalled 'bits' and you have anything looking for something that is not there anymore. And as mentioned, check Synaptics for broken dependency and fix packages.

Hope that is some help.

---

### Post by Roanoke on 2009-03-31
> **Bucky Ball said:**
> [https://bugs.launchpad.net/ubuntu/+bug/208181](https://bugs.launchpad.net/ubuntu/+bug/208181)
And as mentioned, check Synaptics for broken dependency and fix packages.

How would I recognize a broken dependency? I never use synaptic, so it's sort of alien.

And as for that bug, that's not my problem. My problem is that I can't open places **on my local disk in my linux partition** from the 'Places' menu.

---

### Post by Bucky Ball on 2009-04-01
System->Administration->Synaptic Package Manager->Edit (drop down menu)->Fix Packages

There is information in the bar along the bottom also which tells you about broken packages and dependencies. :)

---

### Post by Roanoke on 2009-04-01
That does nothing, so I guess I have all dependencies installed.

---

### Post by logic++ on 2009-04-01
Open a terminal and run
```
nautilus ~
```
and post what happened.
I would try also reinstalling the nautilus package and another one whose name I don't remember for sure but it is something like nautilus-scripts.

---

### Post by Roanoke on 2009-04-01
Nautilus opens without a problem.

---

### Post by Roanoke on 2009-04-10
Solved on IRC.
Needed to specify nautilus as the desired file-opening program.

---

