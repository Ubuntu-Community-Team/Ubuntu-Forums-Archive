---
title: "White screen after ubuntustudio-audio and ubuntustudio-video install"
date: 2008-08-07
forum: Desktop Environments
---

### Post by tr33m4n on 2008-08-07
Hello there,

I recently installed ubuntu 8.04 on my laptop and it worked brilliantly. However upon realizing there was an ubuntu studio version (which would better serve my needs) i decided to install the meta packages for the audio and video editing aspects over the current installation. Now when I login the screen is white with just a cursor showing. I think it may be something to do with compiz-fusion... but i cant be sure. Can anyone help?

Many thanks

Dan

---

### Post by overdrank on 2008-08-07
> **tr33m4n said:**
> Hello there,

I recently installed ubuntu 8.04 on my laptop and it worked brilliantly. However upon realizing there was an ubuntu studio version (which would better serve my needs) i decided to install the meta packages for the audio and video editing aspects over the current installation. Now when I login the screen is white with just a cursor showing. I think it may be something to do with compiz-fusion... but i cant be sure. Can anyone help?

Many thanks

Dan

Hi and I have seen this issue with studio version of late. What is the model of the graphics card?

---

### Post by tr33m4n on 2008-08-07
erm ati mobility radeon x300... the ati drivers were working fine so dont think it was them, but im not sure

dan

---

### Post by mcduck on 2008-08-07
I'm actually pretty sure that it's the drivers.. You probably got the real-time kernel with the ubuntustudio, and your drivers are not working correctly with it. Try selecting the normal kernel from Grub menu and see if things work correctly with that one (they should..).

If you wish to use the rt kernel you probably need to disable the desktop effects..

---

