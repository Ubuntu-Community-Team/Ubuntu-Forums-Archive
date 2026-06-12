---
title: "Faulty slocate with big files in Gutsy"
date: 2007-11-28
forum: Desktop Environments
---

### Post by HJB on 2007-11-28
Hi all. I just noticed that slocate doesn't find certain files although they are indexed?

I just ripped a dvd. It is in my home directory. 
I tried to updatedb and then slocate movie.iso but it didn't show the new file.

I then did the following:
sudo rm /var/lib/slocate/slocate.db
sudo updatedb -v|grep movie.iso ## this is to see what is being indexed
/home/hjb/movie.iso ##is the result on the screen, thus it is being indexed

and then when I type: slocate -i movie.iso
the output is blank.

hjb@kubuntu:~$ ls movie.iso -lha ## results in
-rw-r--r-- 1 hjb hjb 4.2G 2007-11-28 09:08 movie.iso

Is this a error or am I missing something?
I read through the man pages of both slocate an updatedb but there is nothing about size?

Im using kubuntu 7.10
Linux kubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

more info
md5sum /usr/bin/slocate
21b25a38dd9a449975423a3ee9cff490  /usr/bin/slocate

hjb@kubuntu:~$ ls -lha /usr/bin/slocate
-rwxr-sr-x 1 root slocate 31K 2007-10-03 20:36 /usr/bin/slocate*

mount shows:
/dev/sda3 on /home type ext3 (rw)

This is very strange?
Please advice.

Bye
HJB:confused:

---

