---
title: "Help! GTK apps slow after upgrading Ubuntu"
date: 2011-06-16
forum: Desktop Environments
---

### Post by tbraun on 2011-06-16
Hello!

I have recently upgraded my laptop from 9.10 to 10.04. All works
well, except that now my GTK-based applications seem to perform
slowly: Scrolling in web browsers, but (most annoying for me) 
also in gnome-terminal or gvim.

I have a Dell D820 with nVidia GeForce Go 7400 card, and use
the latest nVidia drivers that are available by default with 
10.04.

Under 9.10, I was able to use gnome-terminal even with anti-alias
fonts and it was fast and responsive. Now with 10.04, this is not
the case. Scrolling is much slower, CPU load is high. I changed
to non-aliased fonts, but they only provide a marginal 
improvement.

Note that the 3D effects in the desktop are smooth and fast.
And in non-GTK application - such as 'xterm' - scrolling is
very fast.

Also, once I switch off 'composite' in xorg.conf, the
scrolling performance is improved. However, I would rather keep
my nice composite desktop. Besides, under 9.10, I had composite
AND fast scrolling.

Any help or idea what is going on and how I can improve the
performance?

Thank you very much...

---

