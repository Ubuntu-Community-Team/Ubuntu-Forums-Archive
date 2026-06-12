---
title: "Update Manager failing"
date: 2009-02-05
forum: General Help
---

### Post by Dobbie03 on 2009-02-05
I tried to do an update this morning but it failed and I recieved this message:

Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/exaile/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/exaile/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Anyone have any ideas how to get around this?

---

### Post by Zill on 2009-02-05
> [http://download.tuxfamily.org/syzygy42/dists/feisty/exaile/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/exaile/binary-i386/Packages.gz)  

Looks like you are trying to download feisty files.  This release is no longer supported.

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

If you are still running feisty then it is time to upgrade. ;-)

Otherwise just delete the offending line from your /etc/apt/sources.list file.

---

### Post by Dobbie03 on 2009-02-05
Thank you.

---

### Post by Dobbie03 on 2009-02-05
ummm how do I delete that line?  where do I go?

---

### Post by Zill on 2009-02-05
> **MattDobson said:**
> ummm how do I delete that line?  where do I go?

Open the Terminal (Menu: Applications, Accessories, Terminal) then open the sources.list file with the nano editor by copying and pasting the following code:

```
sudo nano /etc/apt/sources.list
```

Hit ctrl-k to delete the line containing "http://download.tuxfamily.org/syzygy42/dists/feisty/exaile/binary-i386/Packages.gz"

Hit ctrl-o to save the revised file, then hit ctrl-x to exit the nano editor.

---

