---
title: "Lynx downloads without lauching file-roller"
date: 2008-08-09
forum: Desktop Environments
---

### Post by sgornick on 2008-08-09
Not sure if this is something new in Hardy or if I just never noticed it before but even though I am using the Lynx text mode browser to download a gzipped file, the file-roller gui tool will still launch after the file is downloaded.

I'm using terminal window for a reason and thus I don't want any gui utilities.  I did figure out a workaround ... disable the DISPLAY=:0.0 environment variable and lynx will then act the way I want it to.

$ unset DISPLAY
$ lynx

This is obviously not the best way to solve the problem, as I don't want to always go without DISPLAY=:0.0, but I couldn't figure out where else I can tell Lynx to not use file-roller.  

I am assuming it has to do with mime-type but I couldn't figure out what to change to cause Lynx to use its built-in download (text mode) to handle gzip files.

---

### Post by pauper on 2008-08-10
Hmm. Let say you go to [http://www.gnu.org/software/coreutils/manual](http://www.gnu.org/software/coreutils/manual) and high-
light "HTML compressed (232K bytes gzipped)". Then press "d" (DOWNLOAD), select
"Save to disk", press Enter or Right Arrow--enter proper path, press Enter.
And a while later file-roller pops up?

Try uncommenting (line 3380?) in /etc/lynx.cfg

#GZIP_PATH:

---

### Post by sgornick on 2008-08-11
> Then press "d" (DOWNLOAD), 

Oh man, am I embarrassed.  I was pressing enter on the link, rather than pressing "d".  If I press "d", lynx will ask me if I want to download ... which is what I want.   Apparently if I press enter, lynx tries to launch the appropriate app and uses the mimetype to know which app to launch.

Problem solved.  Thank you for the help.

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

