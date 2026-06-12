---
title: "Possibility USB external data only drive working on 2nd PC"
date: 2009-05-05
forum: General Help
---

### Post by texas.chef94 on 2009-05-05
Would be surprised if there is a way, but had to ask.
My wife and I both run 9.04, she has windows as dual boot I only have ubuntu
if that is relevant.
I have 160GB external USB data drive only. My question is there any way short terms to plug the USB into her PC and access data.

Thanks

Allen

---

### Post by prem1er on 2009-05-05
I'm not sure I'm understanding your question.  Do you mean you run Ubuntu off the external usb drive, or you just have some files that you save on the drive that you want to be able to access on the 2nd computer?

---

### Post by codeseer on 2009-05-05
If it's just an external USB data drive, you can unplug it from one system and plug it into another system and it should be recognized and show up under the Places menu in Ubuntu. In Windows, it should show up under My Computer.

---

### Post by texas.chef94 on 2009-05-05
I think codeseer answered the question, but to make it abundantly clear on my PC 9.04 is installed on my HD and my 160GB USB is one huge data partition.
My question was can I plug that USB into my wife's PC and access data from that drive.

Allen

---

### Post by prem1er on 2009-05-05
Yes, follow Codeseer's response.

---

### Post by gordintoronto on 2009-05-05
If the external drive has a format that Windows can recognize, you should be OK.  If it's EXT3, that's a different story.  I seem to remember that there's an EXT3 driver for Windows, but I don't have any details.


> **texas.chef94 said:**
> I think codeseer answered the question, but to make it abundantly clear on my PC 9.04 is installed on my HD and my 160GB USB is one huge data partition.
My question was can I plug that USB into my wife's PC and access data from that drive.

Allen

---

### Post by texas.chef94 on 2009-05-05
This file format adds another question. The USB data partition is in fact ext4. If that makes a difference what if I booted directly into ubuntu on the other PC, then plugged in USB and went to places leaving windows out of the mix.

Allen

---

### Post by codeseer on 2009-05-05
9.04 should have no problem recognizing Ext4. I believe there's a beta type driver that supports Ext4 as well in Windows though.

---

