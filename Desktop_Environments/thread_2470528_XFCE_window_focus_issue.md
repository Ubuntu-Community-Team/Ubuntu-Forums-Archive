---
title: "XFCE window focus issue"
date: 2022-01-02
forum: Desktop Environments
---

### Post by davidramage on 2022-01-02
Good evening,
I recently installed Xubuntu 20.04 on an older Thinkpad (T410).  I am having a very strange problem with window focus.
Fairly often I will open an application and be able to click around in it without any problems, but I won't be able to click menu bars, icons in other applications, and so on.  Running xfwm4 --replace allows me to switch to another app.  I have been using Xubuntu on another computer for years without any such problems.  I will be very grateful if someone can point me in a direction that'll let me get this fixed!

---

### Post by KBar on 2022-01-03
Hi and welcome to the forum!

There are two dialogs that control the behavior of window focusing: *Window Manager* and *Window Manager Tweaks*. Try playing around with their settings and see if that helps.

---

### Post by davidramage on 2022-01-03
Thank you for pointing me toward that, but unfortunately I think something weirder is going on and I may need to come up with a better title for this thread.

Currently I have Firefox and the Window Manager dialog open.  If I try to click "Window Manager" up in the taskbar at the top, nothing happens.  The same thing is true of the application menu.  I have mapped xfwm4 --replace to my F12 key, and if I tap that I can again click on things in the task bar.  I am able to switch between applications using Alt+Tab.

is there a way to increase logging verbosity?

---

### Post by KBar on 2022-01-03
Redirect standard error to the sink like so:
```
xfwm4 --replace 2>/dev/null
```

---

### Post by schragge on 2022-01-04
@**KBar**. Increase, not decrease.

@**OP**. Is your issue similar to the one described in the xfwm4 FAQ under [I have only one desktop and can't move my windows anymore! HELP!]("https://docs.xfce.org/xfce/xfwm4/faq#i_have_only_one_desktop_and_can_t_move_my_windows_anymore_help")?
> If you have no window borders anymore and can't focus windows, xfwm4 probably closed itself. This happens sometimes and due to the random nature of this annoying bug it's hard to track. But there are workarounds available.

---

### Post by KBar on 2022-01-04
schragge, thank you for correcting me. My apologies.

In that case, defining the **XFSM_VERBOSE** variable should suffice. Refer to **xfce4-session**(1).

---

