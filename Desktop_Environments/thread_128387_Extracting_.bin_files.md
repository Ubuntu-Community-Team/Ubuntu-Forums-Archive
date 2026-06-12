---
title: "Extracting .bin files?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by stalefries on 2006-02-11
I have a rogue .bin file that I need to get extracted, but I cannot find any way to extract besides buying a Mac, which is obviously out of the question.

I'm getting [this]("http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.0.x/System_7.0.1.smi.bin") .bin file, in relation to [this]("http://nothickmanuals.info/doku.php?id=minivmac") project, and I can't seem to find anything to extract it. Does anyone out there own a Mac, and could you extract this file for me, or is there a way I could do it myself?

---

### Post by lha on 2006-02-11
Install [bchunk]("http://he.fi/bchunk/") from universe.

---

### Post by stalefries on 2006-02-11
It's just a .bin file. It didn't come with a .cue file.

---

### Post by taurus on 2006-02-11
Or you can try something like 

chmod 755 <filename>.bin
./<filename>.bin

---

### Post by stalefries on 2006-02-11
I already tried that. It's not executable.

---

### Post by taurus on 2006-02-11
Do you know what is that file about?  Is it a movie, data, etc.?

---

### Post by kaamos on 2006-02-11
Try this: [http://ubuntuforums.org/showpost.php?p=620412&postcount=11](http://ubuntuforums.org/showpost.php?p=620412&postcount=11)

---

### Post by stalefries on 2006-02-11
Thanks, kaamos. That worked perfectly.

Edit: Scratch that. There were supposed to be multiple files, of name and type I do not know. I only got one file, an iso, which didn't check out.

---

### Post by stalefries on 2006-02-13
It seems that it is supposed to be some sort of archive.

---

### Post by taurus on 2006-02-13
With iso, you can mount it and access it as

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.iso /mnt/iso
cd /mnt/iso
ls -la

---

### Post by stalefries on 2006-02-14
After the second command, I get:
```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by taurus on 2006-02-14
So what does "dmesg | tail" say then?  Again, you can only mount an iso file, NOT a bin file, with that command...

---

### Post by stalefries on 2006-02-14
I know I tryed the .iso it produced. 

I did the dmsg | tail thing, then re-tried the mount, then "dmesg | tail"'ed once again, and the only difference was:

```

[5101387.403000] Unable to identify CD-ROM format.

```

Which makes sense. It seems that it isn't supposed to be an .iso.

---

### Post by taurus on 2006-02-14
Then perhaps it's not an iso format then!!!  What does it say when you run this command?

file <filename>.iso

---

### Post by mednamot on 2006-02-14
ya know...I have it in my mind that the xbox mod community had a few tools around for cracking bins...

I haven't the time at the moment, but check like xbox-scene.com...

I'm near positive I had bin extraction tools on my machine before

---

### Post by stalefries on 2006-02-14
It reports: "data".

I'll check that xbox site later. Gotta do homework. :)

---

### Post by stalefries on 2006-02-14
I found this:

[http://www.xbox-scene.com/xbox360-tools/JADE.binUnpacker.php](http://www.xbox-scene.com/xbox360-tools/JADE.binUnpacker.php)

On the xbox site. I tried running it under wine, and that apparently didn't work. I also tried compiling it, but I couldn't get it to go.

---

