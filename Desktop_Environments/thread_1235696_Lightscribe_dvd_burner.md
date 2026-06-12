---
title: "Lightscribe dvd burner"
date: 2009-08-09
forum: Desktop Environments
---

### Post by Mia1990 on 2009-08-09
I was wondering if anyone could tell me how well lightscribe dvd burners work with ubuntu i am thinking about replacing my burner with one.

---

### Post by Richardarkless on 2009-08-09
you would need a piece of software to install the support and the create the covers

just done a quick search under google and this was the first one i seen

[http://ubuntuforums.org/showthread.php?t=289922](http://ubuntuforums.org/showthread.php?t=289922)

hope that helps, will continue looking if not

EDIT: found this pieces of software on their website for linux

[http://lightscribe.com/downloadSection/linux/](http://lightscribe.com/downloadSection/linux/)

---

### Post by fballem on 2009-08-09
> **Mia1990 said:**
> I was wondering if anyone could tell me how well lightscribe dvd burners work with ubuntu i am thinking about replacing my burner with one.

Lightscribe works well in Ubuntu. Depending on whether you are using 32-bit or 64-bit Ubuntu, the installation can be a bit complex.

These are my notes for installing Lightscribe sofware:

LightScribe is used to label LightScribe discs.

- obtain the software from: LightScribe website.

32-bit Linux
- install the software. There are two components. The core software must be installed first, then the Application.

64-bit Linux (This needs to be installed using the following commands in a Terminal). The version numbers will need to be changed to match the actual download files. The first two commands will install the LightScribe software. The remaining commands will resolve issues with referencing a required library.
```

sudo dpkg -i --force architecture lightscribe-1.18.6.1-linux-2.6-intel.deb
sudo dpkg -i --force architecture lightscribeApplications-1.18.6.1-linux-2.6-intel.deb
sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/
sudo ldconfig

```
Set the label so that it will print darker: 
```

sudo /usr/lib/lightscribe/elcu.sh

```

Once installed, then a menu option can be created to use the software.

[LIST=1]
[*]Right-click on Applications and select Edit Menu from the context menu.
[*]Click on Accessories, which is where the lightscribe menu item will be placed.
[*]Click the New Item button, and enter the following information into the fields:
[LIST=2]
[*]Ensure that Type is set to Application.
[*]Name may be anything. I use LightScribe Labeler.
[*]Command is: /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler (the browse button may be used to locate the application, which is in the /opt/lightscribeApplciations/SimpleLabeler folder.
[*]Comment may be anything. I use Writes a label on Lightscribe-enabled discs
[*]Click on the icon and browse to /opt/lightscribeApplications/SimpleLabeler/content/images folder. Once browsed, a list of suitable icons appears. Select one.
[*]Click on the Close button, which will complete the application.
[/LIST]
[/LIST]
To use, select the launcher from Applications > Accessories > LightScribe Labeler (or whatever was put in the Name field.

---

### Post by Mia1990 on 2009-08-23
Thank you i just installed my new lightscribe dvd burner today and it works great.

---

