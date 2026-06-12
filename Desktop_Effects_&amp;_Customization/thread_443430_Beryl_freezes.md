---
title: "Beryl freezes"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by bartoz on 2007-05-14
Hi everybody.
I installed beryl 0.30 git (from svn repository) on my ubuntu feisty (but I got the same problem with beryl 0.20).
What happens is that sometimes (I noticed that it usually is when opening a new window) all the graphical interface except the mouse pointer freezes and it doesn't get any input (for instance I can't restart the x server by hitting Ctrl + Alt + Backspace), I can only move the mouse pointer all around the screen, but can't interact with anything.
Is there anyone else with the same problem?
Does anybody know what can be the cause of it?

Thanks in advance.

---

### Post by bartoz on 2007-05-15
bump..

---

### Post by S.Peterman on 2007-05-15
I get the same issue when running Beryl. I also get window burn, where if I move the window, a very transparent version of the window still shows on my background. I too would be interested in what I can do to fix this. Thank you

---

### Post by bartoz on 2007-05-15
I don't have the "window burn" problem, though the freezing problem is still there..

I noticed also another issue. (it's a bit off topic in fact..)
To be able to watch videos with beryl active I had to set the video output to X11. This way videos play correctly (while with the default option I saw black screen and caught glimpses of the video playing only while moving or resizing the window itself), but the playback uses a lot of cpu and maximized videos happen to be not totally smooth.
Is there a way to make the video card do the work instead of the cpu?

---

### Post by Soybean on 2007-05-15
> **bartoz said:**
> To be able to watch videos with beryl active I had to set the video output to X11. This way videos play correctly (while with the default option I saw black screen and caught glimpses of the video playing only while moving or resizing the window itself), but the playback uses a lot of cpu and maximized videos happen to be not totally smooth.
Is there a way to make the video card do the work instead of the cpu?

The way I understand it, the video card is busy doing crazy things for Beryl, so it doesn't have time to be messing around with your videos. ;) I mean, I'm sure the actual explanation is a little more complicated than that, but that simplified version was enough to satisfy me. The situation is normal, anyway.

The freezing is less normal, but I think it happens to a lot of people from time to time with Beryl. Actually, do you have an NVidia card? I think there's a bug in the closed-source NVidia drivers that can lock up your kernel.

---

### Post by Bohlio on 2007-05-15
I dont think I have Beryl, but i have a freshly installed version of Fiesty Fawn and I get the same problem if i have the "Desktop Effects" enabled...

---

### Post by bartoz on 2007-05-16
> **Soybean said:**
> The way I understand it, the video card is busy doing crazy things for Beryl, so it doesn't have time to be messing around with your videos. ;) I mean, I'm sure the actual explanation is a little more complicated than that, but that simplified version was enough to satisfy me. The situation is normal, anyway.

The freezing is less normal, but I think it happens to a lot of people from time to time with Beryl. Actually, do you have an NVidia card? I think there's a bug in the closed-source NVidia drivers that can lock up your kernel.

I'm pretty sure thath the "crazy" things that beryl makes the video card do are not so crazy.. I mean, the card potential is far bigger than what is required by beryl.
And also, when I play videos I'm not using any of the beryl plugins to do anything..
The problem is that if I set the video card to render the videos (as I think it means to leave the default option) the videos are played, but images can't be seen if not from time to time if I resize or move the window.
Setting the video outoput mode to X11 (I think) means that the video is rendered by the cpu, through the X-server.
So the question is: "How to make videos work with beryl and the "default" video output?"

Anyway I've got an ATI Mobility X700.

---

### Post by Tatty on 2007-05-20
i have the exact same freezing problem with both compiz and beryl  :(

It works for a while generally fine, although every now and again it will freeze for 5-10 seconds while my processor goes crazy for a bit.  ive been monitoring this with the system monitor and using "top" in a terminal.  and it seems to be that every time this happens, one of the cores in my cpu has maxed out, and when the system starts working again its always beryl or compiz which are sitting at the top of my "top" list.

Then eventually it simply hangs up and the only thing i can do is move my mouse about or switch off my machine by holding down the power button.

And windows users keep laughing at me :cry:

---

### Post by GuillemVTR on 2007-07-13
Hi all!

I've got the same problem using x86 Ubuntu Feisty and an ATI Radeon 9100.

Any idea?

Thanks!

---

