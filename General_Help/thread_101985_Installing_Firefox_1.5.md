---
title: "Installing Firefox 1.5"
date: 2005-12-11
forum: General Help
---

### Post by Zonrox on 2005-12-11
Hello.

I've just downloaded the new Firefox tar file. I opened it but I don't know which file to install.

How do I install it?

Thanks.

---

### Post by psychicdragon on 2005-12-11
There's a file called *firefox* inside the tarball that is the exectutable. You just need to extract the tarball somewhere and you can run it.

What I did was extract the tar file to my bin (/home/david/bin/), then created a file called firefox15 in the bin with this as the contents:
```
#!/bin/sh

cd /home/david/bin/firefox
./firefox
```

Then run **chmod +x firefox15** to make the script executable. Now you can run Firefox 1.5 (or create a launcher for it), with the command *firefox15*.

---

### Post by Zonrox on 2005-12-11
Hmm... I can't seem to extract the file onto the bin directory says that I don't have the permission to do so. So, I'ma go figure this one out first.

---

### Post by Zonrox on 2005-12-11
Okaaay... I'm stuck here.

I can't extract the file to the directory you specified. Unless I do it in the terminal. What's the command to extract tar files in the terminal?

---

### Post by tkr7 on 2005-12-11
You can extract .tar-files by command:
tar -xvf filename
If this file is also gunzipped (.gz) you can do it also directly with tar-command:
tar -xvzf filename

---

### Post by GilGalad on 2005-12-11
There is a nice HowTo in here:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

