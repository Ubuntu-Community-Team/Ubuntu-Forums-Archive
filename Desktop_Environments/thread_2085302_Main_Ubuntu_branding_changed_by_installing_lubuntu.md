---
title: "Main Ubuntu branding changed by installing lubuntu-desktop packages"
date: 2012-11-17
forum: Desktop Environments
---

### Post by MHazell on 2012-11-17
Yesterday I installed the lubuntu-desktop package on my main Ubuntu 12.04 LTS install. I installed it because my PC is old and LXDE runs really well. I like LXDE, and enjoy using it, but now I have a problem with it.

When I rebooted my PC after installing updates the other day, the Ubuntu boot screen with the dots changed completely. It now has the Lubuntu logo, the Lubuntu blue-ish background and the blue loading dots. I do not want this change as I prefer to have the original Lubuntu branding.

If someone can aid me this, please let me know. This always makes me feel bad about installing other DEs because it can change stuff that wasn't expected, like this.

---

### Post by Mr_JMM on 2012-11-17
Sorry, can you explain a couple of things:
You say
> **MHazell said:**
> I prefer to have the original Lubuntu branding
But that is what you have:
> **MHazell said:**
> It now has the Lubuntu logo, the Lubuntu blue-ish background and the blue loading dots.

You then say:
> **MHazell said:**
> This always makes me feel bad about installing other DEs because it can change stuff that wasn't expected, like this.
You installed the Lubuntu desktop and it changed things to show the Lubuntu desktop. How is this a surprise ("Wasn't expected")?

Did you mean you wanted to keep the original Ubuntu theme when loading? Or are you referring to pure LXDE compared to Lubuntu?

---

### Post by zombifier25 on 2012-11-18
To change the Plymouth theme (the boot screen, that is) back to the Ubuntu theme, run this command:
```
sudo update-alternatives --config default.plymouth
```
Then choose the ubuntu-logo one.

---

### Post by whatthefunk on 2012-11-18
You installed Lubuntu and now you feel bad because its Lubuntu?  Im confused....

---

### Post by zombifier25 on 2012-11-18
> **whatthefunk said:**
> You installed Lubuntu and now you feel bad because its Lubuntu?  Im confused....

I think what he meant was that he wanted to install other DEs, but he did not want them to tamper with certain parts of the system (such as the boot screen)

---

### Post by Yellow Pasque on 2012-11-19
> **MHazell said:**
> This always makes me feel bad about installing other DEs because it can change stuff that wasn't expected, like this.

Just be more careful when installing -desktop metapackages..

---

### Post by Peripheral Visionary on 2012-11-19
> **Temüjin said:**
> Just be more careful when installing -desktop metapackages..

How much more careful can you be about selecting a metapackage and installing it via Synaptic, Software Manager, or Terminal?  

Maybe a better way to put it is, "know what you're installing before you install it."  The Lubuntu-desktop metapackage does much more than just install the LXDE desktop environment. It installs Lubuntu's default settings, menus, and applications as well!  The same goes for all the 'buntu-desktop metapackages.

To install just the desktop environment without all the 'buntu defaults and applications, choose *only* the DE, *not* the metapackage.

---

### Post by mcduck on 2012-11-19
..on the other hand it also makes perfect sense to get the themes, default desktop configurations, applications and all the other parts that come with the *-desktop metapackages. In which case simply using *update-alternatives* to switch between themes and configurations is the right way to go, as suggested by zombifier25. That's what the command *is* for. :)

---

### Post by critin on 2012-11-19
> **MHazell said:**
> Yesterday I installed the lubuntu-desktop package on my main Ubuntu 12.04 LTS install. I installed it because my PC is old and LXDE runs really well. I like LXDE, and enjoy using it, but now I have a problem with it.

When I rebooted my PC after installing updates the other day, the Ubuntu boot screen with the dots changed completely. It now has the Lubuntu logo, the Lubuntu blue-ish background and the blue loading dots. I do not want this change as I prefer to have the original Lubuntu branding.

If someone can aid me this, please let me know. This always makes me feel bad about installing other DEs because it can change stuff that wasn't expected, like this.

It's booting into the lubuntu session because that was what you were using last, before shutting down.  If you use lubuntu,  login to ubuntu before shutting down,  the next login should be on ubuntu's login.   Then choose lubuntu session at login.  

At least give it a try.

edited to add:  Post # 7  says: >  [by Peripheral Visionary]("http://ubuntuforums.org/member.php?u=1570698")  To install just the desktop environment without all the 'buntu defaults and applications, choose *only* the DE, *not* the metapackage.

I thought you'd added only the DE since you  didn't expect the login screen to change.   So my suggestion isn't going to change anything.  Sorry.

---

