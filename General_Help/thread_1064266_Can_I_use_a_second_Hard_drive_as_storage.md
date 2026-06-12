---
title: "Can I use a second Hard drive as storage?"
date: 2009-02-08
forum: General Help
---

### Post by jono2009 on 2009-02-08
Hi there,

Having to Hard drives, one loaded with Ubuntu can I use a second Hard drive without any operating system as storage, for like movies, music etc?

Thanks for helping me.

---

### Post by ugm6hr on 2009-02-08
Yes.

---

### Post by cyfur01 on 2009-02-08
To elongate the above "Yes", you can mount the storage drive anywhere in your file system. Using this approach, I have my operating system files on a separate partition from my home folder so that when I reinstall Ubuntu, all my personal settings and documents are still retained.

You can add the drive to the "/etc/fstab" file (although messing up this file can mess up your Ubuntu installation... take heed), or if you prefer, while installing Ubuntu, manually edit the partition configuration and then you can select where to mount your second drive.

---

### Post by 2hot6ft2 on 2009-02-08
Certainly. I use 1 for my OS's and the others for storage. If windows is going to accessing the files on the drive as well you may want to format it to NTFS and use ntfs-config to auto mount it with read write privileges in ubuntu. That way you wont have to edit the fstab by hand.

If there's not going to be any windows needing to access it ext3 would work fine.

---

### Post by BoDwayne on 2009-02-08
Okay, a little more help here, please.  I have a second hard drive, formatted as ext3, for storage.  After every boot, I have to re-mount it, using

sudo mount /dev/sdb1 /media/drive2

Isn't there a way to have this automount each time?  It seems like I once saw a command you can do in the terminal to make a drive automount - without having to go in and edit the fstab file.

---

### Post by ugm6hr on 2009-02-09
> **BoDwayne said:**
> Isn't there a way to have this automount each time?  It seems like I once saw a command you can do in the terminal to make a drive automount - without having to go in and edit the fstab file.

fstab editing: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

You can do this without technically editing fstab, using tee, but it amounts to the same result (an extra line in fstab).

---

### Post by binbash on 2009-02-09
yes you can

---

### Post by BoDwayne on 2009-02-11
Thank you ugm6hr. I followed the steps in the link you gave me to and it worked great - not as scary as I expected.  A couple of questions though, just because I like to learn:

sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage

I know chown means "change owner".  I assume -R means "recursive"?  Is that so?  Does lowercase -r and Cap -r work the same?
What does "chmod" mean?
What does the "755" do?

Thanks so much for your help.

Oh, yes . . . I've read that you should provide "thanks" for helpful posts.  How do I do that?

---

### Post by cyfur01 on 2009-02-12
First, if you have questions about what a command does, try typing "man chmod" (for exmaple) into a terminal. man will display the manual for chmod, which describes what it does, and the various options for it. Not all commands have manuals, but most common ones do.

> I know chown means "change owner". I assume -R means "recursive"? Is that so? Does lowercase -r and Cap -r work the same?
-R does stand for recursive, so the change will be applied recursively to the whole of the /storage folder. However, -r does not exist for chown.

> What does "chmod" mean?
"Change file mode bits". In more understandable words, this changes read/write/execute permissions for files.

> What does the "755" do?
[This pdf book]("http://www.ubuntupocketguide.com/download2.html") has a good explination on file permissions (pg 78, pdf page 96).
[This site]("http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation") also offers a decent description of file permissions.

> Oh, yes . . . I've read that you should provide "thanks" for helpful posts. How do I do that?
As far as I can see, that's now been removed, though I don't know why... never pay much attention to such things. However, it is good to mark posts as SOLVED when you do solve your problems.

---

### Post by geirha on 2009-02-12
Most terminal commands has a manual page installed. If you wonder what a particular command does, read it's man-page.
```
man chown
man chmod
```

The manual page will open in a pager called less. Hit 'q' to quit and 'h' to get help on keyboard shortcuts. Some keyboard shortcuts have a ^ in front, for instance ^L which repaints the screen. The ^ means use ctrl as modifier, so ^L means hit Ctrl+L.

---

### Post by jono2009 on 2009-02-14
ugm6hr, cyfur01, 2hot6ft2, binbash, geirha.

Thankyou all for your replies to my post, you have answered my question. 

As a noob to posting I unable to find this post. Now I know to search under my username.:P 

Cheers.

---

### Post by ugm6hr on 2009-02-14
> **jono2009 said:**
> As a noob to posting I unable to find this post. Now I know to search under my username.:P 

There is also an option to automatically subscribe to threads you post in.

That way, you can find it in your "User CP" and will know when you've had replies.

---

### Post by jono2009 on 2009-02-14
> **ugm6hr said:**
> There is also an option to automatically subscribe to threads you post in.

That way, you can find it in your "User CP" and will know when you've had replies.

OBoy, thanks again. I'll learn to steer my boat yet.:)

---

