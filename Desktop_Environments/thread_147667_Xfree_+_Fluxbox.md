---
title: "Xfree + Fluxbox"
date: 2006-03-20
forum: Desktop Environments
---

### Post by shaan_l on 2006-03-20
Hey!

I installed Kubuntu (dapper) as Server, as I wanted to have a minimal install of linux on my pc.

I wanted to install fluxbox as well, so in aptitude I installed (what I hope and think is) the xfree server (x.org server stuff) as well as all the dependencies, xdm (and all the dependencies) and fluxbox.

Everything installed fine, however when I type fluxbox, I get an error that it cannot connect to the X server. Also, when I type xdm my screen flickers then goes back to the command prompt.

What I want to do is have fluxbox be my default windows manager and have it boot straight to that, if possible!

Any ideas?

---

### Post by stuporglue on 2006-03-20
create a file in your home directory named ".xinitrc". In that file, put the line "exec fluxbox".

Then to start it, run "startx". Startx will launch the X server, read your .xinitrc and run the commands in it. Quitting fluxbox will cause the X server to exit (which is what you usually want to happen).

---

### Post by shaan_l on 2006-03-20
I tried running startx but it says its not found.

---

### Post by stuporglue on 2006-03-20
That probably means you don't have all the components of the X server installed. Does a package "xserver-xorg" exist? Can you install that? 

sudo apt-get install xserver-xorg

If you can, then try startx again.

---

### Post by shaan_l on 2006-03-20
thanks for the help!

That is one of the packages I did install, and still nothing.

---

### Post by stuporglue on 2006-03-20
I don't know which package(s) is(are) missing. You could do "sudo apt-get install ubuntu-desktop", look at what it wants to install, then cancel it. 

You should see some xorg related stuff in there. Installing those packages should fix install startx and whatever else is missing.

---

### Post by shaan_l on 2006-03-20
cool thanks man :)

---

### Post by shaan_l on 2006-03-21
ok i got it working, but i installed xdm and it seems to have taken over!

do i need xdm to make fluxbox work?

---

### Post by stuporglue on 2006-03-21
No you don't.

Interesting that XDM got installed...can you un-install it? 

sudo apt-get remove xdm

---

### Post by shaan_l on 2006-03-21
i owe you a beer :)

how do i get out of xdm? it loads automatically now

---

### Post by stuporglue on 2006-03-21
> how do i get out of xdm? it loads automatically now

Can you un-install it? See previous post. 

You can also stop it by switching to a term (ctrl+alt+F1) and running "sudo /etc/init.d/xdm stop" after logging in. 

You can maybe just "sudo chmod -x /etc/init.d/xdm" it too. That'll make it non-executable.

---

### Post by shaan_l on 2006-03-22
i got it all sorted now!

now how would i have it start automatically after i logon?

---

