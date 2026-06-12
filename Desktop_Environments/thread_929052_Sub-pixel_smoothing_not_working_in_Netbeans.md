---
title: "Sub-pixel smoothing not working in Netbeans"
date: 2008-09-24
forum: Desktop Environments
---

### Post by sayeo87 on 2008-09-24
Hi, I'm having trouble getting sub-pixel smoothing working in NetBeans 6.1.

I can't stand the monospaced (or any other fonts) in Netbeans without sub-pixel smoothing and I was hoping somebody knows how to make it work.

Here's what I'm talking about:


**gedit (with smoothing)**
[IMG]http://web.ics.purdue.edu/~yeo/withSmoothing.png[/IMG]


**netbeans (without smoothing)**
[IMG]http://web.ics.purdue.edu/~yeo/withoutSmoothing.png[/IMG]


Thanks,
Suan

---

### Post by apere006 on 2009-07-28
I know this is an old thread but im having the same problem in netbeans 6.5. Any help will be apericated

---

### Post by hictio on 2009-07-28
Not sure, but... Are you using any other than RGB Sub-pixel order?
Perhaps this might help you: [Subpixel/Lcd mode with VRGB/VBGR makes qt4 applications on Jaunty unreadable](https://bugs.edge.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657)

---

### Post by Zorael on 2009-07-28
FWIW as terminology goes, the gedit image looks like it's using slight or medium hinting, whereas netbeans looks to be using full hinting. (And I *strongly* prefer the netbeans look (full hinting); gedit there just seems fuzzy.)

At any rate, have you tried making changes to your ~/.fonts.conf? Example;
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>true</bool>
 </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="**hinting**" >
   <bool>**true**</bool>
  </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="**hintstyle**" >
   <const>**hintfull**</const>
  </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```
I'm not sure netbeans obey GNOME's settings, but it just might obey .font.conf's. Change **hintfull** to **hintslight** or **hintmedium**, perhaps.

See [http://fontconfig.org/fontconfig-user.html](http://fontconfig.org/fontconfig-user.html) for more documentation, [http://www.kilobitspersecond.com/2009/04/17/ubuntu-font-hinting-you-a-cautionary-tale/](http://www.kilobitspersecond.com/2009/04/17/ubuntu-font-hinting-you-a-cautionary-tale/) for some examples, and [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) for the Ubuntu Wiki entry.

---

### Post by bjtuna on 2009-11-03
I'm having the same issue as the original post. Nothing I've tried has worked, including adding "-J-Dswing.aatext=true -J-Dawt.useSystemAAFontSettings=lcd" to netbeans_default_options in netbeans.conf. I'm using sun-java6 on Ubuntu 9.04, with Netbeans 6.8beta.

---

### Post by cm000000 on 2010-01-14
Have you get any advance in this matter? I've been googling and tryed sevareal changes (included yours) in configuration but i cant get antialias in netbeans 6.8.

Regards

---

### Post by Yellow Pasque on 2010-01-14
[http://wiki.archlinux.org/index.php/Java_Fonts_-_Sun_JRE](http://wiki.archlinux.org/index.php/Java_Fonts_-_Sun_JRE)

---

