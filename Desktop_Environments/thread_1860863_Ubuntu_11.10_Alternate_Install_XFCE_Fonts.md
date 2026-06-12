---
title: "Ubuntu 11.10 Alternate Install XFCE Fonts"
date: 2011-10-15
forum: Desktop Environments
---

### Post by melodosgr on 2011-10-15
Hello everyone.

I've used the Alternate install, cause I really can't bother with Unity and so many apps that I don't really need. I am a pure "debian guy" who uses simply apt-get to install software and I really love the ubuntu repos and especially the way ubuntu is rendering the fonts. I can't really get the same results when I am installing apt-get install xfce4 on my ubuntu clean system. Can someone tell me how to improve the rendering? Should I simply try to install xubuntu desktop instead? I really hate it though, as I don't want to have gdm. I would rather have startx..

Thanks!

---

### Post by mips on 2011-10-15
> **melodosgr said:**
> Hello everyone.

I've used the Alternate install, cause I really can't bother with Unity and so many apps that I don't really need. I am a pure "debian guy" who uses simply apt-get to install software and I really love the ubuntu repos and especially the way ubuntu is rendering the fonts. I can't really get the same results when I am installing apt-get install xfce4 on my ubuntu clean system. Can someone tell me how to improve the rendering? Should I simply try to install xubuntu desktop instead? I really hate it though, as I don't want to have gdm. I would rather have startx..

Thanks!

I also did a alternate base install + xubuntu-desktop and xubuntu settings etc etc but my fonts still look crap.

xubuntu-desktop does not use gdm, it uses lightdm which in my cse also does not work...


EDIT: I changed my font settings to this, crisp & clear
[IMG]http://ompldr.org/vYXRsdw/Screenshot%20-%2015102011%20-%2017:57:54.png[/IMG]

Play around with the sub-pixelorder as you get different results depending on your lcd panel.



.

---

### Post by melodosgr on 2011-10-17
> **mips said:**
> I also did a alternate base install + xubuntu-desktop and xubuntu settings etc etc but my fonts still look crap.

xubuntu-desktop does not use gdm, it uses lightdm which in my cse also does not work...


EDIT: I changed my font settings to this, crisp & clear
[IMG]http://ompldr.org/vYXRsdw/Screenshot%20-%2015102011%20-%2017:57:54.png[/IMG]

Play around with the sub-pixelorder as you get different results depending on your lcd panel.



.

Thanks, but you're running xubuntu-desktop and probably everything works as it should, but it's not the same when using XFCE. Any other suggestions anyone???

---

### Post by gsmanners on 2011-10-17
Since you're doing your own thing with startx, maybe [fontconfig]("http://en.wikipedia.org/wiki/Fontconfig") is what you need.

---

### Post by melodosgr on 2011-10-17
> **gsmanners said:**
> Since you're doing your own thing with startx, maybe [fontconfig]("http://en.wikipedia.org/wiki/Fontconfig") is what you need.

Thanks for you reply.. I also thought that this might be the solution but I am not sure what to do exactly to get the same font settings as the once provided with Ubuntu-desktop. Could you please describe me the steps?

Thanks!

---

### Post by gsmanners on 2011-10-17
I haven't messed with that in a while. I suppose you could just try different things in your ~/.fonts.conf

This was the last one I did ( back in August 2008 ):

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

 <alias>
 <family>serif</family>
 <prefer>
 <family>DejaVu Serif</family>
 <family>Times New Roman</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>Bitstream Vera Serif</family>
 <family>Thorndale AMT</family>
 <family>Luxi Serif</family>
 <family>Nimbus Roman No9 L</family>
 <family>Times</family>
 <family>Frank Ruehl</family>
 <family>MgOpen Canonica</family>
 <family>AR PL SungtiL GB</family>
 <family>AR PL Mingti2L Big5</family>
 <family>FreeSerif</family>
 <family>Baekmuk Batang</family>
 </prefer>
 </alias>

 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>DejaVu Sans</family>
 <family>Verdana</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans</family>
 <family>Arial</family>
 <family>Albany AMT</family>
 <family>Luxi Sans</family>
 <family>Nimbus Sans L</family>
 <family>Helvetica</family>
 <family>Nachlieli</family>
 <family>MgOpen Moderna</family>
 <family>AR PL KaitiM GB</family>
 <family>AR PL KaitiM Big5</family>
 <family>FreeSans</family>
 <family>Baekmuk Dotum</family>
 <family>SimSun</family>
 </prefer>
 </alias>

 <alias>
 <family>monospace</family>
 <prefer>
 <family>DejaVu Sans Mono</family>
 <family>Courier New</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans Mono</family>
 <family>Andale Mono</family>
 <family>Cumberland AMT</family>
 <family>Luxi Mono</family>
 <family>Nimbus Mono L</family>
 <family>Courier</family>
 <family>Miriam Mono</family>
 <family>FreeMono</family>
 <family>AR PL KaitiM GB</family>
 <family>Baekmuk Dotum</family>
 </prefer>
 </alias>

 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>false</bool>
 </edit>
 </match>

</fontconfig>
```

EDIT:

Oh yeah, plus this for ~/.Xdefaults:

```
Xft.antialias: 1
Xft.hinting: 1
Xft.hintstyle: hintslight
Xft.rgba: none
Xft.dpi: 100
```

You'll need to add

```
xrdb -load ~/.Xdefaults
```

to your .xinitrc of course. :D  Ah, fun times.

---

### Post by melodosgr on 2011-10-17
> **gsmanners said:**
> I haven't messed with that in a while. I suppose you could just try different things in your ~/.fonts.conf

This was the last one I did ( back in August 2008 ):

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

 <alias>
 <family>serif</family>
 <prefer>
 <family>DejaVu Serif</family>
 <family>Times New Roman</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>Bitstream Vera Serif</family>
 <family>Thorndale AMT</family>
 <family>Luxi Serif</family>
 <family>Nimbus Roman No9 L</family>
 <family>Times</family>
 <family>Frank Ruehl</family>
 <family>MgOpen Canonica</family>
 <family>AR PL SungtiL GB</family>
 <family>AR PL Mingti2L Big5</family>
 <family>FreeSerif</family>
 <family>Baekmuk Batang</family>
 </prefer>
 </alias>

 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>DejaVu Sans</family>
 <family>Verdana</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans</family>
 <family>Arial</family>
 <family>Albany AMT</family>
 <family>Luxi Sans</family>
 <family>Nimbus Sans L</family>
 <family>Helvetica</family>
 <family>Nachlieli</family>
 <family>MgOpen Moderna</family>
 <family>AR PL KaitiM GB</family>
 <family>AR PL KaitiM Big5</family>
 <family>FreeSans</family>
 <family>Baekmuk Dotum</family>
 <family>SimSun</family>
 </prefer>
 </alias>

 <alias>
 <family>monospace</family>
 <prefer>
 <family>DejaVu Sans Mono</family>
 <family>Courier New</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans Mono</family>
 <family>Andale Mono</family>
 <family>Cumberland AMT</family>
 <family>Luxi Mono</family>
 <family>Nimbus Mono L</family>
 <family>Courier</family>
 <family>Miriam Mono</family>
 <family>FreeMono</family>
 <family>AR PL KaitiM GB</family>
 <family>Baekmuk Dotum</family>
 </prefer>
 </alias>

 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>false</bool>
 </edit>
 </match>

</fontconfig>
```

EDIT:

Oh yeah, plus this for ~/.Xdefaults:

```
Xft.antialias: 1
Xft.hinting: 1
Xft.hintstyle: hintslight
Xft.rgba: none
Xft.dpi: 100
```

You'll need to add

```
xrdb -load ~/.Xdefaults
```

to your .xinitrc of course. :D  Ah, fun times.

I think that the issue here is about font smoothing. I don't have gnome so I guess I should take the manual configuration to make things work?

[https://wiki.ubuntu.com/Fonts#Font_Smoothing]("https://wiki.ubuntu.com/Fonts#Font_Smoothing")

---

### Post by gsmanners on 2011-10-17
Well, if you don't have a DM (gdm or lightdm), you pretty much have to do everything manually that applies to that session.

---

### Post by melodosgr on 2011-10-17
> **gsmanners said:**
> Well, if you don't have a DM (gdm or lightdm), you pretty much have to do everything manually that applies to that session.

So I guess the steps you described above should work fine? I'm just wondering which are the default xubuntu-desktop settings and if I could simply copy them to my XFCE installation.

---

### Post by PsyGeek on 2011-10-17
> **melodosgr said:**
> So I guess the steps you described above should work fine? I'm just wondering which are the default xubuntu-desktop settings and if I could simply copy them to my XFCE installation.

Xubuntu and ubuntu with XFCE are basically the same except for the artwork and the default applications, so if you want XFCE with xubuntu settings you just want to install xubuntu :).

To answer the question: you can install xubuntu-default-settings.

edit: I didn't see that you don't want lightDM. You could either try to install the dependencies of xubuntu-default-settings which don't force you to install lightdm, or install xubuntu and replace lightDM later.

---

### Post by melodosgr on 2011-10-17
> **PsyGeek said:**
> The Xubuntu and XFCE sessions are basically the same except for the artwork and the default applications, so if you want XFCE with xubuntu settings you just want to install xubuntu.

However: yes you can: Just install xubuntu-default-settings.

I was thinking about that as well. but wouldn't that pull all the libraries and artwork that xubuntu uses? I really love my ubuntu clean system and xubuntu-desktop uses more resources than a clean ubuntu with xfce installation.. Oh, well.. I'll give it a go.

---

### Post by gsmanners on 2011-10-17
> **melodosgr said:**
> So I guess the steps you described above should work fine? I'm just wondering which are the default xubuntu-desktop settings and if I could simply copy them to my XFCE installation.

FWIW, the defaults for Xubuntu are in /etc/xdg/xdg-xubuntu (from the package xubuntu-default-settings).

EDIT: Oh, and the steps I described worked for me. I don't think Xubuntu can work properly without some kind of DM (so you can't just copy the settings--you'd have to port them).

---

### Post by melodosgr on 2011-10-21
> **gsmanners said:**
> FWIW, the defaults for Xubuntu are in /etc/xdg/xdg-xubuntu (from the package xubuntu-default-settings).

EDIT: Oh, and the steps I described worked for me. I don't think Xubuntu can work properly without some kind of DM (so you can't just copy the settings--you'd have to port them).

I think that the answer I am looking for is the patching that Ubuntu is doing to it's fonts using some sort of smoothing for rendering for LCD Screens. How can I enable this feature in XFCE? There is only hinting and subpixel order..

[https://wiki.ubuntu.com/Fonts#Font_Smoothing]("https://wiki.ubuntu.com/Fonts#Font_Smoothing")

---

### Post by gsmanners on 2011-10-21
> **melodosgr said:**
> I think that the answer I am looking for is the patching that Ubuntu is doing to it's fonts using some sort of smoothing for rendering for LCD Screens. How can I enable this feature in XFCE? There is only hinting and subpixel order..

[https://wiki.ubuntu.com/Fonts#Font_Smoothing]("https://wiki.ubuntu.com/Fonts#Font_Smoothing")

I'm not sure what to make of the Gnome dialog. It looks misleading to me, considering that fontconfig doesn't really have the ability to do what it implies is possible (or maybe I'm looking at it wrong). Bleh. Xfce isn't Gnome (thank goodness).

In any case, I have no idea how you've decided to handle your desktop, so I have no advice for you. Sorry.

---

### Post by melodosgr on 2011-10-22
> **gsmanners said:**
> I'm not sure what to make of the Gnome dialog. It looks misleading to me, considering that fontconfig doesn't really have the ability to do what it implies is possible (or maybe I'm looking at it wrong). Bleh. Xfce isn't Gnome (thank goodness).

In any case, I have no idea how you've decided to handle your desktop, so I have no advice for you. Sorry.

Left: Xubuntu Default desktop Right: Ubuntu with XFCE. They both have their default settings and I fiddled with XFCE apperance tab too.. This sort of "blurriness" is what I'm looking for that is apparently enabled on both Ubuntu and Xubuntu distros.. God.. I really need to find this!!

[IMG]http://img23.imageshack.us/img23/5351/unledgvy.png[/IMG]

---

### Post by gsmanners on 2011-10-22
> **melodosgr said:**
> Left: Xubuntu Default desktop Right: Ubuntu with XFCE...

I don't see any difference (might just be my monitor).

---

