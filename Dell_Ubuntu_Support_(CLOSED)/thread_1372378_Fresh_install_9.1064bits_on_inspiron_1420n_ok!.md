---
title: "Fresh install 9.10/64bits on inspiron 1420n ok!"
date: 2010-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by marsopia on 2010-01-04
I recently upgraded my Inspiron 1420n from 2Gb of Ram to 4, so I decided to upgrade my OS to 64bits one to take plenty advantage form the 4gigs.

I proudly have my Inspiron with 7.10 32bits preintalled since a year and a half. I made successive upgrades to 8.04, 8.10, 9.04 and 9.10 without problems. 

I downloaded a Ubuntu Desktop 9.10/64 iso, burned it to a Cd and made a fresh install keeping Dell's sistem and os partitions, erasing the ext3 partition and creating a new one for the new install using native ext4.

I had my fears doing this new upgrade, but everything seems to work fine and mostly out of the box, except flash. After installing gnash I wasn't able to watch online videos, but after installing nonfree flash, youtube came to life...

Wifi works fine, just finished the installation, looked for my connection and made the final update via wifi; sound works ok, so does the intel graphic card with a resolution of 1200x800 without blanc screens; keyboard is ok, even shortcuts as Fn+F10 to expel the DVD, something I love. Touchpad without problems, and front panel lights blinking perfectly well...

I am listening radio via Rythmbox just now and installing my favorite apps... 
Only thing I miss is LinDVD, but I found in forums I could call Canonical, and after verifing that LinDVD was shipped with my laptop they'll send me a link to download a new version.

Any issue I find while I use my "new" laptop, I'll let you know.

Happy new year!

Mariano

---

### Post by bobcollard on 2010-01-04
> **marsopia said:**
> I recently upgraded my Inspiron 1420n from 2Gb of Ram to 4, so I decided to upgrade my OS to 64bits one to take plenty advantage form the 4gigs.

I proudly have my Inspiron with 7.10 32bits preintalled since a year and a half. I made successive upgrades to 8.04, 8.10, 9.04 and 9.10 without problems. 

I downloaded a Ubuntu Desktop 9.10/64 iso, burned it to a Cd and made a fresh install keeping Dell's sistem and os partitions, erasing the ext3 partition and creating a new one for the new install using native ext4.

I had my fears doing this new upgrade, but everything seems to work fine and mostly out of the box, except flash. After installing gnash I wasn't able to watch online videos, but after installing nonfree flash, youtube came to life...

Wifi works fine, just finished the installation, looked for my connection and made the final update via wifi; sound works ok, so does the intel graphic card with a resolution of 1200x800 without blanc screens; keyboard is ok, even shortcuts as Fn+F10 to expel the DVD, something I love. Touchpad without problems, and front panel lights blinking perfectly well...

I am listening radio via Rythmbox just now and installing my favorite apps... 
Only thing I miss is LinDVD, but I found in forums I could call Canonical, and after verifing that LinDVD was shipped with my laptop they'll send me a link to download a new version.

Any issue I find while I use my "new" laptop, I'll let you know.

Happy new year!

Mariano
Instead of using Gnash, open Synaptic Package Manager and type flash into the search bar.  In the results get flashplugin-installer and flashplugin-nonfree.  This will open anything in your browsers.  flashplugin-installer may already be installed.  Then uninstall Gnash.

---

### Post by LMP900 on 2010-01-04
I also have an Inspiron 1420n. I am using Ubuntu 9.10 32-bit and the only significant issue is the screen not going blank after closing the lid.

After waking from suspend mode, however, it works as it should.

---

### Post by bobcollard on 2010-01-04
> **LMP900 said:**
> I also have an Inspiron 1420n. I am using Ubuntu 9.10 32-bit and the only significant issue is the screen not going blank after closing the lid.

After waking from suspend mode, however, it works as it should.
Check your Power management settings for your lid switch.

---

### Post by LMP900 on 2010-01-06
> **bobcollard said:**
> Check your Power management settings for your lid switch.

Yep, it's set to "blank screen." Others seem to have a similar issue, but the suspend-first workaround is good enough for now.

(BTW, I'm a fellow central Illinois Ubuntu user :))

---

### Post by bobcollard on 2010-01-07
> **LMP900 said:**
> Yep, it's set to "blank screen." Others seem to have a similar issue, but the suspend-first workaround is good enough for now.

(BTW, I'm a fellow central Illinois Ubuntu user :))
Cool. well watch the forum for another workaround.  Sorry it didn't work.  A fellow Illini?  Great.

---

### Post by marsopia on 2010-01-09
Thanks Bob for your suggestion!
It works properly now.

Mariano

---

