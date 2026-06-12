---
title: "Steam locking up sound (css)"
date: 2007-09-14
forum: Gaming &amp; Leisure
---

### Post by cytg on 2007-09-14
This just started today.
After launching steam and running

 lsof /dev/snd/pcm* /dev/dsp

it shows Steam.exe, and subsequently there is no sound in-game.(been here before with other apps locking up the sound hardware)

I figure they've launched some crappy flash ad or something that locks it up .. anyone else with this issue ?

I figure I should be able to run css around steam somehow!

---

### Post by cytg on 2007-09-14
apparantly running css without steam is associated with pirating or something.. wich is lame.
Those friggin ad's have been bothering me from the beginning! goddamnit i BOUGHT this game, why the hell should i be forced to look at crappy ad's .. they got their money, but of course they want more.

---

### Post by gubemton on 2007-10-24
It's an annoying yet easy-to-fix problem:
```

$ cat /dev/urandom > /dev/dsp &
$ wine steam &
$ # wait til steam's launched
$ killall cat # you could also use fg <whatever job your cat has become, usually 1> and ctrl + c, but usually killing all cats should work fine

```
The running cat process blocks steam's access to /dev/dsp. After steam's running you can kill cat, so your steam *apps* can access /dev/dsp and fill your ears with slaughter.

Another annoying thing, forced registration on ubuntuforums, can easily be bypassed by using bugmenot.com. Thanks to bugmenot!

---

