---
title: "permission denied"
date: 2005-07-21
forum: Desktop Environments
---

### Post by RadixLecti on 2005-07-21
Hi,

I have a file, part of a rar archive, that won't allow itself to be removed. 

I've tried:

rm file.r70
rm -f file.r70

both as user and sudo (and via root term)

ls -al   shows every other file in the folder, except r.70.

I've tried to change permissions

chown user file.r70,

and on the folder:

chown -R user folder name

Every time, i get 

cannot access folder name/file.r70: permission denied.

Being very new to Linux, I'm at the end of my rope here. Is there SOMETHING I can do?

---

### Post by musicman2059 on 2005-07-21
A single entry under ls -al kinda looks like this:

-rwxrwxrwx owner groupowner size filename.

If you're username isn't listed under owner, then that would be the reason.  Of course, since you can't see it, it's kinda hard to figure it out.

However, since you're using a normal user account, the command:

```
chown -R user folder name
```

Should be:

```
**sudo** chown -R user folder name
```

Then just enter your password when prompted.

---

### Post by RadixLecti on 2005-07-21
[QUOTE=musicman2059]A single entry under ls -al kinda looks like this:

-rwxrwxrwx owner groupowner size filename.

If you're username isn't listed under owner, then that would be the reason.  Of course, since you can't see it, it's kinda hard to figure it out.

However, since you're using a normal user account, the command:

```
chown -R user folder name
```

Should be:

```
**sudo** chown -R user folder name
```

Then just enter your password when prompted.[/QUOTE]



Ok, my bad. ;)

I should have said that I've tried all of the above both as root and as user. And as user, with and without the sudo command.

Boy, I must me mushy in the brain:

ls -al as root shows me file.r70, but... 

```
ls -al
ls: file.r70: Permission denied
total 1
```

As it might be of consequence, I moved this folder from /home/ to another partition. All files worked like a charm before the move.
Is there a program I can use to scan for broken files and remove/fix them?

---

### Post by cwaldbieser on 2005-07-21
Try:

```
$ sudo chmod ugo+w filename
```

You may need to just give the file write permissions before you can delete it.

---

### Post by RadixLecti on 2005-07-22
[QUOTE=cwaldbieser]Try:

```
$ sudo chmod ugo+w filename
```

You may need to just give the file write permissions before you can delete it.[/QUOTE]
 Thanks for the tips, everyone.

I opted for the reinstall though, as my comp froze up as soon as I ventured into the partition where the offending file was located. I just rescued what I could and formatted it.
I will keep cwaldbiesers tip in mind though, if it happens again.

---

