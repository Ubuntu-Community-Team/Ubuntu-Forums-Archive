---
title: "Brother MFC-8670DN -- Scanner Not Working"
date: 2009-05-10
forum: General Help
---

### Post by noobwifi on 2009-05-10
I just purchased a Brother MFC-8670DN.  Got the printer working fine in Ubuntu 9.04.  Having problems getting the scanner to work in Ubuntu 9.04.  I downloaded and installed brscan, brscan2 and brscan3 from the Brother website to no avail.  It looks like for some models you need to edit certain *.ini files.  See this page 

[http://solutions.brother.com/linux/en_us/download_scn.html](http://solutions.brother.com/linux/en_us/download_scn.html)

Anyone know which drivers and which edits are needed for the Brother MFC-8670DN?  Thanks in advance.

---

### Post by noobwifi on 2009-05-11
This SUCKS.  I called Brother and they don't provide tech support for Linux.  I was told "You have to call Linux for that problem." :)  Calling Linux:  Anyone have a solution?

---

### Post by ihaveabu on 2009-05-11
i had a hell of a time with my brother 490cw. if yours wireless?

i ended up installing the CUPS driver and managing it's settings through the CUPS ip. for me it's: [http://localhost:631/](http://localhost:631/)

i still can't get the scan key to work. still trying. one of the few drawbacks of linux

---

### Post by lazyart on 2009-05-11
You can do this.  I have a 7820N that I print to and scan from.  I just upgraded to Jaunty yesterday so I have to install it all over again, but it worked cleanly before then.

You have to make sure you get the right driver and scankey for your model.  The directions to do it all are here: [http://solutions.brother.com/linux/en_us/instruction_scn1a.html](http://solutions.brother.com/linux/en_us/instruction_scn1a.html)

---

### Post by Mark20 on 2009-05-11
I don't even bother anymore when I have issues printing in Linux.  If you download [VMware Server]("http://www.vmware.com/products/server/"), or Sun's [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") (both are free) you can setup a Windows Virtual Machine and you will be able to print no problem.

---

### Post by lazyart on 2009-05-11
Try installing it as an 8660DN.

---

### Post by noobwifi on 2009-05-12
Thanks for the suggestions. Unfortunately, none of them worked.  

Got this prompt email reply from Brother:

Dear Sir/Madam,

This is the Japanese Solutions Center.
Thank you for your inquiry.

I regret to inform you that currently none of brscan drivers support MFC-8670DN.  Also we only provide email support. 

For MFC-8670DN scanner, please Install brscan2 driver and add the following line at the end of [Support Model] section in
/usr/local/Brother/sane/Brsane2.ini

0x020A,108,1, "MFC-8670DN"

And restart the system just in case.

Thank you for your cooperation.

~~~~~~~~~~~
Didn't work.  Appreciate Brother's prompt reply.  Back to Winblows Vista for now.

---

