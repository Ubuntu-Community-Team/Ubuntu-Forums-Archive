---
title: "Problems compiling mpg123"
date: 2006-01-10
forum: Desktop Environments
---

### Post by djpenguin on 2006-01-10
I've been using gentoo linux primarily for quite saome time now, so I am very familiar with compiling software.  I recently set up Kubuntu on my wife's laptop, and I am trying to compile mpg123 (need a command-line audio player for alarm-clock purposes), and I've run into some sticky issues.

I used apt-get to install make, automake, gcc, and build-essential, so I'm pretty sure I've got all the tools needed.

However, every time I try to compile the program (in this case the command should be "make linux-alsa", I get a really bizarre error output that looks like this:

```
mpg123.c:649: warning: comparison between pointer and integer
mpg123.c:649: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:649: warning: comparison between pointer and integer
mpg123.c:650: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:650: warning: comparison between pointer and integer
mpg123.c:652: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:652: warning: comparison between pointer and integer
mpg123.c:661: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:661: warning: comparison between pointer and integer
mpg123.c:671: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:682: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:682: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:682: warning: passing argument 1 of â&#128;&#152;audio_encoding_nameâ&#128;&#153; makes integer from pointer without a cast
mpg123.c:682: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:682: warning: format â&#128;&#152;%ldâ&#128;&#153; expects type â&#128;&#152;long intâ&#128;&#153;, but argument 3 has type â&#128;&#152;struct topt *â&#128;&#153;
mpg123.c:682: warning: format â&#128;&#152;%dâ&#128;&#153; expects type â&#128;&#152;intâ&#128;&#153;, but argument 5 has type â&#128;&#152;struct topt *â&#128;&#153;
mpg123.c: In function â&#128;&#152;set_synth_functionsâ&#128;&#153;:
mpg123.c:758: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:758: error: invalid operands to binary &
mpg123.c:764: error: invalid use of undefined type â&#128;&#152;struct audio_info_structâ&#128;&#153;
mpg123.c:764: warning: passing argument 1 of â&#128;&#152;make_conv16to8_tableâ&#128;&#153; makes integer from pointer without a cast
make[2]: *** [mpg123.o] Error 1
make[2]: Leaving directory `/tmp/mpg123-0.59r'
make[1]: *** [mpg123-make] Error 2
make[1]: Leaving directory `/tmp/mpg123-0.59r'
make: *** [linux-alsa] Error 2

```

Any ideas what's going on here?  I've never seen this sort of error before.

---

