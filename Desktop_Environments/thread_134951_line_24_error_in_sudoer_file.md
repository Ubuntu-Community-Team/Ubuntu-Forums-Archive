---
title: "line 24 error in sudoer file"
date: 2006-02-22
forum: Desktop Environments
---

### Post by mervg on 2006-02-22
When i entered the apt-get upgrade command the response was that there was an error in line 24 in /etc/sudoer and it needed to be edited. When trying that, the sudoer won't open to edit. is there a recovery?

Whew:oops: 
Merv

---

### Post by stevea1210 on 2006-02-22
To edit the sudoers file, you need to enter
```
sudo visudo
```

after you do that, can you post the contents.

---

### Post by mervg on 2006-02-22
[QUOTE=stevea1210]To edit the sudoers file, you need to enter
```
sudo visudo
```

after you do that, can you post the contents.[/QUOTE]
Tried it, got this in return

merv:~$ sudo visudo
>>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24

---

### Post by stevea1210 on 2006-02-22
ok, try this 

```
sudo cat /etc/sudoers
```

Although that probably will fill also with the same of similar error.

If that fails, you will probably need to edit the file by booting into a live cd, mounting the / partition, and editing the file from there.

---

### Post by mervg on 2006-02-22
[QUOTE=stevea1210]ok, try this 

```
sudo cat /etc/sudoers
```

Although that probably will fill also with the same of similar error.

If that fails, you will probably need to edit the file by booting into a live cd, mounting the / partition, and editing the file from there.[/QUOTE]

Thanks, that's where i'll go.

---

### Post by mervg on 2006-02-23
[QUOTE=mervg]Thanks, that's where i'll go.[/QUOTE]

Mounting / from a live cd may work, but i haven't found how to do that.  I can get to the root of the installed ubuntu, and can see the hda2 it is on, but can't get where i can edit (vi/vim) the sudoers file. Anyone know how to do that?

---

