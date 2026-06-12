---
title: "Making screen red to preserve night vision while doing astronomical observations?"
date: 2009-02-25
forum: Education &amp; Science
---

### Post by heypete on 2009-02-25
Greetings all,

Does anyone knew of any software that one could use to tint the screen red, so as to preserve one's night vision while doing astronomical observations (and not annoy other nearby observers)?

While I *could* just tape a piece of red cellophane over the screen, I'd prefer something in software. I tend to be forgetful, and it'd suck to leave the cellophane at home.

I'm comfortable with the command line, and would be perfectly willing to invoke commands or run shell scripts if necessary, so long as there was a also a command/script to revert the screen back to normal colors. ;)

Any recommendations?

---

### Post by sanskaras on 2009-02-25
I don't know how with anyother graphics card but if you have a Nvidia graphics card you can go in System -> Administration
Theres a NVIDIA X Server Settings thingy.

It opens up a GUI and has a bunch of options.  Click X Server Color Correction.

-Turn down the brightness all the way for all color channels.

-Turn The Contrast and Gamma all the way down for the Green and Blue color Channels

-Adjust the Red Color Channel's Brightness, Contrast and Gamma to suit your needs!

I'm sure someone on here can make a script to apply these settings, but I'm lost when it comes to that.

---

### Post by heypete on 2009-02-26
My apologies for not mentioning it earlier: I have a Dell Inspiron 1521 with an ATI X1200/X1250/X1270 (same card reported differently in different OSs and in the BIOS. Go figure.) integrated graphics card, so the nvidia option is out.

I'm not using the fglrx binary driver, as it causes the system to freeze and behave oddly when suspending/waking. The driver I'm presently using, which I presume to be the open source "ati" or "radeon" driver (anyone know how to check for sure? The exact command eludes me.), doesn't have this problem so I've been using it for the time being.

Oh, for reference, I'm also using 8.10.

Oh, and **sanskaras**, thanks for the prompt response.

---

### Post by sanskaras on 2009-02-26
No problem.  Also, found an even easier option, should work for your set up.

found it at [http://xcalib.sourceforge.net/]("http://xcalib.sourceforge.net/")

But it's in the repositories

So just type:

```
sudo apt-get install xcalib
```

to install

Then for your red screen type:

```
xcalib -green .1 0 1 -alter
xcalib -blue .1 0 1 -alter

```

And your screen will turn red.

The settings for the colors are <gamma> <brightness-percent> <contrast-percent>, so if you have trouble reading the red screen use

```
xcalib -red <gamma> <brightness-percent> <contrast-percent> -alter
```

to adjust it to your needs.

```
xcalib -clear
```

Will return your screen back to normal.


All this can easily be made into a quick bash script also of course.

---

### Post by yahooshua on 2010-09-30
This might help you. Look at the post by jsgoodall. The first script works well.

[http://ubuntuforums.org/showthread.php?p=9906874#post9906874](http://ubuntuforums.org/showthread.php?p=9906874#post9906874)

---

### Post by hkarl629 on 2010-10-07
The astronomy program "Stellarium" has a Night setting which turns all the stuff on the screen red.  Might want to check it out.

---

### Post by Nolroz on 2010-11-17
Great Solution! I installed xcalib today, and I am happily seeing RED now! And I can write a cron for it. Sweet!

---

### Post by ukreech on 2010-11-18
thanks for the links guys. curiosity helps. LOL!

---

### Post by Keith Myers on 2010-11-21
Unfortunately, Stellarium is broken with 10.10.  I really wanted to look at this one.  The only planetarium program I've had a chance to use in Linux is the KStars program using the KDE interface over in my 10.04LTS installation.  I'm a dedicated astro-imager and the best solution for keeping your laptop screen from blinding you and other observers and taking out your night vision, is to use either a red gel velocroed over the screen or better yet a custom cut piece of 1/8" thick red acrylic or Lexan plastic laid over the screen.  I've found that trying to enable a software solution for a red screen inevitably backfires because too many programs want to control the user inferface and will toggle the red screen settings off in one program while enabling it in the other. Also typically, program menus and title bars are immune from control with software solutions.  Most everyone I run into out on the telescope field using a laptop uses a hardware screen solution.  You can also cut down your light leakage by putting a cut down cardboard box over the laptop where it blocks the sides and back of the screen.  Your neighbors will thank you and it will solve dew issues too.  Just my $0.02 of practical experience.

Keith

---

### Post by KnightByDay on 2010-12-03
> **sanskaras said:**
> No problem.  Also, found an even easier option, should work for your set up.

found it at [http://xcalib.sourceforge.net/](http://xcalib.sourceforge.net/)

But it's in the repositories

So just type:

```
sudo apt-get install xcalib
```to install

Then for your red screen type:

```
xcalib -green .1 0 1 -alter
xcalib -blue .1 0 1 -alter

```And your screen will turn red.

The settings for the colors are <gamma> <brightness-percent> <contrast-percent>, so if you have trouble reading the red screen use

```
xcalib -red <gamma> <brightness-percent> <contrast-percent> -alter
```to adjust it to your needs.

```
xcalib -clear
```Will return your screen back to normal.


**All this can easily be made into a quick bash script also of course**.


Hey! I'm fairly new to Ubuntu and have never written any bash scripts, could you please tell me how to write a script for this red screen!? 

Thanks heaps, Knight by Day.

---

