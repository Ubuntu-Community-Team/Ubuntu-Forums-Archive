---
title: "Bastille, error &quot;not running stable Debian...&quot;"
date: 2005-11-16
forum: Desktop Environments
---

### Post by thumbsoup on 2005-11-16
I installed Bastille on Ubuntu 5.10 from Synaptic.  

bastille (1:2.1.1-11)
libcurses-perl (1.12-1ubuntu1)

When I first tried to run Bastille, I got an error about it not finding Perl tk, so I installed that from Synaptic as well.

perl-tk (1:800.025-2)

I installed Bastille using interactive mode.   When I finished and tried to apply the configuration, I got a list of error messages where it failed to apply changes:

"System is not running a stable Debian GNU/Linux version. Setting to 3.0."

Is it looking for Debian-Stable?  Should I install a different version of Bastille?  

The Bastille site points to a Debian software page for versions of Bastille including stable, testing and unstable.  Should I try one of these?

# oldstable (admin): Security hardening tool
1:1.3.0-2.1: alpha arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc
# stable (admin): Security hardening tool
1:2.1.1-11: alpha amd64 arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc
# testing (admin): Security hardening tool
1:2.1.1-12: alpha amd64 arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc
# unstable (admin): Security hardening tool
1:2.1.1-12: alpha amd64 arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc
1:2.1.1-11: hurd-i386

[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bastille](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bastille)


P.S. Found a Kubuntu user posting on Linux Questions who got a similar message.  They had a Firestarter firewall problem later, I didn't install the Bastille firewall.

[http://www.linuxquestions.org/questions/history/382279](http://www.linuxquestions.org/questions/history/382279)

Thanks for any advice you might have.

---

### Post by thumbsoup on 2005-11-20
Well, looks like no one had any advice on this issue....

As far as I can see, Bastille did change a few file permissions and disabled a kernal log daemon (was marked as "failed" at boot).

I used the revert function with Bastille and removed the config changes it did make.  Have not experienced any problems.

I think I will wait for better information before trying this again.

---

