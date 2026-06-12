---
title: "how to (re)install fonts in Breezy ?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by ivar on 2005-10-14
I recently upgraded to Breezy, and so far the only issue is that I lost my beloved 'ProFont' ( [http://www.tobias-jung.de/seekingprofont/](http://www.tobias-jung.de/seekingprofont/) ) as an option.. 
ProFont comes as a bunch of .pcf files.. after 'locate'-ing other .pcf files, it looks like font handling has changed in Breezy, with new folders being used, etc. 
I've copied my font files into all three font subfolders (100dpi, 75dpi, and misc) but it still doesn't show up as an option... 

So.. how does one install a new .pcf font ?

---

### Post by thewayofzen on 2005-10-14
Im not sure if this will help you.. but its what i did to make my pcf fonts work in breezy.  If it doesnt work for u i apologise but it DID work for me with my artwiz .pcf fonts.  I get tired of typing sudo all the time.. so i su'd into root.

1. I looked to find where my pcf fonts were..  (at some point i realised they were .gz i forget how)

root@SATORi:/etc/apt # locate cursor.pcf.gz
/usr/share/X11/fonts/misc/cursor.pcf.gz
/usr/share/X11/fonts/misc/olcursor.pcf.gz

2.   I took the .pcf fonts i wanted to install  (snap.pcf, edge.pcf, anorexia.pcf, etc)  and i did this:

root@SATORi:/home/delaney # gzip *.pcf

3.  I copied my new *.pcf.gz files into the above dir.

root@SATORi:/home/delaney # cp *.pcf.gz /usr/share/X11/fonts/misc/

4.  I did a dpkg-reconfigure fontconfig

root@SATORi:/home/delaney #dpkg-reconfigure fontconfig


Hope that helps.. if not.. good luck.

---

### Post by ivar on 2005-10-15
[QUOTE=thewayofzen]
4.  I did a dpkg-reconfigure fontconfig
Hope that helps.. if not.. good luck.[/QUOTE]

thank you, wayofzen.
your shared 'dpkg-reconfigure fontconfig' wisdom has helped me acheive font satori...

---

### Post by TheOrangeRider on 2005-11-01
Hi there,

I tried doing the above solution for ProFont, and it didn't seem to work for me. Did you have the .pcf and .gz files as root as the owner? Or did you use something other than default settings when running [FONT="Fixedsys"]dpkg-reconfigure fontconfig[/FONT]? I'm using Kubuntu so I'm also wondering if that might have something to do with it. I also tried installing the font using Konqueror and the System Settings and by putting the files in the default [FONT="Fixedsys"]$HOME/.font/[/FONT]. And I tried running fc-cache -fv... but none of these endeavors have proven fruitful :???:. Please let me know if you can shed some light on how I can install this font... it's my heart's desire!

Thanks!

EDIT: I found that installing the windows ttf file to be easily done using the GUI install. And that's all I need.

---

