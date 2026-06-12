---
title: "Dell Mini 1012 crashing sometimes after opening lid"
date: 2012-08-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kvcckid on 2012-08-13
So I just installed 32 bit Ubuntu 12.04 on a Dell Inspiron Mini 1012 and sometimes when I open the lid it crashes.

I've tried telling it to both suspend when closing the lid and do nothing, but when opening the lid back up it randomly crashes; about 1/10th of the times.

Not sure if this issue has been tackled already or not.  Being looking around online and some ppl have said it was an issue with the sound card, most ppl have said it is an issue of kernel panic.

I did find this [http://gqshen.com/archives/442]("http://gqshen.com/archives/442") not sure if it will work

where sound I go from here?

---

### Post by kvcckid on 2012-08-13
Just tried the instructions in that link [http://gqshen.com/archives/442]("http://gqshen.com/archives/442")

Pretty simple, make a unload_module file containing the line

```
SUSPEND_MODULES="xhci-hcd"
```

in your /etc/pm/config.d/

So far so good.  The true test is if my granddad, primary user of the mini dell, can get it to crash.

Just have to wait for him to wake up in the morning.  I'll post back in a week to confirm or deny if this fixed the issue.

EDIT: nope, I just got it to crash

---

### Post by Tobeus on 2012-08-13
I'm not sure what you mean by "crashes" so I'm going to take a stab at a similar problem I had on my Dell laptop.  I had an SSD card installed in the reader and Ubuntu auto-mounts the card whenever it boots up.  Whenever I opened the lid it would sometimes freeze or the screen would stay black.

Here is the link I found to the issue (for an older version, but was still a problem on 10.04-11.04 last I checked, but not sure about newer versions):

[INDENT][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464712](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464712)
[/INDENT] 
And a link to a workaround for keeping it from happening again:

[INDENT][https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877/comments/29](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877/comments/29)
[/INDENT]
Of course, you could also check to see if you have an SD card in the reader (or a memory card of some kind) and take it out.

That's about all I have.  Good luck, and hope it helps!

-Tobeus

---

### Post by kvcckid on 2012-08-14
The dell does have an SD card slot but it just has a blank plastic cover in it.  The laptop has an SSD in it I think, it might be an HDD not an SSD.

I might end up just installing another distro and seeing if it has the same problem.  Just to check if it's a hardware issue or software issue.  It never did this in Windows 7 but ya' never know.

The dell also has another problem where the touchpad/trackpad wont work while plugged in, in all distors.  I looked it up and apparently the charger inter-fears with the touch pad so that is a hard ware issue.

I think I'll try Xubuntu next, or Lubuntu.  Something even lighter than ubuntu. Is there a crash log or something I can fish out to try look at b4 I start on the other distros?

---

