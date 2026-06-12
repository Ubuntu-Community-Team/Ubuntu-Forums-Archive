---
title: "SNES9X no longer after upgrade to 13.10"
date: 2013-10-25
forum: Emulators
---

### Post by mcse2000ca on 2013-10-25
[COLOR=#000000]It was working fine in 13.04 but after the upgrade i can open it but after i go into preferences and press ok or try choosing a ROM it will go to a greyish black 

screen and can only close it by right clicking and forcing to quit the program. [/COLOR][COLOR=#000000]I have downloaded zsnes and it works fine just a personal preference towards snes9x.


[/COLOR]

---

### Post by LubLearner on 2013-10-26
Hi.

Have you try uninstalling it completely and reinstalling it yet? I mean it would be better to delete the settings files before reinstalling.

I am not an expert, I have just started using Lubuntu and I have not used Snes9x.

---

### Post by mcse2000ca on 2013-10-27
Ran a purge and even deleted the hidden settings folder in my home folder.

---

### Post by BigSilly on 2013-10-28
If you hang on a short while, the developer Brandon Wright (Bearoso) usually [updates his PPA]("https://launchpad.net/~bearoso/+archive/ppa") to the newest version shortly after release. :)

---

### Post by mcse2000ca on 2013-10-29
Thanks Big will hold on, this will teach me for upgrading so soon after a release hehe.

---

### Post by nll on 2013-11-02
I have the same problem. First I tried running the raring version from the Bearoso PPA, then I tried compiling the GTK3 version, then the GTK2 version, and then the command-line version. The only one which worked was the command-line one, but unbelievably it lacks some options in relation to the GTK version (like fullscreen). If you wanna try, there's a guide here: [http://maxolasersquad.blogspot.com.br/2013/09/compiling-snes9x-on-ubuntu.html](http://maxolasersquad.blogspot.com.br/2013/09/compiling-snes9x-on-ubuntu.html)

---

### Post by nll on 2013-11-02
You could also install [bsnes]("https://apps.ubuntu.com/cat/applications/bsnes/"), but you'll need to use bsnes-purify on your roms so that it recognizes them. I don't like this one very much though, and it's very computer-demanding. If you do, remember there's three optimizations of it you can try: bsnes-accuracy, bsnes-compatibility, and bsnes-performance

---

### Post by BigSilly on 2013-11-02
Have to say I am surprised to read that the Raring package doesn't work on Saucy. I would have hoped by now the PPA would have been updated, but sadly it hasn't. Hopefully Bearoso is OK and still active, and it's just a matter of time.

What is the terminal output of the Raring package on Saucy? I would look myself but I'm still on Raring for the time being.

---

### Post by BigSilly on 2013-11-03
Hmmm...installed Cinnamon stable today ([2.0.6 from here]("https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable")), and the Raring package for this works. Again, I'm using 64 bit Saucy now. Very confused that Snes9X-gtk works on Cinnamon and not Unity, but it could be worth knowing for some of you.

---

### Post by BigSilly on 2013-11-03
Aaaand it's completely crashed on me! Having to remove Cinnamon now, but Snes9x did work on it for the short while Cinnamon was running for me. May be worth looking into Mint 16 later.

---

### Post by nll on 2013-11-03
> **BigSilly said:**
> What is the terminal output of the Raring package on Saucy? I would look myself but I'm still on Raring for the time being.

That's the weirdest thing, it doesn't give any error messages.

Since the command-line works, I'm guessing it should be some incompatibility with GTK 3.8. Is Cinnamon 2.0 based on GTK 3.10? (Wait, it probably isn't or else you wouldn't be able to install it on Saucy without massive breakage.)

---

### Post by nll on 2013-11-03
For anyone else interested in BSNES and struggling to understand the bsnes-purify instructions, you gotta do this:

1- Create a directory called *bsnes* in your home folder;
2- Create inside the *bsnes* directory another directory called *purified*;
3- Extract your roms and copy your .smc files into the *bsnes* directory¹;
4- Open a terminal and type *bsnes-purify output bsnes bsnes/purified*.
5- That's it! Now you have got the .sfc files/folders and you just need to point BSNES to the *purified* directory in *Load > Super Famicon*.
¹[SIZE=1]You don't necessarily need to extract your zipped roms, but it won't work if the .zip package have other files inside in addition to the .smc, like a readme or whatever.[/SIZE]

These are very simple instructions, but it took me a bit to figure that out so I just thought it might save someone some time. The same thing works for Higan, which is how the last versions of BSNES are called (it's not in the Ubuntu repositories, you need a PPA or to compile it).

---

### Post by BigSilly on 2013-11-03
> **nll said:**
> That's the weirdest thing, it doesn't give any error messages.

Since the command-line works, I'm guessing it should be some incompatibility with GTK 3.8. Is Cinnamon 2.0 based on GTK 3.10? (Wait, it probably isn't or else you wouldn't be able to install it on Saucy without massive breakage.)

Cinnamon 2.0 is now a complete DE and doesn't rely on Gnome at all apparently. However, it did completely nork up on me and I had to remove it. Hopefully this won't happen when Mint 16 makes an appearance.

> **nll said:**
> For anyone else interested in BSNES and struggling to understand the bsnes-purify instructions, you gotta do this:

1- Create a directory called *bsnes* in your home folder;
2- Create inside the *bsnes* directory another directory called *purified*;
3- Extract your roms and copy your .smc files into the *bsnes* directory¹;
4- Open a terminal and type *bsnes-purify output bsnes bsnes/purified*.
5- That's it! Now you have got the .sfc files/folders and you just need to point BSNES to the *purified* directory in *Load > Super Famicon*.
¹[SIZE=1]You don't necessarily need to extract your zipped roms, but it won't work if the .zip package have other files inside in addition to the .smc, like a readme or whatever.[/SIZE]

These are very simple instructions, but it took me a bit to figure that out so I just thought it might save someone some time. The same thing works for Higan, which is how the last versions of BSNES are called (it's not in the Ubuntu repositories, you need a PPA or to compile it).

Just curious, but is BSNES better than Snes9x-gtk? 

OK, to continue my distro hopping today I decided to try out Kubuntu 13.10 64 bit. Still not as good as previous releases imho, with a lot of crashes. Really sad. I've managed to get it set up and mostly stable, but it doesn't feel as convincing as it should, and I'm waiting for my next crash.

But I digress: the Raring Snes9x-gtk package works perfectly on it. No problems at all. Go figure that eh? A GTK package that works better on KDE than it does on a Gnome-based distro! :D  It must be a Unity thing.

---

### Post by nll on 2013-11-03
> **BigSilly said:**
> Just curious, but is BSNES better than Snes9x-gtk?

Well, people claim it's way more accurate and emulates more games. It's tons more resource-intensive for sure. I honestly didn't notice much difference in games, but I didn't make a side-by-side comparison. What I absolutely adore about SNES9X is the easy setup of Blargg's gorgeous NTSC filter. I got a similar effect in BSNES with *Video Filter > Scanline-Light + Video Shader > Blur*, so I'm happy for now. I'm not gaming that much these days anyway.

> **BigSilly said:**
>  Go figure that eh? A GTK package that works better on KDE than it does on a Gnome-based distro! :D  It must be a Unity thing.

Oh, the devillish imps of the perverse!
It's officially a Unity thing then. Damn!

---

### Post by mcse2000ca on 2013-11-05
Oh well will wait then not a big fan of KDE they have just messed too much of a good thing up in that manager lately and the stability has never been on par with gnome.

---

### Post by mcse2000ca on 2013-11-15
Anyone hear any news from Brandon about updating his client for the new Unity?

---

### Post by techzilla2 on 2013-11-21
I linked to my ppa which has my new snes9x-gtk package, check the other thread for the posts [http://ubuntuforums.org/showthread.php?t=2182196&highlight=snes9x](http://ubuntuforums.org/showthread.php?t=2182196&highlight=snes9x).

Should we have a mod combine these two?  As I just noticed I got to this one through google, and that means many people won't see the newly working package.

---

### Post by cdoublejj on 2013-11-24
well this is an interesting thread. i was just looking for the snes9x the other day i could not find in synaptic package manager. am i doing something wrong?

EDIT: i'm mistaken, i have it installed but, it does crash when you try to load a rom. i'm using LUbuntu 13.10, which does not use unity.

---

### Post by mcse2000ca on 2013-11-25
I would try techzillas ppa if you are not using unity cdoublejj it worked in Kubuntu for me ( it was Kubuntu that crashed lol so got rid of it hehe)

---

### Post by cdoublejj on 2013-11-26
how long do you think that PPA will last? will i need to eventually switch it back? does that even make sense? why does ubuntu have to keep old stuff in the repositories.

---

### Post by BigSilly on 2013-12-28
Just to let you all know, Brandon Wright (Bearoso) updated his PPA with a new release of SNES9X-gtk for both Saucy *and* Trusty! [Get it here]("https://launchpad.net/~bearoso/+archive/ppa")! :)

---

### Post by cdoublejj on 2014-01-13
so i added the ppa and updated it didnt make a difference. you don't have to use bios to play roms or any thing do you?

---

### Post by cdoublejj on 2014-06-11
Has anyone get this working on 14.04 LTS?

---

### Post by adec2 on 2014-06-11
Works fine for me in Kubuntu 14.04 64bit. try running it from command line and note any errors it shows

---

### Post by michael-piziak on 2015-01-18
> **cdoublejj said:**
> Has anyone get this working on 14.04 LTS?

I can get Snes9x to work in Ubuntu 12.04 lts.  I once updated my system to 14.04 lts and could not get Snes9x to work.  That's one of the few reasons I went back to 12.04 lts.

Furthermore, I installed Ubuntu 14.04 lts on my sister's computer and Snes9x won't work on her system.

So I'm confident that there is something about 14.04 lts that gives some or many users a problem with Snes9x.

---

