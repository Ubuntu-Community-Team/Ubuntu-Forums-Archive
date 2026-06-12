---
title: "help in starting synaptic and apt-get"
date: 2006-03-10
forum: Desktop Environments
---

### Post by melquiades on 2006-03-10
guys,
     let me start by saying that I'm an absolute linux newbie. I tried using synaptic package manager to get some packages. here's the log in my failed attempt to start synaptic.

<snip>

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

</snip>

same thing happens with apt-get. please help.

thanks in advance,
melquiades

---

### Post by dcstar on 2006-03-10
[QUOTE=melquiades]guys,
     let me start by saying that I'm an absolute linux newbie. I tried using synaptic package manager to get some packages. here's the log in my failed attempt to start synaptic.
.......
same thing happens with apt-get. please help.

thanks in advance,
melquiades[/QUOTE]
Unless you have a working (and direct) Internet connection you will get messages like this.

Are you trying to connect through a proxy server?, if so do a forum search for using Synaptic through this sort of connection.

---

### Post by melquiades on 2006-03-10
I log in the internet using dialup; have tried synaptic and apt-get online but no cigar,
produces log attached in my first post.

---

### Post by akiro.yamamoto on 2006-03-11
This is what my Synaptic Repository list looks like.
The other pic is the settings for the 5.10 binary repo.
Compare to yours. 
You can switch to us.archive.ubuntu.com ;)
Some of the servers may be unavailable at the time ( high user vol, maintenace
etc.) .. Or find one close to you.
Then do an update...
And then try to install your app.

---

### Post by akiro.yamamoto on 2006-03-11
This will help generate a sources.list specifically for you ;)
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Hope this helps....

---

### Post by eriefisher on 2006-03-11
When you get this message have you tried to surf or use email, just to confirm the connection is still ok? 

eriefisher

---

### Post by tmart on 2006-03-11
Have just got the same problem on my computer. Tried another computer fresh install Breezy same response. Problem appears to be at Ubuntu end. This wont help at least we are in the same boat.

---

### Post by eriefisher on 2006-03-11
Try changes the country code it could be that the server is down. I would try a mirror just to see if helps.

eriefisher

---

### Post by melquiades on 2006-03-11
thanks for all the help guys. I can't recall where i got the tip but since I tried 
'sudo apt-get update', i had no problems starting synaptic nor apt-get. When 
I edit my sources.list file, the same problem recurs. I tried pressing the reload 
button on the synaptic toolbar and voila! it's up and running again.

---

