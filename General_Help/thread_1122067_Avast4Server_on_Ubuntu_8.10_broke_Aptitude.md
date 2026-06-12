---
title: "Avast4Server on Ubuntu 8.10 broke Aptitude"
date: 2009-04-10
forum: General Help
---

### Post by Semirrahge on 2009-04-10
I am not sure if this is the right place for this, and I know this is likely application-specific. I just put this here for general knowledge purposes and maybe a warning so others don't have the same problems. 

FYI: I need antivirus tools for cleaning crap off of my client's windoze systems, I'm not dumb enough to run trojans myself. :P

This is a copy of the post I made on the Avast forums this morning; At this point I'm tired of not being able to use Aptitude and I'll probably just do a reinstall later this evening.

I'm not happy with Avast! at this point for obvious reasons, and we will probably buy a copy of BitDefender. They have a very nice repository for use with different flavors of linux and a nice GUI for GNOME and other window managers.

I would like to hear from someone more experienced than me on what possibly could have caused this. Is it something I did (I just downloaded and installed the .deb - nothing I haven't done over 9000 times before), or is there a problem with the .deb from Avast, or is it an issue with trying to install a 'server' package on a 'workstation' install?

Also, in the errors below it says it can't find '/etc/sysconfig/avastd' - this folder does not exist and I don't know enough about packages to figure out what is calling for it.

Also, I'm running 8.10 32-bit, 2.6.27-11 on an E8500, Intel board (DQ45CB) w/ 2GB ram. FWIW.

 - - - 

For whatever reason, when I tried to install the package 'avast4server-3.0.1-i586.deb' the package manager failed during the install. Immediately thereafter if I tried reinstalling using Gdebi I get:

**Could not open 'avast4server-3.0.1-i586.deb' The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.**

I know I have ownership and all permissions for the file. When I try running Synaptic it authenticates as normal but then tells me:

[B]E: The package avast4server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/B]

and kicks me out.  I don't really care whether I keep Avast! or not, I just want to use my package manager again. Smiley

Running '**sudo dpkg -i avast4server-3.0.1-i586.deb**' produces:

[B](Reading database ... 128894 files and directories currently installed.)
Preparing to replace avast4server 3.0.1 (using avast4server-3.0.1-i586.deb) ...
.: 93: Can't open /etc/sysconfig/avastd
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
.: 93: Can't open /etc/sysconfig/avastd
dpkg: error processing avast4server-3.0.1-i586.deb (--install):
 subprocess new pre-removal script returned error exit status 2
.: 93: Can't open /etc/sysconfig/avastd
invoke-rc.d: initscript avastd, action "restart" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 avast4server-3.0.1-i586.deb[/B]

I did a bit of digging on my own and came up with: '**sudo dpkg --force-remove-reinstreq --remove avast4server**' which gave me basically the same thing:

[B]dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 128893 files and directories currently installed.)
Removing avast4server ...
.: 93: Can't open /etc/sysconfig/avastd
dpkg: error processing avast4server (--remove):
 subprocess pre-removal script returned error exit status 2
.: 93: Can't open /etc/sysconfig/avastd
invoke-rc.d: initscript avastd, action "restart" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 avast4server[/B]

Can someone please tell me how to fix this? Any ideas on what caused this in the first place? Any help would be very greatly appreciated.

---

