---
title: "Update manager spinning forever"
date: 2012-03-05
forum: Desktop Environments
---

### Post by iceback on 2012-03-05
I'm new to 11.10 (GNOME) and Update Manager shows new updates available but clicking install button sets the screen grey and spins forever.  Never asks for password, never downloads, not killable from task-bar (if that's the term for the suite of icons on the left) icon titled "Update Manger". Not happy.

---

### Post by 2F4U on 2012-03-05
Have you ever been able to install updates before? Did you try opening a terminal and entering

```
sudo apt-get update
sudo apt-get upgrade
```

Please make sure that neither Update Manager nor Software Center are open.

---

### Post by cortman on 2012-03-05
```
sudo update-manager stop-spinning
```

jk.

To run the commands given by 2F4U you'll have to exit the Update manager. Either reboot or run

```
ps -ef | grep -i update
```

and kill the update manager processes, with

```
sudo kill -9 process_id
```

The process ID is the number in the second column from left.

---

### Post by iceback on 2012-03-05
Nice one (stop-spinning).  Came close to trying that!

But sudo apt-get update did get me further.  At least now I see an error message which I couldn't find in /var/logs.  

... 
```
Get:22 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [60.0 kB]
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Fetched 1,220 kB in 4s (247 kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 52A794126E3AB2D3

```

Are my source url's scrogged?

---

### Post by cortman on 2012-03-05
Looks like a very common GPG error. There's instructions in this [blog post]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/") on how to fix them.

---

### Post by iceback on 2012-03-06
I popped over to the blog reference and walked those steps, but both plans left me wanting.

For apt-get update I got (short form)

Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 52A794126E3AB2D3


For apt-key adv –keyserver keyserver.ubuntu.com –recv-keys 52A794126E3AB2D3 I got:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.FIfkm1Whzf --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg –keyserver keyserver.ubuntu.com –recv-keys 52A794126E3AB2D3
usage: gpg [options] [filename]

```
Do I have the wrong apt-* components?
apt-get --version --> apt 0.8.16~exp5ubuntu13 for amd64 compiled on Oct  6 2011 15:33:19

---

### Post by cortman on 2012-03-06
Not so good. Have you tried changing your repository mirrors? You can do this by going to System Settings>Software Sources> and changing the "Download from:" to a different server.

---

### Post by iceback on 2012-03-06
Not sure about those resources.  I am on-line with synaptic working well. My problem seems to be this key value:52A794126E3AB2D3 not being correct for "http://ppa.launchpad.net oneiric Release".  I've added oneiric to my list of suppliers.

---

### Post by cortman on 2012-03-06
> **iceback said:**
> Not sure about those resources.  I am on-line with synaptic working well. My problem seems to be this key value:52A794126E3AB2D3 not being correct for "http://ppa.launchpad.net oneiric Release".  I've added oneiric to my list of suppliers.

How about commenting it out in /etc/apt/sources.list, then running apt-get update, then uncommenting it again?

---

### Post by iceback on 2012-03-06
Commented out both lines in /etc/apt/sources.list.d/jconti-gnome3-oneiric.list and that appears to have done the trick.
apt-get update; apt-get upgrade both went swimmingly.

THANKS A TON

The obvious question is what's up with the launchpad site (or my installation vis. that site)?

---

### Post by cortman on 2012-03-06
Glad that worked. I guess I'm not sure where the error is. You could try re-adding the repository in Synaptic, which should load a current key along with it, but anyway.
Oh, and if you would mark this thread as [SOLVED] we'd be obliged.
Cheers!

---

