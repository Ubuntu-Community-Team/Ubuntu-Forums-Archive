---
title: "what xserver does breezy use, and is it possible to..."
date: 2006-08-25
forum: Desktop Environments
---

### Post by Choad on 2006-08-25
... set up a dapper system but with the xserver that is used in breezy. my sisters laptop does *NOT* agree with the dapper xserver in any way! 

basically.... i really want to get xubuntu on there for her because xubuntu is pretty much the best os i have EVER used as far general user friendlyness/performance/reliability goes

she needed to write an essay over the weekend so i have slapped breezy on there but with 256mb of ram and a celeron 900mhz its not lightening quick

cheers for any help

---

### Post by der_joachim on 2006-08-26
Two hints, hopefully helpful:

- If you are not installing from scratch: last week somehow a faulty X server hit the repos. It was replaced quickly enough, but you may not have the latest version yet? 
- PLease give us some specs of your sister's video card. Maybe we can nudge you the right way. 

I know a way, but it requires a lot of effort and may not even work at all. You can install breezy (from scratch), use apt-pinning to 'freeze' your X version and upgrade to dapper. For apt-pinning, you will need to add something like the following lines in your /etc/apt/preferences:
```

Package: xfree86-server-blah
Pin: breezy
Pin-Priority: 1000

```
You will have to google for the precise specs.

An alternative is using a recent Knoppix CD and if it correctly recognizes your chip, rip the xorg.conf. :)

---

### Post by Choad on 2006-08-26
very nice idea about the knoppix thing.... it might work. and apt-pinning sounds like a great idea too!

thank you very much! i now have some hope of getting the awesome xubuntu installed again :)

the laptop has an intel i810 graphics chip, and the i810 driver works fine.

oooooooooooooh yeah! that was it, i remember now. the error was something to do with "could not enable compositing window manager" or something to do with xcomposite.... something like that

i think xfce uses it's own window manager yeah? xfwm4. could this be part of it? hmmm.... well i have at least a few more ways of trying before im totally stumped again.

---

