---
title: "Use a Runic keyboard layout on Lubuntu 12.04"
date: 2012-05-14
forum: Desktop Environments
---

### Post by Lyfang on 2012-05-14
Good day,

I'm using Lubuntu 12.04 LTS and I would like to write Runes with a Runic keyboard layout. I found Thomas J. Webb’s Ecology Blog [http://thomaswebb.net/my-code/write-runes-on-your-computer/](http://thomaswebb.net/my-code/write-runes-on-your-computer/) (website is down right now)

However I was not able to change keyboard layout. Now you want to get these Runic letters, numerals & punctuations working with Linux
[SIZE=2]&#5792;&#5794;&#5798;&#5801;&#5809;&#5811;&#5815;&#5817;&#5819;&#5822;&#5825;&#5828;&#5831;&#5832;&#5833;&#5835;&#5839;&#5842;&#5846;&#5847;&#5850;&#5853;&#5855;&#5854;&#5802;&#5803;&#5795;&#5856;&#5857;&#5859;&#5860;&#5816;&#5858;&#5861;&#5793;&#5799;&#5838;&#5870;&#5871;&#5872;&#5867;&#5868;&#5869;[/SIZE]

My current BabelStone Runic keyboard layout on Windows 7
[SIZE=2]a&#5802; b&#5842; c&#5811; d&#5854; e&#5846; f&#5792; g&#5815; h&#5819; i&#5825; j&#5828; k&#5859; l&#5850; m&#5847; n&#5822; o&#5801; p&#5832; q&#5858; r&#5809;
s&#5835; t&#5839; u&#5794; w&#5817; x&#5833; y&#5795; z&#5861;[/SIZE]

Pressing down the Shift key
[SIZE=2]A&#5803; E&#5856; G&#5816; H&#5831; I&#5857; K&#5860; N&#5853; O&#5855; T&#5798;[/SIZE]

Runic numerals copied
[SIZE=2]&#5870;17
&#5871;18
&#5872;19[/SIZE]

Punctuations [SIZE=2]&#5867; &#5868; &#5869;[/SIZE]

Convert Latin alphabet to Runic alphabet
[http://heima.olivant.fo/~styrheim/tools/runes/convert.html]("http://heima.olivant.fo/%7Estyrheim/tools/runes/convert.html")
[http://www.furorteutonicus.eu/germanic/runescribe/index.php](http://www.furorteutonicus.eu/germanic/runescribe/index.php)
[http://www.alanyates.com/funstuff/runic.html](http://www.alanyates.com/funstuff/runic.html)

See also
Runes for Modern English/Spelling Reform? [http://ubuntuforums.org/showthread.php?t=1226761](http://ubuntuforums.org/showthread.php?t=1226761)

Best Regards,
Lyfang

---

### Post by Lyfang on 2012-07-20
Anyone with understanding of XKB? Any help is greatly appreciated! Website is up again: [Write Runes on Your Computer]("http://thomaswebb.net/my-code/write-runes-on-your-computer/")

The /etc/X11/xkb folder is empty. This file [en_futhark]("http://thomaswebb.net/code/en_futhark")  is to be saved in the /etc/X11/xkb/symbols/pc folder.

---

### Post by robertmf on 2012-07-22
:popcorn:   In 12.04 where now are the /etc/X11/xkb/symbols keyboard layout files ?  
[COLOR="Blue"]
The kbd files are in /usr/share/X11/xkb/symbols[/COLOR]

> **Lyfang said:**
> Anyone with understanding of XKB? Any help is greatly appreciated! Website is up again: [Write Runes on Your Computer]("http://thomaswebb.net/my-code/write-runes-on-your-computer/")

The /etc/X11/xkb folder is empty. This file [en_futhark]("http://thomaswebb.net/code/en_futhark")  is to be saved in the /etc/X11/xkb/symbols/pc folder.

---

### Post by Lyfang on 2012-07-22
Thanks robertmf for responding! I found files at /usr/share/X11/xkb/symbols, do I place [en_futhark]("http://thomaswebb.net/code/en_futhark") inside this folder? How can I change the keyboard layout to the runic keyboard layout (en_futhark) easily? Can Lxkeymap or setxkbmap (command line) be used to change the layout?

See also: [Switch between keyboard layouts easily in LXDE ]("https://answers.launchpad.net/ubuntu/+source/lxde-common/+question/194012")

---

### Post by amjjawad on 2012-07-25
> **Lyfang said:**
> Good day,

I'm using Lubuntu 12.04 LTS

Hi,

I'd like to just highlight that Lubuntu 12.04 is NOT LTS :)

[https://wiki.ubuntu.com/Lubuntu/#Welcome_to_the_Lubuntu_Desktop_project](https://wiki.ubuntu.com/Lubuntu/#Welcome_to_the_Lubuntu_Desktop_project)

---

### Post by Lyfang on 2012-07-25
@amjjawad: Thanks for letting me know, I still shure Firefox will be updated though.

I placed en_futhark here: /usr/share/X11/xkb/symbols/en_futhark

I found the xfree86.lst file (a symbolic link) at /usr/share/X11/xkb/rules/xfree86.lst & added the key board to the list. 

setxkbmap __ gives me an error:
Error loading new keyboard description

---

### Post by amjjawad on 2012-07-26
> **Lyfang said:**
> @amjjawad: Thanks for letting me know, I still shure Firefox will be updated though.


You welcome and don't worry much about being LTS or not :)

---

### Post by Lyfang on 2012-10-16
Will [http://thomaswebb.net/code/en_futhark](http://thomaswebb.net/code/en_futhark) work with Ubuntu 12.10 (Quantal Quetzal)?

---

### Post by amjjawad on 2012-10-18
> **Lyfang said:**
> Will [http://thomaswebb.net/code/en_futhark](http://thomaswebb.net/code/en_futhark) work with Ubuntu 12.10 (Quantal Quetzal)?

And what was that?

---

### Post by Lyfang on 2012-10-18
> **amjjawad said:**
> And what was that?
Runic keyboard layout for Linux.

---

### Post by Lyfang on 2012-11-30
I'm using Kubuntu 12.04 LTS right now. I want to use a custom keyboard layout and I want to be able to switch between keyboard layouts. How do I add the *en_futhark *keyboard layout in KDE?

---

### Post by Lyfang on 2012-12-03
What is the current equivalent of: /etc/X11/xkb/symbols/pc and /etc/X11/xkb/rules/xfree86.lst in today's Ubuntu?

---

### Post by Lyfang on 2013-03-29
Will [http://thomaswebb.net/code/en_futhark](http://thomaswebb.net/code/en_futhark) work with Lubuntu 13.04 (Raring Ringtail)?

---

### Post by Lyfang on 2013-08-11
I want to automate the process of transcribing Latin letters to the Runic alphabet. I would like a BASH or Python script that does this process simple. Can someone please write a simple "latintofuthark.sh" script?

English Latin letters extended with letters þ and &#331;:
a&#5800; b&#5842; c&#5811; d&#5854; e&#5846; f&#5792; g&#5815; h&#5818; i&#5825; j&#5827; k&#5810; l&#5850; m&#5847; n&#5822; o&#5855; p&#5832; q&#5865; r&#5809; s&#5834; t&#5839; u&#5794; v&#5793; w&#5817; x&#5866; y&#5795; z&#5833; þ&#5798; &#331;&#5852;

Swedish Latin letters extended with letters þ and &#331;:
a&#5800; b&#5842; c&#5811; d&#5854; e&#5846; f&#5792; g&#5815; h&#5818; i&#5825; j&#5827; k&#5810; l&#5850; m&#5847; n&#5822; o&#5794; p&#5832; q&#5865; r&#5809; s&#5834; t&#5839; u&#5796; v&#5793; w&#5817; x&#5866; y&#5795; z&#5833; å&#5801; ä&#5831; ö&#5855; þ&#5798; &#331;&#5852;

I'm not a specialist at runology so any suggestions for changes are welcome.

The letter sequence, position in rune-row:    
1.&#5792; 2.&#5794; 3.&#5798; 4.&#5800; (&#5801;?) 5.&#5809; 6.&#5810; (&#5811;?) 7.&#5815; 8.&#5817; 9.&#5818; 10.&#5822; 11.&#5825; 12.&#5827; 13.&#5831; 14.&#5832; 15.&#5833; 16.&#5834; 17.&#5839; 18.&#5842; 19.&#5846; 20.&#5847; 21.&#5850; 22.&#5852; 23.&#5854; 24.&#5855; others &#5795;? &#5865;? &#5793;? &#5796;? &#5866;?
*extended with Fuþorc and Younger Fuþark letters.

---

### Post by Lyfang on 2013-10-08
The web-based Runescribe transcribe engine: [http://www.furorteutonicus.eu/germanic/runescribe/index.php](http://www.furorteutonicus.eu/germanic/runescribe/index.php)

---

### Post by Lyfang on 2013-12-02
Does [http://thomaswebb.net/code/en_futhark](http://thomaswebb.net/code/en_futhark) work with Ubuntu 13.10 (Saucy Salamander)? 

Is there a way to make my own custom keyboard layout for Ubuntu 13.10 (Saucy Salamander)? I.e.with help of unicode characters using e.g. this page and scrolling down to "RUNIC LETTER" [Unicode Value Table: Other Letters - The Unicode Character Reference]("http://www.marathon-studios.com/unicode/categories/Lo/Other_Letter")? 

Has anyone tried the [Keyboard Layout Editor (KLE)]("http://code.google.com/p/keyboardlayouteditor")?

---

### Post by Lyfang on 2014-03-22
Web-based transcribe engine with Nordic characters: [http://lyfangrunes.tk/](http://lyfangrunes.tk/)

---

### Post by Lyfang on 2014-05-13
I hope there are people who are working on adding Runic support in XKB.

---

### Post by rafaellaguna2 on 2014-06-22
Hello, guys. Amjjawad, I did the same as you, and Futhark does not appear in the LXPanel keyboard applet (neither in XFCE keyboard layout). I downloaded the en_futhark file to /usr/share/X11/xkb/symbols and added the line en_futhar at the "layout" section like this:

```
! layout
  en_futhark      Futhark (old norse)
  us              English (US)
  af              Afghani
  etc...
```

What am I doing wrong?

---

### Post by Lyfang on 2014-08-26
I wish there was a tool to add the Futhark keyboard layout.

---

