---
title: "The right side of my screen"
date: 2007-10-24
forum: Desktop Environments
---

### Post by acl123 on 2007-10-24
Something has changed so that there is a 1 pixel border/space on the right hand side of my screen. This means I can't throw mouse and close a window or drag the scrollbar (pretty major usability problem).
I'm guessing the culprit is Gutsy or Compiz. Anyone know what it could be? I can't find any thing.

---

### Post by yyz on 2007-10-24
I'm having the exact problem, the only difference that occurs is that on my screen the inessential border appears to be on the lefthand side of the screen lol 

:)

Anybody there

---

### Post by PokerJoker on 2007-10-24
> **acl123 said:**
> Something has changed so that there is a 1 pixel border/space on the right hand side of my screen. This means I can't throw mouse and close a window or drag the scrollbar (pretty major usability problem).
I'm guessing the culprit is Gutsy or Compiz. Anyone know what it could be? I can't find any thing.

Sometimes letting the monitor auto-config itsself helps, if it has on-screen-display and buttons to do so.

---

### Post by yyz on 2007-10-24
PokerJoker what you've adviced doesn't seem to work. Do you have different suggestions? I'd like to know about them.

Thank you.

---

### Post by acl123 on 2007-10-24
I'm pretty sure the culprit is Compiz because if I turn off advanced desktop effects the problem goes away. I've tried turning off each of the plugins but I haven't been able to find it that way.

---

### Post by yyz on 2007-10-25
Hi acl123 here is how you fix it.
Go to terminal and type in: 
```
sudo dpkg-reconfigure xserver-xorg
```

Select your Graphics Card from the list, and continue selecting only the 'default' options for the rest of the settings provided. Around to the end of the setup, you will get a short list of screen resolutions. Choose the one you please to use.

Now hit CTRL+ALT+BACKSPACE on your keyboard to logout of your computer.
Re-login.
On your monitor press the Auto-Adjust button, and you'll be done !

:)

---

### Post by acl123 on 2007-10-25
Hi thanks, that doesn't work though. I don't think the problem is with the resolution. I think the problem is with a setting in Compiz/Compiz Fusion because when I turn off advanced desktop effects I can use the right side of my screen again.

---

