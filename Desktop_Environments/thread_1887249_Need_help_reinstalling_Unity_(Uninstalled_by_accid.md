---
title: "Need help reinstalling Unity (Uninstalled by accident)"
date: 2011-11-26
forum: Desktop Environments
---

### Post by asad.bukhari on 2011-11-26
I was learning Terminal codes and to practice wanted to uninstall compiz (CCSM). I was stupid and put 'compiz' as the program into the terminal. I hadnt realized what I had done until I restarted.

I have no UI when logging into my Ubuntu 11.10. There is a terminal box. I tried installing unity again using the code but it is unable to fetch the archives, or something along that line.

Can anyone help me get Unity back?

---

### Post by JRV on 2011-11-26
try:```
sudo apt-get install ubuntu-desktop
```

---

### Post by asad.bukhari on 2011-11-26
I used ```
dpkg -l | grep compiz
``` to confirm that I do not have compiz.

I tried ```
unity --replace
``` as well as ```
unity --reset
```
Both informed me that unity is not installed.

When I try ```
sudo apt-get install compiz
``` or ```
sudo apt-get install unity
``` or ```
sudo apt-get install ubuntu-desktop
``` I get the same error ```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

The core of my problem is the error. What is it and how do I get around it?

---

### Post by LinuxFan999 on 2011-11-26
The error message suggests to run apt-get update. Try running that command, then try installing Compiz and Unity again.

---

### Post by asad.bukhari on 2011-11-26
I entered ```
sudo apt-get update
``` 
but only receive further errors 
```
W: Failed to fetch http://[Several different websites] Could not resolve the archive

W: Some index files failed to download. They have been ignored, or old ones used instead.
```
The several different websites were:
[List]archives.canonical.com
security.ubuntu.com
extras.ubuntu.com
us.archive.ubuntu.com
deb.opera.com[/list]

I cannot post the actual code b/c I have no means to do so. I return to my windows partition to post here.

Is this a major issue?
Is there a way to resolve it?

---

### Post by bluexrider on 2011-11-26
sudo apt-get autoremove
sudo apt-get upgrade--fix-broken

---

### Post by asad.bukhari on 2011-11-26
```
sudo apt-get autoremove
```

Did a lot.

However, 
```
sudo apt-get upgrade--fix-broken
```
Resulted in:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove & 0 not upgraded
```

I tried to install unity, compiz, etc but still had the same error.
Now what?

---

### Post by asad.bukhari on 2011-11-27
Does anyone else know a solution to this?

---

