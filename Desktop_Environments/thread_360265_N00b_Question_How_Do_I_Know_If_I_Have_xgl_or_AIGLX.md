---
title: "N00b Question: How Do I Know If I Have xgl or AIGLX"
date: 2007-02-12
forum: Desktop Environments
---

### Post by JLuv on 2007-02-12
I feel like such an uber-n00b for asking this. But I want to be 200% sure that neither of these are on my setup.

I want to install Beryl on Edgy w/ nVidia drivers. I read that Edgy w/ nVidia doesn't use xgl or AIGLX, but like I said, I want to be 200% sure.

whereis returned no results and Synaptic doesn't show me anything pertaining to either environment. Also, is there a "find" option for apt-get? I read the man pages but I don't recall seeing an option that lets me search for installations on my system.

---

### Post by highneko on 2007-02-13
> **JLuv said:**
> I feel like such an uber-n00b for asking this. But I want to be 200% sure that neither of these are on my setup.

I want to install Beryl on Edgy w/ nVidia drivers. I read that Edgy w/ nVidia doesn't use xgl or AIGLX, but like I said, I want to be 200% sure.

whereis returned no results and Synaptic doesn't show me anything pertaining to either environment. Also, is there a "find" option for apt-get? I read the man pages but I don't recall seeing an option that lets me search for installations on my system.
To find packages you could try installing and using apt-file. You could use dpkg maybe:
# Find packages:
dpkg -l *packagename*
# Or for listing installed files that come with a package:
dpkg -L example
Is that what you meant?

About your beryl questions: I don't know, but here's a good tutorial: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

Good luck, have fun.

---

### Post by JLuv on 2007-02-13
Thanks. I ran those commands and they found nothing for xgl or aiglx. So, I guess i'm clean.

And I'm using an automated script from [that same wiki](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia) to install Beryl. 

Thanks for your help.

---

### Post by pay on 2007-02-13
AIGLX is now built into xorg 7.1 (and newer), which Edgy users so you don't have to worry about AIGLX. Just setup your xorg.conf to use aiglx and install beryl-manager.

---

### Post by JLuv on 2007-02-13
So, is there any difference/[dis]advantages to using AIGLX vs. not using AIGLX for Beryl?

I just ran the autoscript from the wiki and I don't remember seeing a line that activiated AIGLX.

---

### Post by amit1947 on 2007-02-13
I'm in the process of upgrading from 6.06 to 6.10. I installed and have been running compiz+xgl for a while , will this screw up the upgrade? If so, what components should I remove before 6.10 finishes downloading?!

---

### Post by pay on 2007-02-13
> **JLuv said:**
> So, is there any difference/[dis]advantages to using AIGLX vs. not using AIGLX for Beryl?

I just ran the autoscript from the wiki and I don't remember seeing a line that activiated AIGLX.AIGLX is built in, that it the main advantage. Also you can still use 3d acceleration with Aiglx and it is less hacky than xgl

---

### Post by JLuv on 2007-02-13
Ok. Thanks.

And I just got Beryl up and running. It's pretty sweet. :)

---

