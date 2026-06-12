---
title: "Can't play media from a share"
date: 2013-03-09
forum: Desktop Environments
---

### Post by Pikazzo on 2013-03-09
Hello xubunters, I'm new to this game and Im trying to understan (little by little) how Linux works. I work with Microsoft sience DOS so I don't get any idea of commands or anything.
Just to start to learn some more yesterday I've installed Ubuntu 12.10 to an old Thinkpad (Pentium 4 with 380MB RAM) and then I figured out (with forums help) how to install Xubuntu from the console.
That's the good thing because then I can see the desktop and start to work with the computer (Ubuntu doesn't work, apparently Unity bar has more requirements to run)
So basically figured out how to use Gigolo and connect to my NAS (WD Book Live) to get to the Public folder. The thing is I can see the files there BUT, if I tri to double click them everything hangs up. I have to restart the computer to work again.

Then I tried VLC player and something new happened, If I try to double click an MP3 from the Share, VLC put it on the playlist but don't reproduce it.
BUT! if I drag and drop the flie from the File Manager to VLC it plays well.... the anoying thing is that I can't drag and drop entire folders I must do it only with files.

Tried XBMC aswell and weird thing is: It can see the NAS drive using NFS protocol, nos SAMBA. But XBMC can get to the Public folder and even navigate on folders but when you enter on a folder with media files it HANGS UP.

Bottom line is, I cannot play from my NAS. Can anyone suggest me something else to try? because Im running out of ideas :s

Thanks a lot!

---

### Post by tgalati4 on 2013-03-09
Does your NAS have uPnP or DAAP protocols running?  See if you can turn them on and then run rhymbox or banshee.  The music shares should show up and play.

---

### Post by Pikazzo on 2013-03-11
Thanks Tgalati4 ! I know that the router has that protocol running yes but on the webconfig of the NAS didn't mention any uPnP protocol to check. 
Anyway I tried for hours to make it work and I did, there were strange things in fact because I made XBMC to read the NAS using the Search option via Samba and I can reach it (Music)
But with the Video path when I selected Samba "no resource" appeared.
So, finally input SMB://192.168...... all the path in that format, on Video and WORKED!
Music was reached by XBMC using the search button with Samba and worked aswell so... I don't know why or what I did but XBMC plays both formats now... strange issue.

Thanks again for the reply!

---

