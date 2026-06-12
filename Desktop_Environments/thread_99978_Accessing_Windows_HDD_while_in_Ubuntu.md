---
title: "Accessing Windows HDD while in Ubuntu"
date: 2005-12-06
forum: Desktop Environments
---

### Post by n8dagr8 on 2005-12-06
I have 2 HDDs in my computer - one running Win. XP (/dev/sda) and the other Ubuntu (/dev/sdb). 

I have a bunch of music (MP3) files on the Windows disk that I would like to be able to access while in Ubuntu. The Windows drive is formatted as NTFS. Is this possible? If so, how do I do this? Thanks,

N8

---

### Post by invalid on 2005-12-06
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514705](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514705)

---

### Post by doitashimashite on 2005-12-06
Accessing ntfs filesystems from Ubuntu is no problem. You can read your files from there, but writing is (still) an issue.

Is your ntfs filesystem currently not mounted?

---

### Post by n8dagr8 on 2005-12-06
[QUOTE=doitashimashite]Accessing ntfs filesystems from Ubuntu is no problem. You can read your files from there, but writing is (still) an issue.

Is your ntfs filesystem currently not mounted?[/QUOTE]

no, it isn't.

I have a dual-boot machine but the OSs are on different HDDs. I think it may have something to do with the HDD access mode from reading other post.

---

### Post by n8dagr8 on 2005-12-06
[QUOTE=invalid][http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514705](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514705)[/QUOTE]

doesn't help...this is what I tried before I posted my question....like I stated above, it may have something to do with the HDD access mode (auto as opposed to LBA).

Thanks for the help, though.

---

### Post by bunty on 2005-12-06
We cant guess, post more info.

I you think it is access (unlikely ) post what you/ve got so someone can comment.

What cant you do , mount it, read it, find it. Where's the prob?:cool:

---

### Post by invalid on 2005-12-06
[QUOTE=n8dagr8]doesn't help...this is what I tried before I posted my question....like I stated above, it may have something to do with the HDD access mode (auto as opposed to LBA).

Thanks for the help, though.[/QUOTE]
You are going to have to be a lot more specific as to what your problem is..

Is there a problem with mounting the drive? Is there a problem once it gets mounted? What is the exact error you are getting?

---

### Post by aysiu on 2005-12-06
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

