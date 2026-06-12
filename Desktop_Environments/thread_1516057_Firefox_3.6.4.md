---
title: "Firefox 3.6.4"
date: 2010-06-23
forum: Desktop Environments
---

### Post by lean on 2010-06-23
Will Firefox 3.6.4 come as an update to Ubuntu? Or are there any ppa's that have that version. This version have 'Crash Protection', so it is not just a minor security update.

---

### Post by demuxer on 2010-06-23
There is another thread with the solution here
[http://ubuntuforums.org/showthread.php?t=1515916&highlight=firefox+update&page=2](http://ubuntuforums.org/showthread.php?t=1515916&highlight=firefox+update&page=2)

basically, the solution is to add
deb [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) lucid main


and then synaptic show the upgrade

---

### Post by lovinglinux on 2010-06-23
> **lean said:**
> Will Firefox 3.6.4 come as an update to Ubuntu? Or are there any ppa's that have that version. This version have 'Crash Protection', so it is not just a minor security update.

[It will come to all supported Ubuntu versions](http://ubuntuforums.org/showthread.php?t=1500861). When? I don't know.

If you want it now, see the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by m94mni on 2010-06-23
> **demuxer said:**
> There is another thread with the solution here
[http://ubuntuforums.org/showthread.php?t=1515916&highlight=firefox+update&page=2](http://ubuntuforums.org/showthread.php?t=1515916&highlight=firefox+update&page=2)

basically, the solution is to add
deb [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) lucid main


and then synaptic show the upgrade

This is build 7, which should be VERY similar to the final version.

I tested this, and after installation, firefox did not even start. Does anyone recognize this?

---

### Post by nanotube on 2010-06-24
Try the ubuntuzilla repository - .deb packs of the official mozilla releases:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
(32bit only)

---

### Post by lovinglinux on 2010-06-24
Looks like it will be available tomorrow.

[http://ubuntuforums.org/showpost.php?p=9502858&postcount=22](http://ubuntuforums.org/showpost.php?p=9502858&postcount=22)

---

### Post by Stephen_at on 2010-06-29
Or maybe not.

I assume the Thunderbird update will be pushed out at the same time.

---

### Post by interzoneuk on 2010-06-29
Hi.

Don't get 3.6.4 it has been superseded by 3.6.6 which has a fair few bug fixes.

---

### Post by moongia on 2010-06-29
I got 3.6.6 a few days ago,by using ubuntuzilla.u install a small deb and run a small script.I will update to the latest firefox,and let you know when theres a new one..

---

### Post by nanotube on 2010-06-29
> **moongia said:**
> I got 3.6.6 a few days ago,by using ubuntuzilla.u install a small deb and run a small script.I will update to the latest firefox,and let you know when theres a new one..

you're using the old instructions.
ubuntuzilla is now just a normal repository, containing mozilla builds.
see [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for latest instructions...
the script way still works... but repo is cleaner and better.

<rant>stupid blogs and their useless copying of the old ubuntuzilla script instructions</rant> :mad:

---

### Post by chrisccoulson on 2010-06-29
> **nanotube said:**
> you're using the old instructions.
ubuntuzilla is now just a normal repository, containing mozilla builds.
see [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for latest instructions...
the script way still works... but repo is cleaner and better.

<rant>stupid blogs and their useless copying of the old ubuntuzilla script instructions</rant> :mad:

Is it the old instructions which cause us problems such as [this]("https://bugs.edge.launchpad.net/ubuntu/+source/firefox/+bug/599978")?

---

### Post by nanotube on 2010-06-30
> **chrisccoulson said:**
> Is it the old instructions which cause us problems such as [this]("https://bugs.edge.launchpad.net/ubuntu/+source/firefox/+bug/599978")?

in brief, yes :)

---

### Post by lovinglinux on 2010-06-30
> **chrisccoulson said:**
> Is it the old instructions which cause us problems such as [this]("https://bugs.edge.launchpad.net/ubuntu/+source/firefox/+bug/599978")?

Should I stop recommending to divert firefox for those installing it manually from Mozilla?

---

### Post by chrisccoulson on 2010-06-30
> **lovinglinux said:**
> Should I stop recommending to divert firefox for those installing it manually from Mozilla?

Yes please. Diverting /usr/bin/firefox breaks our maintainer scripts (when they try to register /usr/bin/firefox as an alternative for x-www-browser), which causes upgrades to fail and users to report bugs that we just end up closing.

---

### Post by lovinglinux on 2010-06-30
> **chrisccoulson said:**
> Yes please. Diverting /usr/bin/firefox breaks our maintainer scripts (when they try to register /usr/bin/firefox as an alternative for x-www-browser), which causes upgrades to fail and users to report bugs that we just end up closing.

I used to recommend to create a symlink for the alternative firefox under /usr/local/bin, but the last time I tried, the default version was launched when running firefox command. Any ideas?

---

### Post by lovinglinux on 2010-06-30
@chrisccoulson

Looks like Firefox 3.6.6 upgrade is not going to be smooth:

[http://ubuntuforums.org/showthread.php?t=1521190](http://ubuntuforums.org/showthread.php?t=1521190)
[http://ubuntuforums.org/showthread.php?t=1521140](http://ubuntuforums.org/showthread.php?t=1521140)
[http://ubuntuforums.org/showthread.php?t=1520985](http://ubuntuforums.org/showthread.php?t=1520985)

---

### Post by nanotube on 2010-06-30
> **lovinglinux said:**
> I used to recommend to create a symlink for the alternative firefox under /usr/local/bin, but the last time I tried, the default version was launched when running firefox command. Any ideas?

i bet the default version was already opened somewhere, so running it just opened a new window. make sure to completely quit firefox before trying that again?

basically, look at output of:
```
echo $PATH
```
if /usr/local/bin is first in line, then the firefox in /usr/local/bin WILL take precedence over /usr/bin.

---

### Post by nanotube on 2010-06-30
> **lovinglinux said:**
> Should I stop recommending to divert firefox for those installing it manually from Mozilla?

hmm, apparently the local diversions don't play nicely with the pre/post scripts that come through from the packages...

---

### Post by lovinglinux on 2010-06-30
> **nanotube said:**
> i bet the default version was already opened somewhere, so running it just opened a new window. make sure to completely quit firefox before trying that again?

basically, look at output of:
```
echo $PATH
```
if /usr/local/bin is first in line, then the firefox in /usr/local/bin WILL take precedence over /usr/bin.

Yes, it is. I'm sure firefox was closed. Anyway, I will do some tests and update my extension.

Thanks.

---

### Post by nanotube on 2010-06-30
> **lovinglinux said:**
> @chrisccoulson

Looks like Firefox 3.6.6 upgrade is not going to be smooth:

[http://ubuntuforums.org/showthread.php?t=1521190](http://ubuntuforums.org/showthread.php?t=1521190)
[http://ubuntuforums.org/showthread.php?t=1521140](http://ubuntuforums.org/showthread.php?t=1521140)
[http://ubuntuforums.org/showthread.php?t=1520985](http://ubuntuforums.org/showthread.php?t=1520985)

heh well, fwiw, been running 3.6.4 since its release, via ubuntuzilla repo, with nary a problem :P

---

### Post by nanotube on 2010-06-30
> **lovinglinux said:**
> Yes, it is. I'm sure firefox was closed. Anyway, I will do some tests and update my extension.

Thanks.

yea give it another try... let know how it goes.

also try command ```
which firefox
```
that'll give you the full path of the command that would be executed if you call 'firefox'.

---

### Post by lovinglinux on 2010-06-30
> **nanotube said:**
> yea give it another try... let know how it goes.

also try command ```
which firefox
```
that'll give you the full path of the command that would be executed if you call 'firefox'.

I didn't need to test. I'm using a compiled version of Firefox and it is located at /usr/local/bin. It works indeed.

---

### Post by nanotube on 2010-06-30
> **lovinglinux said:**
> I didn't need to test. I'm using a compiled version of Firefox and it is located at /usr/local/bin. It works indeed.

cool. :) must have had an open window of firefox hiding on one of the desktops that one time when it didn't work... :)

---

### Post by lovinglinux on 2010-07-19
> **nanotube said:**
> i bet the default version was already opened somewhere, so running it just opened a new window. make sure to completely quit firefox before trying that again?

basically, look at output of:
```
echo $PATH
```
if /usr/local/bin is first in line, then the firefox in /usr/local/bin WILL take precedence over /usr/bin.

It only works if I start firefox from terminal. The launchers are still launching the default version. The launchers are the default ones, with a **firefox %u** command, not a path.

I'm trying to implement a divertion removal in my extension, but I can't rely on the user being able to start it only via terminal.

I installed Ubuntuzilla again today, just to see if it is detected and it does create a diversion:

> Adding `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'

What should I do?

---

### Post by nanotube on 2010-07-20
> **lovinglinux said:**
> It only works if I start firefox from terminal. The launchers are still launching the default version. The launchers are the default ones, with a **firefox %u** command, not a path.

I'm trying to implement a divertion removal in my extension, but I can't rely on the user being able to start it only via terminal.

I installed Ubuntuzilla again today, just to see if it is detected and it does create a diversion:



What should I do?

Local diversions (what used to be done by the script) are different from package diversions (what is being done now)... so it should be fine.

---

### Post by lovinglinux on 2010-07-20
> **nanotube said:**
> Local diversions (what used to be done by the script) are different from package diversions (what is being done now)... so it should be fine.

What is the difference? I'm using this:

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```

Then, symlinking the new firefox from /opt:

```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

I never had any problems with updates.

---

