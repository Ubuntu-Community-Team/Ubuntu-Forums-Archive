---
title: "Strange intermittent blue static"
date: 2012-06-03
forum: Desktop Environments
---

### Post by residualbit on 2012-06-03
This is an issue I have not seen before and is quite strange. I took some screenshots, but realized that the static is not actually captured on them.

What I am seeing is wavy/shaky blue static on areas of the screen where dark colors are displayed (like on the panel and dash for instance). If I open up google (which is mostly white) in firefox and maximize the window, there is no static to be seen. Like the subject says, this is very intermittent and I have not found a way to re-create it or solve it reliably. I can say that it usually occurs when I first turn the computer back on, or after it comes back from being idle. It usually either goes away on its own or after a restart. The monitor is connected via dvi and I have an nvidia gt520 card.

At first I was worried about the monitor, but I have yet to see this happen on other computers.

Any ideas? I'll try to take a picture of it next time it happens.

---

### Post by Paddy Landau on 2012-06-03
If it does not appear on your screen-shots, and it goes away after resuming, this is almost certainly a hardware fault. By your description, it would not be a fault with the monitor but with your graphics card.

---

### Post by residualbit on 2012-06-03
I switched from the dvi port to the vga port on the same card, and so far haven't seen the issue. I'll just leave it like that until I can get around to buying a new card I guess.

---

### Post by Paddy Landau on 2012-06-04
> **0xnak said:**
> I switched from the dvi port to the vga port on the same card, and so far haven't seen the issue. I'll just leave it like that until I can get around to buying a new card I guess.
I don't suppose there is a way to prove that it's the card? I wouldn't want you to spend money on a new card if it were something else.

---

### Post by residualbit on 2012-06-12
I started running a separate windows machine through this same monitor via DVI with the same cable and noticed some issues there as well. Not the same exact thing, but similar. I guess that narrows it down to the cable or the monitor. To troubleshoot, I went with the cheaper and easier option by buying a new DVI cable. It has been 3 days, and I have not seen the blue static on the Ubuntu box. I'm hoping that the issue was just the cable, but I suppose I could just be getting lucky...

My question now is, do DVI cables go bad like that? I had assumed it was either an all or nothing thing as they were digital and that they couldn't 'sort of' go bad.

---

### Post by patrickceg on 2012-06-12
> **0xnak said:**
> My question now is, do DVI cables go bad like that? I had assumed it was either an all or nothing thing as they were digital and that they couldn't 'sort of' go bad.

It's possible that something happened to get noise (and therefore a corrupted image) for some cases but not all cases, making your cable intermittently fail. Note I haven't seen it for HDMI or DVI yet, but I have seen half-broken USB cables transferring files at slow rates. In the case of DVI of course it can't slow the transmission down so you get "artifacts" instead.

---

### Post by Paddy Landau on 2012-06-13
> **0xnak said:**
> My question now is, do DVI cables go bad like that? I had assumed it was either an all or nothing thing as they were digital and that they couldn't 'sort of' go bad.
Nothing in this universe is perfect or absolute. Maybe a DVI cable *shouldn't* go "sort of" bad, but *shouldn't* is not the same as *can't*.

---

