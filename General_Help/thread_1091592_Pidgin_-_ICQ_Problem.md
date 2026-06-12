---
title: "Pidgin - ICQ Problem"
date: 2009-03-09
forum: General Help
---

### Post by change_mode on 2009-03-09
> The client version you are using is too old. Please update at http://pidgin.im/"

I guess this is related to the recent ICQ update and older protocol versions are not allowed to connect anymore.

Do I have to compile the newest Pidgin version or get .deb files somewhere else, or will there be a fix via the ubuntu update, like last time?

---

### Post by linuxd00 on 2009-03-09
i suspect like last time they changed the protocol data a bit. Just wait for a update. 

In any case we should not hammer the Pidgin website like last time.

It definitely not their fault.

---

### Post by heatblazer on 2009-03-09
I`ve encountered the same problem with my pidgin. Guess it`s the same from the last time :) This time I won`t hex edit the file. Just will wait for the update :)

---

### Post by fraktalek on 2009-03-09
In the mean time, we can use LICQ. Kopete doesn't work for me either.
I also tried SIM-IM and it maybe works but its user interface is broken in my installation - it lacks all icons.

---

### Post by raynedanser on 2009-03-09
Makes another of us having the issue. Glad it isn't just me. 

About how long for the update to come out?

---

### Post by NobleSavage on 2009-03-09
Same problem here.  I hope there is an update soon.

---

### Post by garylinux on 2009-03-09
I went to [http://www.pidgin.im/download/](http://www.pidgin.im/download/)  and grabbed the source and ran
./configure --disable-meanwhile --disable-nm --disable-perl --disable-tcl
then ran
make 
make install
and then run /usr/local/pidgin
and it is not hard to remove when ubuntu gets the fix put into the package

---

### Post by NobleSavage on 2009-03-09
> **garylinux said:**
> I went to [http://www.pidgin.im/download/](http://www.pidgin.im/download/)  and grabbed the source and ran
./configure --disable-meanwhile --disable-nm --disable-perl --disable-tcl
then ran
make 
make install
and then run /usr/local/pidgin
and it is not hard to remove when ubuntu gets the fix put into the package



Ok, I'm gonna try this.  Will it automatically install in /usr/local/pidin ?

And how do you remove it?

---

### Post by novafluxx on 2009-03-10
Yeah its because the version of pidgin in Intrepid is fairly old. Hasn't been update in...almost 6 months :-D

Newest version is 2.5.5 while Intrepid includes 2.5.2

So I hope Ubuntu releases an update...

---

### Post by novafluxx on 2009-03-10
> **NobleSavage said:**
> Ok, I'm gonna try this.  Will it automatically install in /usr/local/pidin ?

And how do you remove it?

My questions exactly...I've heard some say make uninstall works, but I've no idea.

---

### Post by garylinux on 2009-03-10
> **NobleSavage said:**
> Ok, I'm gonna try this.  Will it automatically install in /usr/local/pidin ?

And how do you remove it?

it installs into /usr/local/bin/

but make uninstall  in the dir that you built it in should do the trick
and if you have not done much building from source there should not be much there anyway

---

### Post by ulukay on 2009-03-10
> **NobleSavage said:**
> Ok, I'm gonna try this.  Will it automatically install in /usr/local/pidin ?

And how do you remove it?

use
./configure --disable-meanwhile --disable-nm --disable-perl --disable-tcl --prefix=/opt/pidgin-2.5.5

and remove it with 
rm -rf /opt/pidgin-2.5.5

---

### Post by novafluxx on 2009-03-10
[www.getdeb.net](www.getdeb.net)

Thats what I did, I'm not familiar with building from source...this site is awesome when you need to get an updated package!:P

---

### Post by vvd416 on 2009-03-10
Just downloaded version 2.5.5; ./configure, make & make install ran without problems. Anyhow, ICQ still doesn't work

---

### Post by novafluxx on 2009-03-10
> **vvd416 said:**
> Just downloaded version 2.5.5; ./configure, make & make install ran without problems. Anyhow, ICQ still doesn't work

I got it from getdeb.net and ICQ works for me now.

---

### Post by vvd416 on 2009-03-10
Mine is from [http://pidgin.im](http://pidgin.im). Do you think it could be different from Debian distro?

Last time it depended on the zone whether non-native clients were working or not. Who knows what AOL figured out now.
I'm getting tired of it.

---

### Post by novafluxx on 2009-03-10
If you compiled from source you should be fine :-) I just don't know how yet, so I used getdeb.net

---

### Post by Yellow Pasque on 2009-03-10
Don't expect an update to Ubuntu 8.10 this late in its development cycle. Ubuntu 9.04 will be out next month and will include at least Pidgin 2.5.5

---

### Post by freeediver on 2009-03-10
I have the same issue.
Cant make it work and hoping for an update.
Hardy 8.04

---

### Post by AllesMeins on 2009-03-10
Pidgin 2.5.5 is now in the jaunty repositories. So just add

```

deb http://de.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty universe

deb http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

```

to /etc/apt/sources.list, press reload, search for pidgin and mark it for upgrade. That worked fine for me.
Don't forget to remove those lines after the pidgin upgrade, unless you want an full upgrade to jaunty.

[COLOR="Red"]Note added: Please do not mix Intrepid and Jaunty repos in the sources.list, there is a high probability it messes up your install.[/COLOR]

---

### Post by quonsar on 2009-03-10
i compiled 2.5.5 from source on amd64 and ICQ still doesn't work. will try the getdeb pkg next.

---

### Post by roman.lange on 2009-03-10
Solution Found:

I downloaded pidgin (564.3 kB), pidgin-data (7.2 MB), libpurple0 (1.5 MB),  libpurple-bin (100.1 kB) from getdeb.net and installed it using the following method and I didn't even have to uninstall the previous version. I found the solution in the comments on getdeb.net:

You don't have to uninstall the previous version if you are using the command line to install pidgin.

Type:

sudo dpkg -i libpurple-bin_2.5.5-1~getdeb1_all.deb libpurple0_2.5.5-1~getdeb1_i386.deb pidgin_2.5.5-1~getdeb1_i386.deb pidgin-data_2.5.5-1~getdeb1_all.deb

(all four packages separated just by a space) and it will be updated on the fly. You don't even have to reinstall your plugins!

Original Problem:

Same for me, built Pidgin 2.5.5 from source ([http://pidgin.im/](http://pidgin.im/)) but ICQ still doesn't work. It just says "ICQ disabled, the client version you are using is too old. Please upgrade at [http://pidgin.im](http://pidgin.im)

Ubuntu 8.10, 2.6.27-13-generic

Can anyone confirm that the installation from GetDeb really solves the problem?

---

### Post by darthmob on 2009-03-10
icq didn't connect yesterday afternoon. the package from getdeb.net solved it for me!

PS: I did follow their advice and uninstalled pidgin before installing the new version. I'm not sure if it helps but it can't be wrong. :)

---

### Post by rhenium3 on 2009-03-10
> **AllesMeins said:**
> Pidgin 2.5.5 is now in the jaunty repositories. So just add

```

deb http://de.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty universe

deb http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

```

to /etc/apt/sources.list, press reload, search for pidgin and mark it for upgrade. That worked fine for me.
Don't forget to remove those lines after the pidgin upgrade, unless you want an full upgrade to jaunty.


Thanks, that seemed to work :)

---

### Post by Yellow Pasque on 2009-03-10
> **AllesMeins said:**
> Pidgin 2.5.5 is now in the jaunty repositories. So just add...
to /etc/apt/sources.list, press reload, search for pidgin and mark it for upgrade. That worked fine for me.
Don't forget to remove those lines after the pidgin upgrade, unless you want an full upgrade to jaunty.

That's a really bad practice, but I'm glad it worked for you in this instance.

---

### Post by rhenium3 on 2009-03-10
> **Temüjin said:**
> That's a really bad practice, but I'm glad it worked for you in this instance.


No, I have to agree now, I really messed up my system and ubuntu won't load! kjlafdjlkfdsa;lkjfdsa

---

### Post by freeediver on 2009-03-10
And now MSN has quit in Pidgin.

---

### Post by Bapf on 2009-03-10
> **rhenium3 said:**
> No, I have to agree now, I really messed up my system and ubuntu won't load! kjlafdjlkfdsa;lkjfdsa

Same here.

Downgrading the following packages to the intrepid-version fixed it for me:
[http://packages.ubuntu.com/intrepid/gtk2-engines-pixbuf](http://packages.ubuntu.com/intrepid/gtk2-engines-pixbuf)
[http://packages.ubuntu.com/intrepid/libgtk2.0-0](http://packages.ubuntu.com/intrepid/libgtk2.0-0)

---

### Post by ivze on 2009-03-10
Bump. 
Same problem, Intrepid pidgin can't connect to ICQ anymore.

---

### Post by bapoumba on 2009-03-10
Packages are distributed according to their version number in each release. If you mix repositories from several releases, and even more from other distributions, chances are they will not play nice together. The package manager always installs the latest version available. You can end up with a non-functional system, especially if central packages such as libs are upgraded.
Please do not do it, and do not recommend to do so. Thanks.

---

### Post by mokolo on 2009-03-10
> **Bapf said:**
> Same here.

Downgrading the following packages to the intrepid-version fixed it for me:
[http://packages.ubuntu.com/intrepid/gtk2-engines-pixbuf](http://packages.ubuntu.com/intrepid/gtk2-engines-pixbuf)
[http://packages.ubuntu.com/intrepid/libgtk2.0-0](http://packages.ubuntu.com/intrepid/libgtk2.0-0)

How did you manage to do it? I never get to the login screen.

> **bapoumba said:**
> Packages are distributed according to their version number in each release. If you mix repositories from several releases, and even more from other distributions, chances are they will not play nice together. The package manager always installs the latest version available. You can end up with a non-functional system, especially if central packages such as libs are upgraded.
Please do not do it, and do not recommend to do so. Thanks.

How could I revert those changes and make sure to downgrade the appropriate packages?

---

### Post by quonsar on 2009-03-10
> **roman.lange said:**
> Solution Found:

I downloaded pidgin (564.3 kB), pidgin-data (7.2 MB), libpurple0 (1.5 MB),  libpurple-bin (100.1 kB) from getdeb.net and installed it using the following method and I didn't even have to uninstall the previous version. I found the solution in the comments on getdeb.net:

You don't have to uninstall the previous version if you are using the command line to install pidgin.

Type:

sudo dpkg -i libpurple-bin_2.5.5-1~getdeb1_all.deb libpurple0_2.5.5-1~getdeb1_i386.deb pidgin_2.5.5-1~getdeb1_i386.deb pidgin-data_2.5.5-1~getdeb1_all.deb

(all four packages separated just by a space) and it will be updated on the fly. You don't even have to reinstall your plugins!

Original Problem:

Same for me, built Pidgin 2.5.5 from source ([http://pidgin.im/](http://pidgin.im/)) but ICQ still doesn't work. It just says "ICQ disabled, the client version you are using is too old. Please upgrade at [http://pidgin.im](http://pidgin.im)

Ubuntu 8.10, 2.6.27-13-generic

Can anyone confirm that the installation from GetDeb really solves the problem?

This worked perfectly! Don't forget if you are running 64-bit to change the references to 'i386' to 'amd64' in the command line.

---

### Post by vvd416 on 2009-03-11
> **roman.lange said:**
> Solution Found:

I downloaded pidgin (564.3 kB), pidgin-data (7.2 MB), libpurple0 (1.5 MB),  libpurple-bin (100.1 kB) from getdeb.net and installed it using the following method and I didn't even have to uninstall the previous version. I found the solution in the comments on getdeb.net:

You don't have to uninstall the previous version if you are using the command line to install pidgin.

Type:

sudo dpkg -i libpurple-bin_2.5.5-1~getdeb1_all.deb libpurple0_2.5.5-1~getdeb1_i386.deb pidgin_2.5.5-1~getdeb1_i386.deb pidgin-data_2.5.5-1~getdeb1_all.deb

(all four packages separated just by a space) and it will be updated on the fly. You don't even have to reinstall your plugins!

Original Problem:

Same for me, built Pidgin 2.5.5 from source ([http://pidgin.im/](http://pidgin.im/)) but ICQ still doesn't work. It just says "ICQ disabled, the client version you are using is too old. Please upgrade at [http://pidgin.im](http://pidgin.im)

Ubuntu 8.10, 2.6.27-13-generic

Can anyone confirm that the installation from GetDeb really solves the problem?

I confirm that the solution worked for me.
I also built 2.5.5 from source taken from the Pidgin site and I had the same problem with ICQ.
Debian packages did the job.

Thanks, man.

---

### Post by JuniorJack on 2009-03-11
> **roman.lange said:**
> Solution Found:

I downloaded pidgin (564.3 kB), pidgin-data (7.2 MB), libpurple0 (1.5 MB),  libpurple-bin (100.1 kB) from getdeb.net and installed it using the following method and I didn't even have to uninstall the previous version. I found the solution in the comments on getdeb.net:

You don't have to uninstall the previous version if you are using the command line to install pidgin.

Type:

sudo dpkg -i libpurple-bin_2.5.5-1~getdeb1_all.deb libpurple0_2.5.5-1~getdeb1_i386.deb pidgin_2.5.5-1~getdeb1_i386.deb pidgin-data_2.5.5-1~getdeb1_all.deb

(all four packages separated just by a space) and it will be updated on the fly. You don't even have to reinstall your plugins!

Original Problem:

Same for me, built Pidgin 2.5.5 from source ([http://pidgin.im/](http://pidgin.im/)) but ICQ still doesn't work. It just says "ICQ disabled, the client version you are using is too old. Please upgrade at [http://pidgin.im](http://pidgin.im)

Ubuntu 8.10, 2.6.27-13-generic

Can anyone confirm that the installation from GetDeb really solves the problem?

Hi,

I can also confirm that it fixed the problem for me. I did follow your guide
and it was pretty straightforward. 

Now ICQ is working on my EEE with Ubuntu 8.10, Thanks so much!

BR

---

### Post by cwhisperer on 2009-03-11
> **roman.lange said:**
> Solution Found:

I downloaded pidgin (564.3 kB), pidgin-data (7.2 MB), libpurple0 (1.5 MB),  libpurple-bin (100.1 kB) from getdeb.net and installed it using the following method and I didn't even have to uninstall the previous version. I found the solution in the comments on getdeb.net:

You don't have to uninstall the previous version if you are using the command line to install pidgin.

Type:

sudo dpkg -i libpurple-bin_2.5.5-1~getdeb1_all.deb libpurple0_2.5.5-1~getdeb1_i386.deb pidgin_2.5.5-1~getdeb1_i386.deb pidgin-data_2.5.5-1~getdeb1_all.deb

(all four packages separated just by a space) and it will be updated on the fly. You don't even have to reinstall your plugins!

Original Problem:

Same for me, built Pidgin 2.5.5 from source ([http://pidgin.im/](http://pidgin.im/)) but ICQ still doesn't work. It just says "ICQ disabled, the client version you are using is too old. Please upgrade at [http://pidgin.im](http://pidgin.im)

Ubuntu 8.10, 2.6.27-13-generic

Can anyone confirm that the installation from GetDeb really solves the problem?

this works perfectly for me without uninstall. great job

---

### Post by Bapf on 2009-03-11
> **mokolo said:**
> How did you manage to do it? I never get to the login screen.
I downloaded them on another computer, copied them via scp to my ubuntu box and installed them with dpkg -i via ssh.

But I also recommend downgrading the jaunty pidgin packages with

pidgin
libpurple0
libpurple-bin
pidgin-data

from [http://www.getdeb.net/release/3961](http://www.getdeb.net/release/3961) (just install them over the jaunty packages with dpkg -i) if you want to update your intrepid any longer. ;)

---

### Post by bapoumba on 2009-03-11
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027711.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027711.html)
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/340151](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/340151)

Looks like the fixes are available.

---

### Post by gdcondor on 2009-03-11
Hello all !

I've seen it has been corrected in hardy-proposed (pidgin 2.4.1-1ubuntu2.3) but I'm using 2.5.2-0ubuntu1~hardy1 through hardy-backports :( Will it be updated also in hardy-backports ? (and it doesn't work when I try to force version to 2.4.1-1ubuntu2.3 in synaptic :( )

Thanks for your help !
-- 
Florian

---

### Post by SpaceTeddy on 2009-03-11
I am still using hardy (as this is supposed to be an LTS version) - yet i am not able to upgrade the client (according to the logs the 2.4.1-2.3 version got patched - yet that is not even in my repositories yet) and on top of that even if it was, the patched version is older than the current one i have installed. Maybe i am on backports, maybe i am not (i really don't know that) - i know i have never added any repositories, as this is still a plain install. 

Guys, this needs to be fixed. If you support a LTS version, then make sure it also works. This is very frustrating. 

Also, i have been going through the trouble of compiling this pidgin from sources on 8.04 (after installing a million dependencies for building the thing) i now have 2.5.5 working on hardy - but it still does not work (yes, i checked the version, it is 2.5.5). Does this mean that libpurple needs to be patched as well ?

The packets from getdeb don't work either, as they produce more than one unsatisfied dependency and break the packet manager. I've been through that process as well. 

So, what is the point of an LTS if there is no fix for a problem flowing back into it ?

yes, i am annoyed...

---

### Post by Yellow Pasque on 2009-03-12
> **SpaceTeddy said:**
> Guys, this needs to be fixed.
It is fixed [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/340151/comments/37](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/340151/comments/37)
Even if it wasn't, it wouldn't magically get fixed by complaining on this forum. Instead of typing up a rant to fellow users, you should have taken the time to read the Launchpad bug report. The change is currently working its way onto the "hardy-update" repo mirrors and should be available as an update soon.
[https://launchpad.net/ubuntu/hardy/+source/pidgin/1:2.4.1-1ubuntu2.3](https://launchpad.net/ubuntu/hardy/+source/pidgin/1:2.4.1-1ubuntu2.3)

If you want to build from source and have the ICQ fix, you need to use this patch before compiling - [http://developer.pidgin.im/viewmtn/revision/diff/1a658bb7a0436b518d65b9b95116915a5511a7d3/with/3224dd8677b28d02b866cce510941fbf67e0fcb7/libpurple/protocols/oscar/oscar.h](http://developer.pidgin.im/viewmtn/revision/diff/1a658bb7a0436b518d65b9b95116915a5511a7d3/with/3224dd8677b28d02b866cce510941fbf67e0fcb7/libpurple/protocols/oscar/oscar.h)

---

### Post by SpaceTeddy on 2009-03-12
maybe i am misunderstanding something here - but how does a 2.4.1 packet help me when my packet-cache thinks the newest version is 2.5.2 ? I will get update notifications every day that there is a new pidgin out (i have already tried this - and once the update runs through, i have the old version installed)

So, do i have to fix the packet on specific version, do i have to forbid dpkg/apt to update it, or do i have to unpack it and edit the packet description myself ? I am very confused with this...

And yes, i should not have complained - but this is really frustrating...

---

### Post by Yellow Pasque on 2009-03-12
If you're using hardy-backports, the fix probably won't show up there until the next automated upload.

---

### Post by Vadi on 2009-03-12
[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin) ?

---

### Post by MFGorilla on 2009-03-12
my update manager just came up with an alert for pidgin.  installed it and restarted pidgin and ICQ is working...

---

### Post by sanakan on 2009-03-13
In the ubuntu 8.04 there is not yet an update...

Or is it just on my computer? I refresh 1000 times a day to check. I even changed between US and swedish servers to see if there's a difference :(

Ah well, if you're SURE there will eventually be a working update, i will just wait. I was just curious if you 8.04-users have got one working update yet.

---

### Post by SpaceTeddy on 2009-03-13
that's what i was saying before - there is no update for the LTS. Kinda strange if it is claimed to be supported, but then forgotten with an update like this. 

Or am i misunderstanding some mechanics of the repositories ?

---

### Post by SpaceTeddy on 2009-03-15
still nothing for hardy... long live the LTS

---

### Post by Yellow Pasque on 2009-03-15
> **SpaceTeddy said:**
> still nothing for hardy... long live the LTS
The new Hardy package is already in the repos...
If Synaptic shows a 2.5.x version of Pidgin installed, then you're probably not using the standard hardy repos (for instance, you may be using hardy-backports or you've installed a third-party .deb).

Please post output of:
```
cat /etc/apt/sources.list
```

---

### Post by SpaceTeddy on 2009-03-15
i guess this is what you are looking for in the output ?

```
deb http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```

ok, i clearly have the backpors enabled (although i really don't know why... i don't even know what they are - but i must have done it at some point).
The question is - how do i fix it ?

i've forced the version back to 2.4.1-2.3 but now i am getting update messages for pidgin. Athough, only the gnome update icon is complaining, while an apt-get upgrade tells me that the packages are being held back... weird. 
Also, i don't know what other stuff i have installed from the backports, so removing them might break my entire system at some later point... or am i wrong here ?

thanks for the help

---

### Post by coldmack on 2009-03-29
Everytime I try to get libpurple and the pidgin data to install it keeps saying something along the lines of perl needs to be the latest version in order to install. So, the question aries where can I get a deb of Perl version 5.8.8-12 or latter to install or at least add the repo where that is located? Thank you.

---

### Post by coldmack on 2009-03-29
So it is turning out I am having an error with current version of libpurple0 and the only way I can figure out how to install it or remove it is to update perl to the current version of perl which is 5.8.8-12...04 or something. I am not able to install it via debs(stating like an error), so is there a repo I can add for perl so I can the latest version of it please?

---

