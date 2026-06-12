---
title: "Help Synaptic is missing"
date: 2006-06-04
forum: Desktop Environments
---

### Post by gary_emms on 2006-06-04
Well not quite. I've just done a new install. The update indicator is orange and when I click it asks me for my password (so far so good) and tells me that there are three updates available.

When I mark the update and press the Install button I get a window telling me that its checking my system, then the original display. 

I thought that I'd try and check the sources but when I try to open a terminal nothing happens, the same with Synaptic.

If i try to use the installer, it allows me to select an application, then dissapears when I try to install it.

Has anyone got any idea whats going on?

Please!!!!!!!!
](*,) Gary

---

### Post by skymt on 2006-06-04
Let's try this manually. Open a terminal and enter "sudo apt-get dist-upgrade" (basically what the update manager would do). If it works, great. If it doesn't, post the output and we'll see what we can do.

---

### Post by gary_emms on 2006-06-04
Problem, I can't open a terminal. Is there any way to do this other than through the Apps menu?

---

### Post by croak77 on 2006-06-04
Alt-F2 type in gnome-terminal.

---

### Post by nanotube on 2006-06-04
[QUOTE=gary_emms]Problem, I can't open a terminal. Is there any way to do this other than through the Apps menu?[/QUOTE]
hit alt-f2, that will bring up the "run" dialog, and you can type 'gnome-terminal' into it.
or switch to another console (ctl-alt-f2) and you will have a shell there.

---

### Post by gary_emms on 2006-06-04
Interesting, I had to use the ctr/alt/f2 route as running gnome terminal doesn't do anything.
When I typed in 'sudo apt-get dist-upgrade' it worked. So I'm assuming the the problem is with gnome.
any ideas?

---

