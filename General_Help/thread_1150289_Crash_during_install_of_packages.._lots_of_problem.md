---
title: "Crash during install of packages.. lots of problems now"
date: 2009-05-05
forum: General Help
---

### Post by MarkReaves on 2009-05-05
I was attempting to install the "ugly" codecs with synaptic on Jaunty (fresh install) and midway through everything froze solid. Nothing worked, no mouse, no ctrl+alt+backspace, nothing. Had to do a hard shut down.

When I rebooted and tried installing something else, it told me to issue a command to fix the problem (sudo dpkg --configure -a). I did it, it didn't fix the problem. Tried removing a package and got this:
> 4 not fully installed or removed.
After this operation, 614kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109310 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libdvdread4 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libdvdread4 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libid3tag0 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libid3tag0 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libmad0 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libmad0 (--remove):
 subprocess post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 liba52-0.7.4
 libdvdread4
 libid3tag0
 libmad0
E: Sub-process /usr/bin/dpkg returned an error code (1)

So far I cleaned the cache, tried "apt-get --purge remove liba52-0.7.4 libdvdread4 libid3tag0 libmad0" tried autoremoving them, tried everything I could think of and still same error. At this time I cant install or uninstall anything.

---

### Post by adult swim on 2009-05-06
does running ```
sudo apt-get -f install
``` help any?

---

### Post by MarkReaves on 2009-05-06
> **adult swim said:**
> does running ```
sudo apt-get -f install
``` help any?
No it doesn't.

> The following packages will be REMOVED:
  liba52-0.7.4 libdvdread4 libid3tag0 libmad0
0 upgraded, 0 newly installed, 4 to remove and 9 not upgraded.
4 not fully installed or removed.
After this operation, 614kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109310 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libdvdread4 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libdvdread4 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libid3tag0 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libid3tag0 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libmad0 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libmad0 (--remove):
 subprocess post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 liba52-0.7.4
 libdvdread4
 libid3tag0
 libmad0
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MarkReaves on 2009-05-07
I'm thinking this is a bug as I've seen other posts with similar issue, same error (maybe diff packages) and no fixes. This needs to be corrected as I can't install/remove/upgrade anything.

---

### Post by fartknocker on 2009-05-07
appears that everyone with Jaunty is having problems updating their core and restricted extras... would be helpful to be able to do so considering some of us aren't entirely proficient in re-installing things that we accidentally delete

---

### Post by MarkReaves on 2009-05-07
I found a fix for my issue.. I will list it here.

Open terminal and:
[COLOR=DarkGreen]cd /var/lib/dpkg/info[/COLOR]

I then issue:
[COLOR=DarkGreen]rm packagename.post*[/COLOR]
where packagename is the package I'm having issues with (in my case the scripts were empty which caused the errors).

Then I used this:
[COLOR=DarkGreen]apt-get --purge remove packagename[/COLOR]
where packagename is the package name I'm having issues with.

Doing that fixed my issue and now everything works.

---

### Post by ordinareez on 2009-07-08
> **MarkReaves said:**
> I found a fix for my issue.. I will list it here.

Open terminal and:
[COLOR=DarkGreen]cd /var/lib/dpkg/info[/COLOR]

I then issue:
[COLOR=DarkGreen]rm packagename.post*[/COLOR]
where packagename is the package I'm having issues with (in my case the scripts were empty which caused the errors).

Then I used this:
[COLOR=DarkGreen]apt-get --purge remove packagename[/COLOR]
where packagename is the package name I'm having issues with.

Doing that fixed my issue and now everything works.

hey thanks Mark!
it helps me lot when I trying to remove libgtk1.2

---

### Post by arielon on 2009-11-07
One hour later I found you!

Thanks. Will post [on my original Thread]("http://ubuntuforums.org/showthread.php?t=1318760") with the results.

> **MarkReaves said:**
> I found a fix for my issue.. I will list it here.

Open terminal and:
[COLOR=DarkGreen]cd /var/lib/dpkg/info[/COLOR]

I then issue:
[COLOR=DarkGreen]rm packagename.post*[/COLOR]
where packagename is the package I'm having issues with (in my case the scripts were empty which caused the errors).

Then I used this:
[COLOR=DarkGreen]apt-get --purge remove packagename[/COLOR]
where packagename is the package name I'm having issues with.

Doing that fixed my issue and now everything works.

---

### Post by chmac on 2010-05-05
Just found this thread and it worked for me on Jaunty also. Much appreciated.

---

### Post by vansteen on 2010-06-22
Thanks for this very good tip indeed!

---

### Post by quintanarra on 2010-08-08
Thanks for this tip. Spot on! my scripts were empty as well..

---

