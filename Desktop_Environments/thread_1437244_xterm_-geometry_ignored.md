---
title: "xterm -geometry ignored"
date: 2010-03-23
forum: Desktop Environments
---

### Post by Sebastian Stein on 2010-03-23
Hi,

this one is driving me really crazy. I got a larger monitor and wanted to ajust the font size of my xterm under KDE.

Here is my current .Xdefaults file (I don't have a .Xresources):

```

xterm*allowWindowOps: true                           
xterm*allowFontOps: true
xterm*allowTitleOps: true
xterm*allowTermcapOps: true
xterm*background:   black
xterm*foreground:   white
xterm*highlight:   white
xterm*cursorColor:   green
xterm*loginShell: true
xterm*font: -misc-fixed-medium-r-normal--18-120-100-100-c-90-iso10646-1
```

The font looks nice. However, if I start a new xterm by pressing Alt+F2 and entering "xterm -geometry 100x30", an xterm is started, but the geometry is always ignored. It doesn't make any difference which values I use for the geometry parameter.

First, it was also impossible to change the size of a running xterm using the xtermcontrol program. To overcome this problem, I added the allow*Ops: true stuff to my .Xdefaults.

Does anyone know what is causing that the -geometry parameter is ignored? Also, if I add to my .Xdefaults the following, nothing happens:

```
xterm*vt100*geometry: 100x60
```

I also tried running the command from a konsole shell. Also, there is no alias defined for xterm, at least I don't see anything related to xterm if I type "alias".

As a note aside, I'm running zsh as my shell within xterm.

Anyone any ideas what is going wrong here?

---

### Post by itcotbtoemik on 2010-03-24
Perhaps there's already a more-specific resource in effect.
Generally, class names (the names using capital letters)
override the application names.  You can see most of what's
applicable using "appres XTerm".

---

### Post by Sebastian Stein on 2010-03-24
The command you mentioned produces the following output for a xterm, which I started from "konsole" terminal using "xterm -geometry 100x50":

```
*Entry.highlightBackground:	#ffffff
*Entry.foreground:	#141312
*Entry.activeBackground:	#ffffff
*Entry.selectForeground:	#ffffff
*Entry.background:	#ffffff
*Entry.activeForeground:	#141312
*Entry.highlightColor:	#141312
*Entry.selectBackground:	#418bd4
*XmFrame.background:	#e9e8e8
*XmFrame.foreground:	#141312
*XmLabel.background:	#e9e8e8
*XmLabel.foreground:	#141312
*XmLabelGadget.background:	#e9e8e8
*XmLabelGadget.foreground:	#141312
*Form.background:	#e9e8e8
*Form.foreground:	#141312
*XmList.background:	#ffffff
*XmList.foreground:	#141312
*Frame.highlightBackground:	#e9e8e8
*Frame.foreground:	#141312
*Frame.activeBackground:	#e9e8e8
*Frame.background:	#e9e8e8
*Frame.activeForeground:	#141312
*Frame.highlightColor:	#141312
*XmMenuShell.background:	#e9e8e8
*XmMenuShell.foreground:	#141312
*XmMessageBox.background:	#e9e8e8
*XmMessageBox.foreground:	#141312
*Label.highlightBackground:	#e9e8e8
*Label.foreground:	#141312
*Label.activeBackground:	#e9e8e8
*Label.background:	#e9e8e8
*Label.activeForeground:	#141312
*Label.highlightColor:	#141312
*XmPanedWindow.background:	#e9e8e8
*XmPanedWindow.foreground:	#141312
*List.background:	#ffffff
*List.foreground:	#141312
*fontMenu*allow-tcap-ops*Label:	Allow Termcap Ops
*fontMenu*font1*Label:	Unreadable
*fontMenu*fontescape*Label:	Escape Sequence
*fontMenu*allow-font-ops*Label:	Allow Font Ops
*fontMenu*fontsel*Label:	Selection
*fontMenu*font-linedrawing*Label:	Line-Drawing Characters
*fontMenu*allow-title-ops*Label:	Allow Title Ops
*fontMenu*font-doublesize*Label:	Doublesized Characters
*fontMenu*font2*Label:	Tiny
*fontMenu*allow-window-ops*Label:	Allow Window Ops
*fontMenu*font-loadable*Label:	VT220 Soft Fonts
*fontMenu*font3*Label:	Small
*fontMenu*render-font*Label:	TrueType Fonts
*fontMenu*font4*Label:	Medium
*fontMenu*utf8-mode*Label:	UTF-8
*fontMenu*font5*Label:	Large
*fontMenu*utf8-title*Label:	UTF-8 Titles
*fontMenu*fontdefault*Label:	Default
*fontMenu*font6*Label:	Huge
*fontMenu.Label:	VT Fonts
*XmPushButton.background:	#e9e8e8
*XmPushButton.foreground:	#141312
*Listbox.highlightBackground:	#ffffff
*Listbox.foreground:	#141312
*Listbox.activeBackground:	#ffffff
*Listbox.selectForeground:	#ffffff
*Listbox.background:	#ffffff
*Listbox.activeForeground:	#141312
*Listbox.highlightColor:	#141312
*Listbox.selectBackground:	#418bd4
*XmPushButtonGadget.background:	#e9e8e8
*XmPushButtonGadget.foreground:	#141312
*Menu.highlightBackground:	#e9e8e8
*Menu.foreground:	#141312
*Menu.activeBackground:	#e9e8e8
*Menu.background:	#e9e8e8
*Menu.activeForeground:	#141312
*Menu.highlightColor:	#141312
*tek4014*fontLarge:	9x15
*tek4014*font2:	8x13
*tek4014*font3:	6x13
*tek4014*fontSmall:	6x10
*XmRowColumn.background:	#e9e8e8
*XmRowColumn.foreground:	#141312
*MenuButton.background:	#e9e8e8
*MenuButton.foreground:	#141312
*MenuButton*borderWidth:	0
*VT100.utf8Fonts.font5:	-misc-fixed-medium-r-normal--18-120-100-100-c-90-iso10646-1
*VT100.utf8Fonts.font3:	-misc-fixed-medium-r-normal--14-130-75-75-c-70-iso10646-1
*VT100.utf8Fonts.font4:	-misc-fixed-medium-r-normal--13-120-75-75-c-80-iso10646-1
*VT100.utf8Fonts.font:	-misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso10646-1
*VT100.utf8Fonts.font2:	-misc-fixed-medium-r-normal--8-80-75-75-c-50-iso10646-1
*VT100.utf8Fonts.font6:	-misc-fixed-medium-r-normal--20-200-75-75-c-100-iso10646-1
*VT100.font5:	9x15
*VT100.font3:	6x10
*VT100.font1:	nil2
*VT100.font4:	7x13
*VT100.font2:	5x7
*VT100.font6:	10x20
*XmSash.background:	#e9e8e8
*XmSash.foreground:	#141312
*Menubutton.highlightBackground:	#e9e8e8
*Menubutton.foreground:	#141312
*Menubutton.activeBackground:	#e9e8e8
*Menubutton.background:	#e9e8e8
*Menubutton.activeForeground:	#141312
*Menubutton.highlightColor:	#141312
*vtMenu*cursesemul*Label:	Enable Curses Emulation
*vtMenu*autolinefeed*Label:	Enable Auto Linefeed
*vtMenu*hardreset*Label:	Do Full Reset
*vtMenu*visualbell*Label:	Enable Visual Bell
*vtMenu*appcursor*Label:	Enable Application Cursor Keys
*vtMenu*clearsavedlines*Label:	Reset and Clear Saved Lines
*vtMenu*bellIsUrgent*Label:	Enable Bell Urgency
*vtMenu*appkeypad*Label:	Enable Application Keypad
*vtMenu*tekshow*Label:	Show Tek Window
*vtMenu*poponbell*Label:	Enable Pop on Bell
*vtMenu*scrollbar*Label:	Enable Scrollbar
*vtMenu*scrollkey*Label:	Scroll to Bottom on Key Press
*vtMenu*tekmode*Label:	Switch to Tek Mode
*vtMenu*scrollttyoutput*Label:	Scroll to Bottom on Tty Output
*vtMenu*jumpscroll*Label:	Enable Jump Scroll
*vtMenu*cursorblink*Label:	Enable Blinking Cursor
*vtMenu*vthide*Label:	Hide VT Window
*vtMenu*allow132*Label:	Allow 80/132 Column Switching
*vtMenu*reversevideo*Label:	Enable Reverse Video
*vtMenu*titeInhibit*Label:	Enable Alternate Screen Switching
*vtMenu*altscreen*Label:	Show Alternate Screen
*vtMenu*keepSelection*Label:	Keep Selection
*vtMenu*autowrap*Label:	Enable Auto Wraparound
*vtMenu*activeicon*Label:	Enable Active Icon
*vtMenu*selectToClipboard*Label:	Select to Clipboard
*vtMenu*reversewrap*Label:	Enable Reverse Wraparound
*vtMenu*softreset*Label:	Do Soft Reset
*vtMenu.Label:	VT Options
*XmScrollBar.background:	#e9e8e8
*XmScrollBar.foreground:	#141312
*Radiobutton.highlightBackground:	#e9e8e8
*Radiobutton.foreground:	#141312
*Radiobutton.activeBackground:	#e9e8e8
*Radiobutton.background:	#e9e8e8
*Radiobutton.activeForeground:	#141312
*Radiobutton.highlightColor:	#141312
*XmScrolledWindow.background:	#e9e8e8
*XmScrolledWindow.foreground:	#141312
*Scale.highlightBackground:	#e9e8e8
*Scale.foreground:	#141312
*Scale.activeBackground:	#e9e8e8
*Scale.background:	#e9e8e8
*Scale.activeForeground:	#141312
*Scale.highlightColor:	#141312
*Scale.troughColor:	#e9e8e8
*XmSelectionBox.background:	#e9e8e8
*XmSelectionBox.foreground:	#141312
*mainMenu*hpFunctionKeys*Label:	HP Function-Keys
*mainMenu*allowsends*Label:	Allow SendEvents
*mainMenu*backarrow key*Label:	Backarrow Key (BS/DEL)
*mainMenu*kill*Label:	Send KILL Signal
*mainMenu*num-lock*Label:	Alt/NumLock Modifiers
*mainMenu*redraw*Label:	Redraw Window
*mainMenu*scoFunctionKeys*Label:	SCO Function-Keys
*mainMenu*quit*Label:	Quit
*mainMenu*alt-esc*Label:	Alt Sends Escape
*mainMenu*logging*Label:	Log to File
*mainMenu*tcapFunctionKeys*Label:	Termcap Function-Keys
*mainMenu*meta-esc*Label:	Meta Sends Escape
*mainMenu*print*Label:	Print Window
*mainMenu*suspend*Label:	Send STOP Signal
*mainMenu*delete-is-del*Label:	Delete is DEL
*mainMenu*print-redir*Label:	Redirect to Printer
*mainMenu*continue*Label:	Send CONT Signal
*mainMenu*oldFunctionKeys*Label:	Old Function-Keys
*mainMenu*interrupt*Label:	Send INT Signal
*mainMenu*sunFunctionKeys*Label:	Sun Function-Keys
*mainMenu*toolbar*Label:	Toolbar
*mainMenu*8-bit control*Label:	8-Bit Controls
*mainMenu*hangup*Label:	Send HUP Signal
*mainMenu*sunKeyboard*Label:	VT220 Keyboard
*mainMenu*securekbd*Label:	Secure Keyboard
*mainMenu*terminate*Label:	Send TERM Signal
*mainMenu.Label:	Main Options
*XmSeparator.background:	#e9e8e8
*XmSeparator.foreground:	#141312
*Scrollbar*height:	15
*Scrollbar.foreground:	#141312
*Scrollbar.highlightBackground:	#e9e8e8
*Scrollbar*pushThumb:	false
*Scrollbar.highlightColor:	#141312
*Scrollbar.troughColor:	#e9e8e8
*Scrollbar.activeBackground:	#e9e8e8
*Scrollbar*shadowWidth:	2
*Scrollbar*Cursor:	left_ptr
*Scrollbar.activeForeground:	#141312
*Scrollbar*width:	15
*Scrollbar*background:	#e9e8e8
*Scrollbar*cursorName:	left_ptr
*XmSeparatorGadget.background:	#e9e8e8
*XmSeparatorGadget.foreground:	#141312
*XmTearOffButton.background:	#e9e8e8
*XmTearOffButton.foreground:	#141312
*form.Thickness:	0
*XmTearOffButtonGadget.background:	#e9e8e8
*XmTearOffButtonGadget.foreground:	#141312
*XmText.background:	#ffffff
*XmText.foreground:	#141312
*Box.background:	#e9e8e8
*Box.foreground:	#141312
*XmTextField.background:	#ffffff
*XmTextField.foreground:	#141312
*XmToggleButton.background:	#e9e8e8
*XmToggleButton.foreground:	#141312
*XmToggleButtonGadget.background:	#e9e8e8
*XmToggleButtonGadget.foreground:	#141312
*Button.highlightBackground:	#e9e8e8
*Button.foreground:	#141312
*Button.activeBackground:	#e9e8e8
*Button.background:	#e9e8e8
*Button.activeForeground:	#141312
*Button.highlightColor:	#141312
*SimpleMenu*menuLabel.font:	-adobe-helvetica-bold-r-normal--*-120-*-*-*-*-iso8859-*
*SimpleMenu*menuLabel.vertSpace:	100
*SimpleMenu*Sme.height:	16
*SimpleMenu*borderWidth:	2
*SimpleMenu*Cursor:	left_ptr
*SimpleMenu*foreground:	#141312
*SimpleMenu*HorizontalMargins:	16
*SimpleMenu*BackingStore:	NotUseful
*SimpleMenu*background:	#e9e8e8
*menubar.borderWidth:	0
*SmeBSB*shadowWidth:	3
*rvplayer*authortext.background:	#e9e8e8
*rvplayer*authortext.bottomShadowPixel:	#ffffff
*rvplayer*authortext.topShadowPixel:	#535353
*rvplayer*statustext.background:	#e9e8e8
*rvplayer*statustext.foreground:	#141312
*rvplayer*volumeslider.bottomShadowPixel:	#ffffff
*rvplayer*volumeslider.topShadowPixel:	#535353
*rvplayer*copyrighttext.background:	#e9e8e8
*rvplayer*copyrighttext.bottomShadowPixel:	#ffffff
*rvplayer*copyrighttext.topShadowPixel:	#535353
*rvplayer*Label.BorderColor:	#141312
*rvplayer*MenuButton.BorderColor:	#141312
*rvplayer*MenuButton.background:	#e9e8e8
*rvplayer*timeinfotext.background:	#e9e8e8
*rvplayer*timeinfotext.bottomShadowPixel:	#ffffff
*rvplayer*timeinfotext.foreground:	#141312
*rvplayer*timeinfotext.topShadowPixel:	#535353
*rvplayer*Vslider.thumbPixel:	#ffffff
*rvplayer*Command.BorderColor:	#141312
*rvplayer*Command.background:	#e9e8e8
*rvplayer*Command.foreground:	#141312
*rvplayer*SepLine.BorderColor:	#e9e8e8
*rvplayer*SepLine.bottomShadowPixel:	#ffffff
*rvplayer*SepLine.topShadowPixel:	#535353
*rvplayer*SimpleMenu.BorderColor:	#535353
*rvplayer*SimpleMenu.background:	#e9e8e8
*rvplayer*SimpleMenu.foreground:	#141312
*rvplayer*proptext.background:	#e9e8e8
*rvplayer*proptext.foreground:	#141312
*rvplayer*timeslider.bottomShadowPixel:	#ffffff
*rvplayer*timeslider.foreground:	#e9e8e8
*rvplayer*timeslider.thumbPixel:	#ffffff
*rvplayer*timeslider.topShadowPixel:	#535353
*rvplayer*SmeBSB*fgInsensitive:	#ffffff
*rvplayer*statusback.background:	#e9e8e8
*rvplayer*statusback.foreground:	#141312
*rvplayer*titletext.background:	#e9e8e8
*rvplayer*titletext.bottomShadowPixel:	#ffffff
*rvplayer*titletext.topShadowPixel:	#535353
*rvplayer*background:	#e9e8e8
*Text.highlightBackground:	#ffffff
*Text.foreground:	#141312
*Text.activeBackground:	#ffffff
*Text.selectForeground:	#ffffff
*Text.background:	#ffffff
*Text.activeForeground:	#141312
*Text.highlightColor:	#141312
*Text.selectBackground:	#418bd4
*Toggle.background:	#e9e8e8
*Toggle.foreground:	#141312
*Canvas.highlightBackground:	#ffffff
*Canvas.foreground:	#141312
*Canvas.activeBackground:	#ffffff
*Canvas.selectforeground:	#ffffff
*Canvas.background:	#ffffff
*Canvas.activeForeground:	#141312
*Canvas.highlightColor:	#141312
*Canvas.selectbackground:	#418bd4
*Toplevel.highlightBackground:	#e9e8e8
*Toplevel.foreground:	#141312
*Toplevel.activeBackground:	#e9e8e8
*Toplevel.background:	#e9e8e8
*Toplevel.activeForeground:	#141312
*Toplevel.highlightColor:	#141312
*XmCascadeButton.background:	#e9e8e8
*XmCascadeButton.foreground:	#141312
*XmCascadeButtonGadget.background:	#e9e8e8
*XmCascadeButtonGadget.foreground:	#141312
*Checkbutton.highlightBackground:	#e9e8e8
*Checkbutton.foreground:	#141312
*Checkbutton.activeBackground:	#e9e8e8
*Checkbutton.background:	#e9e8e8
*Checkbutton.activeForeground:	#141312
*Checkbutton.highlightColor:	#141312
*XmDialogShell.background:	#e9e8e8
*XmDialogShell.foreground:	#141312
*tekMenu*tekcopy*Label:	COPY
*tekMenu*tektext3*Label:	#3 Size Characters
*tekMenu*vtshow*Label:	Show VT Window
*tekMenu*tektextsmall*Label:	Small Characters
*tekMenu*vtmode*Label:	Switch to VT Mode
*tekMenu*tektextlarge*Label:	Large Characters
*tekMenu*tekpage*Label:	PAGE
*tekMenu*tekreset*Label:	RESET
*tekMenu*tektext2*Label:	#2 Size Characters
*tekMenu*tekhide*Label:	Hide Tek Window
*tekMenu.Label:	Tek Options
*Command.background:	#e9e8e8
*Command.foreground:	#141312
*XmFileSelectionBox.background:	#e9e8e8
*XmFileSelectionBox.foreground:	#141312
*Dialog.background:	#e9e8e8
*Dialog.foreground:	#141312
*XmForm.background:	#e9e8e8
*XmForm.foreground:	#141312
*ptyInitialErase:	true
*foreground:	#141312
*ScrollbarBackground:	#e9e8e8
*ShapeStyle:	Rectangle
*saveLines:	1024
*IconFont:	nil2
*charClass:	33:48,35:48,37-38:48,43-47:48,58:48,61:48,63-64:48,95:48,126:48
*beNiceToColormap:	false
*backarrowKeyIsErase:	true
*background:	#e9e8e8
*borderColor:	black

```

I can't find anything about geometry. If I issue "xtermcontrol --geometry=100x50" in this xterm window, it resizes as expected.

Any ideas?

---

### Post by itcotbtoemik on 2010-03-24
The X libraries may not be looking in $HOME/.Xdefaults

For instance, in a quick check here (fvwm2), strace shows
me that it's looking in $HOME/.Xdefaults-{my hostname}

That's consistent with the X manpage's documentation for
the XENVIRONMENT variable.

I usually rely on XAPPLRESDIR, and populate that with
whatever customized app-defaults that I'm testing,
though in my environment, that's not set until after
the window manager starts (so xterm's started via the
window manager do not see the customized app-defaults).

---

### Post by Sebastian Stein on 2010-03-24
A friend of mine asked an important question: "Why aren't you using konsole?" Well, I had no good answer so I switched and there everything works.

So I basically gave up on xterm. I know that's lame, but sometimes I just need getting things done...

---

### Post by Fafnir089 on 2012-04-11
Hi,

I came across this post through the Search function at top right. I had the same problem.
The documentation that solved my problem is here:
[http://www.debian-administration.org/article/Customizing_your_xterm](http://www.debian-administration.org/article/Customizing_your_xterm)
Here is my sample .Xresources file:

```
       !
       ! xterm configuration file
       !
       
       XTerm*background:       black
       XTerm*foreground:       white
       XTerm*cursorColor:      white
       XTerm.vt100.geometry:   100x45-0-0
       XTerm*scrollBar:        true
       XTerm*scrollTtyOutput:  false
```It places the xterm window in the bottom right corner.
After editing  .Xresources issue the command
```
xrdb -merge ~/.Xresources
```to force a reload of ~/.Xresources
Notice the line Xterm.vt100.geometry instead of Xterm*vt100*geometry. It seems that it works both ways.
:cool:

---

### Post by itcotbtoemik on 2012-06-29
> **Fafnir089 said:**
> 
Notice the line Xterm.vt100.geometry instead of Xterm*vt100*geometry. It seems that it works both ways.
:cool:

s/Xterm/XTerm/

---

