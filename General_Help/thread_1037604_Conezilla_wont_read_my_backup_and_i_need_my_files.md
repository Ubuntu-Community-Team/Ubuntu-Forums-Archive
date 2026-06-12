---
title: "Conezilla wont read my backup and i need my files?"
date: 2009-01-11
forum: General Help
---

### Post by mikeuhlik on 2009-01-11
Hi everyone this is my issue I used Clonezilla to backup My hole drive to a image on my My Book 500 gig. Now when I use Clonezilla to restore the image it says I don't have a backup but I do I have my backup located here.

/media/My Book/2008-12-03-04-img

Clonezilla is not able to read it there and I cant get it to recognize it at all no matter what I try. I have booted with 3 different cds.

clonezilla-sysresccd-full-mod-2.6.0.iso
gparted-clonezilla-2.3.iso
clonezilla-live-1.2.1-17.iso

Also I am trying to restore it to a Virtual Box PC with the live CD because I only need the home directory not the hole system so I was going to restore the clonezilla backup on the Virtual Box machine and when it booted to the restored ubuntu system I was going to back up just the home directory to my external My Book and do a reinstall of ubuntu on my main system.

I also read on a post that you can mount the clonezilla backup image in ubuntu and extract files you need but have not been successful.

[http://ubuntuforums.org/showthread.php?t=872832]("http://ubuntuforums.org/showthread.php?t=872832")

Here are the directions I got from the post.

1. Prepare a large disk in Linux
2. Say if your image is /home/partimag/YOURIMAGE/, and the image is /home/partimag/YOURIMAGE/hda1.ntfs-img.aa, hda1.ntfs-img.ab...
run
"file /home/partimag/YOURIMAGE/hda1.ntfs-img.aa"
to see it's gzip, bzip or lzop image. Say it's gzip, then you can run
cat /home/partimag/YOURIMAGE/hda1.ntfs-img.* | gzip -d -c | ntfsclone --restore-image -o hda1.img -
Then you will have a "hda1.img" which you can mount it by
mount -o loop -t ntfs hda1.img /mnt

Then all the files are in /mnt/

My goals are to get my home directory back from this clonezilla backup either by mounting the image or getting the restore to work the clonezilla restore has not been working I have been trying to do it for 2 weeks now and no luck so I am thinking the best way would be to mount the image and browse it and get the files back from my home directory.

I don't understand the mounting direction above for my layout.

My backup is in my My Book here: /media/My Book/2008-12-03-04-img

In the 2008-12-03-04-img folder i have these file there

/media/My Book/2008-12-03-04-img/parts
/media/My Book/2008-12-03-04-img/sda1.aa
/media/My Book/2008-12-03-04-img/sda1.ab
/media/My Book/2008-12-03-04-img/sda1.ac
/media/My Book/2008-12-03-04-img/sda1.ad
/media/My Book/2008-12-03-04-img/sda1.ae
/media/My Book/2008-12-03-04-img/sda1.af
/media/My Book/2008-12-03-04-img/sda1.ag
/media/My Book/2008-12-03-04-img/sda1.ah
/media/My Book/2008-12-03-04-img/sda1.ai
/media/My Book/2008-12-03-04-img/sda1.aj
/media/My Book/2008-12-03-04-img/sda1.ak
/media/My Book/2008-12-03-04-img/sda-chs.sf
/media/My Book/2008-12-03-04-img/sda-mbr
/media/My Book/2008-12-03-04-img/sda-pt.parted
/media/My Book/2008-12-03-04-img/sda-pt.sf

I am pretty sure that it is gziped and the I backedup is filesytem is ext3.

I ran this command in ubuntu terminal "file /home/partimag/YOURIMAGE/hda1.ntfs-img.aa"

but like this "file /home/partimag/2008-12-03-04-img/sda1.aa"

I got this error "ERROR: cannot open `/home/partimag/2008-12-03-04-img/sda1.aa' (No such file or directory)"

so I tried this command "file /media/My Book/2008-12-03-04-img/2008-12-03-04-img/sda1.aa"

I got this error "/media/My:                                        ERROR: cannot open `/media/My' (No such file or directory)
Book/2008-12-03-04-img/2008-12-03-04-img/sda1.aa: ERROR: cannot open `Book/2008-12-03-04-img/2008-12-03-04-img/sda1.aa' (No such file or directory)"

I was also wondering how I would run these command to my system specs since I am not using ntfs I did a backup of ext3 filesytem

Example command: 
cat /home/partimag/2008-12-03-04-img/sda1.* | gzip -d -c | ext3clone --restore-image -o hda1.img -

mount -o loop -t ext3 hda1.img /mnt

Please if any on could help my I really need these file to get up and running for my work. I am stuck now just trying to get these files back.

Please Please very much appreciated.

Thanks for your time eveyone.:confused:

---

