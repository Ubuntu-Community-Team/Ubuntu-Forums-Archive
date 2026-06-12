---
title: "no sound with mpegs"
date: 2006-02-08
forum: Desktop Environments
---

### Post by bung-foo on 2006-02-08
So, I figured out how to add universe and multivers and get mpeg video support but none of the .mpg or .mpeg movies I have play with sound. I have a few .avi and divx movies that play with sound just fine.

I'm really new to ubuntu and would really appreciate some assistance with this.

---

### Post by queenorych on 2006-02-08
Make sure you have the proper audio codec.  What player are you using?  Taking a guess I'd say enable all your repositories (under package manager) install gstreamer-ffmpeg, and any other gstreamer-(whatever) you see.

---

### Post by mjsoccer1 on 2006-02-08
you can install the gstreamer meta package (see Synaptic), that should cover all your bases as far as having all of the correct codecs.  If that doesn't work, try changing your Multimedia system- I use ESD and it works great (though, since you can hear AVIs, I would not suspect this to be the problem)... Let us know if that helps

---

### Post by bung-foo on 2006-02-08
Ok, I'm at work for the next few hours but I'll try your suggestions when I get home and then post the results.

I installed gxine (because I like it). Prior to that NO movies would play, after that, my current situation developed.

Thanks a lot everyone.

---

### Post by bung-foo on 2006-02-08
that seemed to do the trick. Thanks folks.

---

