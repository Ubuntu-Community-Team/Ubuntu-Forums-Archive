---
title: "Menu/ Title  bar missing error 11.04 restart X"
date: 2011-05-30
forum: Desktop Environments
---

### Post by 08x on 2011-05-30
I have been using 11.04 since it was released, I first did an upgrade but had this problem.

I ran a fresh install on another machine this problem eventualy reared its ugly head.

I do not know what triggers this so I am unable to replicate this error.

The only way to get it back is to reboot, logout or restart X all are very annoying to say the least.

I have attached screen shots to clarify.

I am using Ubuntu 11.04 64bit.

Many thanks in advance

Pete

---

### Post by Krytarik on 2011-05-30
If that happens, Compiz' "gtk-window-decorator" or even Compiz itself has crashed. You can just restart either of those. I suggest placing launchers for the below stated commands on your desktop, at least for the latter mentioned case, if you are using Unity, otherwise you could also run those commands through the Alt+F2 dialog.

To restart "gtk-window-decorator":
```
gtk-window-decorator --replace
```To restart Compiz:
```
compiz --replace
```Greetings.

---

### Post by 08x on 2011-05-30
Thank you for your swift reply.

I will try this the next time I come accoss this problem.

What I would like to know is this a bug, and has it been noted for repair?

This has just happened on U11.04 32bit different system...

Many thanks

---

### Post by Krytarik on 2011-05-30
> **08x said:**
> 
What I would like to know is this a bug, and has it been noted for repair?

You can search launchpad.net for related bug reports regarding both packages "compiz" and "compiz-gnome".

I want to add that I had a similar issue in my Lucid 10.04, where Compiz didn't bring up the window decorations every other login or so. But it has since been fixed, or at least it doesn't happen anymore.

Although you didn't specifically say it, it seems that in your case the window decorations disappear within a running session, right?

---

### Post by 08x on 2011-05-31
Ok I will have a look, I have been googling it for a few weeks now.

That's correct the session is currently running.

Sometimes it can be fixed by closing the program that seems to be missing the bar and re-open it, it is not always on all windows, other times it is.

---

### Post by 08x on 2011-05-31
I have just had this error happen, mid session on ALL windows, closing all programs and reopening did not fix but

> gtk-window-decorator --replace

Did without restart and worked VERY quickly...

So thank you for that and i hope someone finds the bug soon

---

### Post by gellingboe on 2011-06-15
This only works if I leave the command window up.  As soon as I close it, the original problem pops back up again.

---

### Post by Krytarik on 2011-06-16
> **gellingboe said:**
> This only works if I leave the command window up.  As soon as I close it, the original problem pops back up again.
Please see my initial post regarding running those commands through the Alt+F2 dialog or launchers.

---

### Post by yanick.rochon on 2011-06-22
> **Krytarik said:**
> If that happens, Compiz' "gtk-window-decorator" or even Compiz itself has crashed. You can just restart either of those. I suggest placing launchers for the below stated commands on your desktop, at least for the latter mentioned case, if you are using Unity, otherwise you could also run those commands through the Alt+F2 dialog.

To restart "gtk-window-decorator":
```
gtk-window-decorator --replace
```To restart Compiz:
```
compiz --replace
```Greetings.

I've had the same issue and replacing gtk-window-decorator solves the problem. I think it happens when I fire up Netbeans 7.0 (might be a Java issue with gtk?)

In any case, I created two launchers in the top panel for a quick fix when the problem happens again.

Thank you for the solution!

---

### Post by macrules on 2011-07-11
> **yanick.rochon said:**
> I've had the same issue and replacing gtk-window-decorator solves the problem. I think it happens when I fire up Netbeans 7.0 (might be a Java issue with gtk?)

In any case, I created two launchers in the top panel for a quick fix when the problem happens again.

Thank you for the solution!

This is not really a solution, more of a work around.
The solution is to disable compiz.
Sorry to say, but it is buggy as hell and made multiple systems i have unstable.

Select Ubuntu Classic logon, remove unity and compiz and after that using gconf you can set the 3d rendering to metacity.
And last but not least: please report the bug on compiz :)

---

### Post by SushiAddiction on 2011-11-21
> **08x said:**
> I have been using 11.04 since it was released, I first did an upgrade but had this problem.

I ran a fresh install on another machine this problem eventualy reared its ugly head.

I do not know what triggers this so I am unable to replicate this error.

The only way to get it back is to reboot, logout or restart X all are very annoying to say the least.

I have attached screen shots to clarify.

I am using Ubuntu 11.04 64bit.

Many thanks in advance

Pete

MASSIVE BUMP when will this be fixed. It's still there in 11.10. Ubuntu will have less users because of this.

Has anyone found a way to fix this.
No, I have not edited any settings. Yes, it happens intermittently mid session when opening programs, resizing windows, etc.
(see the first post for pictures)

---

### Post by noisemaker? on 2011-12-12
hello,

does this problem relate espicialy to gnome? would the use of kde avoid crossing this problem?

---

### Post by noisemaker? on 2011-12-12
> **Krytarik said:**
> If that happens, Compiz' "gtk-window-decorator" or even Compiz itself has crashed. You can just restart either of those. I suggest placing launchers for the below stated commands on your desktop, at least for the latter mentioned case, if you are using Unity, otherwise you could also run those commands through the Alt+F2 dialog.

To restart "gtk-window-decorator":
```
gtk-window-decorator --replace
```To restart Compiz:
```
compiz --replace
```Greetings.


i have ubuntu studio 11.10 and i have tried your things.. but i get  messge that compiz i not installed

so langsam nervt es mich, weil jedes mal irgendwas anders nicht funktioniert, ich komme nicht zum arbeiten sondern bin nur am rum machen

---

