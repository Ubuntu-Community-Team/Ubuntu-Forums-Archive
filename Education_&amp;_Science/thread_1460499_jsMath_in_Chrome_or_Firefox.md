---
title: "jsMath in Chrome or Firefox"
date: 2010-04-22
forum: Education &amp; Science
---

### Post by SnickerSnack on 2010-04-22
Hi all,

I need to install jsMath fonts in either Google Chrome (5.0.342.9 beta) or Firefox (3.5.9) (or both, of course).  When I go to a site that uses it, like planetmath.org, formulas don't render, _and the buttons to open the jsmath Control Panel don't work_.

I might be able to find the fonts somewhere, but I doubt that alone will help with the fact that jsMath doesn't seem to be working at all.

As far as I know, I have java installed correctly.

I tried 'sudo apt-get install jsmath', but that appears to install jsmath to a webserver, not enable it in a browser.

Help?

---

### Post by euclidean on 2011-01-31
You posted quite a while ago but, in case anyone else needs the info...

1) You can find the free jsMath fonts here:

[http://www.math.union.edu/~dpvc/jsmath/download/jsMath-fonts.html](http://www.math.union.edu/~dpvc/jsmath/download/jsMath-fonts.html)

Remember to download the "extra" fonts linked at the bottom of the page as well as the main ones.

2) You don't need Java. The JSMath javascript is sent to your browser automatically.

3) I also have problems with the jsMath control panel on PlanetMath - using Opera 11, Firefox, Konqueror, and Midori all on Lucid. The pages render the fastest on Midori and Konqueror and very slow (and CPU intensive) on Opera.

---

### Post by sekhar12 on 2011-02-01
It has been working well in Firefox.

---

### Post by euclidean on 2011-02-01
Does the jsMath control panel work for you on PlanetMath? Which version of FF and *buntu are you using?

Tangent to this - I set up mathJax on a server recently and was surprised how incredibly easy it was (and how smoothly it worked in all browsers).

---

### Post by SnickerSnack on 2011-02-18
Thanks euclidean.

I installed the main fonts, and things starting working okay in Chromium (9.0.597.84 (72991) Ubuntu 10.10) and FF (v 3.6.13), but they were loading pretty slowly (since it loads images).  FF complained about not having cmmib10.ttf, so I installed that from the extras page, which seems to have either made chromium loads jsmath faster or ff load slower.

I still can't open the jsmath control panel in any case.

---

