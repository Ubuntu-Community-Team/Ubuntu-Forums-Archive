---
title: "Lost Mouse Wheel!"
date: 2006-06-28
forum: Desktop Environments
---

### Post by howipepper on 2006-06-28
I installed Dapper Drake last night and all was working wonderfully.  I have a Microsoft IntilliMouse with the wheel, and it was detected and worked just fine.  This afternoon we had a thunderstorm roll through that killed our power.  I wasn't able to shut down the computer safely before the UPS died.  When power finally came back on, I rebooted the computer and all seemed fine, until I tried to use the mouse wheel to scroll through some documents.  It no longer worked.  Everything else works just fine, just no scroll wheel.  I tried unplugging the mouse (usb) and plugging back in, no good.  I tried shutting down normally and turning the system back on, no good.  Here's the kicker, I have an MS wireless usb mouse as well.  I plugged that in and it uses the wheel.

More info: I have a Belkin four port KVM switch.  I share the keyboard, monitor and mouse with three other computers.  The scroll wheel on the "bad" mouse works fine on all of these other computers, just not the one running Ubuntu.

I could probably just reinstall Ubuntu and get the mouse wheel to work again, but that's not the right way to do it.  Anyone have any ideas?

---

### Post by howipepper on 2006-06-29
Never mind folks.  I did a total shutdown of my entire network that was connected to the KVM switch, then "rebooted" the KVM switch and brought the computers back up one at a time.  That seems to have fixed the problem.

---

### Post by reidi on 2006-11-05
Edgy/Dapper
Belkin 2-Port KVM

Problem: Switching between computers using the KVM switch causes the mouse scroll wheel to stop functioning.  (With my KVM switching is activated by issuing: ScrollLock, ScrollLock, [port #])

Solution: Per the Belkin Manual:  unplug the mouse connector from the KVM for 2-3 seconds, and replace.  This should restore full mouse functionality.  This worked fine for me.  At that point the KB stopped responding.  This could well have been because I bumped the KB connector.  At any rate the same trick worked for restoring KB input.

---

### Post by jp-newtolinux on 2007-01-05
> **reidi said:**
> Edgy/Dapper
Belkin 2-Port KVM

Problem: Switching between computers using the KVM switch causes the mouse scroll wheel to stop functioning.  (With my KVM switching is activated by issuing: ScrollLock, ScrollLock, [port #])

Solution: Per the Belkin Manual:  unplug the mouse connector from the KVM for 2-3 seconds, and replace.  This should restore full mouse functionality.  This worked fine for me.  At that point the KB stopped responding.  This could well have been because I bumped the KB connector.  At any rate the same trick worked for restoring KB input.
reidi,

Thanks.  This is the first "fix" that has worked.  I've tried all the remapping of buttons etc etc.

Now the question is this:  Is there a code-equivalent to the 3-second unplug so I could just put it on the panel?

jp

---

### Post by StephaneLenclud on 2007-02-25
I have the same problem with 6.10. I'm loosing every mouse button but 1, 2 and 3 after a KVM switch.

I managed to [fix that problem on openSuse 10.0]("https://slion.net/twiki/bin/view/Dev/LinuxConfig#Mouse_wheel_issues") before.  Actually on my KVM I have that openSuse 10.0 machine and my Ubuntu 6.10.  The mouse keeps working fine for Suse but won't for Ubuntu.

I'm using the same x11 conf than with my Suse machine and tried to make it work by playing with the kernel command line. I tried the following options:
psmouse_proto=imps
psmouse_proto=imps2
psmous_proto=exps

That just won't work so far. There must be a way to fix that though!!!

---

### Post by StephaneLenclud on 2007-02-25
I found some interesting reading:
[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1041517](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1041517)
[http://ubuntuforums.org/archive/index.php/t-28643.html](http://ubuntuforums.org/archive/index.php/t-28643.html)

Unloading/reloading psmouse module by running the following command makes the wheel work again on my Ubuntu 6.10, no need to reboot, no need to restart X:
```

modprobe -r psmouse
modprobe -a psmouse

```

---

### Post by StephaneLenclud on 2007-02-25
Seems to me like all the confusion with proto=imps and KVM mouse not working properly  has nothing to do with the drivers or kernel not working. It's just a misunderstanding of how module options are enabled in Ubuntu (6.10 in my case).

You can't specify module options in /etc/modules but rather just the name of the modules that need to be loaded. Using kernel command line would not work for me either.

One way to specify module option is to use /etc/modprobe.d/options.

So in our case all you need to do is:
    *  Edit and add the following to /etc/modules : 

#Load psmouse module
psmouse

    * Edit and add the following to /etc/modprobe.d/options 

#Make my mouse work with KVM
options psmouse proto=imps

See [https://slion.net/twiki/bin/view/Dev/LinuxUbuntu#How_to_make_your_mouse_work_with](https://slion.net/twiki/bin/view/Dev/LinuxUbuntu#How_to_make_your_mouse_work_with)

---

### Post by firefly2442 on 2007-11-05
> **StephaneLenclud said:**
> Seems to me like all the confusion with proto=imps and KVM mouse not working properly  has nothing to do with the drivers or kernel not working. It's just a misunderstanding of how module options are enabled in Ubuntu (6.10 in my case).

You can't specify module options in /etc/modules but rather just the name of the modules that need to be loaded. Using kernel command line would not work for me either.

One way to specify module option is to use /etc/modprobe.d/options.

So in our case all you need to do is:
    *  Edit and add the following to /etc/modules : 

#Load psmouse module
psmouse

    * Edit and add the following to /etc/modprobe.d/options 

#Make my mouse work with KVM
options psmouse proto=imps

See [https://slion.net/twiki/bin/view/Dev/LinuxUbuntu#How_to_make_your_mouse_work_with](https://slion.net/twiki/bin/view/Dev/LinuxUbuntu#How_to_make_your_mouse_work_with)

This worked for me, thanks.  For mine, if you try switching and then move the mouse right away it behaves erratically.  If you switch and then wait a couple seconds and move the mouse it should be OK.  At least that's what happened when I tested it. :)

---

