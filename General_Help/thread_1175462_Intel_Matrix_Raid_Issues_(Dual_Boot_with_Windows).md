---
title: "Intel Matrix Raid Issues (Dual Boot with Windows)"
date: 2009-06-01
forum: General Help
---

### Post by Jericon on 2009-06-01
Hello,

I am currently dual booting Windows 7 and Ubuntu 9.04.  I have them on separate partitions of my 150 GB OS Drive.  I am required to keep Windows for several reasons, including work (VPN).  

In addition to my 150 GB OS Drive, I have a 4x 1 TB Raid 5 configured using the onboard raid.  This is done through the Intel ICH10R controller.  It is currently formatted as NTFS.

I would like to be able to boot into Ubuntu and still be able to access the files on this raid, without degrading it or limiting the access when booted via Windows.  I looked through the HowToFakeRaid wiki article, but could not get it to properly mount.

Here is some information that I have which may assist in troubleshooting.

=-=-=-=-=

root@trimaxian:/dev/mapper# dmraid -b
/dev/sde:   1953525168 total, "9QJ2E07H"
/dev/sdd:   1953525168 total, "9QJ0SPY3"
/dev/sdc:   1953525168 total, "9QJ1YEDL"
/dev/sdb:   1953525168 total, "9QJ0HV2D"
/dev/sda:    293046768 total, "WD-WXL908131579"

root@trimaxian:/dev/mapper# dmraid -rD
isw: untested metadata version 1.3.00 found on /dev/sde
isw: untested metadata version 1.3.00 found on /dev/sdd
isw: untested metadata version 1.3.00 found on /dev/sdc
isw: untested metadata version 1.3.00 found on /dev/sdb
/dev/sde: isw, "isw_bibhgfcabi", GROUP, ok, 1953525165 sectors, data@ 0
/dev/sdd: isw, "isw_bibhgfcabi", GROUP, ok, 1953525165 sectors, data@ 0
/dev/sdc: isw, "isw_bibhgfcabi", GROUP, ok, 1953525165 sectors, data@ 0
/dev/sdb: isw, "isw_bibhgfcabi", GROUP, ok, 1953525165 sectors, data@ 0

root@trimaxian:/dev/mapper# dmraid -aY
isw: untested metadata version 1.3.00 found on /dev/sde
isw: untested metadata version 1.3.00 found on /dev/sdd
isw: untested metadata version 1.3.00 found on /dev/sdc
isw: untested metadata version 1.3.00 found on /dev/sdb
RAID set "isw_bibhgfcabi_Data" already active
=-=-=-=-=

When I attempt to mount (using mount -t ntfs /dev/mapper/isw_bibhgfcabi_Data /data) I receive an error that a valid NTFS file system does not exist on the device.  If I attempt to mount without the -t flag, it tells me that I must specify a file system.

Can anyone point me into the right direction to get this working?  Is it even possible to do what I want to do?

The raid is currently about halfway full, as such, I cannot afford to reformat it or anything like that to get it working.

Thanks in advance.

Ciao,
-J

---

### Post by ronparent on 2009-06-01
In my case dmraid does not handle isw in a raid 5 configuration. Do **dmraid -l** which tells you what formats are handled. This implies only that dmraid doesn't handle the format, not necessarily true for the chipset (ie with proprietary drivers for windows).

---

### Post by Jericon on 2009-06-01
> **ronparent said:**
> In my case dmraid does not handle isw in a raid 5 configuration. Do **dmraid -l** which tells you what formats are handled. This implies only that dmraid doesn't handle the format, not necessarily true for the chipset (ie with proprietary drivers for windows).


[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Indicates that dmraid can support raid 5 on the Intel ICH9 Controller.  I will have to run dmraid -l when I get home to verify though.

If it does not, is there any alternate method of getting something like this to work?

---

### Post by Jericon on 2009-06-02
> **ronparent said:**
> In my case dmraid does not handle isw in a raid 5 configuration. Do **dmraid -l** which tells you what formats are handled. This implies only that dmraid doesn't handle the format, not necessarily true for the chipset (ie with proprietary drivers for windows).

You were correct.  It does Raid 1 and 0, but not raid 5.

This puts me at an impasse.  I really want to use Ubuntu as my primary OS on my system.  However, there is a good amount of data that I need to have accessible in Windows (iTunes library, Picture collection, etc) and I do need to use Windows on a regular basis for work.

Short of purchasing a new motherboard or a hardware raid card, is anyone aware of any way to get this to work?  I would be willing to reformat the raid drives and set it up another way if that's the only way that I can get it to work.  It is important, though, that I have all 4 of these drives in Raid 5.

Thanks again.

---

### Post by ronparent on 2009-06-02
I think you are faced by an impass. Although possible to reformat the drives to use them as a software raid set, they would not be accessible to windows in that form. This is because I don't believe that the drives could be used in a software raid without erasing the 'fakeraid' metadata needed for the windows drivers to recognize them. Also creating the mddam (software) raid5 set in itself would erase all data on the drives. You might find out from someone in the servers forum if there is a workaround - but prepare to be lectured on how inferior the fakeraid approach is compared to a true raid or software raid implementation before you get a helpful response. Also you could try a separate dmraid (fakeraid) forum site to see if anything is in the works.

I wish I could be more help. Good luck.

---

### Post by Jericon on 2009-06-30
> **ronparent said:**
> I think you are faced by an impass. Although possible to reformat the drives to use them as a software raid set, they would not be accessible to windows in that form. This is because I don't believe that the drives could be used in a software raid without erasing the 'fakeraid' metadata needed for the windows drivers to recognize them. Also creating the mddam (software) raid5 set in itself would erase all data on the drives. You might find out from someone in the servers forum if there is a workaround - but prepare to be lectured on how inferior the fakeraid approach is compared to a true raid or software raid implementation before you get a helpful response. Also you could try a separate dmraid (fakeraid) forum site to see if anything is in the works.

I wish I could be more help. Good luck.

That was very much the case.

What I ended up doing probably wasn't the most elegant solution, but I dropped some extra money and built myself a NAS Server that is now running SMB on Gentoo.  It's also next to my TV so I can play videos straight that way.

And, of course, files are accessible via both Windows and Linux.  As I said, not the most elegant solution, nor the cheapest one, but it works for me. :)

Thanks for the input.

/J

---

