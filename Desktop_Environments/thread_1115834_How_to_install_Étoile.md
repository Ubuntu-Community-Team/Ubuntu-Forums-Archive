---
title: "How to install Étoile?"
date: 2009-04-04
forum: Desktop Environments
---

### Post by field33P on 2009-04-04
I readed online about the Étoile Desktop Environment, but I don´t know how to install it.

Can someone help me out?

---

### Post by afrodeity on 2009-06-28
> **field33P said:**
> I readed online about the Étoile Desktop Environment, but I don´t know how to install it.

Can someone help me out?

apparently there is an install script ubuntu-install-etoile.sh but not sure where to get it.

You have to install GNUstep from particular packages. Here are [general instructions]("http://etoileos.com/downloads/install/") and [more specific for ubuntu]("http://etoileos.com/downloads/install/ubuntu/")

Here is an early [guide.]("http://etoileos.com/news/archive/2006/08/29/2050/")

I haven't managed to get it to work yet mainly because of the unique GNUstep environment it requires. The GNUstep in the repo isn't up to date, and the gnustep-startup-0.23.0 installer gives you this:
```

afrodeity@afrodeity-desktop:~$ dpkg -l | grep gnustep
ii  gnustep-base-common                        1.14.1-2ubuntu1                                            GNUstep Base library - common files
ii  gnustep-base-runtime                       1.14.1-2ubuntu1                                            GNUstep Base library
ii  gnustep-common                             2.0.2-1                                                    Common files for the core GNUstep environmen
ii  libgnustep-base1.14                        1.14.1-2ubuntu1                                            GNUstep Base library
afrodeity@afrodeity-desktop:~$ 

```

with the following result from Etoile setup.sh

```

Your GNUstep environment isn't set up correctly. To install Etoile, you must source GNUstep.sh or GNUstep.csh located in System/Library/Makefiles/GNUstep.sh

```

If I get any further, will let you know.

---

### Post by cyborgx7 on 2011-08-12
I know this is 3 years old but I'd like to rreopen it.
Is there an 'easy' way(I know it's not going to be easy but maybe there is one for somebody who lacks experience) to get Étoilé running on Ubuntu Natty Nahrwahl? Or can somebody who did it give me a step by step tutorial?

---

### Post by Duncan Williams on 2011-08-12
[http://www.google.com/search?q=Etoile#pq=etoile&hl=en&cp=8&gs_id=d&xhr=t&q=Etoile+ubuntu&qe=RXRvaWxlIHU&qesig=_8xdJy3udy-P-vF7AOmKcg&pkc=AFgZ2tmq-eP7h9747uEZzSIMF0IqJ-c7ZJKD0U4Xcstl68Lm7UJggEHMEl25H4eVK88XGzBk_vFbife1_DXtgjsmrXdIGMjznQ&pf=p&sclient=psy&source=hp&pbx=1&oq=Etoile+u&aq=0&aqi=g1g-s2g2&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=1a2cc6000ca7d280&biw=1109&bih=640](http://www.google.com/search?q=Etoile#pq=etoile&hl=en&cp=8&gs_id=d&xhr=t&q=Etoile+ubuntu&qe=RXRvaWxlIHU&qesig=_8xdJy3udy-P-vF7AOmKcg&pkc=AFgZ2tmq-eP7h9747uEZzSIMF0IqJ-c7ZJKD0U4Xcstl68Lm7UJggEHMEl25H4eVK88XGzBk_vFbife1_DXtgjsmrXdIGMjznQ&pf=p&sclient=psy&source=hp&pbx=1&oq=Etoile+u&aq=0&aqi=g1g-s2g2&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=1a2cc6000ca7d280&biw=1109&bih=640)

---

