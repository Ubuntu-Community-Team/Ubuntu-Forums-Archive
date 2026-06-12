---
title: "Trying to run minecraft"
date: 2015-11-20
forum: Gaming &amp; Leisure
---

### Post by Sean_Schilling on 2015-11-20
Hello, Recently I just switched to the latest version of ubuntu 15 and I'm having some trouble running Minecraft. This system had no trouble with it on other OS, so I don't know why its not working now. I'm using intel graphics and I made sure all drivers are up to date. I also have openjdk java 8 installed and confirmed working with other programs. Here is what the launcher displays.

```

Bootstrap (v5)
Current time is Nov 20, 2015 1:28:20 AM
System.getProperty('os.name') == 'Linux'
System.getProperty('os.version') == '4.2.0-18-generic'
System.getProperty('os.arch') == 'amd64'
System.getProperty('java.version') == '1.8.0_66-internal'
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

If anyone can help me figure this out it would be appreciated. 
thanks

---

### Post by rocco6 on 2015-11-21
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo update-ca-certificates -f
```

Use this in terminal.[/FONT][/COLOR]

Java 8 works bad on Linux, try OpenJDK 7

---

### Post by Sean_Schilling on 2015-11-21
Thanks, that worked great.

---

