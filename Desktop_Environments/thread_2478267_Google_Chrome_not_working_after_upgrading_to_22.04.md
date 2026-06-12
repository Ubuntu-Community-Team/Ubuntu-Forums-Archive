---
title: "Google Chrome not working after upgrading to 22.04"
date: 2022-08-21
forum: Desktop Environments
---

### Post by fehercs on 2022-08-21
I just upgraded from 20.04 to 22.04 and after launching google chrome it's not loading any pages, not even settings. The loading spinner in the tab title just spinning around and after a while it just gets a "Page Unresponsive" alert. Launching it from terminal it spits out the following error:
```
libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)
```

Firefox works perfectly, but all my bookmarks, history, etc. is in chrome so I'd rather not switch.
I tried running with all the disable options (plugins, extensions, HW acceleration), which didn't solve the issue.
The only thing that works is to run chrome with the --v=1 flag, that launches chrome and everything seems to work fine.

Any suggestions on resolving the issue? What does the --v=1 flag do? What I found is that is connected somehow with logging with the --enable-logging flag, but nothing on what it's function by itself.

---

### Post by Frogs Hair on 2022-08-21
You could try removing the profile folder in home/hidden folders/ .config/google-chrome. You will loose your bookmarks, extensions,and settings but they can be restored if you are using sign onto chrome to sync your browser. If using the same bookmarks in Firefox you can import them.

---

### Post by fehercs on 2022-08-21
Thanks, I tried moving the ~/.config/google-chrome and ~/.cache/google-chrome folders but unfortunately the issue still persists.

---

### Post by Frogs Hair on 2022-08-22
Have attempted removal and reinstalling after deleting the folder I suggested ?

---

### Post by Holger_Gehrke on 2022-08-22
'libva' is probably for video acceleration, at least a quick 'apt search libva' makes me think so. So I'd check what display server (Wayland or X11) you're running and try the other one.

Holger

---

### Post by ActionParsnip on 2022-08-23
[https://bbs.archlinux.org/viewtopic.php?id=258759](https://bbs.archlinux.org/viewtopic.php?id=258759)

Seems to be an Nvidia thing

---

### Post by fehercs on 2022-08-23
> **Frogs Hair said:**
> Have attempted removal and reinstalling after deleting the folder I suggested ?
Yes, a couple of times. Did reinstall, restart and reinstall, spin around twice in my chair and reinstall.

---

### Post by fehercs on 2022-08-23
> **Holger_Gehrke said:**
> 'libva' is probably for video acceleration, at least a quick 'apt search libva' makes me think so. So I'd check what display server (Wayland or X11) you're running and try the other one.

Holger
That might have something to do with the issue, since I just remembered that 22.04 uses wayland as default, while 20.04 used x11, although the fact that the &#8212;v=1 flag solves the issue doesn&#8217;t makes sense in that case.

---

### Post by fehercs on 2022-08-23
> **ActionParsnip said:**
> [https://bbs.archlinux.org/viewtopic.php?id=258759](https://bbs.archlinux.org/viewtopic.php?id=258759)

Seems to be an Nvidia thing
I didn’t mention it previously, but it’s a laptop with integrated intel gpu. I’ll take a look, hopefully has something useful.

---

### Post by thomasuc2 on 2022-08-25
> **fehercs said:**
> I didn’t mention it previously, but it’s a laptop with integrated intel gpu. I’ll take a look, hopefully has something useful.

I have the same issue with:
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

Disabling wayland didn't help

Actually, Chrome worked for about 1 hour after I installed Ubuntu 22.04.
Chrome stopped working after I did a sudo apt install -f (suggested by Software Updater because it couldn't update).
Not sure if this caused it.

So I am also interested in suggestions.

---

### Post by thomasuc2 on 2022-08-26
Probably not a reproducible solution but I got Chrome to work again (at least for now).

While Chrome was running I did a 'ps -ef|grep chrome' and got a long list of processes.
I started killing them one by one, starting with the lowest PID ('kill PID' where PID is the number listed by the ps-command ) . 
When I had killed 4 processes this way, I got a message that a plugin had crashed (didn't see which one).

I closed Chrome and opened it again.
It now runs as expected.

It seems to me that a particular plugin is somehow blocking chrome from loading pages.
If it happens again, I will try to figure exactly which plugin it is.

I hope this helps.

---

### Post by fehercs on 2022-09-03
> **thomasuc2 said:**
> Probably not a reproducible solution but I got Chrome to work again (at least for now).

While Chrome was running I did a 'ps -ef|grep chrome' and got a long list of processes.
I started killing them one by one, starting with the lowest PID ('kill PID' where PID is the number listed by the ps-command ) . 
When I had killed 4 processes this way, I got a message that a plugin had crashed (didn't see which one).

I closed Chrome and opened it again.
It now runs as expected.

It seems to me that a particular plugin is somehow blocking chrome from loading pages.
If it happens again, I will try to figure exactly which plugin it is.

I hope this helps.

Thanks for your input. I tried killing the processes however I'm running a clean install of chrome, so there are no plugins. Starting with the lowest PID always closes chrome for me, I guess that would be the main process for the browser. Starting with the highest didn't do anything for the first couple of processes and restarting started all the processes again.

---

### Post by fehercs on 2022-09-03
> **Holger_Gehrke said:**
> 'libva' is probably for video acceleration, at least a quick 'apt search libva' makes me think so. So I'd check what display server (Wayland or X11) you're running and try the other one.

Holger

I just tried changing back to xorg, the issue still persists unfortunately.

---

### Post by fehercs on 2022-09-03
I am thinking of doing a fresh install of Ubuntu, maybe the Upgrade messed something up. Although that's sounds like a massive inconvenience, I'll report back when I got myself to do it.

---

### Post by thomasuc2 on 2022-09-05
> **fehercs said:**
> I am thinking of doing a fresh install of Ubuntu, maybe the Upgrade messed something up. Although that's sounds like a massive inconvenience, I'll report back when I got myself to do it.

I just experienced the same thing on a different computer (laptop this time).
And the solution with killing processes on the first computer only worked temporarily.

HOWEVER, starting chrome with "google-chrome-stable --no-sandbox" works for me on both computers!

...and if you want this to work with the dock icon, you should modify /usr/share/applications/google-chrome.desktop by adding "--no-sandbox" to the lines starting with "Exec=".

Best regards,
-thomas

---

### Post by fehercs on 2022-09-10
> **thomasuc2 said:**
> I just experienced the same thing on a different computer (laptop this time).
And the solution with killing processes on the first computer only worked temporarily.

HOWEVER, starting chrome with "google-chrome-stable --no-sandbox" works for me on both computers!

...and if you want this to work with the dock icon, you should modify /usr/share/applications/google-chrome.desktop by adding "--no-sandbox" to the lines starting with "Exec=".

Best regards,
-thomas

Starting chrome with "google-chrome-stable --no-sandbox" also works for me, however reading around it looks like disabling sandbox is a security risk and not recommended.
Running with the "google-chrome-stable --v=1" also solves my issue and it keeps the sandbox running, although I have no idea what it does and if it opens up some attack vectors or not.

---

### Post by fehercs on 2022-09-10
> **fehercs said:**
> Starting chrome with "google-chrome-stable --no-sandbox" also works for me, however reading around it looks like disabling sandbox is a security risk and not recommended.
Running with the "google-chrome-stable --v=1" also solves my issue and it keeps the sandbox running, although I have no idea what it does and if it opens up some attack vectors or not.
Just found this website: [https://peter.sh/experiments/chromium-command-line-switches/](https://peter.sh/experiments/chromium-command-line-switches/)
It states that the --v flag defines the logging level for chrome. I don't think that could be a serious security risk, but you never know.

---

### Post by e-plumber on 2022-10-01
The --v=1 solution above also works for me on Ubuntu 22.04, Intel EVO.

Switching from Wayland to X11 did not help me. I also tried updating the Mesa drivers to no avail.

---

