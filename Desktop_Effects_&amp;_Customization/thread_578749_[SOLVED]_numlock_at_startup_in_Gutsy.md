---
title: "[SOLVED] numlock at startup in Gutsy"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by celticbhoy on 2007-10-17
Two small problems.

1 - I cant seem to enable the numlock to be set to on at startup. I have tried the tutorials listed in posts suggested by the site. But I have no /etc/X11/gdm directory.

2 - How do you change the backgroung colour for the gnome splash screen?

Using Gutsy.

---

### Post by Linicks on 2007-10-17
In all GNU/Linux I use this for numlock ON

In rc.local:

```
setleds +num
```

That is all you need.

Nick

---

### Post by celticbhoy on 2007-10-17
What or where is rc.local ??

---

### Post by cudaman73 on 2007-10-17
It's in /etc/rc.local ;)

---

### Post by Chazall1 on 2007-10-18
This works after login, how can I get numlock on during Boot, to have it functional at login ???

Thanks

---

### Post by GuiPoM on 2007-10-18
maybe try to install 'numlockx' (from synaptic or apt-get, as you prefer)

---

### Post by celticbhoy on 2007-10-18
have it installed how do you use it

---

### Post by GuiPoM on 2007-10-18
Nothing special to do. When it is installed, you should get num lock activated at least from gdm login time.

---

### Post by celticbhoy on 2007-10-18
But as in original post :-

But I have no /etc/X11/gdm directory.

---

### Post by skeelee on 2007-10-19
In Gutsy, the gdm folder is directly under /etc and not under /etc/X11. Just remove X11 in the path and everything should work as before.

---

### Post by MarshHawk on 2007-10-19
Thanks skeelee.  That's what I needed.

OK, just to wrap up what others have said, this is what worked for me:

Make sure the universe repository is enabled.
Execute the following commands in a terminal:

sudo apt-get install numlockx
sudo gedit /etc/gdm/Init/Default

Edit this file by adding the following lines at the end before the line &#8220;exit 0&#8221;:

if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi

Save the file, reboot, and numlock should be on.

---

### Post by Chazall1 on 2007-10-19
> Edit this file by adding the following lines at the end before the line “exit 0”:

if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi

That worked great, thanks

---

### Post by celticbhoy on 2007-10-20
Yeah done the trick for me to.

---

### Post by shmengie on 2007-11-18
thx, all. just what i needed!

---

### Post by run.don't.walk on 2008-01-05
Why must it be so difficult?

---

### Post by zanomix on 2008-01-16
Thanks!

---

