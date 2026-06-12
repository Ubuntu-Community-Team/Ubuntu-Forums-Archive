---
title: "CTL font display (Thai) messed up"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Timokl on 2006-08-27
Hi,

anyone who managed to set up Thai fonts to work in Dapper correctly? In Dapper I can't seem to get the fonts right which worked good with Breezy.

The Problem: Thai is a language with Complex Text Layout (CTL) - the vowels are written on all four sides of a consonant: Some vowels are written on top of the preceding consonant, some before, some under, and some - believe it or not - behind the consonant. And in addition, Thai also has tone markers which are written on top of everything - so in some cases three letters which are entered consecutively on the keyboard have to be displayed above each other.

However, I have installed all Thai packages (apart from ThaiLaTeX), but the display of Thai text is quite messy. In Firefox some pages like [http://www.sanook.com](http://www.sanook.com) look ok, but some are messed up. See the two attached screenshots for reference. The correct screenshot was taken from [http://www.ethaimusic.com/lyrics/225.htm]("http://www.ethaimusic.com/lyrics/225.htm") and the incorrect one by copying the same text into an editor window from ubuntuforums.org.

Also: OpenOffice.org makes problems with Thai, too when I mix western and thai fonts in one document.

How managed to make Thai work correctly in Ubuntu Dapper? And how did you manage to do it?

Bye,
Timo

---

### Post by Timokl on 2006-08-28
No Thai Linux experts online? I would really appreciate any kind of help!!!

---

### Post by museum_geek on 2006-08-29
I'm having tha same problem...Thai fonts wouldn't display correctly anywhere.  Any help would be appreciated.

Thanks.

---

### Post by Timokl on 2006-08-30
hey museum-geek,

I already found it that it's a problem of the used fonts. Did you install the following packages already?
[LIST]xfonts-thai-ttf[/LIST]
[LIST]ttf-thai-tlwg[/LIST]

Then you have to set up one of these fonts to be used as "System Font". I chose "Garuda", a TrueType font by NECTEC, which also doesn't look too bad for western text. But honestly, Bitstream Vera Sans looks much better for western script. :rolleyes: 

You can find a list of all available ubuntu packages for Thai here: [http://packages.ubuntu.com/cgi-bin/search_...l&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=Thai&searchon=name&subword=1&version=all&release=all")

Then you can simply install with Synaptic or apt-get.

Do you also stay in Bangkok?

&#3610;&#3657;&#3634;&#3618;&#3654; :) 
Timo

---

### Post by jrz on 2006-10-14
Anyone able to explain how to be able to type Thai in OpenOffice.org Word processor? No matter what we cannot get a Thai character to appear, I have read everything and cannot find any mentioned packages missing, but obviously something is not set up properly. I assume there should be a hot key to toggle between English and Thai but have not discovered one yet. Can anyone help to get this working? We would appreciate it greatly.

---

### Post by jrz on 2006-10-14
Never Mind, I finally stumbled onto what I needed to do and got it to switching between languages easily.

---

### Post by jrz on 2006-10-14
If the problem referred to in the original post here is that the Thai characters typed don't match the keys struck on the keyboard, I had that problem and found it to be due to having defined the keyboard to be Thailand Patachote, and switching it to Thailand TIS-820.2538 corrected the problem.

---

### Post by Timokl on 2006-11-19
There is also a bug report on this.

[https://launchpad.net/distros/ubuntu/+source/thai-system/+bug/30528](https://launchpad.net/distros/ubuntu/+source/thai-system/+bug/30528)

---

### Post by paark.s on 2007-04-16
Hi,
   I am using Thai but seems to have no problem. What i've done is I set every to use LOMA from the system to the applications.

try LOMA, it might help.

---

### Post by enlightened on 2007-04-16
Hi! i wonder if you could try this;
$ apt-get install libthai0 pango-libthai

---

### Post by Timokl on 2007-04-17
> **paark.s said:**
> Hi,
   I am using Thai but seems to have no problem. What i've done is I set every to use LOMA from the system to the applications.

try LOMA, it might help.

Loma is good for Thai. But my first language is German which I have set on Ubuntu. And in German we have [some special characters]("http://de.wikipedia.org/wiki/Umlaut") - ä, ö, ü, ß - that look awkward with Loma.

What works quite well for both languages is the DejaVu font family.

&#3586;&#3629;&#3610;&#3588;&#3640;&#3603;&#3609;&#3632;&#3588;&#3619;&#3633;&#3610; :KS 

Timo

---

### Post by Timokl on 2007-04-17
> **enlightened said:**
> Hi! i wonder if you could try this;
$ apt-get install libthai0 pango-libthai

Hey, I thought I had everything installed that has something to do with processing Thai text, but it seems I missed pango-libthai. Thnx for pointing me to there.

Bye,
Timo

---

