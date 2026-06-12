---
title: "Rename Download Folder"
date: 2011-11-09
forum: Desktop Environments
---

### Post by ornages on 2011-11-09
I'm using Ubuntu 11.10 with Nautilus Filebrowser.
I renamed my 'Downloads' folder to 'downloads' because it's faster to write without capitals. However, the old 'Downloads' folder keeps coming back everytime I log back in. How can I delete it permanently?
Also I can't figure out how to remove the bookmark in the left panel of Nautilus (Computer->Downloads).

Thank you!

---

### Post by gamblor01 on 2011-11-09
I have never really tried this so I didn't realize that the Downloads directory would keep coming back.  One thing you could do though is just make a symbolic link to Downloads:

```

cd ~
ln -s Downloads downloads

```


This way you could use either one and it would work.

---

### Post by m_duck on 2011-11-09
Do you use Firefox? Actually this is probably browser agnostic. You will need to change the download location to ~/downloads in the preferences of your browser. If you haven't done this already, it is probably just getting recreated each time you download something since ~/downloads is not the same as ~/Downloads.

---

### Post by ornages on 2011-11-09
I have Firefox installed, but I'm using Chromium and in Chromium I already changed the default download location to the new value.

---

### Post by ornages on 2011-11-09
hey great, this removed the bookmark in nautilus! I will check later if it also got rid of the folder comeback thing. Thanks so far!

---

