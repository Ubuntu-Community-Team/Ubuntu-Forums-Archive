---
title: "Basic Help"
date: 2005-10-24
forum: Desktop Environments
---

### Post by ~EN~ on 2005-10-24
Im new to Linux and I have read the guide, which is very helpful by the way, but i still cant get some things working (i.e. BitTorrent) I have tried to use the guide but keep getting errors and it tells me to run update so i do and this is the output and it still tells me to run the update :

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


I have done the respoitories and everything else i can think of, please help thank you.

---

### Post by Kyral on 2005-10-24
Hoary-Backports is no longer on Mirrormax, thats why.

Change the "http" line to "http://archive.ubuntu.com"

UbuntuGuide is out of date. Use [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation) instead

---

### Post by ubuntu27 on 2005-10-24
If you have Ubuntu Breezy, try this:

Add this to your repository:

To edit your Repo, open the Terminal (Epplications menu / Accesories / Terminal )

and then type this: sudo gedit /etc/apt/sources.list

It will open a Text editor. Copy and paste the following. [Delete what you had ebfore]

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
 
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
 
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
 
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
 
deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main restricted universe multiverse

### Backports
#deb http://ubuntu-backports.mirrormax.net/ breezy-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main universe multiverse restricted

```

Then save it, and close. That should solve your problem ;)


EDIT: Now that I think.... taking a closer looka t your post... Are you using Hoary or Breezy?  The solution I gave you is for Breezy.

---

### Post by Nevyn on 2005-10-31
I installed Ubuntu yesterday an have been experiencing something similar as the thread-starter described. I followed ubuntu27:s method, stated above, and now I cant use the "add application" function anymore. A try to install xmms resulted in this error:
"Application 'xmms' not available
The application can not be found in your archive. This usually means that it is not available for your hardware platform"

Odd message, having an Intel Pentium 3GHz with 1Gb RAM and tons of free disk space.

Thankful for helping response.

---

### Post by Nevyn on 2005-10-31
I'm not sure following message will help at all. I'm a _very_ fresh newbie. I can not guarantee the stuff below is correct. Feel free to ignore it :smile: 

Concerning my problem with xmms, I solved it by deleting whatever was in my /etc/apt/sources.list and copied the code from [this web page]("http://www.psychocats.net/linux/sources.php") right off, saving and closing, adding xmms by the "Add application" in Applications-menu.

What ubuntu27 describes in his previous post is how to open backports. An advanced Debian-user friend of mine (Ubuntu is based on Debian) said that the backports are not yet available in Ubuntu. That would make ubuntu27's method unusable.

Again, not sure if this is correct.

---

