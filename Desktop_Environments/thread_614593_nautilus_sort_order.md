---
title: "nautilus sort order"
date: 2007-11-16
forum: Desktop Environments
---

### Post by zymologist on 2007-11-16
Bash sort order
```
$ ls -la
total 2.4G
drwxr-xr-x  2 zym 4.0K 2007-11-16 19:57 ./
drwxr-xr-x 11 zym 4.0K 2007-11-16 19:09 ../
-rw-r--r--  1 zym 351M 2007-11-07 15:13 Ugly.Betty.S02E01.HDTV.XviD-XOR.avi
-rw-rw-rw-  1 zym 350M 2007-10-04 22:30 ugly.betty.s02e02.hdtv.xvid-xor.avi
-rw-r--r--  1 zym 351M 2007-11-07 16:35 Ugly.Betty.S02E03.HDTV.XViD-Caph.avi
-rw-r--r--  1 zym 351M 2007-11-07 15:06 Ugly.Betty.S02E04.HDTV.XViD-Caph.avi
-rw-r--r--  1 zym 351M 2007-10-26 03:10 ugly.betty.s02e05-caph.avi
-rw-r--r--  1 zym 351M 2007-11-07 14:19 Ugly.Betty.S02E06.HDTV.XviD-NoTV.avi
-rw-r--r--  1 zym 351M 2007-11-16 06:19 Ugly.Betty.S02E07.HDTV.XviD-XOR.avi
zym@home /media/Ugly Betty

```

Nautilus sort order
```

ugly.betty.s02e02.hdtv.xvid-xor.avi
ugly.betty.s02e05-caph.avi
Ugly.Betty.S02E01.HDTV.XviD-XOR.avi
Ugly.Betty.S02E03.HDTV.XViD-Caph.avi
Ugly.Betty.S02E04.HDTV.XViD-Caph.avi
Ugly.Betty.S02E06.HDTV.XviD-NoTV.avi
Ugly.Betty.S02E07.HDTV.XviD-XOR.avi

```

How can I get nautilus to sort sanely like bash? I dont care what case a file is named with, only that the numbers are sorted in order

my local settings are as follows:
```
$ locale
LANG=en_AU.UTF-8
LC_CTYPE="en_AU.UTF-8"
LC_NUMERIC="en_AU.UTF-8"
LC_TIME="en_AU.UTF-8"
LC_COLLATE=en_AU.UTF-8
LC_MONETARY="en_AU.UTF-8"
LC_MESSAGES="en_AU.UTF-8"
LC_PAPER="en_AU.UTF-8"
LC_NAME="en_AU.UTF-8"
LC_ADDRESS="en_AU.UTF-8"
LC_TELEPHONE="en_AU.UTF-8"
LC_MEASUREMENT="en_AU.UTF-8"
LC_IDENTIFICATION="en_AU.UTF-8"
LC_ALL=

```

---

### Post by zymologist on 2007-11-19
nobody else has been bothered by this and knows how to solve it?

---

### Post by erginemr on 2007-11-20
> **zymologist said:**
> nobody else has been bothered by this and knows how to solve it?

Hello,

I have made a small research in Google on the problem, and it turned out that quite a few people have been bothered by this behavior of Nautilus. Some of pthepeople pointed to the LC_COLLATE environment value but playing with it before starting Nautilus did not yield a favorable result either. Yet, apparently there is no solution to that and you have to live with it.

There is a little handy file manager "PCManfm", very similar in looks to Nautilus, which can be installed with:

sudo aptitude install pcmanfm

It does show the files in the correct, non-case-sensitive mode. First screenshot below belongs to Nautilus, and the second belongs to PC File Manager.

Hope this helps.

---

### Post by erginemr on 2007-11-20
By the way, you can check its features from:

[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

But the deb version there is kind of obsolete, so if you decide to try, you should install it by using:

sudo aptitude install pcmanfm

---

### Post by zymologist on 2007-11-20
Thanks, I tried a few different settings for LC_COLLATE but they appear to have zero effect on nautilus (although it was possible to mess up the bash sort order so it was the same as nautilus). i was "ctrl+alt+backspacing" between changing each setting so nautilus would definitely have been being restarted.

pcman looks like an ok replacement, any idea where I'd specify it to be the default file manager that gets opened for the places menu, etc?

---

### Post by Developer.ca on 2008-01-15
I just fixed this on my system myself.  Nautilus is dependent on your locale settings, but you have to change your .profile, not your .bashrc.

I just added this to my .profile

export LC_COLLATE="Posix"

(replace Posix with whatever collating you want, evidently en_AU.UTF-8 )

By the way, if you check 'man 7 locale' you can see the hierarchy of LC_ALL, LC_<whatever> and LANG.   The hierarchy is: LC_ALL overrides everything (if set to a non-null value).  If LC_ALL is not used, then it checks the LC_ variables.  If the specific one is not set, it checks LANG.

Since you are setting LANG and all your LC_ vars to en_AU.UTF-8, you don't have to set the LC_ variables...unless you want them set to something different than your LANG setting.

Richard

---

