---
title: "Unable to read .ICEauthority"
date: 2009-03-27
forum: General Help
---

### Post by Sigma47 on 2009-03-27
Hey, I was messing with my file permissions earlier today and all of a sudden bam...my desktop is gone when I login to Ubuntu and it displays a message similar to the subject. I have tried changing the owner and group of the directory and all subs back to me and my group, as well as modding permissions to 644 of my entire user directory...no dice!!! So what now, when I go to TTY I can't cd or ls my home directory w/o being su...please help!!! :confused:

**Got it** Nevermind I figured it out...I had to give exec..priveledges or something any way Im back with my GUI where I need to be...but one thing i do need to know and that is : how do I mark a post as solved or done?

---

### Post by snova on 2009-03-27
> **Sigma47 said:**
> Hey, I was messing with my file permissions earlier today and all of a sudden bam...my desktop is gone when I login to Ubuntu and it displays a message similar to the subject. I have tried changing the owner and group of the directory and all subs back to me and my group, as well as modding permissions to 644 of my entire user directory...no dice!!! So what now, when I go to TTY I can't cd or ls my home directory w/o being su...please help!!! :confused:

644 doesn't include +x permissions. On directories, the +x bit refers to permission to enter/list contents of, or something to that effect (I'm not sure of the precise implications +x has, only that you need it).

> **Got it** Nevermind I figured it out...I had to give exec..priveledges or something any way Im back with my GUI where I need to be...but one thing i do need to know and that is : how do I mark a post as solved or done?

There used to be a way of marking it as such (it was under Thread Tools), but it was disabled a while back due to database issues. The currently recommended method is to add a 'solved' tag to the thread.

---

