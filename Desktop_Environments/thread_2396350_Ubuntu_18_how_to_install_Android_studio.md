---
title: "Ubuntu 18 how to install Android studio?"
date: 2018-07-14
forum: Desktop Environments
---

### Post by deepakdeshp on 2018-07-14
[COLOR=#242729][FONT=Arial]I Installed Android studio on Ubuntu 18. I unzipped the android-studio-ide file (around 850 MB) and ran the installer. Installer prompted that SDK files (around 1GB)need to be downloaded. Accordingly these were downloaded and installed.When I start the Android studio,I get the message that ,cannot locate SDK I am again prompted to download the 1gb SDK file. [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My query is how to relate the downloaded SDK to Android studio. And how to start Android after installation ? Is it by running studio.sh?
Thank you for any answers.[/FONT][/COLOR]

---

### Post by saderror256 on 2018-07-16
Well ill shorten up a guide i found

You will need java --> ```
sudo apt install openjdk-8-jre openjdk-8-jdk
```

Then simply install the snap package

```
sudo snap install android-studio
```

:KS that should do the trick

---

### Post by deepakdeshp on 2018-07-17
Thank you for your response.
I was able to install Android studio by redoing the step once more which prompted me to install 1.1 gb of packages.
After that I was stuck up at error message 'No virtual device' available. The solution was to go to VMD (virtual manager device) and crteate the virtual disk

---

### Post by kazakore on 2018-07-18
EDIT: I should learn to read fully. Problem solved above.

---

