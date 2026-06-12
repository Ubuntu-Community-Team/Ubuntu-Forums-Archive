---
title: "Do I need more than just firewire PCMCIA card?"
date: 2009-05-04
forum: General Help
---

### Post by MooseMagnet on 2009-05-04
I want to add a firewire PCMCIA card to my laptop, to capture the video from my Sony digital film camera. The camera has a firewire port. 

I'm running Intrepid. Do I need to download some drivers? Or do I only need the card and Kino or Kdenlive? 

thanks,
R-

---

### Post by alwayshere on 2009-05-06
I had same problem and i just now sorted it by in terminal putting

 sudo nautilus

then when window pops up i went tio the filesystem and in the dev file
i found the raw1394 file and right clicked it when to prperties then permissions set all to read and write and group as disk and ticked the execute then closed all windows and then all was sorted.

if that dont help ya you may need to searh ieee1394 in synpac manager ind install everthing that sonds handy 

hey im no wiz kid just a average guy that gets there in the end somehow lol

---

### Post by MooseMagnet on 2009-05-06
Thanks. No expert here either.

What is dvgrab? I have it installed, but can't run it. Here is the description from synaptic pkg mgr.

dvgrab receives audio and video data from a digital camcorder via an
IEEE1394 (widely known as FireWire) or USB link and stores them into
one of several file formats. It features autosplit of long video
sequences, and supports saving the data as raw frames, AVI type 1,
AVI type 2, Quicktime DV, a series of JPEG stills or MPEG2-TS.

I have installed it and re-installed it, but can't start it from the terminal, and it doesn't appear in the list of applications.

Confused.

---

### Post by alwayshere on 2009-05-07
I have not used dvgrab but it sounds like the same deal as kino. I just used kino tonight to get my home vids off my dv camera and kino worked for me so i would say stick with kino.

---

### Post by Bucky Ball on 2009-05-08
Kino uses dvgrab to 'grab' or capture video. You can run it from the command line with the appropriate instructions but probably only if you are comfortable with working in the terminal.

Another thing people can try is launching Kino from a terminal with:

sudo kino

This will launch it as root so you should have all appropriate permissions. If this sorts things out, you can then create a launcher in your toolbar using:

sudo kino

as the command to launch. :)

---

