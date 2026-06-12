---
title: "How do you download your site with Nvu?"
date: 2005-12-18
forum: General Help
---

### Post by equal on 2005-12-18
I've installed Nvu, and I'd like to start using it. I've set up the ftp server, I can see all the files on our host server, but I can't download them onto my machine to edit them, or even open them through Nvu to edit the pages. Help?

---

### Post by equal on 2005-12-18
Hmmm I found a work around method. I can open the site pages individually and then save them to my computer one by one, but this seems like the long way around. Any other ideas?

---

### Post by aysiu on 2005-12-18
How about using an FTP client?
gFTP
KBear
Kasablanca
...
or even Nautilus or Konqueror...

---

### Post by stuporglue on 2005-12-18
Did you set up your site in NVU's site manager, and is the site manager visible when you have NVU open? 

Like this: [http://stuporglue.org/img/nvu.png](http://stuporglue.org/img/nvu.png)

To show the site manager: view menu-> Show/Hide ->Site manager

If your site isn't set up in site manager, hit "Edit Sites" then fill in the applicable values in the window that pops up. With the values filled in, press the "New Site" button which will save your site. 

Once that's done, you should be able to just click your site in the list of sites in the site manager, and view a listing of all the files and folders visible to the ftp login you supplied. Double click a file to edit it, and hit publish to push it back up to the web. 

Site note: NVU is very nice. I do all of stuporglue.org with it, except the menu on the left which is just a chunk of HTML I manually put on every page with a php include statement.

---

