---
title: "&quot;Invalid unicode&quot; in Nautilus and Öö Ää characters"
date: 2004-11-03
forum: Desktop Environments
---

### Post by hyde on 2004-11-03
If I have file which has non-english character in its name, Nautilus says "invalid unicode" and shows question mark instead of character. 

I know it is coding problem, Gnome probably uses UTF-8 coding. How to change it to use ISO-8859-1 coding? I have Finnish / Swedish keyboard (they are same) , and keyboard works fine.

---

### Post by JsPr on 2004-11-06
[QUOTE=hyde]If I have file which has non-english character in its name, Nautilus says "invalid unicode" and shows question mark instead of character. 

I know it is coding problem, Gnome probably uses UTF-8 coding. How to change it to use ISO-8859-1 coding? I have Finnish / Swedish keyboard (they are same) , and keyboard works fine.[/QUOTE]
 Could you past the output of the locale command? I have no problems with åäö in Nautilus.

---

### Post by Julius on 2004-11-06
I'm having problems with files/folders that contain ÁÉÍÓÚ/áéíóú in my windows partition.
They just won't show up in nautilus, or it will show different characters instead.
It's not really a problem, but some apps, like the gimp, will simply ignore the existence of folders with those special characters.

---

### Post by JsPr on 2004-11-06
I use ISO8859-1 as my character set in Ubuntu. I wonder if windows use that windows-1252 or something and that's why your listing gets wrong. Can you see the correct chars in a xterm/console?

---

### Post by bucho on 2004-12-19
Did you ever find a solution to this problem?  I have the same issue using Hoary when trying to read certain filenames from a vfat partition.

---

### Post by JsPr on 2004-12-20
[http://www.ubuntuforums.org/showthread.php?t=7344&highlight=convert+utf-8](http://www.ubuntuforums.org/showthread.php?t=7344&highlight=convert+utf-8)

---

### Post by docomo on 2005-01-02
I had the problem that filenames with åäö in my ntfs partitions were not displayed correctly in nautilus. I solved it by adding this option to the ntfs partitions in my /etc/fstab :

iocharset=utf8

Now everything works fine. From [http://linux-ntfs.sourceforge.net/info/ntfs.html](http://linux-ntfs.sourceforge.net/info/ntfs.html):

    NTFS stores all file and directory names in Unicode which can represent any character from any language. By default the Linux NTFS driver converts the names to ASCII which is OK for some people, but no good if your languages includes letters like å or é.

    NLS (Native Language Support) controls how characters are displayed. You can choose either utf8 which, like Unicode, can represent all characters, or your own codepage, e.g. iso8859-1 (Western Europe), iso8859-2 (Central Europe), gb2312 (Simplified Chinese), iso8859-8 (Hebrew). Below are some example mount commands:

    mount /dev/hda1 /mnt/windows -t ntfs -r -o iocharset=utf8
    mount /dev/hda1 /mnt/windows -t ntfs -r -o iocharset=iso8859-2
    mount /dev/hda1 /mnt/windows -t ntfs -r -o iocharset=gb2312

---

### Post by adamkane on 2006-03-13
This is an ancient thread, but a lot of people are still reading it, so I wanted to post some additional info.

Windows NTFS partitions must be mounted with nls=utf8 added to the /etc/fstab file in order to see special characters.

Windows partitions use CP850 encoding, not ISO-8859-1 encoding. If you are unfortunate enough to transfer files from a Windows partition to an ext3 partition, and you forget to mount the partition using nls=utf8, you need to convert your filenames using: 

```

convmv -f cp850 -t utf-8 -r *.*

``` 
There are Nautilus scripts and Konqueror service menus available that will perform this operation for you as well.

If you have archives of ISO-8859-1 encoded files, you need use the following to convert the filenames of your extracted files to UTF-8:

```

convmv -f iso-8859-1 -t utf-8 -r *.*

``` 
convmv can handle many different encodings:

```

convmv --list

```

---

### Post by louisgag on 2007-01-21
> **adamkane said:**
> This is an ancient thread, but a lot of people are still reading it, so I wanted to post some additional info.

Windows NTFS partitions must be mounted with nls=utf8 added to the /etc/fstab file in order to see special characters.

Windows partitions use CP850 encoding, not ISO-8859-1 encoding. If you are unfortunate enough to transfer files from a Windows partition to an ext3 partition, and you forget to mount the partition using nls=utf8, you need to convert your filenames using: 

```

convmv -f cp850 -t utf-8 -r *.*

``` 
There are Nautilus scripts and Konqueror service menus available that will perform this operation for you as well.

If you have archives of ISO-8859-1 encoded files, you need use the following to convert the filenames of your extracted files to UTF-8:

```

convmv -f iso-8859-1 -t utf-8 -r *.*

``` 
convmv can handle many different encodings:

```

convmv --list

```

Thanks alot! That finally solved my problem! Although my file format was iso8859-1 from windows XP, I guess that's dependant on your windows location settings... :)

---

### Post by Egils on 2007-04-17
An additional note on UTF8 foreign / non-English characters and mounting NTFS partitions, despite having mounted my NTFS partitions with the nls=utf8 option in my fstab I was unable to copy files over from my linux partitions to the NTFS partitions (mounted with read/write support using the NTFS-3G  drivers) when the files included non-English characters in the file name. 

I eventually discovered that it is still necessary to include the iocharset=utf8 option in addition to the nls=utf8 option in fstab. Eg:

/dev/xxxx   /media/xxxx   ntfs-3g   defaults,nls=utf8,iocharset=utf8   0  0

Now I can copy over files with names that include non-English European characters (ö ä å ñ ã õ ç é è á à etc) as well as Asian (Chinese, Japanese, Korean, etc.) characters.

EDIT
It turned out that using the nls and iocharset options did not solve my problems, but using the locale option did. For example:

/dev/xxxx   /media/xxxx   ntfs-3g   defaults,locale=fr_FR.utf8   0  0

To use the locale option the corresponding language support also had to be installed in the System>Administration>Language Support panel.

---

