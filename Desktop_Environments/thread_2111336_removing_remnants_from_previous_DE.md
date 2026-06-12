---
title: "removing remnants from previous DE"
date: 2013-02-01
forum: Desktop Environments
---

### Post by Baldrick_NZ on 2013-02-01
I decided to test Edubuntu installed from the software centre for my wife to test from a teaching perspective. 
I expected it would install separately to my installed Ubuntu, and would appear as an option when at log-in. Instead it installed over top of my installation!

Wanting to revert to Ubuntu, I uninstalled Edubuntu, but am still left with some annoying Edubuntu stuff, namely...

1/ On start-up I now get an ugly Edubuntu splash, not the preferred  purple start up screen;

2/ The BFB icon on the top left of the screen is Edubuntu;

3/ My log in screen is just purple, I can't seen to change it to a pic of my own.

I've tried to change these using Ubuntu Tweak, Dconf, Gconf, etc... to no avail. Having said that, the answer is probably within one of these apps, but I'm simply missing it.

Any help to sort these minor (but really annoying) issues would be very much appreciated!

Kind regards,
Baldrick

---

### Post by zombifier25 on 2013-02-02
The edubuntu-package is merely a meta package that automatically pulls in the Edubuntu stuffs (educational apps, bootup screen,...). If you want to remove Edubuntu, you need to manually remove the packages it provides. [This page may help](http://www.psychocats.net/ubuntu/pureubuntu).

---

### Post by Baldrick_NZ on 2013-02-02
> **zombifier25 said:**
> The edubuntu-package is merely a meta package that automatically pulls in the Edubuntu stuffs (educational apps, bootup screen,...). If you want to remove Edubuntu, you need to manually remove the packages it provides. [This page may help](http://www.psychocats.net/ubuntu/pureubuntu).

Thanks heaps for your help! 

While I had already removed Edubuntu using software centre, trying your suggestion didn't work for me. However, it did point me in the right direction. I launched Synaptic and bought up 'Edubuntu' and removed all such entries, which in turn solved points 1 & 2. 
A quick google search bought up this, [http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594), which fixed point #3.

Thanks again for pointing me in the right direction. :-)

---

