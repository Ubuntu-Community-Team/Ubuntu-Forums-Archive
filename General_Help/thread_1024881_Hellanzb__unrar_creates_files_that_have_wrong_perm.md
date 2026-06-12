---
title: "Hellanzb / unrar creates files that have wrong permissions...  possible umask problem"
date: 2008-12-29
forum: General Help
---

### Post by Elchbulle on 2008-12-29
I need some help here, in a little over my head.

I am running hellanzb (a usenet binary downloader) and all works well, until it actually unrars the file to the specified directory.

What happens is when the folders / files are created they have permissions of 700 .  I want them to have at least 770, preferably 777.  I have checked the umask on the directory where they are being stored and it is 0000.  If I create a file / folder in there it has the correct 777 permissions.  However when hellanzb (and I suppose technically unrar, since it unrars the files and places them in there) puts them in there it has 700.  This is very annoying since I share most of the items on my network and every time something is downloaded I have to manually change it to 777....

Any ideas on what I can check?  unrar and hellanzb are running as root...  

Thanks in advance for any and all help!

Tim

---

