---
title: "encrypt flash drive"
date: 2008-12-18
forum: General Help
---

### Post by kainalu on 2008-12-18
ok I know this has been covered before but the article was way back at gutsy and things change. what is the best way to encrypt an entire flash drive or a folder on a flash drive? can encryptfs-utils be used?

---

### Post by tornadof3 on 2008-12-18
Yes, or you could try Truecrypt ([www.truecrypt.org](www.truecrypt.org)) - which has Ubuntu packages and works really well.

---

### Post by Izek on 2008-12-18
But is it like 7zip where the encryption only appears if the another user of the flash drive uses true crypt? ;)

---

### Post by tornadof3 on 2008-12-18
When you use Truecrypt with a usb flash drive, it is usually best to use it in "container file" mode - so you have a file, say a 1gb file named "secure.tc". When that is opened with truecrypt and the correct passphrase is supplied, that file is itself "mounted" within the fiel system - eg /media/truecrypt1 in linux or as a new drive (eg G:\) in windows and you can save as many files to it as you like. Yes the other user does need truecrypt, but you can also put the truecrypt software on the USB stick and run it without having to install it. See "traveller mode"

---

