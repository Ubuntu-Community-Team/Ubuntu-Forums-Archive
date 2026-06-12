---
title: "unmounting with wine running"
date: 2006-11-28
forum: Gaming &amp; Leisure
---

### Post by lakersforce on 2006-11-28
Hi there.
I am trying to install some windows games with Wine. I seem to a problem though.
I have most of my games on image files (and I dont want to have to burn them on a cd). If I for example run "wine "D:\setup.exe"" setup fail immidiatly. The only way I can the setup is to go to the mounting point and run the setup file from there. Ok, so far so good. But the problem occours when I am prompted to change my cd. To do that I will have to unmount my imagefile. Here's the problem: I am not allowed to unmount! The reason for this is that my terminal window is open at my mount point. And if I close my terminal I kill my wine process and therfore terminate my install process! How do I solve this problem?

---

### Post by lakersforce on 2006-11-29
anyone?

---

### Post by seethru on 2006-11-29
> **lakersforce said:**
> Hi there.
I am trying to install some windows games with Wine. I seem to a problem though.
I have most of my games on image files (and I dont want to have to burn them on a cd). If I for example run "wine "D:\setup.exe"" setup fail immidiatly. The only way I can the setup is to go to the mounting point and run the setup file from there. Ok, so far so good. But the problem occours when I am prompted to change my cd. To do that I will have to unmount my imagefile. Here's the problem: I am not allowed to unmount! The reason for this is that my terminal window is open at my mount point. And if I close my terminal I kill my wine process and therfore terminate my install process! How do I solve this problem?
Why are you typing D:\setup?

It should be..
```
wine /the/mount/point/you/specified/setup.exe
```

---

### Post by lakersforce on 2006-11-29
You can use both. No matter which method I use, the install program can't run unless I go to the mountpoint and run setup from there. Which again results in that I can't unmount my imagefile because my terminal is open at my mountpoint.

---

### Post by hikaricore on 2006-11-29
either open another terminal or end your command with the "&" symbol

this will allow you to keep using the same terminal.

example:

> wine /the/mount/point/you/specified/setup.exe **&**

or from inside your directory

> wine setup.exe **&**

---

