---
title: "World of Warcraft work?"
date: 2005-01-05
forum: Gaming &amp; Leisure
---

### Post by rudeboyskunk on 2005-01-05
I have Cedega/Wine on my linuxbox, and I want to get World of Warcraft...does it work in cedega?

---

### Post by jdodson on 2005-01-05
[QUOTE=rudeboyskunk]I have Cedega/Wine on my linuxbox, and I want to get World of Warcraft...does it work in cedega?[/QUOTE]


yes.

---

### Post by brdweb on 2005-01-06
It works almost perfectly. Even UI mods like cosmos work without a hitch.

---

### Post by robtotheb on 2005-02-07
[QUOTE=brdweb]It works almost perfectly. Even UI mods like cosmos work without a hitch.[/QUOTE]

How did u manage that?  I've tried it and its too slow compared to running it on XP, cant even work out how to get the resolution past 640x480.

---

### Post by apoc on 2005-02-07
Works for me aswell,

make sure you have AGP enabled for your card.

---

### Post by robtotheb on 2005-02-07
how do i check?

---

### Post by AndersAA on 2005-02-07
dmesg | grep AGP

you can also cat /var/log/X*.0.log | egrep 'WW|EE' (to search your X log for warnings/errors).

I also have it running rather flawlessly.  I run it in opengl, so I can't have my minimap open while inside buildings (it'll crash), but the performance is considerably better than direct3d.  (to use opengl start WoW.exe -opengl).  There's a mod available that makes sure the minimap defaults to off, so you dont have to make sure your outside when you quit :)

---

### Post by mattyh on 2005-02-08
I had heard there were some bugs that caused random crashing...experiencing any of that? I've been running windows for a while now in order to play WoW mostly, I'd like to come back to Ubuntu soon, cause to be honest I like it better :)

---

### Post by AndersAA on 2005-02-08
[QUOTE=mattyh]I had heard there were some bugs that caused random crashing...experiencing any of that? I've been running windows for a while now in order to play WoW mostly, I'd like to come back to Ubuntu soon, cause to be honest I like it better :)[/QUOTE]


I've actually had more crashes in windows than I've had in linux.  In windows it would hardlock on occasion (probably some kind of hardware bug).

---

### Post by dmatrix on 2005-02-08
World of Warcraft works great on all my Ubuntu systems in Direct3D and OpenGL. Performance is really good and the game has been rock solid for me. I do not recall having a single crash and if I did it was just WoW crashing and a quick restart fixed it up. I have been playing almost daily since the Beta started. This game is great and worth the money.

---

### Post by robtotheb on 2005-02-08
Im using an ATI 9700 card which run wow perfectly under windows but ATI drivers for linux are famous for being ******!  Any of you who have it running well in Ubuntu use similar hardware?



What does this mean??  

"you can also cat /var/log/X*.0.log | egrep 'WW|EE' (to search your X log for warnings/errors)."

Can you been more specific please - im a linux newbie :P

---

### Post by AndersAA on 2005-02-08
[QUOTE=robtotheb]"you can also cat /var/log/X*.0.log | egrep 'WW|EE' (to search your X log for warnings/errors)."

Can you been more specific please - im a linux newbie :P[/QUOTE]


execute : 
cat /var/log/X*.0.log | egrep 'WW|EE'
in a terminal, cat will show the file Xorg.0.log or Xfree86.0.log and egrep will search for WW (warnings in the log) and EE (errors).

---

### Post by robtotheb on 2005-02-08
I get this

"         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Loading extension MIT-SCREEN-SAVER
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
"

---

### Post by AndersAA on 2005-02-08
hm, well, you could atleast remove the busid line from your xorg.conf/XF86Config-4.  The chipset part I'm not sure about.

---

### Post by robtotheb on 2005-02-09
Didnt help  ](*,) 

What did you type in your WTF/config file to get opengl to work?

---

