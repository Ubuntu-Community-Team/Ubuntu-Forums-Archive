---
title: "How To: Install OpenOffice 3.0.1"
date: 2009-01-29
forum: General Help
---

### Post by scouser73 on 2009-01-29
Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html#en-US]("http://download.openoffice.org/other.html#en-US") and download the Linux **.deb** file.

Once you have done that, extract the .deb file, **OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO300_m15_native_packed-1_en-US.9379**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO300_m15_native_packed-1_en-US.9379** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9376_all.deb**

Once you've done that you'll find OpenOffice 3.0.1 in Office

---

