---
title: "XFCE no window decoration?"
date: 2012-06-13
forum: Desktop Environments
---

### Post by WritersTear on 2012-06-13
I need some help here. I don't know what the heck happened but my xfce desktop environment is all messed up. There are no window decorations or title bar for the file manager window or the applications window when I run an application such as FireFox or AbiWork.

I can't even right click on them. I don't know what happened, everything was working fine a week ago, I was playing around with the window decoration manager, changing window appearance to suit my taste and when I rebooted up on Tuesday, the window appearance around the application dissapeared. I can't move the apps around, they are stuck on the left hand side of the screen and I can't do a snapshot of the desktop because I can't alt tab to the application to show you what you mean.

Is there a way I can fix the XFCE desktop? Or do I need to remove it completly and if so how?

---

### Post by black veils on 2012-06-13
have you tried going back in to those settings and changing the window decoration theme back to default?

maybe you added a theme to your system which didnt have all the files?

or did you get a bit delete-happy in your themes folder?

if you installed compiz, this will be why the window decorations are gone etc.

---

### Post by Toz on 2012-06-13
> **WritersTear said:**
> I need some help here. I don't know what the heck happened but my xfce desktop environment is all messed up. There are no window decorations or title bar for the file manager window or the applications window when I run an application such as FireFox or AbiWork.

I can't even right click on them. I don't know what happened, everything was working fine a week ago, I was playing around with the window decoration manager, changing window appearance to suit my taste and when I rebooted up on Tuesday, the window appearance around the application dissapeared. I can't move the apps around, they are stuck on the left hand side of the screen and I can't do a snapshot of the desktop because I can't alt tab to the application to show you what you mean.

Is there a way I can fix the XFCE desktop? Or do I need to remove it completly and if so how?

Sounds like the window manager might have crashed. Start it up again by Alt+F2 and:
```
xfwm4 --replace
```

And it sounds like xfdesktop might not be running as well:
```
xfdesktop
```

---

### Post by wildmanne39 on 2012-06-13
Hi, here is a link to help, please be sure to follow the correct part of the guide for your version.

With xfce you probably need to enable move windows if you changed settings in compiz and there is a section for windows decorations in the guide.
[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)
Thanks

---

### Post by WritersTear on 2012-06-14
> **wildmanne39 said:**
> Hi, here is a link to help, please be sure to follow the correct part of the guide for your version.

With xfce you probably need to enable move windows if you changed settings in compiz and there is a section for windows decorations in the guide.
[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)
Thanks

I don't need 3D. And I don't have Compiz installed.
The command xfwm4 --replace worked, do I need to do this every time I log in?

---

### Post by Toz on 2012-06-14
It should work automatically if you save your session when you log out. If not, you might want to clear out your sessions cache to reset it and solve the problem. To reset your sessions cache, simply delete the **.cache/sessions** folder in your home directory.

---

### Post by WritersTear on 2012-06-14
> **Toz said:**
> It should work automatically if you save your session when you log out. If not, you might want to clear out your sessions cache to reset it and solve the problem. To reset your sessions cache, simply delete the **.cache/sessions** folder in your home directory.

I don't see .cache/sessions folder in my home directory. Could it be located somewhere else?

---

### Post by Toz on 2012-06-14
.cache is a hidden folder. Make sure you have "Show hidden files" enabled in Thunar (in the View menu or Ctrl+H) or from a command prompt (terminal window) you can delete the contents of that folder with the following command:
```
rm -rf ~/.cache/sessions
```
(be careful using the 'rm -rf' command)

---

