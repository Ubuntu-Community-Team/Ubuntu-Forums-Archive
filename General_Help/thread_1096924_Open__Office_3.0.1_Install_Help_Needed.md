---
title: "Open  Office 3.0.1 Install Help Needed"
date: 2009-03-15
forum: General Help
---

### Post by wheelerrver on 2009-03-15
I have been trying to upgrade to Open Office 3.0.1 on my 8.10 Ubuntu

Still new, so, may be missing something.

I started following instructions in [http://ubuntuforums.org/showthread.php?p=6639054#post6639054](http://ubuntuforums.org/showthread.php?p=6639054#post6639054)

However, when I unpack the gz file I do not find a file with the name I need for the next step.  Lots of files, but not that one.  Any advice?

---

### Post by wheelerrver on 2009-03-15
A reply to myself.  I had done some archive thing, not an extract.  When I did extract I got the file I was expecting.

---

### Post by cbtengr on 2009-03-15
> **wheelerrver said:**
> A reply to myself.  I had done some archive thing, not an extract.  When I did extract I got the file I was expecting.
 Try this instead.  It will add a repository so you can install from Synaptic package Manager:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

gh

---

### Post by Nano_ext3 on 2009-03-15
You do NOT have to add a repository.  All you need is the DEB package from the Open Office official site.  See this website:

[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

Find your language and download the "deb" package.  From the GUI you can double click this to install it.  Or run "sudo dpkg -i PACKAGE_NAME" from the terminal

Cheers!

-Nano

---

### Post by vanadium on 2009-03-15
You *better* use the repository approach. Easiest, standard and makes sure you are getting the updates.

---

### Post by neon100 on 2009-03-17
I am also stuck with the same problem. But i am using 8.04. how do i use the repository method?

---

### Post by neon100 on 2009-03-17
sorry to jump in...

I got much farther using the 8.10 method. But there are two problems. When i click the IMPORT KEY button, and browse to desktop, it does,'t show that file. So i cannot click on that file to add that key. Alternately. i double clicked on that file... a notification appeared on the bottom right corner of screen saying that the key had been added but still it doesn;t appear under the authentication tab.

Also . there is the base core update listed in my update window but when i start the update manager, i says that following packages cannot be authenticated. That list also includes all the open office packages.

any solution?

---

### Post by neon100 on 2009-03-17
I've added the key somehow. but still the Open office update is not enabled in the Update Manager window.

---

### Post by abn91c on 2009-03-17
> **cbtengr said:**
> Try this instead.  It will add a repository so you can install from Synaptic package Manager:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

gh
[COLOR="Red"]wheelerever[/COLOR],  you better off using the step by step guide in the above link

---

### Post by ktmom on 2009-03-17
> **cbtengr said:**
> Try this instead.  It will add a repository so you can install from Synaptic package Manager:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

gh

Thank you for the pointer.  That was easy.

---

