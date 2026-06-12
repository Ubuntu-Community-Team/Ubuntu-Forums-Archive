---
title: "gnome-xcf-thumbnailer does not generate thumbs in Nautilus"
date: 2012-12-30
forum: Desktop Environments
---

### Post by OrangeVixen on 2012-12-30
I downloaded and installed gnome-xcf-thumbnailer hoping that it would allow Nautilus to automatically generate thumbs in a directory full of GIMP .xcf image files, however it did nothing.

I found a bug regarding this at [https://bugs.launchpad.net/bugs/999070](https://bugs.launchpad.net/bugs/999070)

To fix it, you need to create the file:

/usr/share/thumbnailers/gnome-xcf.thumbnailer

```

sudo mkdir -p /usr/share/thumbnailers/
sudo nano /usr/share/thumbnailers/gnome-xcf.thumbnailer

```

and it should contain:

```

[Thumbnailer Entry]
TryExec=gnome-xcf-thumbnailer
Exec=gnome-xcf-thumbnailer %i %o
MimeType=image/x-xcf;image/x-compressed-xcf;

```

Save and then re-run Nautilus and it should begin create thumbs for .xcf files in any director. You may need to click on Reload in Nautilus.

---

### Post by BennyHill on 2013-01-03
Cheers for this, works great.

---

### Post by r_mano on 2013-05-18
I use a more eye-candy solution (the thumb will have a GIMP logo suprposed), i.e. having thumbnails like this: 

[IMG]http://www.rgtti.com/images/example-xcf-thumb.png[/IMG]

You need to  install gnome-xcf-thumbnailer as mentioned above, then you put the following script in /usr/bin with name xcf-thumb, executable by all (chmod a+rx /us/bin/xcf-thumb): 

```

#!/bin/bash

tmpfile1=$(tempfile --prefix xcft --suffix .png)

# remove file if something strange happens
trap 'rm -rf $tmpfile1' INT EXIT TERM

die() {
  echo >&2 "$@"
  rm -rf $tmpfile1
  exit 1
}
 
# The script will be called with parameters : -s %s %u %o
# -s %s: vertical size,  %u: input url, %o: output file

if [ $1 = "-s" ]; then 
   size=$2
   uin=$3
   fout=$4
else
   size=32 #default size
   uin=$1
   fout=$2
fi

# uin es una url, eliminar "file://"
fin=${uin#file://*}

gnome-xcf-thumbnailer -s $size $fin $tmpfile1 || die "gnome-xcf-thumbnailer failed"
composite -gravity southeast  \
   \(  -resize $((size/2))x$((size/2)) /usr/share/gimp/2.0/images/wilber.png \) \
   \( -resize $sizex$size $tmpfile1 \)  $fout || die "convert failed"
rm -rf $tmpfile1
exit 0

```

and putting im /usr/share/thumbnailers/ this other file: 

```

[Thumbnailer Entry]
Exec=/usr/bin/xcf-thumb -s %s %i %o
MimeType=image/x-xcf;image/x-compressed-xcf;

```

you will have nicer thumbnails that stands out from the other image formats...

---

### Post by dannyboytward on 2014-01-30
Does anyone know if there is a way to create the thumbnailer entry per user ( i.e. in ~/.local/share/thumbnailers ) rather than as root (i.e. in /usr/share/thumbnailers ).  I'd like to install a thumbnailer at work where I don't have root access, and it doesn't seem to work.

---

