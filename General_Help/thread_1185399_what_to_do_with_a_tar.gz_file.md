---
title: "what to do with a tar.gz file"
date: 2009-06-12
forum: General Help
---

### Post by chebbie on 2009-06-12
guys i've been searching and searching and there is no other way to understand how to compile or what to do with a tar.gz file.
each and everyone in this forum has been kind in explaning, but your explanation for such matters are too complicated for a newbie in Linux to understand.
you're talking about installing something before doing something else.
i would appreciate if someone could explain from the very beginning in very simple terms what do to line by line.
i would really appreciate it.
thanks.

---

### Post by colau on 2009-06-12
> **chebbie said:**
> guys i've been searching and searching and there is no other way to understand how to compile or what to do with a tar.gz file.
each and everyone in this forum has been kind in explaning, but your explanation for such matters are too complicated for a newbie in Linux to understand.
you're talking about installing something before doing something else.
i would appreciate if someone could explain from the very beginning in very simple terms what do to line by line.
i would really appreciate it.
thanks.
```

tar vzxf filename.tar.gz
cd filename
./configure
make
sudo make install

```

---

### Post by rCXer on 2009-06-12
tar.gz files are like zip files in windows.
If you want to extract the files graphically, double click on it to show it's contents.  To extract it's contents either drag them from the tar.gz window (to select multiple files hold down ctrl).  Or click on the "extract" button and give it a location.

---

### Post by dk_learning_linux on 2009-06-12
It is a type of compression file format like zip. You can extract files in it using the above ways mentioned by our friends. See [here]("http://en.wikipedia.org/wiki/Tar_(file_format)") for more information about tar.gz

---

### Post by gradinaruvasile on 2009-06-12
> **chebbie said:**
> guys i've been searching and searching and there is no other way to understand how to compile or what to do with a tar.gz file.
each and everyone in this forum has been kind in explaning, but your explanation for such matters are too complicated for a newbie in Linux to understand.
you're talking about installing something before doing something else.
i would appreciate if someone could explain from the very beginning in very simple terms what do to line by line.
i would really appreciate it.
thanks.

In this case try finding an ubuntu package (deb) for whatever are you trying to compile.

---

### Post by chebbie on 2009-06-13
my other problems are with the compilling. cans omebody explain to me in very simple terms how to compile, what software are needed before hand before compilling like alien (how to install it and run it).

i've downloaded flash plug in 10 i unzip the tar.gz file and the flasbplayer-intaller is locked.  There is a lock somehow on the folder.  Why's that.  And I did download the linux version.

tar.bz2 is the same as tar.gz?

please explain to me how to compile since there are lots of software whereby you have to compile since the .deb file is not available.

i've downloaded the filezilla tar.bz2 and after unzipping and got two folders in there, namely bin and share.  not .deb anywhere.  What to do with these folders?

---

### Post by asmoore82 on 2009-06-13
> **chebbie said:**
> my other problems are with the compilling. cans omebody explain to me in very simple terms how to compile, what software are needed before hand before compilling like alien (how to install it and run it).

i've downloaded flash plug in 10 i unzip the tar.gz file and the flasbplayer-intaller is locked.  There is a lock somehow on the folder.  Why's that.  And I did download the linux version.

tar.bz2 is the same as tar.gz?

please explain to me how to compile since there are lots of software whereby you have to compile since the .deb file is not available.

i've downloaded the filezilla tar.bz2 and after unzipping and got two folders in there, namely bin and share.  not .deb anywhere.  What to do with these folders?

you've got the wrong flash plugin 10 -
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

---

### Post by kostkon on 2009-06-13
> **chebbie said:**
> my other problems are with the compilling. cans omebody explain to me in very simple terms how to compile, what software are needed before hand before compilling like alien (how to install it and run it).

i've downloaded flash plug in 10 i unzip the tar.gz file and the flasbplayer-intaller is locked.  There is a lock somehow on the folder.  Why's that.  And I did download the linux version.

tar.bz2 is the same as tar.gz?

please explain to me how to compile since there are lots of software whereby you have to compile since the .deb file is not available.

i've downloaded the filezilla tar.bz2 and after unzipping and got two folders in there, namely bin and share.  not .deb anywhere.  What to do with these folders?
Both Flash 10 and Filezilla are in the repositories. Check [this nice how-to on how to install software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware").

Hope that helps somehow.

---

