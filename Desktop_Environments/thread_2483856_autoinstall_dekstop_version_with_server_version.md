---
title: "autoinstall dekstop version with server version"
date: 2023-02-11
forum: Desktop Environments
---

### Post by lokomass on 2023-02-11
Hi all,

I'm trying to create an auto install iso, and install it in proxmox.
After spent long hours to search how to auto install a Desktop version, I finally abandoned.... (if anybody has an idea, I'm waiting for :))
I see that it's possible to do this with server version only, so I follow this tutorial in a first time : [https://www.pugetsystems.com/labs/hpc/ubuntu-22-04-server-autoinstall-iso/](https://www.pugetsystems.com/labs/hpc/ubuntu-22-04-server-autoinstall-iso/)

This works, and I install automatically with interaction my ubuntu server.
But now, I'm trying to customize my yml file to set Desktop environnement, with full language, etc.
I have some problems.
Here is my yml file :

```
#cloud-config
autoinstall:
  version: 1
  storage:
    layout:
      name: lvm
      match:
        size: largest  
  locale: fr_FR.UTF-8
  keyboard:
    layout: fr
  #network:
  #  version: 2

  #  renderer: NetworkManager # I've tried this for network problem, but there is an installation error with these lines
  identity:
    username: loko
    hostname: ubuntu
    password: ...
  ssh:
    allow-pw: true
    install-server: true
  apt:
    primary:
      - arches: [default]
        uri: http://fr.archive.ubuntu.com/ubuntu/
  packages: 
    - curl
    - net-tools
    - ubuntu-desktop
    - build-essential
    - qemu-guest-agent
    - hunspell-fr-classical
    - language-pack-fr-base
    - libreoffice-help-common
    - language-pack-gnome-fr-base
  package_update: true
  package_upgrade: true
  late-commands:
   # tried this but not work :[COLOR=var(--black-800)][/COLOR]- curtin in-target -- [COLOR=var(--black-800)][FONT=var(--ff-mono)]apt-get install $(check-language-support)[/FONT][/COLOR]
    - sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT=""/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/' /target/etc/default/grub
    #- /usr/sbin/update-grub
    - /sbin/poweroff
  #late-commands:
    #- curtin in-target -- sed -i '/GRUB_CMDLINE_LINUX_DEFAULT=/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/' /etc/default/grub
    #- curtin in-target -- update-grub
    #- curtin in-target -- wget -qO /root/preseed.sh http://10.0.0.1/proxmox/includes/preseed.sh \
    #- curtin in-target -- chmod a+x /root/preseed.sh \
    #- curtin in-target -- /bin/bash /root/preseed.sh \
    #- curtin in-target -- rm -f /root/preseed.sh

```
I have these problems :

- I can't run update-grub to set quiet splash at boot => exit code error can't execute in "/cow" something like this
- my login page isn't in French (we can see "not listed" text)

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291745&stc=1[/IMG]

- which command can I add to autologin ubuntu at boot ?
- I don't have network manager for fired connection ? Nevertheless my dhcp working, I have an ip.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291746&stc=1[/IMG]


- how can I do an update-grub to add quiet splash ?
- finally, how can I skip/answer questions for first login without interaction, and close it at the first boot ?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291747&stc=1[/IMG]

thanks for your help !



[IMG]https://ubuntuforums.org/blob:https://ubuntuforums.org/f3bbfdf1-0798-4e8a-849a-f96dbc89152e[/IMG]

---

