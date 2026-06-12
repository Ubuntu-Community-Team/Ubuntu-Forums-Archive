---
title: "Folder for &quot;Desktop&quot;..."
date: 2009-11-05
forum: Desktop Environments
---

### Post by wayneox on 2009-11-05
ok i have a little problem..
was playing with kubuntu-desktop and xubuntu-desktop today  - i messed up ubuntu-desktop....

Changed the paths in kubuntu... etc. played for a bit, desided i prefer gnome, so removed all xubuntu and kubuntu... now my ubuntu is working, only the desktop using /home/wayne (my home flder) as the desktop point....

(so documents etc are always shown on desktp) - how do i switch it back to ~/Desktop  - not annoying too much, except it keeps creating the folders "Desktop" and "Documents" wen i log in - i mapped music / etc to various other folders on my windows disk... so i guess thats why they arent loaded... but Documents was remapped to My Documents in windows also, but auto- mk.dir  ....

no rush, just one of those annoyances... - im pretty sure its something i changed in kde just not sure how to change it back since i uninstalled kde etc...

thanks!

---

### Post by wojox on 2009-11-05
Try Alt+F2

Type in:

gconf-editor

Go to apps > nautilus > preferences 

Make sure desktop_is_home_dir is unchecked. Log out and back in.

This is for Karmic right?

---

### Post by wayneox on 2009-11-06
> **wojox said:**
> 
This is for Karmic right?
oh yeah sorry, 9.10.

already checked that too - found it on google somewhere... and it IS **un**checked...

logged out etc a cpl but still the same, i don't all that much... BUT the fact it keeps recreating the desktop / documents folder makes it annoying. :S [i like what im used to in general - when i switched to linux before (onto Debian originally with the KDE desktop) i didn't like it. but it grew on me... when i installed Ubuntu it was nice cause i found gnome easy to make "look like windows"

on an additional note i appear to have two volume controls on the notification area also, even though only one appears to work... if i remove the panel on the panel and re add it, it becomes my network and volume, then both work as supposed to. [networking and sound works correctly, just not the notification area]

oh additional: since i reinstalled the desktop my graphics HAVE been BRILLIANT [even shows the nVidia logo now, never used to... - not that i like this, but it means it is using the driver correctly, yes? and i can even view the login screen. (i used a TV/monitor hook up - which only supports 60hz refresh, so it doesnt show anything else - except my initial post) - so for these two annoyances i don't fancy reinstalling, since there must be a good way to fix this - correct?...]

- oh also for info: when i removed Kubuntu / xubuntu / Ubuntu desktops  i was left with just BARE SHELL... and no desktop AT ALL... then used the "apt-get install ubuntu-desktop" (removed the others with debfoster)

- when i logged back in after install ubuntu-desktop all of my /home/*user* directory was empty - i didn't keep anything in there important, just a few d/l of deb files... and symlinks on desktop to my windows drives.

cheers for help so far :)

---

