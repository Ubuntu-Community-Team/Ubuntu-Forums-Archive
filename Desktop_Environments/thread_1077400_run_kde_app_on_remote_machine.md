---
title: "run kde app on remote machine?"
date: 2009-02-22
forum: Desktop Environments
---

### Post by kasper22 on 2009-02-22
Hi,

I have a htpc in another room that I'm ripping my DVDs on (using k9copy), but it's a real hassle to get up every 10 - 20 minutes and check on the progress.  So my first solution was to use vncserver, however as soon as I tell k9copy to copy the disk, the vncserver crashes.  So that is no good.  

Now I'm trying to find another method, where I can monitor progress without having to get up until the rip is done.  One idea I had was to run the application on a remote display.  The how to said to do something like this:

[LIST]
[*]On the machine I'm at run: xhost + (I'm being lazy and just opening everything for now)
[*]On remote machine run: DISPLAY=remote.domain:0 k9copy &
[/LIST]
This seems close except I get a message "could not connect to x ...", and both machines are running xfce ubuntu.

Anyone know if I'm close on the idea above, or if someone has another idea I'm all ears.

Thanks,
Bryan

---

### Post by kasper22 on 2009-03-01
I'm really surprised no one had an answer on this.  It turns out to be super simple.

On remote computer make sure in /etc/ssh/sshd_config you have X11Forwarding on: X11Forwarding yes

Then on the machine you are sitting at ssh as such:
```

ssh -X remote.address appToForward

```

From what I read it is not very secure to have X11Forwarding just on, so if your machine is open to the internet you might want to do a little research into securing the forwarding.

Bryan

---

