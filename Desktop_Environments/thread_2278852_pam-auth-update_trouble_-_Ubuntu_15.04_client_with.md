---
title: "pam-auth-update trouble - Ubuntu 15.04 client with network logins"
date: 2015-05-19
forum: Desktop Environments
---

### Post by jgoguen on 2015-05-19
I'm running Ubuntu 15.04, fresh client install, and I'm trying to set up network authentication using SSSd. I have SSSd set up correctly and I can log in any which way with a network account, but the home directory isn't created. I see people elsewhere saying to create [FONT=courier new]/usr/share/pam-configs/mkhomedir[/FONT] with contents:

```
Name: Create home directory on login
Default: yes
Priority: 0
Session-Type: Additional
Session-Interactive-Only: yes
Session:
    optional            pam_mkhomedir.so

```

I have this (I had to modify the file, it originally had "Default: no") and when I run [FONT=courier new]pam-auth-update --package[/FONT] I still don't have pam_mkhomedir.so in any files under [FONT=courier new]/etc/pam.d/[/FONT] and the home directory still isn't created. I don't see any logs or debug options to help me sort out what's going on, nor can I find a description of the grammar of the files under [FONT=courier new]/usr/share/pam-configs/[/FONT].

I'm also trying to add a couple of other files under [FONT=courier new]/usr/share/pam-configs/[/FONT] to execute scripts using pam_exec, but they aren't being added to [FONT=courier new]/etc/pam.d/common-*[/FONT] either. There are two basic formats of the files I'm trying to add, the only differences being the Name field on the first line and the path to the script on the last line:

```
Name: Thing to do on interactive sessions
Default: yes
Priority: 1
Session-Type: Additional
Session-Interactive-Only: yes
Session-Final:
    optional    pam_exec.so seteuid quiet /path/to/executable/file
```

```
Name: Thing where I need the user password
Default: yes
Priority: 1
Password-Type: Additional
Password:
    optional    pam_exec.so  seteuid expose_authtok /path/to/executable/file
```

I've verified that the paths are all executable; some are shell scripts, some are binaries.

A bit about the environment and desired end result: This is going to be the template for creating Chef recipes that will be used to lay down configurations for various client systems. The imaging process and post-image setup lays down a fresh encrypted Ubnutu install plus some additional files that dictate which cookbooks are run and which are skipped. Since pam_mkhomedir isn't enabled by default, and the whole process needs to be as automated as possible it's very important that human interaction is kept to a minimum; ideally as much as possible is done through Chef and requires zero human interaction. What files are laid down in [FONT=courier new]/usr/share/pam-configs/[/FONT] may vary based on what cookbooks are applied, but at the end of the Chef run when [FONT=courier new]pam-auth-update --package[/FONT] is run, [FONT=courier new]/etc/pam.d/[/FONT] needs to be updated with whatever configs were set up.

---

### Post by jgoguen on 2015-05-19
Turns out [FONT=courier new]/var/lib/pam/seen[/FONT] had the file names listed for some reason. Removed them and it worked fine.

---

