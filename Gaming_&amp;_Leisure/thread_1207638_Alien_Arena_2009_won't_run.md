---
title: "Alien Arena 2009 won't run"
date: 2009-07-08
forum: Gaming &amp; Leisure
---

### Post by LinuxFox on 2009-07-08
I decided to download this game since I wanted to look into more open source games, and I can't get it to run.  I'm using Ubuntu 8.04.

When I ran it from the terminal, it said something about not being able to find libopenal.so.1.  I tried Googling it and I keep coming up empty handed.

Can someone please help me, I'd like to actually try the game.

---

### Post by Irritant on 2009-07-08
You need to install openal, and probably ogg-vorbis.

---

### Post by LinuxFox on 2009-07-08
> **Irritant said:**
> You need to install openal, and probably ogg-vorbis.Problem is, I think it's installed.  I check Synaptic and OpenAL and Vorbis seem to be installed.  Unless there's another package I need?

---

### Post by del_diablo on 2009-07-08
libal or libopenal, maybe with dev at the end also. Just hit a much as possible and se if it works :P

---

### Post by LinuxFox on 2009-07-08
Just an update, now the terminal is telling me it "libgnutls.so.26" doesn't exist.  Synaptic says I have gnutls installed.  This is really confusing me since I have OpenAL and gnutls libs installed, at least that's what's synaptic is telling me.

Edit, while searching I came across a "ln" command that did something with libopenal.so.0 and made libopenal.so.1.  I can't seem to find it online now, and I don't know if this works.

---

### Post by Brebs on 2009-07-08
[*Recompile* alienarena](http://ubuntuforums.org/showthread.php?t=1192175) for your Ubuntu version. Then it will use the libs that you've got, rather than the libs that a different Ubuntu version has.

Uninstall the alienarena you have currently, because it's for a different Ubuntu version, and keeping it around will probably just cause confusion for you, when you try to install it again.

---

### Post by LinuxFox on 2009-07-08
> **Brebs said:**
> [*Recompile* alienarena](http://ubuntuforums.org/showthread.php?t=1192175) for your Ubuntu version. Then it will use the libs that you've got, rather than the libs that a different Ubuntu version has.

Uninstall the alienarena you have currently, because it's for a different Ubuntu version, and keeping it around will probably just cause confusion for you, when you try to install it again.Thanks for the link.  I tried the recompile instructions and tips in that topic, and I'm getting nowhere. :(

But thanks anyway.

---

### Post by ELD on 2009-07-08
> **LinuxFox said:**
> Thanks for the link.  I tried the recompile instructions and tips in that topic, and I'm getting nowhere. :(

But thanks anyway.

Well.....what went wrong? Telling us it didn't work is not helping yourself dude.

---

### Post by LinuxFox on 2009-07-08
> **ELD said:**
> Well.....what went wrong? Telling us it didn't work is not helping yourself dude.Ok, I will.  I downloaded the game from one of the mirrors listed at the Alien Arena website.  Specifically the Atomic Gamer mirror.

I tried following the instructions in the link in Brebs' post to recompile it.  After I type "make", I get an error 1 and 2.  I tried this on my external hard drive (more space, plus Cube 2 and Nexuiz play fine off it), and I tried it in my home folder, same result in both.  Here's the result I keep getting after trying to compile it.

```
cl_http.c:(.text+0x44): undefined reference to `curl_multi_init'
cl_http.c:(.text+0x52): undefined reference to `curl_easy_init'
release/client/cl_http.o: In function `CL_HttpDownloadCleanup':
cl_http.c:(.text+0x92): undefined reference to `curl_multi_remove_handle'
release/client/cl_http.o: In function `CL_ShutdownHttpDownload':
cl_http.c:(.text+0x191): undefined reference to `curl_easy_cleanup'
cl_http.c:(.text+0x1a8): undefined reference to `curl_multi_cleanup'
release/client/cl_http.o: In function `CL_HttpDownloadThink':
cl_http.c:(.text+0x1ed): undefined reference to `curl_multi_perform'
cl_http.c:(.text+0x215): undefined reference to `curl_multi_info_read'
cl_http.c:(.text+0x283): undefined reference to `curl_easy_getinfo'
release/client/cl_http.o: In function `CL_HttpDownload':
cl_http.c:(.text+0x3db): undefined reference to `curl_easy_reset'
cl_http.c:(.text+0x3f8): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x415): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x44e): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x46b): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x481): undefined reference to `curl_multi_add_handle'
collect2: ld returned 1 exit status
make[1]: *** [release/crx] Error 1
make[1]: Leaving directory `/media/disk/alienarena2009/source'
make: *** [build-release] Error 2
tailsy@tailsy-desktop:/media/disk/alienarena2009/source$
```  I hope providing this information could help.

---

### Post by Irritant on 2009-07-08
Yup, you're missing libcurl.

---

### Post by LinuxFox on 2009-07-08
> **Irritant said:**
> Yup, you're missing libcurl.When I check Synaptic, it says I have libcurl3.  Is there a different version I need to install?  I tried libcurl4-gnutls-dev, but I keep getting an error and it won't install.

---

### Post by LinuxFox on 2009-07-09
Some very good news, I installed the dependencies and recompiled it, and now the game runs.  Played a bit of it to make sure it works and it's sweet.  Thanks for the help guys. :)

Now I'm running into another problem, there's no sound when I play it.  I can still play it, but I don't see why there's no sound.

Edit: The game crashes when I click Apply in Video Options.

---

### Post by X1R1 on 2009-11-30
same error here, Try to change settings and the game drops me to a terminal and doesnt change anything, also no sound.

---

