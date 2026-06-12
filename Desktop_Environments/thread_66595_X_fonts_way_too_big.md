---
title: "X fonts way too big"
date: 2005-09-17
forum: Desktop Environments
---

### Post by brockjudkins on 2005-09-17
(Edit: attached screenshot)

Hi all!

When I start up an application such as emacs or ddd, they look way too big. The font size on everything look a few points to high. This is with a freshly installed Ubuntu Hoary dist.

Emacs' default size, for instance, takes up (by deafult) about 85% of my 1024x768 display  :-?. Not that I want just the window size to decrease, but I also want the fonts be smaller too.

I am the only one who has encountered this?
How do you adjust the size?

Much less importantly: is there a cool app out there to tweak the "X" look?  :-# 

Shukran!
Brock


Part of my xorg.conf:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

---

### Post by brockjudkins on 2005-10-02
OK i finally found the answer myself on a Debian how-to. 

It was easy! Is this not very well known, or was it just a stupid question?

You just switch the order of the FontPath lines that say 100 dpi and 75 dpi in the xconf file, found in /etc/X11/xorg.conf. That is, the lines that have "75 dpi" should be first.

---

### Post by rajan on 2006-06-08
good call on this... i might add that you need to reboot (this is probably true any time you change X11 settings, but i wasn't sure)

---

### Post by httpnetworks.com on 2006-06-23
I think I have found the solution. It's to do with kdm

edit /etc/kd3/kdm/kdmrc

change
ServerArgsLocal=-nolisten tcp

to 
ServerArgsLocal=-dpi 96 -nolisten tcp

Restart the xserver.

---

### Post by stu bon 5k on 2008-04-10
i have the same exact problem, but in xorg.conf file , the files section has nothing in it. i cant make the changes necessary to fix the problem

---

