---
title: "Shmorgusboard of Problems/Issues"
date: 2008-12-17
forum: General Help
---

### Post by ZeroTruths on 2008-12-17
First off, let me say that I've been a longtime supporter of Ubuntu, and as of a couple months ago (when I first received my laptop w/ Vista) became a dedicated user of Ubuntu. Whenever I find something wrong, or something I want to change, my first inclination isn't to make a new thread on these forums and ask away, but instead I try to solve the inherit problem and be on my way. However, as of late, I've been running into a couple of issues, and between moving, working, and Finals, I haven't had the time or patience for looking into these issues. Ala why I come here now. I'll post the issues that I have (and some that I think of later) here, and will accept any help, be it for all of them, or just one problem in particular. And as always, all help is thanked.

PS: I'm not afraid to compile if need be...

Laptop Specs:
 Ubuntu 8.10, kernel 2.6.27-9-generic
 HP Pavillion dv5
 AMD Turion Dual Core 2.2GHz
 2GB Ram, 1GB Swap (Has yet to be used)
 Resolution: 1280px by 800px

**1)** When changing the volume through the Volume Applet, the volume change occurs exponentially. Basically, the only noticeable volume change occurs in the 75% to 100% of the sliding bar on the applet. Is there any way to change the volume change to linear (the way music applications change volume), or switch the global volume control to alsamixer?
**[EDIT]: Solved :D**

**2)** I've owned a Logitech VX Nano Cordless Mouse for a couple of weeks now, and am loving it. I've been able to configure all of the buttons (leaving the center for middle click), except for the side scroll-wheel clicks. I have not been able to find any guides for configuring this action, and was wondering if there was anyone out there who has been able to do so. Also, how would I go about mapping these actions to volume control (I already have XBindKeys running on startup, and figure the solution would involve messing with this).

**3)** I recently changed Boot Screen Splash management from usplash to splashy and have loved it (I love to customize btw). However, a strange things has been happening. Whenever I shutdown Ubuntu, it begins to shut down normally, and then for some reason, it switches to Root Console 1 (ctrl-alt-f1). Does anyone know why this is and/or how to fix it?

**4)** Another audio-related issue. Whenever I start up my laptop, I have to have my headphones plugged into the headphone jack in order to be able to use then in Ubuntu. If I don't, then all sound will come from my speakers, and if I try using headphones, no change will happen. Is there any way to fix this?
**[EDIT]: Solved :D**

**5)** An issue that I've had since I got Ubuntu is that I'm unable to use Hibernation or Sleep (Suspend) modes. Whenever I try to go into Hibernation, I get these messages:
```

ata2: softreset failed (device not ready)
ata1: softreset failed (device not ready)

```
I then close the laptop, but instead of turning off, it goes to the Locked screen (prompts for password). Once I login, the headphone issue comes back (see 4). If I try to Suspend, the laptop goes black, and simply stays like that. I have to force shut it down (hold down the power button for a few seconds) to use it again. Any help here?

**6)** This last one has been bugging me for a while now. I'd love to be using Conky, but the one thing that's stopping me is that fact that I'm always maximizing windows. I'd love to have Conky visible at all times, but the only programs that I know can do this are docks. Does anyone know of any other way, or any lightweight docks that can be rendered completely invisible? Oh, btw, I use the default Window Manager that come w/ Ubuntu (Metacity, I believe).

I know it's a lot, but any help would be appreciated.

---

### Post by chrisamiller on 2008-12-17
1) I assume you've checked your alsamixer settings, but have you also checked the other volume controls (specifically PCM)?  Go to Preferences, then check the appropriate ones to open them up.

4) Did you check under Volume Control >Switches to make sure the headphone switch is set appropriately.

---

### Post by ZeroTruths on 2008-12-17
1) Well, alsamixer changes volume as expected- linearly. However, I've isolated the problem to be the actual Volume Applet itself, and don't know how to change it's setting.

...Hold on, I think changing the device to control worked...Strange. Thanks :D

4) Hmm, so that's what those type of properties are for. I'll start messing with them and see what comes up.
[EDIT]: It worked! :D

---

### Post by HermanAB on 2008-12-17
Don't use Splashy - it is bad news - still very buggy and it will cause weird problems.

Cheers,

Herman

---

### Post by ZeroTruths on 2008-12-17
Well, the whole reason that I started using Splashy was because I have a wide-screen monitor, and as I understand, usplash isn't able to display wide-screen images.

---

### Post by ZeroTruths on 2008-12-29
*Bump for unresolved issues*
(Mostly #5: Suspend & Hibernate)

---

### Post by chipyoung on 2009-01-21
Ditto on the number 5 problem.  Sorry no help, but just wanted to let you know your not the only one.  It worked in 8.04 but not now in the latest release.

---

