---
title: "Zapping crashes entering in preferences"
date: 2006-06-05
forum: Desktop Environments
---

### Post by iceclow on 2006-06-05
I am in trouble with this. After upgrading from breezy if you open zapping and go to preferences, it crashes. The same happens when you try to go to the channels window. It seems that its broken. 

Any ideas?

---

### Post by Pahanilmanlintu on 2006-06-06
Same problem here, no ideas.

---

### Post by Ramses de Norre on 2006-06-06
Tried reinstalling it? Or purging it and then installing again?

---

### Post by Jason_25 on 2006-06-06
I had to recompile it to make it work on amd64 because I was getting the same crashes as you.  Horrible program still, just like many of the other tv apps out there.

---

### Post by hafuch on 2006-06-19
Hi All,

I've been frustrated by the Zapping TV crashes since my upgrade to Dapper 6.06, but here is a strange work-around to until the program gets fixed or someone comes up with a proper solution.

In short, since Zapping TV crashes anytime you try to edit preferences or channels, you can't change channels. So, what I did is install TV Time, which works but doesn't give as good a quality picture as Zapping does. In TV Time, I change to the channel I want to watch, then close it. I then open Zapping TV, and voilà: I have in Zapping the last channel I used in TV Time. I know it's a bit stupid, but like I said: it's temporary, until a REAL solution arises.

Here's how I did it:

STEP 1:
Setup your video card (I have an older BT878 ). For my card, I typed the following at the command line:

sudo gedit /etc/modprobe.d/options

Then I added the following line to the end of the file that opens up:

options bttv card=24 tuner=5 radio=1

(You can get the card and tuner parameters for your card from here: [http://www.telenovela-world.com/~spade/linux/howto/BTTV-4.html](http://www.telenovela-world.com/~spade/linux/howto/BTTV-4.html) )

I then rebooted, but you only need to type in the terminal: modprobe -a
or something like that (I'm not totally sure).

STEP 2:
I then installed TV Time and Zapping TV through Synaptic.

Then open TV Time, scan channels, and make sure the "line-in" under your sound controller isn't muted (right click on the speaker icon in the upper right corner of your screen) and open preferences or something like that. You'll find it.) Find the channel you like, then close it.

Then open Zapping, and you should have the last channel you had in TV Time.

STEP 3:
If you keep getting this "can't start in overlay mode" everytime you start Zapping, open the "help" dialogue in Zapping and look through there for the solution. I'll post the fix for this as soon as I get home.

I know this sounds really zany to have to do, and many will question the need for such ridiculous gymnastics to get Zapping TV (of all TV apps?!) to work, but the simple truth is that Zapping gives GREAT picture quality (better than any other app I've been able to get to work), and most importantly ... my wife likes it. (Often, when your wife's happy, you're happy! :) )

I also apologize in advance for the overly (some might say patronizingly) simple instructions given here, but I suppose there are many Ubuntu users like myself who would consider themselves a Newbie even after using Ubuntu since 2004! We just want things to work, and aren't too comfortable with excessive "tweaking", but do LOVE the Ubuntu Linux community and are willing to embrace a post-Windows learning curve ... and the idea of being free of Windows!

Anyway, that's my two cents worth. And if anyone has other advice, I'm all ears.

In the spirit of Ubuntu, Good luck ... and let us know if someone finds a solution to the Zapping TV snafu!

hafuch

---

### Post by DooMRunneR on 2006-07-26
Hi,

i have the same problem with zapping, the workaround with tvtime works, but..... you know.....

do you get the same error when starting zapping in the terminal and klick on the preferences button?

```

** (zapping:27906): WARNING **: GConf key '/apps/zapping/plugins/deinterlace/method' is unset and has no default. Schemas incomplete or not installed?


(zapping:27906): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, GTK_LIST_STORE(tree_model))' failed

(zapping:27906): GLib-GObject-WARNING **: gtype.c:3312: type id `0' is invalid

(zapping:27906): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced

```

I tried to build zapping out of the cvs but dind´t work.

GTK+2.0=>GTK+2.4 Error

---

### Post by dcotruta on 2006-08-14
BUMP!!!

I thought I was going insane - but I guess I'm not.

This is still broken - and it seems to be the only application that I can use to run my WinTv USB II.

Bah, any updates / any way we can raise this to a higher level?

---

### Post by Philippt on 2006-09-09
update/compile the sorce (zapping_0.10cvs6-1_i386) and everything works...

---

### Post by sque on 2006-09-29
I would rather hear. "Yes probably it will be fixed or removed". Why is there at repository if it is broken?

I have same output when I run zapping and go to preferences
```
sque@sque-ubuntu:~$ zapping

** (zapping:27352): WARNING **: GConf key '/apps/zapping/plugins/teletext/cache_size' is unset and has no default. Schemas incomplete or not installed?


(zapping:27352): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, GTK_LIST_STORE(tree_model))' failed

(zapping:27352): GLib-GObject-WARNING **: gtype.c:3312: type id `0' is invalid

(zapping:27352): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced

```

---

### Post by darkteckno on 2006-10-06
Is there a Deb for the latest version?

Cheers

Jon

---

### Post by junglebunny on 2006-10-20
Thanks Phillippt, for your tip: 

"update/compile the sorce (zapping_0.10cvs6-1_i386) and everything works..."

Forgive my ignorance, but how does one compile Zapping from the source, and where can I download/get it?

I'd love to do this and "fix" my Zapping installation.

Thanks,

Junglebunny

---

### Post by k_f on 2006-10-20
> Forgive my ignorance, but how does one compile Zapping from the source, and where can I download/get it?

I'd love to do this and "fix" my Zapping installation.

Thanks,

Junglebunny

You can get the source here: 

[http://zapping.sourceforge.net/Zapping/Download.html](http://zapping.sourceforge.net/Zapping/Download.html)

I just compiled zapping_0.10cvs6 but there is a new problem, when it runs a error window pops up. I got this in terminal:

> ** (zapping:8198): WARNING **: GConf key '/apps/zapping/plugins/deinterlace/method' is unset and has no default. Zapping schemas incomplete or not installed?


Any idea how to fix it?

Thanks,

Fei.K

---

### Post by darkteckno on 2006-11-07
Bumpa Bumpa stick it up your jumpa

---

