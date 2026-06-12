---
title: "My easy suggestions for speeding up your Xubuntu"
date: 2009-07-19
forum: Desktop Environments
---

### Post by stozi on 2009-07-19
If you use xubuntu you probably have limited hardware resources and/or a desire for speed. Personally, I have a 1Ghz CPU and a 4Gig hard drive. The default install of Xubuntu works well, but leaves room for improvement in resource use. I'm no guru, but I thought I'd share what I've done to reduce my OS heft with anyone who might not know these options.

Xubuntu gives you some programs that are default in Ubuntu but have lighter, faster and I'd say just as usable alternatives. I traded:

Totem for Xfmedia
Ristretto for Gpicview 
Evince for Epdfviewer
gnome system monitor for Xfce taskmanager

I suppose if you have very limited image altering needs you could go for gpaint instead of gnome.

I installed Midori which is smaller and faster than firefox but too beta to do any javascript or ajax without crashing.

Other than that, I go through synaptic and remove all the programs which're obviously for something I never do, like deal with optical drives, screensavers, or gnumeric. I leave the ones that xubuntu-desktop relys on just for less headache at update time. Then I use deborphan, sudo apt-get autoclean & sudo apt-get autoremove to ensure nothing's left over.

If you go to Synaptic, select "installed" then order the packages by clicking on "size." you may notice that right up top, just smaller than linux-headers-2.6 are some help packs for openoffice, which is not installed in xubuntu by default. They are the dependancies of a meta-package, language-support-translations-en, which provides a few huge, I'd say useless help packages: 

openoffice.org-help-en-gb
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
thunderbird-locale-en-gb
gimp-help-en
evolution-documentation-en

My OS is on it's own drive with no personal files. It takes up under 2Gb, though everything I removed are somewhat counterbalanced by non-default packages that I need, like Openoffice Impress (please, please, someone make a gnome office ppt ap!), soundconverter, scim with chinese language support (ouch), and stardict.

So there you go. This is the bulk of my linux wisdom.

---

### Post by kerry_s on 2009-07-19
you should do a base install with xfce4, far easier to get it where you want from the get go.

i use xfce4 on a base debian testing install, with almost the same programs you suggest. my system is 450mhz 256mb ram.

my media = gnome-mplayer
monitor = htop

---

### Post by stozi on 2009-07-19
I've thought about it. Going through every package installed does take a while but isn't really necessary, but other than that, I'm not sure a fresh install really would be easier... I am planning on trying puppy though. 

If one were really serious about performance one could do away with xfce altogether in favour of, say, jwm. Admittedly I have raided xfce-look.org, taking up quite a bit more drive space, but hey, I don't want people looking over my shoulder thinking Linux is primitive.

---

### Post by kerry_s on 2009-07-19
sorry, i just got up & running. i switched to a 64bit install. 

> I don't want people looking over my shoulder thinking Linux is primitive

:lolflag: you would think most people, would think it was more advanced instead. i use to use jwm, but i felt like a change so i'm using xfce.

---

### Post by stozi on 2009-07-19
I wasn't sniding your screenshot mate. It's just when I've stepped too far from defaults things haven't looked as shiny as OS X or Vista, largely my own fault. I agree that under the hood Linux is more advanced and versitile. I think it's good to prove to new people that Linux can surpass MS or OS X in every way, particularly in the first things they see; people get stuck on superficiality.

---

### Post by stozi on 2009-07-26
I have also changed to Wicd, which is quite a bit smaller than network-manager.

---

### Post by kerry_s on 2009-07-26
> **stozi said:**
> I have also changed to Wicd, which is quite a bit smaller than network-manager.

you can skip a network manager & just set your settings in /etc/network/interfaces if you don't need wireless roaming around.
if your just plugged in, you don't need a manager at all.
if you must have a gui, try wifi-radar or network-config, both lighter than wicd & they have no running daemon to continue sucking up resources.

---

### Post by ugm6hr on 2009-07-26
I found xfmedia to not load after the first time I used it...

I suggest xine-ui myself for lightweight media...

---

### Post by stozi on 2009-07-27
interesting, kerry_d, those are much smaller still. The daemon doesn't do anything important?

xfmedia works fine for me... will look at xine though.

---

### Post by kerry_s on 2009-07-27
> **stozi said:**
> interesting, kerry_d, those are much smaller still. The daemon doesn't do anything important?

xfmedia works fine for me... will look at xine though.

no, not really, most of what the network daemon does is built in now a days.

dump the xine players, there just plain slow. instead use:
gnome-mplayer
gecko-mediaplayer
w32codecs

with those you'll play damn near everything in or out of the browser & it's faster & lighter. i use that on my 450mhz 256mb ram, i can watch movies in full screen, which is what i'm about to do. :D

---

### Post by stozi on 2009-07-27
Interesting, *kerry_s*. 

I tried wifi-radar, and although it connected to the router, I couldn't load any webpage. Slightly beyond my skill level I guess.

---

