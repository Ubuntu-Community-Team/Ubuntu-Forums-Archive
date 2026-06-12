---
title: "Help with displaying icon in GNOME please??"
date: 2013-06-25
forum: Desktop Environments
---

### Post by rondamato on 2013-06-25
I am running a stock version of 12.04LTS using the stock WM--lightdm I believe?--which I ALSO believe is a Gnome variant.

This machine is a VDI, and it is connected to the company's AD using Likewise Open.

On the older 10.04 builds *libpam-mount* is installed--and the code to show the user's network drive is in the */etc/security/pam_mount.conf.xml*. It is written as such:

[FONT=arial]```
[/FONT][FONT=arial]<volume[/FONT]
[FONT=arial]user="*"[/FONT]
[FONT=arial]fstype="cifs"[/FONT]
[FONT=arial]server="ushofsvpnetapp1"[/FONT]
[FONT=arial]path="cifs.homedir"[/FONT]
[FONT=arial]mountpoint="~/%(USER)"[/FONT]
[FONT=arial]/>
[/FONT][FONT=arial]
```

However, I cannot get the icon to show up on the desktop--even though this works just fine under the 10.04 environment. I assume that this has something to do with a "*gsettings" *command but not sure of which one. If I turn on the desktop icons with

```
[/FONT][COLOR=#000000][FONT=Tahoma]gsettings set org.gnome.desktop.background show-desktop-icons true[/FONT][/COLOR][FONT=arial]
```

and then, say, turn on the networking icon with

```
[/FONT][COLOR=#000000][FONT=Tahoma]gsettings set org.gnome.nautilus.desktop network-icon-visible true[/FONT][/COLOR][FONT=arial]
```

the ENTIRE network folder shows up...NOT the user's homedir.

I'm pretty sure that this is simply an issue with *lightdm* and the *gsettings* command although I have no idea what the correct command might be. 

Can anybody help out with this issue or perhaps has run into it before?

Thanks so much for your help as always,

Ron[/FONT]

---

### Post by Frogs Hair on 2013-06-25
> [COLOR=#000000][FONT=arial]the ENTIRE network folder shows up...NOT the user's homedir.[/FONT][/COLOR]

I'm not positive I understand correctly , but if you want display the home folder install the Gnome Tweak Tool which  has options for desktop folders . Excuse me if I have misunderstood. 12.04 uses Gnome 3 and a different configuration editor  so the commands may no longer apply .

[https://apps.ubuntu.com/cat/applications/precise/dconf-tools/](https://apps.ubuntu.com/cat/applications/precise/dconf-tools/)

---

### Post by rondamato on 2013-06-26
Well, this is a large corporation. Every user has a "homedir" that is usually their first initial of their first name followed by their last name.

That bit of XML that I gave you, in 10.04 will show a "hard drive" icon on the desktop...along with the name of the person that logged in. So if I logged in the drive would show up on the desktop and would be named "RDamato."

When I open this drive, it is mapped to my "home drive" [H] in the Windows server. I am running Likewise to authenticate to AD.

This bit of XML worked perfectly fine on 10.04 which made me think that perhaps this was a Gnome setting. In 10.04, there are NO settings to be made--as long as this XML is there it works just fine and brings the drive up onto the desktop. Its only 12.04 that this issue arises in.

Thanks for your help and have a great day!

Ron

---

