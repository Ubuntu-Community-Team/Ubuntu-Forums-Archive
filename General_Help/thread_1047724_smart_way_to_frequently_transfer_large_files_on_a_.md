---
title: "smart way to frequently transfer large files on a home network?"
date: 2009-01-22
forum: General Help
---

### Post by evencoil on 2009-01-22
in my new home network setup I'm going to be frequently backing up a large media collection from one computer to another via computer 1 (wireless) --> wireless router --> computer 2 (physically plugged into the router).

speed of file transfer is important.
security not really that important.


I was going to use NFS for this, but then I realized that I'm only choosing that because that's all I know of :). So is that a good option? Or are there other approaches that would be better? Thanks!

---

### Post by tmetzcc325 on 2009-01-22
NFS should be okay if both boxes are running Linux.  If you are using Windows, you'd need Samba.  Are you simply copying the files so they can be accessed from both machines, or is this for the sole purpose of backup?  If you are just trying to create backups, I highly recommend you install and use sbackup.  I've been using this for a few weeks, and it works well.  It has the capability to do full and incremental backups to remote servers (either over ftp or ssh; I use it over ssh, which is probably overkill since both boxes are on the same network).  The difference is that it creates giant tarballs of your data, so if you'd like to, say, play a music file that you copied to box 2, you'd first need to un-tar it.

I know that is more detail than you were asking for, but hope it helps.

Tom

---

### Post by evencoil on 2009-01-22
they are both linux machines and I would like to be able to access the files from both machines, so sbackup is not what I'm looking for. (although I do use it for other things and like it quite a bit.)

do you know what type of speed I should be expecting from NFS? I have my NFS set up but haven't really looked into tweaking it at all. According to rsync files are transferring at about 1.3 MB/s.

---

### Post by tmetzcc325 on 2009-01-22
That is better than I get.  I have the same setup, where one computer is wireless, and the other is plugged right into the router, and I usually get well less than 1MB/sec.  It probably isn't ideal, but it works well enough for me that I am too lazy to look into it.  Now I know I have a lot of interference in this apartment building, which no doubt contributes to the speed issues.  Hopefully someone else out there can help you out, though.

---

### Post by evencoil on 2009-01-22
Well I didn't know if that's fast or slow. Maybe it's already as good as its going to get :). One option I did add in my /etc/fstab was rsize=8192,wsize=8192 for the mounting options. These are supposed to affect the speed but then (this is all according to nfs.sourceforge.net) you are supposed to do some diagnostics to find out what the right value of these are for your setup. I didn't do that. You might want to try it out though.

---

### Post by donkyhotay on 2009-01-22
I just use FTP for my network. If you are at all familiar with the CLI then proFTP is a snap to setup a server with. If you want to get really fancy you can then also configure apache so that you can then download files through a web browser making it easier if you are sending files to lots of different people on the network. I just use FTP both ways though since I'm generally the only one on my network. Speed is pretty good but then again I have gigabit ethernet on most of my systems. (c:

---

### Post by evencoil on 2009-01-22
oh i forgot to add something; i want to be able to use rsync with whatever solution.

can i do that with proFTP?

---

### Post by grndslm on 2009-01-22
nfs or sshfs

---

### Post by tmetzcc325 on 2009-01-22
Well, I don't believe you'd need rsync for ftp, since ftp is a protocol in and of itself.  For ftp, I use vsftp, which was pretty easy to set up (but again, that is only for a couple users, I don't have any virtual users or anything like that, since it is just on a home network).

If you plan on opening ports to the outside world (for ssh at least, have yet to figure out how to set it up for ftp) then I highly recommend you install denyhosts, which helps defend against brute-force attacks.

---

### Post by Yashiro on 2009-01-22
Use NFS. Running ftp servers on all clients is not a good idea.

---

### Post by evencoil on 2009-01-22
well I want to use the synchronizing abilities of rsync and using an ftp protocol doesn't seem like that would work.

anyway, looks like nfs is the winner. thanks for all the input.

---

### Post by yther on 2009-01-22
I would think rsync the ideal tool for this, especially if your transfer is always going to be [Computer A] --> [Computer B].  Rsync would only transfer the differences between them, so when you add new files on A they would be transferred, but not the old files.  So, your first backup would take a long time, but successive ones would take a fraction of that.

As far as I know, you just need to set up an rsync daemon on the machine that will be receiving the files (B in my example above), then run the client on the sending one (A).  Rsync is designed to work across a network, so you would not need NFS for this task.

---

### Post by evencoil on 2009-01-22
oh really, I didn't know that. I figured that I needed either SSH or NFS set up to be able to use rsync. I'll look into that, thanks!

---

### Post by Yashiro on 2009-01-22
rsync for scheduled backups/terminal fiends.
NFS for drag and drop in the gui.

---

