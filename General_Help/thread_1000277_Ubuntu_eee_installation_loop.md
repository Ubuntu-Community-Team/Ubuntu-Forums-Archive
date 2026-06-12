---
title: "Ubuntu eee installation loop"
date: 2008-12-02
forum: General Help
---

### Post by jspolen on 2008-12-02
Hi maybe this is in the wrong place.

I have a problem installing Ubuntueee on my Acer eeepc 900. For some reason the installation aborts around 79 percent. It then boots the live version, only to start the installtion once more.

Downloade the latest Ubuntueee 8.04.1 and unetbootin from [http://www.ubuntu-eee.com/]("http://www.ubuntu-eee.com/") so I can boot from usb.

Does anyone know what's wrong?

---

### Post by collinp on 2008-12-02
Does it output a error when installing when the bar stops? If not, you may have to wait a while, Ubuntu can occasionally take a while to install.

---

### Post by jspolen on 2008-12-02
Nope no error, just starting over.

---

### Post by mdurham on 2008-12-02
Is there an option when booting the stick to do a media validity check? If so, try doing it. Maybe it's corrupt or not complete.
Cheers, Mike

---

### Post by jspolen on 2008-12-02
I did the validy check and found one error.

About to download another image file, hopefully it will work this time.

---

### Post by jspolen on 2008-12-03
Okay I have now downloaded a couple of different iso files, and even veryfied them with md5. But for some reason the validity check finds one error.

Is there something wrong with unetbootin when I transfer to usb?

---

### Post by cmay on 2008-12-03
i used the usb startup creator in ubuntu 8.10 to create a sub stick with eee ubuntu and it works. i cant say honest i installed it so the whole install procces from the usb stick i have yet to do. i had to return the eeepc for repair since the alt button was faling off. so i get it back in a matter off days buit i still have the usb stick waiting. maybe you could use this if you have intrepid ibex .

---

### Post by jspolen on 2008-12-03
Hmm now I finally got to a iso file that installed all the way, asked me to reboot and I did. But now after grub loads I get 

[ 10.8813129] Kernel panic - not syncing : junk in compressed archive.

---

