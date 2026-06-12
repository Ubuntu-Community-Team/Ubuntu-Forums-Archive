---
title: "Jaunty Low Sound"
date: 2009-05-24
forum: General Help
---

### Post by hacker_at_linux on 2009-05-24
I have just installed jaunty but I if I turn on a movie the sound is so less that I am hardly able to hear it. Even I installed VLC and made the volume 400% bt still it is so less that I cn't even hear what is been said in the movie.

Is there a prob wid my ALSA or it is a codex prob !!!!!!!!

Please help me

---

### Post by fooman on 2009-05-25
right-click on the volume/speaker icon in the top panel...choose "open volume control"

when it opens,  check that all the sliders are not muted and are turned up to max.

hope that helps.

---

### Post by hacker_at_linux on 2009-05-25
already tried no result
It think it shd b smthing from alsa

---

### Post by fooman on 2009-05-25
you could also try the gnome-alsamixer....it has many more volume sliders.  perhaps one of them is not turned up.

open a terminal and type or copy/paste:

```
sudo apt-get install gnome-alsamixer
```after it installs,  find it in applications > sound & video > gnome alsamixer

check the sliders there.

---

### Post by hacker_at_linux on 2009-05-25
No man It din't worked for me

Any other Alsa Tweak

---

### Post by fillintheblanks on 2009-05-25
just trial and error.. goto Volume Control > Preferences and check all different channels many of them are hidden, I have Jaunty with Audigy 2 and volume is just fine

---

### Post by hacker_at_linux on 2009-05-25
Man Even Tried that nothing happens

---

### Post by kthari85 on 2009-05-28
Yes, me too facing the similar issue . I tried all drivers, but none helped. Anyone who have succeeded ?
The volume is there, but very low . Also watching video in full screen logs out users :( .

---

### Post by Altay_H on 2009-05-28
Out of curiosity, is this problem Jaunty-specific? I mean, was the sound louder in Intrepid than it is in Jaunty? If not, we're having the same problem in this thread: [http://ubuntuforums.org/showthread.php?t=1154512](http://ubuntuforums.org/showthread.php?t=1154512)

---

### Post by CLoss on 2009-05-28
Same here, i think it must be ubuntu software, as its less then half what i get in windows,
Im sorry to say it, but windows is better at sound levels.
yes i just said "windows is better" lol

---

### Post by hacker_at_linux on 2009-05-29
I think its the new architecture on ALSA as I have even replaced the alsa-base conf file with all the specifications of intrepid but still nothing is happning and sound is really less

---

### Post by paradigm2 on 2009-05-29
Check out this post:

[http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html](http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html)

Do that to install a newer pulseaudio and alsa.  If that does not work, then perhaps try deleting ~/.pulse and rebooting.

If no luck still, you might consider upgrading to the unofficial 2.6.30rc:

[https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

There have been fixes to various drivers.

But perhaps before you do this, you might tell us what hardware you have by doing 'lspci' at the terminal.

---

### Post by hacker_at_linux on 2009-05-31
My hardware config is
```
ashmeet@bunker:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by hacker_at_linux on 2009-05-31
I think I found out the problem but I am unable to solve it
I am posting a screenshot of ALSA Mixer which has my Headphone volume to none. but when I try to increase it nothing happens it stays at 0. So I think this is the problem. But is any one can tell ho to resolve it?????
[IMG]http://www.newtrojansblog.com/S.png[/IMG]

---

### Post by matemargo on 2009-06-03
Thanks **fooman** for your suggestion. After installing gnome-alsamixer I've ajusted the levels and everthing worked fine.

---

### Post by CanadianLinux on 2009-06-23
Bump.

Im having the same issue, volume seems weak. I have the same headphone volume at 0 in alsamixer as hacker_at_linux. (tried all the things listed in the forums so far)

---

### Post by kakyoism on 2009-07-24
me too, tried everything above, none works!

---

### Post by kakyoism on 2009-07-25
My problem solved.

My laptop is a HP dv-3,

This one did the trick. 

[http://david.shermandavis.org/blogs/2009/apr/05/hp-dv3-no-sound-ubuntu-904]("http://david.shermandavis.org/blogs/2009/apr/05/hp-dv3-no-sound-ubuntu-904")

---

### Post by wobin77 on 2009-09-28
well, everything worked fine for me. Untill yesterday i wanted to give my WUSB54G another go, but the same while closing down. Hangs on 'shutting down bluetooth....'. After reboot (hard reboot) no sound. Now installed the ALSA mixer ```
sudo apt-get install gnome-alsamixer
```, turned it all up. And no problem anymore! 
Just to inform you guys...

---

