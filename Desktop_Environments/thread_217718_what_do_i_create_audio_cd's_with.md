---
title: "what do i create audio cd's with?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by randell6564 on 2006-07-17
Hello!

I have AcidRip, Sound Juicer, and Ripperx, but I just want to create a music cd from music files already on my HD.

Dont need to extract, rip... just want to burn.  what can I use?

It needs to be an application that can burn a cd that will play back in your everyday cd players... car stereo, home stereo etc...

Thanks!

---

### Post by philippe_carlo on 2006-07-17
GnomeBaker
K3B
...

---

### Post by christhemonkey on 2006-07-17
Serpentine?
The AudioCD creator preinstalled...

---

### Post by randell6564 on 2006-07-17
> **philippe_carlo said:**
> GnomeBaker
K3B
...

OK!  Ill give it a shot!  Is it a command line application or gui?

Thanks!

---

### Post by randell6564 on 2006-07-17
> **christhemonkey said:**
> Serpentine?
The AudioCD creator preinstalled...

Thats it!  I goofed and UNinstalled it after installing ubuntu. I forgot the name.

Thanks!

---

### Post by asplode on 2006-07-17
I was playing around with the different audio cd creator programs and I'm pleased to find that Serpentine can even use MPC files, and you couldn't ask for a cleaner or simpler interface.  Its addictive.

---

### Post by philippe_carlo on 2006-07-17
K3B has one very cool feature. It uses fingerprinting from musicbrainz to guess titles. Otherwise, very good andintuitive interface. Slight drawback: it comes with the kde-libs.

---

### Post by randell6564 on 2006-07-17
> **asplode said:**
> I was playing around with the different audio cd creator programs and I'm pleased to find that Serpentine can even use MPC files, and you couldn't ask for a cleaner or simpler interface.  Its addictive.


Yeah, I like that, but... my problem now is that burning cd's useing Nero in Windoze works on your everyday cd players eg; car stereo, home stereo.

But cd's that are burned useing serpentine will not play back in my car or house!

How do you configure serpentine?  The only options that I get are, Maximum writing speed, 2 seconds between tracks and eject disk after write.

Thanks!

---

### Post by asplode on 2006-07-17
Really?  Thats so odd, because I've used CDs burned in Serpentine at CD players in my car, at home, at work in multiple DVD/CD and home theater systems (I work in an electronics store) with no problems... 

> **randell6564 said:**
> Yeah, I like that, but... my problem now is that burning cd's useing Nero in Windoze works on your everyday cd players eg; car stereo, home stereo.

But cd's that are burned useing serpentine will not play back in my car or house!

How do you configure serpentine?  The only options that I get are, Maximum writing speed, 2 seconds between tracks and eject disk after write.

Thanks!

---

### Post by asplode on 2006-07-17
Come to think of it, you might want to [download the latest version of serpentine here]("http://download.berlios.de/serpentine/serpentine-0.7.tar.gz"), unpack it, and cd into the directory for a very quick compile with:
```
./configure
make
sudo make install
```

and see if that helps it out any

---

### Post by randell6564 on 2006-07-17
> **asplode said:**
> Come to think of it, you might want to [download the latest version of serpentine here]("http://download.berlios.de/serpentine/serpentine-0.7.tar.gz"), unpack it, and cd into the directory for a very quick compile with:
```
./configure
make
sudo make install
```

and see if that helps it out any

I'll give it a shot.  Thanks My friend!

---

### Post by randell6564 on 2006-07-18
Hi!

For some reason,  the second cd that i burned worked!

So now I can trust that Serpentine will copy music that is playable!

Thanks to Everyone!

---

