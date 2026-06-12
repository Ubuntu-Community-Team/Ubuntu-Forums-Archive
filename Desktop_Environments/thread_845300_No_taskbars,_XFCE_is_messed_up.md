---
title: "No taskbars, XFCE is messed up"
date: 2008-06-30
forum: Desktop Environments
---

### Post by CC440 on 2008-06-30
I tried to log out of Xubuntu to save my desktop setting and it took about 3 minutes to do so. Upon logging back in the taskbars were gone. All the desktop icons remain and work, but I can no longer see the menus at the top of the screen and they no longer load no matter what type of session I try and start. I am a very new user so any basic level help would be appreciated.

---

### Post by vambo on 2008-06-30
Try:

<alt> <F2> to bring up the "Run Command" dialogue

Enter

```
xfce4-panel
```

and run it.

This should give you your panels back. To ensure they are there in the future make sure you have:

"Save session for future logins" checked in the "Quit" dialogue.

---

### Post by sisco311 on 2008-06-30
press Alt+F2 and type:
```
xfc4-panel
```click on the *Run... *button.
This should restore your panels.
Close all aplication and log out with the *Save session* option.

If the command doesn't restore your panels, open a terminal(Applications->Accessories->Terminal) and post the output from:
```
xfce4-panel
```

EDIT: D'oh, I'm slow.

---

### Post by NET WT on 2008-07-03
I had this problem also, but that fixed it for me. Thanks alot!

---

### Post by mobilediesel on 2008-07-06
> **vambo said:**
> Try:

<alt> <F2> to bring up the "Run Command" dialogue

Enter

```
xfce4-panel
```

and run it.

This should give you your panels back. To ensure they are there in the future make sure you have:

"Save session for future logins" checked in the "Quit" dialogue.

I have to do the <alt><F2> xfce-panel every single time I boot. I tried checking "Save session for future logins" and tried UNchecking it. same result each time. I have to do the <alt><F2> xfce-panel so get the panels to come up.

What else can I look at for the fix?

---

### Post by sisco311 on 2008-07-06
try to rename the  ~/.cache/sessions/ folder.
```
mv ~/.cache/sessions ~/.cache/sessions-backup
```
and restart the x server(Ctrl+Alt+Backspace)

to restore the original settings:
```
mv ~/.cache/sessions-backup ~/.cache/sessions
```

---

### Post by mobilediesel on 2008-07-07
Well, after doing <alt><f2> and xfce-panel, I went into settings and deleted the panels and recreated them. Also unchecked the "allow xfce to manage desktop" and rechecked it. Now everything does what it's supposed to do.

...except for the time it didn't.

At least when things DO go wrong in Linux, you actually get suggestions on what to try next! And most suggestions WORK! When I had trouble in Windows I usually got responses like "HA! N00B!" and B.S. like that. The only reason I know Windows so freakin well now is that it KEPT BREAKING!

---

