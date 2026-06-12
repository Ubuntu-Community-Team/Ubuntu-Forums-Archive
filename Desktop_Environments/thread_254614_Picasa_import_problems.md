---
title: "Picasa import problems"
date: 2006-09-10
forum: Desktop Environments
---

### Post by robin_reala on 2006-09-10
I'm sure this worked before, but it's not doing it now and I'm not sure what's changed. I'm trying to get Picasa to import the photos from a digicam. If I plug it in (via USB) and turn it on while Picasa's loaded then the following happens:

1) Gnome automounts it with the volume name 'usbdisk' and pops up a File Browser window with the contents
2) Picasa pops up a dialog that says "x pictures found on drive d: Would you like to copy these pictures to your computer and view them in Picasa?"

If I click on OK the Picasa import window opens, but it doesn't pick up any photos. The default device is set to 'Removable Drive(d:\)' which I assume is Wine's automount coming into play. I've also got the option of GPhoto2 Camera and the scanner that's attached to the system - setting it to the GPhoto2 camera doesn't make any difference.

Under System / Preferences / Removeable Drives and Media / Cameras I've got Digital Camera / Import digital photographs when connected unticked. This (if active) would be calling gthumb. Maybe this would be a better option than Picasa? I'd rather keep it in the one program if possible though.

Any help much appreciated, thanks!

---

### Post by mgmiller on 2006-09-10
I use gthumb with picassa.  I let gthumb handle the direct import of the pictures from my camera and save them to the Pictures directory that Picassa knows to look in.  Notice that by spelling the directory with a capital P as in Pictures instead of lower case p as in pictures, the gnome screen saver can use all your pics as screen savers.

---

### Post by robin_reala on 2006-09-11
OK, thanks. If I can't get the Picasa import working I'll go down that route - good to know it works fine for you.

Before I do that though, has anyone else got any ideas as to why Picasa might not be working?

---

### Post by sirmrmatt on 2006-11-13
There seems to be precious little info on the net about doing auto-importing in Ubuntu (I am using Edgy 6.10) into Picasa "direct." 

Usually the Removable Drives and Media preferences, under the "Cameras" tab, list the command

```
gnome-volume-manager-gthumb %h
```

as the default. I have seen that you can switch to f-spot-import if you want to use F-Spot, but what if you want to just use Picasa?

I like Picasa, I am comfortable with Picasa, it looks really nice, etc. It does cool stuff like collages, etc. 

Anyhow, does anyone know the command for this? I am using the gthumb import as we speak, however, it seems rather inelegant to use two programs to do this.

- Matt

---

