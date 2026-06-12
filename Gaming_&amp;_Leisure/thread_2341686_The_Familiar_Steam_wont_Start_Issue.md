---
title: "The Familiar Steam wont Start Issue"
date: 2016-10-30
forum: Gaming &amp; Leisure
---

### Post by Jason_Hunter on 2016-10-30
I get this trying to run steam on 16.10. 

I've cleaned out my .steam directory (removed it) and reinstalled

I was able to solve it before with a preload, but it doesn't seem to work anymore. I find numerous threads on it, but nothing seems to work. 

Why is this even an issue? I remember I had the same issue on 16.04.

Running Steam on ubuntu 16.10 64-bit
STEAM_RUNTIME is enabled automatically
/bin/bash: /home/b0ef/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
awk: /home/b0ef/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.7)
Installing breakpad exception handler for appid(steam)/version(1476379980)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

---

### Post by Koobelakahn on 2016-11-02
I just actually resolved this last night, this is the thread that helped me solve it

[http://askubuntu.com/questions/784141/steam-wont-start-on-ubuntu-gnome-16-04](http://askubuntu.com/questions/784141/steam-wont-start-on-ubuntu-gnome-16-04)

Posted below is the answer copy-pasted from the site.

[COLOR=#111111][FONT=Ubuntu]You need not download Steam installer as it is already present in official Ubuntu repository. Do the following:
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]1. Remove Steam, fix broken dependencies, update installed packages[/FONT][/COLOR]
```

sudo su
apt remove --purge steam
apt autoremove
apt -f install
apt update
apt upgrade

```
[COLOR=#111111][FONT=Ubuntu]2.1 Option 1: Install Aptitude:
[/FONT][/COLOR]```

apt install aptitude
aptitude install steam

```

[COLOR=#111111][FONT=Ubuntu]OR

2.2 Option 2: install Synaptic:
[/FONT][/COLOR]```

apt install synaptic
synaptic

```
[COLOR=#111111][FONT=Ubuntu]Synaptic pop up box appears. On search panel type steam. A number of apps appear in list. one of them is steam. click on the box immediate to it's left. It will ask for confirmation to install dependencies. Click yes. Click apply. After it has finished close the window.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]3. If all fails remove libstdc++[/FONT][/COLOR]
```

cd ~/.local/share/Steam/ubuntu12_32/steam-runtime/
rm \
  amd64/installed/libstdc++6-4.6-pic_4.6.3-1ubuntu5+srt4_amd64 \
  amd64/installed/libstdc++6-4.6-pic_4.6.3-1ubuntu5+srt4_amd64.md5 \
  amd64/installed/libstdc++6_4.8.1-2ubuntu1~12.04+steamrt2+srt1_amd64 \
  amd64/installed/libstdc++6_4.8.1-2ubuntu1~12.04+steamrt2+srt1_amd64.md5 \
  amd64/usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++_pic.a \
  amd64/usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++_pic.map \
  amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6 \
  amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.18 \
  amd64/usr/share/doc/libstdc++6 \
  amd64/usr/share/doc/libstdc++6-4.6-pic \
  i386/installed/libstdc++6-4.6-pic_4.6.3-1ubuntu5+srt4_i386 \
  i386/installed/libstdc++6-4.6-pic_4.6.3-1ubuntu5+srt4_i386.md5 \
  i386/installed/libstdc++6_4.8.1-2ubuntu1~12.04+steamrt2+srt1_i386 \
  i386/installed/libstdc++6_4.8.1-2ubuntu1~12.04+steamrt2+srt1_i386.md5 \
  i386/usr/lib/gcc/i686-linux-gnu/4.6/libstdc++_pic.a \
  i386/usr/lib/gcc/i686-linux-gnu/4.6/libstdc++_pic.map \
  i386/usr/lib/i386-linux-gnu/libstdc++.so.6 \
  i386/usr/lib/i386-linux-gnu/libstdc++.so.6.0.18 \
  i386/usr/share/doc/libstdc++6 \
  i386/usr/share/doc/libstdc++6-4.6-pic \
  ~/.local/share/Steam/ubuntu12_32/steam-runtime.old/i386/usr/share/doc/libstdc++6

```
[COLOR=#111111][FONT=Ubuntu]4. Remove libgcc_s
[/FONT][/COLOR]```

cd ~/.local/share/Steam/ubuntu12_32/steam-runtime/
rm \
  amd64/lib/x86_64-linux-gnu/libgcc_s.so.1 \
  i386/lib/i386-linux-gnu/libgcc_s.so.1

```
[COLOR=#111111][FONT=Ubuntu]5. Also
[/FONT][/COLOR]```

 rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libxcb.so.1

```
[COLOR=#111111][FONT=Ubuntu]6. Then repeat either of the above methods

Basically, the steps involving removal of the corrupt steam and synaptic are the ones that worked for me.[/FONT][/COLOR]

---

### Post by Jason_Hunter on 2016-11-02
Hi and thank you for taking the time to write this and this looks like what I've done before and it'll probably work. 

, but I don't understand why we have to go through this?

Everybody who wants steam has to do this?

It's been like this since 16.04

There is no official bug on this and nobody give a flying f?

I find it so hard to understand why I have to go through this ordeal and who is the person responsible?;)

---

### Post by oldrocker99 on 2016-11-02
> **Jason_Hunter said:**
> Hi and thank you for taking the time to write this and this looks like what I've done before and it'll probably work. 

, but I don't understand why we have to go through this?

Everybody who wants steam has to do this?

It's been like this since 16.04

There is no official bug on this and nobody give a flying f?

I find it so hard to understand why I have to go through this ordeal and who is the person responsible?;)

The top sticky on this gaming forum specifically states to use the Steam file from the repositories, **not** the installer from the Steam website. The ordeal wouldn't have had to be gone through that way.

---

### Post by Koobelakahn on 2016-11-02
> **oldrocker99 said:**
> The top sticky on this gaming forum specifically states to use the Steam file from the repositories, **not** the installer from the Steam website. The ordeal wouldn't have had to be gone through that way.


This is true. The website has the downloadable packages because of other distributions.
As much as we may like to think sometimes, Ubuntu is NOT the only distribution of linux out there. :p

---

### Post by MelloNello on 2016-11-05
Thank you so much!  I'd practically given up hope of ever solving this, having tried a number of solutions on different threads.  It may be worth bearing in mind for other folks, what you said at the bottom, i.e. you need to repeat either of the above methods.  Good work, 
Koobelakahn!

---

