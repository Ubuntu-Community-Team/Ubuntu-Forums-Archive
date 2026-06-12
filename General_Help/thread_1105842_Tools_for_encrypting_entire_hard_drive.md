---
title: "Tools for encrypting entire hard drive?"
date: 2009-03-25
forum: General Help
---

### Post by cybergenesis on 2009-03-25
Hi I am a former windows user. Security is very important to me, I am involved in certain legal matters and I am somewhat paranoid.

On Windows I used truecrypt to encrypt my entire hard drive from boot up. Is there any simular tool on ubuntu? I would also like to be able to create something simular to truecrypt's "virtual volumes" inside ubuntu that is mount an encypted file as a volume, for added security.

One other question. On Windows when you delete files it merely removes the file reference from the file system but the files can be easily retrieved. Do any utilities exist on ubuntu that will wipe over "free" hard drive space or hard wipe deleted files?

If possible please refer me to GUI driven programs, not command line driven programs.

---

### Post by dcstar on 2009-03-25
> **cybergenesis said:**
> Hi I am a former windows user. Security is very important to me, I am involved in certain legal matters and I am somewhat paranoid.

On Windows I used truecrypt to encrypt my entire hard drive from boot up. Is there any simular tool on ubuntu? I would also like to be able to create something simular to truecrypt's "virtual volumes" inside ubuntu that is mount an encypted file as a volume, for added security.

One other question. On Windows when you delete files it merely removes the file reference from the file system but the files can be easily retrieved. Do any utilities exist on ubuntu that will wipe over "free" hard drive space or hard wipe deleted files?

If possible please refer me to GUI driven programs, not command line driven programs.

Do a forum search as these sort of questions have been covered previously.

---

### Post by aurelieng on 2009-03-25
So far, the pre-boot authentication you use with truecrypt is not compatible with linux. However, there are plenty of possibilities to encrypt your disks. For instance, the whole disk except the /boot partition can be encrypted very easily during install [1] or even afterwards [2]. You can also use Truecrypt on linux to create virtual volumes.

Also, to remove a file, you can "shred" it (man shred).

Cheers,

Aurélien.


[1] [http://howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system](http://howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system)
[2] [http://ubuntuforums.org/showthread.php?t=420182&highlight=feisty+luks](http://ubuntuforums.org/showthread.php?t=420182&highlight=feisty+luks)

---

### Post by cybergenesis on 2009-03-25
Thanks for the help. And yes for the above post, yep I am naughty when it comes to using the search function, I shall try and amend my ways :)

---

### Post by anaconda on 2009-03-25
I prefer to use truecrypt, but I dont use it for the WHOLE disk. I just use it for my "sensitive" data

I have a 2GB truecrypt file. which contains all I want to encrypt.

Why do you want to encrypt everything? Won't it make the whole system slower? And what is the use of encrypting eg. root folder? there isnt anything "secret" in there.

Just my opinion...

And btw. Having a movie-file, that wont work.. (which is in reality a truecrypt volume) is safer than encrypting everything. Because You WILL have to give your encrypt password to for example police if they want it. (atleast in my country)

But if you just have a moviefile that wont work.. eg. in torrent download directory. who would guess it is a truecrypt volume, and not a partially downloaded movie.  And who would demand its password. 

And no I dont have anything i would NEED to hide from police, but.. private data is private.

---

### Post by anaconda on 2009-03-25
Oh. and the same thing with USB-stiks. WHy would anyone want to encrypt the WHOLE usb-stick. (which seems to be a spreading trend nowadays)

I think it is better to have a truecrypt file on the stick

so that when you give that nonsensitive document or program from your USB-stick to your friend you dont need to "unlock" the USB -stick on your friends unsafe machine.. or on a unsafe net-cafe...

---

### Post by cybergenesis on 2009-03-25
Good points anaconda, thanks

---

### Post by RansomStark on 2009-03-25
> **aurelieng said:**
> Also, to remove a file, you can "shred" it (man shred).

Important to note Shred is not a secure delete method.

CAUTION:  Note  that  shred relies on a very important assumption: that the file system overwrites data in place.  This is the traditional  way to  do  things, but many modern file system designs do not satisfy this assumption.  The following are examples of file systems on which  shred is not effective, or is not guaranteed to be effective in all file sys-tem modes:

* log-structured or journaled file systems, such as those supplied with
AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

Use Secure Delete instead

[http://packages.ubuntu.com/search?keywords=secure-delete](http://packages.ubuntu.com/search?keywords=secure-delete)

---

### Post by RansomStark on 2009-03-25
> **anaconda said:**
> 
Why do you want to encrypt everything? Won't it make the whole system slower? And what is the use of encrypting eg. root folder? there isnt anything "secret" in there.

I have a complete LUKS encrypted drive (which is also RAID1 to compensate for any speed issues), as well as commercially sensitive data in my home folder, there is the matter of saved passwords, cache history and all the related items used when using Firefox to access the internet. Plus of course, other programs store data outside of this that if you computer was stolen you wouldn't want people being able to access.. It is also very handy to be able to enter the LUKS password on boot and then be able to access all of your encrypted files on the fly without having to open encrypted files/drives.

I do also use truecrypt drives, as it allows me to create a backup of my files and still keep everything secure.

---

### Post by kuja on 2009-03-25
> **anaconda said:**
> I prefer to use truecrypt, but I dont use it for the WHOLE disk. I just use it for my "sensitive" data

I have a 2GB truecrypt file. which contains all I want to encrypt.

Why do you want to encrypt everything? Won't it make the whole system slower? And what is the use of encrypting eg. root folder? there isnt anything "secret" in there.

Just my opinion...

And btw. Having a movie-file, that wont work.. (which is in reality a truecrypt volume) is safer than encrypting everything. Because You WILL have to give your encrypt password to for example police if they want it. (atleast in my country)

But if you just have a moviefile that wont work.. eg. in torrent download directory. who would guess it is a truecrypt volume, and not a partially downloaded movie.  And who would demand its password. 

And no I dont have anything i would NEED to hide from police, but.. private data is private.

Well, the idea is something like this: somebody else could replace all sorts of naughty things if they wanted to if they're not encrypted. For example giving you nice presents like say maybe a keylogger to get your encryption password :) Of course, no system is completely secure, not even a fully encrypted one, but every little bit helps right? Just a matter of how much convenience you're willing to sacrifice for how much of a margin of security.

---

### Post by aurelieng on 2009-03-26
If the password-based authentication (what you know) is not secure enough for you, you can use it in combination with keyfile-based authentication (what you physically have).

If you put your keyfile (or even /boot) on a write protected USB key that is not stored with your computer, it is very unlikely that someone could put a keylogger on your machine, even with a physical access to it.

See [here]("http://petaramesh.org/post/2007/11/29/Une-cle-de-contact-pour-votre-portable-chiffre") for more informations (in french, but english summary at the end).

---

