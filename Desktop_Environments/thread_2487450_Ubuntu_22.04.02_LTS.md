---
title: "Ubuntu 22.04.02 LTS"
date: 2023-06-05
forum: Desktop Environments
---

### Post by QKC on 2023-06-05
Dear Ubuntu Forum Member
I am setting up RAID on my desktop running Ubuntu 22.04.02 LTS according to instruction to the link [https://techviewleo.com/configure-software-raid-on-ubuntu-using-mdadm/](https://techviewleo.com/configure-software-raid-on-ubuntu-using-mdadm/) . But when I configuring mount sudo vim /etc/fstab , an error appear "Directory 'etc' does not exist. I am unable to continue. May I know how do I go from there to solve the problem.

Thanks

---

### Post by ActionParsnip on 2023-06-06
What is the output of
```

ls /etc

```
Thanks

---

### Post by QKC on 2023-06-06
Hi ActionParsnip.
Attach is part of my settings. Please assist. I will attach somemore on another reply.

[ATTACH=CONFIG]292346[/ATTACH][ATTACH=CONFIG]292347[/ATTACH]
[ATTACH=CONFIG]292348[/ATTACH][ATTACH=CONFIG]292349[/ATTACH]
[ATTACH=CONFIG]292346[/ATTACH][ATTACH=CONFIG]292347[/ATTACH]
[ATTACH=CONFIG]292348[/ATTACH][ATTACH=CONFIG]292349[/ATTACH]

Thanks

---

### Post by QKC on 2023-06-06
Hi ActionParsnip,
Attach are all my settings. Please assist


Thanks

---

### Post by QKC on 2023-06-06
> **ActionParsnip said:**
> What is the output of
```

ls /etc

```
Thanks


jq@OEM:~$ ls /etc
ModemManager                   gtk-2.0              pnm2ppa.conf
NetworkManager                 gtk-3.0              polkit-1
PackageKit                     hdparm.conf          ppp
UPower                         host.conf            printcap
X11                            hostid               profile
acpi                           hostname             profile.d
adduser.conf                   hosts                protocols
alsa                           hosts.allow          pulse
alternatives                   hosts.deny           python3
anacrontab                     hp                   python3.10
apg.conf                       ifplugd              rc0.d
apm                            init                 rc1.d
apparmor                       init.d               rc2.d
apparmor.d                     initramfs-tools      rc3.d
apport                         inputrc              rc4.d
appstream.conf                 insserv.conf.d       rc5.d
apt                            ipp-usb              rc6.d
avahi                          iproute2             rcS.d
bash.bashrc                    issue                resolv.conf
bash_completion                issue.net            rmt
bash_completion.d              kernel               rpc
bindresvport.blacklist         kernel-img.conf      rsyslog.conf
binfmt.d                       kerneloops.conf      rsyslog.d
bluetooth                      ld.so.cache          rygel.conf
brlapi.key                     ld.so.conf           sane.d
brltty                         ld.so.conf.d         security
brltty.conf                    ldap                 selinux
ca-certificates                legal                sensors.d
ca-certificates.conf           libao.conf           sensors3.conf
ca-certificates.conf.dpkg-old  libaudit.conf        services
chatscripts                    libblockdev          sgml
console-setup                  libnl-3              shadow
cracklib                       libpaper.d           shadow-
cron.d                         libreoffice          shells
cron.daily                     locale.alias         skel
cron.hourly                    locale.gen           snmp
cron.monthly                   localtime            speech-dispatcher
cron.weekly                    logcheck             ssh
crontab                        login.defs           ssl
cups                           logrotate.conf       subgid
cupshelpers                    logrotate.d          subgid-
dbus-1                         lsb-release          subuid
dconf                          machine-id           subuid-
debconf.conf                   magic                sudo.conf
debian_version                 magic.mime           sudo_logsrvd.conf
default                        mailcap              sudoers
deluser.conf                   mailcap.order        sudoers.d
depmod.d                       manpath.config       sysctl.conf
dhcp                           mdadm                sysctl.d
dictionaries-common            mime.types           systemd
dpkg                           mke2fs.conf          terminfo
e2scrub.conf                   modprobe.d           thermald
emacs                          modules              timezone
environment                    modules-load.d       tmpfiles.d
environment.d                  mtab                 ubuntu-advantage
ethertypes                     nanorc               ucf.conf
firefox                        netconfig            udev
fonts                          netplan              udisks2
fprintd.conf                   network              ufw
fstab                          networkd-dispatcher  update-manager
fuse.conf                      networks             update-motd.d
fwupd                          newt                 update-notifier
gai.conf                       nftables.conf        usb_modeswitch.conf
gdb                            nsswitch.conf        usb_modeswitch.d
gdm3                           openvpn              vdpau_wrapper.cfg
geoclue                        opt                  vim
ghostscript                    os-release           vtrgb
glvnd                          pam.conf             vulkan
gnome                          pam.d                wgetrc
groff                          papersize            whoopsie
group                          passwd               wpa_supplicant
group-                         passwd-              xattr.conf
grub.d                         pcmcia               xdg
gshadow                        perl                 xml
gshadow-                       pki                  zsh_command_not_found
gss                            pm
jq@OEM:~$ ^C
jq@OEM:~$

---

