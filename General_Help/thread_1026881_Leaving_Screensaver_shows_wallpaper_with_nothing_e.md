---
title: "Leaving Screensaver shows wallpaper with nothing else. It's NOT locked (mouse moves)!"
date: 2008-12-31
forum: General Help
---

### Post by thimad on 2008-12-31
It seems the problem is with fullscreen apps.

Sometimes (at least once a day) when I move the mouse to leave screensaver, i see my wallpaper and my mouse cursor moving, but nothing else appears!

It also happens when I'm trying to leave "fullscreen mode" in VLC Media Player (either by pressing F11 to return to a normal window, or by just pressing ALT-TAB during a fullscreen video to change to another window).

It's NOT locked (the mouse moves).
It's not a Kernel Panic (caps lock does NOT blink/flash)

I tried the following things, but nothing worked:

- acpi=off, acpi=noirq, pci=noacpi
- changing screensaver
- changing my wireless to 802.11b (ipw 4965 bug: see intrepid release notes)
- ctrl-alt-backspace doesn't work
- ctrl-alt-F1 doesn't work
- Alt-SysRq-B doesn't work
- AltGr-SysRq-B doesn't work

The only solution is to hard power off (cut power), but I'm afraid that will damage my hard drive.

My Video Card (lspci | grep VGA):
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I'm using Compiz in Gnome.

PLEASE, help! I formated windows (not using it anymore) and I'm loving Ubuntu, but i want to make it stop freezing!

Thanks,
Thiago.

---

### Post by fooman on 2008-12-31
do you have your video drivers installed?

have you tried changing screensaver to "blank screen" (not a fix,  but better then a hard power down) ?

---

### Post by donkyhotay on 2008-12-31
Regardless of whether the mouse moves or not any time my system prevents from even swapping screens (ctrl-alt-f#) I consider it locked up. Anyways... since this appears to only happen after coming out of screensaver I would look at your power management and screensaver system. Check the gnome power management, is your computer set to 'sleep' after a specific length of time? Does your BIOS have similar sleep settings? What screensaver system are you using? Your probably using the gnome-screensaver (which is the default) but if you're using xscreensaver that would be good to know as well. I would also try a screen saver (such as black screen) that doesn't use any hardware acceleration.

---

### Post by eBoxNet on 2008-12-31
did you try alt+ctrl+backspace ?

---

### Post by donkyhotay on 2008-12-31
> **eBoxNet said:**
> did you try alt+ctrl+backspace ?

4th item in his list of things tried...

---

### Post by thimad on 2008-12-31
Well, previous versions of Ubuntu used to blacklist my intel video card. But I think Intrepid installed the correct drivers by default. It's the first time Ubuntu installs it by itself. Now I can use all compiz effects. Even the xVideo works with compiz enabled.

I will try the blank screensaver. I can't tell if it worked now because the problem doesn't happen every time. But ASAP i will post results.

Thanks for all suggestions!
And I still accept more!
:D

Thiago.

---

### Post by thimad on 2008-12-31
My BIOS is so simple! It has NO sleeping functions...

My computer does NOT sleep after some time. Even if I close the lid, it does NOT sleep.

How do I check if I'm using gnome-screensaver or xscreensaver? I don't think I have changed this. It must be the default.

Thanks again!
Thiago.

---

### Post by Drubie on 2008-12-31
> **eBoxNet said:**
> did you try alt+ctrl+backspace ?

Hehe, I just fell for the old "alt F4 to throw the knife" bit...
My own fault...

---

### Post by Drubie on 2008-12-31
I just experienced the same issues when I was exploring the screensavers.   I am running 8.04 on my mini - had to do a hard restart...

I never had this problem just using blank screensaver, so that could be a pseudosolution...

---

### Post by abn91c on 2008-12-31
check you monitor refresh rate, you may need to drop to 60Hz

---

### Post by thimad on 2008-12-31
The monitor resolution is @ 60 Hz, 1280x800...
I think it's correct, right?

By the way, my video card, according to "lspci", is:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I hope that's useful.

Thanks again!

---

### Post by abn91c on 2008-12-31
it's probably compiz's fault, turn off desktop effects, if it continues then remove compiz entirely

---

### Post by thimad on 2009-01-01
Since i like compiz, I'm trying the "blank screen" screensaver first.

But indeed, i read about some "obscure" bugs of compiz, and if it continues for too long, i will disable/remove it.

Thanks for the tip.

---

### Post by thimad on 2009-01-01
Until now, since I changed my screensaver to 'blank screen', I had no problems, for nearly a full day. I'm very happy using compiz effects.

Thanks for the tips, guys!

I will test it for more a couple of days.

---

### Post by thimad on 2009-01-03
:popcorn:

Changing my Screensaver to Blank Screen "solved" the problem. For more than 2 days I didn't have any "empty and unresponsive desktop after leaving screensaver".

I didn't have to hard power off anymore, and I'm very happy with that.

Thank you very much for all your help and suggestions!

---

### Post by thimad on 2009-01-08
Oh, and putting Compiz on it's default settings was also necessary.

I still haven't found out which plugins cause problems, but i think they may be either:

- thumbnailing windows on the taskbar

or

- minimize effect (magic lamp)

I CONSIDER THIS SOLVED.

Thanks everyone.

---

### Post by fordp on 2009-01-09
I have this problem.

If you have to switch things off that should work then it is not solved, you have just worked round it.

I came on the forum to try and find a bug number for this issue.

Does anybody know if it has been logged ?

Cheers.

---

### Post by fordp on 2009-01-10
I noticed a bit more.

The problem is when coming out of the screensaver.

The machine draws the correct wallpaper but there is then nothing else drawn on the screen. The mouse pointer moves but nothing else seems to work and I have to restart the machine.

---

### Post by thimad on 2009-01-11
> **fordp said:**
> If you have to switch things off that should work then it is not solved, you have just worked round it.

I agree with you. It's just a work around, but i really don't know what else to do.

Although I didn't disable Compiz (i just use the default plugins). Better than nothing.

Unfortunatelly i don't know of any related BUG submited to launchpad.

Cheers.

---

### Post by thimad on 2009-01-11
> **fordp said:**
> I noticed a bit more.

Well, i think you described exactly my problem. Not a bit less, not more.

:)

Welcome to the club... lol!

Thiago.

---

### Post by keithb on 2009-01-11
I have been having trouble with this for a while now on intrepid.

I tried changing Visual Effects to None on Appearance Preferences. I thought that was helping but then I also had the screensaver freeze up completely and wasn't able to get out. Now I am also using Blank screen for Screensaver Preferences.

I guess I can try enabling visual effects and leave Blank screen for screensaver and see if that works. I prefer to use Random instead of Blank screen.

I am using the onboard graphics on my motherboard. I am wondering if buying a new graphics card would help.

Any helpful suggestions? Anyone else with this problem?

Thanks,

Keith

---

### Post by thimad on 2009-01-12
I launched a BUG report:

[https://bugs.launchpad.net/ubuntu/+bug/316414](https://bugs.launchpad.net/ubuntu/+bug/316414)

---

### Post by eldersoares on 2009-02-08
Hi folks!
I have had the same problem and i'll tell you more: it doesn't happen only with the screensaver. actually, for me, it has never happended with screensaver, but with anything that goes fullscreen (firefox, f-spot, etc)

it doesn't happen always, i still don't know exactly when or why. i know that it is only the video and the keyboard that freezes because i keep listening to music and all program seems to keep working. but the keyboard doesn't do nothing, neither a num lock!

well, i hope this will be solved
bye

---

### Post by UncleLev on 2009-06-06
I'm pretty sure I found the solution, in case there are still folks who have this issue! :) :) :)

I myself first encountered it today after a fresh installation of Ubuntu 9.04.

Whenever my screen would switch over full screen mode, or switch back from it, the wallpaper would show for a split second. Not a big deal, but kinda annoying, especially when it comes out of nowhere.

So anyhow, yes, it is caused by Compiz. I tried various tests... basically with all the plugins and options that were already set to default. I tracked it down to coming from a single setting.

Open the "CompizConfig Settings Manager" program and click "General Options". On the first tab, "General", you will see a check box for an option reading "Unredirect Fullscreen Windows". This was checked for me by default, but after unchecking it, the problem immediately went away.

For any of you folks who still run into this, try what I mention above, because it was a quick and simple fix, and probably the source of the problem in the first place.

---

