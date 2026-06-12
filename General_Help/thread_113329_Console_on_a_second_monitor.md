---
title: "Console on a second monitor"
date: 2006-01-06
forum: General Help
---

### Post by Haegin on 2006-01-06
Hi,
I have just brought a new tft monitor an I am planning to use it as my main monitor with my tv set up as a console screen (like when you press Ctrl + Alt + 1). In another howto there are instructions for setting up the tv on x but not as a terminal. How would I do this?

Regards

---

### Post by jannol on 2006-01-06
I have no idea if it is possible to do, well probably not impossible but. I was wondering, you could set it up as clone and run as many terminal windows you like on the tv

---

### Post by Suger on 2006-01-06
Yes, why not use Xinerama and put Terminal windows in the TV ?

---

### Post by Haegin on 2006-01-06
How do I do that? What does xinerama do? I really don't have a clue about this - I'm just sure I can do it somehow...

---

### Post by jannol on 2006-01-06
that can be tricky since the auto configure cant config dual monitor so you'll have to edit /etc/X11/xorg.conf your self but first you need to understand your setup cause if anything is wrong in xorg.conf you can't start X

I can guide you through it but first I need to know your hardware, do you have two graphicscards or just one with dual support? if it is only one ATI I can't help very good. Also it is good if you know a few commands if something do go wrong  while trying.

I guess you know a few commands since you want terminal(s)

---

### Post by Haegin on 2006-01-06
[FONT="Comic Sans MS"]I have one graphics card with a VGA connector, a DVI connector and an s-video connector. I will be using the vga for my monitor and the s-video for connecting the tv. My graphics card is an nvidia GeForce 2 MX400 (latest and greatest as I'm sure you will agree...) and I have installed the latest drivers for it. I do know some commands for the terminal (I can do all the basics and I am a quick learner) and I am very happy to learn more.[/FONT]

---

### Post by lysis on 2006-01-06
just an FYI . . . any TEXT on a crt tv is going to look like crap. you will give yourself a headache trying to read it.   

tv's pixels are much further away than monitors, so that's why it looks much worse.

---

### Post by Haegin on 2006-01-07
Does that include text through a gui interface? I'm hoping to use the tv for msn, email and net when I'm in bed so they will all need text. Should I just accept it won't work? Thanks for the help so far.

---

### Post by jannol on 2006-01-07
ok, zorry i've been gone, have you tried anything yet?

can you attach your xorg.conf to a post and I'll try to modify it for you, in that case I wanna know if you want to use clone or not, what TV type you have ex PAL-G/NTSC-M and what resolution you want and can use on your tv.

---

### Post by Haegin on 2006-01-07
I haven't tried anything with my tv yet as I'm still waiting for the cable to arrive but I have hooked up a second monitor using a dvi-analogue converter and tried to set up a dual monitor setup on the two screens. I followed the instructions from Nvidia but it still failed to work so currently I have the same image on both monitors. There was a message after X closed saying something about not supporting two graphics outputs on my card but according to Nvidia my card can handle dual outputs. I think I will have to wait until the cable arrives next Friday to do much more.

---

