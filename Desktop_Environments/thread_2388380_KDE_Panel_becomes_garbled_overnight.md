---
title: "KDE Panel becomes garbled overnight"
date: 2018-04-02
forum: Desktop Environments
---

### Post by accounts0 on 2018-04-02
Its been a week or so that my panel in KDE winds up being a jumbled up when I wake up in the morning. Can't get a screenshot of it since when I hit the button (or mouse for that matter) it goes back to normal, so I have a photo instead.


Also, once I noticed that my clock stopped refreshing after several minutes, the seconds stop. Went back to normal when I moved my mouse.


I have several tabs set to auto-refresh at different intervals in Chrome, but I haven't seen if they're affected.


Tried rebooting a few days ago & it didn't help. Also 'killall plasmashell && kstart plasmashell' doesn't seem to have a lasting effect.

Screenshot/pic: [https://imgur.com/a/0pCZF](https://imgur.com/a/0pCZF)

---

### Post by SeijiSensei on 2018-04-02
Do you have two panels? What's that at the top of the image?

What version of Kubuntu?

---

### Post by accounts0 on 2018-04-02
> **SeijiSensei said:**
> Do you have two panels? What's that at the top of the image?

What version of Kubuntu?

The top of the 2 images is the garbled panel, below is after I move the mouse or touch the keyboard. Ubuntu version is 16.04.3 with the kubuntu package installed.

Note that it hasn't happened since switching to the 4.13.0-32 kernel after last Thursday's intel-microcode update borked the 4.13.0-36 kernel. I can't tell if the 4.13.0-37 version would have helped, with the intel-microcode issue being unresolved at this point- hope to be able to check that sooner than later.

---

### Post by accounts0 on 2018-04-08
With kernel [FONT=monospace][COLOR=#000000]4.15.0-13-generic & intel-microcode [/COLOR][/FONT][FONT=monospace][COLOR=#000000]3.20151106.1 the behavior remains an issue. Maybe 30-ish minutes away & when I come back the panel's borked & clock's stopped. In this most recent case google-chrome-stable was not running, nor was any windowed desktop app unless you count thunderbird in the tray.[/COLOR]
[/FONT]

---

### Post by accounts0 on 2018-04-08
The image below is the panel when it's okay.
[ATTACH=CONFIG]279204[/ATTACH]

This one is when it's not right.
[ATTACH=CONFIG]279205[/ATTACH]

---

### Post by speartip on 2018-04-08
Could be a theme issue. Are you using the installed Breeze theme or something else?
You could also try deleting the panel altogether if it persists, then add a new panel & put all your widgets back.
I notice you also have an incredible amount of widgets on the panel, one of them could be causing the issue. You could try deleting everything on the panel but the stock install widgets, logout & in again & see if you still have the problem.

---

### Post by accounts0 on 2018-04-25
At some point this past week, and using 4.15.0-15-generic, with both the old & the new bugfixed intel-microcode package, the issue has stopped happening. Since this happened before where it only appeared to be solved for a few days rather than permanently, I'm not going to mark the thread as 'Solved' just yet.

Should time permit, I plan to upgrade to the new LTS this week- in which case I'll update status here again afterward.

---

