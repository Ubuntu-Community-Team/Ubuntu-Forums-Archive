---
title: "Ubuntu desktop is half black and wrong colors."
date: 2013-03-26
forum: Desktop Environments
---

### Post by stickjoe on 2013-03-26
After a fresh install of Ubuntu desktop i find my desktop to be half black and half weird messed up colors. Is there anyway to fix this?

---

### Post by Frogs Hair on 2013-03-26
Could you describe the computer and Ubuntu version please. Select the print screen key and then you can upload the thumbnail  to the forums with the manage attachments option below the reply box.

---

### Post by stickjoe on 2013-03-26
Its Ubuntu desktop 12.10 64 bit. I don't have the system specs on me but it is a server machine if that helps.
i had already taken this picture sorry for no print screen im not typing on the same machine.

---

### Post by Frogs Hair on 2013-03-26
Welcome to the forums BTW

It definitely looks like a graphics problem, but without some more information about the computer there isn't much to be done at the moment. If I give you a command to display system information it doesn't help because you can't read it or post it here.

---

### Post by stickjoe on 2013-03-26
I found this on the website where i bought it. **[h=1]"Super Micro 512F-280B Dual Xeon Quad-Core L5420 2.5GHz 8GB 250GB 1U Mini Server w/Video & Dual GbLAN"[/h]**

---

### Post by Frogs Hair on 2013-03-26
The video specifications (w/video ?) are important because there is no way to suggest a video driver installation  without that information if there is one available. The server editions don't include a GUI, so I guess it depends how you intend to use the installation as to weather that is important. The cpu and memory are fine for all flavors Ubuntu.

 Lubuntu and Xubuntu have lower video requirements than the default Ubuntu desktop edition and don't include Unity. Lubuntu uses the least resources of the two.

[http://lubuntu.net/taxonomy/term/226](http://lubuntu.net/taxonomy/term/226)

[http://xubuntu.org/news/tag/12-10/](http://xubuntu.org/news/tag/12-10/)

---

### Post by gordintoronto on 2013-03-26
If you were able to boot a LiveCD or LiveUSB, you can open Terminal and enter this command:
lspci

It should produce just over a dozen lines of output, and one of them should include "VGA". If you were to post that line, it should help to solve your problem.

---

