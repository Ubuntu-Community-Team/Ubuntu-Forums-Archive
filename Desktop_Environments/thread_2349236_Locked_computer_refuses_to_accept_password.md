---
title: "Locked computer refuses to accept password"
date: 2017-01-12
forum: Desktop Environments
---

### Post by orthoducks on 2017-01-12
Last night I left my Ubuntu machine running. When I got up this morning it was still running, but had locked. When I entered the password, Ubuntu said it was invalid.

I checked the Caps Lock key and re-entered the password carefully, several times. It never worked. Finally I pressed the reset button. When Ubuntu came back up it accepted the password with no problems.

I don't recall what release this is (it's not on hand as I write), but it's recent; probably 14.04.5.

Is this a known problem? Is there a workaround that avoids the need to reboot?

---

### Post by rakuba2 on 2017-01-12
Well this probably not a definitive answer but I have seen this behaviour with many different machines and operating systems, particularly a well known commercial operating system, and of course the only recourse is to hit the reset button. I suggest you check your power saving settings, it may have put itself to sleep and not been able to wake up, or it may just be bad luck. Dont worry about it, it is very unlikely to be a direct result of running ubuntu.
For myself I always turn everything off at night unless I have got something compiling for hours, but thats because I dont want to be making the electric company any richer than it already is.

---

### Post by orthoducks on 2017-01-12
I appreciate your effort to answer, but that doesn't really move me forward.

I don't understand what the power saving settings could have to do with it (or what to look for) since the system did not shut down. The display shut down, but that happens all the time, and it never causes a problem (and it reversed itself properly when I tapped a key).

I'm not sure what you mean by "unlikely to be a direct result of running Ubuntu." I was running Ubuntu; the problem happened, and it left me SOL with regard to the long-running program that obliged me to leave the computer on. What caused the problem is unimportant, except in the sense that  knowing the cause might help me avoid a repeat.

In this case the long-running program was shred, and I don't think it had anything useful to tell me once it was done. Next time I probably won't be so lucky!

---

### Post by wildmanne39 on 2017-01-12
I do not know the answer but here is the way to safely reboot the computer when it is frozen and it works almost all the time as long as the keyboard is not frozen too.

That is - hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly, one after the other. On some keyboards/systems, you need to use the AltGr key. 

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by howefield on 2017-01-13
> **orthoducks said:**
> I don't recall what release this is (it's not on hand as I write), but it's recent; probably 14.04.5.

Might be helpful to know..

```
cat /etc/*-release
```

---

### Post by orthoducks on 2017-01-13
howefield: I've checked since then. It's 16.04.

wildmanne39: I must be missing something about your suggestion. The Alt+PrtSc codes are good to know about, but the one you recommended just restarts the system. I can do that by pressing reset. If it's safer, I don't understand how. I still lose all my work, which is the only reason this is a significant problem.

---

### Post by wildmanne39 on 2017-01-13
When you say reset you mean hitting the power button? if so that will eventually crash your hard drive and corrupt files.

---

### Post by orthoducks on 2017-01-16
Last night I suspended the system, and when I tried to start it this morning the keyboard froze again. Apparently this is going to happen about once a week. This time the Ctrl+PrtSc REISUB hack didn't work, either.

This is unworkable. I need to find a way to avoid or correct this behavior, or a version of Linux that doesn't do it.

---

### Post by Taemojitsu on 2017-01-17
>keyboard froze again.

Did it happen before? It sounds like a different problem than password not being accepted.

If you get the 'password not accepted' problem again, can you switch to the tty's using Alt-Ctrl-F1? Can you log in there? Is it possible that Shift key isn't working and you can't see it due to displaying circles only?

---

### Post by orthoducks on 2017-01-18
You're right; this is not the same problem, at least not the same symptom. That is even more alarming, as it suggests that there are two problems to solve.

As for the shift key... it always worked before the problem occurred, and it has always worked since I rebooted. I can't prove it wasn't failing when I couldn't enter the password, but that seems very unlikely.

---

### Post by Taemojitsu on 2017-01-18
I've had the screen not turn on in association with the keyboard not working (except keyboard was still working if I was on a TTY, and not using Xorg, which suggests Xorg stopped working when my graphics card did), but that was due to using a proprietary graphics card driver.

If you have the financial means to obtain a USB keyboard, what happens if you encounter a frozen keyboard and plug in the USB one? Actually I'm assuming this is a laptop... were other input devices working? This is pretty much the limit of the help I can give.

---

### Post by orthoducks on 2017-01-19
Not a laptop. I'm glad you mentioned that, because I was looking blankly at your message and thinking, "USB keyboard? What other kind is there any more?"

As for other input devices... the mouse was working normally. Nothing else was attached.

---

### Post by charleswebb76 on 2017-04-10
I have same problem.  Did you ever get your problem solved.  Since I am new to Ubuntu and Linux I don't want to waste a bunch of time on a system that has problems that can't be fixed.
thanks
Charles Webb

---

