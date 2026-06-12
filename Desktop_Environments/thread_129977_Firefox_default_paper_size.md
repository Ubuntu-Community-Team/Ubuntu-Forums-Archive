---
title: "Firefox default paper size"
date: 2006-02-15
forum: Desktop Environments
---

### Post by slux on 2006-02-15
After some serious Googling, Teomaing and fiddling with a bunch of variables in about:config I'm almost ready to give up but I'll give asking Ubuntuforums as a last resort a shot.

I currently have Letter set as the default paper size in Firefox on some Ubuntu breezy machines. As I'm located in Finland and the normal paper size here is A4 I'd like to change that but I've found no way to do that. I have, however found talks of a 3-year-old bug that apparently prevents the print dialog from remembering the paper size, forcing people to change it each time. I don't know if that's related but I'd simply like to change what it's originally set to. (I know it's possible since in some magic way I have one ubuntu installation where it's set to A4 and for no logical reason got changed to A5 while I played around with the various configuration vars)

I've tried changing print.postscript.paper_size and print.printer_PostScript/<default and printer name>.paper_name (and all the accompanying variables) and I've done the same with a few other variables as well (print.tmp... or something like that). 

I have /etc/papername set to a4, my locale is finnish (so LC_PAPER should presumably cause some apps to default to a4). I've checked that the printer's default paper size in Cups is A4. All of this fails to affect Firefox in any way.

I'm really unsatisfied with the Firefox print dialog at this point and almost ready to give up. This is part of a wider problem with Firefox, Openoffice.org and other Mozilla projects. In their quest to support every ancient unix install using CDE they refuse to depend on a modern Unix desktop environment or any other components that are readily available in most desktop Unixes. They have their very own file picker dialog, application defaults and a print dialog that apparently doesn't care about system locale settings. Some of these things are fixed with the Ubuntu Firefox version (firefox-gnome-support) but I've no idea if that's part of the official Mozilla Firefox. I wish they'd just understand the error of their ways and integrate to a desktop environment properly.

Ok, well, rant over but I'd be really, really happy if anyone could help me with this task that looks very simple on the surface but is certainly not. Anyone?

---

