---
title: "Gnome-shell?"
date: 2012-02-06
forum: Desktop Environments
---

### Post by Jujo12 on 2012-02-06
Hi,
I have recently switched to Ubuntu from Windows, and I already love it. I have been using Unity for a few days, but decided to try GNOME Shell. I installed the gnome-shell package, and switched to GNOME in lightdm.
However, my interface doesn't look anything like GNOME shell. There is no sidebar, no activities menu, and it all looks a lot like the old GNOME.

I attached a screenshot, too.
I am inexperienced when it comes to linux, and probably I have got something wrong. Please, help :)

---

### Post by MG&amp;TL on 2012-02-06
Can we have your hardware specs please?

That interface is gnome-fallback, what gnome-shell launches if it detects that your computer is not up to GNOME, or would run intolerably slowly. Alternatively, you might not have installed the correct drivers for your hardware...which would result in GNOME thinking that you cannot run it...

Welcome to linux! Friendly bunch here, I'm sure you'll get along fine, you have a good attitude. :)

---

### Post by Jujo12 on 2012-02-06
Thanks :)

It is a laptop, Dell N5110. 4GB of RAM, Intel Core i5-2410M (2.3 Ghz), nVidia GeForce GT525. On Windows, it worked like a charm, never a single performance problem.
How am I able to check my drivers installed?

EDIT: I just checked in system info, under System info -> Graphics. Screenshot provided.

---

### Post by MG&amp;TL on 2012-02-06
Ahah. Okay, open the unity dash and type "additional drivers", then click the circuit-board icon. You should be able to install drivers from there, which should boost your linux experience quite a bit. Although I am just reading some bad things about that card, be careful...:L

---

### Post by Jujo12 on 2012-02-06
Several nVidia drivers available over here. I am using one of those. Still, under system info, there is "no data"

---

### Post by MG&amp;TL on 2012-02-06
Okay...now what happens if you log into gnome-shell?

---

### Post by Jujo12 on 2012-02-06
This *was* already activated. So no change, of course.
And under system info same thing too... :/

---

### Post by MG&amp;TL on 2012-02-06
Hmmm...well...I'm not very experienced with this area, but from googling your card, it would appear that it has NVIDIA's Optimus technology, which is not well-supported under linux. I'm doing some reading, but hopefully somebody more experienced should be along soonly. :)

---

### Post by Jujo12 on 2012-02-06
Well, my laptop also has Intel graphics card. I am also reading about this, but people say that Intel graphics work just fine...

---

### Post by MG&amp;TL on 2012-02-06
> **Jujo12 said:**
> Well, my laptop also has Intel graphics card. I am also reading about this, but people say that Intel graphics work just fine...

They do (running gnome-shell brilliantly here)-I have a feeling that Optimus somehow disables that though.

As a measure of 3d-capability (not sure how to do it otherwise), could you open a terminal, and paste in this:

```
/usr/lib/nux/unity_support_test -p

```

Thanks. Paste the output in [CODE] Tags.

---

### Post by Jujo12 on 2012-02-06
Damnit, I have chosen some other drivers, restarted, and now there is no interface for me. No boot screen, nothing :P

---

### Post by MG&amp;TL on 2012-02-06
Can you remember (exactly) what drivers you picked? If so, we can manually remove them....that's bad, sorry this has happened to you.

---

### Post by Jujo12 on 2012-02-06
Sorry, nope... Gonna try something I found on Google.

No problems, I'm used to experimenting a lot, and know that it is not so simple to get something right from the first try. Guess we all have to learn, right? :)

In worst case, I'm going to reinstall Ubuntu.

Will get back to you soon. And thanks :)

---

### Post by MG&amp;TL on 2012-02-06
> **Jujo12 said:**
> Sorry, nope... Gonna try something I found on Google.

No problems, I'm used to experimenting a lot, and know that it is not so simple to get something right from the first try. Guess we all have to learn, right? :)

In worst case, I'm going to reinstall Ubuntu.

Will get back to you soon. And thanks :)

Okay, if you're happy with that...here we go! :twisted:

Boot ubuntu, then as soon as you've got past BIOS, press the shift key. Select "recovery mode". Then select "drop to root shell prompt". Then type:

```
apt-get remove nvidia*
```

Unless something vital (i.e something without nvidia in it) looks like it will be removed, press y, then reboot with:

```
reboot
```

And you should have to desktop back to reinstall.

I'm not entirely sure how reliable that is though. No problem, hope you're having fun. :)

---

### Post by Jujo12 on 2012-02-06
Ok, now after rebooting, I don't even get the console (which was there before removing nvidia* :D)

Going to do a fresh ubuntu install. ;)

---

### Post by 3Miro on 2012-02-06
argh!!! a laptop with Nvidia 525, this means Optimus. Unfortunately Nvidia did not provide proper drivers for Linux with Optimus. At this point, I would do a clean reinstall and you should look carefully from now on. If anyone asks, you should specifically say that you have Optimus and read help accordingly. I think at this point, regardless of what you do, you will have some issued, but you should be able to use your system properly.

Last time I checked, it best way to deal with Optimus was to disable the Nvidia card from the BIOS and go with the Intel one, which is more than enough for Unity 3D and Gnome-shell (no need for proprietary drivers either). Nvidia is needed for Gaming and very heavy 3D stuff only.

This was the last that I read, things may have changed.

---

### Post by Jujo12 on 2012-02-07
Yes, I found that out, just a bit too late.
Never mind, I am doing a backup of all my data at the moment, and am going to do a fresh install. I have checked my BIOS for a way to disable the nVidia graphics card. However, I couldn't find any option, so I would just have to be careful.

Hopefully one day optimus support will come to Linux too :)
I do not play any heavy graphics games (I wouldn't switch to Linux if I do :P ), but am working with 3D graphics, which is much easier to work with on nVidia. However, the new Sandy Bridge GPU is also great ;)

---

### Post by kurt18947 on 2012-02-07
You know there is *some* support for Optimus, yes?  I have no first-hand experience but a search for "bumblebee" should yield some reading/watching.  That the O P doesn't reach for the PANIC button upon a setback bodes well.  Here is one of the first links that shows up:
[http://ubuntuportal.com/bumblebee-3-0-tumblewed-nvidia-optimus-gpu-switching-for-linux-has-been-released-how-to-install-bumblebee-3-0-on-ubuntu/](http://ubuntuportal.com/bumblebee-3-0-tumblewed-nvidia-optimus-gpu-switching-for-linux-has-been-released-how-to-install-bumblebee-3-0-on-ubuntu/)

---

### Post by Jujo12 on 2012-02-07
Just wanted to report that after a fresh install, and being careful for a few minutes about some things mentioned here, everything is working like a charm. Thanks!

@kurt: I have read something about it (after I crashed the system :D ). However, I would not really like to risk the whole system (again) just for experimentation. Maybe some other time I'm going to try it, and see how it works in my particular case. Anyway, thanks for the info :)

---

