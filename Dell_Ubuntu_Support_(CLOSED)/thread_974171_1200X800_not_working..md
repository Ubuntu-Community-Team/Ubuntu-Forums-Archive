---
title: "1200X800 not working."
date: 2008-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Twizz on 2008-11-07
I have a Dell XPS1530 and I just upgraded to 8.10.  Everything works fine, even better than 8.4, except I can not get 1200X800 to show up even as an option to choose it.  My normal screen resolution is 1440X900 and it works great, but I want to use 1200X800.  I've tried coping my old configuration to the new 8.10 install, and I even installed a fresh copy of 8.10, but nothing seems to work.  If I cant get it to work I'll probably just stick to 8.04 for a few more months.  I have Nvidia 8600M GT video card.

EDIT: I meant to say 1280X800 not 1200X800...

---

### Post by clw3388 on 2008-12-22
First.. what LCD do you have? 
Native resolutions:
  
 
WXGA
 1280 x 3 (RGB) x 800 at 262 K colors
 
WXGA+
 1440 x 3 (RGB) x 900 at 262 K colors
 
WSXGA+
 1680 x 3 (RGB) x 1050 at 262 K colors
 
Also are you using the restricted driver for the nvidia card? If so i suggest you stick with the resolution you have as i have edited the Xorg.conf file manually with the restricted driver and things break...
If not.. feel free to add to the xorg.conf

[http://kbase.redhat.com/faq/docs/DOC-5262](http://kbase.redhat.com/faq/docs/DOC-5262)

---

