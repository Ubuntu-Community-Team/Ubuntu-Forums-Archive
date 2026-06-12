---
title: "Minecraft Install"
date: 2018-07-29
forum: Gaming &amp; Leisure
---

### Post by Taylz on 2018-07-29
Hi all,

I have Minecraft on the Xbox (paid for) and noticed within the software center that it's available on here for free? When I installed and booted it up it asked for a login. I take it this isn't based nor saved on your actual HDD but possibly via a cloud via a login you have to create. Am I right?

Also, I take it you can't link these across platforms?

Anyone on here actually play Minecraft on their Ubuntu installs that's able to offer some advice and insight into how it works on Ubuntu? Any help would be greatly appreciated.

Regards,

Tayl.

---

### Post by #&amp;thj^% on 2018-07-29
Here is a couple of ways: [https://laptop.ninja/how-to-install-minecraft-on-ubuntu/](https://laptop.ninja/how-to-install-minecraft-on-ubuntu/)
I don't game but have installed it with out the PPA for some buddies of mine.
And the login screenshot.

---

### Post by Taylz on 2018-07-29
> **1fallen said:**
> Here is a couple of ways: [https://laptop.ninja/how-to-install-minecraft-on-ubuntu/](https://laptop.ninja/how-to-install-minecraft-on-ubuntu/)
I don't game but have installed it with out the PPA for some buddies of mine.

Hi 1fallen,

Thanks for that site. Followed the instructions for method 1 and upon completion of everything, when I go to load Minecraft, I get the following issue:
```

Bootstrap (v5)
Current time is Jul 29, 2018, 6:30:37 PM
System.getProperty('os.name') == 'Linux'
System.getProperty('os.version') == '4.15.0-29-generic'
System.getProperty('os.arch') == 'amd64'
System.getProperty('java.version') == '10.0.1'
System.getProperty('java.vendor') == 'Oracle Corporation'
System.getProperty('sun.arch.data.model') == '64'

Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 2/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 3/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 4/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 5/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 6/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 7/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 8/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 9/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma (try 10/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Unable to download remote file. Check your internet connection/proxy settings.
FATAL ERROR: net.minecraft.bootstrap.FatalBootstrapError: Unable to download while being forced
	at net.minecraft.bootstrap.Bootstrap.execute(Bootstrap.java:95)
	at net.minecraft.bootstrap.Bootstrap.main(Bootstrap.java:381)


Please fix the error and restart.

```

Any advice?

Regards,

Tayl.

---

### Post by #&amp;thj^% on 2018-07-29
> **Taylz said:**
> Hi 1fallen,

Any advice?

Regards,

Tayl.
As I mentioned I just installed from the Ubuntu repos  I did not add the PPA >>>Games and such should be installed form our sources. :) Just works better and less fussing about
**EDIT: I just read the errors now sorry>>>But see if this helps:**
```
sudo update-ca-certificates -f
```

---

### Post by #&amp;thj^% on 2018-07-29
Ok just tried method one with the edited solution I made in post #4 and it works.
```
sudo update-ca-certificates -f
```

Sorry I did not take the time to read your errors in the first place. :(

---

### Post by Taylz on 2018-07-30
Hi 1fallen,

All working now. The help is really appreciated, thanks!

Regards,

Tayl.

---

### Post by uncielser456 on 2018-08-11
Glad it was resolved bookmarking this coz I often encounter errors in mine too.

---

### Post by shv00 on 2019-03-10
This [instruction]("https://shv.red/3-how-to-install-minecraft-on-linux-ubuntu-manjaro.html") helped me to install Minecraft.
But sometimes the game slows down a bit.
[COLOR=#000000][FONT=Tahoma]Intel Celeron N3350
4GB RAM
HDD
But I think my PC have to work well with this game[/FONT][/COLOR]

---

