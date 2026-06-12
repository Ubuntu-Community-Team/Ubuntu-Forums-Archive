---
title: "ibus no input window in gnome 3"
date: 2011-05-16
forum: Desktop Environments
---

### Post by franklinno1 on 2011-05-16
Hi all,

I recently installed gnome 3, using the ppa -> dist-upgrade -> install gnome-shell method..

ibus used to work fine with gnome 2.3 and unity, but in gnome 3, the icon is still there, the deamon is still running ( i presume) but no matter where i click, it always shows 'no input window'... (for example, i can't type anything other than English here...).

Does any of you have any idea how to solve the problem? Any help is much appreciated!:D

---

### Post by franklinno1 on 2011-05-16
problem solve indeed...

$sudo apt-get purge ibus

then 

 $ sudo add-apt-repository ppa:shawn-p-huang/ppa 
 $ sudo apt-get update 
 $ sudo apt-get install ibus-gtk ibus-qt4 ibus-pinyin ibus-pinyin-db-open-phrase 
 $ sudo apt-get upgrade 
 $ im-switch -s ibus

I also went to the language support and installed chinese language support with input method and extra fonts. 

and reboot...

apparently simply logging out does not bring ibus to work....

strangly, i have to select 'keyboard input method system' to 'none' in Language Support in order to get ibus working......

---

### Post by franklinno1 on 2011-05-16
But anyone knows how to change the label to [solved]?:(

---

### Post by wildmanne39 on 2011-05-16
> **franklinno1 said:**
> Hi all,

I recently installed gnome 3, using the ppa -> dist-upgrade -> install gnome-shell method..

ibus used to work fine with gnome 2.3 and unity, but in gnome 3, the icon is still there, the deamon is still running ( i presume) but no matter where i click, it always shows 'no input window'... (for example, i can't type anything other than English here...).

Does any of you have any idea how to solve the problem? Any help is much appreciated!:D

Hi,if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.

---

### Post by franklinno1 on 2011-05-16
> **wildmanne39 said:**
> Hi,if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.


I was about to do that. but I couldn't find the 'forum tools'....could you provide a little more detail about how to change it to 'solved'? cheers!

---

### Post by franklinno1 on 2011-05-16
> **franklinno1 said:**
> I was about to do that. but I couldn't find the 'forum tools'....could you provide a little more detail about how to change it to 'solved'? cheers!

got it...

---

### Post by 3togo on 2011-08-01
How can u solve it without installing ibus-gtk3?

---

### Post by shifu on 2011-12-13
> **franklinno1 said:**
> problem solve indeed...

$sudo apt-get purge ibus

then 

 $ sudo add-apt-repository ppa:shawn-p-huang/ppa 
 $ sudo apt-get update 
 $ sudo apt-get install ibus-gtk ibus-qt4 ibus-pinyin ibus-pinyin-db-open-phrase 
 $ sudo apt-get upgrade 
 $ im-switch -s ibus

I also went to the language support and installed chinese language support with input method and extra fonts. 

and reboot...

apparently simply logging out does not bring ibus to work....

strangly, i have to select 'keyboard input method system' to 'none' in Language Support in order to get ibus working......


How would I go about reversing everything I did here via this post? I followed every step and it did not work for me (using Lubuntu).

I would like to reverse every command before going forward. Thank you for you help.

---

### Post by newb85 on 2012-01-20
> **shifu said:**
> How would I go about reversing everything I did here via this post? I followed every step and it did not work for me (using Lubuntu).

I would like to reverse every command before going forward. Thank you for you help.

This didn't work for me either.  Apt fails to download index files from the ppa.  Incidentally, the nothing in the ppa was compiled for anything newer than Maverick, which may be part of the problem.

I'll break down the reversing process.
Remove the packages that were installed (if you got this far):
sudo apt-get remove [package names, space-delineated]

Remove the ppa:
sudo add-apt-repository -r ppa:shawn-p-huang/ppa
(The notice I received from this command said it was adding the repository, but it did in fact remove it.)

Then proceed to reinstall the IME as before.

---

### Post by bebopiiam on 2012-05-27
Hi.
 I had the same problem under Ubuntu 12.04 with Anki Japanese input and your response led to the solution.  For Japanese input:[INDENT]$ sudo apt-get install ibus-gtk ibus-qt4
 $ sudo apt-get upgrade 
$ sudo reboot
[/INDENT]fixed the problem.

Thanks much!

Steve S.

---

### Post by rykel on 2012-10-31
Hi, I am running GNOME 3 on Ubuntu 12.10 and NO, I cannot find a way to use the Chinese Input Method. I do NOT wish to use a PPA for such a basic system task. Thanks!

---

