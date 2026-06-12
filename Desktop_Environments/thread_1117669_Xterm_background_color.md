---
title: "Xterm background color"
date: 2009-04-06
forum: Desktop Environments
---

### Post by test006 on 2009-04-06
Hi,
I am currently running kubuntu 9.04 beta. I am using xterm for carrying out my CLI commands. I would like to change the color of the background for my xterm window. How do i go about changing the background color of the xterm window.

Please advise what config files do i have to modify...

thanks in advance.....

---

### Post by kellemes on 2009-04-06
Edit /home/<username>/.Xdefaults

I'll post mine, I play around with settings for other apps too, but surely you can figure out how set Xterm's background..

```
#.Xdefaults
#
# Colors: #http://www.nisrv.com/modules.php?name=Hex_Colors
#
#

Xft.antialias:			true
xcalendar*firstDay:		1
xcalendar*markHoliday:		false
!Xcursor.theme: 		whitelarge
!Xcursor.size: 		32

!-------------------------------------------------------------------------------
!
!	U R X V T - Setting
!
URxvt*perl-ext-common: default,tabbed
# Clickable URL's in the commandline begin.
#URxvt*urlLauncher: opera
#URxvt*matcher.button: 1
#URxvt*perl-ext-common: matcher
# Clickable URL's in the commandline end.
URxvt*cursorBlink: true
URxvt*geometry:         	83x48
URxvt*background:       	#000000
URxvt*foreground:       	#ffffff
URxvt*inheritPixmap:    	true
URxvt*reverseVideo:		false
URxvt*tintColor:        	#dfdfdf
URxvt*shading:	        20		!trans, 0=opaque    
URxvt*fading:	        10		!term unfocus      
!URxvt*font:	     		-lfp-gamow-medium-r-normal-*-*-90-*-*-c-*-iso8859-5
!URxvt*font:			-*-terminus-medium-*-*-*-17-*-*-*-*-*-koi8-*
URxvt*font			xft:Monospace:pixelsize=21
!URxvt*font:  		xft:matto:antialias=true:size=8
!URxvt*font:			xft:Bitstream Vera Sans mono:size=9
URxvt*scrollBar:		true
URxvt*scrollBar_floating:	true
URxvt*scrollBar_right:	false
URxvt*scrollColor:		#D25D5D
URxvt*saveLines:		10000
!URxvt*termName:		URxvt-ml
URxvt*cursorColor:		#d8d8d8
URxvt*colorBD:		lightyellow
URxvt*colorUL:		goldenrod

!colors
!black
URxvt*color0:		#676767
URxvt*color8:	        #757575
!red
URxvt*color1:	        #EA6868
URxvt*color9:	        #FF7272
!green
URxvt*color2:	        #ABCB8D
URxvt*color10:	        #AFD78A
!yellow
URxvt*color3:	        #E8AE5B
URxvt*color11:	        #FFA75D
!blue
URxvt*color4:	        #71C5F4
URxvt*color12:	        #67CDE9
!magenta
URxvt*color5:	        #E2BAF1
URxvt*color13:	        #ECAEE9
!cyan
URxvt*color6:	        #21F1EA
URxvt*color14:	        #36FFFC
!white
URxvt*color7:	        #F1F1F1
URxvt*color15:	        #FFFFFF


!-------------------------------------------------------------------------------
!
!	X T E R M - Setting
!
!
!XTerm*underLine:		on
XTerm*colorMode:		on
XTerm*colorBD:			lightyellow
!XTerm*colorBDMode:		off
XTerm*colorUL:			yellow
XTerm*colorULMode:		on
XTerm*dynamicColors:		off
XTerm*highlightSelection:	true
XTerm*background:		#000000
XTerm*foreground:		#7f7f7f

!colors
!black
XTerm*color0:		#000000
XTerm*color8:		#666666
!red
XTerm*color1:		#9e1828
XTerm*color9:		#cf6171
!green
XTerm*color2:		#aece92
XTerm*color10:		#c5f779
!yellow
XTerm*color3:		#968a38
XTerm*color11:		#fff796
!blue
XTerm*color4:		#414171
XTerm*color12:		#4186be
!magenta
XTerm*color5:		#96c359
XTerm*color13:		#cf9ebe
!cyan
XTerm*color6:		#418179
XTerm*color14:		#71bebe
!white
XTerm*color7:		#bebebe
XTerm*color15:		#ffffff 


!-------------------------------------------------------------------------------
!
!	X M E S S A G E - Setting
!
!
.xmessage.form.okay.shapeStyle: rectangle
.xmessage.form.okay.background: #777777
.xmessage.form.okay.foreground: snow
!xmessage*message*background: snow
xmessage*defaultButton: okay
Xmessage.form.message.Scroll:  WhenNeeded

!-------------------------------------------------------------------------------
!
!
!	X F O N T S E L - Setting
!
!
!XFontSel*sampleText.background: TEXTBG
XFontSel*menu*showUnselectable: false
XFontSel*MenuButton.shadowWidth: 0
XFontsel*Toggle*ToggleStyle: check
XFontsel*MenuButton*Justify:    left
XFontsel*MenuButton*MenuButtonStyle: select
.xfontsel.pane.commandBox.quitButton.background: #777777
.xfontsel.pane.commandBox.quitButton.foreground: snow
.xfontsel.pane.commandBox.ownButton.background: orange3
.xfontsel.pane.commandBox.ownButton.foreground: snow
.xfontsel.pane.commandBox.countLabel.background: snow
.xfontsel.pane.viewPort.sampleText.background: #777777
.xfontsel.pane.viewPort.sampleText.foreground: snow
.xfontsel.pane.fieldBox.field0.background: #777777
.xfontsel.pane.fieldBox.field0.foreground: snow
.xfontsel.pane.fieldBox.field1.background: #777777
.xfontsel.pane.fieldBox.field1.foreground: snow
.xfontsel.pane.fieldBox.field2.background: #777777
.xfontsel.pane.fieldBox.field2.foreground: snow
.xfontsel.pane.fieldBox.field3.background: #777777
.xfontsel.pane.fieldBox.field3.foreground: snow
.xfontsel.pane.fieldBox.field4.background: #777777
.xfontsel.pane.fieldBox.field4.foreground: snow
.xfontsel.pane.fieldBox.field5.background: #777777
.xfontsel.pane.fieldBox.field5.foreground: snow
.xfontsel.pane.fieldBox.field6.background: #777777
.xfontsel.pane.fieldBox.field6.foreground: snow
.xfontsel.pane.fieldBox.field7.background: #777777
.xfontsel.pane.fieldBox.field7.foreground: snow
.xfontsel.pane.fieldBox.field8.background: #777777
.xfontsel.pane.fieldBox.field8.foreground: snow
.xfontsel.pane.fieldBox.field9.background: #777777
.xfontsel.pane.fieldBox.field9.foreground: snow
.xfontsel.pane.fieldBox.field10.background: #777777
.xfontsel.pane.fieldBox.field10.foreground: snow
.xfontsel.pane.fieldBox.field11.background: #777777
.xfontsel.pane.fieldBox.field11.foreground: snow
.xfontsel.pane.fieldBox.field12.background: #777777
.xfontsel.pane.fieldBox.field12.foreground: snow
.xfontsel.pane.fieldBox.field13.background: #777777
.xfontsel.pane.fieldBox.field13.foreground: snow
.xfontsel.pane.fieldBox*foreground: #000000
.xfontsel.pane.fieldBox.MenuButton.borderWidth: 1
.xfontsel.pane.fieldBox.MenuButton.internalHeight: 1
.xfontsel.pane.fieldBox.MenuButton.internalWidth: 2
.xfontsel.pane.fieldBox.MenuButton.shapeStyle: rectangle

```

---

### Post by test006 on 2009-04-06
Hi,
Thanks for a quick response....I created a .Xdefaults file in my hone directory but i still have the problem when i start xterm i get white background. I would like to change the background color to be black.
I found a file called XTerm-color in the following directory:
/etc/X11/app-defaults/
I have changed stuff into here but still cannot black background xterm window.
contents of Xterm-color file is:
```

! $XTermId: XTerm-col.ad,v 1.20 2006/06/24 14:57:29 tom Exp $
! $XFree86: xc/programs/xterm/XTerm-col.ad,v 3.7 2005/09/18 23:48:12 dickey Exp $

#include "XTerm"

*VT100*colorMode: on
*VT100*boldColors: on
*VT100*dynamicColors: on

! Set the default text foreground and background colors.
!*VT100*foreground: gray90
!*VT100*foreground: black
!*VT100*background: black

! - OR -
! Uncomment this for black text on a "white" background.
*VT100*foreground: black
*VT100*background: gray90

! - OR -
! leave the foreground/background colors alone (at the mercy of your desktop
! designer).

! Color the popup/pulldown menu border to match the text widget's foreground.
!*SimpleMenu*borderColor: gray15

! Uncomment this to use color for underline attribute
!*VT100*colorULMode: on
*VT100*colorUL: yellow

!*VT100*italicULMode: on

! Uncomment this to disable underlining, e.g., if colorULMode is set.
!*VT100*underLine: off

! Uncomment this to use color for the bold attribute
!*VT100*colorBDMode: on
*VT100*colorBD: white

! Uncomment this to use the bold/underline colors in preference to other colors
!*VT100*colorAttrMode: on

! These are the 8 ANSI colors and their bright equivalents.  Depending on
! other resource settings, xterm may use the bright colors when displaying
! bold text (see the boldColors resource).
*VT100*color0: black
*VT100*color1: red3
*VT100*color2: green3
*VT100*color3: yellow3
*VT100*color4: blue2
*VT100*color5: magenta3
*VT100*color6: cyan3
*VT100*color7: gray90
*VT100*color8: gray50
*VT100*color9: red
*VT100*color10: green
*VT100*color11: yellow
*VT100*color12: rgb:5c/5c/ff
*VT100*color13: magenta
*VT100*color14: cyan
*VT100*color15: white

! Disclaimer: there are no standard colors used in terminal emulation.
!
! The choice for color4 and color12 is a tradeoff between contrast, depending
! on whether they are used for text or backgrounds.  Note that either color4 or
! color12 would be used for text, while only color4 would be used for a
! background.  These are treated specially, since the luminosity of blue is
! only about half that of red/green, and is typically not accounted for in the
! RGB scheme.
!
! Blue text on a black background should be readable.
! Blue backgrounds should not be "too" bright.
!
! Originally color4/color12 were set to the names blue3/blue
!*VT100*color4: blue3
!*VT100*color12: blue
!
! They are from rgb.txt respectively:
!  0   0 205		blue3
!  0   0 255		blue
! However, blue3 is not readable on a black background.
!
! Another choice was from the Debian settings:
!*VT100*color4: DodgerBlue1
!*VT100*color12: SteelBlue1
!
! From rgb.txt:
! 30 144 255		DodgerBlue1
! 99 184 255		SteelBlue1
!
! Some users object to this choice because the background (color4) is brighter
! than they are accustomed.  Others point out that the different weights for
! the red/green components make it appear to be not really blue.  Finally, it
! provides poor contrast against color13 and color14.
!
! The current choice uses equal weights for red/green (effectively adding a
! gray to the result).  It is brighter than the original choice, and provides
! more contrast between color12 and color13, color14 than SteelBlue1 did.
! Contrast of color4 against black is slightly improved over the original.
!
! Some refinement is certainly possible (you are welcome to try) -TD


#if PLANES > 8
! Color the popup menus and the menubar to match:
*SimpleMenu*background: AntiqueWhite
*SimpleMenu*foreground: gray15

! Color the menubar to match:
*Form.menubar.background: AntiqueWhite
*Form.menubar*background: AntiqueWhite
*Form.menubar.foreground: gray15
*Form.menubar*foreground: gray15
*Form.background: AntiqueWhite
*form.background: AntiqueWhite

*mainMenu*background: AntiqueWhite
*mainMenu*foreground: gray15
*vtMenu*background: AntiqueWhite
*vtMenu*foreground: gray15
*fontMenu*background: AntiqueWhite
*fontMenu*foreground: gray15
*tekMenu*background: AntiqueWhite
*tekMenu*foreground: gray15

! The following two sections take advantage of new features in version 7
! of the Athena widget library; see Xaw(7x).

! This section is commented out because Xaw has no way to dynamically size
! the gradient.  The dimension parameter may need to be adjusted depending
! on the font used in the menu.
!*SimpleMenu*backgroundPixmap:   gradient:vertical?dimension=350&start=gray90&end=gray60
!*SimpleMenu*foreground:         gray15

*VT100.scrollbar.thumb:         vlines2
*VT100.scrollbar.width:         14
*VT100.scrollbar.background:    gray60
*VT100.scrollbar.foreground:    rgb:a/5/5
*VT100.scrollbar.borderWidth:   0
*VT100.scrollbar.displayList:\
foreground      gray90;\
lines           1,-1,-1,-1,-1,1;\
foreground      gray60;\
lines           -1,0,0,0,0,-1
#endif

```

---

### Post by thompson42 on 2009-04-07
Once you have changed your .Xdefaults file, it is necessary to tell the X Windows server to read the changed file.  Here are two ways to do that.

1. Log out and log back in.

2. Enter the command:  xrdb --merge .Xdefaults

---

