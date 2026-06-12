---
title: "Firefox 1.5 keeps closing for no reason"
date: 2006-01-06
forum: General Help
---

### Post by phiphedog on 2006-01-06
I'm running Ubuntu Hoary 5.04 and I just installed Firefox 1.5 and when i start it up it just closes after about 10-20 seconds.

I downloaded Firefox 1.5 from the firefox-1.5.tar.gz from the mozilla website and installed it to /usr/share with the command:

tar -zxvf firefox-1.5.tar.gz from the /usr/share directory.

I am starting Firefox from /usr/share/firefox/firefox and it loads fine but then closes for no reason.

I have read this post [http://ubuntuforums.org/archive/index.php/t-52875.html](http://ubuntuforums.org/archive/index.php/t-52875.html) with the same problem but on Breezy that says to:
sudo gedit /usr/bin/firefox

find these strings into the file:

MOZ_ENABLE_PANGO=1
export MOZ_ENABLE_PANGO

and put comment like this:

#MOZ_ENABLE_PANGO=1
#export MOZ_ENABLE_PANGO

save the file and start firefox

But i have no firefox file in /usr/bin and when I gedit my /usr/share/firefox/firefox  file I can not find any reference to MOZ_ENABLE_PANGO=1 or export MOZ_ENABLE_PANGO

Any suggestions to get firefox 1.5 working?

---

