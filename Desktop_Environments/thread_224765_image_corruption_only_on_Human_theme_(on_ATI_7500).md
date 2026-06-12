---
title: "image corruption only on Human theme (on ATI 7500). help"
date: 2006-07-28
forum: Desktop Environments
---

### Post by syxbit on 2006-07-28
[IMG]http://lehi.ath.cx/dropbox/ubuntu/distorted.jpg[/IMG]
running 2.6.15-26-686
on an IBM thinkpad with an ATI radeon 7500

fglrxinfo displays the following
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

hovering over the corrupted buttons refreshes it, and it then works for a while
any ideas?

---

### Post by roostishaw on 2006-07-28
From what I know, Nautilus makes a sort of cache of thumbnails that its used. They are stored in the .thumbnails folder in your home folder. If Nautilus can't find a thumbnail that it has cached, it will just regenerate it. Mabey it was one of these cached images  that was courrupted. Try deleting them (mabey backup the folder first?), then hopefully they will be regernerated.

Tell me how it goes

---

### Post by syxbit on 2006-07-29
thanks for the idea.
it didn't  work, however
the fact that mousing over it fixes it temporarily means it has to be the video driver (i think)
i managed to install the video drivers, and fglrxinfo now shows ATI instead of Mesa
any other ideas ?

---

### Post by markh0001 on 2006-08-09
I have exactly the same problem with an IBM Thinkpad A31. Device Manager shows the video adapter to be a 'Radeon Mobility M7 LW [Radeon Mobility 7500]', the X config has it as a Radeon Mobility M7 LW [Radeon Mobility 9000].

I've tried dpkg-reconfigure xserver-xorg to no effect. Everything is ok, apart from the corrupt buttons.(There's no hardware issue, the machine runs XP without any problems).

I've seen this before when I used to work on GPU's and the memory or core timings were set incorrectly. 

The only other thing I've noticed is that during a restart from hibernate the screen is corrupt, follwed by a VGA console briefly flashing up a message indicating that something is wrong with the video config, then X starts - I've not managed to capture the message.

---

### Post by p0rnflake on 2006-08-10
Having the exact same issue here with an Thinkpad T42 with ATI 7500 Mobile.

Running 6.06.1

---

### Post by joemastro67 on 2006-08-16
Same issue here as well. IBM T40 with an ATI 7500.

---

### Post by becatlibra on 2006-11-26
Had that problem on a T42 - switched themes and it didn't happen anymore.

Something with the human theme . . ,

---

