---
title: "mp3 fonts"
date: 2005-04-23
forum: Desktop Environments
---

### Post by ishkabob on 2005-04-23
Ok I've been using Ubuntu for a few weeks now and its just great.  I have tried to make the full switch in the past but to no avail, I think this is finally the answer.  I have an ntfs drive mounted that I just copied all of my mp3s from onto my linux drive.  They are organized into directories by artist and album, however, if I have an artist, or an album, or a song title with certain characters, it will not display them correctly.  For example, Bjork (which should have umlauts over the O) will display as B?rk.  It will display the characters fine in the id3 tag, like in rhythmbox or xmms, but not the file names.  Fonts are something I guess I never had to learn anything about in Windows so I never bothered.  Do I need to install truetype fonts?

Along the same lines, If I type something in OpenOffice, save it as an rtf and then try and print it from a windows machine, the fonts do not translate well, which is bad considering I'm a college student and usually need to meet some stupid page requirement.  Any help is much appreciated

---

### Post by Dr Gonzo on 2005-04-23
No, it's that filenames can only contain certain characters.  I think you pretty much have to use standard English characters.  I've never tried to internationalize my machine, though.

Really, it's the ID3 tags that matter anyway, right?  So, if I were you, I'd just change the filenames to standard characters and live with it.

---

### Post by geolr on 2005-04-23
Hi there!
I experienced the same problem, eventhough I did not copy them but used a mounted Win$$ Partition (but with vfat not ntfs!). Changed my fstab by hand.
Now I saw those unknown charakters in Filenames, which made me think of mount options. So  after studying man pages I tried the additional option in fstab *utf8* like this:
/dev/hda7       /mountpoint      vfat    rw,user,utf8    0       0

Now the german Umlauts are shown at least.
Use the locale command to see if your locale is set correctly.

Obviously your files are copied already, so this does not change those...

Cheers!

---

