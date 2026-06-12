---
title: "Anyone get Amnesia working with Intel HD 4000?"
date: 2012-07-02
forum: Gaming &amp; Leisure
---

### Post by amoxicillin on 2012-07-02
I am assuming that it crashes because of OpenGL and my lack of a dedicated graphics card but I have found some threads where people are saying it should run with Intel HD 3000 graphics and above.  I also have seen people suggest to install it in your home folder.

My question is, does anyone currently have it running under an Intel Ivy Bridge setup with the integrated HD 4000 graphics?  I downloaded it from the USC and am using 12.04.  If so, what did you do to make it run?

---

### Post by Dlambert on 2012-07-02
> To get Amnesia to run on an Intel HD 4000 (integrated Ivy Bridge graphics), I had to do the previously mentioned "**force_s3tc_enable=true**" trick. After that and a bit of graphics-quality tweaking, it runs like a charm.

To do this:

```
sudo apt-get install driconf
driconf
```

Open driconf, go to the tab "image quality" and activate the S3TC texture compression, even if the software support is not available. (Default is "no" change to "yes")

---

### Post by amoxicillin on 2012-07-02
Worked like a charm!  Thank you Dlambert!!

---

### Post by Dlambert on 2012-07-03
Please mark thread as solved! :D

---

