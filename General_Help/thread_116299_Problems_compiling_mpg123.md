---
title: "Problems compiling mpg123"
date: 2006-01-12
forum: General Help
---

### Post by djpenguin on 2006-01-12
I've been using gentoo linux primarily for quite some time now, so I am very familiar with compiling software.  I recently set up Kubuntu on my wife's laptop, and I am trying to compile mpg123 (need a command-line audio player for alarm-clock purposes), and I've run into some sticky issues.

I used apt-get to install make, automake, gcc, and build-essential, so I'm pretty sure I've got all the tools needed.

However, every time I try to compile the program (in this case the command should be "make linux-alsa", I get a really bizarre error output that looks like this:

```
mpg123.c:649: warning: comparison between pointer and integer
mpg123.c:649: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:649: warning: comparison between pointer and integer
mpg123.c:650: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:650: warning: comparison between pointer and integer
mpg123.c:652: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:652: warning: comparison between pointer and integer
mpg123.c:661: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:661: warning: comparison between pointer and integer
mpg123.c:671: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:682: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:682: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:682: warning: passing argument 1 of â€˜audio_encoding_nameâ€™ makes integer from pointer without a cast
mpg123.c:682: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:682: warning: format â€˜%ldâ€™ expects type â€˜long intâ€™, but argument 3 has type â€˜struct topt *â€™
mpg123.c:682: warning: format â€˜%dâ€™ expects type â€˜intâ€™, but argument 5 has type â€˜struct topt *â€™
mpg123.c: In function â€˜set_synth_functionsâ€™:
mpg123.c:758: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:758: error: invalid operands to binary &
mpg123.c:764: error: invalid use of undefined type â€˜struct audio_info_structâ€™
mpg123.c:764: warning: passing argument 1 of â€˜make_conv16to8_tableâ€™ makes integer from pointer without a cast
make[2]: *** [mpg123.o] Error 1
make[2]: Leaving directory `/tmp/mpg123-0.59r'
make[1]: *** [mpg123-make] Error 2
make[1]: Leaving directory `/tmp/mpg123-0.59r'
make: *** [linux-alsa] Error 2

```

Any ideas what's going on here?  I've never seen this sort of error before.


*I posted this in the Kubuntu forum too, but got no responses, so I figured I'd try it here since this problem really has very little to do with KDE.

---

### Post by Mr_Grieves on 2006-01-12
Do you need to compile it? Can't you just fetch it via Synaptic or some other packet manager?

Looking at the syntax above.. I'd guess that you're missing a lib. "Use of undefined data structure"

---

### Post by djpenguin on 2006-01-12
That would be nice, but it hasn't worked out so far.

'apt-get install mpg123' returned a no package found error, and I could not find mpg123 (or any other command line audio player, for that matter) by looking through the package listing displayed by the package manager included with Kubuntu (Adept.)

I just want a command-line audio player so I can set up an alarm clock as a cron job.  I'd much rather use something that is in the current package repository, failing that, at least something available in a .deb package, but since I haven't been able to find anything yet, it looks like I'm stuck doing it the old-fashioned way.

---

### Post by Mr_Grieves on 2006-01-12
Searching the allmighty google I found that mpg123 is depending on ALSA OSS and ALSA Library.

Do you got those two installed?

---

### Post by Mr_Grieves on 2006-01-12
Btw.. about finding a package in Synaptic.. it's not like you've just forgot to add some extra repositories?


[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by djpenguin on 2006-01-12
ALSA is installed and working on that machine, so the libraries are definitely there.  I looked at the packages, but couldn't find one that specifically said alsa-oss, so I'm assuming it's part of some meta-package.  Any idea which one, so I can see if it's installed or not?

---

### Post by Sudokan on 2006-01-12
I am not sure if this is the same, but there is a command line driven mp3 player in the universe repositories called "mpg321". It is listed as a a mpg123 compatible player. There is also an "mpg123" command line mp3 player in the multiverse repositories. This has several versions. The default mpg123 package uses OSS, but there is a version supporting esound and another supporting NAS. Hope this is what you were looking for.

Sudokan

*The opposite of a correct statement is a false statement.  But the opposite of a profound truth may well be another profound truth.  ~Niels Bohr*

---

