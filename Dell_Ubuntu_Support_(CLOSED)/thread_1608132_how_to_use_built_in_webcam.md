---
title: "how to use built in webcam?"
date: 2010-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BeladonaVamp on 2010-10-28
hi, i am kinda new at this  so  please forgive  my  kinda dumb question  and  please give me answers  a non geek can understand, lol  I can't seem to figure out how to get the built in web cam on my computer to work  with 10.10.  It wasn't really an issue before , my computer was duel booted so i  would use windows when i wanted to use it  but now  i only  have ubuntu and i have tried a few programs out but none of them seem to work really well and for some reason i can't seem to find the one i used to use.

I have a dell inpiron 1420 with a  built in web cam  and i know  on windows it had  dell web cam center  but i am not sure if  that is also on ubuntu or even if i could  get it to work with wine.    I have done a little searching around the forums  and all i can  seem  to find is info referring to  usb web cams.  All i really want to be able to do is  take photos using my web cam,  i am not really worried about being able to get online with it.  I tried cheese but  it takes really bad photos  and i know my web cam  can do better then that!!!

any help is  really appriciated!!!!

---

### Post by mikewhatever on 2010-10-29
Do you mind explaining what exactly is wrong. 
Webcams are usually not intended for taking good quality pictures. With the pixel count ranging from 0.3 to 1.3 mega-pixels, the best they can do is take small pictures of average quality.

---

### Post by murmik on 2010-10-30
I have similar problem with inspiron mini 1012. Just got it and as I'm dealing first time with ubuntu, I even can't find, what kind of webcam I have here built in. 
I'm using Ubuntu 10.04 and only my gmail account recognises that I have webcam in my computer, but it does actually not work at all. Skype does not see it. 

Regards
Tarmo

---

### Post by mikewhatever on 2010-10-30
Hi murmik, I don't think your problem is similar in the least. You have different Ubuntu versions, and the OPs webcam takes bad quality pictures, whereas yours doesn't work at all. It's odd though, because I thought Dell mini 1012 was well supported.

---

### Post by murmik on 2010-10-31
Hi,

Thank you for your opinnion. In my example I would say it is not well supported. First I had to change Dell Wi-Fi card to Intel, to get it work. Now I can't find webcam. Firefox tells me every time I start, it is already open and I should close it, even after restart of OS.

Tarmo

---

### Post by Unicorn85 on 2010-11-15
Hi, 
Even I have a problem with inbuilt web cam detection with ubuntu. 
I have recently installed Ubuntu on my Dell laptop. 
Can anyone please guide me how do I set up my inbuilt webcam to work on ubuntu ??


Thanks

---

### Post by fenway2k on 2010-11-16
Not to be left out of this thread, but I am having webcam issues as well.

I have a Dell Latitude D531 and after becoming disillusioned with Windows, I have decided to switch to Ubuntu 10.10.

I love the O/S even though I am very new to using it. However, I noticed that nothing seems to detect my webcam.  The reason I am given is that the drivers are missing.

I went to Dell and couldn't find drivers for it. Is there any place where I can find some generic drivers just to get the webcam working?

---

### Post by azertyh on 2010-11-17
hello,

i have a dell vostro 1015 with a built-in webcam. what i did to use this webcam with cheese?

1- opened a terminal and typed ```
gstreamer-properties
```
2- it gave me error that i must install gnome media to use gstreamer-properties
3- opened synaptic and installed gnome media
4- repeat 1-
5- it opens a window with two tabs
6- selected video
7- in default input, plugin=video for linux 2 (v4l2), device=integrated_webcam_2m, and clicked TEST --> i saw my beautiful face.
8- installed cheese

i read that the module uvcvideo must be loaded if you want to use a webcam. normally, this module is loaded automatically. to be sure, in a terminal, type ```
lsmod
``` and check for uvcvideo. in my case, i have 2 modules : videodev and v4l1_compat

---

### Post by Deadbydawn on 2011-11-08
Hello all,

I tried to check my webcam with the command gstreamer-properties.

It opened the new windows with the audio and video tab. But, in the video input section, there is no webcam at all (the scroll-menu is empty and no device). 

When i launch a test, i have following message : 

** Video for Linux 2 (v4l2): Impossible d'identifier (to identify) le périphérique (the device) « /dev/video0 »**
 
and in the terminal can be read : 

** gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Impossible d'identifier le périphérique « /dev/video0 ». [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:**

Can someone help ? I cannot use Skype properly...

DELL Inspiron 1720, Ubuntu 10.04

Thanks a lot in advance

DBD

---

### Post by Shehla on 2012-11-07
Thanks. I have done it perfectly within minutes.

---

### Post by Shehla on 2012-11-07
Thanks Azerthye

---

### Post by Rushlight on 2013-03-31
I tried the above "gstreamer-properties" and  had the same issue. it couldnt find any device. Im running 12.04.2 desktop on  Gateway nv53(its ****). lest jsut say i have to use ubuntu cause my windows went awol, but thats another issue. i cant get my built incamera to work, i downloaded Cheese! and all. if you have a solution, please walk me though in code... im a copy-paste linux user XD.

---

### Post by mörgæs on 2013-04-03
Hi, welcome to the fora.

The problem is not likely to be specific to Dell. Better to post again in [Absolute Beginners Section]("http://ubuntuforums.org/forumdisplay.php?f=326"), stating the results from all your attempts together with the output from **lsusb**.

---

