---
title: "dvd burning problems"
date: 2005-10-26
forum: Desktop Environments
---

### Post by mrt on 2005-10-26
I've got a [sony dvd dual layer burner.]("http://www.supermediastore.com/sony-dwq-30a-16x-dual-layer-dvd-rw-burner-black.html")

nautilus will not burn to it however, it keeps asking me to insert media with enough space on it.  First I tried buring 5GB of data, then I tried 1GB, it still said there was not enough space on my media.  The media is DVD+R DL (dual layer), and should be able to accomodate 8.5GB.  

Then I tried burning 80MB to a cdr, and it worked.

Is there anything I can do?

---

### Post by jeffreyvergara.NET on 2005-10-26
i guess Ubuntu or the Burning software you used does not support dual layer, I also have a dvd dual layer but I havnt used a dl DVD yet. Regular DVDs worked fine, im using k3b btw.

---

### Post by mrt on 2005-10-27
surely someone here should be able to say if nautilus supports dual layer burning....anyone?

---

### Post by Joeb on 2005-10-27
[QUOTE=mrt]I've got a [sony dvd dual layer burner.]("http://www.supermediastore.com/sony-dwq-30a-16x-dual-layer-dvd-rw-burner-black.html")

nautilus will not burn to it however, it keeps asking me to insert media with enough space on it.  First I tried buring 5GB of data, then I tried 1GB, it still said there was not enough space on my media.  The media is DVD+R DL (dual layer), and should be able to accomodate 8.5GB.  

Then I tried burning 80MB to a cdr, and it worked.

Is there anything I can do?[/QUOTE]

I had a similar problem with one of the beta versions, but it was with burning CD-RWs with Nautilus (although it has been resolved).  If I recall, it was a problem with something in the kernel.  I don't know if your problem is related or not as my burning is working fine with the released version of Ubuntu 5.10.

You might try installing K3B and see if it works.  If so, that would indicate that it is a gnome/nautilus problem and not the kernel.  Or, if you don't want to have the KDE libs installed with K3B, try graveman (although I expect you will have similar results).

---

### Post by mrt on 2005-10-27
K3B recognized that it was a dual layer burner, but was not able to write to it (input/output error).  How can I tell if the kernel is setup properly?

---

### Post by Joeb on 2005-10-28
[QUOTE=mrt]K3B recognized that it was a dual layer burner, but was not able to write to it (input/output error).  How can I tell if the kernel is setup properly?[/QUOTE]

I don't recall the specifics about the kernel.  But I just burnt a DVD (not dual layer) so the stock Ubuntu kernel seems ok.  If I recall, the work around was to tell it to burn one track at a time instead of disk at once.  Also, I believe I had to first insert the blank media and when nautilus popped up, I had to manually close it.  Otherwise K3B couldn't open it.

Is it possible that you are using the same DVD that you tried to burn with earlier.  If so, and a little bit of data was written to it, it might be unusable now.  You might try opening a terminal window and running k3b from there (sudo k3b).  That way, you'll get more descriptive error messages.

---

### Post by kanem on 2005-10-29
I also recently tried and failed to burn a dual layer dvd with the Nautilus burner. It does single layer fine for me, but for the dual layer it somehow would not realize that the dvd was big enough for what I was trying to burn. 

But it seems to be a problem with the Nautilus burner and not the backend. I was able to succesfully burn the ~7.5GB on the dual later at the command line:

growisofs -dvd-compat -speed=1 -Z /dev/hdc=image.iso
if burning an iso image or:
growisofs -dvd-compat -speed=1 -Z /dev/hdc /path/to/files
if burning individual files.

I used speed=1 'cause I was paranoid about making a coaster. Them dual layers ain't cheap. And, of course, replace hdc with whatever device your burner is.

---

### Post by mrt on 2005-10-30
```
root@linus:/home/mike# growisofs -dvd-compat -speed=1 -Z /dev/hdc=pics_mp3.iso
Executing 'builtin_dd if=pics_mp3.iso of=/dev/hdc obs=32k seek=0'
/dev/hdc: splitting layers at 1308128 blocks
:-( unable to SEND DVD+R DOUBLE LAYER RECORDING INFORMATION: Input/output error
root@linus:/home/mike#
```
does this shed any light on the situation?

---

### Post by jvictor on 2005-10-31
Tried Graveman ? works perfectly for me

---

### Post by frenkel on 2005-10-31
[QUOTE=jvictor]Tried Graveman ? works perfectly for me[/QUOTE]
Won't help because that uses the growisofs backend also.

Do you have any problems reading DVD's with the device? And are cables and stuff well connected?

---

### Post by cbestsf on 2007-03-31
I too had most of the problems mentioned above, including the error message:

 unable to SEND DVD+R DOUBLE LAYER RECORDING INFORMATION: Input/output error

I  flashed the firmware on my Liteon SOHW-1093s DVD burner and that fixed the problem.

I have had that burner a year or so and the new firmware was dated March 22 2006 so mine must have been older.

What a relief.

Crawford Best

---

### Post by jackdaw on 2007-05-14
could it be an issue with file size? i have been trying to do backups to an iomega rev drive (which uses udf file system) using tar, but it pukes at ~1gb file size. iirc, it's an issue with the kernel and udf file sizes. i now have a lite-on dvd+r dl drive (which i believe also uses udf, but i could be wrong), can burn 5gb files in that other os, but not ubuntu. also, i cannot mount the dvd drive when there's a dvd dl with a large (~5gb) file on it.  i have read where others have burned numerous smaller files to dual-layer dvd drives, but i haven't tried that yet.

hth,

cliff

---

