---
title: "wont login"
date: 2009-04-04
forum: General Help
---

### Post by hp owner on 2009-04-04
ok, so i just upgraded my laptop to kubuntu and it boots up good, but when it comes to the login window i enter the user name and password; hit enter and it acts like it is going to log int, but the screen goes black, flashes a hole bunch of words, then goes back to the login window. anyone know how i can login and get the desktop??


thanks in advanced

---

### Post by bertolo on 2009-04-04
you should try booting using safe mode an tell us the feedback and ubuntu with gnome instead of kubuntu. i rather prefer it, but that's just me =P

---

### Post by hp owner on 2009-04-05
isn't safe mode for windows?? if not how do you do it, im still new to linux

---

### Post by F6F Freak on 2009-04-05
All I have ever seen is "Recovery mode." It is a long shot from safe mode.

---

### Post by yamarc on 2009-04-05
Get into Recovery Mode, try logging in.

If it works, type "startx" into the terminal and see if you get your desktop after a few seconds.

If not, post the output here.

---

### Post by hp owner on 2009-04-07
sorry for the long wait to reply, in the recovery menu their are 4 options

resume        resume normal boot
dpkg          repair broken packeges
root          drop to root shell prompt
xfix          try to fix x server

which one do i choose??

---

### Post by hp owner on 2009-04-07
ok, i do that and i get this. i hope you can read it









btw this is on my compaq presario laptop

---

### Post by hp owner on 2009-04-07
still wont login

---

### Post by hp owner on 2009-04-07
please people i really need to get this back up and running before the weekend, ive done everything you guys have told me, so what next??

---

### Post by wandalalakers on 2009-04-07
Just curious, what version of Kubuntu are you using?
What is the model number of the HP/Compaq you are using?
What video card does your HP/Compaq have?
Are you able to boot into Kubuntu using the live cd?
If using the live cd try booting into the vga mode option.

---

### Post by hp owner on 2009-04-07
kubuntu 8.04
presario 2100
ati radeon igp 320m
and idk about the livecd, i haven't tried that yet, ill get back to you tomorrow

---

### Post by utnubuuser on 2009-04-07
Not sure about Kubuntu, but if I were having this kind of problem in Gnome...

I'd get to the root recovery console, then > sudo apt-get remove xserver-xorg-core --purgethen> sudo apt-get insall xserver-xorg-corethen restart

Chances are this is a driver issue since you're using a ATI card. Reinstalling the xserver won't hurt.

---

### Post by hp owner on 2009-04-10
ok, i did that, now it wont even load, im just going to give up on ubuntu versions on this pos laptop, its nothing but problems, im going to try a different version of linux. thanks anyways

---

### Post by hp owner on 2009-04-11
just a lil follow up, i formatted my hd and installed fedora 10 on the laptop, and it works perfect with the ati graphics card

---

