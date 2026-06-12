---
title: "Problem with sound device in Skype"
date: 2006-06-22
forum: Desktop Environments
---

### Post by rpalyvoda on 2006-06-22
Hi,

I've been using Skype on Ubuntu for some time, and everything was Ok till I installed recent updates.

Now, Skype loads as usually, but each time I try to make a call, I get an error message saying.

/dev/dsp-1: Device or resource busy

Has anyone experienced similar problems, and is there a solution?

I've already re-installed skype and it still doesn't work...

---

### Post by fdimmling on 2006-06-22
[QUOTE=rpalyvoda]
/dev/dsp-1: Device or resource busy
[/QUOTE]

Do you have two soundcards? Normally /dev/dsp is the first - and maybe only - soundcard. Did you check setting headset to /dev/dsp ?

Friedrich

---

### Post by benjaminzsj on 2006-06-22
I have a familiar problem, if not the same. I don't get any error but I can't chat with others, the warning they get is something like "Remote sound device problem".

---

### Post by fares on 2006-06-23
Hi guys,

are you using an integrated/on-board audio chipset or a proper soundcard?

I have both on my PC: one isn't installed at all (lack of driver) and the on-board realtek has a problem that looks related to the fact that the mic jack can also be used as an extra output for a 5.1 surround configuration.

I didn't find a way to solve this problem (yet).

See y'all,

Fabio

---

### Post by rpalyvoda on 2006-06-23
Nothing seems to be working....

I've tried averything, and even skype_dsp_hijacker doesn't work.

What's really strange is that it used to work!!! And in XP, it works so it's not a problem with hardware, it's about drivers or config.

Well, I'll keep trying...

Anyway, thanks for help!!! This is such a wondrefull community that makes Ubuntu the best linux distro!

---

### Post by rpalyvoda on 2006-06-30
Yeah!

I installed new Skype 1.3 beta, and it works pretty well!

---

### Post by matjaz_pirnovar on 2006-06-30
Hi guys,

Perhaps a silly question but... are you talking about skype 1.2.0.18 and older or new 1.3 beta?

1.3 beta should work on Dapper (well, hopefully) and alsa providing you deleted /etc/asound.conf  file if you were you using it on old version.

Smile
M

---

### Post by rpalyvoda on 2006-07-01
[QUOTE=matjaz_pirnovar]Hi guys,

Perhaps a silly question but... are you talking about skype 1.2.0.18 and older or new 1.3 beta?

1.3 beta should work on Dapper (well, hopefully) and alsa providing you deleted /etc/asound.conf  file if you were you using it on old version.

Smile
M[/QUOTE]

The problem was with version 1.2. Beta version works fine, after I a few easy steps (it may be helpfull for some)
a) delete /etc/asound.conf
b) configure Skype to use ALSA (options, sound devices)
c) reboot

---

