---
title: "NVidia driver not working on Inspiron 8200"
date: 2008-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thechop on 2008-07-07
Hi all,

I am having trouble getting my NVidia driver working on my Inspiron 8200 (graphics card GeForce 440) with Hardy 8.04. I didn't have any problems with the Feisty version after I downloaded and installed the NVidia driver and added the following option to xorg.cong:

Option "UseDisplayDevice" "DFP-0"

I got this tip from the following link [http://ubuntuforums.org/showthread.php?t=528207]("http://ubuntuforums.org/showthread.php?t=528207")

Unfortunately the same doesn't work on Hardy. I am doing the following steps:

1. CTRL+ALT+F2 on startup.
2. sudo /etc/init.d/gdm stop
3. sudo sh NVIDIA_... (long filename). I follow the instruction and generate a new xorg.conf.
4. I add the "UseDisplyDevice" option above.
5. sudo /etc/init.d/gdm start

... and everything work, except for when I restart and I get the "Low graphic mode" message.

Has anyone had the same problem or has anyone had success with getting it going?

Thanks in advance.

Chris

---

