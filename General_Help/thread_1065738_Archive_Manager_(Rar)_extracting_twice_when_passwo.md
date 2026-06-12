---
title: "Archive Manager (Rar) extracting twice when password protected"
date: 2009-02-10
forum: General Help
---

### Post by scrapee on 2009-02-10
Hi

I hope this isn't a double post or a already known issue, but I didn't find it via the search.

When i unpack a .rar file which is password protected the Archive Manager unrar's the file completely. Then it asks me for the password and starts again from the beginning. So it takes double the time to unpack big password protected .rar files.

Is there anything that can be done, because this is really annoying.

thanks

---

### Post by binbash on 2009-02-10
you can fill a bug report for this (yes i had same issue).I always unrar them at terminal via unrar e filename.rar command.If you don't like CLI you can use [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)  ;)

---

### Post by mb_webguy on 2009-02-10
Which rar module are you using in Archive Manager?  It can use either the unrar package or the 7zip-rar package.  You might try switching to the other to see if there's any difference.

---

### Post by scrapee on 2009-02-10
Thank you for your replies. 

I installed the unrar package. How do I switch the used package?

If that does not change anything I will just use the terminal in the future.

---

### Post by mb_webguy on 2009-02-10
I would install one and uninstall the other.  I prefer to use 7zip-rar (if only so that if I want to extract an archive from the terminal I only have to remember one command) and I haven't had any problem with it.  On the other hand, I don't think I've tried extracting any password-protected rar archives.

---

