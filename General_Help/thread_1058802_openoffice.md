---
title: "openoffice"
date: 2009-02-03
forum: General Help
---

### Post by gotenks123 on 2009-02-03
how to upgrade to the latest version of openoffice?

---

### Post by howefield on 2009-02-03
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Follow the instructions there and that will get you to version 3.0.1.

---

### Post by Neural oD on 2009-02-03
it's highly recomended that u use the repositories, that is unless you know what you are doing. Another way is to google to see if someone has made a .deb for ubuntu. And lastly you can compile it from source.

---

### Post by scouser73 on 2009-02-03
These instructions are for OpenOffice 3.0.1, which is a newest version.

Download the .deb file from [http://download.openoffice.org/other.html#en-US]("http://download.openoffice.org/other.html#en-US")

Then extract the file, place the extracted folder onto the desktop, open terminal and paste this command: > **sudo apt-get remove openoffice*.*** *_Which removes OpenOffice_*

Then again using terminal paste this command: > **sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb**

And finally this command in terminal: > **sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9376_all.deb**

---

### Post by visctrix on 2009-02-03
The tutorial at [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml) seems to be the best solution I can find.

Edit your sources list and let Ubuntu update itself automatically. Less scary for me than removing OpenOffice completely and reinstalling.

---

### Post by pvonbert on 2009-02-03
I've just installed OOo 3.0.1 using Ubuntu Tweak (found at this Forum).
You have to unlock the Third-Party Sources on the Applications Tab.
You might get a GPG error, but it installs anyway.

---

### Post by mb_webguy on 2009-02-03
Adding the [openoffice-pkgs PPA]("https://launchpad.net/~openoffice-pkgs/+archive") (which is what the Softpedia tutorial is about) is the best way.  Just make sure you add the GPG key.

---

### Post by forger on 2009-02-07
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

