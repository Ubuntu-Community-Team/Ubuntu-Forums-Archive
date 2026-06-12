---
title: "SOS Urgent **** Ubuntu 20.04 LTS (Focal Fossa)  creating 360 mb journal per minute"
date: 2020-06-23
forum: Desktop Environments
---

### Post by crusader5 on 2020-06-23
[COLOR=#ff0000]**SOS Urgent **** Ubuntu 20.04 LTS (Focal Fossa)  creating Automatically 360 MB of journal files per minute and system crashes after the hard disk gets full **[/COLOR]

Hi  All,

In my Ubuntu 20 Desktop system Every Minute 360 MB of journal log data is generated and my processor is busy with 100% utilization running systemd-journal.

Kindly help me urgently as every minute it is storing 128Mb * 3 files in /var/log/journal/42b76941196c44ebabf29f6efc5047c7/ Folder  

I am clearing log with this command manually >  ```
sudo journalctl --vacuum-size=50M
Deleted archived journal /var/log/journal/42b76941196c44ebabf29f6efc5047c7/system@00000000000000000000000000000000-00000000015de62d-0005a8bd92211c3a.journal (128.0M).
Deleted archived journal /var/log/journal/42b76941196c44ebabf29f6efc5047c7/system@00000000000000000000000000000000-000000000160c6b7-0005a8bd93351c1b.journal (128.0M).
Deleted archived journal /var/log/journal/42b76941196c44ebabf29f6efc5047c7/system@00000000000000000000000000000000-000000000163a7b1-0005a8bd945c0bf2.journal (128.0M).
Vacuuming done, freed 3.8G of archived journals from /var/log/journal/42b76941196c44ebabf29f6efc5047c7.
Vacuuming done, freed 0B of archived journals from /run/log/journal.
```

3.8 GB of data created in just few minutes  and the journal files keeps on getting created and my cpu is busy always 100% 

Currently i have done this setting changed :---

In sudo nano /etc/systemd/journald.conf   file modified this settings 

```
SystemMaxUse=50M
MaxLevelStore=err
MaxLevelSyslog=warning
MaxLevelKMsg=warning
MaxLevelConsole=err
```

> ```
top
PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                             >
328 root      19  -1  468040 265696 263872 R 100.0   1.6  31:13.14 systemd-journal
``` 

```
/var/log/journal/42b76941196c44ebabf29f6efc5047c7 &#57520; ls -lhsa
total 3.5G
 12K drwxr-sr-x+ 2 root systemd-journal  12K Jun 23 11:01 .
4.0K drwxr-sr-x+ 3 root systemd-journal 4.0K Jun 15 02:45 ..
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:53 [EMAIL="system@00000000000000000000000000000000-0000000000b928b7-0005a8bd50cff991.journa"]system@00000000000000000000000000000000-0000000000b928b7-0005a8bd50cff991.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:53 [EMAIL="system@00000000000000000000000000000000-0000000000bc0a5c-0005a8bd51dfebc1.journa"]system@00000000000000000000000000000000-0000000000bc0a5c-0005a8bd51dfebc1.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:53 [EMAIL="system@00000000000000000000000000000000-0000000000beeae8-0005a8bd5327bbb9.journa"]system@00000000000000000000000000000000-0000000000beeae8-0005a8bd5327bbb9.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:54 [EMAIL="system@00000000000000000000000000000000-0000000000c1cf12-0005a8bd5491ec30.journa"]system@00000000000000000000000000000000-0000000000c1cf12-0005a8bd5491ec30.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:54 [EMAIL="system@00000000000000000000000000000000-0000000000c4b0ab-0005a8bd55a40899.journa"]system@00000000000000000000000000000000-0000000000c4b0ab-0005a8bd55a40899.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:54 [EMAIL="system@00000000000000000000000000000000-0000000000c7947b-0005a8bd56bf31e1.journa"]system@00000000000000000000000000000000-0000000000c7947b-0005a8bd56bf31e1.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:54 [EMAIL="system@00000000000000000000000000000000-0000000000ca7b31-0005a8bd57e08298.journa"]system@00000000000000000000000000000000-0000000000ca7b31-0005a8bd57e08298.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:55 [EMAIL="system@00000000000000000000000000000000-0000000000cd5d82-0005a8bd58f27c6f.journa"]system@00000000000000000000000000000000-0000000000cd5d82-0005a8bd58f27c6f.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:55 [EMAIL="system@00000000000000000000000000000000-0000000000d0421e-0005a8bd5a0eb633.journa"]system@00000000000000000000000000000000-0000000000d0421e-0005a8bd5a0eb633.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:55 [EMAIL="system@00000000000000000000000000000000-0000000000d324e0-0005a8bd5b414cea.journa"]system@00000000000000000000000000000000-0000000000d324e0-0005a8bd5b414cea.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:56 [EMAIL="system@00000000000000000000000000000000-0000000000d60651-0005a8bd5c5b194e.journa"]system@00000000000000000000000000000000-0000000000d60651-0005a8bd5c5b194e.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:56 [EMAIL="system@00000000000000000000000000000000-0000000000d8eb81-0005a8bd5d7f5e1d.journa"]system@00000000000000000000000000000000-0000000000d8eb81-0005a8bd5d7f5e1d.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:56 [EMAIL="system@00000000000000000000000000000000-0000000000dbd098-0005a8bd5e9a9369.journa"]system@00000000000000000000000000000000-0000000000dbd098-0005a8bd5e9a9369.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:57 [EMAIL="system@00000000000000000000000000000000-0000000000deb64b-0005a8bd5fbe668e.journa"]system@00000000000000000000000000000000-0000000000deb64b-0005a8bd5fbe668e.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:57 [EMAIL="system@00000000000000000000000000000000-0000000000e19c03-0005a8bd60d8c9fe.journa"]system@00000000000000000000000000000000-0000000000e19c03-0005a8bd60d8c9fe.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:57 [EMAIL="system@00000000000000000000000000000000-0000000000e4814d-0005a8bd61ee85f3.journa"]system@00000000000000000000000000000000-0000000000e4814d-0005a8bd61ee85f3.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:58 [EMAIL="system@00000000000000000000000000000000-0000000000e766ad-0005a8bd63092fa2.journa"]system@00000000000000000000000000000000-0000000000e766ad-0005a8bd63092fa2.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:58 [EMAIL="system@00000000000000000000000000000000-0000000000ea47e6-0005a8bd6420b7d5.journa"]system@00000000000000000000000000000000-0000000000ea47e6-0005a8bd6420b7d5.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:58 [EMAIL="system@00000000000000000000000000000000-0000000000ed2b78-0005a8bd6592ecbf.journa"]system@00000000000000000000000000000000-0000000000ed2b78-0005a8bd6592ecbf.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:59 [EMAIL="system@00000000000000000000000000000000-0000000000f011ae-0005a8bd66fd52a8.journa"]system@00000000000000000000000000000000-0000000000f011ae-0005a8bd66fd52a8.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:59 [EMAIL="system@00000000000000000000000000000000-0000000000f2f60c-0005a8bd68164432.journa"]system@00000000000000000000000000000000-0000000000f2f60c-0005a8bd68164432.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 10:59 [EMAIL="system@00000000000000000000000000000000-0000000000f5d72f-0005a8bd69297455.journa"]system@00000000000000000000000000000000-0000000000f5d72f-0005a8bd69297455.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 11:00 [EMAIL="system@00000000000000000000000000000000-0000000000f8bb3a-0005a8bd6a453704.journa"]system@00000000000000000000000000000000-0000000000f8bb3a-0005a8bd6a453704.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 11:00 [EMAIL="system@00000000000000000000000000000000-0000000000fb9c70-0005a8bd6b770daa.journa"]system@00000000000000000000000000000000-0000000000fb9c70-0005a8bd6b770daa.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 11:00 [EMAIL="system@00000000000000000000000000000000-0000000000fe8190-0005a8bd6c92d47f.journa"]system@00000000000000000000000000000000-0000000000fe8190-0005a8bd6c92d47f.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 11:01 [EMAIL="system@00000000000000000000000000000000-00000000010166e5-0005a8bd6dac401f.journa"]system@00000000000000000000000000000000-00000000010166e5-0005a8bd6dac401f.journa[/EMAIL]l
129M -rw-r-----+ 1 root systemd-journal 128M Jun 23 11:01 [EMAIL="system@00000000000000000000000000000000-0000000001044c9e-0005a8bd6ecfe4c3.journa"]system@00000000000000000000000000000000-0000000001044c9e-0005a8bd6ecfe4c3.journa[/EMAIL]l
 24M -rw-r-----+ 1 root systemd-journal  24M Jun 23 11:01 system.journal
8.0M -rw-r-----+ 1 root systemd-journal 8.0M Jun 23 11:01 user-1000.journal
```

System Details :

```
cat /etc/os-release

NAME="Ubuntu"
VERSION="20.04 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
```



Kindly guide me to resolve this issue at the earliest its very urgent, Thanks in advance.

Regards

---

### Post by slickymaster on 2020-06-23
Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output, because when posted as plain text it loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by deadflowr on 2020-06-23
Cleaning helps, but you need to post what the logs are saying.
If anything ever log spams it means an error is occurring.
Try taking a snippet of the logs before deleting them and post it.
Typically just copy the end of it with
```
journalctl -b | tail -n 100
```
to get the last 100 lines, which normally is enough to get a fair idea of the issues.

(Most of the time when logs get spammed it's one particular issue, repeating itself ad nauseam.

---

### Post by crusader5 on 2020-06-24
Hi All,

Thanks for the reply.

Here are few steps which I performed after looking at the logs.

In my /var/log  folder these two files were also taking up space.

```

ls -lsha
71G -rw-r-----   1 syslog            adm              71G Jun 24 15:51 kern.log
71G -rw-r-----   1 syslog            adm              71G Jun 24 15:52 syslog

```

as suggested by deadflowr did tailing on this files

```

sudo tail -n 10 /var/log/syslog
Jun 24 15:52:17 crusader update-notifier.desktop[3393]: Cannot stat file /proc/3137/fd/10: Permission denied
Jun 24 15:52:17 crusader update-notifier.desktop[3393]: Cannot stat file /proc/3137/fd/11: Permission denied
Jun 24 15:52:17 crusader update-notifier.desktop[3393]: Cannot stat file /proc/3137/fd/16: Permission denied
Jun 24 15:52:17 crusader update-notifier.desktop[3393]: Cannot stat file /proc/3137/fd/17: Permission denied
Jun 24 15:52:48 crusader gnome-shell[1903]: Some code accessed the property 'discreteGpuAvailable' on the module 'appDisplay'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Jun 24 15:52:48 crusader gnome-shell[1903]: ../clutter/clutter/clutter-actor.c:10556: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.

```

```

sudo tail -n 10 /var/log/kern.log
ieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID) Jun 2 pcieport 0000:00:1c.5: AER: device [8086:9d15] error status/mask=00000001/00002000 kernel: [ 178.057760] pcieport 0000:00:1c.5: AER: [ 0] RxErr


```

I opened the grub file and modified this line..

```

sudo nano /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT='quiet splash'

with this below line

GRUB_CMDLINE_LINUX_DEFAULT='quiet splash pci=noaer'


```

and rebooted my system and when I run top command now my cpu utilization is back to earlier. ie, systemd-journal process is not running and not utilizing 100% of my cpu usage.

While I was googling through found that if system was utilizing more power not sure about it but I connected the external air cooler pad in laptop usb and laptop exhaust was blowing out lot of hot air. was this because my system was unable to manage power management ? 


Any other steps do you suggest for me.

as of now system is running fine.

I also ran few commands to before running this commands.

```

sudo apt-get update
sudo apt-get dist-upgrade

```


Thanks will wait and watch the stability of my laptop hope it should work fine.

---

### Post by anarchy-x on 2020-06-29
Is this a fresh install or upgrade via apt?

---

### Post by oldfred on 2020-06-29
What brand/model system?

Some need boot parameters.

Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

