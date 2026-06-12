---
title: "Unity dashboard &quot;Waiting to install&quot; doesn't go away"
date: 2016-05-01
forum: Desktop Environments
---

### Post by cash1981 on 2016-05-01
I just installed a fresh Ubuntu 16.04 LTS

I tried to install chromium from the software center. And the waiting to install doesnt go away.
I had to eventually install it using the terminal.

I have tried to restart the computer, and when I right click I cant remove the icons.
What do I do?

[ATTACH=CONFIG]268743[/ATTACH]

---

### Post by grahammechanical on 2016-05-01
On 16.04 with the new Ubuntu Software application we have to click the reload button at the top left. The application window should reload and the Install button should change to a Remove button. Ubuntu Software is actually a re-branded Gnome Software. So, we are kind of stuck with the design philosophy of the Gnome developers.

As for the problem of being unable to move launcher icons to different places on the launcher, I doubt it is connected to the way that Ubuntu Software works or dosen't work. Depending on your point of view.

This command will reset the launcher icons back to default. 

```
unity --reset-icons
```

This command will reset Unity

```
unity
```

This command will restart Unity

```
setsid unity
```

Regards.

---

