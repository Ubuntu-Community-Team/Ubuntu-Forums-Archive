---
title: "**********!!!No desktop!!!*********"
date: 2009-03-01
forum: General Help
---

### Post by steigerjb on 2009-03-01
I had been trying to get xwinwrap to work with no avail. I want to get rid of it so I can have my desktop back. (When xwinwrap is installed there are no more desktop icons) How do I remove xwinwrap??? HELP

I have tried the

killall xwinwrap
kill xwinwrap

nothing....

I have been told it may not be xwinwrap that hid my desktop. No desktop icons or right click on desktop :(

HELP HELP!! ](*,)

---

### Post by damis648 on 2009-03-01
Try
```
killall -9 xwinwrap
```
and if that doesn't work press Alt+F2 and type in
```
gconf-editor
```
and Navigate to Desktop>Background and make sure draw_background is checked.

---

### Post by binbash on 2009-03-01
pkill xwinwrap

---

### Post by miegiel on 2009-03-01
For fun I tried 
```
gconf-editor
```
to make my icons disappear and get a nice clean desk top.

I found it under Desktop>_Gnome_>Background, that's in hardy though. However *draw_background* made my desktop image (dis)appear. So I assume it won't help steigerjb with his icons.

---

### Post by steigerjb on 2009-03-01
didn't work :(

---

### Post by miegiel on 2009-03-01
I don't know anything better than to try```
sudo apt-get install ubuntu-desktop
```But you might want to wait for some better advice before you try that.

---

### Post by steigerjb on 2009-03-02
found a solution:

alt+f2
"gconf-editor"
apps->nautilus->preferences.
click "show desktop"
alt+f2
"nautilus"

---

### Post by thedavis on 2009-03-06
> **steigerjb said:**
> found a solution:

alt+f2
"gconf-editor"
apps->nautilus->preferences.
click "show desktop"
alt+f2
"nautilus"

This works for me, but when I restart.... no desktop again :(:(:(

---

