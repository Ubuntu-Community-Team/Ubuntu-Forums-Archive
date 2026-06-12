---
title: "wget -O option with input file"
date: 2013-09-15
forum: Desktop Environments
---

### Post by Geoff_Lane on 2013-09-15
wget is an excellent download manager but wonder if anyone can tell me if this is possible.

I have a TV recorder which lists programs by their name but files them under an incrementing number system.

I know I can batch download using a text file listing the individual URLs and thought that putting -O 'filename' after the URL would work, it don't :(

Individual files no problem and usually this is OK but sometimes I have to transfer a number of recorded programs and it is annoying having to wait for each one to finish before starting another.

Geffers

---

### Post by Lars Noodén on 2013-09-15
You can't do [globbing](http://manpages.ubuntu.com/manpages/raring/en/man7/glob.7.html) with HTTP.  If I understand correctly it only works with FTP.  So if you can set up Anonymous FTP for downloads then you could use globbing.

The other way around it would be to make a script which predicts the file names used by your recorder and have that call wget.  It would be best though to let them download one at a time, one after the other, because trying to download in parallel would just add overhead to an already saturated network.  Can you provide an example of some of the URLs as you would use them?  A script might be easy.

---

