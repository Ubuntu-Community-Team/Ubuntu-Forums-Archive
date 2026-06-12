---
title: "Nautilus: folder-specific preview/thumbnails?"
date: 2009-04-26
forum: General Help
---

### Post by nortexoid on 2009-04-26
In windows it's possible to set folder-specific view settings, so that e.g. the folder "My Pictures" previews photos in thumbnails while another folder "Pictures of Fat Women" does not. Can Nautilus do this? I notice that previewing via thumbnails is a "global" setting.

I ask because I want to preview only my photo folders, and not e.g. my 1000+ pdf folder.

---

### Post by ibuclaw on 2009-04-26
Yes, Press **Ctrl+1**, **Ctrl+2** and **Ctrl+3** to switch between the different view modes.

They should stick...

Regards
Iain

---

### Post by nortexoid on 2009-04-26
I can change views alright, and they stick, but I want the preview function (Edit -> Preferences -> Preview) to be folder-specific rather than applying to all folders in the same way.

I just want preview thumbnails for some, not all, folders!

---

### Post by lovinglinux on 2009-04-26
> **nortexoid said:**
> I can change views alright, and they stick, but I want the preview function (Edit -> Preferences -> Preview) to be folder-specific rather than applying to all folders in the same way.

I just want preview thumbnails for some, not all, folders!

It would also nice if we could set only pictures to have thumbnails, but the only option available is media in general. I don't want video thumbs, because they put an extra load in the CPU while I'm doing other stuff, but I need pictures thumbs. 

I guess Nautilus can't do what we want, because the preview settings are global.

---

### Post by Bystroi on 2009-08-19
> **lovinglinux said:**
> It would also nice if we could set only pictures to have thumbnails, but the only option available is media in general. I don't want video thumbs, because they put an extra load in the CPU while I'm doing other stuff, but I need pictures thumbs. 

I guess Nautilus can't do what we want, because the preview settings are global.

Too bad.. I've also been looking for this feature in Ubuntu as it makes finding certain folder from huge pile of other similar folders so much faster in XP.
Representative image for folder contents is my preferred way of finding the folder I'm looking for, rather than long descriptive names or dates.

At least until some image content analysis capable search agent comes around. :)

I wonder if there is a way to make a plugin or script or something for Nautilus that would do the trick?

---

### Post by scebert on 2010-02-20
In gconf-editor /apps/desktop/gnome/thumbnailers you can activate or deactivate thumbnailing for individual filetypes.

---

### Post by Cresho on 2010-10-19
program is called cover-thumbnailer

[http://gnome-look.org/content/show.php/Cover-thumbnailer?content=120258](http://gnome-look.org/content/show.php/Cover-thumbnailer?content=120258)

better than xp.  Im using it in 10.04.  install deb and reboot.  configuration is in preferences.

---

### Post by Sysyphus Jones on 2011-01-14
> **Cresho said:**
> program is called cover-thumbnailer

[http://gnome-look.org/content/show.php/Cover-thumbnailer?content=120258](http://gnome-look.org/content/show.php/Cover-thumbnailer?content=120258)

better than xp.  Im using it in 10.04.  install deb and reboot.  configuration is in preferences.
Suddenly this is broken for me as of the last software update. (I'm also using 10.04.)

Basically just shows the default folder view in nautilus, regardless, including old folders that were showing cover art before. 

My usual setup is to name some file .cover.jpg in the folder but never seems to set the folder view now.

File thumbnails still show previews so I don't think it's a  global setting that's busted

I have the FLOZz's PPA in software  Centre.

Anyone else have the problem/and or suggestions?

---

