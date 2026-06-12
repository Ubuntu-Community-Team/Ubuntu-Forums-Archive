---
title: "Configuring xterm"
date: 2008-02-20
forum: Desktop Environments
---

### Post by Magatsu Taito on 2008-02-20
Ok, this sucks. I want to configure xterm, and I have been reading liek crazy. There are several threads about it, that are actually really good, but nothing I do can change the looks of my xterm window.  All guides talk about different files, where the ubuntu forum talks about ~/Xdefaults. I am not sure where this file is located?

Someone said you need to create it yourself, but where should I put it? I tried putting it into my home folder, pasting in a config someone else did, but nothing happend. Googling about this just makes the problem bigger, since they are talking about other files, and other ways to do it.

I am just stuck, completely stuck with an ugly xterm window that I need to change.

---

### Post by drcranium on 2008-02-20
Make your ~/.Xdefaults

Then run

xrdb -merge ~/.Xdefaults

---

### Post by amohanty on 2008-02-20
In a terminal:

touch ~/.Xdefaults # creates file
gedit ~/.Xdefaults  # to edit it

sample content:

> ! [http://www.xfree86.org/current/xterm.1.html](http://www.xfree86.org/current/xterm.1.html)

! Athena stuff (e.g. xterm) tends to use the following
*Scrollbar.background: gray50
*Scrollbar.foreground: gray50
*Scrollbar.borderWidth: 0
*Scrollbar.shadowWidth: 0
*Scrollbar.thickness: 14
*Scrollbar.minimumThumb: 20
*Scrollbar.backgroundPixmap: gradient:horizontal?dimension=14&start=gray65&end=gray90
*Scrollbar.borderPixmap: gradient:horizontal?dimension=14&start=gray90&end=grey65

XTerm.toolBar:                  true

! vt100  resources
XTerm.vt100.activeIcon:         true
XTerm.vt100.alwaysHighlight:    true
XTerm.vt100.autoWrap:           true
XTerm.vt100.reverseWrap:        true

XTerm.vt100.background:         #383838
XTerm.vt100.foreground:         #e5e5e5
XTerm.vt100.pointerColor:       ivory
XTerm.vt100.cursorColor:        yellow

XTerm.vt100.cutNewline:         false
XTerm.vt100.deleteIsDEL:        true

XTerm.vt100.renderFont:         true
XTerm.vt100.faceName:           Bitstream\ Vera\ Sans\ Mono
XTerm.vt100.faceSize:           8

XTerm.vt100.geometry:           80x25
XTerm.vt100.internalBorder:     4

XTerm.vt100.scrollBar:          true
XTerm.vt100.jumpScroll:         true
XTerm.vt100.multiScroll:        true
XTerm.vt100.rightScrollBar:     true
XTerm.vt100.scrollLines:        1
XTerm.vt100.scrollTtyOutput:    true
XTerm.vt100.scrollBarBorder:    1

XTerm.vt100.loginShell:         true
XTerm.vt100.visualBell:         true


load it up

xrdb < ~/.Xdefaults

fire up xterm and should work.

HTH
AM

---

### Post by kerry_s on 2008-02-20
any time you see this> **~** <means your home folder, it's like a shortcut.
open your file manager and press> **ctrl+h** <to show hidden files & folders
then right click and select new file
name it> **.Xdefaults** <note the dot, it's to be a hidden file
to activate the Xdefaults you need to run> **xrdb -merge ~/.Xdefaults**
you also need to put that in your startup to load xdefaults when you log in.

here's mine->

```
! you should run> xrdb -merge ~/.Xdefaults 


xpdf*initialZoom: width
xpdf*geometry: 800x600

xedit*geometry: 800x600
xedit*enableBackups: off
xedit*fontSet: -*-fixed-*-r-*-*-15-*-*-*-*-*-*-*
xedit*foreground: white
xedit*background: black
xedit*editWindow.scrollHorizontal: true
xedit*bc_label.foreground: black
xedit*Command.foreground: black
xedit*formWindow*foreground: black
xedit*SimpleMenu*foreground: black
xedit*Scrollbar.thumb:               wide_weave
xedit*hScrollbar.thumb:              wide_weave

.xmessage.form.okay.shapeStyle: rectangle
.xmessage.form.okay.background: gray
.xmessage.form.okay.foreground: black
xmessage*message*background: white
xmessage*defaultButton: okay
Xmessage.form.message.Scroll:  WhenNeeded

xcalc*geometry: 400x300                                                         
xcalc.ti.bevel.background: #111111                                              
xcalc.ti.bevel.screen.background: Green                                         
xcalc.ti.bevel.screen.DEG.background: Green                                     
xcalc.ti.bevel.screen.DEG.foreground: Black                                     
xcalc.ti.bevel.screen.GRAD.background: Green                                    
xcalc.ti.bevel.screen.GRAD.foreground: Black                                    
xcalc.ti.bevel.screen.RAD.background: Green                                     
xcalc.ti.bevel.screen.RAD.foreground: Black                                     
xcalc.ti.bevel.screen.INV.background: Green                                     
xcalc.ti.bevel.screen.INV.foreground: Red                                       
xcalc.ti.bevel.screen.LCD.background: Green                                     
xcalc.ti.bevel.screen.LCD.foreground: Black                                     
xcalc.ti.bevel.screen.LCD.shadowWidth: 0                                        
xcalc.ti.bevel.screen.M.background: Green                                       
xcalc.ti.bevel.screen.M.foreground: Black                                       
xcalc.ti.bevel.screen.P.background: Green                                       
xcalc.ti.bevel.screen.P.foreground: Black                                       
xcalc.ti.Command.foreground: White
xcalc.ti.Command.background: black                                              
xcalc.ti.button5.background: orange                                             
xcalc.ti.button20.background: red                                               
xcalc.ti.button25.background: red                                               
xcalc.ti.button30.background: red                                               
xcalc.ti.button35.background: red                                               
xcalc.ti.button40.background: green                                             
xcalc.ti.button22.background: blue                                              
xcalc.ti.button23.background: blue                                              
xcalc.ti.button24.background: blue                                              
xcalc.ti.button27.background: blue                                              
xcalc.ti.button28.background: blue                                              
xcalc.ti.button29.background: blue                                              
xcalc.ti.button32.background: blue                                              
xcalc.ti.button33.background: blue                                              
xcalc.ti.button34.background: blue                                              
xcalc.ti.button37.background: blue                                              
xcalc*Cursor:                 hand2                                             

XTerm*faceName: Dejavu Sans Mono:size=10
XTerm*boldFont: Dejavu Sans Mono:style=Bold:size=10
XTerm*loginShell: true
XTerm*scrollBar: false
XTerm*eightBitInput:   false
XTerm*colorMode: true
XTerm*utf8: 1 
XTerm*reverseVideo: false

UXTerm*faceName: Dejavu Sans Mono:size=10
UXTerm*boldFont: Dejavu Sans Mono:style=Bold:size=10
UXTerm*loginShell: true
UXTerm*scrollBar: false
UXTerm*eightBitInput:   false
UXTerm*colorMode: true
UXTerm*utf8: 1 
UXTerm*reverseVideo: false
```

---

