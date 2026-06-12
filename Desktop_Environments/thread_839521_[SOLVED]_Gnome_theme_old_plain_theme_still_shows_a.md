---
title: "[SOLVED] Gnome theme: old plain theme still shows and exists how to replace with bett"
date: 2008-06-24
forum: Desktop Environments
---

### Post by bigdee973 on 2008-06-24
im sick and tired of the same old plain looking gnome theme popping up here and there. I dont like seeing what i dont want on it... check out these 2 pictures...
[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/Screenshot-1.png[/IMG]
[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/Screenshot.png[/IMG]
the one with the green bar is set as my gtk theme but the normal dark blue bar theme always pops up i hate seeing that plain old dirty looking theme.  Every now and then that blue bar theme shows up but i dont want that nasty looking theme to appear anywhere.  not even in nautilus.  so how do i go about changing this and making that green bar theme stick with ALL parts of gtk and never showing up.  i also want to know why is this happening when i have my gtk theme set to the one with the green bar thank u in advance

---

### Post by adewale on 2008-06-24
The plain theme comes up because you're running a root program and root has its own theme which is the default gnome theme. You can correct this by running appearance as root and selecting your current theme. This solves it.

---

### Post by magnus0 on 2008-06-24
Why the hell do you have Xp theme:confused:

---

### Post by bigdee973 on 2008-06-24
lol its MY version of windows that doesnt catch viruses and its a message to Mircosoft to say F YOU.  i can do everything u do even look like u all for free.  and with FREEDOM! SECURITY! RELIABLITY! AND SPEED.  ITS JUST MY WAY OF BRUSHING UP AND IT MAKES MY FRIENDS WANT TO GET THIS OS WHEN THEY SEE I CAN MAKE THIS OS LOOK JUST LIKE VISTA, XP AND MAC LOL ALL THREE OPERATING SYSTEMS FOR NOTHING

---

### Post by bigdee973 on 2008-06-24
how do i go about doing step by step please be clear

---

### Post by bigdee973 on 2008-06-24
> **adewale said:**
> The plain theme comes up because you're running a root program and root has its own theme which is the default gnome theme. You can correct this by running appearance as root and selecting your current theme. This solves it.
so how do i go about doing this step by step how do i become root and change appearance.  i tried sudo appearance but it didnt work

---

### Post by bigdee973 on 2008-06-25
nevermind i found out how to do it here in this site the 3rd guy called future pilot worked for me.  where is says sudo ln -s something soemthing
[http://ubuntuforums.org/showthread.php?t=595664](http://ubuntuforums.org/showthread.php?t=595664)

or simply just input these two commands in terminal.

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons

---

