---
title: "fluxbox - wallpaper not changing"
date: 2009-01-29
forum: Desktop Environments
---

### Post by toasty_ghosty on 2009-01-29
Hello

I try to only ask questions after I have exhausted everyother source, and this is definitly one of those times...

My main PC died, and so therefor I have resorted to using an old Pentium 4 I had laying around. I have fluxbuntu on it and love it. I'm actually thinking about putting it on my main rig once thats backup, but the issue is I cannot change my background. I have tried setting the init file with:

session.styleOverlay:	~/home/theking/Pictures/green_grass_1920x1200.jpg

and this:

background.pixmap: </home/theking/Pictures/green_grass_1920x1200.jpg>

and the startup file with:

 fbsetbg -l

after setting it manually. The issue is when the pc first starts up, it shows the image, but is very quickly replaced with the stock image that comes with Fluxbuntu...

Any ideas?

Thanks.

---

### Post by snowpine on 2009-01-29
In Fluxbuntu, rox filer controls the wallpaper. Just right-click on one of the desktop icons, and you should be able to change the wallpaper from the rox-filer options. 

I think you can also disable this behavior of rox filer to set your wallpaper manually, in the traditional fluxbox way. I guess they figured in order to make Fluxbuntu a "real distro" they needed a GUI wallpaper changer...

ps A lot of LXDE based distros have followed this trend, except with pcmanfm instead of rox filer.

---

### Post by toasty_ghosty on 2009-01-29
Wow

That was a lot easier then I was used to..

Thank you so much.

---

### Post by snowpine on 2009-01-29
No problem. Let me know if you have any more Fluxbuntu questions! It is a weird but strangely appealing distro for me. :)

---

### Post by toasty_ghosty on 2009-01-29
Yea. I'm really thinking about using it on my main rig. I am a big slackware fan and the text file editing is something I really like. But is there a way to get the menu to appear larger in certain themes? The font is tiny in many of the themes I have.

Once again. Thanks for the help.

---

### Post by snowpine on 2009-01-29
It's all done by editing text files. /usr/share/fluxbox/themes I believe (I'm on a different computer right now)

Are you using Fluxbuntu 7.10 or did you somehow get ahold of one of the newer versions?

---

### Post by toasty_ghosty on 2009-01-29
I am on version 7.10. Since my PC died I couldn't burn any CDs so I am stuck with 7.10...

Heres the theme file:

> ! -- toolbar --
toolbar:                            			flat 
toolbar.pixmap:          	    			bar.xpm
toolbar.textColor:                  			#c0c0c0
toolbar.justify:                    			center
toolbar.height:					16
toolbar.borderWidth:				1
toolbar.borderColor:				#1f1f1f

toolbar.workspace:                      		flat
toolbar.workspace.pixmap:			bar.xpm
toolbar.workspace.textColor:            	#c0c0c0

toolbar.iconbar.empty:				flat 
toolbar.iconbar.empty.pixmap:			bar.xpm

toolbar.iconbar.focused:			flat 
toolbar.iconbar.focused.pixmap:		focused.xpm
toolbar.iconbar.focused.textColor:	#ffffff
toolbar.iconbar.focused.justify:		center

toolbar.iconbar.unfocused:			flat 
toolbar.iconbar.unfocused.pixmap:		bar.xpm
toolbar.iconbar.unfocused.textColor:	#ffffff
toolbar.iconbar.unfocused.justify:      	center

toolbar.clock:                      			flat
toolbar.clock.pixmap:				bar.xpm
toolbar.clock.textColor:				#c0c0c0

toolbar.button:                     			flat
toolbar.button.pixmap:				bar.xpm
toolbar.button.picColor:            		#c0c0c0

! -- menu --

menu.title:						flat 
menu.title.pixmap:					menu.xpm
menu.title.justify:					center
menu.title.color:					#
menu.title.colorTo:					#
menu.title.textColor:				#2c2c2c
menu.title.font: 					Lucida Grande-0

menu.frame:						flat
menu.frame.pixmap:			        frame.xpm
menu.frame.justify:					left
menu.frame.color:					#
menu.frame.textColor:				#c0c0c0
menu.frame.disableColor:			#c0c0c0

menu.hilite:						flat
menu.hilite.color:					#1f1f1f
menu.hilite.textColor:				#ffffff

menu.bevelWidth:					1
menu.titleHeight:					6
menu.itemHeight:					12
menu.borderColor:					#1f1f1f
menu.borderWidth:					1
menu.bullet:		empty
menu.bullet.position:		Right
menu.submenu.pixmap:			bullet.xpm
menu.hilite.submenu.pixmap:	bullet_selected.xpm

! -- window --

window.title.focus:					flat
window.title.focus.pixmap:			bar.xpm
window.title.focus.color:			#
window.title.focus.colorTo:			#
window.title.unfocus:				flat
window.title.unfocus.pixmap:			bar.xpm
window.title.unfocus.color:			#
window.title.unfocus.colorTo:			#

window.label.focus:				flat
window.label.focus.pixmap:			bar.xpm
window.label.focus.color:			#
window.label.focus.colorTo:			#
window.label.focus.textColor:		#ffffff
window.label.unfocus:				flat
window.label.unfocus.pixmap:		bar.xpm
window.label.unfocus.color:			#
window.label.unfocus.colorTo:		#
window.label.unfocus.textColor:		#c0c0c0

window.button.focus:				flat
window.button.focus.color:      		#
window.button.focus.colorTo:      		#
window.button.focus.picColor:		#
window.button.unfocus:				flat
window.button.unfocus.Color:		#
window.button.unfocus.ColorTo:		#
window.button.unfocus.picColor:		#
window.button.pressed:				flat
window.button.pressed.color:		#
window.button.pressed.colorTo:		#
window.button.pressed.picColor:		#

window.close.pixmap:				close.xpm
window.close.unfocus.pixmap:		close.xpm
window.close.pressed.pixmap:		close_pressed.xpm

window.iconify.pixmap:				min.xpm
window.iconify.unfocus.pixmap:		min.xpm
window.iconify.pressed.pixmap:		min_pressed.xpm

window.maximize.pixmap:			max.xpm
window.maximize.unfocus.pixmap:	        max.xpm				
window.maximize.pressed.pixmap:		max_pressed.xpm

window.stick.pixmap:				bar.xpm
window.stick.unfocus.pixmap:		        bar.xpm
window.stick.pressed.pixmap:			bar.xpm

window.stuck.pixmap:				bar.xpm
window.stuck.unfocus.pixmap:		bar.xpm

window.handle.focus:				flat
window.handle.focus.color:			#1f1f1f
window.handle.focus.colorTo:			#1f1f1f
window.handle.unfocus:				flat
window.handle.unfocus.color:		#1f1f1f
window.handle.unfocus.colorTo:		#1f1f1f
window.handleWidth:				4

window.grip.focus:					flat
window.grip.focus.color:				#1f1f1f
window.grip.focus.colorTo:			#1f1f1f
window.grip.unfocus:				flat
window.grip.unfocus.color:			#1f1f1f
window.grip.unfocus.colorTo:			#1f1f1f

window.bevelWidth:					0
window.shade:					true
window.borderWidth:				1
window.borderColor:				#1f1f1f
window.justify:					Center
window.title.height:				18

*font:							lucida grande-6.8




What all should I change? And sorry to everyone about that post...

---

### Post by snowpine on 2009-01-29
Never edited a theme actually, but I bet you it's this line:

menu.title.font: Lucida Grande-0

Or it could be the very last line I guess.

Make a copy of the file, then you can mess with it all you want without screwing up the original.

Lots of nice themes at box-look.org, deviantart, etc. if you're looking for ideas.

---

### Post by toasty_ghosty on 2009-01-29
I'll just save a copy and keep editing it until it changes..

Thanks for the help.

---

### Post by RedSquirrel on 2009-01-30
The man page for **fluxstyle** has all the info about Fluxbox style settings (including fonts):

```
man fluxstyle
```You could comment out (put a '#' in front of) the lines in your style file that refer to a font setting and just put 

```
 *.font: Sans-12
```to make all the fonts the same size. You can also select fonts and font sizes for various components of Fluxbox:

```
            window.font:                    <font>
           menu.frame.font:                <font>
           menu.title.font:                <font>
           toolbar.clock.font:             <font>
           toolbar.iconbar.focused.font: <font>
           toolbar.iconbar.unfocused.font: <font>
           toolbar.workspace.font:         <font>
```

---

### Post by Tmi on 2009-01-30
I have the same problem, I've set the bakground in my init-file and it flashes by quickly in the startup before the theme takes over and sets its own background.

I'm using Ubuntu 8.10 where I installed fluxbox (sudo aptitude install fluxbox), so no "real" fluxbuntu. Thus I have no icons on the desktop and can't follow the tip given in the first reply.

The thing is, I put my wallpaper command last in my startup file, but it still seems to be loaded before themes and thus overwritten. Any ideas how this can be solved? I like to change themes a little now and then so it would be nice not to have to edit away wallpapers from every theme.

---

### Post by RedSquirrel on 2009-01-30
> **Tmi said:**
> I have the same problem, I've set the bakground in my init-file and it flashes by quickly in the startup before the theme takes over and sets its own background.

I'm using Ubuntu 8.10 where I installed fluxbox (sudo aptitude install fluxbox), so no "real" fluxbuntu. Thus I have no icons on the desktop and can't follow the tip given in the first reply.

The thing is, I put my wallpaper command last in my startup file, but it still seems to be loaded before themes and thus overwritten. Any ideas how this can be solved? I like to change themes a little now and then so it would be nice not to have to edit away wallpapers from every theme.

Create the file ~/.fluxbox/overlay, with the following line in it:

```
background: none
```This should prevent styles from setting a background.

---

### Post by yabbadabbadont on 2009-01-30
> **RedSquirrel said:**
> Create the file ~/.fluxbox/overlay, with the following line in it:

```
background: none
```This should prevent styles from setting a background.

It should, but I know that there was at least one version of fluxbox that ignored that setting...  one of the things that made me switch to openbox.  :D

It is fixed in the very latest fluxbox release though.

---

### Post by RedSquirrel on 2009-01-30
> **yabbadabbadont said:**
> It should, but I know that there was at least one version of fluxbox that ignored that setting...  one of the things that made me switch to openbox.  :D

It is fixed in the very latest fluxbox release though.

In Intrepid, the Fluxbox version is 1.0.0, so I think the overlay trick should work. (I cannot test it without installing that version since I'm running 1.1.1 at the moment.)

In the past, I've noticed some strange behaviour with setting the background in Fluxbox, but I haven't really played around with this feature recently. I've been using dwm or Openbox or fvwm or jwm or ... :)

I generally use a solid background anyway, so it's not a big issue for me:

```
$ cat .fluxbox/overlay 

background: solid
background.color: grey40
```

---

### Post by Tmi on 2009-01-31
Thank you, RedSquirrel. Your tip solved my problem.

---

