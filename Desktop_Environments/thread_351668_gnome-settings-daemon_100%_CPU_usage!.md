---
title: "gnome-settings-daemon 100% CPU usage!"
date: 2007-02-02
forum: Desktop Environments
---

### Post by jgeewax on 2007-02-02
Hi All,

I am running Edgy with GNOME and I have had XGL working for quite a while. The issue that started lately (which I just pinpointed) is that gnome-settings-daemon or one of it's dependencies consumes 100% CPU constantly.

In the system monitor, nothing looks out of place. Everything idling is low, with the max CPU time of the group being about 6 or 7. When I switch to the resources tab, it says CPU usage 100% and the graph shows it's been like that for quite some time.

If I go back to the Processes tab and End *only* gnome-settings-daemon (there are two of them, so I'm not sure which one I'm killing), CPU usage drops to normal and the machine becomes far more responsive. This, of course, removes the theme for my buttons/controls in all the windows, which I'd rather not do. Sometimes I can kill the daemon and the buttons are preserved -- (but they are not for the login after screen-saver lock window).

I've googled on this issue and found something about reading mime-types, but I tested that manually and found it wasn't the issue. 

Basically I need to figure out what is happening with gnome-settings-daemon and why I'm maxing out at 100% for no reason (and why the system monitor doesn't show which process is using this amount of CPU time...)

If anyone has any suggestions, please let me know, 

JJG

---

### Post by bwhite82 on 2007-02-03
Dunno if this will help you out, but the only time I've seen someone complaining about this problem (100% CPU useage) was when they had a dual-core proc and didn't have 686-SMP installed. I'm just trying to help, I saw that this question had zero answers. If you do, then I'm at a loss, and the least I did was bump the message to the top for you :)

---

### Post by jgeewax on 2007-02-03
Hi there,

I am running a P4 system, so the dual core issue isn't relevant. I think -- as far as I know -- that I am running everything 686 rather than 386, so that shouldn't be an issue either.

I still cannot figure out the problem, but I have managed to kill the gnome-settings-daemon which manages the buttons for the screen-saver login screen, so it has no large effect.

If anyone has any other ideas please let me know!

JJG

---

### Post by mobilehavoc on 2007-02-04
I'm having the exact same problem and have no clue how to resolve this...anything you can come up with would be great!

---

### Post by mobilehavoc on 2007-02-04
> **mobilehavoc said:**
> I'm having the exact same problem and have no clue how to resolve this...anything you can come up with would be great!

Don't ask me how or why - it's 5am and i'm tired - but I managed to fix it.

Go to System -> Keyboard -> Layout and hit Reset to Default. Worked for me. :confused: :guitar: ):P

---

### Post by jgeewax on 2007-02-05
My god, that is weird.

Worked for me though -- excellent work!

JJG

:lolflag:

---

### Post by floke on 2007-02-07
Have just read on these forums that the 100% usage might be due to a root process, rather than the user processes - if you go to terminal and type 'top' then it lists all the processes, usr-owned and root, by their CPU usage - you can then use this to diagnose what the high-using processes are.

---

### Post by jgeewax on 2007-02-07
Does anyone have an idea why resetting the keyboard layout to default drops the CPU usage back to normal?

I'm still baffled.

---

### Post by mooter on 2007-02-07
Man that happened to me too and it must have been like that all night!  I noticed in my toolbar applet my processor had been at full so I checked the processes and there you go, something keeping it at !00% even though nothing showed up, so I did a restart.
My cpu had been at 54 Celsius all night! Rrrrgggg.
So next time I'll try the Keyboard reset.
Thanks for the info.

---

### Post by dummypackage on 2007-04-10
> **jgeewax said:**
> My god, that is weird.

Worked for me though -- excellent work!

JJG

:lolflag:

Hahaha, I'm happy!! It worked for me too!:lol:

PS
This bug comes only if XGL session is running on my desktop. Try to uncheck the option in Keyboard Preferences -> Layout Options -> Miscellaneous compatibility options -> 'Shift with numpad keys works as in MS Windows'

---

### Post by A3N.AciD on 2007-07-02
Guys, I'm absolutely amazed. I had the same problem and the "reset to defaults" worked for me also.
I don't understand, how could someone find out such solution :), but it's great that it works.
Anyway, problem is that I need two layouts (english-us, and slovak-qwerty) for writing the documents in my language and anytime I add the second layout, it raises the CPU level again to 100%. It's really anoying.

P.S.: this happens me when XGL and beryl is running...
Thanks for any further help, it is really appreciated...

---

### Post by only_kami on 2007-09-18
Hello!
I had the same problem and hopefully I found a permanent solution. Anyway the solution is consisted of fact that you have to have only one layout of keyboard in "keyboard preferences"  window(System>Preferences>Keyboard) which will probably be your local layout of keyboard like in my case:))
In short you have to sacrifice English/us layout for your local..

Just in case if somebody didn't understand me I uploaded the image how the "keyboard preferences" are suppose to look.

Good luck! :)

---

### Post by vitobcn on 2007-09-20
I had the exact same problem and the keyboard reset solved it too... Thanks!

btw, using 'top' on a terminal you can't still see the cpu taking process. The cpu is showed to be running at 100% though...
With 'ps -aux' it's not shown either.

In my case, the issue occurs when running two gnome instances, a local and remote one (via NOmachine NX) and having the two keyboard layouts.

hope that helps...

---

