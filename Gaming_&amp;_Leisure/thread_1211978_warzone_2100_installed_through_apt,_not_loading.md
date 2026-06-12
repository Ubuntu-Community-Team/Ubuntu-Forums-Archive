---
title: "warzone 2100 installed through apt, not loading"
date: 2009-07-13
forum: Gaming &amp; Leisure
---

### Post by cl0vvn on 2009-07-13
I installed warzone 2100 through apt (version 2.1 i believe is what it gets) and it will not launch.

I had been trying to build the newest one (v. 2.2.1) from source, but I gave up after someone told me it was available through apt ^_^

Any help? I'm using Jaunty, just installed on my laptop after i formatted my drive (got rid of vista). I've got an intel core2 duo t7300, a geforce 8600M GT, and 2 GB of ram.

On an ASUS G2S, if that helps any.

thanks in advance.

---

### Post by HavocXphere on 2009-07-13
Is your graphics driver installed correctly? Cause if it isn't then its not going to fly.

Also, try launching it from the console so that you can maybe see whats going wrong. error messages etc

---

### Post by Grishka on 2009-07-13
get 2.2.1 [from getdeb](http://www.getdeb.net/app/Warzone2100). or post your errors, it's tough guessing what could be wrong.

---

### Post by cl0vvn on 2009-07-13
getting this error

error   : [frameInitialise] Error: Could not initialise SDL (No available video device).

Probably is the video drivers; i'll try reinstalling.

---

### Post by cl0vvn on 2009-07-14
Alright, I reinstalled the gfx drivers, but I'm still getting that same error.

error   : [frameInitialise] Error: Could not initialise SDL (No available video device).

any ideas?

---

### Post by cl0vvn on 2009-07-14
Alright, another update, I installed 2.2.1 (most recent version) using the link posted by Grishka.

Also reinstalled the gfx drivers available from NVIDIA.

still getting this error:

error   |05:09:54: [frameInitialise] Error: Could not initialise SDL (No available video device).

Not terribly savvy, so I'm not sure what to do here. Any help?

---

### Post by Grishka on 2009-07-14
> **cl0vvn said:**
> Alright, another update, I installed 2.2.1 (most recent version) using the link posted by Grishka.

Also reinstalled the gfx drivers available from NVIDIA.

still getting this error:

error   |05:09:54: [frameInitialise] Error: Could not initialise SDL (No available video device).

Not terribly savvy, so I'm not sure what to do here. Any help?

this is odd. how did you install you graphics drivers? downloading them from the NVIDIA site and installing manually is usually NOT the way to go. are you sure they work? have you tried some other game which requires acceleration?

---

### Post by mister_playboy on 2009-07-21
> **Grishka said:**
> get 2.2.1 [from getdeb](http://www.getdeb.net/app/Warzone2100). or post your errors, it's tough guessing what could be wrong.

Thank you for that link.  I actually own the Playstation version of this game...

---

### Post by wayward4now on 2009-07-21
> **mister_playboy said:**
> Thank you for that link.  I actually own the Playstation version of this game...

I had it working with Hardy. Just re-installed it through synaptic and it works like before. I am using an nVidia 5700 card with the driver installed through nVidia via that .run file. Envyng has been broken for a while. 

You might want to go to their website and check on the includes. Just in case it's not packaged correctly, but I'd guess it's your video. . 

Oh yeah, THANKS! Now I've been playing this game for over an hour or so. Now I remember why I un-installed it, it's addicting. :)  Ric

---

### Post by cl0vvn on 2009-09-28
> **Grishka said:**
> this is odd. how did you install you graphics drivers? downloading them from the NVIDIA site and installing manually is usually NOT the way to go. are you sure they work? have you tried some other game which requires acceleration?

I installed them using synaptic. Pretty sure they work; I've gotten Quake 4 to run just fine.

Also, I installed Chocolate Doom recently, and that has given me the same error, that "no video device available."

---

