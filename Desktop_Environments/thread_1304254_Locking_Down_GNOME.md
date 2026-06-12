---
title: "Locking Down GNOME"
date: 2009-10-29
forum: Desktop Environments
---

### Post by jonnytabpni on 2009-10-29
Hi Folks,

So I'm well under way to making a Linux desktop environment which is suitable for a workplace which requires strict lockdowns.

I've used a combination of:
Pessulus (I've locked down the Panel, removed the Ubuntu Menu)
GConf-Editor
PublicFox (For firefox)
And changing permission of certain gnome binaries

I have a few questions:

1) Is public fox good enough to lockdown firefox? The main thing I want out of it is to disable access to the options for home page and proxy

2) I followed a tutorial online which told me hold to edit a nautilus XML file to remove the option to change the desktop background. This setting never worked (Changing the respective menu item to hidden=true) so I was resorted to chmod the respect binary so only root could access it. Is this good enough?

3) Any ideas on how I could make the GNome "File/Open" dialog only give access to the user's home folder?

5) I have to give the user access to pessulus, as if I removed the button for this, then I coudn't change the profile anymore (Found that out the hard way!). So what I've done, is that using my admin account, created a symbolic link to pessulus. Then in the restricted account, created a keyboard shortcut to this symbolic link. Then before I hand out the computers, I just remove the symbolic link, so if the user were to press the keyboard shortcut, it just says File Not Found. What you think of this?

Cheers in advance

Jonny

---

