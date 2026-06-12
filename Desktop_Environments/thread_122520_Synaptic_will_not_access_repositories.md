---
title: "Synaptic will not access repositories"
date: 2006-01-27
forum: Desktop Environments
---

### Post by billchivers on 2006-01-27
Synaptic will not access repositories

Hello again,

My second post and another request for help. I use Ubuntu 5.10 and of course synaptic (V0.57.4). All was working until I tried to use Synaptic at my workplace, which is behind a proxy server.

The problem is that Synaptic cannot get past the proxy. During installation of Ubuntu 5.04 this resulted in a 45 minute wait and no repositories configured (I have not tried to install 5.10 at work). With 5.10 properly configured on my notebook (I installed it at home, with a simple direct broadband connection) I tried to use Synaptic at work yesterday but I could not---changing the proxy settings to use our proxy and using ports 8080 and 3128 did not work.

So today, at home, I set the proxy setting in Synaptic back to "Direct connection to the Internet" which has always worked at home, and it is no longer working at home! I get the following messages:

When I click "Reload":
----------------------
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) MD5Sum mismatch
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) MD5Sum mismatch
[http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

Then when I click close
-----------------------
The following problems were found on your system:

W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

HELP! I am not a Linux guru, just a Linux user. I really need a computer that works, so that I can get on with my teaching and research. The place where I work is a committed Microsoft shop, very Linux-phobic. Whenever I contact the help desk, they tell me that I should not be using Linux, even if I ask for proxy settings. 

All other applications, such as Firefox, work though the proxy. Firefox auto-detects the proxy so I do not have to change settings at home.

Sorry if I sound stressed, but I am. This problem is a real killer for my use of Ubuntu at work. And, if I cannot fix it at home then I will have to re-install, which takes a long time as I use extra packages such as latex which total over 200Mb downloads!

Many thanks,

Bill Chivers

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=billchivers]Synaptic will not access repositories

Hello again,

My second post and another request for help. I use Ubuntu 5.10 and of course synaptic (V0.57.4). All was working until I tried to use Synaptic at my workplace, which is behind a proxy server.

The problem is that Synaptic cannot get past the proxy. During installation of Ubuntu 5.04 this resulted in a 45 minute wait and no repositories configured (I have not tried to install 5.10 at work). With 5.10 properly configured on my notebook (I installed it at home, with a simple direct broadband connection) I tried to use Synaptic at work yesterday but I could not---changing the proxy settings to use our proxy and using ports 8080 and 3128 did not work.

So today, at home, I set the proxy setting in Synaptic back to "Direct connection to the Internet" which has always worked at home, and it is no longer working at home! I get the following messages:

When I click "Reload":
----------------------
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) MD5Sum mismatch
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) MD5Sum mismatch
[http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

Then when I click close
-----------------------
The following problems were found on your system:

W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

HELP! I am not a Linux guru, just a Linux user. I really need a computer that works, so that I can get on with my teaching and research. The place where I work is a committed Microsoft shop, very Linux-phobic. Whenever I contact the help desk, they tell me that I should not be using Linux, even if I ask for proxy settings. 

All other applications, such as Firefox, work though the proxy. Firefox auto-detects the proxy so I do not have to change settings at home.

Sorry if I sound stressed, but I am. This problem is a real killer for my use of Ubuntu at work. And, if I cannot fix it at home then I will have to re-install, which takes a long time as I use extra packages such as latex which total over 200Mb downloads!

Many thanks,

Bill Chivers[/QUOTE]

What kind of proxy server do you have at work?  Does it use basic authentication or NTLM?

---

### Post by dcstar on 2006-01-28
[QUOTE=billchivers]Synaptic will not access repositories

Hello again,

My second post and another request for help. I use Ubuntu 5.10 and of course synaptic (V0.57.4). All was working until I tried to use Synaptic at my workplace, which is behind a proxy server.
.......
Sorry if I sound stressed, but I am. This problem is a real killer for my use of Ubuntu at work. And, if I cannot fix it at home then I will have to re-install, which takes a long time as I use extra packages such as latex which total over 200Mb downloads!

Many thanks,

Bill Chivers[/QUOTE]
Have a look at these:

[http://ubuntuforums.org/showthread.php?t=111773&highlight=synaptic+proxy](http://ubuntuforums.org/showthread.php?t=111773&highlight=synaptic+proxy)
[http://ubuntuforums.org/showthread.php?t=103449&highlight=synaptic+proxy](http://ubuntuforums.org/showthread.php?t=103449&highlight=synaptic+proxy)

---

