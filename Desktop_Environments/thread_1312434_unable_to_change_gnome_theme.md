---
title: "unable to change gnome theme"
date: 2009-11-03
forum: Desktop Environments
---

### Post by SpUpUz on 2009-11-03
as shown in the screeshot i can't change gnome theme in the Karmic Koala 9.10 i come from upgrade done thru the all alpha and beta stages.

Ubuntu 9.10

Thanks

---

### Post by dzon65 on 2009-11-03
Upgrades can be tricky,have you tried a fresh install?

---

### Post by SpUpUz on 2009-11-03
> **dzon65 said:**
> Upgrades can be tricky,have you tried a fresh install?

everything is working like a charm i would try to find out a solution before.

---

### Post by alienclone on 2009-11-03
have you tried installing a theme manually? 
download a theme from gnome-look.org then drag the package into the box that you took the screenshot of.

---

### Post by emigrant on 2009-11-03
see what is inside the theme folder:

```
ls -a /usr/share/themes/
```

---

### Post by SpUpUz on 2009-11-03
> **emigrant said:**
> see what is inside the theme folder:

```
ls -a /usr/share/themes/
```

belloa@belloa-laptop:~$ ls -a /usr/share/themes/
.                              Industrial                     Shiki-Illustrious
..                             Inverted                       Shiki-Noble
AgingGorilla                   Lush                           Shiki-Wine
Amaranth                       MagicChicken                   Shiki-Wise
Atlanta                        Metabox                        Simple
Bluecurve                      Mist                           SphereCrystal
BlueHeart                      Mythbuntu                      ThinIce
Bright                         New Wave                       Unity
CleanIce                       New Wave Dark Menus            Wasp
CleanIce-Dark                  Nodoka                         Xfce
CleanIce-Debian                Nodoka-Aqua                    Xfce-4.0
Clearlooks                     Nodoka-Gilouche                Xfce-4.2
ClearlooksClassic              Nodoka-Looks                   Xfce-4.4
CortlandChicken                Nodoka-Midnight                Xfce-b5
Crux                           Nodoka-Rounded                 Xfce-basic
Darklooks                      Nodoka-Silver                  Xfce-cadmium
DarkRoom                       Nodoka-Squared                 Xfce-curve
Default                        Nuvola                         Xfce-dawn
Dust                           Nuvola-old                     Xfce-dusk
Dust Sand                      OkayishChicken                 Xfce-kde2
Emacs                          QtCurve                        Xfce-kolors
Esco                           Raleigh                        Xfce-light
Galaxy                         Redmond                        Xfce-orange
Gorilla                        Shiki-Brave                    Xfce-redmondxp
HighContrastInverse            Shiki-Colors-Easy-Metacity     Xfce-saltlake
HighContrastLargePrintInverse  Shiki-Colors-Metacity          Xfce-smooth
Human                          Shiki-Colors-Striped-Metacity  Xfce-stellar
Human-Clearlooks               Shiki-Dust                     Xfce-winter
HumanLogin                     Shiki-Human
belloa@belloa-laptop:~$

---

### Post by SpUpUz on 2009-11-03
> **alienclone said:**
> have you tried installing a theme manually? 
download a theme from gnome-look.org then drag the package into the box that you took the screenshot of.

can't drag into the box. i have been using linux ubuntu since version 5.10 and that's the first time i found a problem like this.

---

### Post by SpUpUz on 2009-11-03
any hint?

---

### Post by Anzan on 2009-11-03
gnome-appearance-properties daemon is screwy. Kill it, log out and back in. Try Failsafe GNOME or another WM and look around in themes then try GNOME again. Rebooting might work since GNOME's underthings tend to gt tangled.

---

### Post by SpUpUz on 2009-11-03
> **Anzan said:**
> gnome-appearance-properties daemon is screwy. Kill it, log out and back in. Try Failsafe GNOME or another WM and look around in themes then try GNOME again. Rebooting might work since GNOME's underthings tend to gt tangled.

it is the same since 2 or 3 weeks and logging out or restart does not produce any effects

---

### Post by SpUpUz on 2009-11-09
please someone help me!!

---

