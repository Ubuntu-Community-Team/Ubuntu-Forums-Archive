---
title: "problems lead to a descion"
date: 2006-04-03
forum: Desktop Environments
---

### Post by amunimanghi on 2006-04-03
okay
here we go

1. I noticed after i reswitched back to a 56k modem (dont ask) there have been problems. 
    
    a. Prgrams quit with out notification directly to the desktop
    
    b. Programs crash (freeze)
         I. Aegis Virus Scanner
         II. Terminal
         III. Firefox
    
    c. I will leave the computer alone for a while (2 hours) and i will come        
       back finding the screen warped with a mix of colors at the top. The    
       computer is also crashed. 



2. There are more but I dont remeber. A source I have said I did something wrong. The only thing I have dont was try to install QEMU. I didnt get all of the dependencies it needed (25 MB) since i have a 56k modem. 

3. I deleted a lot of programs i didnt need.
    a. Deleted all of the games i had in Cedega
    b. Deleted around 6 GB of Duplicated Files.  (Zips for games)
    c. Deleted the extra games (tux racer...)
    d. I had 20 Gb of hd left. Now i have 39-41 Left. (80 gig total)

I Bascially did a hard drive cleanup. I am 100% sure i did not delete any files needed to 

4. If i cant fix this, I will move back to Windows XP, but honestly i dont want to. 


I will post a history of what i did in my terminal later. 

Help?

---

### Post by taurus on 2006-04-03
[QUOTE=amunimanghi]
4. If i cant fix this, I will move back to Windows XP, but honestly i dont want to. [/QUOTE]
Maybe it's me but I am kind of annoyed when people did something to their system which they shouldn't have (be careful using the sudo to remove stuff) and when they can't fix it because they don't remember what they've removed, they're always threaten to go back to Windows!!!  ](*,)  ](*,)  ](*,)

---

### Post by amunimanghi on 2006-04-03
[QUOTE=taurus]Maybe it's me but I am kind of annoyed when people did something to their system which they shouldn't have (be careful using the sudo to remove stuff) and when they can't fix it because they don't remember what they've removed, they're always threaten to go back to Windows!!!  ](*,)  ](*,)  ](*,)[/QUOTE]

this isnt the hate thread. ;) 

here is the terminal


  451  pwd
  452  xracer
  453  torc
  454  tarc
  455  torcs
  456  whereis torcs
  457  history
  458  history
  459  ~~~sudo gedit /etc/inittab'
  460  sudo gedit /etc/inittab
  461  uname -r
  462  uname -r && uname -m
  463  uname -r
  464  uname-m
  465  uname -m
  466  sudo apt-get install linux-k7 linux-headers-k7 linux-image-k7 linux-restricted-modules-k7
  467  exit
  468  qemu
  469  lsmod
  470  lspci
  471  /exec
  472  /
  473  start
  474  /Desktop/ey4.bat
  475  ls Desktop
  476  ls Desktop/ey4.bat
  477  nautilis
  478  nautilus
  479  sudo nautilus /Files
  480  sudo nautilus
  481  clamav
  482  whereis clamav
  483  whereis jasp
  484  whereis File
  485  sudo cedega
  486  sudo apt-get install clamav
  487  clamav
  488  whereis clamav
  489  start clamav
  490  whereis clamav
  491  clamab
  492  clamav
  493  whereis frox
  494  frox
  495  sudo frox
  496  whereis clamav
  497  run
  498  start
  499  beagle
  500  history

---

### Post by amunimanghi on 2006-04-04
i think i found out what may have been the problem. I tried to install QEMU. 

[http://en.wikipedia.org/wiki/QEMU]("http://en.wikipedia.org/wiki/QEMU")

[http://fabrice.bellard.free.fr/qemu/]("http://fabrice.bellard.free.fr/qemu/")

I downloaded the qemu-0.8.0.tar.gz. Then I needed some respitories, around 25 MB of downloading. I did this through the terminal. Since I have a 56k modem I couldnt download it all.  Earlier that day, everything was fine. The computer worked like a charm. My suspision is that this is what is causing the problem. You can find out what happened in the Terminal. 

Earlier that day, all else i did was deactivate my network connection, activate my modem, use cedega, and use the internet.

---

### Post by amunimanghi on 2006-04-04
in the last 6 minutes firefox has just 'vanished' 3 times. here is the last couple of lines my .xsession-errors.

```
(nautilus:8137): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(nautilus:8137): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(nautilus:8137): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(nautilus:8137): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(nautilus:8137): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed

(nautilus:8137): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(nautilus:8137): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(nautilus:8137): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

maybe this might help you

---

