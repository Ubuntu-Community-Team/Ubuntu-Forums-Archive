---
title: "Firefox issue with Zillow.com"
date: 2009-05-30
forum: General Help
---

### Post by notfound123 on 2009-05-30
I am running Firefox 3.0.10 (with Shockwave 9.0.r999 plug in) on Jaunty. I am having trouble with Zillow.com. Its search screen gives me an error (attached).  

How can I troubleshoot this problem? Any suggestions?

---

### Post by notfound123 on 2009-05-30
Anyone?

---

### Post by Wiebelhaus on 2009-05-30
double post , my bad.

---

### Post by Wiebelhaus on 2009-05-30
It's a pluin or addon  , try running firefox in safemode or without addons to begin the process of elimination. I'm not having any issues with the site with relatively the same setup so it's something localized and unique to your environment , I see your running flashblock , if your using adblock or no script , I'd start with those three.

Cheers , Not much we can do remotely for you.

---

### Post by notfound123 on 2009-05-30
Thanks so much for your help.

I ran it in a safe mode and got the following error:

Loading stream: [http://www.zillow.com/vstatic/17ae0d1100050a99400fa033f888c212/static/swf/ZillowMap.swf](http://www.zillow.com/vstatic/17ae0d1100050a99400fa033f888c212/static/swf/ZillowMap.swf)
SWFDEC: ERROR: swfdec_bitmap_data.c(146): swfdec_bitmap_data_loadBitmap: loadBitmap cannot find image with name balloons

Does this mean anything to you? What version of swfdec do you have? Mine is 0.8.2. Should I upgrade it? Thanks.

---

### Post by Wiebelhaus on 2009-05-30
> **notfound123 said:**
> Thanks so much for your help.

I ran it in a safe mode and got the following error:

Loading stream: [http://www.zillow.com/vstatic/17ae0d1100050a99400fa033f888c212/static/swf/ZillowMap.swf](http://www.zillow.com/vstatic/17ae0d1100050a99400fa033f888c212/static/swf/ZillowMap.swf)
SWFDEC: ERROR: swfdec_bitmap_data.c(146): swfdec_bitmap_data_loadBitmap: loadBitmap cannot find image with name balloons

Does this mean anything to you? Thanks.

Yes it does actually.

Someone may disagree with me and I'm not trying to insult anyone's hard work nor be an ingrate but the Free flash alternatives are crappy and don't work well at all in my experiences.

Do this:

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get remove swfdec-gnome
```

```
sudo apt-get remove swfdec-mozilla
```

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install w32codecs
```

```
sudo apt-get install flashplugin-nonfree
```

```
sudo apt-get install ubuntu-restricted-extras
```

Log out then log back in and retry that website , the flash plug in you are using is one of the open alternatives and it's malfunctioning.

All of this is a maintenance and full reinstall of all restricted extra's and flash.

Cheers.

by the way , the reason the are separated and not combined as one long easy command is so that you can easily watch for errors.

---

### Post by notfound123 on 2009-05-31
Works fine!!!! Thanks for your help!

---

### Post by dmemt on 2009-06-05
[SIZE=3][FONT=Verdana][SIZE=2]I recently got my online banking login to work in Firefox simply by removing the swfdec-mozilla package with Synaptic in Jaunty.

It appears the the swfdec package was keeping the "internal" Firefox Adobe swf plugin from running.

Symptoms included non-masking of the account and password fields, as well as the login failing.

Just thought I'd tack it on here in hopes of saving somebody else a bit of aggravation. :)[/SIZE]

Dana
[/FONT][/SIZE]

---

