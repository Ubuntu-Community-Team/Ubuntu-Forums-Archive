---
title: "gnome window drag/close issues still not fixed?"
date: 2010-04-23
forum: Desktop Environments
---

### Post by inanutshellus on 2010-04-23
Ever notice how sometimes you'll close an application and the one behind it closes instead? Or how you'll drag a window and the one behind it will snap to your cursor?

YES OF COURSE YOU HAVE. Ubuntu/Gnome's been doing it for 6 months, since 9.10 was released. I've seen it on all four of my Ubuntu 9.10 machines.

I just installed 10.04 beta 2 and... it's still there. *head-meet-desk* I can't believe it. Seriously, I have to put up with this for another six months?

---

### Post by mcduck on 2010-04-23
> **inanutshellus said:**
> 
YES OF COURSE YOU HAVE.

Actually I've never seen such thing happening. And to be honest, this is the first time I even see anybody complaining about such bug in these forums...

Are you using Metacity or Compiz as your window manager? Try changing to the other one, in case that makes any difference.

---

### Post by coffeecat on 2010-04-23
> **inanutshellus said:**
> Ever notice how sometimes you'll close an application and the one behind it closes instead?

No.

> **inanutshellus said:**
>  Or how you'll drag a window and the one behind it will snap to your cursor?

No. :|

> **inanutshellus said:**
> I've seen it on all four of my Ubuntu 9.10 machines.

And I've seen this on none of my four machines. Curious.

A question: did you use a live CD or a live USB pendrive to install your systems? The reason I ask is that I discovered that the pendrive will remember various settings and change some system files. (It remembers details of network devices in /etc/udev/rules.d/70-persistent-net.rules, for example.) I wonder if something got changed/corrupted on the pendrive and then this got carried over to all four machines. Except this wouldn't apply if that was a fresh install of Lucid Beta.

Or, as mcduck points out, have a look at compiz. Always the first port of call when trouble-shooting weird happenings on the desktop.

---

### Post by inanutshellus on 2010-04-23
I have seen it at least once a day every day for the last six months. I haven't figured out exactly what does it. I think it's a combination of focus and maximized and floating windows. I was able to do it once just now, but it hasn't done it again yet. I believe it's always for the same application though. Meaning if you have multiple Terminal windows, for example, it affects the other Terminal windows, not, say, an also-open Firefox window. 

The windows don't even have to be on top of each other or in the same monitor. I'll go to grab a windowed terminal and the maximized terminal in another monitor will windowize and move under my cursor.

I've seen it on my home desktop (an older, custom built dual core machine) and on all four of the Dell laptops (d620's and d630's) that my team at work uses. We all know it, see it, and hate it.

---

### Post by coffeecat on 2010-04-23
> **inanutshellus said:**
> I think it's a combination of focus and maximized and floating windows.

...

I believe it's always for the same application though. Meaning if you have multiple Terminal windows, for example, it affects the other Terminal windows, not, say, an also-open Firefox window. 

I think I understand what you mean. No, I've not seen this, but I'll watch out for it.

---

### Post by inanutshellus on 2010-04-23
It may also have something to do with multiple monitors. One co-worker says it doesn't happen for him at home, where he only has one monitor.

---

### Post by inanutshellus on 2010-04-23
> **inanutshellus said:**
> I believe it's always for the same application though. Meaning if you have multiple Terminal windows, for example, it affects the other Terminal windows, not, say, an also-open Firefox window.

Ok, this isn't true. I had a maximized terminal window in my secondary monitor. I clicked on the Pidgin icon to bring up the contacts list, it came up on top of the terminal. I double-clicked a contact then dragged the contact's window. 

Instead of the contact's window moving, the maximized terminal window de-maximized and attached itself to my cursor. 

Attempts to reproduce it failed, however. =/

---

### Post by coffeecat on 2010-04-23
> **inanutshellus said:**
> It may also have something to do with multiple monitors. 

If it is then this is maybe why I haven't seen it - I never use multiple monitors on my desktops. I will, however, hook up an external monitor to a laptop and try this when I have time. It sounds like a bug that ought to be reported. Have you looked on [Launchpad]("https://bugs.launchpad.net/ubuntu")?

---

### Post by inanutshellus on 2010-04-26
> **coffeecat said:**
> Have you looked on [Launchpad]("https://bugs.launchpad.net/ubuntu")?

AH HAH!

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/516049](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/516049)

Just have two windows, maximize one with double-click, then try to grab or drag another. Well, at least in understanding it I can avoid it. I'll just stop using double-click to maximize my windows. Problem solved.

---

### Post by mcduck on 2010-04-26
> **inanutshellus said:**
> AH HAH!

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/516049](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/516049)

Just have two windows, maximize one with double-click, then try to grab or drag another. Well, at least in understanding it I can avoid it. I'll just stop using double-click to maximize my windows. Problem solved.

That could explain why I've never seen such thing happen, as I always set the doubleclick on title bar to shade windows... :)

---

