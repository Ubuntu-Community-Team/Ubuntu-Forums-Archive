---
title: "sshfs login problem (len too large)"
date: 2006-08-27
forum: Desktop Environments
---

### Post by cjraven on 2006-08-27
Trying to get sshfs to work..2nd Ubuntu Dapper install. The weird thing is the first install (before I broke certain basic stuff and rendered my system unbootable!!) I was able to get sshfs to work flawlessly first time out. I used this howto: [http://myy.helia.fi/~karte/mount_sshfs.html](http://myy.helia.fi/~karte/mount_sshfs.html) which definitely got stuff working. Not so on the reinstall however....
I got sshfs installed, did modprobe fuse, added fuse to /etc/modules, added myself to the fuse group, then a restart (just to be absolutely sure) and then.........

> 
sudo sshfs [email]user@remote.machine.tld[/email]: /mnt/office_server -o allow_other
Password: ^&%$**@
reply len too large: 1315267940


Now this exact procedure funtioned flawlessly the first time, and produced a mounted remote filesystem. Nothing changed on the remote machine, only on my w/s (reinstall as said above) - BUT the ubuntu version is the same (same CD!) and unless some unknown update made a change between Monday and Friday, then the only local change is the reinstall itself.

"len" I speculate is something to do with keylength. But what steps can I take in order to remedy this? /etc/ssh/ssh.config is - as it was the first time out - a stock "out-of-the-box config file", mostly everything is commented out (as it was the first time) and I have not personally edited anything. 

Ideas, suggestions, inspirations...any/all would be most welcome.

](*,)

Regards & TIA
-C

---

### Post by QuantumMechanic on 2006-11-14
I am getting the same problem, and there doesn't seem to be much info out there regarding this. 

The mount option -o max_read=<xxx> doesn't seem to fix anything.

Would also appreciate any help anyone has.

Cheers!

---

### Post by cjraven on 2006-11-15
This isn't the answer by any means, but I accidentally solved this by deleting the .bashrc file on the REMOTE server I was connecting to.

I recreated the .bashrc and was able to replicate the error. I'm speculating that the problem might be permissions related on the remote side, but haven't played with stuff to the point where I can prove that.

The absence of a .bashrc on the remote server is a slight pain-in-the-keester when I login directly to the box, but I sort of muddled through it with extra stuff in .profile, so it's sort of "good enough for now". In pure terms this is not an acceptable answer, but could only be described (at best) as a "workaround".

Regards & HTH,
-Colin

---

### Post by keithweddell on 2006-11-15
Have you tried -o uid=xxxx,gid=xxxx ?  I needed to set these to the uid/gid of the remote user so that I had read/write permissions for their files.  Think I found this in the Ubuntu wiki.

Keith

Edit  - I also put user_allow_other in /etc/fuse.conf but can't remember if this was part of the same problem.

---

### Post by juve on 2007-04-19
The **reply len too large** error occurs because of bogus/greeters printed by the remote server.
I read that:
a) it is fixed in sshfs 1.7
b) deleting .bashrc on the remote host might fix the problem for older sshfs versions

Unfortunatelly egdy and feisty are using sshfs 1.6

---

