---
title: "No linux installer in UT2004 DVD"
date: 2011-06-26
forum: Gaming &amp; Leisure
---

### Post by MichaelMale on 2011-06-26
Hello all,

I have the Sold Out Software UK version of Unreal Tournament 2004. I've tried running it under WINE but that didn't work that well. I then found out that they made it for Linux but there was no linux installer in the DVD.

Any ideas, or should I get another retail version?

Thanks

Michael

---

### Post by Perfect Storm on 2011-06-26
Not all UT2004 comes with a Linux installer, if you're one of the unlucky:

[http://ubuntuforums.org/showpost.php?p=10981407&postcount=80](http://ubuntuforums.org/showpost.php?p=10981407&postcount=80)

---

### Post by MichaelMale on 2011-06-27
> **Artificial Intelligence said:**
> Not all UT2004 comes with a Linux installer, if you're one of the unlucky:

[http://ubuntuforums.org/showpost.php?p=10981407&postcount=80](http://ubuntuforums.org/showpost.php?p=10981407&postcount=80)

Thanks for that link, I'll try it out later. I guess that's what you get when you buy a £3 discount version!

---

### Post by MichaelMale on 2011-06-27
I got it working! After numerous goes I installed it through WINE and found that I did some silly mistakes. For anyone viewing this for future reference, I used this off the WineHQ game list. One thing, though, is that for me the settings only gave me up to 1024x768, so I had to set the resolution on winecfg to 1024x768. With the updates it worked perfectly!

> I found that I had to make these changes to get the game to work in full-screen mode. Once these changes were made it worked perfectly all the time.

In the registry set the following key: 
  HKEY_CURRENT_USER/Software/Wine/DirectInput/MouseWarpOverride = force

In winecfg add checkmarks to the following checkboxes: 
  Allow DirectX apps to stop the mouse leaving their window 
  Emulate a virtual desktop (enter your screens native resolution)

In UT2004/System/UT2004.ini in the [Engine.Engine] section: 
  Uncomment RenderDevice=OpenGLDrv.OpenGLRenderDevice 
  Comment out your old RenderDevice

In UT2004/System/UT2004.ini in the [WinDrv.WindowsClient] section: 
  Set your WindowedViewport to your native resolution 
  Set your FullscreenViewport to your native resolution 
  Set your MenuViewport to your native resolution

Thanks Artificial Intelligence for the help.

---

### Post by Virus666 on 2011-06-28
> **MichaelMale said:**
> I got it working! After numerous goes I installed it through WINE and found that I did some silly mistakes. For anyone viewing this for future reference, I used this off the WineHQ game list. One thing, though, is that for me the settings only gave me up to 1024x768, so I had to set the resolution on winecfg to 1024x768. With the updates it worked perfectly!


Well, you really do not need to run the game via Wine. UT2004 has already been a "native" Linux game. If you follow my instructions which was refered before, you may run the game natively without trouble...

[http://ubuntuforums.org/showpost.php?p=10981407&postcount=80](http://ubuntuforums.org/showpost.php?p=10981407&postcount=80)

---

### Post by holastickboy on 2011-06-28
The original versions of the game come with a Linux installer too if you find that too difficult.  They are pretty cheap on eBay!

---

