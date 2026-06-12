---
title: "Beryl Skydome image --low quality"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by guitarben on 2007-06-12
I just switched from Fedora to Ubuntu and so far I've really been enjoying it. I've got beryl up and running and the only thing that's bugging me is the poor image quality of my skydome. It better than EGA but it reminds me of KQ4! I'm using the same image that I was using in FC6 and it looked perfect. So I know my laptop is capable of displaying it properly.

This is a Dell Inspiron w/ the Intel 945/950. 
Resolution: 1440x900
gxlinfo -l |grep GL_MAX_TEXTURE_SIZE 
        2048
xvinfo |grep max
       maximum XvImage size: 1920x1088

The image I want to display is a png @ 2048x1024. I'm guessing the problem is w/ Xv or an xorg setting. Any ideas? This is driving me crazy. 

Thanks for the help.

---

### Post by guitarben on 2007-06-12
also: I've tried using the intel driver and the i810.

---

### Post by Chymera on 2007-08-29
you could be a little more specific about "poor quality" maybe a screenshot could give us some idea.
As far as i'm concerned beryl skydome always looked exceedingly  crappy :(

---

