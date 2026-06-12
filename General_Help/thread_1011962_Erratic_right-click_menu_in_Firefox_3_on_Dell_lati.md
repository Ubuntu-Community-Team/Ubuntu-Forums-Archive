---
title: "Erratic right-click menu in Firefox 3 on Dell latitude D830"
date: 2008-12-15
forum: General Help
---

### Post by BOBSta on 2008-12-15
Hi all

Recently I've noticed Firefox behaving erratically.  I was wondering if anyone else had come across these problems and if they are related to Ubuntu (or Linux in general), a general FF problem, or a hardware issue?

I'm running Ubuntu 8.10 32bit on a Dell Latitude D830 laptop and using Firefox 3.04 with AdBlockPlus, Foxmarks and NoScript.  The problem happens when using either the internal trackpad buttons or an external mouse (I have dell, Logitech and Kensington USB mice).  I don't use any other apps for long enough to confirm if the problem happens in them as well.

I start browing web and everything works fine for about 10 to 15 mins.  After that strange things start to happen whenever I right-click on a link, be it a text link or an image link.  This behaviour is instead of the right-click context menu appearing in FF and it seems to get worse over time, e.g.:

1) link will auto open straight away in a new tab - sometimes in a new window even though my FF default is set to open links in a new tab.

2) Evolution config window appears as if I've chosen to "Send Image" or "Send Link" via email - I haven't configured Evolution as I use web-email.

3) "Set As Desktop Background" window appears.

So:
Is this a bug in FF3?
Is this a bug in the linux/ubuntu mouse drivers?
Is this a bug in Gnome/X?
Is this a bug in Ubuntu or does it happen on other Linuxes?
Is it a hardware issue?

The laptop is dual-booted with Windows XP pro SP3 (32bit) and FF3.04 works fine in that on the same websites.  One issue of note might be that in Windows, when any external mouse is connected, the mouse pointer will sometimes "drift" across the screen of it's own accord and I've discovered this is an issue with many different dell laptops which use the same type of trackpad as mine.

The recommended fix is to set the BIOS (mine is up to date) so the internal trackpad is set to auto-disable itself on connection of an external mouse.  I've done this, but problem still occurs.

Anyone got any ideas?

Thanks
Rob.:confused:

---

### Post by BOBSta on 2009-01-06
Have updated to Firefox 3.05.  Still getting same problem.

Have now found out how to middle click to open in a new tab, which is getting around this problem... for now.

---

### Post by bryncoles on 2009-01-06
my firefox 3 on a dell inspiron1525n is buggy as hell too - sounds like the same issue. i feel your pain!

---

### Post by mwillams73 on 2009-01-09
same here weird right clik with no context menu, works fine sometimes and sometimes not, running amd1.9 gigherz

---

### Post by morbid_bean on 2009-01-09
yup same here i thought i was just crazy so i never said anything...so now i fell better

---

### Post by mwillams73 on 2009-01-11
Still looking into the right clik context menu being buggy, it seems to me that its not just you guys's dells, cause mine (AMD 1.9 gigherz,gigabyte motherboard,1 gig ddr2 ram, nvidia 6200 LE 256 ddr2,) is having the same problem. Mines custom built so I dont know why only us 4 or 5 people are having this problem. I would think that if more peoples right cliks were buggy that somebody would know something. Really its just an annoyance but i do alot of online art searches and it happens more and more often, If I can figure this out I'll let you know, Keep us updated so we know if anything changes.

---

### Post by mwillams73 on 2009-01-11
ok so alot of other people are having this problem, and so far theres no fix for it, yes it is a bug but theyve been working on it since april of 2008 and still no fix, I did find however a workaround in another post heres the link,

[http://ubuntuforums.org/showthread.php?t=830676&highlight=right+click+is+buggy+in+firefox+3](http://ubuntuforums.org/showthread.php?t=830676&highlight=right+click+is+buggy+in+firefox+3)

Also heres the launchpad bug report so you guys will know its not just us,

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295)

In the first link theres a guy who has a link to mozilla and you can download a mouse gesture add on , I dont know if this works as of yet but Ive downloaded the add on and I'll test it out if it works I'll let you know.

---

### Post by mwillams73 on 2009-01-11
Ok so ive only been using it for 15 minutes and it seems to work, all I did was download the add on and the erratic context menu problems seem to be gone , Im gonna wait till tomorrow to make sure but for now heres the link for the add on try it out for your selves and let me know ok?

[https://addons.mozilla.org/en-US/firefox/addon/39](https://addons.mozilla.org/en-US/firefox/addon/39)

---

### Post by mwillams73 on 2009-01-12
So since last night and today ive used the mouse gesture add on for fire fox and the erratic right clicks are gone, its been 4 hours today and an hour last night. I hope this helps you guys, all is well with ubuntu again, Yay!!!!!!!!!

---

### Post by BOBSta on 2009-01-15
Thanks for the extra info guys!  Looks like it's not just me being picky afterall.

I had a look on Mozilla's bug tracking website for Firefox ([https://bugzilla.mozilla.org/]("https://bugzilla.mozilla.org/")) and searched for "right click" - it returned 200 reported bugs, so it looks like we are not alone.

Here's hoping someone more technical will be able to advise something soon...?

Bob.

---

### Post by BOBSta on 2009-03-09
Under 3.0.6 and now 3.0.7 this seems to be a little better (happening less), but it does still occur.

I'm now of the oppinion that it's not a hardware issue, but rather a Firefox interface issue - it's just not detecting the right-click properly, or isn't clearing the mouse buffer or something like that and registering subsequent movement / clicks.

---

### Post by kanikilu on 2009-03-09
I've noticed this sometimes as well, on more than one computer (desktop and laptop), it's very erratic and hard to reproduce on cue...

I've managed to just live with it by getting into the habit of holding down the right-mouse button (which has never failed) rather than "clicking and letting go and hoping the menu comes up".

I'll check out that FF add-on as well...

---

### Post by moopet on 2009-03-13
The add-on workaround is all that's listed on the bug report - but the add-on doesn't exist (that link doesn't work and searching for "mouse gestures" fails)

Anyone got a link that works?

This has been bugging me for some time!

---

