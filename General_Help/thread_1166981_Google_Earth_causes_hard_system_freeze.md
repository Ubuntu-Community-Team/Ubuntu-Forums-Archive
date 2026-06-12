---
title: "Google Earth causes hard system freeze"
date: 2009-05-22
forum: General Help
---

### Post by _Herb_ on 2009-05-22
Launching Google Earth 5 on Ubuntu 9.04 causes a hard system freeze within a minute from which I can recover only by unplugging the desktop computer. Video is vanilla integrated Intel. Any ideas on how to fix this?

---

### Post by Soul-Sing on 2009-05-22
1) what is the oucome of: ```
glxinfo | grep direct
```
2) disable visual effects and try it again

---

### Post by _Herb_ on 2009-05-22
$ glxinfo | grep direct
get fences failed: -1
param: 6, val: 0
direct rendering: Yes

Compiz is not installed.

---

### Post by HermanAB on 2009-05-22
Yup, Google Earth is really bad quality software and is best avoided. It may have the press on its side, but they sure don't know how to write decent software.

There are better alternatives out there anyway, for example a site by Microsoft, NASA, the US Geo Survey and the Atlas of Canada to name a few.  Every major country should have a government site that will do way more than Google.

---

### Post by Soul-Sing on 2009-05-22
Yep the 4.2 version was ok, the new 5.0(?) is no good.....

---

### Post by c-fstb on 2009-06-15
I had Google Earth 5.0 running sucsesfully in Ubuntu 8.10 Ibex. Now It freezes, so I reverted back to 4.3 with the same issues. I've had a few other issues sinces upgrading to 9.04 Jackalope, so I think I'm going back to 8.10 Ibex. 
  I'm quite disappointed in the response from Herman. Google Earth may not be the best software in his opinion and I don't have the knowledge to dispute that, but it is one of the best tools out there for many outdoorsman and global explorers. It's greatest feature is that it is used by much of the world so the content that is continually added by users is immensly valuble to users like myself.
    We should be trying to convince the world that Linux is the way to go and I was converted because I was fed up with windoze and found that everything available with ubuntu "just worked" with no issues. Unfortunatly I have allot of speciallized avionics software that is for windows and I've had limited success with Wine, but I'm willing to work through it.
  Google is at least onboard with Linux and writing software for it. So if you can't help with a solution then please don't make comments that will do nothing but convince some Linux newbies to switch back to windoze which at least sort of works in a bad way with most of the worlds software.
  I wish I could add more help other than to suggest reverting back to 8.10

---

### Post by DeMus on 2009-06-15
> **HermanAB said:**
> Yup, Google Earth is really bad quality software and is best avoided. It may have the press on its side, but they sure don't know how to write decent software.

There are better alternatives out there anyway, for example a site by Microsoft, NASA, the US Geo Survey and the Atlas of Canada to name a few.  Every major country should have a government site that will do way more than Google.

What a nonsense. I use Google Earth 5 on Jaunty 64 without any problems. I use it quite a lot and it never freezes or hangs or whatever. Just because you don't like this software is no reason to write it is bad quality software.

---

### Post by Arup on 2009-06-15
GE works fine here, if you are using hardware drivers from the repos it works out of the box or else if you install drivers directly from the manufacturer, you need to copy two libgl files to the /usr/lib32/google-earth folder manually otherwise you get seg fault while launching.

---

### Post by oarion7 on 2009-07-01
same problem here. although i am wondering if the problem is GE itself because i just had the same problem running second life (which i havent run in a long time in a different OS) so its the fist time this has occured, perhaps it's just a coincidence.

google earth seems to freeze up about 10 minutes after initializing the software, other than that it works great. whole computer is freeze/unresponsive and forced to do a hard reset.

---

