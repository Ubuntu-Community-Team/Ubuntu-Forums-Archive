---
title: "Kubuntu takes over Ubuntu????"
date: 2006-06-29
forum: Desktop Environments
---

### Post by dtlinker on 2006-06-29
I have a new installation of Ubuntu 6.06, and wanted to try out Kubuntu desktop and XFCE, so I installed them both. I also tried switching to KDM. All was working as expected, except that I had Kubuntu as the header when booting, which I thought was because I had chosen KDM.

I then tried getting back to baseline, by restoring GDM, and Gnome as the default. Both of these were successful, but I still get Kubuntu as the heading of the startup. 

What does this mean? If I uninstalled Kubuntu would I be hosed? How can I get it to display Ubuntu at startup?

---

### Post by henriet on 2006-06-29
Hello,

try to uninstall kubuntu-artwork-usplash
```
sudo apt-get remove kubuntu-artwork-usplash
```

---

### Post by vayu on 2006-06-29
[QUOTE=henriet]Hello,

try to uninstall kubuntu-artwork-usplash
```
sudo apt-get remove kubuntu-artwork-usplash
```[/QUOTE]

You might need to reconfigure the kernel after that:
sudo dpkg-reconfigure linux-image-$(uname -r)

---

### Post by asimon on 2006-06-29
You don't need to uninstall kubuntu's artwork package. Just
```

$ sudo update-alternatives --config usplash-artwork.so
```
choose your favourite usplash variant and then reconfigure the kernel, as vayu wrote.

---

### Post by dtlinker on 2006-06-30
Thank you for the suggestions.

I tried the apt-get remove alternative, but didn't do it because it said that it was going to remove the kubuntu desktop as well.

I then tried the update-alternative option, and was able to change the * to ubuntu, but not the +. I get Ubuntu splash during shutdown and early startup, switching to Kubuntu later in startup!

I tried sudo dpkg-reconfigure linux-image-$(uname -r) and got:
Package `linux-images-2.6.15-25-386' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-images-2.6.15-25-386 is not installed

I would be willing to try other suggestions.

---

### Post by YourDoom123 on 2006-06-30
kubuntu-desktop is an unnneeded package. its just there to pull all the other kubuntu packages that need to be installed. u can safely uninstall it. as for the output, it doesn't make sense... why does it say linux-**images**-2.6.15-25-386? it should say image, which is the entire problem. check the line you entered to make sure you didn't accidently put an s in there...

---

### Post by asimon on 2006-06-30
[QUOTE=dtlinker]I then tried the update-alternative option, and was able to change the * to ubuntu, but not the +.[/quote]
This is okay, the * marks the current selection, the + shows the default value, which can not be changed.

---

### Post by dtlinker on 2006-07-01
I finally found a solution.

As posted above, the first command is:
sudo update-alternatives --config usplash-artwork.so

The second command that did the trick was:
sudo dpkg-reconfigure linux-image-`uname -r`

After a surprizingly long wait, there was some output, and when I rebooted, all was back to ubuntu, with the capabilityh to choose desktops preserved!

---

