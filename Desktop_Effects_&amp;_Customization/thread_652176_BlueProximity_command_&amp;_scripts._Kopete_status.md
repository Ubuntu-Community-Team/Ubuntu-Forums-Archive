---
title: "BlueProximity command &amp; scripts. Kopete status?"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by philsson on 2007-12-28
I've installed BlueProximity, a tool that automatically locks your screen when your Bluetooth device (cellphone for example) gets away from your computer, Highly recommended!. It is working really great but I would like to add some actions, like Kopete and maybe skype status. So that they change at the same time as I leave the room and the screen locks.

I've tried the same command line as in KbluetoothD but without succes. Besides, the lock function ended to work as well when I put them two together.

Original command line:
gnome-screensaver-command -p

I tried to add the following line witch is the default in KbluetoothD:
dcop kopete KopeteIface setAvailable || /bin/true

Result
gnome-screensaver-command -p | dcop kopete KopeteIface setAvailable || /bin/true

[IMG]http://blueproximity.sourceforge.net/manual_html_m16b1226e.png[/IMG]

Well, I guess I've done something wrong. The kopete command itself works just fine in console, but not in BlueProximity. I would like help adding the commands or maybe there is a way to add application commands together with the start of the screensaver? 

/Philip

---

### Post by thymox on 2007-12-29
> **philsson said:**
> Result
gnome-screensaver-command -p | dcop kopete KopeteIface setAvailable || /bin/true

Well, I guess I've done something wrong. The kopete command itself works just fine in console, but not in BlueProximity. I would like help adding the commands or maybe there is a way to add application commands together with the start of the screensaver? 

/PhilipPlease bear in mind that I have never used BlueProximity so I don't know the ins and outs of it, but I'm guessing it's a fairly simply frontend to various tools...

You've put a pipe ( | ) between the two commands you want to run... try replacing it with a semi-colon ( ; ) instead.

---

### Post by philsson on 2007-12-29
> **thymox said:**
> Please bear in mind that I have never used BlueProximity so I don't know the ins and outs of it, but I'm guessing it's a fairly simply frontend to various tools...

You've put a pipe ( | ) between the two commands you want to run... try replacing it with a semi-colon ( ; ) instead.

Thanks for the tipp! I've tried it and now the Screensaver function keeps working even if I add code, witch it didn't do before with |. But the kopete command does not seam to work in BlueProximity. Thanks though for the tipp (y)

---

### Post by thymox on 2007-12-29
My bad...```
This | that
```The output of *this* goes to the input of *that*.
```
This ; that
```*This* runs, and when it quits *that* runs.
```
This & that
```*This* runs, "disconnects" (for want of a better phrase) from the shell and runs *that* as well.

So, it looks like you'll be wanting:```
gnome-screensaver-command -p & dcop kopete KopeteIface setAvailable || /bin/true
```Incidentally, the _|| /bin/true_ bit... if I remember correctly that's used as a "if the previous bit failed/doesn't exist, then run this instead" (and /bin/true always exits cleanly with an exitcode of 0), that way you don't get errors and application closures/freezes just because you typed something in wrong.

---

### Post by philsson on 2007-12-29
> **thymox said:**
> My bad...```
This | that
```The output of *this* goes to the input of *that*.
```
This ; that
```*This* runs, and when it quits *that* runs.
```
This & that
```*This* runs, "disconnects" (for want of a better phrase) from the shell and runs *that* as well.

So, it looks like you'll be wanting:```
gnome-screensaver-command -p & dcop kopete KopeteIface setAvailable || /bin/true
```Incidentally, the _|| /bin/true_ bit... if I remember correctly that's used as a "if the previous bit failed/doesn't exist, then run this instead" (and /bin/true always exits cleanly with an exitcode of 0), that way you don't get errors and application closures/freezes just because you typed something in wrong.

Thanks once again. The "&" between the command lines seems to be right. Now everything is working just fine.
Now I'll seek for some  command for skype also.

 Thanks!

---

### Post by highno on 2008-02-19
Hi there,

thanks for using my software. Hope it pleases you.

I'd like to mention a 'creative uses' thread we started on sourceforge. We are trying to think of other uses for BlueProximity than just locking the screen. It can be found here:

[http://sourceforge.net/forum/forum.php?thread_id=1935384&forum_id=724285](http://sourceforge.net/forum/forum.php?thread_id=1935384&forum_id=724285)

Have fun,
Lars

---

