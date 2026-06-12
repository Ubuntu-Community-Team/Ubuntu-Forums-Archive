---
title: "Change Video RAM for 945GM"
date: 2008-12-24
forum: General Help
---

### Post by Pipmeister. on 2008-12-24
Hi there. I have been using ubuntu 8.04 for about a month now, and the experience has been very rewarding. I am using a HP Compaq nx6120 with the 945GM intel graphics "accelerator". I need to know how to change the amount of RAM which is dedicated to the graphics. In windows there was an option to change this, and i want to do it now in ubuntu. I have checked the BIOS and its not in there.

Can anyone help me?

---

### Post by Zorael on 2008-12-24
From the man page of the intel driver:
> By default, the i810 will use 8 megabytes of system memory for graphics. For the 830M and later, the driver will automatically size its memory allocation according to the features it will support. The VideoRam option, which in the past had been necessary to allow more than some small amount of memory to be allocated, is now ignored.

---

