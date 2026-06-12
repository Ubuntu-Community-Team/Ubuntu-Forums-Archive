---
title: "Backup/clone DVDs"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Ferio on 2005-10-14
Hello, I wanted to backup some DVDs I own (in fact, the whole Twin Peaks series, that you can't buy in my country anymore because is out of stock and seems to be forever) and I was wondering which would be the easiest way, since I haven't cloned a DVD before. Could anyone help me, please?

---

### Post by manicka on 2005-10-14
The easiest way to clone/backup a dvd is to use dvdbackup

It's a command line program but does a great job

running this command will backup the entire disc to your hard drive
```

dvdbackup -i /dev/dvd -o /home/*yourusername*/ -M
```

You'll also need to install libdvdcss2 to make it work properly. You can get it here

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb)

---

### Post by Ferio on 2005-10-14
And if I wanted to copy it to a blank DVD, could I do it directly? I read something about it saying that it was not so easy, but I couldn't say where or when...

---

### Post by manicka on 2005-10-14
[QUOTE=Ferio]And if I wanted to copy it to a blank DVD, could I do it directly? I read something about it saying that it was not so easy, but I couldn't say where or when...[/QUOTE]

If your burner and disc are dual layered, yes, you can burn a dvd from the backed up files with k3b

... if not and you want to reduce it to single layer then your problem is more complex and you need another solution like using dvdshrink under wine or one of the native Linux apps that will do this for you..

---

### Post by Ferio on 2005-10-15
OK, I think I'll give GnomeBaker or Graveman a try before using K3B, though I think I'll finally come back to it sooner or later. Thank you very much!

---

### Post by manicka on 2005-10-15
I don't think that gnomebaker will burn a video dvd, hence I keep going back to k3b myself. It's a brilliant program and it doesn't take too much kde code to make it useful.

---

### Post by Ferio on 2005-10-15
Then you've saved me some time, I'll use K3B definitely. I wanted to try a GNOME alternative, but it's true that its burning software is ages away from K3B yet; in fact, last time I used GnomeBaker or Graveman they freezed! Thank you again!

---

### Post by Ferio on 2005-10-16
I've just managed to clone a DVD, after crashing three blank ones because I didn't know ho to do it properly with K3B, but I'll never forget it yet. Thank you very much!

---

### Post by JEDIDIAH on 2005-10-18
[QUOTE=manicka]If your burner and disc are dual layered, yes, you can burn a dvd from the backed up files with k3b

... if not and you want to reduce it to single layer then your problem is more complex and you need another solution like using dvdshrink under wine or one of the native Linux apps that will do this for you..[/QUOTE]

Who here has actually used dual layer burners under Ubuntu? Which ones have people here used sucessfully?

I have tried to use a cheap DL burner from Frys with Debian Sarge with no luck and was wondering if Ubuntu would do any better.

---

### Post by manicka on 2005-10-18
I have a lite-on that is working well, but I haven't burnt any dual layer discs yet (to expensive just yet). Everything else is working just fine.

---

### Post by SickTwist on 2005-10-18
[QUOTE=Ferio]Hello, I wanted to backup some DVDs I own (in fact, the whole Twin Peaks series, that you can't buy in my country anymore because is out of stock and seems to be forever) and I was wondering which would be the easiest way, since I haven't cloned a DVD before. Could anyone help me, please?[/QUOTE]

You may want to check out [Thoggen]("http://thoggen.net/"). It's a DVD backup program based on GTK+ and gstreamer so it will blend in nicely with GNOME. Be forewarned that ripping and encoded is *very slow* at this point--the program has not been optimised yet.

---

### Post by BLTicklemonster on 2005-10-18
Trying to use dvd::rip, I get this error:

```
An internal exception was thrown!
The error message was:

mkdir /CHANGE_ME: Permission denied at /usr/share/perl5/Video/DVDRip/Project.pm line261
```

Do I need to toss a chown -R burger on teh DVDRip folder or something?


If my daughter touches this Barbie in Swan Lake dvd one more time, I'm afraid it will be useless.

---

### Post by Ferio on 2005-10-22
Well, but I've got some new problems, it seems they're having some problems with mkisofs, and I only could clone that DVD, but not anyone anymore :S

---

