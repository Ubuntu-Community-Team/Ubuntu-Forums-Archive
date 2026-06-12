---
title: "SSH mounting is dropping out and crashing"
date: 2008-12-22
forum: General Help
---

### Post by eludlow on 2008-12-22
I have a directory that I mount a remote file system into, using SSHFS.  I have a script which creates and then removes a directory in the mounted folder every minute so as to hopefully keep the SSH connection alive.

However, randomly the connection still drops out - sometimes it's happened within minutes of the connection being established, other times it can happily stay connected for a few days.

The big problem when this happens is that the directory to which I mount then becomes totally unusable unless I reboot the server.  By unusable, I mean it can't be accessed, changed, removed or anything.  This hasn't been a huge problem (annoyance aside...) all the time I've been at work 5 days a week, but with being about to go on leave for a fortnight, it's going to be a bit more of a pain....don't want to keep SSHing onto the server from the mountains whilst skiing to reboot the server!

An ls -alh shows the following:

```
d????????? ? ?    ?       ?                ? mount

```

Once I reboot it's fine and ownership is back with me.  Have obviously tried editing / removing it as root, but still no luck.

Any idea what is wrong?

Thanks,
Ed Ludlow

---

### Post by cmnorton on 2008-12-24
The following link might not be an answer, but it might give you some areas to explore:

[http://www.linuxquestions.org/questions/linux-networking-3/ssh-connection-timed-out-537296/](http://www.linuxquestions.org/questions/linux-networking-3/ssh-connection-timed-out-537296/)

I would also look at your /var/log/* logs, especially syslog and messages.

---

### Post by eludlow on 2009-01-19
Bumping this up from a while ago - problem is STILL occurring and I'm now getting annoyed of the restart every few days :(

Don't suppose anyone has any new ideas about what's causing it?  Or even how to delete the suspect folder without having to reboot.

*rm -rf mount* as root does nothing - just get a *rm: cannot remove `mount': Permission denied* error.

Ed

---

### Post by hyper_ch on 2009-01-19
did you try umounting?

---

### Post by eludlow on 2009-01-19
No - but just tried and working fine :)

Thanks so much.

Now to script something to reconnect automatically when the connection drops...

Ed

---

