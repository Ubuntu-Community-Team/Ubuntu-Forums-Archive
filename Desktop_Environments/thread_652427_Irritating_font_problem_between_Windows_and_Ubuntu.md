---
title: "Irritating font problem between Windows and Ubuntu"
date: 2007-12-28
forum: Desktop Environments
---

### Post by Saubazi on 2007-12-28
I originally ripped lots of my music cds to mp3 using windows and now I have a problem with filenames and character encoding. My backups are on DVD and when I insert them into the drive Ubuntu is not able to display characters such as "ä", "ö" or so correctly. I would like to have the names displayed correctly or rather I would like to copy the files so that filenames are converted to a proper character encoding.

Now I noticed that if I start windows with vmware and copy the files from the cd via samba it does the trick but it is somehow a too long shot - how can I do it directly?

---

### Post by mayhemt on 2007-12-28
Hows your /etc/fstab show your DVD/CD drive? Does it look this way?

```

/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```

the udf, iso9660 are the formats you should be worried about.

---

### Post by Saubazi on 2007-12-29
> **mayhemt said:**
> Hows your /etc/fstab show your DVD/CD drive? Does it look this way?

```

/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```

the udf, iso9660 are the formats you should be worried about.

those are just filesystems, the DVD reads ok and I can even play the files - that is not the issue - the issue is that some of the special chracters are shown garbled - I also do have mscorefonts installed so I do not quite know what the problem is. On more irritating level the id3 information seems to be similarly garbled as well...

---

### Post by PeterJS on 2007-12-29
Sounds like it might be a character encoding problem. I hope that's a push in the right direction because that's about all I know. I had a Blue Oyster Cult cd ripped that did that, I just gave up and ended up changing the letter to an O with out the umlauts.

---

### Post by Saubazi on 2007-12-29
It sure is a character encoding problem - msttcorefonts package just did not solve the problem :(

I am tad further with gentoo wiki [http://de.gentoo-wiki.com/Utf8](http://de.gentoo-wiki.com/Utf8)

if I put iocharset=utf8 in /etc/fstab then I get the filenames displayed in a readable manner...

---

