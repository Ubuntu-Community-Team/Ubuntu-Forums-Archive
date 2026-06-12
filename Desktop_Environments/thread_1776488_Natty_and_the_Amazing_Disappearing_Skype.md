---
title: "Natty and the Amazing Disappearing Skype"
date: 2011-06-06
forum: Desktop Environments
---

### Post by frankvw on 2011-06-06
I've been on Natty for two days now. I ditched Unity immediately in favor of the classic UI, because I need something that works (please address flames to [email]nospamp@nono.no[/email]) and so far I'm very happy.

There's just one thing that irritates me no end: Skype will no longer dock to the top panel bar. On my previous Ubuntu distro (a very stale 8.04) I could start Skype minimized (it would show as a status icon in the top bar, and I could minimize it to the top bar (again it would display a status icon). Not so in 11.04, though. When I minimize Skype it just disappears, and trying to restart it ends in an error message informing me that it's already running. My only recourse is to kill the Skype process and start a new one.

I've Googled extensively, and I can't find a real solution (and grazing these forums hasn't led to enlightenment either). I've tried Docky, but I just don't like docks (although Docky *is* nicely done) and it's not an alternative to having a status icon in the topbar all the time.

Suggestions, anyone? All responses would be greatly appreciated!

// FvW

---

### Post by exiztone on 2011-06-07
I've found this frustrating too. None of the solutions I've read work so I've ended up executing ```
gnome-panel --replace
``` and the problem is temporarily resolved. It makes the desktop experience less elegant though. :(

---

### Post by frankvw on 2011-06-07
> **exiztone said:**
> I've found this frustrating too. None of the solutions I've read work so I've ended up executing ```
gnome-panel --replace
``` and the problem is temporarily resolved. It makes the desktop experience less elegant though. :(

How less elegant? Could you post a screenshot?

// FvW

---

### Post by exiztone on 2011-06-08
> **frankvw said:**
> How less elegant? Could you post a screenshot?

// FvW

Less elegant implying we have to do unconventional "tricks" to work around a glitch in GNOME. This bug shouldn't be there and I dislike bringing up the *Run Application* window every time I open Skype (and VLC too for that matter). Replacing the gnome panel has funny side effects like resetting the inhibit applet.

It's not a critical bug, but it impedes the smoothness of the expected workflow.

---

### Post by frankvw on 2011-06-14
> **exiztone said:**
> Less elegant implying we have to do unconventional "tricks" to work around a glitch in GNOME. This bug shouldn't be there ...
It's not a critical bug, but it impedes the smoothness of the expected workflow.

I agree. That said, though, there are far more pressing issues, too. Occasionally the screen saver freezes when I hit a key (instead of exiting and revealing the desktop) and I simply cannot get my desktop back. NetworkManager occasionally looses track of available networks, and my USB mouse dies at unpredictable intervals (even the red LED goes out) and I have to unplug and replug it.

In my previous Ubuntu install there were problems, too. NetworkManager would sometimes loose track of the WiFi connection's WPA password and not be able to reconnect when I re-entered it, and Firefox started acting up, too, starting with the search function no longer working.

The funny thing (and the reason why I mention all this) is that before I switched to Ubuntu's GUI, I only experienced problems like these in Windows. Which leads me to believe that perhaps these issues are more common to a GUI (any GUI) than to a specific version of Gnome or Ubuntu distro.

Thoughts on this, anyone? And what could be done about it?

// FvW

---

### Post by cipherboy_loc on 2011-06-14
Out of curiosity, what graphics driver and adapter are you using? On my desktop with a nVidia graphics card, I was using the latest drivers which didn't support my outdated graphics card, which led to random freezes to the system (it was hiding kernel panics).

---

### Post by frankvw on 2011-06-14
> **cipherboy_loc said:**
> Out of curiosity, what graphics driver and adapter are you using? On my desktop with a nVidia graphics card, I was using the latest drivers which didn't support my outdated graphics card, which led to random freezes to the system (it was hiding kernel panics).

I'm running it on my HP-550 laptop using whatever driver Ubuntu itself decided to install. :-) How can I check which graphics driver is currently being used?

// FvW

---

### Post by cipherboy_loc on 2011-06-14
To check the graphics card:
```

lspci | grep VGA

```

To check for nVidia graphics driver (might be a better way, as it only checks to see if it is installed):
```

dpkg --list | grep nvidia

```

Then for the ATI FGLRX driver: 
```

dpkg --list | grep fglrx

```

---

### Post by frankvw on 2011-06-15
> **cipherboy_loc said:**
> To check the graphics card:
```

lspci | grep VGA

```


Thanks! Done that. Result:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)

```

Fairly simple hardware. As I said, it's a cheap laptop. :-)

BTW the USB mouse issues I mentioned above seem to have to do with power management, but I haven't figured out what to do about it.

// FvW

---

### Post by frankvw on 2011-06-29
> **frankvw said:**
> Thanks! Done that. Result:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)

```

Fairly simple hardware. As I said, it's a cheap laptop. :-)

BTW the USB mouse issues I mentioned above seem to have to do with power management, but I haven't figured out what to do about it.

OK. Here's the score so far:

1. "Fixed" the problem with stuck screen savers by disabling the screen saver. Now it just shows a blank screen before switching off the backlighting (according to the power management settings) and All Is Well.

2. The Skype docking problems disappeared after the last round of updates. Skype now docks and undocks properly as before.

3. The mouse problem was fixed by this one: [http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html)

Marking this thread as solved.

// FvW

---

