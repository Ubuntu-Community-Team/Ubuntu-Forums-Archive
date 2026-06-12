---
title: "No sound in flash"
date: 2005-12-09
forum: Desktop Environments
---

### Post by reuben on 2005-12-09
I have the flash plugin installed in firefox - flash sites work, but they don't have sound. Any way to fix this?

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=reuben]I have the flash plugin installed in firefox - flash sites work, but they don't have sound. Any way to fix this?[/QUOTE]
This might help:
```

$ cat /etc/mozilla-firefox/mozilla-firefoxrc
# which /dev/dsp wrapper to use
FIREFOX_DSP="artsdsp"

```
I had to add that last line to the file before FF would use the correct sound sink.  I am using Kubuntu and aRTS, hence artsdsp.  You may need to use something different depending on your sound system.  E.g. "esddsp".

---

### Post by reuben on 2005-12-09
That did the trick. It had "auto" previously...I guess auto is broken.

---

### Post by Jagunço on 2005-12-12
Hi folks.

I´ve downloaded and installed FF 1.5 by hand, and there´s no firefoxrc around. How can I fix this sound problem?

Thanks in advance.

---

### Post by jrib on 2005-12-12
check out this thread: [http://ubuntuforums.org/showthread.php?t=76743](http://ubuntuforums.org/showthread.php?t=76743)

You'll need to create the symbolic link for libesd.so.1 (post 5) and post 19 too.  Note, that sound is lagged using esd :/

---

### Post by pizzach on 2005-12-14
[quote=_jason]check out this thread: [http://ubuntuforums.org/showthread.php?t=76743]("http://ubuntuforums.org/showthread.php?t=76743")

You'll need to create the symbolic link for libesd.so.1 (post 5) and post 19 too.  Note, that sound is lagged using esd :/[/quote] 

For the love of god, NOOOOOO!  ::End of dramatisism::  I avoid esd like the plague because of how bad it lags on my machine.  Though I did find another way to use aoss.  As said in other places, it is lower level, so it should work better.  So this guide is for if you have laggy audio in Firefox 1.5.  **It works in basically the same way as changing the FIREFOX_DSP="aoss" did in Firefox 1.0.7.  Therefore you should have roughly the same expectations and results.**


I used information from two pages:
[http://www.ubuntuforums.org/showthread.php?t=75237&highlight=firefox+sound+flash]("http://www.ubuntuforums.org/showthread.php?t=75237&highlight=firefox+sound+flash")
[http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Firefox.2C_Mozilla.2C_RealPlayer.2C_Skype_.26_Co]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Firefox.2C_Mozilla.2C_RealPlayer.2C_Skype_.26_Co")
(Who said gentoo users didn't help nobody.  :)  I'm not a gentoo user btw.)


_**[COLOR="Navy"][SIZE="5"]Pizzach's AOSS for Firefox 1.5 Guide V0.0a[/SIZE][/COLOR]**_


[SIZE="4"]**The Test:**[/SIZE]

To see if this hack will work for you without jumping around just enter the following three commands:
```
[B]sudo apt-get install alsa-oss
killall esd
aoss /path_to_firefox_1.5/firefox "$@"[/B]
``` 


[SIZE="4"]**How to set it up if the test worked:**[/SIZE]

**[COLOR=Red]1.[/COLOR]** This step should have already been done, but repeating it doesn't hurt:```
**sudo apt-get install alsa-oss**
``` 

The important ingredient to make firefox 1.5 use aoss is:
aoss /path_to_firefox_1.5/firefox "$@"
I used a shell script named ff15 pointing to firefox.



**[COLOR=Red]2.[/COLOR]** From the terminal create a document called ff15 in gedit by:```
**sudo gedit /usr/bin/ff15**
``` 

**[COLOR=Red]3.[/COLOR]** Copy and paste into gedit the code below then editing for the true path:```
**aoss /path_to_firefox_1.5/firefox "$@"**
``` 
**[COLOR=Red]4.[/COLOR]** Save and quit gedit.

**[COLOR=Red]5.[/COLOR]** Make it executable from the terminal:
```
**sudo chmod +x /usr/bin/ff15**
``` 

**[COLOR=Red]6.[/COLOR]** Then I went to the menu System>Prefered Applications
and put in ```
**ff15 %s**
``` for the custom command box.   This way Firefox uses aoss by default **in the absence of esd** instead of alsa when the default web browser [firefox] is called.


[SIZE="4"]**Esound cleanup:**[/SIZE]

You have now finished setting up firefox.  **If you have esd installed, firefox will try to default to it it before it uses alsa or aoss.**  This is bad because esd audio syncing is horrible.  If you do ```
**killall esd**
``` before starting firefox through ff15, it should correct the problem.  If you feel you don't need esd, you can just do:
```
**sudo apt-get remove esound esound-clients**
```  If you ever need it again someday you can just apt-get it back with:
```
**sudo apt-get install esound esound-clients**
``` 
Make sure that you have from the gnome menu System>Multimedia System Selector set for alsa for both sink and source if you get rid of esd.

Feel free to say if you have any problems this way.  I personally didn't touch firefox 1.07 on my system.  I didnt' feel like chancing a broken system because of something stupid happening.  I just updated this guide to include the esd information.

---

### Post by jrib on 2005-12-14
I was hoping that using aoss would resolve the lag problem, but it persists.  Is there any reason you are so opposed to using flash through esd?  What are the advantages of using aoss?  (I don't know too much about it, so even a nice doc to read would be appreciated).  Thanks

---

### Post by pizzach on 2005-12-15
[QUOTE=_jason]I was hoping that using aoss would resolve the lag problem, but it persists.  Is there any reason you are so opposed to using flash through esd?  What are the advantages of using aoss?  (I don't know too much about it, so even a nice doc to read would be appreciated).  Thanks[/QUOTE]

That no was a reply to what the quote was ahead of it.  With esd my flash laggs....bad.  With aoss I've never had my flash lag.  The one thing about linux is it seems different things work for different people.

Either that or I missed a step.  (>_<)  I did remove esd from my system because it seems firefox 1.5 was trying to auto to it instead of aoss.  Easiest way to try it out is a "killall esd" With no esd, firefox then defaults to alsa.  You can tell that happed because the lack of the ability to have two sounds at once.

---

### Post by pizzach on 2005-12-15
There.  Made the changes to my my short guide to reflect that esd is always first in line unless put in cement shoes in a far corner of the world.

---

### Post by jrib on 2005-12-16
[QUOTE=pizzach]There.  Made the changes to my my short guide to reflect that esd is always first in line unless put in cement shoes in a far corner of the world.[/QUOTE]


I had to kill esd.  The sync'ing in flash is so much better now.  It's not perfect, but I suspect that's because of flash itself.  I've uninstalled esd and I'm telling all my programs to use alsa.  Thank you.

In case anyone else uses this and notices that their sound in flash is really low, you can double click on the volume applet and raise the PCM volume.

---

### Post by ghostdog on 2005-12-18
[QUOTE=Jagunço]Hi folks.

I´ve downloaded and installed FF 1.5 by hand, and there´s no firefoxrc around. How can I fix this sound problem?

Thanks in advance.[/QUOTE]

I was having the same problem, I did try using $aoss firefox , but if I go to a website such as [www.cartoonnetwork.com](www.cartoonnetwork.com), firefox completely freezes.

Anybody had any luck running firefox through arts? Maybe tweaking the firefox script to run "artsdsp -m firefox-bin" ?

---

