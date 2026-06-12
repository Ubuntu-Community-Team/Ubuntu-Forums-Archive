---
title: "20070214 Hardware Information Icon Gone?"
date: 2007-02-14
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-02-14
Today's build changed Control Center with more categories and re-arranged things?

Anyway I fired up on another computer and went to send back the hardware info like the little tag in the corner asks for, so they could have a database of what Feisty Herd 3 is being run on.  Yesterday's build had 5 icons in Hardware, now there's only 4?

Lo and behold, I can't find the Hardware Information icon on the control center - can anyone tell me where it went?

Thanks, Jerry

---

### Post by spd106 on 2007-02-14
It's joined Synaptic in the Applications -> System Tools menu.

Incidentally, can you check the open office writer icon in the main menu, it looks wrong to me. It might just be my that install has gotten confused during updates recently. 

It appeared to have the /usr/share/icons/Human/scalable/apps/ooo-web.svg icon instead of the /usr/share/icons/Human/48x48/apps/ooo-writer.png icon. The strange part was that in Main Menu capplet it showed the right icon and path.

Unfortunately I accidentally deleted the link before I could be certain and take a screenie.

Thanks

---

### Post by jerrylamos on 2007-02-15
On 20070215 (herd 4?) I took a look at Applications, System Tools.  It's got:

Synaptic Package Manager
Ubuntu Device Database

The Ubuntu Device Database selection gathers some info for Ubuntu development and sends it off.  It doesn't display any hardware info, just records some stuff they wanted.

I don't see "Hardware Information" selection there or anywhere in the Control Center.  It used to be there, so I entered a bug in Launchpad.  

Cheers, Jerry

---

### Post by davmor2 on 2007-02-16
Jerry is correct there is no more hardware information.  This used to house the database but since the database and synaptic have lived life in app/system hardware info the app that tells you about your hardware there is nothing.:(

Personally though I would replace it with sysinfo :) nice package that wouldn't look a miss in any desktop.

---

### Post by spd106 on 2007-02-16
You are quite right about the device manager disappearing from the new menu, I posted too quickly without checking first. It's still accessible from a terminal (or Alt-F2) via 'hal-device-manager'.

As far as can tell device manager just scraped info from /sys and /proc just like lshw does from the terminal. I remember reading about a replacement that is in the works. Though it appears to have been deferred from Feisty. 

Here's the [link]("https://wiki.ubuntu.com/DeviceManagerSpec")

---

### Post by jerrylamos on 2007-02-20
Hardware information is back in Control center now.  It's still of use, however the hardinfo package is quite better.

Cheers, Jerry

---

