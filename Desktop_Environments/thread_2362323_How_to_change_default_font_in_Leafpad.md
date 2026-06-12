---
title: "How to change default font in Leafpad"
date: 2017-05-26
forum: Desktop Environments
---

### Post by Xubuntist on 2017-05-26
I've recently had three PCs in the workshop, all old XP or Vista machines, to install Lubuntu and inject some new life into them. I've got a text file on my flash drive with a bunch if copy/paste commands because my command line memory is failing (it was never very good at its best). One thing that has always bugged me is that Leafpad opens with a variable-width font that doesn't suit my preferences and with three machines passing across my desk in recent times, I got sick of constantly going into **Options > Font **with it reverting to its default "Ubuntu 11" font every time I close it. I struggled to find out how to change it and when I did find out, I was happy as Larry and just wanted to share this simple tip because Google didn't:

Open Leafpad and decide which font to set as default - I like "DejaVu Sans Mono 11pt"
In a Terminal ```
sudo leafpad ~/.config/leafpad/leafpadrc
```

Change:```
0.8.18.1
734
686
Ubuntu 11
0
0
0
```to```
0.8.18.1
734
686
DejaVu Sans Mono 11
0
0
0

```
Save and exit.

PS. This is about Leafpad, not Vi or Gedit. Thanks.

---

### Post by egeezer on 2017-05-28
Do you know of the Xubuntu Core ISOs?  They give you a desktop-only, practically no apps, and let you configure a system to your own preferences.  That means it can be as light as (maybe even lighter than) Lubuntu, but with the configurability of xfce4.  

With your username, I would guess you already know this, but I thought I'd mention the option just in case you hadn't come across them.

---

### Post by Xubuntist on 2017-05-29
Thanks for that info. I will definitely give it a shot.
 
The Lubuntu box I'm working on is somehow broken and rather than fix what I don't have enough energy or, clearly, knowledge to fix, I'll give the Xubuntu Core ISO a whilrl!

Many thanks

---

### Post by Xubuntist on 2017-05-29
Well, I installed the x64 Core ISO and it's a smooth install and incredibly light. Thanks for the tip, it'll come in handy for other projects.

---

