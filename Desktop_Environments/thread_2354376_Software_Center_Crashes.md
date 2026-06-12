---
title: "Software Center Crashes"
date: 2017-03-02
forum: Desktop Environments
---

### Post by vdub20002 on 2017-03-02
Xubuntu 16.04 LTS crashes whenever I attempt to install software downloaded from the Internet. For example, I downloaded Google Chrome from Google's website and when I opened the .deb file, the software opens for a couple of seconds before closing without displaying any sort of errors. When I attempt to open the software center itself, it's the same thing.

I'm running the 32-bit version of the software on a Panasonic Toughbook laptop. Is there anyone out there that could try to help me resolve the issue?

---

### Post by RobGoss on 2017-03-02
The 32 bit version of Chome is no longer supported Google dropped it sometime ago

If you have a 32 bit machine  you might want to try installing Chromium

---

### Post by howefield on 2017-03-02
First thing is that 16.04 saw quite a few issues with the Ubuntu Software package when 16.04 was initially released, eg an inability to install third party deb packages. There have been updates since last April to make it perform considerably better so the first thing to check is that your system is properly updated ?

I'd suggest using the Software Updater application or from a terminal..

```
sudo apt update
```
```
sudo apt upgrade
```

What other third party packages are you having a problem with apart from Chrome, which although 32 bit is now unsupported I'd think if you had managed to get an old deb package it should still install.

---

### Post by speartip on 2017-03-02
If you need to install 3rd party .debs from the internet, it should only be done as a last resort, and gdebi  is a far more reliable tool to install .debs than the software centre.

---

