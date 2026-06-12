---
title: "locale encoding"
date: 2006-01-29
forum: Desktop Environments
---

### Post by fangorious on 2006-01-29
I have searched the forums multiple times for nautilus/locale/accent/etc and can't get this working on one of my machines (and also asked on IRC (multiple channels) multiple times). I have a dual-boot laptop with Windows XP Pro and Ubuntu Breezy.. There is an ext3 partition shared between the two (Ext2 IFS driver for read/write in Windows). I have a bunch of files/folders with accented characters (the usual suspects like ö). They all show up just fine in Windows. 

Back when I was using NTFS or vfat on the shared partition, I could just use a mount option like iocharset=utf8 and the filenames would display right in gnome-terminal and nautilus. But ext3 doesn't have that mount option. I have run 'sudo dpkg-reconfigure locales' umpteen times. I've tried using both en_US and en_US.UTF-8 and neither display the filenames properly. Using en_US.UTF-8 Björk displays as "Bj?rk (invalid encoding)" in nautilus and "Bj?rk" in gnome terminal. Using en_US, it displays as "Bjrk" (there's actually a \u0094 that isn't printed though, looking at the character map it's CANCEL CHARACTER) in nautilus and "Bj?rk" in gnome-terminal. I can rename the files with the codes in GNOME Character Map, but then they don't display properly in Windows (which is booted more often then Linux since it's my work machine).

The most frustrating thing about this is setting my locale to en_US worked on my other machine, also running Breezy (should have the same package set). I can ssh from the bad locale machine to the good locale machine, and filenames on the good locale machine will be displayed properly!

---

### Post by linorg on 2006-02-02
I have same type of problem. In a workgroup I have a Windows file server. Most machines run Windows XP, so renaming is out of the question.

How do I get Nautilus to use ISO-8951 instead of UTF-8??

---

### Post by pertti on 2006-03-11
Same thing here. I formatted my 120gb drive as ext2, to have it as a shared space between Ubuntu and Windows, and having "M?sica (invalid unicode)" is not very funny :).

I use Ubuntu most of the time, so I guess that a Windows driver or program that could treat that partition as read-only, encoded with UTF-8 would be ok. Anyone knows one?

---

### Post by adamkane on 2006-03-11
fangorious:
You have Windows files saved on your ext3 partition. There aren't any utilities for reading Windows encoded files off of an ext3 partition. This is the reason you can't see your special characters. The Windows files are CP850 encoded, not ISO-8859-1 or UTF-8 encoded. 

You need to run a command from the terminal to convert the files from CP850 to UTF-8. There is also a Nautilus script you can run or a Konqueror service menu you can use.
[http://www.ubuntuforums.org/showthread.php?t=139154]("http://www.ubuntuforums.org/showthread.php?t=139154")

Here is the basic command to convert your files.

```

sudo apt-get install convmv
cd /<path to>
convmv -f windows-1252 -t utf-8 -r --notest *.*

``` 

linorg, 
Let me know if the following suggetions work for you. 

Browsing to the Windows share will allow you to see your files correctly:

Panel -> Places -> Network Servers

If you are mounting the share, then you need to edit the /etc/fstab file, and add nls=utf8 to see the mounted share in addition to doing the following:
[http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite]("http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite")

If still can't see ISO-8859-1 encoded files with Nautilus, you can use ROX-Filer. It will display the ISO-8859-1 files in red.
[http://www.ubuntuforums.org/showthread.php?t=139154]("http://www.ubuntuforums.org/showthread.php?t=139154")

To install rox-filer:
```

sudo apt-get install rox-filer
rox-filer

``` 

perrti
You have the same issue as fangorius, so try the convmv command.

Don't do any mass conversions without trying it out on a few files first.

---

### Post by fangorious on 2006-03-12
**adamkane**

I was able to set my locale to en_US.ISO-8859-1 on breezy and the Windows created accented file names showed up just fine in Nautilus and in gnome-terminal, even in the plain text console if I remember correctly. So it does work if configured correctly. Dapper just doesn't want to let me configure it correctly, and nobody seems capable of telling me how.

---

### Post by adamkane on 2006-03-12
"But ext3 doesn't have that mount option."

This statement is correct, so you must convert the files to UTF-8, if you want to see your files correctly. You've already moved your files to ext3, so that is why you are in the situation that you are in.

You are also correct that you may be able to see your files correctly if you change the Ubuntu locale to US english iso-8859-1. I think your files are actually CP850 encoded (Windows encoded), so I don't think this will actually work.

Also if you use ROX-Filer, instead of Nautilus, you may be able to see your files correctly without having to convert any of your files to UTF-8 encoding. This will work if your files are ISO-8859-1 encoded, not CP850 encoded.

Ultimately you'll have to convert all your files to UTF-8. Many people are sticking with ISO-8859-1 as long as they can, until Ubuntu can natively deal with both ISO-8859-1 and UTF-8 filenames, but Ubuntu isn't at that stage yet.

Again if the files were still on a Windows partition, you could mount it as UTF-8, and you would be able to see your files, but the files are on an ext3 partition, so you are stuck, unless you can move the back onto a Windows partition. Otherwise you can either convert the files to UTF-8 or try to change your Ubuntu locale to US english ISO-8859-1.

Ubuntu went UTF-8 without warning anyone, and it has caused a lot of turmoil for everyone. Once you've moved files from an improperly mounted Windows partition to an ext3 partition, the only options are to convert the filenames with the convmv command, or to move the files back onto a Windows partition and then mount the Windows partition with nls=utf8.

---

### Post by fangorious on 2006-03-12
> so I don't think this will actually work.
> Many people are sticking with ISO-8859-1 as long as they can, until Ubuntu can natively deal with both ISO-8859-1 and UTF-8 filenames, but Ubuntu isn't at that stage yet.

It did on breezy. It was glorious while it lasted.

> Again if the files were still on a Windows partition, you could mount it as UTF-8, and you would be able to see your files

Then I could either not be able to edit them or write any new ones (ntfs), or be limited to no files over 2 GB (vfat).

> try to change your Ubuntu locate to US english ISO-8859-1.

That's what I was asking how to do in the first place ;) I've probably asked this question 3-5 times on the forums, and at least a dozen times on IRC, and nobody seems to know. :(

---

### Post by adamkane on 2006-03-12
I've seen too many posts about people losing their data trying to change locales, so I wouldn't be able to help you with that. 

Here are some good links about locale switching though:
[http://www.gentoo.org/doc/en/utf-8.xml]("http://www.gentoo.org/doc/en/utf-8.xml")
[http://gentoo-wiki.com/Index:HOWTO]("http://gentoo-wiki.com/Talk:HOWTO_Make_your_system_use_unicode/utf-8")
[http://www.suse.de/~mfabian/suse-cjk/unicode-switch.html]("http://www.suse.de/%7Emfabian/suse-cjk/unicode-switch.html")

If possible, you should move your files to a Windows partition, mount the Windows partition as UTF-8, then move the files back onto an ext3 partition. Or just convert the filenames with convmv.

---

### Post by simormate on 2007-07-29
My problem is that I can change the filenames and then it will be okay in Ubuntu, but that spoils it windows, and its from there that I wont be able to read them.
Any ideas?

---

### Post by adamkane on 2007-07-29
This will sound like a lame question, but can you describe the method you use to move the files between ubuntu and windows.

(BTW why is it so hard to type responses to threads. Each letter takes a second to appear.)

---

### Post by simormate on 2007-07-29
I created an ext3 partition and I copied files on it coming from windows from a pendrive and a portable hard-drive.
I see now that I have the same problem with files I download with Emule.

---

