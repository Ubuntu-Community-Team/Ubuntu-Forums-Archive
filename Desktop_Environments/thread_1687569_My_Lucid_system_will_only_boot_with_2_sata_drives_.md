---
title: "My Lucid system will only boot with 2 sata drives installed"
date: 2011-02-14
forum: Desktop Environments
---

### Post by bturrie on 2011-02-14
My system won't boot unless I have 2 sata drives. It doesn't matter what's on the second one. It even boots if the second "disk" is a powered sata to IDE adapter attached to an unpowered IDE drive.

If I don't have the second drive I get this when I try to boot:


[INDENT]Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist
[/INDENT]
which as best I can tell from other posts, is a kernel problem. If it helps, the UUID in question is for sda5 and is present.

I don't see anything that seems odd to me in my /etc/fstab file.

[INDENT]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation---this is the uuid of sda5
UUID=e261d2a4-0d80-4746-9bf9-b74a9bc36ef8 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation--this is the uuid of sda6
UUID=92ce5628-9764-4425-a174-c7b2c6866665 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3   /media/secondhome ext4 defaults 0 0
[/INDENT]
I've done the whole use a live disk, chroot into my system and reinstall the kernel to no avail.

[INDENT]uname -r gives -- 2.6.32-28-generic
[/INDENT]
Any suggestions other than leaving in the second drive and hoping the next kernel update fixes things?
And, um I haven't filed a bug report yet.

---

### Post by oldfred on 2011-02-14
Post this to see entire configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by bturrie on 2011-02-15
Thanks for the reply, I like the tool. I used it and didn't like what I saw. It turns out I had misinterpreted the bit about requiring a second drive. 

I had a clone of my disk only a couple of weeks old that boots fine so, I decided to try an easier approach to fixing my problem.  I copied partition images from the working drive to the problem drive using Clonezilla. Clonezilla reinstalled grub2 as part of the process. 

The problem disk still won't boot. Same error message dropping me into busybox as before. I'm thinking the drive is at least partly hosed. 

I'll look closer at the drive when the weekend comes.

---

### Post by oldfred on 2011-02-16
If you have totally clone partitions/drives you have duplicate UUIDs that cannot have duplicates. System gets very confused. 

Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

---

### Post by bturrie on 2011-02-16
I believe but can't prove that the first boot failure happened when I had the "problem drive" and an unrelated drive connected; the clone was not in. I only hooked up the clone when I was troubleshooting. The boot diagnostic showed how silly (and embarrassing) that was.

Anyway, I only had one disk connected last night and it wouldn't boot. Once again it dumped me into busybox. 

Experimenting a bit more today, I found out that my "problem disk" boots just fine if I turn off AHCI in my bios. I'd only turned AHCI on for testing because I read that Intel x25 SSDs want it. My disk booted with AHCI on the first couple of times but not since. At this point, I'm thinking bios or missing kernel package or a timing issue. Still looking, though my interest in SSDs is waning fast.

---

### Post by bturrie on 2011-02-17
I found this post online. 

#Please note that changing this BIOS feature after installing the operating system may cause a boot failure. You may be required to reinstall the operating system.

Read more: [http://www.techmetica.com/howto/sata-ahci-mode-bios-setting.-what-does-it-do/#ixzz1EGgx8hcR](http://www.techmetica.com/howto/sata-ahci-mode-bios-setting.-what-does-it-do/#ixzz1EGgx8hcR)

Looks like I'd need to reinstall my OS if I'm going to use AHCI.

---

### Post by oldfred on 2011-02-18
That is with XP.

I installed XP 3 or 4 years ago and did not know I needed the AHCI drivers. Both Linux & XP worked.

I then saw I should enable AHCI and did. Ubuntu booted without issue, then XP did not work. Turned it back off.  I did find somewhere that I could install the XP drivers after the fact but just have not gotten around to it. i keep hoping not to boot XP at all, soon, so then it would not matter.

---

