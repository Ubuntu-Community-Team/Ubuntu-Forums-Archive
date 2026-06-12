---
title: "Xorg won't start (after font removal)"
date: 2005-06-10
forum: Desktop Environments
---

### Post by bonvenon on 2005-06-10
When I try to start the x server I just get to the ubuntu splash image, then the server stops and I'm beeing sent back to the terminal. I can't understand what the problem is.
Before this happened at the firt time, I had just removed a bunch of fonts that I didn't think I needed. I don't know if that is what caused the problem. If that is the case, how do I reinstall the fonts?

My Xorg.0.log is available here: [http://webbform.net/Xorg.0.log](http://webbform.net/Xorg.0.log) 

I hope someone might have an idea of what the problem is.

---

### Post by Xian on 2005-06-10
[QUOTE=bonvenon]When I try to start the x server I just get to the ubuntu splash image, then the server stops and I'm beeing sent back to the terminal.[/QUOTE]

Looks like the message below might be your problem.
Did you remove or change the fonts/paths in that directory?

```
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
```

---

### Post by bonvenon on 2005-06-11
[QUOTE=Xian]Looks like the message below might be your problem.
Did you remove or change the fonts/paths in that directory?

```
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
```[/QUOTE]

I also thought that might be the problem, but I don't know what to do about it.
I removed the fonts by using Nautilus at fonts:/// as root. If I knew which package that contains the fonts I suppose I could try to reinstall it, but I don't know that.

I have uploaded my xorg.conf here: [http://webbform.net/xorg.conf](http://webbform.net/xorg.conf) - as you can see 'Load "speedo"' is in the Module section.

Any ideas?

---

### Post by Xian on 2005-06-11
That font section looks a bit odd in your xorg.conf. You might try commenting out the ~/X11/fonts/Speedo/ path, but it is so different from mine I'd be hard pressed to approach what the proper configuration should be.

Here is my module and font section:

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection
```

```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection
```

---

### Post by bonvenon on 2005-06-11
Hi!

I finally solved the problem by reinstalling the xserver-common package:
```
sudo apt-get install xserver-common --reinstall
```

---

### Post by desdinova on 2005-06-11
You probably removed the fixed fonts - a big nono - X relies on some bare bones fonts as a fallback mechanism...

---

