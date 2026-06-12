---
title: "/dev/zero abused"
date: 2009-01-21
forum: General Help
---

### Post by sandyd on 2009-01-21
Recently someone (probably one of my sons) has been making zip bombs (i saw this from the system log) using

```

dd if=/dev/zero bs=1000 count=1000000 | zip > bomb.zip

```
i know theirs a limit of 4 Gigs / zip, but is there any way of stopping this?

and no, i'm not trying to teach you how to make a zip bomb. 

Don't do it.

---

### Post by cmnorton on 2009-01-22
Not  knowing which if any system software depends on /dev/zero, proceed with caution. 

You should be able to enter

sudo chmod 700, and then only root will be able to access this file. That will only work, though if you are the only one who knows the sudo password.

---

### Post by sandyd on 2009-01-22
hmm. it does the trick as i'm the only person who knows the sudo password

all the other apps sill work.

Thanks!

---

### Post by snova on 2009-01-22
I'm not sure if that will work. Aren't device files regenerated at every boot?

If rebooting makes your changes disappear, then it may be possible to configure the udev system, which is responsible for creating devices.

In the **/etc/udev/rules.d/40-basic-permissions.rules** file, change this line:

```
KERNEL=="zero",				MODE="0666"

```

To:

```
KERNEL=="zero",				MODE="0600"
```

**HOWEVER**, I am *very* unsure of this, and it might have unintended side effects. Please be cautious, I didn't even know this file existed until I looked for a way to solve this.

Of course, this might all be moot, if the changes are applied across a reboot, then don't do it at all!

---

### Post by mssever on 2009-01-22
Note further that there could easily be programs that run as a normal user which need access to /dev/zero. If so if you get weird problems, you might have to undo those changes.

EDIT: Another potential approach would be to use disk space quotas to limit what your son can do. Then, if he exceeds his limit, he'll have to face whatever consequences you decide to impose.

---

### Post by Sorivenul on 2009-01-22
Changing the permissions on /dev/zero may be problematic, though I've done no tests myself. 

From "man 4 zero":
> DESCRIPTION
       Data written on a null or zero special file is discarded.

       Reads  from  the  null  special file always return end of file, whereas
       reads from zero always return \0 characters.

       null and zero are typically created by:

              mknod -m 666 /dev/null c 1 3
              mknod -m 666 /dev/zero c 1 5
              chown root:root /dev/null /dev/zero

FILES
       /dev/null
       /dev/zero

NOTES
       If these devices are not writable and readable for all users, many pro&#8208;
       grams will act strangely.

SEE ALSO
       chown(1), mknod(1), full(4)


During my research I read a report of an HP-UX server's capability being reduced to executing the "cd" command after /dev/zero went missing...

---

