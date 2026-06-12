---
title: "Installing ubuntu-desktop always hangs on xulrunner - 10.04 LTS server"
date: 2013-09-10
forum: Desktop Environments
---

### Post by kingqueen on 2013-09-10
Good evening. I would really appreciate some help if possible.

I have a [kimsufi 2g dedi]("http://www.ovh.co.uk/dedicated_servers/kimsufi_2g.xml") server. It runs various things, but I would like to install a desktop environment and VNC so I can use it as a remote desktop. It has Ubuntu Server 10.04 LTS "Lucid Lynx" on it. 

I have done **sudo apt-get update** && **sudo apt-get upgrade**, but when I do **sudo apt-get install ubuntu-desktop** I know it will get as far as attempting to install xulrunner, and will then hang.

I've tried several times, and tried leaving it for an hour - still it gets stuck at the same place. Re-installing the whole server from scratch doesn't help as the same happens each time. From installation, even before creating a standard user account, I SSH in as root and do **apt-get update**, **apt-get upgrade** and **apt-get install ubuntu-desktop** - and it hangs on installing xulrunner.

Ctrl-C doesn't do anything. If I kill the SSH session, reconnect and log in, I have to delete the lock files before it will let me use apt-get - and then it hangs again when I try to install ubuntu-desktop.

I know xulrunner isn't included in later versions of Ubuntu. Is there any way I can tell apt-get to not install it as part of ubuntu-desktop? Or some other way round it? I have done some substantial configuration on the server now and I don't want to have to re-install from scratch with a different installation image. But I know what will happen if and when I do **sudo apt-get install ubuntu-desktop  **- it'll hang forever on installing xulrunner, apt-get will get in a messed up state and ubuntu-desktop will be in an unusable, half-installed state.

I am somewhat at a loss. Any assistance anybody can bring would be very gratefully received. 

Thank you!

---

