---
title: "How to install dotnetfx in Wine"
date: 2009-02-10
forum: Desktop Environments
---

### Post by minhnt on 2009-02-10
I've tried to many time to install dotnetfx in Wine but cannot. Have you happend like that???

---

### Post by Ng Oon-Ee on 2009-02-10
Why would you want .Net? What exactly are you trying to do?

Wine is primarily for applications, not for libraries such as the .Net libraries.

---

### Post by overlord.gaurav on 2009-02-10
You can install .Net using Winetricks. Though, some of the features will still not be available. But some of your apps will start working.
To install .NET Framework 2.0, do the following:

```
wget http://kegel.com/wine/winetricks
```
```
 sh winetricks corefonts dotnet20
```

You need cabextract utility (project website [here]("http://www.cabextract.org.uk/")) for winetricks corefonts step.
Make sure it's installed locally.

```
sudo apt-get install cabextract
```

Now, try to start your app. If you're lucky, you'll get it to work!

---

