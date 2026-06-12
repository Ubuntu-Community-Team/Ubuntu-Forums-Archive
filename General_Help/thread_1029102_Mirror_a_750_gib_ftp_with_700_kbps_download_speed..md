---
title: "Mirror a 750 gib ftp with 700 kbps download speed. Mirror strategy? Timestamp?"
date: 2009-01-03
forum: General Help
---

### Post by windwhisper on 2009-01-03
Current I am trying to mirror a 750 gib ftp with 700 kbps download speed. I am supposed to find a way to do this and also make it easy to maintain in one week.

The first level of the directory has over 20 subdirectories (referred to as databanks latter), the size of which varies from 163 gib to 188 kib. Every one week or two, these databanks are regenerated, so a complete download will be needed.

**What I have:**
(1) 4 mirror servers. Single-threaded download speed varies from 200kb to 1 mb, depending on server status, can't decide the best server once for all.
(2) 3 local machines available for download every night from 8 p.m. to 8 a.m. . One of them has 2 x 500 gb sata disks to store the mirror. The other two can also write to the disks via nfs. All with Ubuntu 8.04 Server Edition installed.
(3) A 100 mb local network. 

**Main Constraints:**
(1) Every file of this mirror must display exactly the same information as the original site except owner information.
Problems: 
At first I tried "wget -m (-r -I inf -N)", and found the directory's last modified date did not comply with the server. 
I then tried rsync and it worked well regarding directory timestamp. However, the administrator of the server strongly opposed the use of rsync saying it would take more server cpu time and can not provide a better download speed.
(2) A complete download must be accomplished in no more than 36 hours.
Problems:
<I> Single-threaded download
In 12 hours with 700 kb downloaded every second, one machine can download 28.1Gib. 
To download the whole mirror, it would take me 9 days (9 x 12 hours).
Unbearable.
<II> Using multiple threads of "wget -m",
To meet the 36 hours constraint, I have to run 3 "wget -m" on each machine. Then another problem: 6 databanks of the mirror are bigger that 50 gib, 3 of them over 120 gib. If I use different "wget -m" for each databank, the biggest one would be the bottle neck. The total download can not finish as long as download for the biggest one is not over. Sadly, it takes 6 days to download the biggest one using one "wget -m". 
I also tried using multiple "wget -m" to mirror one databank to one destination, and each tended to download the whole thing. No signs of sharing listing and working accordingly. 
<III>How can I tell which servers are busy and which are not? 
Depending on time, some servers can be really hard to connect and the download crawls while others may be enjoying coffee time. 
200 kbps and 1 or maybe 3 mbps do make a great difference.

**My solution:**
(1) To keep timestamp for all and download without "one wget for one databank" mode.
I am trying to work it out with some bash scripts.
Steps:
a Make the 3 local machines share a path to download, say /srv/ftpserv. 
One will actually have the destination directory, while the other two will mount that via nfs. 
At the same time, these 3 machines will share a path for mirror daemon, say /srv/mirror-daemon. 
Under this path, there will be an ls-lR of the server files. 

b Write scripts that can do this:
Change working directory (I will use wd for short afterwards) to download path and begin to scan the ls-lR under the mirror daemon path line by line.

If the line is followed by a content listing of a dir
./databank:
total 166271392
......dira
......fileb
, replace the "." with download path, remove the ":", and then change wd to it. 
Generate a file to keep every dir and file in current wd that has a match in ls-lR, say .maintain.
Go to next line of ls-lR.

If the line is a dir
drwxr-xr-x 113 mirror    archive        3842 Dec  7 21:48 databank
, scan current wd. If there is a dir with the same name, do nothing. 
If not, make one. Save timestamp information under this dir, say databank/.dir-timestamp.
Add name of this dir to .maintain under current wd.
Go to next line of ls-lR. 

If the line is a common file
-r--r--r--   1 mirror    archive     1093786235 Dec  5 03:46 env_nt.01.tar.gz
, scan current wd. If there is file with the same name, timestamp and size, do nothing. 
Add name of this file to .maintain under current wd.
If there is no file with this name or with different timestamp or size, remove any file with the same name and "wget -N" the file.
Go to next line of ls-lR. 

If the line is a symbolic link, create if the link is not there. Never follow symbolic links. 
Add name of this link to .maintain under current wd.
Go to next line of ls-lR.

Before going into another dir, do these:
Scan every dir and file in current wd. If its name can not be found in .maintain, remove it so as to keep things just as the server does.
Change current wd timestamp according to .dir-timestamp generated before.

Summary:
Main constraint 1 can be satisfied as the program uses "wget -N" for file and changes dir timestamp just before leaving it.
I suppose this can also satisfy main constraint 2 mentioned before as multiple wget can run at the same time for one databank and time can be made better use of as no useless wait is needed. Thinking of running no more than 10 wget on one machine, I hope the download speed for one machine can achieve 3 mbps. If everything goes well, a complete download can be done in about 25 hours. 

(2) To find a fast server.
There are always two files ls-lR.Z and ls-lR.old.Z on the server. I am thinking of downloading these two 5 mib files and make a speed assumption of 10 mib / download time. 

**More that happy to get your suggestion**

I am new in Ubuntu and haven't tried a lot yet (sad enough, I googled and checked local program repository, but still didn't know how to modify a file's timestamp). As I don't know much of its power, I suppose there are other better ways to do what I want. 
So, more that happy to get your suggestion, on anything.

---

### Post by windwhisper on 2009-01-04
Wonder if I put this in a wrong category.

Any suggestions?

---

### Post by nemilar on 2009-01-05
You may try posting this in the Networking or Server categories.  I imagine you'd get more targeted help there.

---

