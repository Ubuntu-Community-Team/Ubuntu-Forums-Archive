---
title: "Minecraft on Ubuntu 15.04 Problem"
date: 2015-07-05
forum: Gaming &amp; Leisure
---

### Post by rafael_vicuna on 2015-07-05
Hi all, I recently upgraded to ubuntu 15.04 from 14.10 and when I try to install minecraft for first time, I get this error!

```
Bootstrap (v5)
Current time is Jul 5, 2015 5:46:41 PM
System.getProperty('os.name') == 'Linux'
System.getProperty('os.version') == '3.19.0-21-generic'
System.getProperty('os.arch') == 'amd64'
System.getProperty('java.version') == '1.8.0_45-internal'
System.getProperty('java.vendor') == 'Oracle Corporation'
System.getProperty('sun.arch.data.model') == '64'

Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 2/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 3/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 4/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 5/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 6/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 7/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 8/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 9/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Downloading: [https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma](https://s3.amazonaws.com/Minecraft.Download/launcher/launcher.pack.lzma) (try 10/10)
Exception: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
Unable to download remote file. Check your internet connection/proxy settings.
FATAL ERROR: net.minecraft.bootstrap.FatalBootstrapError: Unable to download while being forced
    at net.minecraft.bootstrap.Bootstrap.execute(Bootstrap.java:95)
    at net.minecraft.bootstrap.Bootstrap.main(Bootstrap.java:381)


Please fix the error and restart.
```


This has happened since yesterday, I restarted my comp and reinstalled java, nothing worked. Someone help me!

---

### Post by Bucky Ball on 2015-07-05
*Thread moved to **Gaming & Leisure**.*

Welcome. Please use code tags for terminal output. See last link in my signature. Have added them to your last post. Good luck.

---

### Post by Toz on 2015-07-05
Does running:
```
sudo update-ca-certificates -f
```
...help?

[Source]("http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/2440292-minecraft-boot-trap-error")

---

### Post by rafael_vicuna on 2015-07-06
Omg yes thank you

---

### Post by Claudia_Ardison on 2015-10-19
> **Toz said:**
> Does running:
```
sudo update-ca-certificates -f
```
...help?

[Source]("http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/2440292-minecraft-boot-trap-error")

This worked flawlessly.
Thanks! ):P

---

### Post by michaelmcole on 2016-04-25
> **Toz said:**
> Does running:
```
sudo update-ca-certificates -f
```
...help?

[Source]("http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/2440292-minecraft-boot-trap-error")


Fixed it for me!  Thank you!

---

### Post by Javier_Macias-Guar on 2016-05-12
> **Toz said:**
> Does running:
```
sudo update-ca-certificates -f
```
...help?

[Source]("http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/2440292-minecraft-boot-trap-error")

Thank you very much. It also works in ubuntu 16.04

---

### Post by turbolego on 2017-02-15
> **Toz said:**
> Does running:
```
sudo update-ca-certificates -f
```
...help?

[Source]("http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/2440292-minecraft-boot-trap-error")

Thank you so much.

Worked for Lubuntu/Ubuntu 16.04.2 LTS and Minecraft 1.11

---

