---
title: "What do you use to play : sega master system with sound+working fullscreen?"
date: 2008-05-31
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-05-31
Hello,
 
I tried:
-osmose
   (one cannot get full fullscreen)
-mekanix 
    no sound works
-xmess.SDL 
    too old

What have you got that works?

thank you !

---

### Post by acoustibop on 2008-05-31
Mednafen.  Make sure you use the current 0.8.8 build: 0.8.7 also emulates the SMS but the Pause button (essential for some games) is disabled there.

---

### Post by frenchn00b on 2008-06-01
> **acoustibop said:**
> Mednafen.  Make sure you use the current 0.8.8 build: 0.8.7 also emulates the SMS but the Pause button (essential for some games) is disabled there.
 
thanks 
On their site, they do not mention about master system.

Anyhow the way to install it:
```
 apt-get install libcdio-dev  libcdio6  libsndfile1-dev
```

get the source:
[http://ftp.debian.org/debian/pool/main/m/mednafen/](http://ftp.debian.org/debian/pool/main/m/mednafen/)
 
```
./configure ; make ; make install 
```
 
I just made a deb, dsc, orig, diff.gz. It works well this emulator !

---

### Post by acoustibop on 2008-06-01
The latest version there is 0.8.7-1.1, frenchn00b, not to mention that there are i386 and amd64 .debs there, so you don't have to do```
./configure ; make ; make install 
```

You'll find that with version0.8.7, as I warned you in my previous post, you'll run into trouble with games that require the use of the Pause button (such as Wonderboy III, where you have to use it to change equipment).

---

### Post by frenchn00b on 2008-06-01
> **acoustibop said:**
> The latest version there is 0.8.7-1.1, frenchn00b, not to mention that there are i386 and amd64 .debs there, so you don't have to do```
./configure ; make ; make install 
```

You'll find that with version0.8.7, as I warned you in my previous post, you'll run into trouble with games that require the use of the Pause button (such as Wonderboy III, where you have to use it to change equipment).


I dont know but as soon as I get in mind to install a new package, I always make it from the code source ... lol 
Dont know why, then make my own deb. That's certainly Linux compiling effect !
 
Actually the deb they provided was not working, they didnt compile it well at all :)  I dont understand why it is in stable. Looks that mine works better.

here is my video :
[http://rapidshare.com/files/119264413/video-sms-predator.avi.html](http://rapidshare.com/files/119264413/video-sms-predator.avi.html)

---

### Post by frenchn00b on 2008-06-01
Even with that 
[http://mednafen.sourceforge.net/documentation/#using-keys-gameboy](http://mednafen.sourceforge.net/documentation/#using-keys-gameboy)
I have troubles to alt +ctrl +1  to set keyboard since I dont have qwer... keyboard ...

let s try : 
```
setxkbmap us
```

with "Penguin Land"  ! :)

...

---

