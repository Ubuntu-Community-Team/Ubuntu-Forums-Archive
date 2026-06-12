---
title: "CS Server FTP"
date: 2006-08-31
forum: Gaming &amp; Leisure
---

### Post by DMack on 2006-08-31
Hello everyone,

I just recently switched over to Ubuntu linux from Windows XP.

I had an ftp program called [GuildFTP]("http://www.guildftpd.com/") that was setup so when i gave other people the ftp info they could upload files and maps to my server, But i don't think GuildFTP is available under Linux OS.

I was wondering if there is any program or way for me to setup a ftp for my Counter-Strike server so that others can upload things to my computer?

Thanks,
DMack

---

### Post by fritz_monroe on 2006-08-31
An FTP server is pretty easy to set up in just about any Linux distro.  Here is the FTP server section of the [Ubuntu guide]("http://ubuntuguide.org/wiki/Dapper#FTP_Server").

I don't know if anything special is required for a Counter-Strike server, but this would probably get you started.

---

### Post by DMack on 2006-08-31
I entered the command sudo apt-get install proftpd and this is what i got.

```
root@server:/home/hlds# sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd
```

What should i do?

---

### Post by peanut butter on 2006-08-31
you probably have to enable the universe repository. see [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by Sam on 2006-08-31
You need to add extra repositories. Check [Ubuntu Guide](http://www.ubuntuguide.org/).

---

### Post by ferose2 on 2006-09-01
If you are using x86 and live in the U.S. you can try this...

1- Type [U]sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
[/U] to backup your current repository list incase mine gives you any trouble. (If it does give you trouble type _sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list_ to restore your old repository.)

2- Type _sudo gedit /etc/apt/sources.list_
 and paste everything 3 lines below over your current repository.



deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

# Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

# Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

# Ubuntu 'Backports' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Ubuntu Bug Fix Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

# Ubuntu Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# PLF - Collection of Non-Free Proprietary Codecs & Applications
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

# WINE - Windows API for Linux
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Skype - VoIP Software
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

# Opera - Web Browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

---

