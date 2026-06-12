---
title: "steam help. keep getting error"
date: 2015-05-18
forum: Gaming &amp; Leisure
---

### Post by xXMLGn1njaXx on 2015-05-18
Hey i need some help, for some reason i keep getting this error whenever i try to boot up steam: Couldn't set up Steam data - please contact technical support. Also this does not happen on my friend's account ON THE SAME PC. how do i fix this?

---

### Post by Vladlenin5000 on 2015-05-18
Hi and welcome.

Considering other users' accounts work in the same system, then logically the problem is in your profile/settings.
Please read: [http://askubuntu.com/questions/470436/steam-cannot-set-up-steam-data](http://askubuntu.com/questions/470436/steam-cannot-set-up-steam-data)
The first answer is the best solution. Open a terminal and copy/paste for accuracy the commands one by one. Keep reading though because the following later answer (by Ric Crouch) explains WHY it happened (ignore the commands, you did it already):

> This error can result if you HAD Steam installed, then did a "nuke and pave" to re-install your system but had /home  on a different partition.  When you reinstall Linux, your home  directory is intact, including your Steam settings, which are in the ~/.steam directory.

PS - Although this forum is here to help and I'm personally glad that I could be of some assistance, it's also true that you had to wait at +4 hours for something you could have easily googled yourself. It took me exactly 0.4 seconds ;).

Enjoy your games.

---

### Post by efflandt on 2015-05-20
I think one issue (which may have been resolved since then) is that if you ran steam as one Linux user and then tried to run steam from a different Linux user, something created in /tmp had permission for the first Linux user who ran steam, but remained when steam was closed, and did not have permission for the other Linux user to run steam. I discovered that when I set up an alternate Steam account last November and tried to run the alternate Steam account from a different Linux user. But because I did not know what the problem was, simply rebooting (which empties /tmp) resolved it.

But running 2 different Steam logins from the same Linux user account is no problem, other than any custom config files for common games being shared and acting the same for both Steam accounts. So now I log into steam as either Steam user from the same Linux user account. But both are me, so it does not matter that config for both are the same. For the two Steam accounts items are still kept separate on Steam's item server and achievements are kept separate on the Steam Cloud.

As far as Steam data file locations, I noticed that changed at some point between Steam beta installed on my desktop before release Jan 2013 when I was running 64-bit Ubuntu 12.04 (and entire /home copied intact to 14.04 which still works) and steam installed from scratch on my laptop using Software Center in 14.04 and steam games installed from scratch there. Even though paths and capitalization of some directories are different, either works if all the directories and symlinks are intact. But if you just copied some things over and not everything (your entire home directory), some things may end up where steam cannot find them automatically.

For example in the early system ~/.steam is mostly symlinks and games are in ~/.local/share/Steam/SteamApps/common/```
efflandt@XPS-8100-1404:~$ ls -l .steam
total 20
lrwxrwxrwx 1 efflandt efflandt   27 May 18 22:05 bin -> /home/efflandt/.steam/bin32
lrwxrwxrwx 1 efflandt efflandt   45 May 18 22:05 bin32 -> /home/efflandt/.local/share/Steam/ubuntu12_32
lrwxrwxrwx 1 efflandt efflandt   45 May 18 22:05 bin64 -> /home/efflandt/.local/share/Steam/ubuntu12_64
-rw-rw-r-- 1 efflandt efflandt 2389 May 18 23:32 registry.vdf
lrwxrwxrwx 1 efflandt efflandt   33 May 18 22:05 root -> /home/efflandt/.local/share/Steam
lrwxrwxrwx 1 efflandt efflandt   41 May 18 22:05 sdk32 -> /home/efflandt/.local/share/Steam/linux32
lrwxrwxrwx 1 efflandt efflandt   41 May 18 22:05 sdk64 -> /home/efflandt/.local/share/Steam/linux64
lrwxrwxrwx 1 efflandt efflandt   33 May 18 22:05 steam -> /home/efflandt/.local/share/Steam
-rwxrwxr-x 1 efflandt efflandt 8860 Dec 30 21:48 steam_install_agreement.txt
-rw-rw-r-- 1 efflandt efflandt    5 May 18 22:05 steam.pid
prw------- 1 efflandt efflandt    0 May 18 22:05 steam.pipe
```
And on the new fresh system games are in ~/.steam/steam/steamapps/common/```
efflandt@GE60-2OE:~$ ls -l .steam
total 464
drwxrwxr-x  4 efflandt efflandt   4096 Apr 13 01:02 bin
lrwxrwxrwx  1 efflandt efflandt     33 Apr 13 01:03 bin32 -> /home/efflandt/.steam/ubuntu12_32
lrwxrwxrwx  1 efflandt efflandt     33 Apr 13 01:03 bin64 -> /home/efflandt/.steam/ubuntu12_64
-rwxrwxr-x  1 efflandt efflandt  11384 Nov 11  2014 bin_steamdeps.py
-rwxrwxr-x  1 efflandt efflandt   5390 Nov 11  2014 bin_steam.sh
drwxrwxr-x  7 efflandt efflandt   4096 Apr 13 01:05 config
drwxrwxr-x  2 efflandt efflandt   4096 Apr 13 01:02 controller_base
drwxr-xr-x  2 efflandt efflandt   4096 Feb 16 11:16 fontconfig
drwxrwxr-x  2 efflandt efflandt  16384 Apr 13 01:02 friends
drwxrwxr-x  3 efflandt efflandt  49152 Apr 13 01:02 graphics
drwxrwxr-x  2 efflandt efflandt   4096 Apr 13 01:02 linux32
drwxrwxr-x  2 efflandt efflandt   4096 Apr 13 01:02 linux64
drwxrwxr-x  2 efflandt efflandt   4096 Feb 16 17:04 logs
drwxrwxr-x  2 efflandt efflandt   4096 Apr 13 01:02 package
drwxrwxr-x  3 efflandt efflandt  20480 Apr 13 01:02 public
-rw-rw-r--  1 efflandt efflandt    662 Apr 13 01:58 registry.vdf
drwxrwxr-x  3 efflandt efflandt   4096 Feb 16 11:15 remoteui
drwxrwxr-x  6 efflandt efflandt  20480 Apr 13 01:02 resource
lrwxrwxrwx  1 efflandt efflandt     21 Apr 13 01:03 root -> /home/efflandt/.steam
lrwxrwxrwx  1 efflandt efflandt     29 Apr 13 01:03 sdk32 -> /home/efflandt/.steam/linux32
lrwxrwxrwx  1 efflandt efflandt     29 Apr 13 01:03 sdk64 -> /home/efflandt/.steam/linux64
drwxrwxr-x  2 efflandt efflandt   4096 Apr 13 01:02 servers
drwxrwxr-x  2 efflandt efflandt   4096 Apr 13 01:02 skins
drwxrwxr-x 12 efflandt efflandt   4096 Apr 13 01:58 steam
-rwxrwxr-x  1 efflandt efflandt    857 Nov 11  2014 steamdeps.txt
-rwxrwxr-x  1 efflandt efflandt   8860 Nov 11  2014 steam_install_agreement.txt
-rwxrwxr-x  1 efflandt efflandt    869 Nov 11  2014 steam_msg.sh
-rw-rw-r--  1 efflandt efflandt      6 Apr 13 01:03 steam.pid
prw-------  1 efflandt efflandt      0 Apr 13 01:04 steam.pipe
-rwxrwxr-x  1 efflandt efflandt  22529 Mar 10 01:37 steam.sh
drwxrwxr-x  3 efflandt efflandt   4096 Feb 16 11:15 tenfoot
-rwxrwxr-x  1 efflandt efflandt    405 Nov 11  2014 ThirdPartyLegalNotices.css
-rwxrwxr-x  1 efflandt efflandt  25088 Nov 11  2014 ThirdPartyLegalNotices.doc
-rwxrwxr-x  1 efflandt efflandt 200227 Dec  1 15:31 ThirdPartyLegalNotices.html
drwxrwxr-x  6 efflandt efflandt   4096 Apr 13 01:02 ubuntu12_32
drwxrwxr-x  2 efflandt efflandt   4096 Apr 13 01:02 ubuntu12_64
```
And if steam does not know which (case sensitive) paths are used, it could affect other steam related files within those paths

---

