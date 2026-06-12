---
title: "Mount as image"
date: 2006-01-03
forum: General Help
---

### Post by thessem on 2006-01-03
Is there any way possible i can mount a folder or a hardrive as a .img file?

I want this, because the windows emulator I am using only really supports .img files, and you set these files to be hard drives or cdrom drives, and I need to mount a samba shared file on another computer as a hard drive.

Thanks

(btw) im using Qemu, so if you use that and find a way to do what I'm trying to do, please tell mah.

---

### Post by dickohead on 2006-01-03
You mean you're after something like daemon tools?

---

### Post by thessem on 2006-01-03
No, exactly the opposite, I want to mount a hard drive or a directory as a .img file, not a .img as a hard drive or directory

I know this is possible because I have seen it done before.

---

### Post by Deaf_Head on 2006-01-04
i'm confused about what you need because i'm not sure what your doing with it .. 

like .. 

do you mean like mounting your windows partition so you can see it than unmounting it when your done?

---

### Post by limit223 on 2006-01-04
Did you mean to make an image .img file from  from a folder?

 mkisofs -R /my/directory/path > myimage.img

Don't expect this file to be bootable..for that just study more options in mkisofs    command line.

---

### Post by thessem on 2006-01-04
limit223: Thanks, thats nearly exactly what I wanted.

The only way that could be better, though, is if i changed the directory, that change would be reflected in the image file, but Im starting to think thats impossible.

Meh, Ill just use mkisofs for now, thanks.

---

