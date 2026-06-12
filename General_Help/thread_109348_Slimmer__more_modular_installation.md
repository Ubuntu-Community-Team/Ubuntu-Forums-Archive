---
title: "Slimmer / more modular installation"
date: 2005-12-28
forum: General Help
---

### Post by runlevel0 on 2005-12-28
I'm just upgrading my 3th box from Gentoo to Kubuntu 5.10. I have had a lot of errors, because the CD driver and the MB doesn't seem to cooperate quite nicely (It's an older Intel PIII board and the drive is a newer Phillps CDROM drive). 

I have already had many similar experiences with older/b0rked hardware and the install disc which *always* runs is Gentoo's.
That's because it's very light weight and having less to install means less possibilities of errors or less time if you have to reinstall.

Unfortunately Gentoo's install disc lacks lot of functionality and requieres you to be present during the install.

That's one of the reasons I changed to Debian based systems: I changed my other two machines in a breeze, trying even Ubuntu/Gnome and switching to Kububtu w/o a single problem and in a minimal fraction of the time I needed to compile all the stuff myself.

As I said I was having lot's of problems, so I was trying to install the 'server' setup and later install everything from the repostories.
During this process I saw that there was a lot of software being installed which is not necessary in a minimal system such as klibc, DHCP (even when you set the netcfg/dhcp_enable=false option at boot), XFS supprot, ReiserFS support, GCC and lot's of stuff nobody will surely need in a basic system. There is on the other hand a lack of certain important software, such as SSH support.

I know that there are options to jump to a menu like the one in the vanilla Debians and also a component chooser menu, but I havn't figured out how to get to them except after an error.

IMHO, it would be interesting to have a really *minimal* system, with just a kernel, network, SSH (of course), NFS a running APT and an editor. Just that. So that when you need to fight against pesky hardware you can have a little linux that you can connect to the rest of the network v&#237;a SSH or mount a local repository via NFS... and install the rest from the internet.

Or at least an option to easily access the Debian-alike menus and component chooser menu.

---

