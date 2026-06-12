---
title: "Monitor turns a reddish pink"
date: 2012-03-27
forum: Desktop Environments
---

### Post by gizmobay on 2012-03-27
I've been having this issue with the monitor turning a reddish pink color on me which causes me to have to log out then back in. I'm using 11.10 kubuntu using the nouveau drivers with a nvidia Gforce 7300 LE. I've attached a sample of what it looks like which just happens to be from Thunderbird. I'm using the standard theme from KDE. Anyone else see this?

---

### Post by Grenage on 2012-03-28
Considering that you said relogging works, this is unlikely but possible:  Is the VGA cable decent; does moving it help?

I've only seen a couple of cases where tinting was software-based, but I've seen a hundred where a bad cable was to blame.

---

### Post by Zorael on 2012-03-28
Is what you attached an unmodified screenshot?

---

### Post by gizmobay on 2012-03-28
I don't think it's the cable as I had a cable go bad before and you could move it and watch the color changes. This one just changes on it's own.

I didn't modify the image but I just took a small section of the whole screen. It happens about once a week so I just kept ksnapshot open so I could get sample to post since I haven't seen any other threads dealing with this issue.

---

### Post by Grenage on 2012-03-29
> **gizmobay said:**
> I don't think it's the cable as I had a cable go bad before and you could move it and watch the color changes. This one just changes on it's own.

It did seem rather unlikely, but it's always worth a quick check.  I am going to assume that it's either temperamental hardware (monitor/graphics card) or a driver quirk.  If the 7300 is supported by the proprietary driver, does the issue still occur when using it?

---

### Post by Zorael on 2012-03-29
No, if it were a damaged cable it would not affect a screenshot, only if you had taken a photo of your monitor.

When it starts, does it happen in every and all applications? (Perhaps it's limited to GTK?)

Also try running the following in the terminal when it's tinted;
```
$ xgamma -gamma 1
```

---

### Post by gizmobay on 2012-03-29
I believe it has something to do with starting Thunderbird as it always seems to happen when I start TB but not every time. Sometimes TB causes the whole computer to freeze as well. I will run the command xgamma -gamma 1 next time it happens.

---

### Post by gizmobay on 2012-03-29
> **Grenage said:**
> It did seem rather unlikely, but it's always worth a quick check.  I am going to assume that it's either temperamental hardware (monitor/graphics card) or a driver quirk.  If the 7300 is supported by the proprietary driver, does the issue still occur when using it?
When I upgraded to 11.04, the prop driver wouldn't work as their was a bug with respect to the Nvidia 7300 since the computer wouldn't boot into KDE. Probably not still there but it was a pain moving back and forth between Nvidia prop driver and the nouveau driver for testing so I just stuck with the nouveau since it worked.

---

### Post by gizmobay on 2012-03-29
It's definitely caused by starting TB as I kept opening TB until it happened. I ran the xgamma command and it says Red 1.000, Green 1.000, Blue 1.000

---

