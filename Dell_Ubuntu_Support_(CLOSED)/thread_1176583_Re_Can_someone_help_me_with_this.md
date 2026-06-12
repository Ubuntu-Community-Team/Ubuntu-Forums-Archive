---
title: "Re: Can someone help me with this ?"
date: 2009-06-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by harecanada on 2009-06-02
I don't understand what Ign , Hit and the rest of the stuff means. Can someone help me out? I tried sudo apt-get update to correct these problems and it didn't change anything. Are they really problems to be concerned about?


Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Packages
Get:13 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Hit [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Packages
Hit [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Fetched 9157B in 6s (1443B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

harecanada

---

### Post by MichaelSammels on 2009-06-02
I can't see any problems. Yes, the message does say "duplicate package lists", but I can't see what problems that would cause.

---

### Post by whoop on 2009-06-02
post contents of /etc/apt/sources.list

---

### Post by harecanada on 2009-06-02
whoop, I tried /etc/apt/sources.list , but it said it didn't exist so I tried this. 
harecanada


harecanada@harecanada-desktop:~$ ls /etc
acpi                    grub.d                passwd-
adduser.conf            gshadow               pcmcia
adjtime                 gshadow-              perl
aliases                 gtk-2.0               pm
alsa                    gxine                 pnm2ppa.conf
alternatives            hal                   PolicyKit
anacrontab              hdparm.conf           popularity-contest.conf
apm                     hesiod.conf           postfix
apparmor                host.conf             power
apparmor.d              hostname              ppp
apport                  hosts                 printcap
apt                     hosts.allow           profile
at.deny                 hosts.deny            profile.d
ati                     hp                    protocols
avahi                   ifplugd               pulse
bash.bashrc             inetd.conf            purple
bash_completion         init.d                python
bash_completion.d       initramfs-tools       python2.5
bindresvport.blacklist  inputrc               python2.6
blkid.tab               iproute2              qt3
blkid.tab.old           issue                 rarfiles.lst
bluetooth               issue.net             rc0.d
bogofilter.cf           java-6-openjdk        rc1.d
bonobo-activation       java-6-sun            rc2.d
brlapi.key              kbd                   rc3.d
brltty                  kde3                  rc4.d
brltty.conf             kernel                rc5.d
ca-certificates         kernel-img.conf       rc6.d
ca-certificates.conf    laptop-mode           rc.local
calendar                ldap                  rcS.d
chatscripts             ld.so.cache           readahead
checkbox.d              ld.so.conf            rearj.cfg
checkinstallrc          ld.so.conf.d          resolvconf
compizconfig            lftp.conf             resolv.conf
ConsoleKit              libao.conf            rmt
console-setup           libgda-3.0            rpc
console-tools           libpaper.d            rsyslog.d
cowpoke.conf            lintianrc             samba
cron.d                  locale.alias          sane.d
cron.daily              localtime             scim
cron.hourly             logcheck              screenlets
cron.monthly            login.defs            screenrc
crontab                 logrotate.conf        scsi_id.config
cron.weekly             logrotate.d           securetty
cups                    lsb-base              security
cvs-cron.conf           lsb-base-logging.sh   sensors.conf
cvs-pserver.conf        lsb-release           services
dbus-1                  ltrace.conf           sgml
debconf.conf            magic                 shadow
debian_version          magic.mime            shadow-
default                 mailcap               shells
defoma                  mailcap.order         skel
deluser.conf            mail.rc               sound
depmod.d                manpath.config        ssh
devscripts.conf         menu                  ssl
dhcp3                   menu-methods          subversion
dictionaries-common     mime.types            sudoers
dkms                    mke2fs.conf           su-to-rootrc
dm                      modprobe.d            sysctl.conf
doc-base                modules               sysctl.d
dpkg                    mono                  syslog.conf
dput.cf                 motd                  terminfo
e2fsck.conf             motd.tail             thunderbird
emacs                   mplayer               tidy.conf
environment             mplayerplug-in.conf   timezone
esound                  mplayerplug-in.types  timidity
event.d                 mtab                  ts.conf
ffserver.conf           mtools.conf           ucf.conf
firefox-3.0             mysql                 udev
fonts                   nanorc                ufw
foomatic                netscsid.conf         updatedb.conf
fstab                   network               update-manager
fuse.conf               NetworkManager        update-motd.d
gai.conf                networks              update-notifier
gamin                   nsswitch.conf         usplash.conf
gconf                   obex-data-server      vga
gdm                     ODBCDataSources       vim
ggi                     odbc.ini              vlc
gimp                    odbcinst.ini          w3m
gnome                   openal                wgetrc
gnome-app-install       openoffice            wildmidi
gnome-system-tools      opera6rc              wodim.conf
gnome-vfs-2.0           opera6rc.fixed        wpa_supplicant
gnome-vfs-mime-magic    opt                   X11
gre.d                   pam.conf              xdg
grep-dctrl.rc           pam.d                 xml
groff                   pango                 xulrunner-1.9
group                   papersize             zsh_command_not_found
group-                  passwd
harecanada@harecanada-desktop:~$

---

### Post by MichaelSammels on 2009-06-02
Try:

```
sudo gedit /etc/apt/source.lst
```

---

### Post by eddietours on 2009-06-02
l think ign is the server was ignore

---

### Post by binbash on 2009-06-02
Paste the output of this command : 

cat /etc/apt/sources.list

---

### Post by harecanada on 2009-06-02
Hey binbash,
here is the output of cat /etc/apt/sources.list
Is there a problem with this or can I just ignore it?
harecanada


harecanada@harecanada-desktop:~$ cat /etc/apt/sources.list
# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc) -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
# Ubuntu supported packages
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted universe multiverse
#Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
#gnome-globalmenu
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main
#opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free
#skype
#deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free
#firefox
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main
#gnome-do
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main
#compiz-fusion
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main
#google
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
#medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
# MySQL Workbench
deb [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) binary/
deb-src [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) source/
# Depot PlayOnLinux
deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) jaunty main
# Ubuntu tweak
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
##Themes du ZgegBlog: Project Bisigi
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main


deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

harecanada@harecanada-desktop:~$

---

### Post by whoop on 2009-06-02
The line:
```

deb http://packages.medibuntu.org/ jaunty free non-free

```
is twice in the file /etc/apt/sources.list
Maybe that is the problem...

backup sources.list and remove one of those lines via:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit /etc/apt/sources.list

```

---

### Post by harecanada on 2009-06-02
Thanks whoop!!
That did it. I really appreciate the help.
How do I mark this as Solved?
harecanada

---

