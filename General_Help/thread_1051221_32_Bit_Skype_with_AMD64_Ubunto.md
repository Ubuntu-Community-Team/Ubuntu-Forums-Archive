---
title: "32 Bit Skype with AMD64 Ubunto"
date: 2009-01-26
forum: General Help
---

### Post by california-ken on 2009-01-26
While wandering through tech support sites for Ubuntu I seem to remember that there is a way of installing/running the 32 bit Ubuntu version of Skype under Ubuntu Server AMD64.  I can't recall where I say the article.

Is this true and, if so, how can I do it?

Thanks.

---

### Post by nikgare on 2009-01-26
why don't you just install the 64bit version of skype?

---

### Post by california-ken on 2009-01-27
The Skype site offers no Linux 64 bit version.

---

### Post by milesinnz on 2009-01-28
[http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

---

### Post by Crafty Kisses on 2009-01-28
I'm pretty sure Skype does offer a 64-bit version, try running this command, just copy and paste and see if that does anything for you:
```
sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb http://www.skype.com/go/getskype-linux-ubuntu-amd64; sudo dpkg -i skype-install.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p libqtcore4 libqtgui4 bluez-alsa
```

---

### Post by halovivek on 2009-01-28
1. Download 32bit version of Skype from [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)
2. Download 32bit version of libqt from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
3. Install Skype

sudo dpkg --force-architecture -i < give the latest downloaded skype file>


4. Install 32bit libraries and linux32

sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6 linux32

5. Install 32bit libqt

sudo dpkg --force-architecture -i libqt3-mt_3.3.6-1ubuntu6.1_i386.deb

6. (Optional) Check if skype still miss libraries

ldd /usr/bin/skype

7. Run skype

linux32 skype&

---

### Post by jespdj on 2009-01-28
The easiest way to install Skype on a 64-bit system is by installing it from the [Medibuntu repository](http://medibuntu.org/).

Just follow the instructions there to enable the Medibuntu repository on your system and install it the usual way:
```
sudo apt-get install skype
```
No manual fiddling with libraries or other "magic" commands necessary. ;)

It works without any problems on my Dell XPS M1530 with 64-bit Ubuntu 8.04.

---

### Post by california-ken on 2009-01-28
Thanks to all of you.  With your help I was able to install the 32 bit version of Skype on my 64 bit Server installation.  Now that I see that there is a 64 bit ".deb" version of Skype available, I will uninstall the 32 bit and go for the 64 bit version.

Thanks again.

Ken

---

### Post by cariboo on 2009-01-28
I found that using the debs in the repositories that skype wouldn't work for me. I followed [this]("http:///ubuntuforums.org/showthread.php?t=432295&highlight=skype") howto and had things working in less than 5 minutes. Even the webcam's builtin mic worked, something I couldn't do in Windows.

Jim

---

