---
title: "Gnome System Extension updates on Ubuntu Gnome"
date: 2017-03-30
forum: Desktop Environments
---

### Post by kevindontenville on 2017-03-30
HI all

Just noticing nearly all the system extensions for UbuntuGnome 16.04 are showing on extensions.gnome.org as out of date and ready for update. 

Will they be updated by UbuntuGnome project via an update to the default extensions in the repo or is there some other preferred way of updating them?

The ones I have installed as a user are updating fine but using the web update on system installs seems to quickly tail-spin!

Thanks

K

---

### Post by kurt18947 on 2017-03-30
I noticed a bunch of updates recently as well. I go to 'extensions.gnome.org' click on 'installed extensions' and the extensions with updates available should have a green icon. Click the green icon and the extension should update. If you haven't used that page before, you may need to give the update mechanism permission to run.

---

### Post by kevindontenville on 2017-04-11
Thanks for getting back to me. Yes, I find I can readily apply the updates for extensions I download from Gnome site, they update fine. The ones installed as system extensions, don't. Not seen anywhere that has asked for or could be given perms to run as root/sudo.  

If I just try to get them to update they they appear to work then 'blow up' and become unconfigurable, ie cant enable, remove or change settings. They obviously don't actually upgrade as they cant write to system areas so I presumed they would update via Ubuntu Gnome Repos, but that doesnt seem to be the case either - yet ;-)

Nothing appears to be actually broken, but I prefer to apply updates when possible as soon as possible.

Any more clues would be good!

K

---

### Post by kurt18947 on 2017-04-12
My ignorance has prevailed over my google-fu.  What are system extensions? Example please?

---

### Post by kevindontenville on 2017-04-12
After shifting up Firefox the system extensions seem to be updating. Maybe something to do with the plugin framework changing but it seems they ae now applying successfully.

It was probably just me ;-)

NB System Extensions: eg Launch New Instance. Workspace Indicator, etc - essentially the pre-installed extensions not the user installed ones. (often fmuellner ones!)

---

### Post by kurt18947 on 2017-04-12
Ah, okay. I don't use any of those so I'd never have noticed an issue. I did use Window List for a while but replaced it with TaskBar. TaskBar was ill-behaved early on but it seems pretty reliable these days.

---

### Post by bcbuch on 2017-04-13
I've upgraded 16.10 to 17.04 on my daily driver some time back after a clean install of 16.10. extensions.gnome.org would not work in either Firefox or Chrome. I ended up installing Epiphany to get the extensions working. I then ran sudo apt-get full-upgrade after installing all the software that I use and proprietary drivers. Somewhere in there everything ironed out. Currently I'm downloading 17.04 64 and 32 bit iso's to fresh install all systems. Should be an interesting year as Canonical migrates the default desktop to Gnome.

---

