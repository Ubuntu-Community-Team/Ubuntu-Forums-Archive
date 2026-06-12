---
title: "xterm and bold font"
date: 2009-02-12
forum: Desktop Environments
---

### Post by asl.pavel on 2009-02-12
Hi guys! I can't find a way to turn off bold font in xterm. Use other terminal is not an option... ( i like xterm ). And i want to keep using freetype fonts ... here's my .Xdefaults:
```

xterm*faceName:         mono:normal:size=9:minspace:rgba=rgb
xterm*bolfFont: 
xterm*scrollBar:        false
xterm*geometry:         80x50
xterm*eightBitInput:    false
xterm*metaSendsEscape:  true
xterm*colorBDMode:      true
xterm*boldMode:         on
xterm*alwaysBoldMode:   false
xterm*utf8Title:        true
xterm*dynamicColors:    on
xterm*colorMode:        on
xterm*saveLines:        10000
xterm*visualBell:       false

!==============================================================================
! colors 
!==============================================================================
xterm*colorBD:     #e6d51d
xterm*background:  #1c1c1c
xterm*foreground:  #b4b4b4
! black
xterm*color0:      #000000
xterm*color8:      #555753
! red
!xterm*color1:      #9e1828
xterm*color1:      #b6212d
xterm*color9:      #ff6565
! green
xterm*color2:      #4c8d00
!xterm*color10:     #7fc862
xterm*color10:     #6bbe1a

! yellow
xterm*color3:      #ff8040
xterm*color11:     #e6d51d
! blue
xterm*color4:      #204a87
xterm*color12:     #9370bd

! magenta
xterm*color5:      #963c59
!xterm*color13:     #cf9ebe
xterm*color13:     #d3649f

! cyan
xterm*color6:      #105952
!xterm*color14:     #71bebe
xterm*color14:     #177f75

! white
xterm*color7:      #bebebe
xterm*color15:     #ffffff

```
setting boldFont to smth change nothing i think its used only by bitmap fonts and doesn't effect in any way. :confused:

---

### Post by thompson42 on 2009-02-12
While I don't know the cause of your bold fonts, I can suggest a way to identify the specific line in your .Xdefaults that is responsible.  Comment out every line in your .Xdefaults, tell your X server to read it by using the command "xrdb -merge .Xdefaults", then start an xterm.  I think you will not see the bold fonts.  Then exit the xterm, uncomment a line in .Xdefaults, do xrdb -merge .Xdefaults, start a new xterm, and see if the problem returns.  Repeat till the problem returns; the last thing you changed is, if not the cause of the problem, at least a clue to the cause.

---

### Post by kerry_s on 2009-02-12
looking at the man page i don't think you can disable bold fonts.
i think your best option would be to set a bold font you like.

you might want to give the man page a read, some of the settings are not needed, there that way by default.

mine:

```


*customization: -color
*font: 9x15
*faceName: mono
*faceSize: 9
*enableBackups: off
*Cursor: hand2

xterm*reverseVideo: true
xterm*geometry: 100x24

xmessage*font: 10x20
xmessage.form.message.Scroll: WhenNeeded

xpdf*geometry: 700x500+0+0
xpdf*initialZoom: width

xcalc*geometry: -0+0
xcalc.ti.Command.foreground: White
xcalc.ti.Command.background: black
xcalc.ti.button5.background: Orange3
xcalc.ti.button20.background: #611111
xcalc.ti.button25.background: #722222
xcalc.ti.button30.background: #833333
xcalc.ti.button35.background: #944444
xcalc.ti.button40.background: #a55555
xcalc.ti.button22.background: #222262
xcalc.ti.button23.background: #222262
xcalc.ti.button24.background: #222272
xcalc.ti.button27.background: #333373
xcalc.ti.button28.background: #333373
xcalc.ti.button29.background: #333373
xcalc.ti.button32.background: #444484
xcalc.ti.button33.background: #444484
xcalc.ti.button34.background: #444484
xcalc.ti.button37.background: #555595
xcalc.ti.button38.background: #555595
xcalc.ti.button39.background: #555595


```

---

### Post by asl.pavel on 2009-02-12
The problem is that i have for xter*faceName a bold font before and i rather tired of it , so i change it to normal face. font without bold parametr looks ok but i cant chanche bold font to be not bold. I just want to see brighter color with same face for font. I read man xterm change everething i can, try googling. And now would very like too see working varaint =)) plz help. here what i got.

[IMG]http://img144.imageshack.us/img144/5356/xtermte4.png[/IMG]

---

### Post by kerry_s on 2009-02-13
i don't know, i've looked around, i don't think it can be done.
yours looks pretty good to me, looks like mine but i use the stock colors.

---

### Post by asl.pavel on 2009-02-13
so bad :*(

---

### Post by kerry_s on 2009-02-13
> **asl.pavel said:**
> so bad :*(

i know, it makes since to me. there should be a way to disable the bold fonts. i tested all the "bold", "colorbold", "font", etc... in the man pages and nothing worked.

---

### Post by asl.pavel on 2009-02-14
Actualy it seems possible to set all fonts the same but u have to use bitmaps fonts, and set boldFont... But its not works when u use Xft... :(

---

### Post by gaqzi on 2010-02-21
First, sorry for bumping an old thread. I'm not a regular on these forums so I hope it's okay since I give a working answer since this is one of the threads that come up pretty high on Google searches for how to disable bold fonts in xterm.

I've found a way to get rid of the bold fonts, set the the same font for bold as the one you have for normal fonts. I'm running this on Ubuntu 9.10.

E.g I prefer [FONT=Lucida Console]fixed[/FONT] as the font so I've added this to my .Xresources:
```

xterm*boldFont: fixed
xterm*font: fixed
```And after the usual xrdb dance and restarting xterm it all looked nice. For an image of the difference see my blog post on [how to disable bold fonts in xterm]("http://sanitarium.se/blog/2010/02/how-to-disable-bold-fonts-in-xterm/").

---

### Post by itcotbtoemik on 2010-03-24
Since OP's using faceName, most of the discussion relating
to font, boldFont, etc., doesn't apply.  Only the pieces
such as colorBDMode would apply.

---

