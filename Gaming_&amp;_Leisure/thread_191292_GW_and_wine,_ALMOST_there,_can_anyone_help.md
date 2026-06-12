---
title: "GW and wine, ALMOST there, can anyone help?"
date: 2006-06-07
forum: Gaming &amp; Leisure
---

### Post by KayinStorm on 2006-06-07
Well, after a night of mad installing, I've got wine up and running, and GW will install, attempt to connect, and freeze.  Is there a fix for this, or a workaround, or is it possible that it's just that slow and there's a way to speed things up?

GW's install is clean, I checked that myself (I worl for GuildWarsGuru in their tech forums, so that's always my first move) but there seems to be an issue in execution in wine.  Anyone got a starting point for me to check?

BTW, the results of this will be posted on GWG so that those interested can make the switch for themselves.  it's been a popular topic as of late in light of Vista.

Thanks...

---

### Post by handy on 2006-06-07
You are the closest that I have seen on these forums to success with GW & Wine!!

That's great!  Wine is sooo close now...

Surely, before this year is out, Wine will have it covered, what a momentous occasion that day will be!

Be patient my friend, all good things come to those who wait!! :KS

---

### Post by KayinStorm on 2006-06-07
I have an idea, considering the structure of Guild Wars...

Is there a way to install a DX version into wine?  if so, can someone walk me through it?

This is my second day of Ubuntu, and though I have a lot of noob in me I know hardware like nobody's business and understand the GW program pretty well after supporting it for more than a year.

let me know how I can help you guys, so we all can reap the rewards here...

---

### Post by KayinStorm on 2006-06-07
Double post of sorts, but...

With another mod from GWG I found why wine breaks with GW, or at least the most likely reason.

DX 9, and the DX APIs.  It's a solely Direct3D game, so it's a yer-bugger to get to run.  Cedega does it because they licensed the API (no wonder it costs) and can therefore support the rendering method.

I'mma go douse my brain now, it's on fire.

---

### Post by Thoop on 2006-06-08
I got it running some time ago, don't know which wine version, but it was very ugly, I could only see some textures and it took 30 min for my mouse to appear :p
I'll try it with the latest version asap.

---

### Post by handy on 2006-06-09
It's great that people are chasing a Wine solution for GW!

I tried the Crossover demo the other day, it doesn't work!

Cedega won't work for me for an unknown reason, with my Dapper install?

I'd love for Wine to work so I can dump Cedega alltogether...

---

### Post by Thoop on 2006-06-09
i'm using cedega for the moment and that works perfectly. I'll try it with wine this afternoon ;)

---

### Post by KayinStorm on 2006-06-09
I'm using cedega to understand why it does/doesn't work.  Not sure yet, but even in cedega it's not working well...

---

### Post by Thoop on 2006-06-09
hmm, doesn't get further than the downloading screen (after download 100%) :(

edit: after upgrading to 0.9.15 I can get to the log in screen, but I can't fill in anything. (that's with XGL)
without xgl using both the nonXgl script and a separate session it only displays garbage after the download screen.

---

### Post by thak on 2006-06-19
[QUOTE=Thoop]hmm, doesn't get further than the downloading screen (after download 100%) :(

edit: after upgrading to 0.9.15 I can get to the log in screen, but I can't fill in anything. (that's with XGL)
without xgl using both the nonXgl script and a separate session it only displays garbage after the download screen.[/QUOTE]

Hmm.  I think I can confirm that Xgl is the key.

I got all the way to the "select your character screen" when I was still running 0.9.9 with Xgl.  I upgraded to 0.9.15 and could still get to that screen.  It looked REALLY weird--all kinds of crazy artifacts and duplication of taskbars and stuff--but it ran.

Just this morning, I turned off Xgl and tried to run it again, and it totally broke.  So it looks like the standard X server doesn't work as well as the Xgl one.

Just my $0.02.

Hope someone gets this fixed soon.  ;)

---

