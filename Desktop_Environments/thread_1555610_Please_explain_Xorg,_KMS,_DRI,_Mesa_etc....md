---
title: "Please explain Xorg, KMS, DRI, Mesa etc..."
date: 2010-08-18
forum: Desktop Environments
---

### Post by finite9 on 2010-08-18
Can someone please explain all the following terms for me as an overview with some practical details:

Im trying to get my head around the graphics stack and want to figure out how to tell if all the right stuff is loaded, and if im using the right drivers.  So I started Googling and came up with the following taking 10.10 as an example:

Intel GMA 4500MHD chipset
Kernel 2.6.35
Xorg 1.9
Mesa 7.8.2

For starters, are these the main packages/components that make up the graphics stack or are there more (i.e. is DRI a separate package or included in Mesa)?

1. KMS is in the kernel.  Is there a specific version needed for Xorg/Mesa etc to take advantage of KMS and if so, what versions are needed?
2. Do I need 2 drivers, one for 2d one for 3d?  is the 2d driver contained in the xorg package as xf86-video-intel, and the 3d driver contained in the Mesa package as xxx_dri.so?
3. How do I check that the 3d driver is installed and how to check if its loaded?
4. What functions do GLX and DRI/DRI2 provide and are they loaded by Xorg and how do you check if they are loaded? How do I check if im running DRI1 or DRI2?
5. Is Ubuntu 10.10 using the Mesa stack with DRI2 for 3D graphics?  Is there any Gallium3D driver for Intel GMA4500 and if so, how do I load that instead of the mesa driver?
6. are there any other programs apart from glxinfo that provide details about the whole graphics stack? Something that lists which components are running and which versions are installed?

Does Ubuntu 10.10 with the versions listed above provide hardware acceleration for H.264 via VA-API and if so, are there any media players that support acceleration for Intel chuipsets via VA-API?

Feels like you have to be a developer just to know what you need to have!!

---

### Post by clhsharky on 2010-08-18
finite9

> Can someone please explain all the following terms for me as an overview with some practical details:
I only know some maybe others will add more.
> For starters, are these the main packages/components that make up the graphics stack or are there more (i.e. is DRI a separate package or included in Mesa)?
DRI with UMS its in mesa, KMS in kernel.
> KMS is in the kernel. Is there a specific version needed for Xorg/Mesa etc to take advantage of KMS and if so, what versions are needed?
Switch - on KMS (kernel mode"module"space) off UMS(user mode space).
Lucid and Maverick use KMS my default, the installed packages works with KMS.
> 2. Do I need 2 drivers, one for 2d one for 3d? is the 2d driver contained in the xorg package as xf86-video-intel, and the 3d driver contained in the Mesa package as xxx_dri.so?
Correct.
> 4. What functions do GLX and DRI/DRI2 provide and are they loaded by Xorg and how do you check if they are loaded? How do I check if im running DRI1 or DRI2?
I don't know much on this. #dri in irc might be of some help, answering or directing you. In Log File Viewer look in Xorg.0.log for installed (driver, GLX and DRI/DRI2)and more.
> 5. Is Ubuntu 10.10 using the Mesa stack with DRI2 for 3D graphics?
Yes, so is Lucid.
> Is there any Gallium3D driver for Intel GMA4500 and if so, how do I load that instead of the mesa driver?
Not yet, but support is planned.
> 6. are there any other programs apart from glxinfo that provide details about the whole graphics stack? Something that lists which components are running and which versions are installed?
Not that i'm aware of, just glxinfo, Xorg.0.log & demsg log.
> Does Ubuntu 10.10 with the versions listed above provide hardware acceleration for H.264 via VA-API and if so, are there any media players that support acceleration for Intel chuipsets via VA-API?
For what I could find, No & No not on your chip.

Have you looked here
[http://www.phoronix.com/forums/forumdisplay.php?f=44](http://www.phoronix.com/forums/forumdisplay.php?f=44)

Hope this helps some

Sharky

---

### Post by finite9 on 2010-08-19
> **clhsharky said:**
> finite9

Yes, so is Lucid.

Not yet, but support is planned.
Sharky

Thanks for all the info.  I suppose I could have figured out that Mesa was being used even in Lucid, but I did not know that it was DRI2 in use.

Shame that there has not been fast progress for VA-API: it's the one area really let down by my TP Edge's CULV CPU: It really needs GFX hardware acceleration for 720p movies.

I am looking forward to the changes contained in Mesa 7.9, after having read a recent Phoronix article, but it does not look like it will make it into Maverick.

I don't know if the driver makes full use of the power of this chipset (GMA 4500MHD), and looking at radeon, there is a large performance gap between the free driver and the closed driver:

It really doesn't have good performance for playing games, but if the driver _isn't_ making full use of the chips performance (unlikely, as Intel is the manufacturer and author of the driver), then maybe a Gallium3D driver could increase this.  Although i'm very happy with this chip for power saving, 2D and basic 3D desktop effects.

---

