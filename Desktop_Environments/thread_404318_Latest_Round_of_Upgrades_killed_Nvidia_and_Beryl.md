---
title: "Latest Round of Upgrades killed Nvidia and Beryl"
date: 2007-04-08
forum: Desktop Environments
---

### Post by serialdae on 2007-04-08
Last week the update manager had a long list of patches. Most of them were for KDE components. I use gnome but figures they would be good for the system overall. After they installed every thing was fine but when I restarted gnome failed to load. KDE failed to load. They would just restart x.

I found I could log into gnome as root or a backup user I had created. However running Beryl caused a restart of X. I then found out the just running glxgears would restart X.

I downloaded and installed the latest drivers from NVidia. After a little work with the xconfig file I got glxgears and beryl running in the root and secondary profiles. Still could not boot into my profile. I also cannot get any Window decarator to load -ie emerald. bery complains that there is  "No GLXFBConfig for depth 32"

What do I need to delete from my user profile to remove all of Beryl's settings ot at least remove beryl from starting when the window manager loads?

Does anyone know what " No GLXFBConfig for depth 32" that may be refering to?

---

### Post by xopher on 2007-04-08
> What do I need to delete from my user profile to remove all of Beryl's settings ot at least remove beryl from starting when the window manager loads?

For Beryl: ```
rm -rf ~/.beryl
```

After that you can manually delete 'beryl-manager' from System -> Preferences -> Sessions. (If you want to remove beryl-manager from the session via terminal, cd to ~/.config/autostart and remove beryl-manager.desktop, this is at least how it's in Feisty.)

---

### Post by serialdae on 2007-04-08
Thanks I can log back in now. Beryl runs with no decorations. glxgears runs.

Now if I can get rid of the "No GLXFBConfig for depth 32" errors all will be well again.

I guess I need to pay more attention to what is getting updated. I run gnome so I didn't think the KDE upgrades would have done to much.

---

### Post by beerorkid on 2007-04-09
I had this problem over the weekend as well.  Tried all sorts of stuff then decided it might be my nvidia driver.  used envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) and all was good once again.

---

### Post by floke on 2007-04-09
Have you added 

Option "AddARGBGLXVisuals" "True" 

to the Device section of your xorg.conf file? This is a known cause of "no GLXFBConfig for depth 32" errors"....

---

### Post by serialdae on 2007-04-09
Does that go in the Device section or the Screen section?

---

### Post by floke on 2007-04-10
Device section

---

