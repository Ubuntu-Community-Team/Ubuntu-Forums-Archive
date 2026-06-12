---
title: "Advise for reinstall please"
date: 2009-01-21
forum: General Help
---

### Post by PoopyTheJ on 2009-01-21
Ok, I've currently got Hardy 8.04 installed on a 20GB drive with my /home partition on a seperate 250GB partition. There are a number of issues with my current 8.04 install which I want to fix and I'm sure some of them have to do with the programs installed on my Home partition. I'd like to reinstall with 8.10 but I don't know if intrepid will use the ATI drivers, I know when it came out it was a nightmare getting the proprietary drivers to work is this still the case? Also if I reinstall and don't set my current /home partition as home, but instead create simlinks to the folders I want, pictures,movies,etc, can I simply grab my bookmarks and email addresses and email messages from my old evolution and firefox installs? I'm thinking this will get rid of some of the issues I've been facing, Firestarter doesn't start at boot, evolution prompts for akeyring password which is from a very old install, slow boot up, boot screen is text rather than the nice new gui, xine crashing randomly etc.
One final and major issue is I can't for the life of me get samba to work to share files between my XP and Ubuntu PC's. This is very important as the XP PC has a very small HDD in it.

---

### Post by HermanAB on 2009-01-21
Regarding re-install - try the live CD first and see whether it works with your video adaptor.

If you re-install and DON'T reformat /home, then all your data and user settings will still be there.

Regarding Samba, see this:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by PoopyTheJ on 2009-01-21
though if in the reinstall I don't choose to mount my current home as home and instead just choose to have home on the / mount point it won't be home right?

---

### Post by PoopyTheJ on 2009-01-21
yep that worked!

---

