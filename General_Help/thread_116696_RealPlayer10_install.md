---
title: "RealPlayer10 install"
date: 2006-01-13
forum: General Help
---

### Post by AlanQ on 2006-01-13
When run from a terminal, RealPlayer10GOLD.bin gives the following error:
> ./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

According to a post at [http://real.lithium.com/real/board/message?board.id=realplayer&message.id=1152](http://real.lithium.com/real/board/message?board.id=realplayer&message.id=1152)
> You need to install the "compat-libstdc++-33" package.
(It contains the two files, "/usr/lib/libstdc++.so.5" and "/usr/lib/libstdc++.so.5.0.7").

Aparently there is a FedoraCore4 rpm package for compat-libstdc++-33 at [http://rpm.pbone.net/index.php3/stat/4/idpl/1757971/com/compat-libstdc++-33-3.2.3-47.fc4.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1757971/com/compat-libstdc++-33-3.2.3-47.fc4.i386.rpm.html), but Ubuntu does not have rpm.

> packages.debian.org is down at the moment due to performance issues.

Does anyone know what I should put in sources.list so that I can apt-get compat-libstdc++-33 ?

Or any other ideas...?

Thanks
Alan

---

### Post by KhanArash on 2006-01-13
I have the same problem! I cant get the realplayer to be installed and run... please HEEEEEEEEELP!

---

### Post by hillbilly on 2006-01-13
Why dont you check for libstdc++ on synaptic. I think it is available through that.

---

### Post by KhanArash on 2006-01-13
but how can I install realplayer i tried with synaptic, but it gives me failstatus 1... and i downloaded the realplayer 10 and tried to install it with add aplication, it gives me the same failestatus 1...

I downoalded the rpm file, is it the file which can be installed  with ubuntu 5.10? or do i need to download the bin file?
and how can i install the bin file in ubuntu 5.10?

---

### Post by hillbilly on 2006-01-13
Hmm..i have not tried to install realplayer on linux. But i know that you can make use of an app "alien" to convert .rpm files to .deb files and then  you can install .deb files using 

> dpkg -i <package>.deb

---

### Post by healychan on 2006-01-13
The problem is that you don't have the libstdc++5 to run the installer. I believe that you can get that by "Synaptic".
Install that package and do the installation again, it should be fine then.

---

### Post by AlanQ on 2006-01-13
Looks like we've all failed to RTFM

After posting my question I found 
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b)
(don't know why the URL is so long)

What it says is:
Download the RealPlayer .deb package at
[ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.6-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.6-0.0_i386.deb)

then:
```
sudo apt-get install libstdc++5
sudo dpkg -i realplayer_10.0.6-0.0_i386.deb

```

I now have RealPlayer10.
And guess what... it works!

Now I just need to find out how to simultaneously record what I'm listening too...

Cheers
Al

---

