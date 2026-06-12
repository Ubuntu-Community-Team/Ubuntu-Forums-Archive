---
title: "Firefox font suddenly ugly"
date: 2009-09-15
forum: Desktop Environments
---

### Post by SirSigma on 2009-09-15
I installed kubuntu-desktop on my Ubuntu configuration this weekend following instructions to get KDE 4.3. I have to say I love it so far, except for one thing that's bothering me now.

Earlier I was changing my color schemes since I used synaptic to install some KDE stuff like themes and emoticons, and to get them working completely I restarted Firefox a few times. That's when I noticed on the usual sites I started visiting where the font seemed to get smaller and uglier. It doesn't seem to affect every site, but I really hate it and I want my font back to however it was before.

I've tried so much to get my fonts working. I've reset all my appearance settings to default. I've searched for solutions that did nothing. I reinstalled the mstcorefonts or whatever they were. I can't find a solution that works. Can somebody help me?

---

### Post by dumblebee100 on 2009-09-15
> **SirSigma said:**
> I installed kubuntu-desktop on my Ubuntu configuration this weekend following instructions to get KDE 4.3. I have to say I love it so far, except for one thing that's bothering me now.

Earlier I was changing my color schemes since I used synaptic to install some KDE stuff like themes and emoticons, and to get them working completely I restarted Firefox a few times. That's when I noticed on the usual sites I started visiting where the font seemed to get smaller and uglier. It doesn't seem to affect every site, but I really hate it and I want my font back to however it was before.

I've tried so much to get my fonts working. I've reset all my appearance settings to default. I've searched for solutions that did nothing. I reinstalled the mstcorefonts or whatever they were. I can't find a solution that works. Can somebody help me?

I think you are feeling the effect of anti aliasing in firefox menus ..

because firefox from 3.5 and after do not take settings from general settings ...

edit the file

/etc/fonts/conf.avail

10-antialias.conf

change anti alias from TRUE to false

now enjoy firefox with crisp fonts

---

### Post by SirSigma on 2009-09-15
> **dumblebee100 said:**
> I think you are feeling the effect of anti aliasing in firefox menus ..

because firefox from 3.5 and after do not take settings from general settings ...

edit the file

/etc/fonts/conf.avail

10-antialias.conf

change anti alias from TRUE to false

now enjoy firefox with crisp fonts
Thanks for the reply. I just tried this using gksudo kate and I don't see a real difference anywhere. The usual sites I go to still have ugly compressed font. Or am I supposed to restart the desktop to see the effects?

Also, I confirmed just yesterday that this was affecting Firefox 3.5 on GNOME as well, so I guess it's not a specific problem for KDE like I originally though.

---

### Post by dumblebee100 on 2009-09-15
> **SirSigma said:**
> Thanks for the reply. I just tried this using gksudo kate and I don't see a real difference anywhere. The usual sites I go to still have ugly compressed font. Or am I supposed to restart the desktop to see the effects?

Also, I confirmed just yesterday that this was affecting Firefox 3.5 on GNOME as well, so I guess it's not a specific problem for KDE like I originally though.

why dont u post a screenshot so that people answering may understand easily

---

### Post by SirSigma on 2009-09-15
> **dumblebee100 said:**
> why dont u post a screenshot so that people answering may understand easily

I'm trying to now but for some reason my prtsc sysrq key doesn't seem to be working right now. :confused:

Anyway, I'm starting to think this just has to do with me using the newest Firefox. Maybe it would be better for me to rollback to at least an earlier version of 3.5.

EDIT: I switched over to GNOME and my prtsc sysrq key works here. Here's a screenshot of the menu bar font change, which stands out most and is just really ugly. Also, I've tried changing fonts in Firefox and I see no change.

[http://img524.imageshack.us/img524/2862/screenshotzk.png](http://img524.imageshack.us/img524/2862/screenshotzk.png)

---

### Post by SirSigma on 2009-09-15
OH YES I forgot to mention a strange but possibly very important detail. I have a new application called Shiretoko Web Browser installed from when I updated to 3.5.3. How do I get rid of that?

SUCCESS!!!!! YES YES YES! I just deleted the fonts.conf file or whatever it was and restarted Firefox. Now it's looking great!

EDIT: False alarm. It looks fine in GNOME, but when I logged off and went into KDE it seemed to revert back. :(

Can somebody help me figure out why it works fine in GNOME but not KDE? I think GNOME is alright but I really like KDE and I don't want to give it up.

---

### Post by dumblebee100 on 2009-09-15
> **SirSigma said:**
> OH YES I forgot to mention a strange but possibly very important detail. I have a new application called Shiretoko Web Browser installed from when I updated to 3.5.3. How do I get rid of that?

SUCCESS!!!!! YES YES YES! I just deleted the fonts.conf file or whatever it was and restarted Firefox. Now it's looking great!

EDIT: False alarm. It looks fine in GNOME, but when I logged off and went into KDE it seemed to revert back. :(

Can somebody help me figure out why it works fine in GNOME but not KDE? I think GNOME is alright but I really like KDE and I don't want to give it up.

I think so that fonts.conf is just for gtk rendering ..I hope there should be some other file where the kde rendering depends ..

anyways tell me which file did u delete ...and give me location of it ...

because I also use shiretoko browser and after disabling anti aliasing I got good crisp font ..because I use tahoma for my application font ..

dont just delete files like that ..you should know what you are doing otherwise you may run into problems ....atleast you should backup it ..

I get the crisp font on every gnome application because I have a file which tells every gnome application to use this font 
in file 

~/.gtkrc.mine

```
style "user-font"
{
  fontset="-microsoft-tahoma-medium-r-normal-*-10-*-*-*-p-*-*"
}
widget_class "*" style "user-font"

```

---

### Post by SirSigma on 2009-09-16
I just tried changing that file, only it was titled gtkrc-2.0-kde4

After I saved the change, I restarted Firefox and saw no difference.:(

But after quickly cutting and pasting the file to my desktop and starting Firefox again, I saw a change in interface for the worse, meaning that this file actually has an effect on Firefox under KDE. I think I may be close.

Also, I've been searching the internet for the past few days for a solution, but everything I find only works for GNOME.

---

### Post by theZoid on 2009-09-16
> **SirSigma said:**
> I just tried changing that file, only it was titled gtkrc-2.0-kde4

After I saved the change, I restarted Firefox and saw no difference.:(

But after quickly cutting and pasting the file to my desktop and starting Firefox again, I saw a change in interface for the worse, meaning that this file actually has an effect on Firefox under KDE. I think I may be close.

Also, I've been searching the internet for the past few days for a solution, but everything I find only works for GNOME.

In KDE, you gone into settings and set your dpi to 96, turned on AA and chosen your fonts, etc?

---

### Post by DrKay on 2009-10-07
I looked at your screenshot. It looks like your anti-aliasing got turned off when you opened Firefox in KDE. The same thing happened to me when I installed KDE on my Ubuntu 9.04 machine to try KDE. I love the KDE desktop, but had to return to GNOME GNOME because of trackpad issues inder KDE. To my horror, the fonts in Firefox look terrible without anti-aliasing. I can't get it to switch back either. There must be a configuration file somewhere. . .

---

### Post by Capa Pinbacker on 2009-10-30
> **dumblebee100 said:**
> I think you are feeling the effect of anti aliasing in firefox menus ..

because firefox from 3.5 and after do not take settings from general settings ...

edit the file

/etc/fonts/conf.avail

10-antialias.conf

change anti alias from TRUE to false

now enjoy firefox with crisp fonts

Thanks!  That worked for me when upgrading from 9.04 to 9.10.  Sweet.

---

### Post by Marrkk on 2009-10-31
i know this is'nt gonna be much help, but Firefox is a GTK app :(
and KDE 4x has a 'QT4-gtk engine' which can help GTK apps fit in to KDE but sadly, it screws Firefox.. at least it used to in Jaunty.. by not shutting Firefox, resulting in a 'firefox is already runng' type of error :(
good job Konqueror is actually really quite good in Karmic .. :)

---

### Post by ~unknown on 2009-10-31
Umm, is it possible to make Firefox use the "best contrast" option? Or something? I don't like full antialiasing, but don't want to disable it either... :(

---

### Post by Zorael on 2009-10-31
I don't get how the fonts are supposed to look? That looks pretty good to me, it's how I have it set up.

If it's still wrong after setting GTK apps to use the KDE font (in System Settings -> Appearance -> GTK Styles), you'll probably want to set up your own **~/.fonts.conf**. You can set up fonts and antialiasing as you please in there. Those settings will override those in /etc/fonts/conf.d/*.

Example of my **~/.fonts.conf** (typo remedied):
```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>

<fontconfig>

  <!-- GENERAL OPTIONS
    -->
  <match target="font">
    <edit mode="assign" name="rgba">		<!-- subpixel rendering color order -->
      <const>rgb</const>
    </edit>
  </match>
  <match target="font">
    <edit mode="assign" name="antialias">	<!-- antialiasing -->
      <bool>true</bool>
    </edit>
  </match>
  <match target="font">
    <edit mode="assign" name="autohint">	<!-- autohinting -->
      <bool>false</bool>
    </edit>
  </match>
  <match target="font">
    <edit mode="assign" name="hinting">		<!-- hinting -->
      <bool>true</bool>
    </edit>
  </match>
  <match target="font">
    <edit mode="assign" name="hintstyle">	<!-- style of hinting: hintfull/hintmedium/hintslight/hintnone -->
      <const>hintfull</const>
    </edit>
  </match>
  <match target="font">
    <edit mode="assign" name="embeddedbitmap">	<!-- font bitmaps, mainly for unicode purposes -->
      <bool>true</bool>
    </edit>
  </match>


  <!-- FONT REPLACEMENT
	Some fonts look positively ugly so changing them to the virtual sans-serif, sans and monospace
    -->
  <!-- serif -->
  <match target="pattern">
    <test name="family" qual="any">
      <string>Times</string>
    </test>
    <edit mode="assign" name="family">
      <string>serif</string>
    </edit>
  </match>
  <match target="pattern">
    <test name="family" qual="any">
      <string>Nimbus Roman No9 L</string>
    </test>
    <edit mode="assign" name="family">
      <string>serif</string>
    </edit>
  </match>

  <!-- sans-serif -->
  <match target="pattern">
    <test name="family" qual="any">
      <string>Bitstream Vera</string>
    </test>
    <edit mode="assign" name="family">
      <string>sans-serif</string>
    </edit>
  </match>
  <match target="pattern">
    <test name="family" qual="any">
      <string>Bitstream Vera Sans</string>
    </test>
    <edit mode="assign" name="family">
      <string>sans-serif</string>
    </edit>
  </match>
  <match target="pattern">
    <test name="family" qual="any">
      <string>Helvetica</string>
    </test>
    <edit mode="assign" name="family">
      <string>sans-serif</string>
    </edit>
  </match>
  <match target="pattern">
    <test name="family" qual="any">
      <string>Nimbus Sans L</string>
    </test>
    <edit mode="assign" name="family">
      <string>sans-serif</string>
    </edit>
  </match>

  <!-- monospace -->
  <match target="pattern">
    <test name="family" qual="any">
      <string>Bitstream Vera Sans Mono</string>
    </test>
    <edit mode="assign" name="family">
      <string>monospace</string>
    </edit>
  </match>
  <match target="pattern">
    <test name="family" qual="any">
      <string>Courier</string>
    </test>
    <edit mode="assign" name="family">
      <string>monospace</string>
    </edit>
  </match>
  <match target="pattern">
    <test name="family" qual="any">
      <string>Nimbus Mono L</string>
    </test>
    <edit mode="assign" name="family">
      <string>monospace</string>
    </edit>
  </match>


  <!-- VIRTUAL FONTS
	The font order which makes up the virtual fonts serif, sans-serif and monospace.
	In Karmic, will follow each font for further fallbacks (defined below and in other fonts/conf.d/ files)
    -->
  <alias>
    <family>serif</family>
    <prefer>
      <family>Times New Roman</family>		<!-- main serif font -->
      <family>Kochi Mincho</family>
    </prefer>
  </alias>
  <alias>
    <family>sans-serif</family>
    <prefer>
      <family>Arial</family>
      <family>DejaVu Sans</family>		<!-- main sans-serif font -->
      <family>Kochi Gothic</family>
    </prefer>
  </alias>
  <alias>
    <family>monospace</family>
    <prefer>
      <family>DejaVu Sans Mono</family>		<!-- main monospace font -->
      <family>Kochi Gothic</family>
    </prefer>
  </alias>


  <!-- FALLBACKS
      Mainly for unicode purposes; as soon as a font doesn't contain a character, it'll try with the next one on this list
    -->
  <alias>
    <family>Times New Roman</family>
    <prefer>
      <family>Times New Roman</family>
      <family>Kochi Mincho</family>
      <family>Sazanami Mincho</family>
    </prefer>
  </alias>

  <alias>
    <family>Arial</family>
    <prefer>
      <family>Arial</family>
      <family>Kochi Gothic</family>
    </prefer>
  </alias>

  <alias>
    <family>DejaVu Serif</family>
    <prefer>
      <family>DejaVu Sans</family>
      <family>Kochi Mincho</family>
    </prefer>
  </alias>

  <alias>
    <family>DejaVu Sans</family>
    <prefer>
      <family>DejaVu Sans</family>
      <family>Kochi Gothic</family>
    </prefer>
  </alias>

  <alias>
    <family>DejaVu Sans Mono</family>
    <prefer>
      <family>DejaVu Sans Mono</family>
      <family>Kochi Gothic</family>
    </prefer>
  </alias>

  <alias>
    <family>Courier New</family>
    <prefer>
      <family>Courier New</family>
      <family>Kochi Gothic</family>
    </prefer>
  </alias>

</fontconfig>
```
Do note that it's set up to use Times New Roman for the Serif virtual font, DejaVu Sans for Sans-serif and DejaVu Sans Mono for Monospace. Also the Kochi series of fonts for unicode fallback, to get good unicode bitmap coverage so CJK (Chinese/Japanese/Korean) fonts aren't drawn as fuzzy vertexes at lower font sizes (<17).

If you don't have those installed it'll just listen to system-specific /etc/fonts/conf.d/* files. Saving this file should make changes apply immediately to newly started programs (and reloaded Firefox pages).

---

### Post by denk_mal on 2009-11-03
Hi,

the problem semms to be the missing font "Bitstream Vera".
It has been removed silenty without any replacements by Ubuntu.
(Anybody knows why? :confused:)

If you using old config stuff (on upgrade) every application using this font
looks very ugly. Especially if it using a monospace font of Bitstream Vera.

You can simply install it from launchpad _[https://launchpad.net/ubuntu/karmic/+source/ttf-bitstream-vera/1.10-7](https://launchpad.net/ubuntu/karmic/+source/ttf-bitstream-vera/1.10-7)_ or replace the fontsetting for every application by another font.
(and again: does anybody knows the official replacement font for Bitstream Vera?)
[COLOR=Red]EDIT: [/COLOR]I found the answer for the second question here: [https://issues.foresightlinux.org/browse/FL-370](https://issues.foresightlinux.org/browse/FL-370)

denk_mal

---

### Post by =NickJ= on 2009-11-05
Its pretty clear there is a difference of opinion here! Going on what everyone has said dumblebee, Capa Pinbacker and Zorael all view having anti-aliasing off as the desired outcome, whereas SirSigma was saying his fonts looked screwed because the AA got turned off and he wants it back on.

DrKay remove the file ~/.fonts.conf (thanks SirSigma), I just did and everything is back in its antialiased beauty again :D

---

### Post by Zorael on 2009-11-06
> **=NickJ= said:**
> Its pretty clear there is a difference of opinion here! Going on what everyone has said dumblebee, Capa Pinbacker and Zorael all view having anti-aliasing off as the desired outcome, whereas SirSigma was saying his fonts looked screwed because the AA got turned off and he wants it back on.

DrKay remove the file ~/.fonts.conf (thanks SirSigma), I just did and everything is back in its antialiased beauty again :D
To be specific, I was trying to make him check the contents of his ~/.fonts.conf file to see if they were forcing any undesired settings. It's not a binary blob, it's humanly readable if you read the tags and do a bit of guesswork. :3

---

### Post by nortexoid on 2010-01-25
> **=NickJ= said:**
> Its pretty clear there is a difference of opinion here! Going on what everyone has said dumblebee, Capa Pinbacker and Zorael all view having anti-aliasing off as the desired outcome, whereas SirSigma was saying his fonts looked screwed because the AA got turned off and he wants it back on.

DrKay remove the file ~/.fonts.conf (thanks SirSigma), I just did and everything is back in its antialiased beauty again :D

That worked to get antialiased fonts for certain application elements (like the menus, etc.) but it didn't work for getting them in rendered web pages. Weird.

Has anyone successfully gotten antialiased fonts for web pages content? I have the DejaVu family set as my fonts with pages not allowed to choose their own fonts.

I should add that antialiasing works fine in Chromium!

---

### Post by Zorael on 2010-01-25
> **nortexoid said:**
> That worked to get antialiased fonts for certain application elements (like the menus, etc.) but it didn't work for getting them in rendered web pages. Weird.

Has anyone successfully gotten antialiased fonts for web pages content? I have the DejaVu family set as my fonts with pages not allowed to choose their own fonts.

I should add that antialiasing works fine in Chromium!
Could you post a screenshot that shows antialiased and non-antialiased text?

I think you're referring to non-full hinting.

---

### Post by Cloink on 2011-05-17
Zorael, 31/10/09, this works -- note filename INCludes the dot, ie.    "~/.fonts.conf" -- Zorael's post one time includes it, one time omits   it.

    Trial and error with exactly how to combine the settings.   For me:
anti-aliasing=false
autohint=false
hinting=true
hintstyle=hintfull

When you've changed a setting, a second or two later, you'll notice some applications re-render with the new settings.

Without being able to do a side-by-side comparison, this now looks just    like Windows with ClearType turned off.  Except not brilliant in    Terminal.  F/fox, Rythmbox, and TextPad, a Wine/Windows text editor, all   brilliantly crisp.

    You need to restart F/fox for the settings to take effect across the    board, eg. in menus & address bar; or just F5/refresh your web    page for the document window to pick up the new settings, if it hasn't   already.

Cloink.

---

