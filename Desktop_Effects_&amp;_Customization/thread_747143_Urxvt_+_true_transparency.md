---
title: "Urxvt + true transparency?"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by Yes on 2008-04-06
I'm trying to get Urxvt to be truly transparent, instead of just displaying the desktop as the background.  Do I need something like Compiz?  I've found blogs about it online, but none of their Xdefaults seem to make my Urxvt transparent.  Here's my current Xdefults:

```
URxvt*geometry:			85x30
urxvt*background:  		rgba:0000/0000/0000/eeee
URxvt*foreground:       	#aaaaaa
URxvt*inheritPixmap:    	true
URxvt*reverseVideo:		false
URxvt*tintColor:        	#dfdfdf
URxvt*shading:	        50		
URxvt*fading:	        	70		!term unfocus      
URxvt*font:	     		xft:snap:size=10
URxvt*scrollBar:		false
URxvt*transparent: true
URxvt*borderLess: true
urxvt.depth: 32
urxvt*internalBorder: 4
urxvt.secondaryScroll: false

Xft.dpi:96
Xft.hinting:true
Xft.hintstyle:hintslight
```

Thanks.

---

### Post by x1a4 on 2008-04-19
Hi,

The only way I know how is to run **xcompmgr**, which is a generic compositing manager.  Then, using **transset** set the transparency.  

This is how I run them in OpenBox: 
```

xcompmgr -c -t-5 -l-5 -r4.2 -o.55 -f &
transset .7

```

When you run **transset** your cursor will turn into a cross.  Click the window you want to set transparency for.  When I figure out how to do it at application startup I'll let you know.

See the man pages for xcompmgr and transset for more information.

EDIT: If you want to set transparency each time time you start rxvt see [thread=760064]this thread[/thread] for information on how I managed to do it.

---

