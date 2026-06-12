---
title: "Jaunty fresh install : very long boot"
date: 2009-05-01
forum: General Help
---

### Post by djiock on 2009-05-01
Hi there ! I usually post on the french forum but noboby seem able to help me and worse, I might be the only one with this problem...

Which is ! I made a fresh install of Jaunty on my laptop, in order to get format in ext4 and I must say that my system fly, there's only this boot problem :

```
Apr 29 01:02:42 julien-laptop kernel: [   12.588024] intel8x0_measure_ac97_clock: measured 53967 usecs
Apr 29 01:02:42 julien-laptop kernel: [   12.588028] intel8x0: clocking to 48000
Apr 29 01:02:42 julien-laptop kernel: [  191.354829] lp: driver loaded but no devices found
Apr 29 01:02:42 julien-laptop kernel: [  191.415747] Adding 1461872k swap on /dev/sda1.  Priority:-1 extents:1 across:1461872k
Apr 29 01:02:42 julien-laptop kernel: [  191.947647] EXT4 FS on sda3, internal journal on sda3:8
```

As you can see It blocks for a very long time on "clocking to 48000" and that's pretty annoying.


I really hope there is a solution... And thanks in advance for it :)

---

### Post by djiock on 2009-05-04
Ah little up... I'm starting to loose hope...

Hey my /boot partition is in ext3, could that be of any influence ?

---

### Post by Bindsa on 2009-05-04
Try typing this into a terminal:

```
[COLOR="Red"]echo[/COLOR] "snd-intel8x0m" | sudo tee -a /etc/hotplug/blacklist
```

Then reboot.

---

### Post by djiock on 2009-05-04
Thanks for the reply !

I tried your command but /etc/hotplug/blacklist doesn't exist, not even /etc/hotplug...

---

### Post by Bindsa on 2009-05-04
I'm afraid I can't help you then... Sorry.

---

### Post by Vonnick on 2009-05-04
Clocking? Is your Mobo overclocked? Try disabling overclocking in your BIOS then see how long it takes to boot.

---

### Post by djiock on 2009-05-04
Nope, no overclocking, besides this problem seems to be related to sound system
[http://www.google.fr/search?hl=fr&client=firefox-a&rls=com.ubuntu%3Afr%3Aunofficial&hs=Grl&q=intel8x0+clocking+stops&btnG=Rechercher&meta=]("http://www.google.fr/search?hl=fr&client=firefox-a&rls=com.ubuntu%3Afr%3Aunofficial&hs=Grl&q=intel8x0+clocking+stops&btnG=Rechercher&meta=")

Can't see what I can do... Changing the kernel didn't resolve it.

---

### Post by djiock on 2009-05-06
Well, try an up again :)

---

### Post by djiock on 2009-05-14
And another... The last ?

---

