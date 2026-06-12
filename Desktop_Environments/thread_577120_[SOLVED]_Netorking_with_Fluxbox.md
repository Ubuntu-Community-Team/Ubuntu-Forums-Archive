---
title: "[SOLVED] Netorking with Fluxbox"
date: 2007-10-15
forum: Desktop Environments
---

### Post by ghandi69_ on 2007-10-15
Ok guys, I live in a college home, with 6 computers (4 windows XP machines, 2 ubuntu machines with fluxbox.) that are all connected through a router.  The two ubuntu machines, are of course, mine.  I would like to be part of the same workgroup to be able to share files and printers easily with the rest of my roommates, but I have been having some issues, so I am open for suggestions.

I have been trying to install samba on both of my machines, but that seems to require my roommates to have to 'map' a network drive to their machines, and also to have a user name and password, I would like for them just to be able to go to 'View WorkGroup Computers', and then see mine, and then browse my files without having to have a password of any kind.  

My other question is, I do use thunar, and I was wondering if there is anyway to browse network folders with thunar?  I was hoping I would not have to install nautilus to do this but it seems like the only way as of now.

---

### Post by mysurface on 2007-10-15
You can mount your remote host through samba, after mounting it, you can access it with thunar, [example here]("http://linux.byexamples.com/archives/101/mount-a-samba-point/").

---

### Post by TeaSwigger on 2007-10-16
Hello, there's a thread at these very forums which helped me immensely in setting up a home network:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Note the part 2, about Windows and WINS server business. Once that was done I no longer had to map the drive etc.

Networking was by far the most frustrating part of my home setup experience. KDE can spoil one - Konqueror at least uses a smb:/ protocol so that you don't have to mount the shares. Eventually I've managed a permanent mounted network - which I can easily use in a lighter regular file manager like Thunar or the even faster ROX, PCmanFM etc, but phew. The clues were all in that thread, it just took me a while to sort it all out.

---

