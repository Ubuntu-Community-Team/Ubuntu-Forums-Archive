---
title: "Thunderbird is already running, but is not responding. To open a new window, you must"
date: 2011-11-01
forum: Desktop Environments
---

### Post by manolomanolo on 2011-11-01
Hi to all.

I just restored my email backup into my new installation of Thunderbird (TB, from now on). In detail, I copied my .thunderbird folder from my previous TB installation of Ubuntu 11.04 to the new TB installation of my Ubuntu 11.10 (installed from scratch).
After replacing the current .thunderbird folder with the backuped one, I experience the following error message while trying to start TB:

```
Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.
```

Please note that the error message occurs even if no other TB or Firefox process is running at that moment, as shown by running the gnome-system-monitor.

What can i do?
Thanks.
Regards.

---

### Post by kellemes on 2011-11-01
try this..
[http://kb.mozillazine.org/Profile_in_use#Remove_the_profile_lock_file]("http://kb.mozillazine.org/Profile_in_use#Remove_the_profile_lock_file")

---

### Post by manolomanolo on 2011-11-01
I just noted that the owner of the backuped .thunderbird folder was root and not the current user. So I "SOLVED" running the following command by terminal:

```
sudo chown -R *my_username:my_groupname* /home/*my_username*/.thunderbird
```

Now my new problem is that, even if my emails have been recovered, TB is downloading them again from server... making me go crazy with useless duplicates :(

---

### Post by kellemes on 2011-11-01
Don't use Thunderbird myself but I'm sure in your account-settings you'll find something like.. "Leave email on server" Guess you have to uncheck/disable it..

---

### Post by shubham1 on 2011-11-01
> **manolomanolo said:**
> Hi to all.

I just restored my email backup into my new installation of Thunderbird (TB, from now on). In detail, I copied my .thunderbird folder from my previous TB installation of Ubuntu 11.04 to the new TB installation of my Ubuntu 11.10 (installed from scratch).
After replacing the current .thunderbird folder with the backuped one, I experience the following error message while trying to start TB:

```
Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.
```

Please note that the error message occurs even if no other TB or Firefox process is running at that moment, as shown by running the gnome-system-monitor.

What can i do?
Thanks.
Regards.
i think this will work
open system monitor find thunder bird
kill it hten open
sometimes it happens with me with ubuntu software center and firefox and it works

---

### Post by kingfisher64 on 2012-01-13
I solved this problem by editing the profiles.ini file in the home > .thunderbird directory, which was pointing to another profile by default.

Copy the profile you want to use into this directory then change the ini file to match the profile name:

Eg, in my example I changed the code from Path=xxx.default to Icuwe8th.default and everything worked fine.

in [General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
**Path=lcuwe8th.default**

If you have not setup a new profile to override then i assume creating a .ini file with the above code pointing to your profile you're copying over will work just fine.

Just make sure the Path line is pointing to a folder in that Home > .thunderbird directory

---

### Post by bebops_lost on 2012-11-12
I had this problem before, and was recommended to delete the file "profiles.ini" -DON'T DO THAT!. It wipes away your profile, and makes it a huge pain to reaccess your emails. 

Instead, open up a terminal and do this:

```

$ cd ~/.thunderbird
$ ls -l

```

then you will see a couple directories; one of them will be a folder with some apparently random characters and then ".default", like for example: 4asfdgr5w.default. In that folder (whatever it's called), there should be an empty file called .parentlock, which is what's preventing you from opening thunderbird again. So:

```

$cd 4asfdgr5w.default
$rm .parentlock
$exit

```

thunderbird should run then.

---

