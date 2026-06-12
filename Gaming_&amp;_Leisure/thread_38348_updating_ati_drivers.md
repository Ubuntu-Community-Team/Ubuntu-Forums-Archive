---
title: "updating ati drivers"
date: 2005-05-31
forum: Gaming &amp; Leisure
---

### Post by veelivar on 2005-05-31
sorry to ask this stuptid question but I'm quite new to linux in general.

I want to update my graphics drivers as I'm only getting ~380 fps from glxgrears (9800 pro should be more methinks).

I've seen plenty of threads with this snippet in
```
sudo apt-get install linux-restricted-modules-<your-kernel-version> xorg-driver-fglrx
``` 

I belive that this gets the latest ati drivers from the ubuntu repository, is this correct?

and most importantly what do I put in <your-kernal-version>?  I've just installed Hoary streight from cd.  

Cheers in advance,
Dan.

---

### Post by BKonkle on 2005-05-31
I followed the directions for my Radeon 9200 with that snippet of code in it, and the directions worked flawlessly.  For me, I ignored the "linux restricted modules" bit and just typed in the following command:

```
sudo apt-get install xorg-driver-fglrx
```

It worked like a dream.

I have the ubuntuforum backport repositories mirror enabled in my sources.list, as well as the marillat testing repositories.  To see how to enable those, see [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories).  I'm not entirely certain that you have to have those enabled to get the fglrx driver, but just in case there you have it.   :smile:

---

### Post by veelivar on 2005-05-31
Cheers I'll try that tonight.

I did see the line you suggested and tried it (and thought it had worked, but what do I know?) I then did the xconf change. but when I did the command to see what driver it was it still said the mesa driver.  I don't think I had the extra repostiry in there though so that could be it.

Oh anyone have any idea why the driver is called fglrx?  rather than ati?

Dan.

---

### Post by BKonkle on 2005-05-31
I followed this howto and it worked like a dream:

[http://ubuntuforums.org/showthread.php?t=24557&highlight=ati+howto](http://ubuntuforums.org/showthread.php?t=24557&highlight=ati+howto)

The important part to getting your driver switched over from the mesa is the line in your xorg.conf file that looks like this:

```
Section "Device"
  Identifier "ATI"
  Driver     "ati"
```

I changed mine to show this:

```
Section "Device"
  Identifier "ATI"
  Driver     "fglrx"
```

Go to [this site](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#install) and look at section 5.  Make the changes to your xorg.conf file that he suggests, and you should be in good shape.

Good luck!

---

### Post by veelivar on 2005-06-01
Cheers,

I got it working in the end.  I'd messed about so much I reinstalled ubuntu (probably unnecessary I know but I'm just getting to grips with this).

Then followed the stop x download to the letter (I had a tick list) and it worked I relaised when booting up that my kernel was 2.6.10-5-386 so used the restricted module thing, I don't know if it helped. 

On thing I did notice was that the order of the Load's on Module mattered.  I started of by having GLCore, glx, dri and sucection extmod (yadda) at the top but it wouldn't restert x.  I moved them to the bottom of the list and it worked.

Any way thanks,
Dan.

---

### Post by BKonkle on 2005-06-01
I didn't realize that was important, but I guess it was.  I started out by putting all those at the bottom and not the top, so I never had any problems.  I guess it has to load a few other drivers before it can load the fglrx stuff.

I'm glad you got it working!  Now, if only I could figure out how to get my framerate higher. . .

---

