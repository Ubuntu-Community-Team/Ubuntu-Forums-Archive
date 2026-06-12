---
title: "gpib IbaAUTOPOLL"
date: 2014-06-03
forum: Education &amp; Science
---

### Post by gary37 on 2014-06-03
I've been tasked with porting some very old software that uses NI gpib running on Solaris8/Ultra 1 to something newer. I'm attempting linux-gpib on ubuntu using a NI gpib-pci card. I'm new to linux, gpib and I'm really not a code pig, so I'm probably missing something obvious. The software mostly works, except for what I believe to be a manual serial poll, which always timesout. I think I need to turn off automatic serial polling, in order for a manual poll to work. I've written a short test program that basically does the following:

ibask (board_handle, IbaAUTOPOLL, &askval);
 ibconfig (board_handle, IbcAUTOPOLL, 0 );
 ibask (board_handle, IbaAUTOPOLL, &askval);

The askval is always 1 with ibsta not showing any ERRs

Is this possibly a configuration or hardware problem or is it poor understanding on my part? If it's me could you point me at what I've missed? I've read quite a few howtos on polling and I'm admittedly not clear on it. Also if there is a better place to post this, that information would be of great value. 

TIA
g

---

