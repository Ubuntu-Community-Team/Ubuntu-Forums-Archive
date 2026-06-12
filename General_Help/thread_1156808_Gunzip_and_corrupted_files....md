---
title: "Gunzip and corrupted files..."
date: 2009-05-12
forum: General Help
---

### Post by StrangeWill on 2009-05-12
So I split a tar.gz file using *split* into 5GB files. Broke them up onto 4 different hard drives so I could build my drive array. Moved them back and combined them with *cat* now I get errors when trying to extract the files....

When I run this command:
gunzip -c storage.tar.gz | tar -xvf -  

I get a list of files (about 1% of the overall data stored) and then get this:
> tar: Skipping to next header

gzip: storage.tar.gz: invalid compressed data--format violated
tar: Error exit delayed from previous errors

Mind you, this is 200GB of data that I'd ***REALLY*** like to not rebuild from scratch, are there any tools I can use to recover the data?


Also I need an application that can deal with files this large, PowerArch wants to extract it before telling me if it can recover it, ugh.


Edit:
Trying gzip recovery. BRB.

---

### Post by StrangeWill on 2009-05-12
Bump, no go.

There is 191GB of data in this file, I have to be able to get to it SOMEHOW.

These were transferred over Samba, so there shouldn't be the FTP ASCII issue.

---

### Post by StrangeWill on 2009-05-12
Okay I figure I need GZip to plow through errors, and same with tar, I have no clue how to do this, I don't care about the corrupted data, I obviously just want the data after it.

---

### Post by StrangeWill on 2009-05-12
Is there any chance that if I take this to a hard drive recovery place they can get my files? I just realized I got work data in this file, ugh!

---

### Post by StrangeWill on 2009-05-12
This is extremely important, am I asking in the wrong place?

---

### Post by StrangeWill on 2009-05-12
Problem #1 is that CPIO does NOT support long filenames, so it isn't dumping files correctly and creating @LongFiles which are a pain to delete from Samba.

Problem #2 Tar does not support recovering files like CPIO does... ugh. A header problem causes tar to fail.

Possible Problem #3 GZip Recovery doesn't seem to be un gzing files all the way, I think I got 5gb in again and it failed, maybe it ran into a weird issue, I couldn't tell being as I ran it overnight along with the CPIO command afterward so I didn't get to see any output.

SO I need a replacement for CPIO that isn't tar. Any ideas?

---

### Post by StrangeWill on 2009-05-12
IT seems to be breaking at the 5gb mark (after that gzrecovery just errors at almost every bit, recovering a few bytes here and there), the exact mark where files were split/cat ugh.

I've done this manually too...

cat storagebitaa > storage.tar.gz
cat storagebitab >> storage.tar.gz

or:

cat storagebit* > storage.tar.gz

Still no go. :(

Am I accidentally appending stuff onto these files?

---

### Post by geirha on 2009-05-12
Let's just see if I got this right.

You made the tar.gz with "tar zcf storage.tar.gz /file/paths", and split it with "split -b 5G storage.tar.gz" ?

Then when you wanted to put the file back to gether you copied the pieces via samba to an ext2/3 filesystem, and you're trying to concatenate them on that same filesystem?

And further, does all but the last file have the same size, 5368709120 bytes?

EDIT:
The files should be in alphabetical order, and bash will expand the pattern alphabetically if you do ```
cat storage* >storage.tar.gz
``` However, in some locales they may get sorted differently. For instance, in a norwegian locale, aa is treated as the character å, which is the last character in the norwegian alphabet, so it will be the last file instead of the first in the list. 

To ensure that locale is not having any impact on this, run it in a shell with locale specifically disabled.
```
LANG= bash -c 'cat storage* >storage.tar.gz'
```

---

### Post by StrangeWill on 2009-05-12
> **geirha said:**
> Let's just see if I got this right.

You made the tar.gz with "tar zcf storage.tar.gz /file/paths", and split it with "split -b 5G storage.tar.gz" ?
Correct, except with "split -b 5000mb" I didn't think it supported G, so it isn't exactly 5GB.

> **geirha said:**
> Then when you wanted to put the file back to gether you copied the pieces via samba to an ext2/3 filesystem, and you're trying to concatenate them on that same filesystem?
Yes, I stored them on an array of systems, including ext3/NTFS (XP + Vista) systems over Samba, I copied them back to an ext3 RAID drive and am concatenating them onto the same drive.

> **geirha said:**
> And further, does all but the last file have the same size, 5368709120 bytes?
Yep.  (though they're 5,120,000kb)

> **geirha said:**
> EDIT:
The files should be in alphabetical order, and bash will expand the pattern alphabetically if you do ```
cat storage* >storage.tar.gz
``` However, in some locales they may get sorted differently. For instance, in a norwegian locale, aa is treated as the character å, which is the last character in the norwegian alphabet, so it will be the last file instead of the first in the list. 

To ensure that locale is not having any impact on this, run it in a shell with locale specifically disabled.
```
LANG= bash -c 'cat storage* >storage.tar.gz'
```

Yeah I'm in the US so I don't think that is the problem. :(

I stored storagebitaa-storagebitau on one drive, so I can't see a drive problem especially because it's failing after ~5gb.

YOur cat doesn't have a space in it, could that cause it?

```

cat storage* >storage.tar.gz
vs.
cat storage* > storage.tar.gz

```

I'm swinging at anything to try to get these files back. :(


Edit:
I did use -9 with gzip when I created the file, if that means anything to you.

---

### Post by geirha on 2009-05-12
> **StrangeWill said:**
> 
YOur cat doesn't have a space in it, could that cause it?


No, the space is optional and has no significance.

If you cat only the first two files, does it still complain around 5GB? 
```
cat storagebitaa storagebitab >storage.tar.gz
```

---

### Post by renkinjutsu on 2009-05-12
i have almost the same problem ... but mine is with a simple tar file with no compression...

i stored my /home directory in a tar archive that is 107 GB in size onto an NTFS drive.. when i tried restoring my linux partition, after the extraction, my entire /home directory was only 9.5GB ... so i too have a massive amount of data missing... what DID extract were a bunch of empty directories and subdirectories .. =[

---

### Post by StrangeWill on 2009-05-12
> **geirha said:**
> No, the space is optional and has no significance.

If you cat only the first two files, does it still complain around 5GB? 
```
cat storagebitaa storagebitab >storage.tar.gz
```

Okay so I did the big "thing you're not suppose to do while troubleshooting" and introduced two variables at once:

First, I'm NOW doing this as root, yes yes, big no no... but...


Whoa, I got past the .sql file that tar was corrupting on, it hasn't extracted more than 5 GB yet (in the process) but tar would error out at the .sql file before a DVD file, now it's processing the DVD file.

I guess keep concatenating files onto the .tar.gz and keep extracting? It may take awhile but it will show me where the error is or if the error was a permissions one.

Now it looks like I'm getting an error on a .VOB file.

I haven't tried gzip recovery, mostly because the software used to unarchive the files wont work anyway.

---

### Post by StrangeWill on 2009-05-12
And running "cat storagebitac >storage.tar.gz" has made it pass the .vob file it failed on.

Also I realized, my user account cannot access the .vob files, obviously it seems to be a permission thing (that seems to have been stored in the .tar.gz).

I feel horribly embarassed if this is what it turns out to be.

---

### Post by renkinjutsu on 2009-05-12
so? .. can anyone help with the restoration of my data?
why is it that my archive is 107GB and only extracts a bunch of directories and a few files? i've also tried to untar it under root, no luck.

this is.. horrible =[ someone please help me D;

---

### Post by geirha on 2009-05-13
StrangeWill, it sounds like they really did get concatenated in the wrong order earlier then. Does ```
echo storage*
``` list the files in correct order?

When you archive as the root user, it will preserve ownership and permissions on the files (not by username, but by user id, which may differ on different system). That'll not be a big problem though. Run nautilus as root with "gksudo nautilus", and you can change the permissions and ownership to give yourself access. Alternatively, you can use the chmod and chown commands in the terminal. You must be very careful about using those however. You can easily change the ownership of many more files than you intended, which could in break the system.

It's common to do backup and restore as the root user btw. 


renkinjutsu, did you get any error messages during extraction? If so, what were they?

---

