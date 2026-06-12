---
title: "Firefox in swedish?"
date: 2008-08-18
forum: Desktop Environments
---

### Post by Diskdoc on 2008-08-18
Hi!

I´m having trouble localizing the menus in Firefox. I installed the necessary language extension through Synaptic but they won´t show up in the add-ons-lists in either Firefox 2 or 3! #-o

I´ve poked around a bit with about:config too, following forum guidelines but to no avail.

My boss wants two computers with Firefox to have the browser in Swedish because the Google work enviroment our school uses automatically selects language according to what the browser is set to..

I know it´s possible to download and manually install Firefox in swedish but it seems a clumsy solution when it SHOULD work more smoothly.

/ Carl

---

### Post by mcduck on 2008-08-19
If it's ok to run the whole desktop in swedish (as compared to only running Firefox in swedish) just install the complete swedish language support, and in the login screen select swedish as the language...

---

### Post by Diskdoc on 2008-08-19
Thanks for your reply! It´s definately what we strive for here, a swedish desktop. I thought I did just that but Firefox hasn´t been effected language- or locale wise. I´ll be sure to double check this and report a bug if I can´t find anything wrong with my settings.

The best solution for our problem I have been able to think of so far is to download the Firefox add-on "Quick locale switcher" and set it to sv-FI (our locale). The browser then reports the correct locale to the Google apps which in turn serve the pages in swedish where appropriate,

/ Carl

---

### Post by Diskdoc on 2008-08-19
I´ll be damned! The swedish language support wasn´t completely installed after all! In the language section there was a "-" instead of a normal checkmark. Firefox works perfectly in swedish now and the locale reports correctly as well.

Cheers,
Carl

---

### Post by mcduck on 2008-08-19
You mentioned both Firefox 2 & 3.. What version of Ubuntu are you running, and are the browsers isntalled from Ubuntu's repositories or in some other way?

The last time I installed Ubuntu with both english & finnish language support selecting finnish as language from the login screen changed all programs, including Firefox, to finnish.

Anyway, check that you have all these packages installed:
language-support-sv
language-pack-sv
language-pack-sv-base
mozilla-firefox-locale-sv-se
language-pack-gnome-sv-base
language-pack-gnome-sv

edit: oh, you already got it solved.. :)

---

### Post by sundman on 2012-02-15
And in newer versions (FF 10) the locale package is named

firefox-locale-sv

just for the record.

---

