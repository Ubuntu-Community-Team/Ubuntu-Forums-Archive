---
title: "torrent download"
date: 2009-02-24
forum: General Help
---

### Post by TDFlanders on 2009-02-24
Just wanted to report:

I downloaded the following two DVD images:

root@thomas-laptop:/home/thomas# md5sum ~/Desktop/ub*8.10*iso
md5sum: /root/Desktop/ub*8.10*iso: No such file or directory
root@thomas-laptop:/home/thomas# md5sum /home/thomas/Desktop/ub*8.04*iso
5fddb647c1945b20055d751576dea8fc  /home/thomas/Desktop/ubuntu-8.04.1-dvd-i386.iso
root@thomas-laptop:/home/thomas# md5sum /home/thomas/Desktop/ub*8.04*iso
5fddb647c1945b20055d751576dea8fc  /home/thomas/Desktop/ubuntu-8.04.1-dvd-i386.iso
root@thomas-laptop:/home/thomas# lsb_release -rd ; uname -a ; date
Description:    Ubuntu 8.10
Release:    8.10
Linux thomas-laptop 2.6.27-12-generic #1 SMP Thu Feb 5 09:26:35 UTC 2009 i686 GNU/Linux
Tue Feb 24 14:51:56 GMT 2009
root@thomas-laptop:/home/thomas# 

<AND>

thomas@thomas-laptop:~$ ls ~/Desktop/ub*8.10*iso
/home/thomas/Desktop/ubuntu-8.10-dvd-i386.iso
thomas@thomas-laptop:~$ md5sum ~/Desktop/ub*8.10*iso
26fd54a27a30d237c05b649b41f1c760  /home/thomas/Desktop/ubuntu-8.10-dvd-i386.iso
thomas@thomas-laptop:~$ [http://torrent.ubuntu.com:6969/file?info_hash=T74%19%DF%CE%E8%A2%5E%5B%3E%BC%C5Y%0A%11%2Ao3%B6](http://torrent.ubuntu.com:6969/file?info_hash=T74%19%DF%CE%E8%A2%5E%5B%3E%BC%C5Y%0A%11%2Ao3%B6) /home/thomas/Desktop/ubuntu-8.10-dvd-i386.iso
bash: [http://torrent.ubuntu.com:6969/file?info_hash=T74%19%DF%CE%E8%A2%5E%5B%3E%BC%C5Y%0A%11%2Ao3%B6:](http://torrent.ubuntu.com:6969/file?info_hash=T74%19%DF%CE%E8%A2%5E%5B%3E%BC%C5Y%0A%11%2Ao3%B6:) No such file or directory
thomas@thomas-laptop:~$ rsync -zHHP rsync://torrent.ubuntu.com:6969/file?info_hash=T74%19%DF%CE%E8%A2%5E%5B%3E%BC%C5Y%0A%11%2Ao3%B6 /home/thomas/Desktop/ubuntu-8.10-dvd-i386.iso
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: error in rsync protocol data stream (code 12) at io.c(635) [receiver=3.0.3]
thomas@thomas-laptop:~$ md5sum ~/Desktop/ub*8.10*iso26fd54a27a30d237c05b649b41f1c760  /home/thomas/Desktop/ubuntu-8.10-dvd-i386.iso
thomas@thomas-laptop:~$ 

I used the torrents from this site:

[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

The download went fine but the info hashes displayed on the above site seem to be all different from the official ubuntu md5sums. I was about to redownload but luckily I googled my hashes and found they were actually legit:

[http://cdimage.ubuntu.com/releases/8.10/release/MD5SUMS](http://cdimage.ubuntu.com/releases/8.10/release/MD5SUMS)
[http://cdimage.ubuntu.com/releases/8.04/release/ubuntu-8.04.1-dvd-i386.metalink](http://cdimage.ubuntu.com/releases/8.04/release/ubuntu-8.04.1-dvd-i386.metalink)

The info hashes are actually related to the bittorrent client only, not to the md5sums:

[http://linuxtracker.org/smf/index.php?topic=94](http://linuxtracker.org/smf/index.php?topic=94)

I downloaded through transmission and did not even know about info hashes, although I used bittornado in the past. None of the ubuntu documentation pages describes what info hashes are good for:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)
[https://help.ubuntu.com/community/BitTorrent](https://help.ubuntu.com/community/BitTorrent)

Unfortunately this seems to lead to much confusion for other ubuntu users too:

[http://ubuntuforums.org/archive/index.php/t-999051.html](http://ubuntuforums.org/archive/index.php/t-999051.html)

Can anyone coach me on how to update the appropiate wiki properly?

Thanks,

Thomas

---

### Post by TDFlanders on 2009-02-24
BTW,

I erroneously tried to rsync a torrent file (See above). Please don't try to copy.

Thomas

---

