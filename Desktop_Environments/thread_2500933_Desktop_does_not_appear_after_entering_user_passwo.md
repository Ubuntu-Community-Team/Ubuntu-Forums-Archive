---
title: "Desktop does not appear after entering user password"
date: 2024-09-16
forum: Desktop Environments
---

### Post by grilli303 on 2024-09-16
[FONT=arial] [SIZE=2]Hi there[/SIZE]
[/FONT]
[FONT=arial][SIZE=2]Since a few days I have the following problem with Ubuntu 22.04.4 LTS on my Notebook.[/SIZE][/FONT]
[FONT=arial][SIZE=2]After I enter the user password, nothing happens for about 100 seconds. The screen is black and the mouse cursor is visible. 
After that, the login for my user usually appears again. Sometimes the login works after the second or third attempt, but each time with this long delay.[/SIZE][/FONT]
[FONT=arial][SIZE=2]It may also not work 10 times or more in a row. A restart has already helped in this case.[/SIZE][/FONT]
[FONT=arial][SIZE=2]As an attachment I have added a partial except of the end of my log file.[/SIZE][/FONT]

---

### Post by ActionParsnip on 2024-09-17
Do you have free space on the disk?
If you log in as a different user (Make a new one if needed), is it OK?

---

### Post by grilli303 on 2024-09-17
Hello ActionParsnip

Thanks for your answer. :P
The disc space on my system seems to be okay:

                       Dateisystem                           Größe Benutzt Verf. Verw% Eingehängt auf
tmpfs                                  1.5G    2.4M  1.5G    1% /run
/dev/nvme0n1p2                         916G     68G  802G    8% /
tmpfs                                  7.5G       0  7.5G    0% /dev/shm
tmpfs                                  5.0M    4.0K  5.0M    1% /run/lock
efivarfs                               148K     26K  118K   19% /sys/firmware/efi/efivars
/dev/nvme0n1p1                         511M     32M  480M    7% /boot/efi  

I will try to add a different user and look if the problem is still there.
I don't know if that's relevant. I have a dual boot system for Ununtu and Windows 10.
Unfortunately, I can't do without Windows completely yet.

---

### Post by grilli303 on 2024-09-17
I have now created a test user account. 
Under this account, the user login seems to proceed normally. 
With the existing user the login worked after the second attempt today. 
I have attached an updated log file again.

---

### Post by ActionParsnip on 2024-09-18
OK you may want to check your user is the owner of all of its home folder as a good start

---

### Post by grilli303 on 2024-09-18
As far as I can tell, it looks good in terms of user rights.


```
daniel@daniel-NL5xNU:/home$ ls -al
insgesamt 16
drwxr-xr-x  4 root     root     4096 Sep 17 12:40 .
drwxr-xr-x 20 root     root     4096 Aug  8 09:05 ..
drwxr-x--- 39 daniel   daniel   4096 Sep 15 14:30 daniel
drwxr-x--- 14 testuser testuser 4096 Sep 17 12:41 testuser

daniel@daniel-NL5xNU:~$ ls -al
insgesamt 103788
drwxr-x--- 39 daniel daniel      4096 Sep 15 14:30  .
drwxr-xr-x  4 root   root        4096 Sep 17 12:40  ..
drwxrwxr-x 11 daniel daniel      4096 Aug 11 20:24  Arduino
drwxr-xr-x  6 daniel daniel      4096 Dez  6  2022  .arduino15
drwxrwxr-x  7 daniel daniel      4096 Dez  6  2022  .arduinoIDE
drwxrwxr-x  5 daniel daniel      4096 Jun 30 10:54  .audacity-data
-rw-rw-r--  1 daniel daniel    770334 Dez 15  2023 'Avery Print from the Web, v5 Document - Avery4780UniversalEtiketten.pdf'
-rw-------  1 daniel daniel     13527 Sep 17 12:26  .bash_history
-rw-r--r--  1 daniel daniel       220 Okt  4  2022  .bash_logout
-rw-r--r--  1 daniel daniel      3771 Okt  4  2022  .bashrc
drwxr-xr-x  5 daniel daniel      4096 Aug  5 11:54  Bilder
drwx------ 45 daniel daniel      4096 Sep 13 02:06  .cache
drwx------ 51 daniel daniel      4096 Sep 17 13:23  .config
drwxrwxr-x  2 daniel daniel      4096 Jun  7 13:03  .deepin-screen-recorder
drwxr-xr-x  2 daniel daniel      4096 Sep 17 12:26  Dokumente
drwxr-xr-x  4 daniel daniel     12288 Sep 17 13:26  Downloads
drwxr-xr-x  2 root   root        4096 Nov 29  2023  DTVP
drwx------  3 daniel daniel      4096 Nov 21  2023  .gnome
drwx------  2 daniel daniel      4096 Sep 16 12:51  .gnupg
-rw-rw-r--  1 daniel daniel 103884100 Nov 13  2023  google-chrome-stable_current_amd64.deb
drwxrwxr-x  2 daniel daniel      4096 Sep 15 14:30  .gphoto
drwxrwxr-x  4 daniel daniel      4096 Feb  7  2023  .java
-rw-------  1 daniel daniel        20 Dez 11  2023  .lesshst
-rw-rw-r--  1 daniel daniel    555355 Jan 11  2023 'Lidl 3.jpeg'
drwx------  3 daniel daniel      4096 Okt  4  2022  .local
drwxrwxr-x  4 daniel daniel      4096 Dez 11  2023  .mcf
drwxrwxr-x  4 daniel daniel      4096 Feb 12  2024  .Mediapurge
-rw-r--r--  1 daniel daniel     22204 Nov 27  2023  mono_crash.d4716fb0.0.json
-rw-r--r--  1 daniel daniel      6467 Jan 15  2024  mono_crash.d4716fb0.1.json
-rw-r--r--  1 daniel daniel      6467 Jan 15  2024  mono_crash.d4716fb0.2.json
-rw-r--r--  1 daniel daniel      6467 Mai 29 17:35  mono_crash.d4716fb0.3.json
-rw-r--r--  1 daniel daniel      6467 Mai 29 18:24  mono_crash.d4716fb0.4.json
-rw-r--r--  1 daniel daniel     16315 Nov 16  2023  mono_crash.eae31791.0.json
-rw-r--r--  1 daniel daniel      7170 Nov 27  2023  mono_crash.eae31791.1.json
-rw-r--r--  1 daniel daniel     23508 Feb  1  2024  mono_crash.eae31791.2.json
-rw-r--r--  1 daniel daniel    500001 Feb  1  2024  mono_crash.mem.3256.1.blob
drwx------  3 daniel daniel      4096 Okt  5  2022  .mozilla
drwxr-xr-x  4 daniel daniel      4096 Aug 17 11:47  Musik
drwxr-xr-x  2 daniel daniel      4096 Okt  4  2022  Öffentlich
drwxrwxr-x  3 daniel daniel      4096 Mai 29 18:21  .openjfx
drwxr-xr-x  9 daniel daniel      4096 Mai 29 17:53  pdfstudio2024
drwxrwxr-x  3 daniel daniel      4096 Dez 11  2023  Pixum
drwx------  3 daniel daniel      4096 Nov  3  2022  .pki
drwxrwxr-x 14 daniel daniel      4096 Aug 30 13:55  .PlayOnLinux
lrwxrwxrwx  1 daniel daniel        38 Okt  4  2022 "PlayOnLinux's virtual drives" -> /home/daniel/.PlayOnLinux//wineprefix/
-rw-r--r--  1 daniel daniel       807 Okt  4  2022  .profile
-rw-rw-r--  1 daniel daniel     48776 Mai 29 18:43  .sambox.cache
drwxr-xr-x  2 daniel daniel      4096 Jul  6 14:47  Schreibtisch
-rw-rw-r--  1 daniel daniel      2223 Aug  4  2023  signal-desktop-keyring.gpg
-rw-rw-r--  1 daniel daniel        34 Okt  4  2022  .smbcredentials
drwx------ 16 daniel daniel      4096 Jun  7 12:20  snap
drwxrwxr-x  3 daniel daniel      4096 Okt 28  2022  snowflake-ssh
drwx------  2 daniel daniel      4096 Okt 27  2022  .ssh
-rw-r--r--  1 daniel daniel         0 Okt  4  2022  .sudo_as_admin_successful
drwxrwxr-x  3 daniel daniel      4096 Feb  7  2023  .swt
-rw-rw-r--  1 daniel daniel    577988 Jun 30 10:54  telefonbrummen.mp3
-rw-rw-r--  1 daniel daniel     94426 Jun  7 11:53  test
drwx------  6 daniel daniel      4096 Okt  5  2022  .thunderbird
drwxr-xr-x  3 daniel daniel      4096 Nov 27  2023  .var
drwxr-xr-x  4 daniel daniel      4096 Sep 15 15:38  Videos
drwx------  5 daniel daniel      4096 Aug 25 18:10  .vnc
drwxr-xr-x  2 daniel daniel      4096 Okt  4  2022  Vorlagen
drwxrwxr-x  3 daniel daniel      4096 Mär  4  2023  .vscode
-rw-rw-r--  1 daniel daniel       179 Okt  4  2022  .wget-hsts
-rw-rw-r--  1 daniel daniel      1263 Feb  2  2024  .xmlcopyeditor
daniel@daniel-NL5xNU:~$
```

---

### Post by grilli303 on 2024-09-21
**I Found this error messages in journalctrl:**

Mai 10 11:03:13 daniel-NL5xNU canonical-livepatch.canonical-livepatchd[837]: Error in livepatch check state: check-failed.


 Mai 10 11:03:13 daniel-NL5xNU canonical-livepatch.canonical-livepatchd[837]: Task "refresh" completed succesfully after 1 retries.


 Mai 10 11:03:30 daniel-NL5xNU gnome-shell[1890]: Error creating proxy: Fehler beim Aufruf von StartServiceByName für org.gtk.vfs.UDisks2VolumeMonitor: Zeitüberschreitung wurde erreich>

                        
 Mai 10 11:03:32 daniel-NL5xNU systemd[1717]: Dependency failed for GNOME XSettings service.


 gnome-session-x11-services-ready.target/verify-active failed with result 'dependency'.

---

### Post by grilli303 on 2024-09-27
Today I installed the latest update offered to me by Ubuntu. 
At the moment, the desktop usually appears on the first login attempt, but it still takes an unusually long time, when I log in until the desktop appears (about 90 seconds). 
With an AMD Ryzen 7 5700U with Radeon Graphics, this shouldn't take that long....
I'm wondering what could be causing this delay and what commands I could use in the terminal to track down the problem.

---

### Post by him610 on 2024-09-27
> I'm wondering what could be causing this delay and what commands I could use in the terminal to track down the problem.
Try this....
```
systemd-analyze blame
```
Post results between code tags.

---

### Post by grilli303 on 2024-09-29
@ him660:
Thank you for your answer.
I'm not shure, what you meant with "Post results between code tags"
hopefully it's ok how I post the result.

Kind regards, Daniel

```
Daniel@daniel-NL5xNU:~$ systemd-analyze blame
6.408s NetworkManager-wait-online.service
3.397s snapd.seeded.service
3.255s snapd.service
2.200s binfmt-support.service
2.198s apparmor.service
2.196s systemd-binfmt.service
2.178s proc-sys-fs-binfmt_misc.mount
2.158s run-rpc_pipefs.mount
2.154s rpcbind.service
2.144s plymouth-quit-wait.service
1.682s dev-nvme0n1p2.device
1.592s dev-loop7.device
1.591s dev-loop3.device
1.589s dev-loop5.device
1.588s dev-loop4.device
1.588s dev-loop6.device
1.579s dev-loop2.device
1.575s dev-loop1.device
1.573s systemd-udev-trigger.service
1.570s dev-loop0.device
1.086s fwupd.service
 756ms media-DS_scans.mount
 681ms media-Dokumente_zum_ablegen.mount
 608ms media-video.mount
 564ms logrotate.service
 542ms media-photo.mount
 476ms media-DS_music.mount
 399ms media-Daten.mount
 317ms media-Haussteuerung.mount
 272ms systemd-resolved.service
 238ms accounts-daemon.service
 167ms user@1000.service
 155ms bluetooth.service
 152ms networkd-dispatcher.service
 151ms udisks2.service
 147ms e2scrub_reap.service
 141ms systemd-timesyncd.service
 137ms systemd-oomd.service
 133ms systemd-journald.service
 132ms systemd-journal-flush.service
 127ms systemd-logind.service
 111ms dev-loop12.device
 111ms dev-loop11.device
 110ms dev-loop23.device
 109ms dev-loop21.device
 109ms dev-loop30.device
 108ms dev-loop29.device
 108ms dev-loop22.device
 108ms dev-loop10.device
 108ms dev-loop42.device
 108ms dev-loop40.device
 108ms dev-loop27.device
 108ms dev-loop17.device
 107ms dev-loop43.device
lines 1-54
```

The boot process itself is normal. 
**The delay occurs only after the user login until the desktop appears.**

---

