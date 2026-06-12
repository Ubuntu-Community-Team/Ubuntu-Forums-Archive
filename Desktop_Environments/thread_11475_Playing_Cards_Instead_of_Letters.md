---
title: "Playing Cards Instead of Letters"
date: 2005-01-16
forum: Desktop Environments
---

### Post by ixus_123 on 2005-01-16
Am I missing fonts?  I've installed all the microsoft ones so I should have plenty(?)

It's just from time to time I will get squares that look like plying cards in the middle of text.  Please se picture

[IMG]http://img.photobucket.com/albums/v284/ixus_123/playingcards.jpg[/IMG]

---

### Post by Yukonjack on 2005-01-17
Have you check your /var/mail for system notice. I had to do this also.

[COLOR=Blue]TrueType and CID font paths which defoma manages have changed again.
Please add these entries to the "Files" section of /etc/X11/XF86Config-4:

  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

Also add these two directories to the "catalogue" path lists in
/etc/X11/fs/config and/or /etc/X11/fs-xtt/config, and delete any mention
of /usr/lib/X11/fonts/CID in any of these files.[/COLOR]

---

### Post by fng on 2005-01-17
/etc/X11/fs/config and /etc/X11/fs-xtt/config dont exist

```
fng@butters:/etc/X11 $ ls
app-defaults  default-display-manager  gdm      rstart     X             xinit  Xresources  Xsession    Xsession.options  Xwrapper.config
cursors       fonts                    rgb.txt  sysconfig  XF86Config-4  xkb    xserver     Xsession.d  xsm
fng@butters:/etc/X11 $

``` 

Should i make those files myself?

---

### Post by Yukonjack on 2005-01-17
After installing the ms fonts, edit the XF86Config-4 and it should look like this

[COLOR=Blue]Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/etc/X11/fs/config"
	FontPath	"/etc/X11/fs-xtt/config"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection[/COLOR]

---

