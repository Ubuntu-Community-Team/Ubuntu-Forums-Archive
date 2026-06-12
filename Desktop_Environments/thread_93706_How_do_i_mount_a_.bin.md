---
title: "How do i mount a .bin"
date: 2005-11-22
forum: Desktop Environments
---

### Post by seiflotfy on 2005-11-22
hi guys
i have a .bin fiel but no .cue belonging to it
can i turn it to a iso or mount it in anyway???

---

### Post by Sheco on 2005-11-22
The bin file is probably the same format as an iso
```

sudo modprobe loop
sudo mount file.bin /mnt/place -o loop -t iso9660

```

---

### Post by souled on 2005-11-22
I don't think you can mount bin files that way. Get bin2iso and convert the bin file to iso. Then mount it with the command that Sheco gave.

---

### Post by Sheco on 2005-11-22
Try it, you might just be able to mount it just like that, I think I have done that before, but I might be wrong. :)

---

### Post by seiflotfy on 2005-11-22
didnt work :

sudo mount Neverwinter_Nights.CD1.bin /media/iso/ -t iso9660 -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
:(

---

### Post by seiflotfy on 2005-11-22
this also didnt work

 bin2iso Neverwinter_Nights.CD1.bin

Apr  7 2005, 03:59:12
bin2iso V1.9b - Converts RAW format (.bin) files to ISO/WAV format
               Bob Doiron, ICQ#280251

Check for updates at [http://users.andara.com/~doiron](http://users.andara.com/~doiron)


Error: Filename not found on first line of cuefile.

---

### Post by seiflotfy on 2005-11-22
bin2iso new.cue -c your.bin 
did the job

---

### Post by kashms on 2005-11-25
Where do you get this bin2iso utility? I couldn't find it in Synaptic.

---

### Post by iluminate on 2005-12-27
> Where do you get this bin2iso utility? I couldn't find it in Synaptic.
I have the same problem. Can not find it anywhere. Not even the deb package.
Where did you guys get it???

Peace

---

### Post by babwe on 2006-01-02
[QUOTE=iluminate]I have the same problem. Can not find it anywhere. Not even the deb package.
Where did you guys get it???

Peace[/QUOTE]
TRy this place
[http://www.linuxsoft.cz/en/sw_detail.php?id_item=2076](http://www.linuxsoft.cz/en/sw_detail.php?id_item=2076)

---

### Post by kaamos on 2006-01-02
bchunk does the same, and it's in the repos.
```
sudo apt-get install bchunk
bchunk foo.bin foo.cue foo
```
Better yet, save this as /usr/local/bin/bchunkcue and set the permission to execute
> 
#!bin/bash
echo "FILE ""$1.bin"" BINARY" >> $1.cue
echo "  TRACK 01 MODE1/2352" >> $1.cue
echo "    INDEX 01 00:00:00" >> $1.cue
bchunk $1.bin $1.cue $1_
rm $1.cue

and you can use bchunk without a cue file with the syntax "bchunkcue foo"

---

### Post by mr.lamp on 2006-01-26
[QUOTE=kaamos]bchunk does the same, and it's in the repos.
```
sudo apt-get install bchunk
bchunk foo.bin foo.cue foo
```
Better yet, save this as /usr/local/bin/bchunkcue and set the permission to execute

and you can use bchunk without a cue file with the syntax "bchunkcue foo"[/QUOTE]

thx!!

---

### Post by frague on 2006-05-01
[QUOTE=babwe]TRy this place
[http://www.linuxsoft.cz/en/sw_detail.php?id_item=2076](http://www.linuxsoft.cz/en/sw_detail.php?id_item=2076)[/QUOTE]

:confused: 

Uh ? I'm unable to download from both linuxsoft and doiron's website.

Any other idea ??

frague

---

### Post by Don_DiZzLe on 2006-08-05
[http://doc.gwos.org/index.php/Mount_ISO_script](http://doc.gwos.org/index.php/Mount_ISO_script)

---

### Post by ferose2 on 2006-08-10
You can mount bin files on KDE with [MountISO]("http://www.kde-apps.org/content/show.php?content=11577"), but, unfortunately, I don't know how to make it work on gnome. Does anyone know if its possible to run MountISO in gnome?

Nevermind Don_DiZzLe's link explains everything.

---

### Post by hamidaddin on 2007-05-24
Kaamos method worked for me perfectly. I had a .bin file without a corresponding .cue file.

The only modification I had to do was to change the first line in the suggested /usr/local/bin/bchunkcue from:


```
#!bin/bash
```

to:

```
#!/bin/bash
```

because I was getting this error:

```
bash: /usr/local/bin/bchunkcue: bin/bash: bad interpreter: No such file or directory
```

I prefer this method since it uses an application from the Ubuntu repositories.

Thanks Kaamos for the tip.

---

### Post by racadent on 2007-07-14
tnx!

---

### Post by Chewytwux on 2007-07-17
Why are y'all complicating this guys life.

Buddy go here n downlad the program and you're all set!!


[http://kde-apps.org/content/show.php?content=44805](http://kde-apps.org/content/show.php?content=44805)


Cheers

---

### Post by tedrogers on 2007-08-02
> **Chewytwux said:**
> Why are y'all complicating this guys life.

Buddy go here n downlad the program and you're all set!!


[http://kde-apps.org/content/show.php?content=44805](http://kde-apps.org/content/show.php?content=44805)


Cheers


I tried this....and I got this problem....what does this mean and how do I fix it under Gnome?

[IMG]http://i77.photobucket.com/albums/j58/fiddybux/dcop.jpg[/IMG]

UPDATE:

Have since ditched the suggested idea and gone with bchunk instead....much simpler really.

---

### Post by lixy on 2007-08-11
Thanks Kaamos!

---

### Post by lucaspr on 2007-09-11
Thanks Kaamos!! Very easy indeed! Much appreciated! :popcorn:

(Why aren't these things (there are more 'simple' scripts which do the job.. (like the installer for a brother printer/scanner)  in the Wiki Guide of Ubuntu? )

---

### Post by thinsoldier on 2007-11-24
how do I make a new file in /usr/local/bin/ so that I can use the bincue code ?

---

### Post by nisseblink on 2008-05-09
This program works like a charm! [http://ubuntuforums.org/showpost.php?p=4914937&postcount=17](http://ubuntuforums.org/showpost.php?p=4914937&postcount=17)

---

