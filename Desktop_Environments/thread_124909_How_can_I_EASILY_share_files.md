---
title: "How can I EASILY share files?"
date: 2006-02-02
forum: Desktop Environments
---

### Post by el3ktro on 2006-02-02
I'm running Gnome both on my desktop and on my laptop, my gf also uses KDE for the next few weeks until she has time to switch. I want to share files between the two, and until now I haven't found a really nice & easy solution to do this. I've tried Samba, SSH & NFS and none works just as I want it.

I've setup Samba via the Gnome utilities, and when I go to "Locations->Connect to server" I can browse all the directories on the remote machine, but when I try to open an OOo document with a whitespace in the filename, I can't open it. I can open filenames with whitespaces in other programs (ghumb, GEdit...) though.

The shared folder shows up in "Locations" and I can browse it with Nautilus, i can also browse it with the "file open dialog" with GEdit for example, but I can't select this share from within a "file save" dialog in GEdit, and when I open a remote file in GEdit i can't change/save it - although I have proper permissions. Why is this?

It seems that OpenOffice doesn't support VFS, and GEdit doesn't support to save to VFS, but it can read from VFS. With Nautilus, I can copy, delete & rename files remotely just fine.

The probems I have with all Linux GUIs is that there is just no easy way to access remote files, especially when the remote connection (a laptop) is not always available. Since both computers are also used by my girlfriend I want to have a really easy solution.

How would you access remote files, so that I can browse & edit them as if they where local with OpenOffice & all the standard Ubuntu applications? I don't care if it is with NFS, Samba, or anything else - it should just work ...


Tom

---

### Post by darth_vector on 2006-02-02
i think a good solution for you would be to set up a remote desktop server on each box (you have an ethernet network right? it will be quite slow otherwise).

---

### Post by el3ktro on 2006-02-02
Ehm sorry I don't understand how that would help me accessing my files on the remote machine!? I don't want to control the remote machine, I want to access the files on it! Or am I just misunderstanding you? :-k 


Tom

---

### Post by lol on 2006-02-02
it's not really what you are looking for, but you could use unison (there is also a GUI, unison-gtk)? This is a very good tool to synchronize files between 2 computers.

The drawback is that it's not exactly the same as sharing, the advantage is that this way you have a backup of your files (they are on both computers). Could be handy if a HD crash...

Otherwise, you can mount a samba filesystem with smbmount. Once the filesystem is mounted, all applications will be able to access them as if they were local files. Same with NFS.

---

### Post by darth_vector on 2006-02-02
[QUOTE=el3ktro]Ehm sorry I don't understand how that would help me accessing my files on the remote machine!? I don't want to control the remote machine, I want to access the files on it! Or am I just misunderstanding you?[/QUOTE]

you are not misunderstanding me. i dont think there is an easy way to edit files accross a network in the manner you are describing. i could be wrong.

if you set up remote desktop you could use ooffice, vim, etc locally on the remote machine to edit files and so forth.

---

### Post by el3ktro on 2006-02-02
Hmm well but we wouldn't be able to work at both computers the same time right? I don't want to use the programs on the laptop from my desktop, I just want to access the files on it - and I also want to do this when my girlfriend is working on the laptop the same time.

I'm just searching for a way to "dynamically" mount the remote directory. The problem with Linux is that all mounts are "static". When the remote directory is not available (laptop turned off) Linux behaves really strange because it constantly tries mounting the remote directory. I worked with KDE previously but i's fish:/ and smb:/ KIOSlaves never really worked for me. I hoped Gnome's VFS was better, but this also doesn't work for me right :-(

Tom

---

