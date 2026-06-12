---
title: "Desktop Effects Could Not Be Enabled (when I am not first user)"
date: 2008-03-26
forum: Desktop Effects &amp; Customization
---

### Post by sparkguitar05 on 2008-03-26
I have searched for this answer in the forums and none of the solutions worked.

My computer has three users: me and both my parents.  I have custom desktop effects enabled, cube and all.  My parents don't like desktop effects so they have them disabled.

When I turn on the computer and log in to my name, the desktop effects work fine.

Here's the problem.  When one of my parents logs in before I do, the desktop effects won't work for me when I switch to my name, and then I try to enable them I get that "Desktop effects could not be enabled" message.

I can only use compiz when I am the first person to log on to the computer.

Any solutions?

---

### Post by sparkguitar05 on 2008-03-27
Any solutions?  This is driving me nuts!

---

### Post by TomMK on 2008-03-28
I would guess you have either an ATi or Intel graphics chip. This is a known problem with those drivers. See here: [https://bugs.launchpad.net/xorg-server/+bug/137745](https://bugs.launchpad.net/xorg-server/+bug/137745)

You need an nVidia graphics card to avoid this bug.

---

### Post by sparkguitar05 on 2008-03-28
The bug report link said that you can only run X for one user at a time.  Since my parents don't use desktop effects, can I just disable X for them so it will always work for me since I'm the only one who uses desktop effects.

And by the way, what is X?

---

### Post by Ub1476 on 2008-03-28
X is the base graphical environment for Linux. Do your parents log out, or are you using the "fast-user-change applet"/switch user applet?

---

### Post by Takido on 2008-03-28
I have the same problem i have a 
```

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```
Also this is my 'compiz' out put
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 



```
is this just totally not compatiable?

---

### Post by sparkguitar05 on 2008-03-29
> **Ub1476 said:**
> Do your parents log out, or are you using the "fast-user-change applet"/switch user applet?

Fast user switch.

---

### Post by Ub1476 on 2008-03-29
Have you tried to log completely out (or do Ctrl+Alt+Backspace)?

---

### Post by sparkguitar05 on 2008-03-29
> **Ub1476 said:**
> Have you tried to log completely out (or do Ctrl+Alt+Backspace)?
When I do that, it closes everyones programs.

Is there a way to make it so that when someone turns on the computer, it automatically logs into my name and then goes back to the login screen?  That way I will always be the first user, and desktop effects will always work for me.

---

