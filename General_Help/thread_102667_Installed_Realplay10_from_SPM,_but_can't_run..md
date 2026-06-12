---
title: "Installed Realplay10 from SPM, but can't run."
date: 2005-12-12
forum: General Help
---

### Post by Dislimit on 2005-12-12
Installed Realplay10 from SPM (Synaptic Package Manager), but can't run correctly.
Tried to click the link generated already but nothing happened.
Run in command line:
$realplay
/usr/bin/realplay: line 75: 10939 Segmentation fault      $REALPLAYBIN "$@"

Can't play real media with any other players even after I have installed w32codecs.

Why?

---

### Post by Dislimit on 2005-12-13
Nobody knows how to deal with realplayer10?

---

### Post by linbetwin on 2005-12-13
Download [Realplayer 10 GOLD]("http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner") for Linux to your Desktop.
Open a terminal and write:
```
cd Desktop
```
then
```
chmod a+x RealPlayer10GOLD.bin
```
then
```
./RealPlayer10GOLD.bin
```

If you receive error messages, post them here.

---

### Post by Dislimit on 2005-12-13
Install succeeded.
When running ./realplay in the installed path:
./realplay: line 75:  9906 Segmentation fault      $REALPLAYBIN "$@"

---

### Post by kaamos on 2005-12-13
This worked for me: [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer)

---

### Post by Dislimit on 2005-12-13
Thank you both.
kaamos, though I have not tried ur way, I have installed realplayer 10.0.6 with SPM. I think basicly it's the same. And all the ways can install realplayer successfully, but result in Segmentation fault when runnning. That's the problem.

I'm wondering the reason...

---

### Post by linbetwin on 2005-12-13
Are you sure the install was successful? Sometimes that message is deceiving. Did you follow the prompts during the installation? Did it take suspiciously little time? Do you have RealPlayer in Applications -> Sound and Video menu?

---

### Post by Randy Sparks on 2005-12-13
I would remove the RealPlayer package via Synaptic and then follow the instructions at: 

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer)

The above instructions worked fine for me. However, if you follow the instructions there to configure Totem to use the Win32 codec pack, there's no need to install RealPlayer because Real movies and audio will play in Totem.

---

### Post by Dislimit on 2005-12-14
[QUOTE=linbetwin]Are you sure the install was successful? Sometimes that message is deceiving. Did you follow the prompts during the installation? Did it take suspiciously little time? Do you have RealPlayer in Applications -> Sound and Video menu?[/QUOTE]

What message is deceiving? Yes, I followed the prompts, the installation completed very fast and I can see the RealPlayer icon in the menu if I use SPM to install it. For the .bin installation, I forgot if there is such an icon there.

Btw, do u guys think that I should uninstall w32codecs in order to make RealPlayer work? (just guessing)

---

### Post by Dislimit on 2005-12-14
[QUOTE=Randy Sparks]I would remove the RealPlayer package via Synaptic and then follow the instructions at: 

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer)

The above instructions worked fine for me. However, if you follow the instructions there to configure Totem to use the Win32 codec pack, there's no need to install RealPlayer because Real movies and audio will play in Totem.[/QUOTE]

I have followed the instructions and installed w32codecs yesterday. But neither VLC nor mplayer can play .rm or .rmvb in my laptop.

Btw, the instructions just tell us to install w32codecs, no more configuration, right?

---

