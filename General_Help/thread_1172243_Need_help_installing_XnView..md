---
title: "Need help installing XnView."
date: 2009-05-28
forum: General Help
---

### Post by Hansmc on 2009-05-28
Need help installing XnView.

I went to [http://www.xnview.com/en/downloadunix.html](http://www.xnview.com/en/downloadunix.html) and down loaded the zip file and unzipped it but do not know what to do with it. There does not seem to be any Ubuntu package, only an rpm.

Thanks for your help.

---

### Post by x33a on 2009-05-28
download alien
```
sudo aptitude install alien
```

with alien you can convert debian (.deb) packages to red hat (.rpm) and vice-versa.

after installing alien, download the xnview rpm file and open the download directory in the terminal and, use this command to convert rpm to deb
```
sudo alien -k filename.rpm
```

this will generate a deb file, which you can install using dpkg or double clicking on that file.

---

### Post by Hansmc on 2009-05-28
Thanks x33a. The installation worked fine, but xnview does not work. I ran 'xnview' from the terminal and all that comes up is a little window that has the 'file', 'options', and 'info' menus on it.

---

### Post by x33a on 2009-05-28
so you aren't able to open any images using the file menu?

i haven't tried xnview, but maybe you can try the windows version with wine.

Though, i would strongly suggest you use a linux alternative. i was a big fan of fast stone image viewer on windows, but gradually i started liking linux options.

eye of gnome, gthumb, f-spot, gwenview are a few of the good options.

---

### Post by Hansmc on 2009-05-28
I am able to open a picture using the file menu, but it looks relay bad. The picture is verily visible and the window is mostly transparent, and buttons are just blobs.

Why am I trying to install xnview? See [http://ubuntuforums.org/showthread.php?t=1171744](http://ubuntuforums.org/showthread.php?t=1171744)

Thanks for your help.

---

### Post by pbateman on 2009-09-29
I am having the exact same issue with xnview.....did you ever get this resolved?

---

### Post by raziv on 2010-01-04
I have the same problem after installing the .rpm with alien. The thing is it happens only when using compiz (Appearance/Visual Effects set to "Normal" or "Extra"), but when setting Appearance/Visual Effects to "None" xnview looks and displays images just fine.

---

### Post by raziv on 2010-01-04
Googling around I've found three workarounds for that. I tried the first two and they seem to work:
1. Using xnview option.
Start xnview with the following command (you can enter it in the "open with/other application/use a custom command" field through nautius:
```
xnview -visualid 0x21
```
2. Using an environment variable.
I wasn't able to use it in nautilus' "use a custom command" - only from terminal, so I don't use it, though to me it smells like a more sound workaround:
```
XLIB_SKIP_ARGB_VISUALS=1 xnview
```
3. Tinkering with compiz.
See [this thread]("http://forum.compiz.org/viewtopic.php?f=86&t=3622&p=25813") in the Compiz Community Forums for an in-depth discussion, references, and everlasting excitement :)
HTH

---

### Post by luigi_mb on 2010-01-04
> **Hansmc said:**
> Need help installing XnView.

I went to [http://www.xnview.com/en/downloadunix.html](http://www.xnview.com/en/downloadunix.html) and down loaded the zip file and unzipped it but do not know what to do with it. There does not seem to be any Ubuntu package, only an rpm.

Thanks for your help.

Go to

[http://newsgroup.xnview.com/viewtopic.php?t=16416](http://newsgroup.xnview.com/viewtopic.php?t=16416)

You must register, but then you will be able to download the new version for Linux . It's work in progress, but it already runs well.

/luigi

---

### Post by julovac on 2010-03-11
> **Hansmc said:**
> I am able to open a picture using the file menu, but it looks relay bad. The picture is verily visible and the window is mostly transparent, and buttons are just blobs.

Why am I trying to install xnview? See [http://ubuntuforums.org/showthread.php?t=1171744](http://ubuntuforums.org/showthread.php?t=1171744)

Thanks for your help.

Compiz Settings Manager, Window Rules, No ARGB visuals
add      class=XnView
works fine after that

---

