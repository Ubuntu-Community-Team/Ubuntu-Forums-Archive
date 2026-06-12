---
title: "Windows closing on key strike (hardy 8.04) strange problem"
date: 2008-07-29
forum: Desktop Environments
---

### Post by _UsUrPeR_ on 2008-07-29
This is a weird one. I can't tell if I should just submit this as a bug, or ask if I'm doing something wrong, so I'll check with the desktop environment people first.

The operating conditions of my system are as follows:

VMware server running (does not matter what I am running in vmware)
allow server to idle to the point where the screen saver turns on.

strike key or move mouse to disable screen saver.

After that, if I open firefox, calculator, chess, or any new windows in ubuntu, then strike ANY key on the keyboard, the window that is running will be closed. The only windows that will remain open are terminal and vmware server.

Inside VMware server, the mouse and keyboard act normally. Inside terminal, a few key combinations will no longer work. such as shift + pgup, shift + crtl + C and shift + insert.

While hitting shift + insert, the following is printed:

```
^[[2~
```

Not even ctrl + alt + backspace works to reset X server.

To rectify this problem, I have to manually log out then log back in.

I am really confused as to why this happens, and even more confused as to how I can even diagnose this problem any further.

---

### Post by ModelM on 2008-07-30
How is the keyboard connected? USB? PS/2?

---

### Post by _UsUrPeR_ on 2008-07-30
Oh, sorry. It's a PS/2 keyboard.

---

### Post by muecker on 2008-08-01
I have been having this same issue.  I think it is a problem with VMWare.  It doesn't do it every time, but sometimes after I have been running VMWare server, it causes this issue.  New programs will normally start but terminate almost immediately (sometimes as soon as I hit a key).  Certain keys (Ctrl, Shift, Alt) do not work, which is normally the first indication it is happening.  Everything continues to work normal within VMWare, but outside of VMWare I see the problems.

The only way to recover is to reboot, which is easier said than done since I cannot start a terminal or type my password into an existing one (cannot type upper case characters).  Ctrl-Alt-F1 works if VMWare has focus, you can switch to a virtual terminal and reboot from there.

---

### Post by _UsUrPeR_ on 2008-08-01
Thank god. I thought I was the only one. Weird how your problem is a little different.

---

