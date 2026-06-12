---
title: "How do I upgrade Ubuntu 8.04 that came pre-packaged with my Dell Mini 10?"
date: 2010-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MasonOrange on 2010-05-04
I purchased a Dell Mini 10 netbook w/ Ubuntu 8.04 pre-installed rather than Windows.  I've done some research and been unable to find people who successfully upgraded to newer versions of Ubuntu (I, of course, can't figure out how to myself).  Has anyone here had any success?  Should I install the newest Ubuntu independently?  How would I go about this?

---

### Post by snowpine on 2010-05-04
Back up your documents and do a fresh reinstall. There is no other method.

Be aware that, depending on which model of Dell Mini 10 you have, your graphics card may not be compatible with "mainstream" Ubuntu releases. If you're one of the unlucky users who has the GMA500 "pouslbo" graphics, you should give this thread a read: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

If you have a Mini 10v, then you have the well-supported Intel GMA950 graphics and can follow the guides on this site: [http://www.ubuntumini.com](http://www.ubuntumini.com)

---

### Post by MasonOrange on 2010-05-04
Just checked my order history (got it back in early Feb) and I DO have a 10v w/ GMA 950.  Thanks for your help, I'll look into it tonight.

---

### Post by my_linux on 2010-05-04
For info about Dell specific Ubuntu releases you should take a look at: 

[http://linux.dell.com/](http://linux.dell.com/) - There's no 10.04 at present.

I agree with snowpine though it's generally better to do a clean install. Consider it your once in a while spring clean :)

---

### Post by snowpine on 2010-05-04
I have the Mini 9, which from what I understand, is the same basic hardware as your 10v with a smaller 9" screen. I think you will find the current version of Ubuntu will run very well, with minor tweaks to get the wifi working and possibly the audio. I am currently running Debian on mine :) but I had good success with Ubuntu 9.04 when I tried it a year ago.

The Dell Remix 8.04 used the "lpia" (low power intel architecture) which Canonical has dropped support for. As of 10.04, all of the Atom optimizations have been rolled into the "regular" i386 release. If there is a direct Dell Remix 8.04 to 10.04 upgrade path, Dell will have to make it themselves (or pay Canonical a lot of money to develop it special).

---

