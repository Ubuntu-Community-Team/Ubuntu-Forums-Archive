---
title: "video-out on a PC"
date: 2005-11-08
forum: Desktop Environments
---

### Post by nemik on 2005-11-08
hello,

i'm not sure where to start....i want to make a little computer with a video-out card that can output a full-screen webpage to a video-input source via the video-out on its graphics card.

however, while it is outputting that, making it so the computer is still usable and can have the OS usable and open and working but through its VGA port for the monitor.

where would i begin for such a project? any recommended video cards? program it in C++, use GDK++ as the GUI?

any suggestions on where to begin would be greatly appreciated.

thank you everyone!

---

### Post by Ampersand on 2005-11-08
For a start, I'd recommend getting an Nvidia graphics card, since the Linux drivers seem quite a bit more reliable than the ATI ones. Any of the current nvidia cards should support svideo out under Linux. A search for the name of the video card along with 'linux' should give you a general idea of how well supported it is.

It may alternatively be worth looking into having two graphics cards. It might be easier to get two seperate displays that way, rather than having the same thing on both.

---

### Post by nemik on 2005-11-08
thank you ampersand. that makes sense. to cut costs i am thinking of using 2 generic nvidia-based video cards. one for the VGA output and other for the output to video-out (s-video or RCA).

the tricky part is that i need the VGA output to display the linux OS (Gnome in ubuntu's case) and all that nicely, but the other video-output should display only a certain program that i choose!
i have a feeling that is going to be the hardest part.

---

### Post by nemik on 2005-11-08
so does anyone know of which software or component in the OS i should look at to get started on this?

---

### Post by graabein on 2005-11-09
You could start out by doing a forum and wiki search on tv-out. Browse the threads and you should get some ideas. 

I have not looked into it my self. I have an nvidia-card but I have not successfully configured my xorg.conf and nvtv (or something) does not work with my 6600 GT.

:(

---

### Post by nemik on 2005-11-09
thanks graabein, i'll have a look around the other resources. i'm wondering if nvidia may not be the best choice because they don't seem to be supported that much.

i know ATI is the worst but maybe something better than nvidia exists, i heard matrox had very good linux support.

---

### Post by Denis on 2005-11-09
Hi. I sometimes connect my system to a TV. I am using S-video for tv out. I guess this also your situation, but maybe with another video in... ?

I've got an Nvidia card, I think in general it will be best to take an Nvidia card, for it's support. 

Right now I use the default behaviour of Ubuntu (Hoary), I either connect the TV or not. To switch to TV of monitor, I have to restart X. 

But I tried some different things before. I think this may be interesting for you: you can use 2 "displays" and each one shows half your desktop. This means if you move your cursor to the end of your monitor, it will snap to the TV. 

here is how I have done this: [http://ubuntuforums.org/showthread.php?t=23628](http://ubuntuforums.org/showthread.php?t=23628) (Though I didn't use that "tv" command)

This way you just need one card with S-video and normal output. 

Maybe this helps you to get an idea of what's possible...

---

