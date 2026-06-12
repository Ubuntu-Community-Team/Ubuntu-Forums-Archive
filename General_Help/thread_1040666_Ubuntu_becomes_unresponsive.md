---
title: "Ubuntu becomes unresponsive"
date: 2009-01-15
forum: General Help
---

### Post by svivian on 2009-01-15
Just now I was browsing the net and Ubuntu became totally unresponsive. I could hear the CPU working constantly and I was unable to do anything. Moving my mouse sometimes moved it a few pixels, but I couldn't click anything, nothing happened when I pressed keys on the keyboard either.

I tried opening the terminal using my shortcut, <Super>+R, and left the computer for about 10 minutes, but nothing happened. Ctrl+Alt+Backspace did nothing, nor did Ctrl+Alt+F7 (usually switches to pure command line mode). The only solution was to power off the tower.

This also happened a few weeks ago. This time, the apps I has open were Opera and IE6 (ies4linux). I don't remember what I had open the previous time. I wasn't doing anything specific when the CPU started thrashing, just reading a web page (digg).

Can anyone suggest what may have caused the problem?

---

### Post by Yashiro on 2009-01-15
Possibly the Flash plugin on your browsers.

---

### Post by cyclobs on 2009-01-15
it could either be:

1. if you've updated to the new nvidia drivers 180.22 they seem to have froze up my computer a lot!

or

2. like the guy said your flash could be causing problems. But i'm running 64 bit flash here so the beta plugins could be a problem.

thats all i can think of unless it's a application it's self causing the problem.

---

### Post by svivian on 2009-01-16
Thanks for the replies so far. My card is ATI, not nvidia, so I'm using the ATI drivers (obviously). I don't think there was any Flash loaded (I block it on digg).

It didn't feel like a particular program was causing it, because the whole system was unresponsive, not just one program.

I will try and recreate later if possible!
[EDIT: ah, I think the page I had open in IE had flash in it... I'll see if that was the problem]

---

### Post by Yashiro on 2009-01-16
The slowdown usually comes from running the flash plugin via the nsplugin wrapper technique.

When you get these immense slowdowns, open System Monitor and sort the processes by CPU usage. Is npviewer.bin maxing out your CPU?

---

### Post by Electric Bill on 2009-02-17
Has a workaround been developed for this problem?

I'm running an AMD tri core and I use the Gnome sensors-applet 2.2.1 in the top panel to monitor my CPU temp and cooling fan.
The fan alarm is set to flash red when my fan goes above 1,000 RMPs.

[IMG]http://newportyachtdirectory.com/Linux_Box/CPU_temp-fan.jpg[/IMG] [IMG]http://newportyachtdirectory.com/Linux_Box/FanAlarm.jpg[/IMG]

Since the fan is PWM controlled to respond to CPU temps it gives me an early warning that my CPU usage is high.
If I open the System Monitor I see at least one of the cores going crazy.

What I have been doing is to use the Firefox add-on NoScript  but of course that disables many features when I'm browsing a site that uses Java.
I can right click on the page and select *temporarily allow all this page* in the NoScript menu but it's a pia to have to do this all the time.
And if I forget to *Revoke Temporary Permissions* it continues indefinitely.

Anyone have a better solution?

When I google this it seems like this problem has been around for quite a long time.
I've even gone so far as to disable Adobe's ability to monitor tracking cookies to see if that was the cause.
This may not seem like a big issue but when you consider the stress on the system components and the huge increase in power usage, in this economy, it is a big issue.

Bill

---

### Post by svivian on 2009-02-18
No, I haven't found any "solutions", though I haven't had this problem since I last posted.

> **Yashiro said:**
> When you get these immense slowdowns, open System Monitor and sort the processes by CPU usage. Is npviewer.bin maxing out your CPU?
This is what I always try to do, but the whole system was frozen, so I couldn't do anything apart from occasionally get the mouse to move.

---

