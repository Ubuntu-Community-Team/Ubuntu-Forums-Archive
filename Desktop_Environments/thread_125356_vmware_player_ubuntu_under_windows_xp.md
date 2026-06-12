---
title: "vmware player ubuntu under windows xp"
date: 2006-02-03
forum: Desktop Environments
---

### Post by tthkbw on 2006-02-03
I am running a vmware player version of ubuntu under windows xp.  I use this to provide me with a cross-compiler for a powerpc version of linux we use.  I have the cross compiler installed and running in the virtual machine.

What I need now is to have a tftp server running from ubuntu.

The ubuntu I am running doesn't have a /etc/inetd.conf file and I don't see how to get the tftp server operational.  

Any pointers to howto's on this?

Thanks,

Terry Brown

---

### Post by Jason_25 on 2006-02-03
Install netkit-inetd from the repos.

BTW, are you using the secure browser applicance?

---

### Post by tthkbw on 2006-02-04
Thanks for the help, I now have it running, although I the in.tftpd is in /usr/sbin, not /usr/bin on my installation.

I am not using the browser appliance.  I can't remember where I got it from, but I have an ubuntu-5.10.zip file which contains a sort of minimal installation of ubuntu, and I have added to that. 

This is a great tool for me.  We do software test development and hardware testing of our embedded linux 3d camera system using linux boxes--now I can do all this from one computer with vmware player running Ubuntu.  The embedded system boots Linux using tftp.  Cool.

You can see what we do at [www.tyzx.com](www.tyzx.com).

Terry

---

