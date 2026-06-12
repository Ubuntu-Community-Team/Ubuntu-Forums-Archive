---
title: "openbox with urxvt"
date: 2008-10-27
forum: Desktop Environments
---

### Post by deuce868 on 2008-10-27
I've got two problems working on getting my openbox setup in hardy. 

First, I'm trying out rxvt which seems to rock. I just can't get the scrollback working at all. I can find no keystroke or mousewheel movement to go back into the scrollback. Supposedly it should work ootb so I'm a bit at a loss. 

This is the relevent section of my .Xresoures file I'm trying to use:
> 
URxvt*scrollstyle:  plain
URxvt*mouseWheelScrollPage: True
URxvt*jumpScroll:       False
URxvt*skipScroll:       False
URxvt*scrollBar:        True
URxvt*scrollColor:      Blue
URxvt*scrollTtyOutput:  False
URxvt*secondaryScroll:  True
URxvt*saveLines::   32767


Any hints? I'm using the rxvt-unicode package. 

Secondly, when I make changes to my .Xresources and try to reload it with:
xrdb -merge ~/.Xresources

I get an error:
<stdin>:38:22: warning: missing terminating ' character

So I had seen that I should try to "sh -x ~/.Xresources" to see what was up and every line of config throws an error like
> 
+ URxvt*font: xft:Liberation Mono:size=7:VL Gothic:antialias=true:hinting=true
/home/rharding/.Xresources: 1: URxvt*font:: not found
+ URxvt*boldFont: xft:Liberation Mono:size=7:antialias=true:hinting=true:style=bold
/home/rharding/.Xresources: 1: URxvt*boldFont:: not found
+ URxvt*background: rgb:10/10/10
/home/rharding/.Xresources: 1: URxvt*background:: not found
+ URxvt*foreground: rgb:d3/d3/d3
/home/rharding/.Xresources: 1: URxvt*foreground:: not found
+ URxvt*color0: rgb:10/10/10
/home/rharding/.Xresources: 1: URxvt*color0:: not found
+ URxvt*color1: rgb:cd/5c/5c
/home/rharding/.Xresources: 1: URxvt*color1:: not found
........


Any hints on why this isn't working would help a ton since I have to reload X right now in order to try .Xresource changes.

---

### Post by bionnaki on 2008-10-28
.Xresource? not familiar with that. 

I use .Xdefaults
and it works great.

> 
URxvt*background: #000000
URxvt*foreground: #F426E9
URxvt*scrollBar:  false

#!Xft settings
#Xft.dpi:                96
#Xft.hinting:            1
#Xft.hintstyle:          hintfull
#Xft.antialias:          1 
#Xft.rgba:               rgb


!URxvt settings
URxvt.urlLauncher:      firefox
URxvt.matcher.button:   1
URxvt.perl-ext-common: matcher
URxvt.perl-lib: /usr/lib/urxvt/perl/matcher
urxvt*font:             xft:Terminus:size=9
URxvt*boldFont:         xft:Terminus:size=9
URxvt*italicFont:       xft:Terminus:pixelsize=9
URxvt*bolditalicFont:   xft:Terminus:size=9
URxvt*internalBorder:   6


!URxvt.termName:           string
URxvt.geometry:           90x30
!URxvt.reverseVideo:       boolean
!URxvt.loginShell:         boolean
!URxvt.jumpScroll:         boolean
!URxvt.skipScroll:         boolean
!URxvt.pastableTabs:       boolean
!URxvt.scrollstyle:        mode
!URxvt.scrollBar_right:    boolean
!URxvt.scrollBar_floating: boolean
!URxvt.scrollBar_align:    mode
!URxvt.thickness:          number
!URxvt.scrollTtyOutput:    boolean
!URxvt.scrollTtyKeypress:  boolean
!URxvt.scrollWithBuffer:   boolean
URxvt.transparent:        false
URxvt.tintColor:          #333333
URxvt.shading:            0
URxvt.fading:             0
URxvt.fadeColor:          #222222
!URxvt.utmpInhibit:        boolean
URxvt.urgentOnBell:       true
!URxvt.visualBell:         boolean
!URxvt.mapAlert:           boolean
!URxvt.meta8:              boolean
URxvt.mouseWheelScrollPage:   True
!URxvt.tripleclickwords:   boolean
!URxvt.insecure:           boolean
!URxvt.cursorUnderline:    boolean
URxvt.cursorBlink:        true
!URxvt.pointerBlank:       boolean
!URxvt.colorBD:            color
!URxvt.colorIT:            color
!URxvt.colorUL:            color
!URxvt.colorRV:            color
!URxvt.underlineColor:     color
!URxvt.scrollColor:        color
!URxvt.troughColor:        color
!URxvt.highlightColor:     color
URxvt.cursorColor:        #ffffff
!URxvt.cursorColor2:       color
URxvt.pointerColor:       #afc81c
!URxvt.pointerColor2:      color
!URxvt.borderColor:        color
!URxvt.intensityStyles:    boolean
!URxvt.inputMethod:        name
!URxvt.preeditType:        style
!URxvt.imLocale:           string
!URxvt.imFont:             fontname
!URxvt.title:               URxvt
!URxvt.iconName:           string
!URxvt.saveLines:          number
!URxvt.depth:              number
!URxvt.transient-for:      windowid
!URxvt.override-redirect:  boolean
!URxvt.hold:               boolean
!URxvt.externalBorder:     number
!URxvt.internalBorder:     number
URxvt.borderLess:         false
!URxvt.skipBuiltinGlyphs:  boolean
!URxvt.lineSpace:          number
!URxvt.pointerBlankDelay:  number
!URxvt.backspacekey:       string
!URxvt.deletekey:          string
!URxvt.selectstyle:        mode
!URxvt.print-pipe:         string
!URxvt.modifier:           modifier
!URxvt.cutchars:           string
!URxvt.answerbackString:   string
!URxvt.secondaryScreen:    boolean
!URxvt.secondaryScroll:    boolean
!URxvt.perl-lib:           string
!URxvt.perl-eval:          perl-eval
!URxvt.perl-ext-common:    string
!URxvt.perl-ext:           string
!URxvt.iso14755_52:        boolean
!URxvt*keysym.sym:         keysym


---

### Post by deuce868 on 2008-10-28
Thanks for the tip. How do you get your url handler to work? What is the key or action needed to fire it for a url? I have the config lines for it and see in your config it's button 1...but what is button one. I'm not seeing anything in the man page for that. 

Thanks

---

### Post by kellemes on 2008-12-30
> **deuce868 said:**
> Thanks for the tip. How do you get your url handler to work? What is the key or action needed to fire it for a url? I have the config lines for it and see in your config it's button 1...but what is button one. I'm not seeing anything in the man page for that. 

Thanks

It's the number of your mousebutton.
So *URxvt.matcher.button: 1* means you need to click mousebutton 1... most left that is, well.. in my case anyway.

---

