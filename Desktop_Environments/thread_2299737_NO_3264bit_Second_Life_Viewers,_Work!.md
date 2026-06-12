---
title: "NO 32/64bit Second Life Viewers, Work!?"
date: 2015-10-20
forum: Desktop Environments
---

### Post by yogich246 on 2015-10-20
I have installed both 32 & 64 bit Ubuntu distros on my Mac's Windows partition, & a Sandisk Ultra Fit USB stick, respectively, with success. Under no circumstances, can I get it to actually load, and work. The 64 bit versions --tho they say i686, in the filename-- are asking for the deprecated ia32libs. Both Linden Lab & Firestorm have done, this, as has the new Catznip. It is as if they do not know that the ia32s are NLA!

I read, in a January 2015 post, that someone successfully ran Singularity. I, however, could not. It required installation, which I did according to instructions, and still would not work.

I realize, that there are many SL users, out there. Is there ANYONE, who can help me, with this? I have been away from Ubuntu, for awhile, but am fairly familiar, all the same. I'll do my best to supply whatever additional info, if any, as required.

Thank you.
--
Intel Mac Mini, 4 GB RAM, & its std internal equipment, otherwise. Booting, from USB stick, since grub didn't wish to write to sda4, or, wasn't found.

---

### Post by Toz on 2015-10-21
Were you getting any error messages?

With respect to the Singularity viewer, on my 64 bit Xubuntu 15.04 install, I simply:
1. Downloaded and uncompressed the 64-bit install file: [https://bitbucket.org/SingularityViewer/singularityviewer/downloads/Singularity-x86_64-1.8.6.6157.tar.bz2]("https://bitbucket.org/SingularityViewer/singularityviewer/downloads/Singularity-x86_64-1.8.6.6157.tar.bz2") (BTW, there are separate i386 and x86_64 files)
2. Installed libasound2-plugins:i386:
```
sudo apt-get install libasound2-plugins:i386
```
3. Ran the singularity executable from its uncompressed directory:
```
/home/toz/Downloads/Singularity-x86_64-1.8.6.6157/singularity
```
...and it worked.

Can you be more specific about the version of Xubuntu you are using, whether you are currently running a 32-bit or 64-bit, and exactly what error messages you are getting when you are trying to run it.

---

### Post by yogich246 on 2015-10-28
Thank you, for your response. As stated, in 1st paragraph: Mac's Windows partition has 32-bit Ubi-15.04 & Sandisk Ultra Fit has 64-bit Ubi-15.04. ;)

The output, is listed in another thread, to which I received no replies: [http://tinyurl.com/pbgd3ar](http://tinyurl.com/pbgd3ar)

---

### Post by Toz on 2015-10-28
Try the instructions from my previous post on your Ubuntu 15.04 64-bit install and see if it works.

---

### Post by yogich246 on 2015-10-28
Bless you, Toz! Singularity, it is! Works, like a charm! :lolflag:

---

