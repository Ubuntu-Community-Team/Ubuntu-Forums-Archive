---
title: "[lubuntu] 18.04: computer refuses to accept password after getting back from sleep"
date: 2019-09-18
forum: Desktop Environments
---

### Post by eldino on 2019-09-18
I have the same issue explained in this closed (but unsolved) thread ([https://ubuntuforums.org/showthread.php?t=2349236&page=2]("https://ubuntuforums.org/showthread.php?t=2349236&page=2"))

I have the following configuration:

- Intel NUC NUC6CAYH (Celeron J3455 1.5 GHz, HD Graphics 500, 8 Gb RAM, 128 GB SSD)
- Logitech Wireless Touch K400 keyboard
- A projector connected via HDMI
- Lubuntu 18.04 (installed via Ubuntu Server + $ sudo apt-get install lubuntu-desktop)
- The OS is up-to-date with the latest updates

Since a couple of weeks it started giving me this issue after getting back from sleep.
It worked flawlessly for two years.
Very static and minimal configuration, I didn't install any new app lately.

Issue:

1. I start the computer and login into it just fine;
2. I use it for a couple of hours;
3. I click on Suspend;
4. The next day I click on the power button;
5. The screen lock popups asking for password;
6. I type in the passwords multiple times, no luck.

I need every time to force reboot the machine via reset button.

Any idea?
Should I open a bug on launchpad?

Thanks!

---

### Post by guiverc on 2019-09-18
Firstly I'd check the keyboard is working/responding  (eg. does CTRL+ALT+F4 switch to terminal 4? when it's suspended).  When you hit RESET are you doing this because none of the keys are working, ie. you cannot use SysRq+REISUB to safely reboot rather than hardware reset?

I just booted a Lubuntu 18.04 LTS box; once booted I suspended it.  On waking, it asked me for password - but I could switch to terminal (CTRL+ALT+F4), and back to GUI without issue -- it's this I'm asking you to check. I'm betting I could use SysRq keys to reboot without logging back in, but didn't test that.

---

### Post by eldino on 2019-09-18
@guiverc
Thanks for your answer :)

I think the keyboard is working fine yes: as I said I'm able to type-in the password just fine after the wake up.
But once I do it, it returns "Authentication Failed".

I'll try to switch to the console and see what happens
I'm pushing the RESET button for commodity, but I'll try the reisub option as well.

---

