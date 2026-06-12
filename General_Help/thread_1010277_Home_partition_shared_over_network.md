---
title: "Home partition shared over network"
date: 2008-12-13
forum: General Help
---

### Post by TripitakaUK on 2008-12-13
I have a main PC running Hardy (hardy-svr) which has my main /home location in a separate partition. I also have a laptop (hardy-dell).

When I boot the laptop, I'd like it to use the /home partition from the server. I seem to recall that it was possible but I cannot find how to do it despite much googling. I must be using the wrong terms.

Can anyone tell me how or point me to a how-to?

Thanks.

---

### Post by tigerstripedcat on 2008-12-13
I can't remember the specifics--I always have to look it up too--but if you're doing linux-linux you want to use nfs, if you're doing linux-windows you'll want to use samba (and use the new cifs).  Since it sounds like you want to use the former you'll need to:

1) Make sure your laptop can see your desktop over the network (can you ping the machine? can you ssh over to it, if it has that installed, the ip is probably 192.168.XX.XX, you'll have to run ifconfig on the other machine to get this)
2) Set up nfs (sudo apt-get install nfs?)
3) make a mount point (mkdir /home/laptopmount)
4) Set up /etc/fstab to reflect this mountpoint as nfs
[http://tldp.org/LDP/nag2/x-087-2-nfs.mountd.html](http://tldp.org/LDP/nag2/x-087-2-nfs.mountd.html)

5) then mount
mount /home/laptopmount

TSC

---

### Post by TripitakaUK on 2008-12-14
Thanks for this. It's now working OK although the wireless connection is giving some issues - thats a separate matter.

Is it normal not to see the nfs network shares under "Network Servers" in Nautilus?

---

### Post by TripitakaUK on 2008-12-15
An update to this:

When I load the nfs server share /home/user on the laptop through fstab, it causes problems on the laptop, most immediately recognisable as programs not starting. If I start Firefox or Synaptic for example, it tries to start then exits.

Any ideas?

Permissions seem OK - I can create, change and delete files in the mounted /home/user directory.

Edit: I need to make clear - I am mounting the nfs server share /home/user as /home/user on the laptop. All drives are ext3.

---

### Post by tigerstripedcat on 2008-12-22
Do you have a user that uses /home/user on your laptop?  You need to create a mountpoint that doesn't conflict with the current one, so if you have the user "imthuser" on both the server and laptop you can't mount  /home/imtheuser on the laptop because it will conflict with the local files on the laptop.  you need to create something like /home/user/theserver as the mount point.  Once mounted, the directory will look like your files on /home/imtheuser on the server.

Hope this helps
TSC

---

### Post by TripitakaUK on 2008-12-22
I guess that is the problem.

The user on the server is /home/mark. The laptop current home is /home/mark.

What I want to do is log on to the laptop and have the server version of /home/mark mounted as the laptop home directory.

---

