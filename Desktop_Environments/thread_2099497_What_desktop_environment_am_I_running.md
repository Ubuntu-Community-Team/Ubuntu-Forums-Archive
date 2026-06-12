---
title: "What desktop environment am I running?"
date: 2012-12-29
forum: Desktop Environments
---

### Post by Rulius on 2012-12-29
Hi,

is there a command that reports the information of the desktop environment one is running?

I run ubuntu 12.04 and system monitor reports gnome3.4.2 (?).
I did install cairo-dock, but apart from the dock the rest of the desktop environment is unity.

Thanks

---

### Post by haqking on 2012-12-29
> **Rulius said:**
> Hi,

is there a command that reports the information of the desktop environment one is running?

I run ubuntu 12.04 and system monitor reports gnome3.4.2 (?).
I did install cairo-dock, but apart from the dock the rest of the desktop environment is unity.

Thanks


```
echo $DESKTOP_SESSION

```

And Unity sits on top of and relies on Gnome

---

### Post by Rulius on 2012-12-29
That command gave me: ubuntu -2d
Is that unity in 2d mode?

Is there a command providing more thorough information?

---

### Post by haqking on 2012-12-29
> **Rulius said:**
> That command gave me: ubuntu -2d
Is that unity in 2d mode?

Is there a command providing more thorough information?

yes Unity-2d.

More thorough how ?

You know you have Gnome 3.4.2 with Unity-2d.

Thats what you wanted to know ?

---

### Post by Rulius on 2012-12-29
Things like: which windows manager is it using ? - for example.

Thanks for your help!

---

### Post by haqking on 2012-12-29
> **Rulius said:**
> Things like: which windows manager is it using ? - for example.

Thanks for your help!

metacity by default for Unity 2d if i remember correctly.

you can install ```
wmctrl
```

then type

```
wmctrl -m
```

or ```
man wmctrl
``` for more info

---

### Post by grahammechanical on 2012-12-30
System Monitor is telling you the version of the Gnome Desktop Environment that is installed. This is not the same as the User Interface. At the login screen if we click on the Ubuntu icon just above where we enter our password we will get a list of User Interfaces installed. That is if we have installed an additional User Interface.

You should see Ubuntu and Ubuntu 2D. Unless the hardware is not able to run Ubuntu-Unity-3D. Then you will only see Ubuntu 2D. I am using 12.10 and Unity 2D is not available in 12.10. Another method is used to give low specification machine users the same experience as Ubuntu 3D. So, we (12.10 users) only see Ubuntu.

The last used UI always becomes the default UI to load.

Regards.

---

