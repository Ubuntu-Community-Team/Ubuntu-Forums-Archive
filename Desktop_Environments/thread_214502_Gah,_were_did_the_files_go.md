---
title: "Gah, were did the files go?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Monsuco on 2006-07-12
On my multiboooting PC was working perfectly. I used the information in [this guide](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs) to enable NTFS write support for Kubuntu (and I also used a special driver to enable Windows to read Ext3, the two OS's worked well together). I got it all working great. The only wierd thing was when I went to the system:/media folder, it would claim my disk was mounted elsewere. Well, it was actually mounted at the /media/ folder, so I just used that to access it instead.

Then one day, linux became unable to even see any of the files there. I dont have a clue why, but for some reason it lost support for it. It is still able to see the Fat32 Windows Recovery partion, but not the NTFS partion.

I'll post some screenshots to explain. [here is the system:/media folder](http://www.ubuntuforums.org/attachment.php?attachmentid=12633&stc=1&d=1152740461). Notice the "Kris" partion is not mounted. It for some reason used to tell me it was mounted at the /media/ folder, but now I get the following error
"Could not mount device.
The reported error was:
mount: only root can mount /dev/sda2 on /media/sda2" if I click on it.

If I do "sudo konqueror" to open up a root konqueror and then go to the same area I get the following error instead:
"The KDE mediamanager is not running"

If I go to the /media/sda2 folder (which is were all my Windows partion used to show up" nothing appears. It gives me an empty folder. Any ideas?

---

### Post by granz on 2007-11-14
No idea, ... but I've got the same issue, on two computers. Both dual boot with Win/Gutsy .... working perfectly one day, then..
No icons on desktop, media folder shows the folders (hda1, hda5, hdb1 etc...  ) BUT, they are empty.
Both computers are different, Intel laptop and AMD desktop, It's an Ubuntu issue.
On reboot the laptop 'found' them again (once).. so i never know if I'll have ntfs support or NOT.
Good luck, I'll be watching with interest

---

### Post by granz on 2007-11-14
it 'seems' ...  in my case at least, that the problem was due to Windows not shutting down correctly.
I need to monitor that still, but I'm pretty sure that that was/is the case. After rebooting (into windows[yes it did say it wasn't shut properly last time]) and shutting down again, then rebooting into Ubuntu.... all is as it should be :)
So, it's a Windows issue ... does that mean if Windows fails, I cant get at my files from Ubuntu ???  DAMM

---

