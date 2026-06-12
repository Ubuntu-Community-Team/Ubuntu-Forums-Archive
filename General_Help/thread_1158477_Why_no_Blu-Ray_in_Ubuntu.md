---
title: "Why no Blu-Ray in Ubuntu?"
date: 2009-05-13
forum: General Help
---

### Post by PsychedelicWonders on 2009-05-13
Why is Blu-Ray not possible in ubuntu?
 
Also, why do I have issues playing regular dvds in Ubuntu?
 
it just opens the program and gives me an error message for regular dvds?

---

### Post by fictivetoast on 2009-05-13
I also can't get dvds to play in Jaunty, although I've installed vlc and ubuntu-restricted extras, and have the universe repo enabled.  Something about the drive being locked...  I've had no trouble in previous releases.

---

### Post by Kareeser on 2009-05-13
Blu-ray is a proprietary technology, and requires a paid licence to use it.

Publishing their decryption sequence would violate their terms of agreement, not to mention it would undercut that profits massively.

Hence, no port has been made for Linux.

HD DVD should've won.

---

### Post by WIGGMPk on 2009-05-13
Do you have libdvdcss2 installed on your machine?

The DVD Movie your trying to play most likely has some sort of encryption. Due to certain legal issues, libdvdcss2 is not installed out of the box.

If this is the case, which I think it is, install the medibuntu repositories and install the libdvdcss2 package. All of the info you need can be found here:

```
https://help.ubuntu.com/community/Medibuntu
```

As far as Blu-Ray discs, I really cant help you with that because I dont own a blu-ray drive for my laptop. Although the options for what to do when a Blu-Ray disc is inserted into the drive are available in Gnome.

---

### Post by SentientFluid on 2009-05-13
[Info using Blu-ray/HD DVD in Intrepid]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD")

Google also brings up [other articles]("http://www.google.ca/search?source=ig&hl=en&rlz=&q=ubuntu+blu-ray&meta=lr%3D").

---

### Post by PsychedelicWonders on 2009-05-25
Ok, so if Blu-ray is a no go on Ubuntu

How do we get normal DVD's & HD-DVD's to play?

---

### Post by zero777zero on 2009-05-25
did you read any of the replys by any chance?

---

### Post by PsychedelicWonders on 2009-05-25
Whoops, I cant believe it didnt click.  thanks.

---

### Post by edm1 on 2009-05-25
For normal DVDs it's as easy as

```
sudo /usr/share/doc/libdvdread4/./install-css.sh
```

---

### Post by glotz on 2009-05-25
[http://bluraysucks.com/](http://bluraysucks.com/)

---

### Post by PsychedelicWonders on 2009-05-25
> **edm1 said:**
> For normal DVDs it's as easy as

```
sudo /usr/share/doc/libdvdread4/./install-css.sh
```

Ok, I will run that code a little later when I get a chance, thanks.

regarding bluraysucks.com

I will say this, I have a brand new, top of the line 46" Samsung and a brand new top of the line computer that I built.  

So I have the bit of the luxury of just buying a $100 blu-ray player/HD-dvd/cd/player/burner and having it all.

So I might as well enjoy the Blu-ray while its around.

Because lets be honest, its probably the only form of HD we'll have for a while.  

Thats pretty crazy blu-rays will self destruct if hacked.

---

### Post by glotz on 2009-05-25
[QUOTE=PsychedelicWonders]
Because lets be honest, its probably the only form of HD we'll have for a while.[/QUOTE]
It's just that's exactly what was said about regular (double-sided) DVDs.

---

### Post by zero777zero on 2009-05-25
the fact of the matter is that blu-ray quality is amazing. the only other option for highdef is torrents

---

