---
title: "Firefox is covering the entire screen when opened"
date: 2009-01-19
forum: General Help
---

### Post by Shadow12313 on 2009-01-19
Hi, recently I force quit firefox because it froze and now when I open it it covers my entire desktop including the panels.  Is there any way to fix this?

Screenshot:
[IMG]http://rapidshare.com/files/186214865/Screenshot.png[/IMG]

---

### Post by estyles on 2009-01-19
try pressing F11 and see if that helps.

---

### Post by Shadow12313 on 2009-01-19
It worked! Thank-you!

---

### Post by scouser73 on 2009-01-19
You can also resize the window, that is what I did when Firefox took the whole screen up.

---

### Post by Shadow12313 on 2009-01-31
Ok, I'll try that next time (if there is one)

---

### Post by -kg- on 2009-02-01
And there is likely to be a next time.

The way you can permanently fix this problem is:

Install Compiz Config (compizconfig-settings in Synaptic).  Once installed (or if already installed) launch the utility by opening a terminal window and typing;

```
ccsm
```

Under "Utilities" click "Workarounds."  At the top you will see "Legacy Fullscreen Support."  Uncheck that box, close the window, and the problem will be solved.

---

### Post by Sunspore on 2009-02-01
Thanks, I have this problem too.

:-)

---

### Post by Shadow12313 on 2009-02-01
> **-kg- said:**
> And there is likely to be a next time.

The way you can permanently fix this problem is:

Install Compiz Config (compizconfig-settings in Synaptic).  Once installed (or if already installed) launch the utility by opening a terminal window and typing;

```
ccsm
```

Under "Utilities" click "Workarounds."  At the top you will see "Legacy Fullscreen Support."  Uncheck that box, close the window, and the problem will be solved.

Ok, I'll try that.

---

### Post by fooman on 2009-02-01
you do not need to install anything to fix this for good.  the solution is really simple....

open firefox.  press f11 twice to get to a normal size screen.

click the unmaximize button.

close firefox.

open firefox.

maximize firefox.

problem gone.

---

### Post by -kg- on 2009-02-01
> **fooman said:**
> you do not need to install anything to fix this for good.  the solution is really simple....

open firefox.  press f11 twice to get to a normal size screen.

click the unmaximize button.

close firefox.

open firefox.

maximize firefox.

problem gone.

That didn't work for me.  I tried that, and the problem resurfaced after a time.

---

### Post by tuxxy on 2009-02-01
Try disabling fullscreen legacy support

```
System > Preferences > CompizConfig Settings Manager > Workarounds > General 
```

---

### Post by Crafty Kisses on 2009-02-01
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox
```

Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any
```

Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```

I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal.

---

