---
title: "reason for an invalid ubuntu cd image file?"
date: 2009-06-23
forum: General Help
---

### Post by Andreas1 on 2009-06-23
here's what happened to me today:

-i burned ubuntu-9.04-desktop-i386.iso to a cd using brasero (default program)
-brasero claimed success, no errors
-cd was not bootable, tried on 2 different laptops
-tried to burn the same image using a crappy burning program on windows, instantaneous error message, stating invalid image file

the image i tried to burn had already successfully served to set up my current ubuntu install, so at a certain point it can't have been broken. so my questions:


-can the file have deteriorated while lying around on my harddisk? what would that mean for all my other files? what other possible reason is there?

-why didn't brasero notice that the image file and the resulting cd were broken? (it seemed to do a lot of checking)


i tried to re-download the file via the official torrent, and i thought i could point transmission to the already existing file and then do "verify local data", but transmission seemed to ignore the existing file, it showed 0% progress. so i deleted the existing file and now i am downloading it for new. :(

---

### Post by s.fox on 2009-06-23
Hi,

Have you tried following [this ]("https://help.ubuntu.com/community/HowToMD5SUM")guide?  I would check out the iso using MD5SUM

-Ash R

---

### Post by Andreas1 on 2009-06-23
> **Ash R said:**
> Hi,

Have you tried following [this ]("https://help.ubuntu.com/community/HowToMD5SUM")guide?  I would check out the iso using MD5SUM

-Ash R

thank you! one more thing learned, i never checked the checksums, i will do as of now:
in this case it does not match (it's not even similar, i guess that's how it works)

kind of what i expected, now the question remains how the file could break while just lying around on my harddisk. does this happen often? (spontaneous data corruption on a harddisk)
and, if the cd were bootable and installed without error messages, would it be safe to assume everything is alright? (this kind of digital indeterminism makes me paranoid, argh!)

---

### Post by Bucky Ball on 2009-06-23
Use a disk cleaner. Sometimes just a speck or smudge virtually unseen with the human eye can cause grave errors.

The best way is to torrent the iso with Transmission. The torrent file can be found under 'Alternative Download Methods' (or something like that) on the download page. The md5sum is checked in the process so it is safest. (and fastest!)

Strange things do happen, though. I did a full install on a new build at Christmas, got to the end of install and blank screen. No 'remove disk and restart machine' or anything. I did a re-install *with the same disk* (as it was telling me the disk was not defective in all my checks) and the install is still up and fine seven months later. Go figure. :-k

---

### Post by niteshifter on 2009-06-23
Hi,

To fast on that delete. Here's what you could have done - it would've helped greatly to isolate the issue, any answers you get now are purely speculative.

Notice at the top of the this page: [http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)
the link MD5SUMS? Clicking on it gets you this:
> 3b5e9861910463374bb0d4ba9025bbb1 *ubuntu-9.04-alternate-amd64.iso
c564ae16dffb51a922aef74a07250473 *ubuntu-9.04-alternate-i386.iso
cace6ea9dde8dc158174e345aabe3fae *ubuntu-9.04-desktop-amd64.iso
**66fa77789c7b8ff63130e5d5a272d67b *ubuntu-9.04-desktop-i386.iso**
8f921e001aebc3e98e8e8e7d29ee1dd4 *ubuntu-9.04-netbook-remix-i386.img
78cf52114804f80576b0bfc8f5984339 *ubuntu-9.04-server-amd64.iso
20480057590ff8b80ad9094f40698030 *ubuntu-9.04-server-i386.iso
5e6f6acf2105c366db2f9727e2a65d03 *wubi.exe

The file in question is in bold. Now I happen to have that file, so I do this:
```
md5sum ubuntu-9.04-desktop-i386.iso
```
which trundles for a bit and emits this:
66fa77789c7b8ff63130e5d5a272d67b  ubuntu-9.04-desktop-i386.iso

See how that first part matches? I know the file wasn't corrupted during download and that it hasn't been corrupted during storage / transfer among storage devices.

How about after burning you may ask? I've found [this page]("http://www.troubleshooters.com/linux/coasterless.htm") to be useful. Caveat: Some burner programs pad, some don't. It can take some digging - like the "Details" drop down in the burner dialog to see what CLI tool is being used and how, or in the program's help / manual files. Or googling a lot. Or if all else fails - in the source files.

---

