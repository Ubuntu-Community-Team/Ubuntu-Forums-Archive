---
title: "Linux Movie Maker suggestions?"
date: 2006-08-23
forum: Desktop Environments
---

### Post by artinla on 2006-08-23
Is there a good program that will allow me to capture video from my camcorder and edit/add music/etc. in Ubuntu similar to Microsoft Movie Maker, Adobe Premier, Pinnacle 10 etc?

I have no clue where to look or what is a good package for Ubuntu.

Thanks,

Art

---

### Post by reclusivemonkey on 2006-08-23
> **artinla said:**
> Is there a good program that will allow me to capture video from my camcorder and edit/add music/etc. in Ubuntu similar to Microsoft Movie Maker, Adobe Premier, Pinnacle 10 etc?

I have no clue where to look or what is a good package for Ubuntu.


I would suggest Kino. Whether or not it will compare with the packages you mention I can't say; I have never used any of them. I've only used Kino to make movies from Counter-Strike demos exported to a series of .tga's. I am presuming its a digital camcorder you are talking about.

[http://www.kinodv.org/](http://www.kinodv.org/)

Other options available to you are;

[http://lives.sourceforge.net/](http://lives.sourceforge.net/)
[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)
[http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/)
[http://pitivi.sourceforge.net/](http://pitivi.sourceforge.net/)

Although I would say that if you have a digital camcorder, Kino would be your best option. HTH

---

### Post by Kabatwa on 2006-08-23
Haven't tried my dvcam in Linux yet but some good programs you might want to keep your eye on are:

Cinelerra (Interface is terrible but works well!) - [http://www.heroinewarrior.com/cinelerra.php3]("http://www.heroinewarrior.com/cinelerra.php3")

Jahshaka - [http://www.jahshaka.org/]("http://www.jahshaka.org/")

---

### Post by fakie_flip on 2006-08-23
I use avidemux for editing video, and audacity for editing mp3s and other sound formats. Kino doesn't allow me to edit the type of video format my digital camera creates.

---

### Post by finite9 on 2006-08-23
Kino seems to have problems with connecting DV cams via firewire.  Keeps saying that the IEEE-1394 module could not be loaded.  Seems like there is no real solution to this - search forums for Kino.

---

### Post by fakie_flip on 2006-08-28
Try the software I mentioned.

---

### Post by norwyn on 2006-09-02
Anyone been able to install [Jahshaka]("http://www.jahshaka.org/"), [LiVES]("http://lives.sourceforge.net/"), [PiTiVi]("http://pitivi.sourceforge.net/") or even [Diva]("http://www.diva-project.org/") on dapper?

[EDIT]
Well, acctually I just installed Jahshaka, but I cannot say I'm impressed...yet. But hopefully, I will be.

To install Jahshaka: 

Not sure if this is standard, but adding this to /etc/apt/sources.list worked for me:
```

sudo gedit /etc/apt/sources.list
```

Add the textline in the end of you sources.list document.
FOR BREEZY:

```
deb http://repo.jahshaka.org/ubuntu/breezy/ binary-i386/
```

FOR DAPPER:

```
deb http://repo.jahshaka.org/ubuntu/dapper/ binary-i386/
```

(note the space between the url and the binary-i386/).

Then save.

Update your repository
```
sudo apt-get update
```

...and then install jahshaka
```
sudo apt-get install jahshaka
```

...and get it kicking by typing "jahshaka" in a terminal.
[Jahshaka forum thread]("http://www.jahshaka.org/component/option,com_forum/Itemid,45/page,viewtopic/t,830/postdays,0/postorder,asc/highlight,ubuntu/start,15/")
[/EDIT]

---

### Post by padre999 on 2006-09-02
An option would also by Mainconcepts's Mainactor. But it is not for free...

[http://www.mainconcept.com/site/index.php?id=395](http://www.mainconcept.com/site/index.php?id=395)

---

### Post by reclusivemonkey on 2006-09-02
> **norwyn said:**
> Anyone been able to install [Jahshaka]("http://www.jahshaka.org/"), [LiVES]("http://lives.sourceforge.net/"), [PiTiVi]("http://pitivi.sourceforge.net/") or even [Diva]("http://www.diva-project.org/") on dapper?


Apparently, yes;

[http://www.ubuntuforums.org/showthread.php?t=241330&highlight=lives](http://www.ubuntuforums.org/showthread.php?t=241330&highlight=lives)

---

