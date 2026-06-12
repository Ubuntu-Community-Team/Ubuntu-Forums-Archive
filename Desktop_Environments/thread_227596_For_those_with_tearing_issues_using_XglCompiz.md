---
title: "For those with tearing issues using Xgl/Compiz"
date: 2006-08-02
forum: Desktop Environments
---

### Post by saracen on 2006-08-02
I just compiled the latest kernel (2.6.17.7) from source and it majorly improved the tearing issues I had.  I barely have any now.  As part of compiling the kernel I also compiled the nvidia binary driver from source and this may have also improved the situation... I don't know.  But I'm a happy camper now so I recommend that all of u suffering from bad tearing issues give it a shot...

---

### Post by metathran on 2006-08-02
What about the tearing with your movies ? Or did you get tearing only when moving a window ?

Is there any way to compile this kernel easily (howto) ?

---

### Post by saracen on 2006-08-02
[Here's the HOWTO]("http://ubuntuforums.org/showthread.php?t=217657") that I followed.  It's very good.  Remember that I had to follow the troubleshooting part for getting my NVIDIA driver installed properly so be sure to check that part out.

I still have a bit of tearing when watching movies, but the situation with dragging windows has improved dramatically.  I also followed the instructions from [here]("http://www.compiz.net/viewtopic.php?id=177") to add this line to my /etc/init.d/gdm script:

```
export __GL_SYNC_TO_VBLANK=1

```

I put that inside the section that deals with exporting the LANGUAGE variable, so basically just look for this section and add that line to the bottom so the whole section looks like this:

```
if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi
  #export __GL_FSAA_MODE=7
  #export __GL_LOG_MAX_ANISO=4
  export __GL_SYNC_TO_VBLANK=1

fi

```

The other two export statements are optional.  They're for anisotropic filtering and anti-aliasing.  They made things really slow for me so I commented them out.

---

### Post by saracen on 2006-08-02
I've been trying to figure out why the newer kernel would have improved my tearing issues.  I think the reason could be this:

> In Graphics Support
-DISABLE NVIDIA RIVA IF YOU ARE USING 3RD PARTY NVIDIA DRIVERS. This has been known to cause problems

This is enabled in the Ubuntu stock kernel.  I disabled it when I compiled the vanilla kernel from kernel.org.

---

### Post by saracen on 2006-08-02
(double post)

---

