---
title: "Installing wine"
date: 2009-04-02
forum: General Help
---

### Post by spectrumvoid on 2009-04-02
Hi all.

I'm running Ubuntu 8.04 LTS. I'm trying to Install WINE via the add/remove applications...

This error message pops up after I've selected to install WINE: W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb](http://sg.archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb)
  Could not connect to sg.archive.ubuntu.com:80 (202.79.181.124), connection timed out


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.0.28a-1ubuntu4.7_i386.deb](http://sg.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.0.28a-1ubuntu4.7_i386.deb)
  Unable to connect to sg.archive.ubuntu.com http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_1.0.0-1ubuntu4~hardy1_i386.deb](http://sg.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_1.0.0-1ubuntu4~hardy1_i386.deb)
  Unable to connect to sg.archive.ubuntu.com http:

I have no problems with my internet connection. Please help.

Thanks.

---

### Post by Dark_Stang on 2009-04-02
Try connecting to a different server. Go System > Administration > Software Sources. In the drop down list select "Other". Then hit the "Select Best Server" button. After that hit "close" and let it reload. Then try to download wine again.

---

### Post by ambdeep on 2009-04-02
try applications->add/remove then on the "show" drop-down menu select all avalable applications.....then search for wine and then install it........the above rccomendation seems good to me......a stupid question....but is your internet connected? if not go to help and check on the appropriate method of connecting to the internet.

---

### Post by tanusgreystar on 2009-04-02
I have wine installed and was able to install Quicktime, but when I run Quicktime it pops up but then disappears. Would that be a problem with Quicktime or wine itself??

---

### Post by Dark_Stang on 2009-04-04
Wine isn't going to allow you to install just any windows application. It will only work for ones that it supports at this point. Why would you need quick time anyway? I've never seen any point to it.

Here is the info for quicktime on wine.
[http://appdb.winehq.org/appview.php?appId=1029](http://appdb.winehq.org/appview.php?appId=1029)

---

