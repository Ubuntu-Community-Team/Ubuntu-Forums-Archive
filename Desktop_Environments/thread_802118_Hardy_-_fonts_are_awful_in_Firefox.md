---
title: "Hardy - fonts are awful in Firefox"
date: 2008-05-21
forum: Desktop Environments
---

### Post by netron on 2008-05-21
I upgraded my laptop from Gutsy to Hardy , and fonts on certain websites are terrible as a result  - [http://forum.openx.org](http://forum.openx.org)  is a good example.


another is : [http://www.w3schools.com/php/php_ref_date.asp](http://www.w3schools.com/php/php_ref_date.asp)

so i did a completely fresh install on a desktop PC, and again, the "ugly" fonts issue came up again.   i dont recall Gutsy ever being this bad - so is it more of a Firefox 3 issue? 

apt-get installing the msttcorefonts package has rectified the ugly fonts somewhat.  why has font rendering gotten so awful in Hardy? there must be a fundemental bug somewhere.

any thoughts anyone?

(i'll post screenshots from the fresh Hardy install in just a sec)

---

### Post by netron on 2008-05-21
screengrabs attached.

screenshot 1 is from a fresh hardy install - before installing msttcorefonts.  firefox 3 beta 5



screenshot 2 is after i apt-getted msttcorefonts and restarted firefox.

---

### Post by Vadi on 2008-05-21
In Firefox font option, there's an option to let websites use their own fonts or something. Try toggling that. I remember solving my problem like that.

---

### Post by netron on 2008-05-21
"Allow pages to choose their own fonts, instead of my selections above"
is ticked.


interestingly , Konqueror fonts appear to render just fine - so maybe its a fundemental font rendering bug in GTK or maybe Firefox 3 itself?

---

### Post by Vadi on 2008-05-21
I said toggle, so what happens when you disable it?

---

### Post by jjgomera on 2008-05-21
Go to System/font, details, outline, and mark none

I had that problem in gutsy too

---

### Post by netron on 2008-05-21
FIXED...

from this reddit posting:

[http://reddit.com/info/6hfhn/comments/](http://reddit.com/info/6hfhn/comments/)


edit /etc/fonts/conf.d/30-metric-aliases.conf

replace all occurences of Nimbus Sans L  with DejaVu Sans

also , replace all occurences of Liberation Sans with DejaVu Sans

restart firefox, and you should now have nice font rendering - at least on websites that use Helvetica or Arial.

---

### Post by DonnieP on 2008-07-04
> **netron said:**
> FIXED...

from this reddit posting:

[http://reddit.com/info/6hfhn/comments/](http://reddit.com/info/6hfhn/comments/)


edit /etc/fonts/conf.d/30-metric-aliases.conf

replace all occurences of Nimbus Sans L  with DejaVu Sans

also , replace all occurences of Liberation Sans with DejaVu Sans

restart firefox, and you should now have nice font rendering - at least on websites that use Helvetica or Arial.
An alternative solution I discovered today is to just install the Liberation Fonts from Synaptic.  The difference in Firefox (without changing my system fonts [DejaVu] and with allowing sites to choose their own fonts) is amazing.

---

### Post by bluzepher on 2008-07-04
> **Vadi said:**
> In Firefox font option, there's an option to let websites use their own fonts or something. Try toggling that. I remember solving my problem like that.

can someone tell me how to do this?

I would love to let the websites chose their own fonts, cant find the option >


Thanks

---

### Post by reddox on 2008-07-04
> **bluzepher said:**
> can someone tell me how to do this?

I would love to let the websites chose their own fonts, cant find the option >


Thanks

In Firefox, open the Edit menu->Preferences

Click on the 'Content' tab. Click 'Advanced'. 

:)

You will find the option here.

---

### Post by reddox on 2008-07-04
> **netron said:**
> FIXED...

from this reddit posting:

[http://reddit.com/info/6hfhn/comments/](http://reddit.com/info/6hfhn/comments/)


edit /etc/fonts/conf.d/30-metric-aliases.conf

replace all occurences of Nimbus Sans L  with DejaVu Sans

also , replace all occurences of Liberation Sans with DejaVu Sans

restart firefox, and you should now have nice font rendering - at least on websites that use Helvetica or Arial.

AWESOME find!! Thank you!!:guitar:

---

