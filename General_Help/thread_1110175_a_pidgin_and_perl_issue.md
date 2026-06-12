---
title: "a pidgin and perl issue"
date: 2009-03-29
forum: General Help
---

### Post by coldmack on 2009-03-29
So, I added the Pidgin repo and it gave me an update to 2.5.5(or what ever the latest version is in their repo). Unfortunately not all of the was able to get installed, like pidgin data and another pidgin based file. Synaptic keeps telling me that I can't upgrade because I don't have the latest version of perl installed, which is 5.8.8-12...04(default installed is 5.8.8-12) or something. I am also getting an error with Libpurple0 in synaptic, because Perl is not up to date. I went on Launchpad, and downloaded the latest version, however, I am getting errors installing them at first citing one thing and now broken dependencies. I tried sudo apt-get install -f and install missing but neither one did fix it.

When I try to remove libpurple0(version for pidgin 2.5.5), I get an error saying I need to reinstall it. When I try to reinstall it, I get an error relating to the version of Perl I have is not the current version. So, I am stuck with that issue there(maybe if i try to install the older version of libpurple0 it may work?)

So, it seems like my options are I either move to back to a version of pidgin that is under 2.5.5.(2.5.2 worked but synaptic showed and update and that is where the problem started) but over 2.4.5(the default that came with my system didn't work as well as 2.5.2). The other option I guess I have is finding a repo that has the latest version of perl, or just figure out a way to install the latest perl version. Ideas, suggestions or something? Thanks.

---

### Post by coldmack on 2009-03-29
I get an error message when I try to install the older version of even reinstall the version of liblpurle0 saying there is a broken dependecy and it needs to be fixed. Not really sure how to do that.

---

### Post by coldmack on 2009-03-29
So now I am getting an error saying: 
E: The package activeperl needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

any ideas?

---

