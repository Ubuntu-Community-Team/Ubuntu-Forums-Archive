---
title: "Enabling XDMCP"
date: 2006-06-05
forum: Desktop Environments
---

### Post by scgriffiths2000 on 2006-06-05
Can someone please tell me how to enable XDMCP via SSH:

1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

Im trying to do that in order to get my vnc server up and running, but i first need to complete the above via SSH.

Thanks.

---

### Post by dmizer on 2006-06-06
i've been doing a little research on this, and it seems that you just have to edit a config file for your gdm/kdm accordingly.

this is where i found the vital info about editing the dm ... [http://www.faqs.org/docs/Linux-HOWTO/XDMCP-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/XDMCP-HOWTO.html)

see section 2.6

---

### Post by dmizer on 2006-06-13
unfortunately, the ONLY way i was able to accomplish this was to use gdm instead of wdm.  once i did that, then i just followed the instructions on page 12 of this thread:
[http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc](http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc)

and i did the whole thing from remote.

---

