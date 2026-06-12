---
title: "sync LG Phone - Evolution"
date: 2009-04-12
forum: General Help
---

### Post by chipppy on 2009-04-12
I am trying to sync a LG Renoir KC910 to evolution in Gnome with Ubuntu 8.10 installed.

I am using a few different information sources both LXF 115 Feb2009 
From here I worked through and added the following packages via Synaptic
[B]synce-sync-engine
synce-trayicon
synce-hal
synce-gnomevfs
multisync
synce-gdm (this is the typo mentioned further down)
opensync-plugin-synce
opensync-plugin-file
opensync-plugin-evoltuion[/B]

I couldnt find **synce-gdm**.  Following a quick search of the web I found a thread mentioning that it was a typo and that lead me to  [http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice]("http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice")
Which is where the following step through comes from.

I carried out the additions to the software sources and reloaded.  Came up with the error of.
[I]
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D[/I]
so reading further down guide found that it recommended to run the following from terminal
[B]
**@****:~$ sudo apt-key adv --recv-keys --keyserver subkeys.pgp.net 7D2C7A23BF810CD5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver subkeys.pgp.net 7D2C7A23BF810CD5
gpg: requesting key BF810CD5 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error[/B]

still no luck but I noticed the difference in the Hex numbers so change the guide hex number to the one from the error message and ran from terminal. 
[B]
sudo apt-key adv --recv-keys --keyserver subkeys.pgp.net B152F042D246C25D[/B] 

same as above but using the different Hex Number

Anyway tried the next step
[B]
****@****:~$ sudo apt-get install synce-hal librra0-tools librapi2-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package librra0-tools is a virtual package provided by:
  librra-tools 0.13-0ubuntu0~ppa1~intrepid1
You should explicitly select one to install.
E: Package librra0-tools has no installation candidate[/B]

At this point I noticed that there was the little orange sun thing in the top right coner of my desktop saying that there was 9 updates available.  Ran update manager and it came up with
*'Not all updates can be installed, run a partial update'* error.  Which I did and it tried to install all the  bits from LXF115 that I added through Synaptic, BUT
[I]**Error authenticating some packages**

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.[/I]
I found another thread. Via another www search,[http://ubuntuforums.org/showthread.php?t=136257]("http://ubuntuforums.org/showthread.php?t=136257")

and it looks to do the same things as above so I look to be still buggered by the Public Key problem.  I read through the thread and got very confused when people started talking different problem with different Distros (Im a newbie)

I am assuming that this is due to the earlier error/problem with the Public Key.

And this is where I cam to a screaming halt.  
From what I can figure out I need to sort out the Public key problem before I can continue.

Anyone/guru have any idea how to do get the correct Public key in order to get the required updates to work?
Or any other suggestions

Cheers
chipppy

---

### Post by rlogan on 2009-12-17
Just wondering if you got your phone to sync to your Ubuntu install, I have the same phone and using Karmic now. It would be nice to have it syncing but must admit I have not tried to

Cheers

Richard

---

### Post by marshag63 on 2009-12-17
Try googling bit-pim for linux.


MarshaG.

---

