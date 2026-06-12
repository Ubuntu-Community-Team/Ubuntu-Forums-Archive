---
title: "Only one application can use my Sound Card at a time. What do i do???"
date: 2006-04-29
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-04-29
Hi,

I have a compaq evo320. using the onboard sound device.
My sound card cannot be shared between applications. Only one application can use it at a time.
I want to play all the sounds at a time.

what do i do..

Regards
-
Dc

---

### Post by deadgobby on 2006-04-29
[QUOTE=dhruv_1884]Hi,

I have a compaq evo320. using the onboard sound device.
My sound card cannot be shared between applications. Only one application can use it at a time.
I want to play all the sounds at a time.

what do i do..

Regards
-
Dc[/QUOTE]
Hi there,

Open your terminal and type.
killall esd

It may be your sound and memory maybe like a mono Synth. Plays one note at a time.

---

### Post by louis_nichols on 2006-04-29
[QUOTE=deadgobby]Hi there,

Open your terminal and type.
killall esd

It may be your sound and memory maybe like a mono Synth. Plays one note at a time.[/QUOTE]

You should also check that all your apps use alsa for utput. Such options are usually in every settings menu.

Also, check under multimedia systems selector that alsa is selected both for output and for sink.

---

### Post by dhruv_1884 on 2006-04-29
Hi,
how do i check my multimedia settings, new to linux
 Regards,
Dc

---

### Post by Ramses de Norre on 2006-04-29
system > preferences > multimedia systems selector

---

### Post by dhruv_1884 on 2006-04-29
[QUOTE=Ramses de Norre]system > preferences > multimedia systems selector[/QUOTE]


Thanks,
It's working fine now

---

