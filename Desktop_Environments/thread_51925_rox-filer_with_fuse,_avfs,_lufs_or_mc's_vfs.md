---
title: "rox-filer with fuse, avfs, lufs or mc's vfs"
date: 2005-07-25
forum: Desktop Environments
---

### Post by suoko on 2005-07-25
Has anyone succeded installing fuse, avfs, lufs or mc's vfs and let one of those work with rox-filer in order to open ftp sites with rox?
Actually it seems that fuse is already installed in ubuntu. 
If it works, how can I use it?

---

### Post by breaking on 2008-03-12
Could anybody be bothered to answer this guy's question? It's weird to me how all VFS related questions get ignored. Type any combination of fuse avfs lufs mc vfs (at least 2+) and this post comes to the top.

Another post comes up as #1 with any combo of gnome and lufs specifically. This friendly, thoughtful poster:
[http://ubuntuforums.org/showthread.php?t=78825](http://ubuntuforums.org/showthread.php?t=78825)

There's a clear pattern here... what gives? I'm not a complete newbie to Linux anymore, but this seems like an impossibly underrated priority for people to accomplish. Why can't I open an http, ftp, ssh / fish:// or sftp (you get the idea) file in any app in any major linux distro with exception for a Knoppix Live distro and a few others. Hopefully if I figure it out, I'll post back everywhere I can think of so the community can get some answers...

but if YOU, yes YOU the person reading this right now wondering why I sound all grumpy and if I should get flamed has any clue what I'm on about, why I'd need to do this, and can help in finding an answer then I for one, would greatly appreciate it and (apparently) would a small portion of the community that uses files over a network and is sick of copying everything to their desktop or /tmp to use them!

---

### Post by gubemton on 2008-03-13
hmm, i wondered the same thing. I forget which distro, but I remember how happy weird kde felt but how happy I was when i realised it was smart enough to open files on the network like windows, osx etc do. Is there a package I'm missing? I installed everything I could think of and nothing seems to realise it's there. Somehow ppl making other distros figure this out, so it must be possible. I also need to open files over ftp like other posters. Help?? Why is this issue so hard for people? Seems really easy compared to things like 3d desktops and all that jazz. :confused:

---

### Post by just-want-one-attachment on 2008-03-17
Bump! I have this same problem too.

---

### Post by toobuntu on 2008-03-27
I have this working successfully in Hardy with Rox-filer:

# mount remote ftp locations as local filesystems with FUSE
```
sudo aptitude install curlftpfs
```
1. general usage
```
sudo curlftpfs ftp://<ftp-site-url>/<subdir>/ /mnt/ftp/ -o allow_other,user="<ftp-username>"
```
2. more secure usage
   a. for security purposes, create a .netrc file to store the username and password so they do not appear in process lists
```
vim .netrc
	machine <ftp-site-url> login <ftp-username> password <ftp-pass>
	default login anonymous password user@site
chmod 600 .netrc
```
   b. mount
```
sudo curlftpfs  <ftp-site-url>/<subdir> /mnt/ftp/ -o allow_other
```
3. even more useful is to create an entry in /etc/fstab and use a netrc file for security
   a. netrc
```
sudo vim /root/.netrc
	machine <ftp-site-url>
		login <ftp-username>
		password <ftp-pass>
	default login anonymous password user@site
sudo chmod 600 /root/.netrc
```
   b. fstab
```
sudo vim /etc/fstab
	curlftpfs#<ftp-site-url>/<subdir>/ /mnt/ftp/               fuse    allow_other,rw,uid=<uid #>,tcp_nodelay,direct_io,noauto        0       0
```
could use gid instead of uid if it's a multiuser setup
   c. mount
```
sudo mount /mnt/ftp/
```
4. libcurl crashes on umount
After adding tcp_nodelay,direct_io options in /etc/fstab, libcurl no longer crashed on umount
# 27-Mar-2008 update: Just tried again without those options (not that they're bad to use or anything, but just to see...) and libcurl did not crash.  Maybe a system update fixed this problem....
5. permissions issues
   a. The problem: After mounting, cat /mnt/ftp/bak/hardy-installation-notes.txt fails with error: "Permission denied."
   b. The solution/workaround: Retry the same command (does not matter if you wait a little bit or retry immediately) and it seems to work.  Weird.

---

