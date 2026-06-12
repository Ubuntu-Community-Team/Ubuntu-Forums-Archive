---
title: "mozilla-calendar"
date: 2005-10-16
forum: Desktop Environments
---

### Post by K@sperl on 2005-10-16
Hi, 

I can't install mozilla-calendar on breezy because it depends on mozilla-browser 1.7.12-ubuntu2 but 1.7.12-ubuntu1 is installed.
```
 apt-get install mozilla-calendar
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-calendar: Depends: mozilla-browser (= 2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
E: Broken packages
```

apt-cache policy:
```
> apt-cache policy mozilla-browser
mozilla-browser:
  Installed: (none)
  Candidate: 2:1.7.12-1ubuntu1
  Version table:
     2:1.7.12-1ubuntu1 0
        500 http://at.archive.ubuntu.com breezy-updates/main Packages
     2:1.7.12-0ubuntu2 0
        500 http://at.archive.ubuntu.com breezy/main Packages
```

What's wrong there? Why depends mozilla-calendar on an older version of mozilla-browser than currently installed?


thx4help,
Kasperl

---

### Post by Ndlovu on 2005-11-30
I had the same problem but found that my sources were not in order. Make sure that you have repositories for updates and security in universe (edit /etc/apt/sources.list). mozilla-calendar is in universe and mozilla-browser is in main.

---

### Post by daynah on 2005-12-01
I also am having problems, but I have all my repos open.

I can't wait to get it working :) It's my main calendar program on my Windows lappy, so I'll be quite the happy girl.

---

