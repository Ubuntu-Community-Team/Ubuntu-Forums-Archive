---
title: "Truecrypt - problem with keyfile"
date: 2006-08-03
forum: Desktop Environments
---

### Post by rafalr on 2006-08-03
I encounter a problem I can not overcome. Below there is text copied from terminal:

1. first I tried to create a volume
-------------------
rafal@Ubuntu-AMD-64:~$ truecrypt -k /home/rafal/crypto/test_key --size 50M --encryption AES --hash SHA-1 -c /home/rafal/c rypto/test_vol.tc
Volume type:
 1) Normal
 2) Hidden
Select [1]: 1

Filesystem:
 1) FAT
 2) None
Select [1]: 2

Enter password for new volume '/home/rafal/crypto/test_vol.tc':
Re-enter password:

TrueCrypt will now collect random data.

Is your mouse connected directly to computer where TrueCrypt is running? [Y/n]: y

Please move the mouse randomly until the required amount of data is captured...
Mouse data captured: 100%

Done: 48.00 MB  Speed: 8.37 MB/s  Left: 0:00:00
Volume created.
---------------------
this done properly, I now tried to mount nad was asked couple of extraquestions, including one about keyfile:
-------------------------------------
rafal@Ubuntu-AMD-64:~$ truecrypt -i
Enter volume path: /home/rafal/crypto/test_vol.tc
Enter mount point [none]: /media
Protect hidden volume? [y/N]: n
Enter keyfile path [none]: /home/rafal/crypto
Enter keyfile path [finish]: --help
Enter keyfile path [finish]: ?
----------------------------------------------
I had no idea about path/name of keyfile - I suppose TC builds them by itself (no key path/file specified while building volume and TC can apparently live with that), so what I am supposed to input above ?

I gave another try to create a volume, this time TC he needs filesys to be specified while mounting the volume- what am I supposed to write if at creation I chose "none" rather then "FAT")- see below:
-------------------------------------------------------------
rafal@Ubuntu-AMD-64:~/crypto$ truecrypt -i
Enter volume path: /home/rafal/crypto/test_vol.tc
Enter mount point [none]: /mnt
Protect hidden volume? [y/N]: n
Enter keyfile path [none]:
Enter password for '/home/rafal/crypto/test_vol.tc':
mount: you must specify the filesystem type
truecrypt: Mount failed
rafal@Ubuntu-AMD-64:~/crypto$

These are apparently my mistakes: what am I supposed to do with keyfile while cresating volume and mounting it ?
What is the right entry for filesystem while mounting a volume ?

Rafal
Ubuntu Dapper

---

### Post by wieman01 on 2006-08-03
You have specified a key file in the first command:

> /home/rafal/crypto/test_key

Use this when being asked for it.

---

### Post by wieman01 on 2006-08-03
Try this command only... then your data is encrypted with your password rather than a personal key file:

> truecrypt --size 50M --encryption AES --hash SHA-1 -c /home/rafal/c rypto/test_vol.tc

Should be ok.

---

### Post by rafalr on 2006-08-03
Thanks for that - will give a try this evening.

Do I understand right that a keyfile is optional ? If while interactive creating volume you hit <enter> instead of giving path/name to keyfile then TC builds none, and the volume is encrypted directly with my passowrd ?

rafal

---

### Post by wieman01 on 2006-08-03
This way the system won't even ask you for the keyfile... :-) Try it out and let us know what the result is. However, I have tested it back home so it should be fine.

Yes, there are two ways to encrypt a volume:

1. Single password
2. Personal key-file

Option 2 is the safest way to encrypt your files because the system collects random(!) data to create the personal key and encrypt your volume. Then the system asks you for a password... Why?? Because it then encrypts your personal key so that no 3rd party can use it right away should you ever lose it or your system be compromised. This password is meant to protect your key, nothing else. :-)

Option 1 is less safe but does the job. This way you don't need to carry around your personal key and can access your files by entering a simple password (or a more complex one). Generally I would suggest to use good/long passwords if you go for this one. This is my preferred option.

---

### Post by orb9220 on 2006-08-03
Same here I use the same option 1. Don't want to have to deal with key-files.

Did a deep read at the truecrypt web site and determined if I use a double-digit password like mine is 14 characters and numbers,

And I secure that it will not be broken.

---

### Post by rafalr on 2006-08-04
Hi wieman,

The TC issue will need to wait now as I did hit much bigger problem.

Could you take a look at the thread "messed up with the system su/root" ([http://www.ubuntuforums.org/showthread.php?t=228467](http://www.ubuntuforums.org/showthread.php?t=228467)) as I am now seriuously stuck with anything including internet access ?

Any help very welcome.

rafal

---

### Post by bandoba on 2006-08-27
Hi rafalr,

I am getting same error "filesystem must be specified" even when I don't use any key file. Does anybody know what filesystem I should specify? I have chosen option 2 i.e. None when creating the volume (similar to first post).

TIA

---

### Post by wieman01 on 2006-08-28
I remember that you have to press "enter"... That's it. The system will choose the default file system (whatever that is). Have not had a problem with the default one so far.

---

### Post by rafalr on 2006-08-28
Hi,

after having resolved the bigger problem I had (su properties missing) I actually gave up TC for a moment. For the time being I simly zip and GPG the folder I keep restricted info and will wait untill the TC team or community pops up with any GUI.

I know I am kind of lazy - but actually PC is my workplace, not a game box or experimenting field...

If anyone hears about a GUI for TC - I am here to test it :-)
Rafal

---

### Post by wieman01 on 2006-08-29
Sorry to hear that TC is so much of a hassle. In fact I had similar problems all over. The missing GUI is indeed a pain although a terminal solution does not really put me off.

Let's hope for the best then.

---

### Post by rafalr on 2006-09-08
Well,

After having studied the available alternatives (dm, crypt-setup, cryptomount, losetup, encfs/fuse) I am humbly back to truecrypt.

After extensive reading it seems you have to play dumb while creating the crypted volume - at least as far as syst file.

The available options are FAT (which theoretically makes no sence with Linux) and NONE (which seems te be the only available compromise). So I aleways was choosing NONE which produced the described proble.

The reading I did proved you juts need to "enter through this question" and (stupidly) accept the default FAT. Does this mean that the fs of the encrypted volume will be reformatted into FAT (if yes, 16 or 32 bit ?), or just the existing fs (in my case reiserfs) will stay intact/unformatted ?

Want to check out before I got some bad surprise and loose data ...

rafal

---

### Post by wieman01 on 2006-09-08
No matter what file system it is, I have never had a problem with TC. I accepted the default file system and it works fine in my case. I have never lost a file so far. Give it a try and test it before you make serious use of it.

---

### Post by rafalr on 2006-09-11
Did play dumb (accepting FAT file system). Also wrote short sripts and linked them to panel icon to mount / unmount the volume.

Everything worked fine, so I already moved the data to the encrypted volume and wiped the "old" folder.

I am however still very curious what is actually happening on HDD: is the encrypted volume indeed a FAT system (the fs I used while installing Ubuntu was raiserfs) Can it be checked ?

rafal

---

### Post by wieman01 on 2006-09-11
> **rafalr said:**
> I am however still very curious what is actually happening on HDD: is the encrypted volume indeed a FAT system (the fs I used while installing Ubuntu was raiserfs) Can it be checked ?

rafal
I would not know how to check it since it would not show in any partitioning tool. However, I'll post another message when I find out since you've made me curious as well.

---

