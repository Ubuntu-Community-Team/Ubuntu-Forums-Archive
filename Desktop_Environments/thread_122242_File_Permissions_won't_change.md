---
title: "File Permissions won't change"
date: 2006-01-27
forum: Desktop Environments
---

### Post by Derek Djons on 2006-01-27
Hi all,

Yesterday I've connected a external Microdrive to my Ubuntu installation in order to copy some data on it. But soon I discovered it was Read-Only. Well, I can change the file permissions I thought.
I've used **chmod -R 660 /media/DATA** (it's the name of my external MICRODRIVE). While applying the settings I could already see it wasn't working and all files and folders still maintain there Read / Execute permission instead of Read / Write.

> chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/01. It Was Supposed To Be So Easy.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/02. Could Well Be In.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/03. Not Addicted.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/04. Blinded By The Lights.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/05. Wouldn\'t Have It Any Other Way.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/06. Get Out Of My House.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/07. Fit But You Know It.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/08. Such A Twat.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/09. What Is He Thinking.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/10. Dry Your Eyes.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/11. Empty Cans.mp3': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/AlbumArtSmall.jpg': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/AlbumArt_{148A2311-06CA-4E2B-AA42-DA3D46BB092B}_Large.jpg': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/AlbumArt_{148A2311-06CA-4E2B-AA42-DA3D46BB092B}_Small.jpg': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/desktop.ini': Read-only file system
chmod: changing permissions of `/media/MICRODRIVE/The Streets - A Grand Don\'t Come For Free/Folder.jpg': Read-only file system
djons@voyager:~$


I've also checked the user rights using **chown -R**. But probably I'm overlooking something. The Microdrive is partitioned with NTFS.

---

### Post by rgrig on 2006-01-27
Some filesystem drivers mount read-only by default because the write support is experimental. The NTFS one is such a case.

---

### Post by Derek Djons on 2006-01-27
[QUOTE=rgrig]Some filesystem drivers mount read-only by default because the write support is experimental. The NTFS one is such a case.[/QUOTE]

Great :) Let's thank Microsoft for being such a great pal and patanting, claiming NTFS and FAT for itself. Thanks for the heads-up so far. I'll boot a Windows box in order to reformat the microdrive to FAT32.

Thank you.

---

### Post by Derek Djons on 2006-01-27
I've converted my Microdrive to FAT32 and I am able to change the permission using the right mouse button. But funny thing is I am only able to change the owner permissions. When I try to change the Group and Other permissions I am suddenly not the owner. Also using chmod and chown doesn't helps.

Anyone know what I'm mocking up? :)

---

### Post by ezsit on 2007-02-08
> I've converted my Microdrive to FAT32 and I am able to change the permission using the right mouse button. But funny thing is I am only able to change the owner permissions. When I try to change the Group and Other permissions I am suddenly not the owner. Also using chmod and chown doesn't helps.

Anyone know what I'm mocking up? 

AFAIK, FAT, FAT32, and NTFS do not support unix style file permissions. Your drive needs to be formatted a native linux filesystem, such as ext2, ext3, XFS, JFS, or Reiser for the full unix style file permissions to work.

---

### Post by greg73654 on 2007-10-04
OK, I'm using apache to run my web server, but I need 2 folders to be writable I've changed the owner of the folder to my username, but it won't let me change them to read/write... What's up?

(If you wanna know the permissions so far no the folder is rwxrwxr-x, I reall just need that last write...)

---

