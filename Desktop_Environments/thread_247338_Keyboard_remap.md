---
title: "Keyboard remap?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by mfhJoe on 2006-08-30
Hi,

I am using Ubuntu on a laptop which the enter key is broken on. I was hoping to remap the keyboard so the right shift key acts as the enter key.

I found [this tutorial](http://sluglug.ucsc.edu/pipermail/sluglug/2001-March/016706.html) (I know it's not for Ubuntu) and it works apart from the part about making the change stay permanent. I put the following line in my xinitrc file (/etc/X11/xinit):

```
xmodmap -e "keycode 62 = Return"
```

But it doesn't seem to do anything. Do I have to use something other than xinitrc in Ubuntu? Any help would be appreciated.

Joe

---

### Post by mfhJoe on 2006-08-31
Sorry, never mind. I figured it out. For anyone who wants to know, I created a .xmodmap file with 'keycode 62 = Return' in it, put it in my home folder and restarted.

Joe

---

