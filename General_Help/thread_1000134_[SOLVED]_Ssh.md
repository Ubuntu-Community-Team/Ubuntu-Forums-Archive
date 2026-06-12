---
title: "[SOLVED] Ssh"
date: 2008-12-02
forum: General Help
---

### Post by IHATEDLINK on 2008-12-02
OK, here's the deal:
I've got a first-gen jailbraked iPod touch running on the latest firmware (2.2).
I use a P2P app ([MewSeek]("http://www.errrick.com.ar/?p=54")) for my on-the-go music needs (before you get all legal, iTunes music downloads aren't available on my country, this is the only way I can get music downloads). This is very cool except for a tiny detail: the music doesn't sync-back to my computer. I usually use a graphical SFTP client for syncing back stuff on Windows (WinSCP), but I couldn't find a better chance to learn some stuff on terminal.
I SSHed onto my iPod using [this guide]("http://gizmodo.com/gadgets/guide/short-and-sweet-ssh-guide-for-the-iphone-300323.php") and then used a [quick tutorial]("http://www.tuxfiles.org/linuxhelp/fileman.html") for basic terminal inputs (ya know, moving, copying, deleting, replacing files and stuff...) 
Anyways, this worked amazingly fine for working with files *inside* my iPod, but I didn't had much luck getting stuff out.
So I was kinda hoping you guys could help me out here... :)

Here's what I achieved: (the files I want to get are in .../Media/Downloads
```
paco@Paco-Ubuntu:~$ ssh root@192.168.1.102
root@192.168.1.102's password: 
Paco-s-touch:~ root# cd /var/mobile/Media/Downloads
Paco-s-touch:/var/mobile/Media/Downloads root# 
```

Soo, yep, that's pretty much it: I can move files around on the device, but can't get them out... PLEASE HELP! :)

Thanks in advance..

---

### Post by dexter on 2008-12-02
Try something like this from your ubuntu computer:
```
scp root@192.168.1.102:/path/to/your/file/you/want/to/copy /destination/directory
```

Replace the paths with their custom values, You can even copy whole directories using the -r flag. See the scp man page for more details.

---

### Post by IHATEDLINK on 2008-12-02
```
paco@Paco-Ubuntu:~$ scp root@192.168.102: /var/mobile/Media/Downloads copy -r /home/paco
ssh: connect to host 192.168.102 port 22: Connection timed out
cp: cannot stat `/var/mobile/Media/Downloads': No such file or directory
cp: cannot stat `copy': No such file or directory
cp: missing destination file operand after `/home/paco'

```

:S, It seems weird to, I mean, I usually have to enter a password for accesing the device...
Oh, and is "copy" a normal command? I was told to use "cp" instead.

---

### Post by ilrudie on 2008-12-03
scp -r root@192.168.1.102:/var/mobile/Media/Downloads /home/paco
                  
scp is secure cp which uses the ssh (secure shell) protocol to "cp" files between different computers.

---

### Post by IHATEDLINK on 2008-12-03
> **ilrudie said:**
> scp -r root@192.168.1.102:/var/mobile/Media/Downloads /home/paco
                  
scp is secure cp which uses the ssh (secure shell) protocol to "cp" files between different computers.

It worked great! thanks A LOT!!

---

### Post by deadowl on 2008-12-03
You can also run the command sftp root@192.168.1.102
I would, however, recommend sftp paco@192.168.1.102

Sftp allows you to browse both folder trees and gives you the ability to move files between devices.

Do it with a GUI:
Go to the places menu
Click "Connect to Server..."
Select SSH fom Service type
Input 192.168.1.102 to the server field

---

### Post by IHATEDLINK on 2008-12-03
> **deadowl said:**
> You can also run the command sftp root@192.168.1.102
I would, however, recommend sftp paco@192.168.1.102

Sftp allows you to browse both folder trees and gives you the ability to move files between devices.

Do it with a GUI:
Go to the places menu
Click "Connect to Server..."
Select SSH fom Service type
Input 192.168.1.102 to the server field

Thanks A LOT men... I forgot how everything was actually built-in on the OS... Anyways I wanna learn more terminal stuff so you'll see me again asking for stuff...

---

