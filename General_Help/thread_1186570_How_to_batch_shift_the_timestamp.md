---
title: "How to batch shift the timestamp?"
date: 2009-06-13
forum: General Help
---

### Post by Quaxo76 on 2009-06-13
Hello,
I have a "weird" need: I need to shift the time stamp of a set of files 7 hours in the future. I need this because I took some photos with a digital camera, which was set to the wrong time zone; and now those photos are "out of sync" with the photos taken during the same trip but with another camera. So when I sort the files from that trip "by time/date", they come out all mixed up. So I would like to find a way to shift "ahead" the time of only those photos.
I know about the command
```
touch -t YYMMDDhhmm.ss filename
```
but this changes the date to an absolute value, not relative; so I should do that by hand for each file (and there are a few hundreds of them). Is there a way to automate the process? I suspect a script that extracts the time stamp from a file, modifies it and then "injects" the result in the original file could do that... but I don't know how to make such scripts.
Can anyone help me?

Thanks in advance,
Cristian

---

### Post by tgalati4 on 2009-06-13
apt-cache search exif

This brings up a list of exif-related files that you can experiment with.  Some are libraries for other programs, others are file information manipulators.  I haven't used any of them, but it can't be more difficult than changing ID3 tags in music files.

---

### Post by Quaxo76 on 2009-06-13
Thanks, I'll look into that. But, though changing exif data would be nice, what I really need is to change the actual timestamp of the file, not the exif data... though changing exif would be an added bonus, so I'll look into it anyway!

Thank you again,
Cristian

---

### Post by stani on 2009-06-15
> **Quaxo76 said:**
> Thanks, I'll look into that. But, though changing exif data would be nice, what I really need is to change the actual timestamp of the file, not the exif data... though changing exif would be an added bonus, so I'll look into it anyway!

Thank you again,
Cristian

Maybe we'll implement this for Phatch. Subscribe here:
[https://bugs.launchpad.net/phatch/+bug/386741](https://bugs.launchpad.net/phatch/+bug/386741)

---

### Post by callan79 on 2009-06-16
> **Quaxo76 said:**
> Thanks, I'll look into that. But, though changing exif data would be nice, what I really need is to change the actual timestamp of the file, not the exif data... though changing exif would be an added bonus, so I'll look into it anyway!



Hi Cristian,

exiftran is the program you need - it can read and edit the EXIF data from your photos. I used this recently for the photos from our wedding - all our friends' cameras had different time settings, some even had the wrong year. Thankfully exiftran fixed it :)

If you just install it, and then do 'man exiftran' you can go from there.

If you need any help, just ask!

Cheers
Callan

---

### Post by Quaxo76 on 2009-06-16
Thank you. I've installed exiftran, and looked at the man page, but I can only find options to rotate the photos and such... the only options about timestamps, is a "preserve timestamps" which is not what I want to do. Maybe the version that's in the repos is old? Or there's some "hidden" feature?
Besides, does it only change the exif data or the actual timestamp too?

Thank you again,
Cristian

---

### Post by geirha on 2009-06-16
Try with
```
touch -d "+7 hours" file1 file2...
```

EDIT: Err, that'll set the timestamp to +7 hours relative to the current time, not the file's timestamp. Sorry :/

EDIT2: Ok, this seems to do the trick:
```
touch -r file1 -d "+7 hours" file1
```

---

### Post by callan79 on 2009-06-16
> **Quaxo76 said:**
> I've installed exiftran, and looked at the man page, but I can only find options to rotate the photos and such... 

Hi Cristian,

I'm sorry! The correct program is jhead.

Look in the man page for the " -ta<+|-><timediff>" switch, this should help.

Sorry for the wrong program the first time!

Callan

---

### Post by Celauran on 2009-06-16
> **geirha said:**
> 
EDIT2: Ok, this seems to do the trick:
```
touch -r file1 -d "+7 hours" file1
```

Automate it.

```
for i in *; do touch -r "$i" -d "+7 hours" "$i"; done
```

---

### Post by TaTaE on 2011-01-03
> **geirha said:**
> Try with
```
touch -d "+7 hours" file1 file2...
```

EDIT: Err, that'll set the timestamp to +7 hours relative to the current time, not the file's timestamp. Sorry :/

EDIT2: Ok, this seems to do the trick:
```
touch -r file1 -d "+7 hours" file1
```
@geirha


God bless you for this information was helpful!

---

### Post by TaTaE on 2011-01-03
> **callan79 said:**
> Hi Cristian,

I'm sorry! The correct program is jhead.

Look in the man page for the " -ta<+|-><timediff>" switch, this should help.

Sorry for the wrong program the first time!

Callan
@callan79


God bless you too my friend !

---

