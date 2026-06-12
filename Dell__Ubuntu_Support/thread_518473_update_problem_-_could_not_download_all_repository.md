---
title: "update problem - could not download all repository..."
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by caspersghosts on 2007-08-05
so a couple days ago (I think) my package managers just stopped working.

on trying to check for updates with Update Manager, this is the output.

>>[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg:](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2:](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

I didn´t change any settings, but that localhost bit of the message seems to be the main issue. can I manually reconfigure that properly?
starting to be a major issue... can´t get any essential software.

Oh, I´m specifically using ubuntustudio 7.04, and its been smooth sailing up until now.
Need to know anything else to help me get this fixed?

---

### Post by RHorse on 2007-08-05
You *may* need a gpg key for that one.  Google gpg key <Your Repo> and see if you come up with anything.  There's a command apt-key I think that dls and installs these keys so you can access the repos that need them.  HTH

---

### Post by smithno on 2007-08-06
I don't have any ideas to help; Sorry! But, the "localhost:4001 (127.0.0.1)." indicates that the Update Manager is trying to connect to your local machine. It's not going to the network! Maybe this clue will help someone in figuring out your problem...

---

### Post by caspersghosts on 2007-08-09
ah yes, seems like that is the problem. the update manager isn´t connecting to the network. is there a cmd for setting that? or a convenient menu? How could something like that get changed?

---

### Post by SSmith on 2007-08-09
Some sort of a proxy problem?  Are you running tor or some sort of anonymizing proxy?  If you are, try disabling those.

---

### Post by caspersghosts on 2007-08-15
well my laptop is setup for direct connection, no proxy
I was experimenting with using a proxy for browsing, but decided it wasn´t going to meet my needs.

perhaps that changed the configuration of the update manager + synaptic?
don´t those follow the standard network settings?
(which I have setup for dhcp, and of course, no proxy)

is there another area I should check, to get that reconfigured?
obviously, connecting to the localhost isn´t going to let me have any outside access...
I´m just a little baffled as to why update manager + synaptic are trying to, since the rest of my web functionality is intact.

---

### Post by sciurus on 2007-08-16
Does this happen at the command line (ie apt-get or better yet aptitude)? Can you paste the result of ```
 cat /etc/apt/sources.list /etc/apt/apt.conf.d/*
```?

---

### Post by andybleaden on 2007-08-16
I just ran that command as I am getting similar issues and got this result

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

# Multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe main multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# Multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

# extra packages from kubuntu.org
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties

APT
{
  NeverAutoRemove
  {
        "^linux-image.*";
        "^linux-restricted-modules.*";
  };

  Install-Recommends-Section "metapackages";
  Never-MarkAuto-Section "metapackages";
};
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
// allowed (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu feisty-security";
//      "Ubuntu feisty-updates";
};

// never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
//      "vim";
};
// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};
// Get rid of unneeded locale files after each package installation

DPkg
{
Post-Invoke {"if [ -x /usr/sbin/localepurge ] && [ $(ps w -p "$PPID" | grep -c remove) != 1 ]; then /usr/sbin/localepurge; else exit 0; fi";};

---

