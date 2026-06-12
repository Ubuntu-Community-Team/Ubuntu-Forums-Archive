---
title: "rsync not working --ecxlude option"
date: 2009-05-27
forum: General Help
---

### Post by Gingalone on 2009-05-27
I am trying (for weeks now!) to backup my data by means of rsync and presently the biggest problem I have is that I can't make work the option --exclude.
I tried --exclude=/home/doc to avoid the backup of the doc directory and tried --exclude-from=/home/norsync.txt, putting in norsync.txt the path /home/doc, but always rsync copies also the doc directory and the files in it.
I tried to put quotes (single, double and backquotes) before and after the exclude pathname but no way, rsync relentlessly continue to copy also the unwanted dir. Any idea? (I had a long look on forums, howtos and other online documentation about rsync without solve this problem)
Thanks for help,
Gingalone :confused::confused:

---

### Post by ianhaycox on 2009-05-27
In the exclude file I believe you need a leading - or + to include or exclude paths, e.g.

- /home/doc

however if there are previous entries that clash then this exclusion might not work.  Also note the way the rsync command is invoked can affect how leading /'s are processed. The "root of the transfer" is important.

Post your complete rsync command and exclusion file if you still can't get it to work.

---

### Post by Gingalone on 2009-05-27
> **ianhaycox said:**
> In the exclude file I believe you need a leading - or + to include or exclude paths, e.g.

- /home/doc

however if there are previous entries that clash then this exclusion might not work.  Also note the way the rsync command is invoked can affect how leading /'s are processed. The "root of the transfer" is important.

Post your complete rsync command and exclusion file if you still can't get it to work.

I tried:
code: sudo rsync -Havu --delete --exclude=/home/ginus/amd/doc/fax /home/ginus/doc /media/ging/rsync_test/

code: sudo rsync -Havu --delete --exclude=/home/ginus/amd/doc/fax/ /home/ginus/doc /media/ging/rsync_test/

code: sudo rsync -Havu --delete --exclude-from=/home/ginus/norsync.txt /home/ginus/doc /media/ging/rsync_test/

the file norsync.txt was:
 /home/ginus/doc/fax
and then
-/home/ginus/doc/fax

in all this tries rsync copied also the dir fax and its files...

Where's the trick?
Thank you for any help,
Gingalone
:confused:

---

### Post by ianhaycox on 2009-05-27
```

rsync -Havu --delete --exclude=/doc/fax /home/ginus/doc /media/ging/rsync_test/

```

Will ignore fax and all files within, but still copy files within doc

```

rsync -Havu --delete --exclude=/doc /home/ginus/doc /media/ging/rsync_test/

```

Will ignore doc

Using the --dry-run option (or -n) helps.

Basically matching the exclude pattern starts after /home/ginus.
Check out man rsync and look specifically at the section ANCHORING INCLUDE/EXCLUDE PATTERNS as it explains it better than I can.

Note: in your norsync.txt file you need a space between - (minus) and the path.

---

### Post by Legace on 2009-05-27
I have an set it up like this:

```
rsync -av --delete --exclude-from="exclude" / /backup
```

The file **exclude** which is in my home directory (~/exclude) contains the following:
```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
```

If it doesn't work, try cd to your home directory:
```
cd ~
```

Hope this clears things up.

---

### Post by XCan on 2009-05-27
> **Gingalone said:**
> I tried:
code: sudo rsync -Havu --delete --exclude=/home/ginus/amd/doc/fax /home/ginus/doc /media/ging/rsync_test/

code: sudo rsync -Havu --delete --exclude=/home/ginus/amd/doc/fax/ /home/ginus/doc /media/ging/rsync_test/

code: sudo rsync -Havu --delete --exclude-from=/home/ginus/norsync.txt /home/ginus/doc /media/ging/rsync_test/

the file norsync.txt was:
 /home/ginus/doc/fax
and then
-/home/ginus/doc/fax

in all this tries rsync copied also the dir fax and its files...

Where's the trick?
Thank you for any help,
Gingalone
:confused:


I think the trick is that the 'root' dir as rsync sees it starts at the last dir of the source's path, i.e. /home/ginus/. This means that when you tells it to 
```
--exclude=/home/ginus/amd/doc/fax 
```
the path rsync actually really will exclude would be
```
/home/ginus/home/ginus/amd/doc/fax
```.

Hence as ianhaycox pointed out what you want to do is simply
```
--exclude=/doc/fax
```.

---

### Post by Gingalone on 2009-05-29
Thank you, it was really a bit tricky!
:p

---

### Post by colau on 2009-06-04
> **Legace said:**
> I have an set it up like this:

```
rsync -av --delete --exclude-from="exclude" / /backup
```

The file **exclude** which is in my home directory (~/exclude) contains the following:
```

boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
```

If it doesn't work, try cd to your home directory:
```
cd ~
```

Hope this clears things up.
One quesion.
Won't the exclude file be like this?
```

/boot/
/proc/
/dev/
/lost+found/
/sys/
/media/
/tmp/
/backup/

```

---

### Post by Legace on 2009-06-04
> **colau said:**
> One quesion.
Won't the exclude file be like this?

I used it like below and it worked for me.. :)

```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
```

---

### Post by colau on 2009-06-04
> **Legace said:**
> I used it like below and it worked for me.. :)

```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
```
But where is the /backup directory?
Should it not be excluded?
```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
backup/

```

---

### Post by Legace on 2009-06-04
> **colau said:**
> But where is the /backup directory?
Should it not be excluded?
```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
backup/

```

Yeah I forgot it. It should be there. :)

---

