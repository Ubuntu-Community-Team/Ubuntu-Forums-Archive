---
title: "Looking for encryption made easy."
date: 2009-01-02
forum: Desktop Environments
---

### Post by XtremeGamer99 on 2009-01-02
Hello,

I'm looking for an easy-to-use encryption mechanism (preferably in a GUI format) that allows for [on-the-fly encryption]("http://en.wikipedia.org/wiki/OTFE"). 

I've been using the default GUI encryption that comes with Ubuntu 8.10. Right click on a file -> encrypt. However, this is very tedious as it leaves the original file in an unencrypted state while having the encrypted .pgp right next to it. it's also annoying to use on a directory, as it asks if you want to zip it and encrypt the zip (which is what I usually do) or encrypt each file within with just leaves a huge mess. Zipping (or tarring or whichever you prefer) the directory creates the zip file alongside the non-encrypted directory, and then created the encrypted file alongside the two non-encrypted files that essentially hold the same data. I have to delete the two things left behind, and in order to decrypt and access the files, I have to decrypt the zip files, extract the zip file and then use the files in there, only to repeat the whole encryption process again when I'm done...

I'm sure this is a good way if your sending the files somewhere, but this is unnecessary work if you have sensitive files on your computer that you just need every now and then. Thus, I am looking for an on-the-fly solution: double click the encrypted directory, give the password, and then access the files in a normal fashion while never decrypting to the hard drive (on-the-fly means it decrypts to the RAM _only_, not to the hard drive).

I guess I'm looking for something similar to Ubuntu'u Private directory, except I don't want it mounted upon login. I'm not real sure how the Private directory works, though...

Also, I would really prefer a GUI solution. I don't mind using the terminal for the initial setup -- I'm completely comfortable with that. I just don't want to break into the terminal every time I need access to the encrypted files.

Another note: please don't suggest TrueCrypt. I've tried setting it up before and it's hell to do, plus it's clunky and third-party. I want something a little more in-line to Linux and my normal file browsing.

Thanks!

---

### Post by XtremeGamer99 on 2009-01-03
Anyone?

---

### Post by apmcd47 on 2009-01-03
> **XtremeGamer99 said:**
> Anyone?

This isn't the answer you were hoping for, but:
[LIST]
[*]Read the Manual pages on Gnu-PG
[*]Write a simple shell-script which will do what you want for a simple file[LIST]
[*]ie replace original with new file
[*]Take the filename as a program argument
[/LIST]
[*]See if you can replace the default "encrypt file" action with your shell-script
[/LIST]
If this works you can then look at either extending the script to work on directories as you wish (create an encrypted ZIP archive and remove the orginal directory) or write a separate script and then work on an action to call the appropriate script.

As far as reading encrypted files is concerned, another script which decrypts to /tmp and open them in your favourite editor is probably the way forward. If they are zip files open them in your favourite zipped-file-browser. After the editor exits your script deletes the file.

I'm sorry, I've never tried to add actions to Konqueror or the Gnome file-browser so I can't help with that part. I imagine it is as easy as opening the options menu and finding an appropriate option to change. 

Andrew

---

### Post by XtremeGamer99 on 2009-01-03
I've looked it up a bit. It seems I can use dm-crypt. However, all the how-to's and tutorials out there describe how to encrypt and mount a block device such as a hard drive or partition, not a single file. How would I be able to use a file with it?

---

### Post by XtremeGamer99 on 2009-01-03
> **apmcd47 said:**
> This isn't the answer you were hoping for, but:
[LIST]
[*]Read the Manual pages on Gnu-PG
[*]Write a simple shell-script which will do what you want for a simple file[LIST]
[*]ie replace original with new file
[*]Take the filename as a program argument
[/LIST]
[*]See if you can replace the default "encrypt file" action with your shell-script
[/LIST]
If this works you can then look at either extending the script to work on directories as you wish (create an encrypted ZIP archive and remove the orginal directory) or write a separate script and then work on an action to call the appropriate script.

As far as reading encrypted files is concerned, another script which decrypts to /tmp and open them in your favourite editor is probably the way forward. If they are zip files open them in your favourite zipped-file-browser. After the editor exits your script deletes the file.

I'm sorry, I've never tried to add actions to Konqueror or the Gnome file-browser so I can't help with that part. I imagine it is as easy as opening the options menu and finding an appropriate option to change. 

Andrew

Heh, you're right. Not really the answer I'm looking for.That's an even more out of the way method then the method i'm doing right now. =P but thank you for the input. =)

A small note -- I'm not really looking to add new features to the file manager. Just a file that I can click on, it asks for a password, and mounts the encrypted file as part of the filesystem using on the fly encryption...

---

### Post by apmcd47 on 2009-01-03
> **XtremeGamer99 said:**
> I've looked it up a bit. It seems I can use dm-crypt. However, all the how-to's and tutorials out there describe how to encrypt and mount a block device such as a hard drive or partition, not a single file. How would I be able to use a file with it?

My gut reaction is that dm-crypt is not what you need. The dm bit stands for "device mapper". I suspect this is probably the method used by the Ubuntu Private Directory, of course I'm too lazy to confirm this suspicion :D, and you have already ruled this solution out!

Andrew

---

### Post by XtremeGamer99 on 2009-01-03
> **apmcd47 said:**
> My gut reaction is that dm-crypt is not what you need. The dm bit stands for "device mapper". I suspect this is probably the method used by the Ubuntu Private Directory, of course I'm too lazy to confirm this suspicion :D, and you have already ruled this solution out!

Andrew


I have a feeling this is what I need. If I were to use an actual partition, the DM would act as a filter and all data passing to and from it would be encrypted/decrypted, if the correct password is used to mount the DM. This is the on-the-fly encryption that I'm looking for -- the decrypted data is never really stored in on the hard drive, just in the RAM. I think TrueCrypt uses the DM like this also, and while I like truecrypt I do not like Ubuntu implementation of it (hard to set up correctly, clunky interface, etc.)

I would be using the DM however it only accepts blockdevices, which a single file is not. I need a way to make a file show up as a block device so that I can use this.

Unless I'm mistaken. If so, correct me. =)

---

### Post by XtremeGamer99 on 2009-01-03
I found this:

[http://www.saout.de/tikiwiki/tiki-index.php?page=looptutorial](http://www.saout.de/tikiwiki/tiki-index.php?page=looptutorial)

Seems to be just what I needed. however, I get to this step:
```
cryptsetup -c aes -y create secret /dev/loop0 
```
and it gives me:
```
~$ sudo cryptsetup -c aes -y create secret /dev/loop0
Enter passphrase: 
Verify passphrase: 
Command failed: device-mapper: reload ioctl failed: Invalid argument
ryan@ryan-laptop:~$ cryptsetup -c aes -y create secret /dev/loop0
mlockall failed: Cannot allocate memory
WARNING!!! Possibly insecure memory. Are you root?
Command failed: Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver 

```

So i try sudo:
```
~$sudo cryptsetup -c aes -y create secret /dev/loop0
Enter passphrase: 
Verify passphrase: 
Command failed: device-mapper: reload ioctl failed: Invalid argument

```

I entered the passphrase that I wish to use, and it says command failed... Why?

EDIT: I'm in the process of reading through man pages to see what's up...

---

### Post by Rob_H on 2009-01-03
> **XtremeGamer99 said:**
> I think TrueCrypt uses the DM like this also, and while I like truecrypt I do not like Ubuntu implementation of it (hard to set up correctly, clunky interface, etc.)

I was about to suggest TrueCrypt. :-) What do you find difficult/clunky about it? I've been using it very successfully for a while now. Works great for on-the-fly encryption of folders/partitions, although I wish they would support whole-drive encryption for Linux.

---

### Post by XtremeGamer99 on 2009-01-03
I don't like the GUI, mostly. I've always had trouble installing it and getting it to work the way on want to on ubuntu...

But I never thought about using it via the command line... I'll be looking into that...

---

### Post by XtremeGamer99 on 2009-01-03
Well, I was successful in making a 500MB file and using it with dm-crypt. I created a small script that would turn it into a loop device, map it using dm-crypt, and mount it after giving a password. Works like a charm, and all i have to do is click a file to mount/unmount it.

However, I gave truecrypt another try. It's been about a year since I used it, and last time it gave me trouble installing it, the GUI never worked quite right, and it was annoying because it asked for the sudo password and only worked every once in a while. But I'm very surprised that i've had zero problems with it. So i guess I'm gonna be using TC. <_<

---

### Post by jpfle on 2009-06-04
> **XtremeGamer99 said:**
> Well, I was successful in making a 500MB file and using it with dm-crypt. I created a small script that would turn it into a loop device, map it using dm-crypt, and mount it after giving a password. Works like a charm, and all i have to do is click a file to mount/unmount it.

Hi XtremeGamer99,

I wonder if your script needs a root access for mounting loop device?

Thanks.

---

### Post by andrea000 on 2009-06-06
Hello,

Take a quick look [here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") this may be what you are looking for it will make a encrypted private directory

---

### Post by pluckypigeon on 2009-06-06
look up encfs

you just mount the folder with encfs then unmount it and it becomes encrypted

---

### Post by aptgetmoo on 2009-06-06
Truecrypt is actually quite easy to install. I think it is in the repository or you can download the *.deb file from truecrypt website. 

After installing it, if you want it to automount whenever you click a *.tc file (truecrypt volume), do this:
1-right click on any *.tc file, go to "Open With" tab
2-Then click add and inside the "Use a custom command" box, type:
```
truecrypt --background-task
```

It will then prompt for a password. If you want to dismount, just click on the truecrypt icon on the notification area, it will automatically disappear when there is no more mounted truecrypt volume.

---

