---
title: "FAT32 mount character map?"
date: 2006-01-16
forum: General Help
---

### Post by Garyu on 2006-01-16
I have tried posting this in beginners talk, but I haven't got any usable replies, so I will try to post it here as well:

I have a FAT-partition (made in WinXP but without OS) for exchanging files like MP3 and documents between OSs. However, when I create files with swedish characters in WinXP they show as "?" where there are swedish characters, i.e. "J?gm?starprogrammet" where it should say "Jägmästarprogrammet". This also means I can not open the files. I can, however, send them with GAIM to users on my contact list, but that is of little help for me.

My /etc/fstab looks like this:
```
/dev/hda5       /FAT            vfat    rw,utf8,umask=0000	0	0

```

I also tried:
```
/dev/hda5       /FAT            vfat    iocharset=iso8859-1,umask=0000	0	0
```

none of this works... the iso8859-1 seems like a more probable solution though, even though it still does not work... so... any suggestions?

---

### Post by epostma on 2006-01-16
Ok, maybe you know this, but first: if you're trying a couple of options out, the best is to first try on the command line before you enter stuff into /etc/fstab, because it's less typing if you get it wrong the first couple of times. Now on to your actual problem...

You could try
```
mount /dev/hda5 /FAT -t vfat -o codepage=850
```
or with codepages 852 or 857 (just try one by one). Another option seems to be
```
mount /dev/hda5 /FAT -t vfat -o uni_xlate
```
which translates the characters into weird sequences, but at least you should be able to open the files.

If one of these works, then edit /etc/fstab and put the option there instead of the utf8 part -- e.g.,
```
/dev/hda5       /FAT            vfat    rw,codepage=850,umask=0000	0	0
```

HTH,

---

### Post by Garyu on 2006-01-16
Thank you for your suggestion epostma, but it did not work.

I tried codepage 850, 852 and 857. I even tried iocharset=iso8859-1,codepage=850 but that did not work either.

sudo mount /dev/hda5 /FAT -t vfat -o uni_xlate
also, that command does the same thing as everything else. I can see everyting, most files ar OK, but the one with swedish characters "does not exist".

One thing I realized I did not mention earlier. Next to the filename with swedish characters it says "(Invalid encoding)".

---

### Post by Garyu on 2006-01-18
funny thing... I just removed "rw," and one of the zeroes, and suddenly it started working. :)

/dev/hda5       /FTP            vfat    utf8,umask=000	0	0

this is what my /etc/fstab looks like now...

I just tried every kind of combination I could think of and suddenly... I don't understand how, but no matter, as long as it is working I am fine with not knowing why or how. :P

---

### Post by epostma on 2006-01-20
Ok, good to hear that it worked out in the end!

---

