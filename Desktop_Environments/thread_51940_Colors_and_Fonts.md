---
title: "Colors and Fonts"
date: 2005-07-25
forum: Desktop Environments
---

### Post by Ian Gordon on 2005-07-25
I am wondering how I can change my colors to millions of colors rather than the 65K i think it is on now.

Also, I am wondering why the fonts for Firefox are so small even though they seem to be the correct display on other machines. Can this be fixed? I think someone in a another thread mentioned QT?

Let me know, thanks.

---

### Post by pampa on 2005-07-26
There is no graphical way that I know of to change it.  What you need to do is to open a terminal and run:

```
sudo gedit /etc/X11/xorg.conf
```

In the text file go to the Screen Section where you see something like:
```
	
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection

``` 

There might be other modes that are commented ... uncomment them if you want.

Now, at the beginning of the section you have something like:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24

``` 

Change DefaultDepth value to one of those depth you want.  After that, restart X Windows by logging out and pressing CTRL+ALT+Backspace

Hope it is undertandable.

---

