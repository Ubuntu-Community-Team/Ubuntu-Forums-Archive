---
title: "Compiz-fusion won't work!"
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by LingLing1337 on 2007-08-25
Hey all. I just used this guide: [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)
to install compiz-fusion, then followed the next-to last posters instructions on getting it running. But I still don't have the cube desktop. I'm running Intel integrated 82945 (or something like that) graphics card with Intel GMA950 accelerator. I'm not sure if I have XGL or AIXGL. Any help?

---

### Post by Rupertronco on 2007-08-25
Did you enable your 3-d acceleration? Do you have the updated drivers for your video card? Go to a terminal and type glxinfo and copy+paste the output. Also I'd recommend that you use one of the how-to threads on this forum if you want the most recent news.

Also the repository(the source for your compiz packages) is Trevino's repository. Trevino's repo is usually, if not always, the newest set of compiz packages, but it is not always the most stable. 

What happens when you type compiz ---replace? (use alt+F2 to bring up the run dialog)

---

### Post by LingLing1337 on 2007-08-25
OK, I'm not using trevino's, I'm using the other one. In a thread I read some admin said that using Trevino's is highly discouraged. Here we go:

glxinfo gives me:

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17


compiz --replace makes the screen flash to just my background then brings up all my windows again. Doesn't seem like it does much.

EDIT: I removed Compiz and used a different guide than I originally stated, one on this forum. I can't remember the repository, but it had "dogfood" in the URL. This is really making me mad. All the guides out there are for ATI and Nvidia, nothing for my Intel Integrated.

---

