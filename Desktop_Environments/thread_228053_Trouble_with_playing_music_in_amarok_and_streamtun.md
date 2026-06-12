---
title: "Trouble with playing music in amarok and streamtuner"
date: 2006-08-02
forum: Desktop Environments
---

### Post by geovino on 2006-08-02
I've tried to use streamtuner and most of the time xmms just freezes up! amarok which everybody likes doesn't play anything, it says "playlist finished" What's with that! I did not have these problems using these with PCLinuxOS. What's wrong with Ubuntu? The only one that has worked is Banshee and I would like to do live streaming. iTunes is still the best and I hope one day a linux like program will be available because most of the other are second rate in comparsion. I've had to restart the computer two times because these audio programs just freeze up. 

Does anyone know how to get these to work? Thanks!

---

### Post by Fully216 on 2006-08-04
Did you install all the restricted formats (like mp3)?  I followed the tips found here to get music to play.

 [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hope this helps!

---

### Post by geovino on 2006-08-05
I went to Synaptic and installed every gstreamer file I could. I must have got the right one... it's working!

---

### Post by lukanikos on 2007-07-11
not working for me?
how did you do it?

---

### Post by geovino on 2007-07-11
can you get either, amaorak or streamtuner to work? 

Go to Synaptic and search for Streamtuner. What files are installed? I libdvdcss2 and w32codecs installed?

---

### Post by lukanikos on 2007-07-11
> **geovino said:**
> can you get either, amaorak or streamtuner to work? 

Go to Synaptic and search for Streamtuner. What files are installed? I libdvdcss2 and w32codecs installed?

streamtuner it's installed and I get this msg when I try to play a station

```
Unable to tune in
Failed to execute child process "xmms" (no such file or directory).
```

amaorak doesn't exist in Synaptic
the libdvdcss2 and w32codecs dont know if they are installed or not?
How can I see?

---

### Post by geovino on 2007-07-11
Go to > System > Administration > Synaptic package manager. All the programs to install are here. Just do a search for:

w32codecs
libdvdcss2
xmms
streamtuner
amarok

Install all of those and see what happens.

---

### Post by lukanikos on 2007-07-11
working now!!

Great!!

Thanks!!


I had to install XMMS and worked.

---

### Post by maxrisc on 2007-08-03
The original title of this post was Streamtuner and Amarok.

Can these two be used together without the XMMS application that is probably going to be removed soon?

---

