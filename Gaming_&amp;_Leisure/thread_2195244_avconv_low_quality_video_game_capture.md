---
title: "avconv low quality video game capture"
date: 2013-12-23
forum: Gaming &amp; Leisure
---

### Post by tehcavil on 2013-12-23
OK here is the situation: i am running starcraft 2 through wine in a separate xserver but using avconv to record it is extremely low quality/pixelated. Can anyone offer suggestions to improve video quality?

here is an example of a video i took with avconv:

[http://www.youtube.com/watch?v=cO4aKuY_XLg](http://www.youtube.com/watch?v=cO4aKuY_XLg)

I am using the command:

avconv -f x11grab -s 1280x720 -r 30 -i :1.0 -f alsa -ac 2 -i default starcraft.mkv

any tips?

---

### Post by dannyboy79 on 2013-12-23
What are you computer spec's?

it takes a lot of computer power to play the game AND record it. Have you attempted to use simplescreenrecorder? I believe it just uses avconv or ffmpeg BUT it's gui based and may provide some setting to be used that you just don't know how to implement using the command line version of avconv or ffmpeg. I have great success using simplescreenrecorder

---

### Post by Arthur_D on 2013-12-23
Try using -vcodec rawvideo but remember this will eat tens of gigabytes in just a few minutes. Then you can encode it in a more lossy format later.

---

### Post by tehcavil on 2013-12-24
> **Arthur_D said:**
> Try using -vcodec rawvideo but remember this will eat tens of gigabytes in just a few minutes. Then you can encode it in a more lossy format later.

I tried using -vcodec rawvideo, it has no effect on the pixelation. maybe there's some sort of container format i need to use as well? could that be effecting it? should i use ogg webm or mkv?

---

### Post by Arthur_D on 2013-12-24
Hmm no the container shouldn't really affect that I think. I tend to just use .avi as the filename/container. Try adding -sameq as well.

---

### Post by dannyboy79 on 2013-12-24
without your computer spec's listed to know how powerful of a computer you have no one will be able to help you. It could be a matter of your computer just not being strong enough

and by the way Arthur_D, -sameq isn't even used by Avconv, see [http://libav.org/avconv.html](http://libav.org/avconv.html)

---

### Post by tehcavil on 2013-12-25
My computer specs are:

AMD 6-core 3.7 processor, one of those faildozers i got cheap off of amazon for like 100$ after they flopped. 
They aren't bad processors, just not insanely fast like they were hyped to be.

16GB RAM - something like 1066 mhz, forget exactly.

2GB ATI/AMD video card using proprietary driver from ubuntu. It's called "V243H VisonTek Radeon HD 5450".  is DDR3/500mhz/8GB bandwidth


Mini ATX motherboard by MSI. 

1.5 TB hard drive. 5400 rpm.

Edit: also, i cant seem to find simplescreenrecorder in the Repos.

---

### Post by tehcavil on 2013-12-25
solved! I added

-qscale 0.1

to it and it works like a charm now!

---

### Post by dannyboy79 on 2013-12-26
glad you got it sorted out. simplescreenrecorder isn't in the default repo's. you can install it from a ppa or by downloading the deb's

---

