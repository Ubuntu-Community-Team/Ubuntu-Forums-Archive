---
title: "Finding pictures by date"
date: 2013-05-23
forum: Desktop Environments
---

### Post by mikesmithv on 2013-05-23
My Pictures folder was once easily searchable in Nautilus by simply clicking on the "Modified" header once (or twice for inverted order).  I depended on this to know when major events happen, like weddings and such.  Were they married in June 2005 or June 2006, just look in the pictures around June for those dates and there is the answer, in pictures.

Then I ran Picasa and all that changed.  Picasa adds thumbnail and other files to the pictures folder which changes the modified date to that day.  Each of the folders now have the same date that Picasa scanned them but the actual picture files are untouched at least.  I know Picsa has it's "time tunnel" and other photo apps have similar wiz-bang features but I prefer the direct method of sorting by date in Nautilus and I want to restore that.  I no longer use Picasa so I tried deleting all Picasa-generated files hoping the folder would revert to the modified date of the pictures within:

```
find . -name 'Thumbs.*' -type f -delete
find . -name 'Picasa.ini' -type f -delete
```

Apparently removing files also update the modified date of the folder, so now they all have an even newer modified date.  Does anyone know if there is a way to make each folder reflect the date of the newest file(s) within each folder?

---

### Post by tgalati4 on 2013-05-23
Someone may have written a script to do this, but you can do it manually using the *touch* command:

```
man touch
```

Music files have a tag called ID3 that stores information such as the artist, track, album, genre, year, etc.  Pictures have a similar tag called EXIF.  There are some exif utilities that you can use to put the correct data in the EXIF tags:

exif - command-line utility to show EXIF information in JPEG files
exifprobe - Read metadata from digital pictures
exiftags - utility to read Exif tags from a digital camera JPEG file

The problem with relying on the creation date of the file is that it changes when files get copied and moved around.  What you want is the correct date in the EXIF file and that will not change as the photo is moved around.  Most photo viewers can display EXIF data and sort by that data.

---

### Post by mikesmithv on 2013-07-12
In case anyone stumbles on this post looking for a solution, I found one.  Shotwell Photo Manager has an Import function that creates a list by date of all your pictures.  You must launch Shotwell as an application, not by right-clicking on a picture (choosing Shotwell), otherwise you do not see the Import choice under File menu.  When you choose "Import by Folder" you can choose your Pictures directory then select the "Import without copying".  It builds a database of all your pictures by date and you can navigate through them in a tree list on the left side of the viewer.  It adds no extra files in the Pictures folder.  It keeps track of everything in a small database file in .local/share/shotwell/data in the Home directory.  It simply "does the right thing" using your Pictures folder and nothing more.  Very happy to discover this.

---

