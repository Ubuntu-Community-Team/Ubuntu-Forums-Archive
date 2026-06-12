---
title: "how do i copy files over from vista"
date: 2009-05-22
forum: General Help
---

### Post by CLoss on 2009-05-22
Ok yesterday (21/5/09) i successfully installed ubuntu! yey.
But like alot of others vista wont boot up now, so i have decided to try to re-install vista but the proublem is i have software on it i want to keep but i have no install disks for, i.e dreamwever cs3, flash cs3, easygif animator, you get the picture.
And see everything is still there on my hard-drive the html, and flv files i am currently working on.
and be4 some1 says it i do have some back ups, but sadly not all.
and i still need my software as that is what i am training on in collage adobe cs3/cs4 programs.
But i obtained them off a guy i did my work experience with (so i have no cd) and now i am off collage for the summer (so cant find the guy) and havce projects that i NEED the cs3 to work on.
is there any way that i can copy over all my software into ubuntu from vista, without needing to be in vista or have the install files.
i do have the space in ubuntu for the software as i left a big partition
and if i can get this working with wine i will have no need for vista ever again.
so if any1 has any help, please help me.
cheers, Mark. ):P

---

### Post by CLoss on 2009-05-22
also incase any1 says to use the ubuntu alternitive for the summer b4 i get back to collage, as i can then get cs3 again or cs4,
is there any ubuntu photoshop, illustrator and flash
THAT CAN OPEN THE photoshop, illustrator and flash programs,
that is .png, .ai and .flv.
and in witch case all i will need is to be able to get my files off my vista hard-drive so will need help for that please.
thankyou

---

### Post by dandnsmith on 2009-05-22
Most Windows software needs to have entries in the registry/hive (created by the installation process, and sundry system files (mostly dll's) put there similarly.

Even if you copy all the files, you'll find you need to do the install process whether you're to re-install vista or to use wine.

Copying the files is a comparatively simple matter (once you've decided which they are) - you just have to get the NTFS mounted, and use *cp*

---

### Post by CLoss on 2009-05-22
i am a complete noob, so how can mount the NTFS and is cp the theminal? and thankyou for the reply.

---

### Post by chriskin on 2009-05-22
> **CLoss said:**
> i am a complete noob, so how can mount the NTFS and is cp the theminal? and thankyou for the reply.
get the storage device manager to mount it for you, you can find it in the repositories if you don't have it


and there is no real reason for cp, just browse to your folder and copy the files :) can't see why this won't work

---

### Post by chriskin on 2009-05-22
also, why reinstall vista?
what is the problem?
if you just can't find it at grub, all you have to do is add some lines in text file (/boot/grub/menu.lst to be specific)

---

### Post by CLoss on 2009-05-22
well see i searched google and tryed every command to boot it, it just says "starting..."
but never starts and when i try to boot it off cd it says i hace a mp3 player\camera attached when i dont.
and i also downloaded and burned onto a cd the booting files but that just stalls my laptop.

---

### Post by CLoss on 2009-05-22
I got it fixed thanks,
i fortunintly had 30gb unallocated so i just installed visto onto that and in doing sdo i can now access all my files on drive d (old vista) from drive c (new vista) and log back into drive d also.

---

