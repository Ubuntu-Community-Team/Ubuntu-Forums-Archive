---
title: "Shifting the monitor"
date: 2011-01-04
forum: Desktop Environments
---

### Post by rodhash on 2011-01-04
Hello guys,

I usually press 'CTRL + F7' to shift between my laptop and my monitor 17", however is there any way to do that through command line?

Thanks!

---

### Post by rodhash on 2011-01-04
Sorry I didn't express myself properly.

For example, if I log in a remote computer, can I export the DISPLAY variable and launch a graphical program as mplayer movie.mkv ??

How can I check the correct value for the DISPLAY variable?

Thanks!

---

### Post by ilantal on 2011-01-04
I probably don't understand the problem, but on my laptop I also have an external monitor. I use the Twin view option and then I can drag the movie player from the small laptop monitor to the larger external monitor.

---

### Post by rodhash on 2011-01-04
Ilantal disregard my first post, I just would like to connect via SSH to a machine and run programs on X server running.

IE: I connect via SSH and I would like to run nautilus or mplayer on the X running. Got it?

---

### Post by ilantal on 2011-01-16
Hi rodhash,
I decided to see if I could understand what you are trying to do. I hooked up to my laptop running sshd with ssh running on this computer. I ran
ssh -X -v 192.168.1.102

and then I ran totem from my laptop. I could see a list of movies on the laptop, so I chose one of them. It displayed on this computer and played well over the LAN.

Do I even understand what you want to do?

Ilan

---

