---
title: "DVD Playback?"
date: 2009-04-24
forum: General Help
---

### Post by omgseth on 2009-04-24
This may sound stupid, but does anyone know the definitive method of getting Jaunty to play DVDs? I just installed fresh and I don't want to open up Terminal and throw a bunch of random lines at it.

---

### Post by omgseth on 2009-04-24
Might there be a .deb package? I love those things...

---

### Post by ciborium on 2009-04-24
the package you need is something like libdvdcss

But if you just

sudo apt-get install vlc

or install VLC from the add/remove programs you will get it.

---

### Post by omgseth on 2009-04-24
I did actually install VLC, but it won't play any DVD's...

---

### Post by codeseer on 2009-04-24
> **omgseth said:**
> I did actually install VLC, but it won't play any DVD's...

libdvdcss2 and libdvdread3 and maybe libdvdnav4

---

### Post by omgseth on 2009-04-24
> **codeseer said:**
> libdvdcss2 and libdvdread3 and maybe libdvdnav4

How do I get those?

---

### Post by bacardiandwatermelon on 2009-04-24
sudo apt-get install libdvdread4


Should work I think....

---

### Post by zero777zero on 2009-04-24
unfortunately the command line is the only way i've been able to do this

open terminal, copy+paste: "sudo apt-get install medibuntu-keyring"
hit enter
copy+paste: "sudo apt-get update" into terminal
hit enter

For i386 Users install Codecs using the following command
"sudo apt-get install w32codecs libdvdcss2"

For amd64 Users install Codecs using the following command
"sudo apt-get install w64codecs libdvdcss2"

---

### Post by coffeecat on 2009-04-24
VLC doesn't come with libdvdcss2, which is not in any of the four Ubuntu repositories. However, you can get libdvdcss2 from [medibuntu]("http://www.medibuntu.org/"). Either download the deb file from there, or enable the medibuntu repository. There's a howto linked from the Medibuntu site.

As another poster said, you also need libdvdread4. The best way to get this is to install ubuntu-restricted extras, which also includes various restricted codecs and other useful packages.

If you install ubuntu-restricted-extras and libdvdcss2, you'll find that the default Totem Movie Player app will play DVDs, although VLC is probably a better all-round multimedia player.

---

### Post by m_2009 on 2009-04-24
Install the ubuntu-restricted-extras package in synaptics or in terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

This will give you DVD playback along with other extra codecs and file support such as MP3, the flash player plugin, rar files etc..

Then run the following command in the terminal window:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

This will install the libdvdcss2 package and enable playback of encrypted DVD', and also saves the need to add the Medibuntu respository.

---

### Post by m3alnemer on 2009-05-17
I had the same problem i fixed it using [this thread]("http://ubuntuforums.org/showthread.php?t=1137655&highlight=m3alnemer") 

Good Luck!

---

### Post by fain on 2009-06-21
> **m_2009 said:**
> Install the ubuntu-restricted-extras package in synaptics or in terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

This will give you DVD playback along with other extra codecs and file support such as MP3, the flash player plugin, rar files etc..

Then run the following command in the terminal window:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

This will install the libdvdcss2 package and enable playback of encrypted DVD', and also saves the need to add the Medibuntu respository.

Just a tip...If you have a DVD in your drive while running the above commands. You will need to re-mount the DVD b4 you can read it I learned that the hard way....

---

