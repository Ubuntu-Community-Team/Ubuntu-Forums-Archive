---
title: "Watching TV on Linux"
date: 2005-12-01
forum: Desktop Environments
---

### Post by prawdapunk on 2005-12-01
Hello !
I have one small question for you.
How on linux a can watchinf TV(some stations whitch have internet transmisions) and recorder some programs ?
Salute

---

### Post by linbetwin on 2005-12-01
I think you need streamtuner and xmms. Maybe some other packages too. I don't know about recording though...

---

### Post by prawdapunk on 2005-12-01
*streamtuner* ? - I used them for recorder internet radios ;) 

Maybe *Penguin TV *?
This program use to watch video blogs, but maybe it can view and recorder TV ?

---

### Post by Biased turkey on 2005-12-01
Install Tvtime with synaptic. Imho Tvtime is the best. I use it to play games with my Playstation2 connected to the S-Video input of my TV-Capture card ( ATI TV-Wonder ).

---

### Post by prawdapunk on 2005-12-01
Yes, this program is very good for Graphical cards with tv extension(I have card with TV extension - GF 6600 GT with TV but I don't use them) and I'm searching a program witch can  show TV stations, whitch have a internet transmissions(you know - CNN, BBC, etc.) and it have option recorder this transmision.

---

### Post by ewtesterman@cox.net on 2005-12-01
I do not have TV on my Video Card, but I have a usb TV card (one drawback to notebooks). I cannot find a driver for it. It is a WinTV USB 2.0. I am doubtful, but wondering if anyone has found a way to make this card work in linux.

---

### Post by prawdapunk on 2005-12-02
Maybe somebody know what i must do to watching tv from internet ?
Salute

---

### Post by JazzCrazed on 2005-12-02
I've never heard of being able to record "tv from the internet," by which I think you are referring to live streaming video (similar to how traditional over-the-air radio stations simultaneously broadcast web radio streams). Tvtime is used to watch/record video from analog inputs, such as over cable or from a standalone DVD/VHS player, and is somewhat irrelevant in this case, since you seem to be describing web streaming and not analog video.

You'd need a ripper to rip streams, like what was described above. Otherwise, if you had a capture card, and your video card has an extra output, you could conceivably run from that output into your capture card's input and record analog using tvtime.

But I'm speaking completely from personal theory.

---

### Post by dbeckham32 on 2005-12-02
If you would like to record video using a Video4Linus device (such as a capture card or webcam), you can use a program called streamer. In fact, if you would like to capture video from a video capture card (such as the TV tuner cards from Hauppauge) you can simply use the "cat" command.

I have a Hauppauge 250 card installed and it's as simple as typing:

cat /dev/video0 > capture.mpg

If you're trying to capture streaming video from the Internet, you can try using mplayer. Try this command:

mplayer -dumpstream mms://domaingoeshere/filename/wmv

VLC is also capable of viewing streaming video on the Net and dumping to a file.

Have fun.

---

### Post by JazzCrazed on 2005-12-02
I'll definitely have to take a closer look at those options in VLC and mplayer! Thanks for the tips. :)

---

