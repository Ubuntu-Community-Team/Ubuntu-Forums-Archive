---
title: "slow disk acces/nautilus in Hardy"
date: 2008-05-16
forum: Desktop Environments
---

### Post by jbtito03 on 2008-05-16
After upgradeing to Hardy my Nautilus is doing very slow whet strating up. For example, i get a mail with an attachement and try to save the attachement the programm freezes for 10 sec. and then gives me the nautilus window. 

Same happens with every program, that acceses the drives (open office, dia, etc.)

I  can not get any log info, as the system does not log anything in that period. 

My installation was not a clean install - i upgraded from 7.10 to 8.04 via update manager.

Any ideas?

Cheers

JB

---

### Post by jbtito03 on 2008-05-19
Hi

still having the same problem. Noone else? Any ideas?

Cheers

JB

---

### Post by shivagit on 2008-05-20
Sorry to say I'm having a similar problem with Nautilus on my 7.10 gutsy system.  It started after an in-place upgrade from 7.04 feisty fawn.  If I Alt-F2 and run gksudo nautilus, it's much faster.  Does anyone know what direction to begin looking into this?  I saw several threads that re-installed nautilus , but continued to have the problem.

---

### Post by dulus on 2008-05-20
I had similar problem but when I created new user and logged in there were no such slowdnown issues. So problem is somewhere in configuration files and directories, they begin with "." (normally hidden files, use ls -la). Then I logged back to my login, deleted all files and directories  beginning with ".", ctrl+alt+backspace and logged again. I lost some desktop and apps settings but nautilus runs now without slowdowns.

---

### Post by shivagit on 2008-05-21
Thanks for the ideas - I did try uninstalling Nautilus as well, wiping out my .nautilus directory and re-installing.  It was still about 30 seconds to open Nautilus.  I went on to other things and may have found the source of my issue and maybe others.  I have a motherboard with 2 NICs, each with their own IP address assigned, however I was only using one (eth1) and had unchecked (eth0) in the Network Settings applet.  The definition for the adapter was still in my /etc/network/interfaces file.  I commented out the stanza for the one not being used and now my Nautilus is very fast again. I'm not sure if it was because Nautilus was looking to the first card and had to timeout before realizing no connection on that NIC existed or what, but it has fixed my issue.  Something to consider if you have 2 NICs also... YMMV

Example of what I commented out to speed up Nautilus:

#iface eth0 inet static
#address 10.10.5.50
#netmask 255.255.255.0
#gateway 10.10.5.1


iface eth1 inet static
address 10.10.5.51
netmask 255.255.255.0
gateway 10.10.5.1

---

