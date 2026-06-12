---
title: "Zelda Classic for Linux not working in Precise?"
date: 2012-05-20
forum: Gaming &amp; Leisure
---

### Post by teddybairs1 on 2012-05-20
I was just wondering if anyone else is having this problem. I go to launch Zelda Classic for Linux, build 1402, and it's refusing to launch. When I try launching it in the terminal, I get this:

./zelda-l: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory

When I try launching zlaunch, something similar:

./zlaunch-l: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

According to Synaptic, the libraries are all there. Near as I can tell from entering the error in Google, it might be because 12.04 is running Wayland instead of X? This is the first time it's refused to launch for me under either Windows or Linux and I've played it under both for several years now, although I haven't run it under Linux for at least a year.

Any ideas or solutions?

BTW, it would be nice if someone would take it up and put it in the repos. I'm not a coder, otherwise I would make a go of trying to get it there.

---

### Post by BigSilly on 2012-05-20
I'd never heard of this, but a quick look on their [downloads page]("http://www.allegro.cc/depot/ZeldaClassic/") shows the last update was 2007. I can only imagine that since then Linux has changed quite a bit and the libraries this used to run are no longer compatible.

However, are you on 64 bit? Could this be a case for ia32-libs?

EDIT: Hmmm it runs on mine but I get no sound. I can play the game fine though.

---

### Post by teddybairs1 on 2012-05-20
That's cool. The Linux version isn't on their downloads page. They don't list anything but what they consider releases on their downloads page (and the Linux build has always been considered a beta), so you have to do a Google hunt for it. I know I've used it on Ubuntu after 2007, and I'm pretty sure this build is at least since '09. From what I've read it's supposed to be as stable as an RC, and other sites said it was supposed to run on 12.04.

I googled the error and got something related to another game that suggested it had something to do with wayland as opposed to X.

Oh, I'm using x64 BTW.

---

### Post by teddybairs1 on 2012-05-20
@BigSilly, what build are you using?

---

### Post by BigSilly on 2012-05-20
The file says zc2116b16 if that means anything to you. It's on the downloads page I linked to above - the tar.gz file.

I'm pretty confident it's nothing to do with Wayland. Ubuntu doesn't use that yet, and probably won't for some time.

---

### Post by teddybairs1 on 2012-05-20
Ok, so that was the first build I tried. I then tried looking for a more recent build which is when I came across the other build. This one is giving me the error:

./zelda-l: error while loading shared libraries: libXpm.so.4: cannot open shared object file: No such file or directory

I'm still not sure why it's doing it if Ubuntu is still using X and yours is working fine.

---

### Post by teddybairs1 on 2012-05-20
Ok, I just googled the error message and it took me to a ZC forum with someone who's having the same problem. He installed the 32-bit versions of the libraries and it worked fine. This will be my next challenge.

---

### Post by teddybairs1 on 2012-05-20
Ok, I'm in the process of installing the ia32-libs transitional package (and all the dependencies) to see if that helps. I had to do some more googling though just to find out about it. Really, there should be some kind of a wiki that's easily accessible for stuff like this. I've been using Ubuntu regularly since 2006, and Linux in general via Debian and Lindows (Linspire) since 2004. I've turned my systems inside out just trying to learn more about it, breaking it, and then learning how to fix it and get stuff working. I'd like to think I'm not a noob when it comes to this stuff, but just moving from 32-bit to 64-bit makes me feel like a noob again sometimes.

---

### Post by teddybairs1 on 2012-05-20
Alright, that fixed it. It's working fine now, sound and everything. This is the 2.50 RC 3 Build I got from [http://armageddongames.net/showthread.php?94138-Zc-2.50-rc3](http://armageddongames.net/showthread.php?94138-Zc-2.50-rc3). It was last updated around the 25th of February, 2012.

---

### Post by madjr on 2012-05-21
lots of info in this blog post:

[http://www.ubuntuvibes.com/2012/02/explore-land-of-hyrule-play-zelda.html](http://www.ubuntuvibes.com/2012/02/explore-land-of-hyrule-play-zelda.html)

---

### Post by teddybairs1 on 2012-05-21
Come to think of it, that link is where I got the 1402 build from. Thanks for pointing it out again, I hadn't looked at it more closely, but there's linux links for the lost isle build which supports both Origin and Lost Isle, which are fabulous ZC games.

---

### Post by Dlambert on 2012-05-23
I had no clue this existed! Thank you.

---

