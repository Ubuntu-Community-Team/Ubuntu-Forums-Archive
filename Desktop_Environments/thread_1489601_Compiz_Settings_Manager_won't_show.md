---
title: "Compiz Settings Manager won't show"
date: 2010-05-21
forum: Desktop Environments
---

### Post by chubz on 2010-05-21
Hello to all. I've run into some problems with compiz, and got a suggestion to start new thread instead of napping another like I already did. I'll paste my post from there and some new info I dug up thanks to realzippy:

> Hi, I'm totally  new to Ubuntu, I've installed it 3 days ago, and my friend sugested to  use the after fresh install script that loads many standard and usefull  aplications and settings found to be best for ubuntu.

Among other thing he said I should use compiz to see what appearance  settings exists for ubuntu and to tweak it to my graphical satisfaction.

I've tried running the compiz settings manager, but have a similar  situation to one above:
I click it in the System->Preferences->Compiz Settings Manager
It lingers in the lower panel for about 20 seconds, then disappears  without starting the manager. 
I've installed compiz fusion to se if it works at all and sure enough it  does. I can choose between metacity and compiz and between Emerald an  GTK WM.

Since I am a newb, and really not sure how to troubleshoot this problem  any suggestions, or even ways to get any information you need is  welcome.
This isn't a crucial problem, so I'm not expecting people to jump on it  but such help would be appreciated, and also a learning experience.

random info says:
when I type in the terminal ~$compiz 
(process:1935): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(process:1937): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
I/O warning : failed to load external entity  "/home/chubz/.compiz/session/106b7a168819b30304127436335428112600000013320001"

also my gfx card is: Nvidia GeForce 8800 GT 512 and have selected  current driver (recommended) in hardware drivers.
There is another option in the drivers which says that alternative  driver version 173 is open to install but I've kept the recomended  because I don't know what is the difference between the two.

EDIT:
My ubuntu is 10.04 x64 - forgot to supply that info too.


Thanks in advance from Borislav
                                                                                                                   now ccsm says:

> ~$ ccsm

(process:1918): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 100, in <module>
    import ccm
  File "/usr/lib/python2.6/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 27, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.6/dist-packages/ccm/Constants.py", line 88, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
and I used cro_CRO for my locale when asked in ubuntu installation on a suggestion by a friend.

but locale in terminal output's:

```

~$ locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME=hr_HR.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```You can see the rest of the napped thread @[ http://ubuntuforums.org/showthread.php?t=1487386]("http://ubuntuforums.org/showthread.php?t=1487386")

Hope everything I've gathered helps, or you notice where I went wrong.

again thanks in advance from Borislav

---

### Post by chubz on 2010-05-21
Because the solution found in the other thread worked for me to, I'll still write it out:

I went to: System -> Admisitration -> Languages Support and set English for my System language and Croatian (Hrvatski) for units and dates.
I've obviously made an error in setting cro_CRO for my locale during installation, because I've had to install Croatian language pack for things to start working.
Now I can run ccsm, normally.

Thanks to the guys in the other thread, and sorry to bug anyone who came across this.

cheers

---

