---
title: "Can not log in (blank screen) :confused:"
date: 2013-10-07
forum: Desktop Environments
---

### Post by Brian_Daniels on 2013-10-07
Hello,

Recently I installed 13.04 alongside OS X Snow Leopard on my Macbook. Somehow I accidentally changed the display settings (I think by changing to a proprietary driver) to where I can no longer log in. Whatever it may have been, it's needless to say that I can not use Ubuntu. I'm posting this off of my OS X partition.

Upon running into my problem, I researched and whatnot, and decided to try logging into a recovery root terminal with networking enabled. after
```
apt-get install gdm
dpkg-reconfigure gdm
```
i selected gdm, rebooted, and it worked!

Well, hilariously enough, I made the same stupid mistake a 2nd time! Don't ask why, but I did. Keep in mind however that this is my hypothesis: it could have been something different, just what my assumption is. Anyway - back to our CLI!!
```
apt-get install kdm ; dpkg-reconfigure kdm
```

Still no luck, so we proceed:
```
apt-get install slim
```

Upon selecting my new display manager, still no love! One can tell  that we are getting to drastic procedures upon the installation of slim. It does not work either, and now if i try to swap to lightdm, gdm, or kdm by using ```
dpkg-reconfigure [display manager]
``` it doesn't do anything. My guess is that all of the settings for each of these (guessing in a .conf?) are fubarred to a max due to my mess up. So, i try this -
```
apt-get remove --purge slim lightdm gdm kdm ; apt-get autoremove ; apt-get update && shutdown -r now 
```

Well, this solved my problem sort-of. After the splash screen (which, in fact, is now ubuntu studio LOL) i am presented with a terminal! So this confirmed (temporarily at least) that I have removed all instances of all display managers. Having this mindset I decided to install the one that came with the distro:
```
sudo apt-get install lightdm
su
dpkg-reconfigure lightdm
shutdown -r now
```

I took notice whenever entering the dpkg command that there was no output afterwards like there was upon initially configuring the other display managers. After rebooting I was presented with the silly splash screen yet again, only to find my same problem with it's passing - a black screen, no backlight, and no keyboard.

So now I can only think that the settings for the display managers remain intact inside of a configuration files, even when you have completely deleted all available files. All that are available, at least, as far as the aptitude program goes.

So now, to return to Ubuntu with a functional display manager, either it be lightdm or gdm or kdm or slim or ratpoison or xcfe or whatever,
[I][SIZE=6]WHAT IN THE WORLD DO I DO NOW? :|
[SIZE=1]

[/SIZE][/SIZE][/I][SIZE=2]Thanks in advance,
Beej.

P.S. for those of you that might find it interesting, I have a previous UbuntuForums account. search "owners4life5" for any previous posts and the like. If any of you might also know how to merge accounts, any further information would be greatly appreciated. I never had an Ubuntu One account because I had no need for one, but I had to create a new account with the same email due to the new login.[/SIZE][I][SIZE=6]
[/SIZE][/I]

---

### Post by QIII on 2013-10-07
Hello!  Please start a thread in the Resolution Centre and the Admins will help you with the username issue.

---

