---
title: "Problem with SSH in Nautilus"
date: 2009-01-26
forum: Desktop Environments
---

### Post by Scanner on 2009-01-26
I have just built a new machine and am running Ubuntu 8.10.  I am unable to connect to my file server using SSH in Nautilus.  I go to file > connect to server and fill out the form setting it to SSH with a server name of emporer directory  of /home/scanman and user of scanman and hit enter, it waits about 5 minutes and then I get an error message that says: 
Could not display "sftp://scanman@emporer/home/scanman".

Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.

I tried deleting the .ssh/known_hosts file and the file in .nautilus/metadata then logging off and logging back in, which appeared in another older post, that didn't help.  I am able to log in at the command line using: sftp scanman@emporer /home/scanman which works fine

The messages in the secure log on the server are:
Jan 26 23:37:09 emporer sshd[8598]: Accepted password for scanman from 192.168.7.10 port 59023 ssh2
Jan 26 23:37:09 emporer sshd[8598]: subsystem request for sftp

And I am able to connect to this sever using nautilus on an older laptop running Ubuntu 7.10 just fine.  I am really stumped here and any help would be appreciated.

---

### Post by _AndY on 2009-01-27
You could give sshfs a go. This allows you to mount a specific location on another machine via ssh.

```
sudo apt-get install sshfs
```

If you mount the directory in /media/ then Nautilus should recognise it and display it in the Places menu as if you'd used "Connect to Server".

You'll need to create the mountpoint manually and set the permissions:
(This only needs to be done once)

E.g.

```
sudo mkdir /media/scanman

sudo chmod a+rwx /media/scanman
```

Then mount the remote dir.

E.g.

```
sshfs scanman@emporer:/home/scanman /media/scanman
```

---

### Post by vinichc on 2011-03-21
I had the same problem... this is a bug with sftp when ssh has some responses...
this FAQ solved my problem

[http://openssh.org/faq.html#2.9](http://openssh.org/faq.html#2.9)

---

### Post by garolou on 2011-03-22
@vinichc
it says "modify your shell initialization"... which is vague to me

What did you do exactly?

---

