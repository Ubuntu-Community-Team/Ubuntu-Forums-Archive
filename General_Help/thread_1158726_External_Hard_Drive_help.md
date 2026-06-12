---
title: "External Hard Drive help"
date: 2009-05-14
forum: General Help
---

### Post by Sentience on 2009-05-14
I need some suggestions for a good portable hard drive that I can use to swap files back and forth from Windows to Ubuntu and back to Windows.

Will this Western Digital work?

[http://www.costco.com/Browse/Product.aspx?Prodid=11318289&whse=BC&topnav=&browse=&lang=en-US&s=1](http://www.costco.com/Browse/Product.aspx?Prodid=11318289&whse=BC&topnav=&browse=&lang=en-US&s=1)


I guess they use the FAT format. Is that also compatible with windows?

---

### Post by Crafty Kisses on 2009-05-14
Not sure if that will work, but I bought a Maxtor OneTouch 4 Mini and that works perfectly, it's formatted as NTFS and it's easy to go between the two. (Windows, Linux.) Here's the link: [http://www.maxtor.com/en/hard-drive-backup/external-drives/maxtor-onetouch-4-mini.html](http://www.maxtor.com/en/hard-drive-backup/external-drives/maxtor-onetouch-4-mini.html). I honestly don't see why the original HD you posted wouldn't work with Linux though.

---

### Post by Sentience on 2009-05-14
I thought NTFS was not compatible with Linux and you had to use the FAT format.

I heard the NTFS is a better format and you can send files larger than 4gbs with it, but that the FAT one was compatible with more types of systems.

---

### Post by ebanlague on 2009-05-14
My friend has that exact model. 

Just make sure it is formatted NTFS, and that you make Ubuntu capable of writing to NTFS drives, by default it can't. If you do that it will definitely work.

---

### Post by Sentience on 2009-05-14
Awesome. Thank you.


While we are talking about it, how do I do that? Ive been using Ubuntu for a few years, but I use it like most people use windows. I just use the front end stuff and not the command line. Im not a computer guru, just prefer supporting the open source community and dont like the data mining and crap that is supposedly built into windows.

---

### Post by Sentience on 2009-05-14
I also have a second slightly OT question.

I have another 160gb portable HD, which I will give to my girlfriend, but I think I ruined it. I unplugged it will it was downloading some larger files and now it will not only not be recognized by either windows or Ubuntu but even the reformatting program wont detect it to start over from scratch. Is there a way to save the old one without sending it in for a replacement? Customer support was no help at all.

But either way, thanks for the help.

---

### Post by Crafty Kisses on 2009-05-14
Plug the external drive in on your Linux box and running the following command:
```
sudo fdisk -l
```
See if it's recognized on the list.

---

### Post by ebanlague on 2009-05-14
Well, first use this to install

```
sudo apt-get install ntfs-config
```Then run it using

```
gksu ntfs-config
```

And enable it. It should all work now :D

---

### Post by Sentience on 2009-05-14
ok.
I did all that, so it should be ready for the new HD when it gets here, but its still not detecting the old one. It looks like I might have corrupted it beyond the point where the formatting tools can salvage it. I will probably have to return the old one.

---

### Post by ebanlague on 2009-05-14
Well, sorry that I can't help you with your dying drive, but it sounds like it has most likely bit it.

Well, best of luck with your new drive ):P

---

