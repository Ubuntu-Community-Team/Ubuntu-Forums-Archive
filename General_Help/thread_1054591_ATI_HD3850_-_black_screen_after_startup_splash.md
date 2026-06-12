---
title: "ATI HD3850 - black screen after startup splash"
date: 2009-01-29
forum: General Help
---

### Post by ntbutler on 2009-01-29
Hi all.

After many problems with my nvidia graphics card, I gave up and thought I would try a radeon card.

However, now when I start ubuntu, the screen goes black (like it is in standby mode) when it should come up with the desktop (I have set it to auto-login).

I have had a look around on other posts, and I have tried these:

[LIST=1]
[*]Failsafe xorg.conf
```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```
This will give me the screen back, but next time i startup the computer, I get the same problem, and sometimes I can't even get to the tty screen at that point.
[*]fglrx driver
I have tried the steps on [http://ubuntuforums.org/showthread.php?t=967691]("http://ubuntuforums.org/showthread.php?t=967691"). The fglrx stuff didn't help at all, but as above, using the xorg failsafe helped a bit.
[*]installing radeonhd driver
I have looked around and it has been suggested to install the radeonhd driver. I tried it (intsructions [here]("http://www.phoronix.com/scan.php?page=article&item=843&num=1")), and i get to the install stage, and this is what it gives me:
> nathan@nathan-desktop:~/xf86-video-radeonhd$ cd xf86-video-radeonhd/; ./autogen.sh --prefix=/usr/; make; sudo make install
bash: cd: xf86-video-radeonhd/: No such file or directory
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
configure.ac:342: error: possibly undefined macro: XORG_MANPAGE_SECTIONS
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:344: error: possibly undefined macro: XORG_RELEASE_VERSION
autoreconf: /usr/bin/autoconf failed with exit status: 1
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

[/LIST]

Does anyone have any ideas on what I should try?

I should mention that I tried installing the ATI restricted driver when I did have the screen, but it didn't download anything like it did when I installed the nvidia drivers for my old card, and i just got the black screen after reboot. Also, I deactivated the nvidia driver before trying the new card and also removed all nvidia stuff ( i think).

Thanks

---

### Post by ntbutler on 2009-01-30
Just thinking, maybe the radeonhd driver is the way, but could someone point me in the right direction for how to install it properly (as you can see from above, I can't get it to the make install stage, I am a little in-experienced at makefiles, so my troubleshooting is not great...)

---

### Post by ntbutler on 2009-01-30
hello?

---

### Post by MadnessRed on 2009-06-01
> **ntbutler said:**
> hello?

if you aer trying to do what i think you are, I used this guide
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

or for other ubuntu versions

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

