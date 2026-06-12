---
title: "Ibex showing blank screen after login"
date: 2008-12-16
forum: General Help
---

### Post by leet hacker on 2008-12-16
I installed 8.10 yesterday on my Dell computer and it was working fine for a while after I started it. I was notified that there were updates available so I began downloading them. They finished downloading and the installation began. After a couple minutes, the computer completely froze up; I couldn't even use the mouse and I had to do a hard shut-down. I started it up again but after I entered my username and password, the screen went black and all I could see was the mouse. I heard the start-up music play and let it sit for 10-15 minutes but the screen still was black. I pressed the power button on the computer (didn't hold it, just pressed it) and I saw a short flash of the light tan background of the login screen and then I saw the Ubuntu shutdown loading screen (the one where the orange bar gets smaller towards the right; not sure what exactly it's called). I started again and the same thing happened: I logged in, saw a blank screen and restarted. I let the computer sit over night and when I tried it a little while ago it did the same thing. Can anyone tell me what the problem might be and, if so, what to do? I'm not feeling too l33t right now and I'm not sure if this is the correct forum for posting this thread.

---

### Post by leet hacker on 2008-12-16
Does anyone see this? What is a reasonable amount of time to wait for replies (I'm new to this forum)?

---

### Post by leet hacker on 2008-12-16
Never mind, I saw another topic about this same thing.

---

### Post by drs305 on 2008-12-16
The easiest thing to try is to boot to recovery mode. If you don't normally see the grub menu during boot, hit ESC repeatedly just a bit after you hear your system beep during boot. This should let you see the grub menu options. One of the options will be to "Try to fix X server". Select that and let it run to see if it can resolve video issues.

---

