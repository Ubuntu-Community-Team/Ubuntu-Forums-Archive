---
title: "Multiple Issues with Hardy Upgrade"
date: 2008-04-27
forum: Desktop Environments
---

### Post by Scarfy on 2008-04-27
Hi,

I've just upgraded to Hardy and I'm experiencing a few issues. For example,

[LIST=1]
[*]Shutdown / Restart / Log off from KDE does not work. System hangs until the power off button is pressed (once, not held)
[*]ATI drivers appear to be a lot slower
[*]KDE has rendering issues
[*]KDE is slower
[*]Konqueror sometimes refuses to launch. Process list shows multiple instances running
[*]Firefox crawls (although it's a beta, so that's probably a given)
[*]CPU goes to 100% for a time and locks system
[/LIST]

Is any one else experiencing such issues? I'm just attempting to determine whether my upgrade has gone horribly wrong?

---

### Post by chandra on 2008-04-29
My upgrade from Gutsy to Hardy went off smoothly and better than I anticipated. I have not experienced any of the issues you have raised except for Firefox.

See

[https://bugs.launchpad.net/bugs/215728](https://bugs.launchpad.net/bugs/215728)

for a workaround after you have solved your other more serious problems.

By the way, I assume that you upgraded to KDE 3.5.9 rather than KDE 4.0.x because the latter is still a little rough.

---

### Post by jalefkowit on 2008-04-29
I'm having the same problems with shutdown after upgrading from Kubuntu Gutsy to Hardy.  Haven't been able to find a solution as of yet.  Grrr.

---

### Post by syko.trevize on 2008-05-06
Same problem here, moreover i cannot find a way to log on without launching kde, ](*,)

---

### Post by geekATlarge on 2008-05-25
I've just fixed a similar problem on my system. Look at: [Failed to initialized HAL, can't mount USB, log-out icon locks-ups]("http://http://ubuntuforums.org/showthread.php?t=806813")

---

### Post by Xiong Chiamiov on 2008-05-26
Though this is an old thread, the shutdown issue has been discussed [here]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/138691").

The rendering issues you're having might be KDE4-related, if you are using that.  It's hard to say since you don't tell us.

---

