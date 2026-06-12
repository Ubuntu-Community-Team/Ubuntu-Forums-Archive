---
title: "Firefox misery"
date: 2009-06-09
forum: General Help
---

### Post by rolo550 on 2009-06-09
Having much misery with firefox. 

It was having a flash problem and at one point i reinstalled firefox,

Now it wont run form the shortcut or command line, but if i run "sudo firefox" at the command line it works fine.  Any ideas?

---

### Post by H2SO_four on 2009-06-09
try opera :) You may like it.

---

### Post by rolo550 on 2009-06-09
i might, but i'm a big firefox fan...have several other boxes with synced bookmarks, etc...

thanks for the advice

---

### Post by synapsys on 2009-06-09
Maybe the permissions of the firefox executable are not allowing you to run as a normal user. Please post output of this command so that I may further help you:

```
ls -l /usr/bin/
```

---

### Post by rolo550 on 2009-06-09
-rwxr-xr-x 1 root   root        396 2009-04-08 19:11 pulse-session
-rwxr-xr-x 1 root   root       8021 2009-06-01 09:45 purple-remote
-rwxr-xr-x 1 root   root        782 2009-06-01 09:45 purple-send
-rwxr-xr-x 1 root   root        647 2009-06-01 09:45 purple-send-async
-rwxr-xr-x 1 root   root      12122 2009-06-01 09:45 purple-url-handler
-rwxr-xr-x 1 root   root       5480 2009-03-18 17:17 pwdx
-rwxr-xr-x 1 root   root       3751 2009-04-16 22:57 py3_compilefiles
-rwxr-xr-x 1 root   root      90048 2009-04-16 22:57 pycentral
-rwxr-xr-x 1 root   root       3723 2009-04-16 22:57 py_compilefiles
lrwxrwxrwx 1 root   root          8 2009-06-09 08:03 pydoc -> pydoc2.6
-rwxr-xr-x 1 root   root         79 2009-04-18 21:44 pydoc2.6
lrwxrwxrwx 1 root   root         12 2009-06-09 08:03 pygettext -> pygettext2.6
-rwxr-xr-x 1 root   root      22103 2009-04-18 21:44 pygettext2.6
-rwxr-xr-x 1 root   root       4902 2009-04-09 20:33 pysupport-movemodules
-rwxr-xr-x 1 root   root       2441 2006-11-23 15:26 pysupport-parseversions
lrwxrwxrwx 1 root   root          9 2009-06-09 08:03 python -> python2.6
-rwxr-xr-x 1 root   root    2268568 2009-04-18 21:53 python2.6
lrwxrwxrwx 1 root   root         29 2009-06-09 08:03 pyversions -> ../share/python/pyversions.py
-rwxr-xr-x 1 root   root      53436 2009-03-27 05:21 qpdldecode
-rwxr-xr-x 1 root   root      50904 2009-02-10 10:13 ranlib
-rwxr-xr-x 1 root   root       5468 2008-10-15 19:32 rarian-example
-rwxr-xr-x 1 root   root       1495 2008-10-15 19:32 rarian-sk-config
-rwxr-xr-x 1 root   root        563 2008-10-15 19:32 rarian-sk-extract
-rwxr-xr-x 1 root   root       5456 2008-10-15 19:32 rarian-sk-gen-uuid
-rwxr-xr-x 1 root   root      67344 2008-10-15 19:32 rarian-sk-get-cl
-rwxr-xr-x 1 root   root        399 2008-10-15 19:32 rarian-sk-get-content-list
-rwxr-xr-x 1 root   root        419 2008-10-15 19:32 rarian-sk-get-extended-content-list
-rwxr-xr-x 1 root   root        382 2008-10-15 19:32 rarian-sk-get-scripts
-rwxr-xr-x 1 root   root       1171 2008-10-15 19:32 rarian-sk-install
-rwxr-xr-x 1 root   root      75536 2008-10-15 19:32 rarian-sk-migrate
-rwxr-xr-x 1 root   root      67316 2008-10-15 19:32 rarian-sk-preinstall
-rwxr-xr-x 1 root   root        821 2008-10-15 19:32 rarian-sk-rebuild
-rwxr-xr-x 1 root   root       9525 2008-10-15 19:32 rarian-sk-update
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 rcp -> /etc/alternatives/rcp
-rwxr-xr-x 1 root   root     224376 2008-08-20 20:43 rdesktop
-rwxr-xr-x 1 root   root        258 2009-02-22 07:15 rdfpipe
-rwxr-xr-x 1 root   root     286320 2009-02-10 10:13 readelf
-rwxr-xr-x 1 root   root     172664 2008-11-12 08:12 readom
lrwxrwxrwx 1 root   root          7 2009-06-09 08:03 red -> /bin/ed
lrwxrwxrwx 1 root   root         24 2009-06-09 08:03 rename -> /etc/alternatives/rename
-rwxr-xr-x 1 root   root       5476 2009-02-18 13:43 rename.ul
-rwxr-xr-x 1 root   root       5468 2009-02-18 13:43 renice
lrwxrwxrwx 1 root   root          4 2009-06-09 08:03 reset -> tset
-rwxr-xr-x 1 root   root       9620 2009-02-26 22:22 resize
-rwxr-xr-x 1 root   root      13808 2009-04-09 19:51 resizecons
-rwxr-xr-x 1 root   root       5488 2009-02-18 13:43 rev
-rwxr-xr-x 1 root   root      34848 2009-04-24 05:27 rfcomm
-rwxr-xr-x 1 root   root         30 2008-11-04 15:15 rgrep
-rwxr-xr-x 1 root   root     640748 2009-04-07 18:52 rhythmbox
-rwxr-xr-x 1 root   root      22816 2009-04-07 18:52 rhythmbox-client
lrwxrwxrwx 1 root   root         24 2009-06-09 08:03 rlogin -> /etc/alternatives/rlogin
-rwxr-xr-x 1 root   root        173 2008-07-25 15:46 routef
-rwxr-xr-x 1 root   root       1262 2008-07-25 15:46 routel
-rwxr-xr-x 1 root   root    4443208 2009-03-27 11:19 rpcclient
-rwxr-xr-x 1 root   root      79628 2009-04-09 03:19 rpcgen
-rwxr-xr-x 1 root   root      13740 2009-04-09 03:19 rpcinfo
-rwxr-xr-x 1 root   root      21892 2009-02-12 03:18 rpl8
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 rsh -> /etc/alternatives/rsh
-rwxr-xr-x 1 root   root       3148 2009-01-13 22:26 rss-glx_install
-rwxr-xr-x 1 root   root       2613 2007-11-07 13:04 rstart
-rwxr-xr-x 1 root   root       1435 2007-11-07 13:04 rstartd
-rwxr-xr-x 1 root   root     372432 2009-02-26 19:28 rsync
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 rtstat -> lnstat
-rwxr-xr-x 1 root   root      30348 2008-06-26 19:31 runcon
-rwxr-xr-x 1 root   root      16292 2008-06-19 07:50 run-mailcap
-rwxr-xr-x 1 root   root         57 2008-08-20 04:56 run-with-aspell
lrwxrwxrwx 1 root   root         23 2009-06-09 08:03 rview -> /etc/alternatives/rview
-rwxr-xr-x 1 root   root      53325 2009-01-05 14:22 s2p
-rwxr-xr-x 1 root   root     112712 2009-03-27 02:54 sane-find-scanner
-rwxr-xr-x 1 root   root       2346 2008-05-03 02:33 sas_disk_blink
-rwxr-xr-x 1 root   root       9434 2009-02-16 15:27 savelog
-rwxr-xr-x 1 root   root      42884 2009-03-27 02:54 scanimage
-rwxr-xr-x 1 root   root      26200 2009-03-09 12:37 scim
-rwxr-xr-x 1 root   root     166108 2008-10-26 16:54 scim-bridge
-rwxr-xr-x 1 root   root      30396 2009-03-09 12:37 scim-config-agent
-rwxr-xr-x 1 root   root       1146 2009-03-09 12:36 scim-setup
-rwxr-xr-x 1 root   root      50932 2009-01-28 15:01 scp
-rwxr-xr-x 1 root   root       2281 2009-04-08 17:05 screen
-rwxr-xr-x 1 root   root       9592 2009-04-09 19:51 screendump
-rwxr-xr-x 1 root   root       1042 2009-04-08 17:05 screen-launcher
-rwxr-xr-x 1 root   root      15823 2009-04-08 17:05 screen-profiles
-rwxr-xr-x 1 root   root       5937 2009-04-08 17:05 screen-profiles-export
-rwxr-xr-x 1 root   root       1857 2009-04-23 06:13 screen-profiles-status
-rwxr-sr-x 1 root   utmp     336452 2009-02-11 06:17 screen.real
-rwxr-xr-x 1 root   root      13768 2009-02-18 13:43 script
-rwxr-xr-x 1 root   root       9600 2009-02-18 13:43 scriptreplay
lrwxrwxrwx 1 root   root         16 2009-06-09 08:03 scrollkeeper-config -> rarian-sk-config
lrwxrwxrwx 1 root   root         17 2009-06-09 08:03 scrollkeeper-extract -> rarian-sk-extract
lrwxrwxrwx 1 root   root         18 2009-06-09 08:03 scrollkeeper-gen-seriesid -> rarian-sk-gen-uuid
lrwxrwxrwx 1 root   root         16 2009-06-09 08:03 scrollkeeper-get-cl -> rarian-sk-get-cl
lrwxrwxrwx 1 root   root         26 2009-06-09 08:03 scrollkeeper-get-content-list -> rarian-sk-get-content-list
lrwxrwxrwx 1 root   root         35 2009-06-09 08:03 scrollkeeper-get-extended-content-list -> rarian-sk-get-extended-content-list
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 scrollkeeper-get-index-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 scrollkeeper-get-toc-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 scrollkeeper-get-toc-from-id -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root         17 2009-06-09 08:03 scrollkeeper-install -> rarian-sk-install
lrwxrwxrwx 1 root   root         20 2009-06-09 08:03 scrollkeeper-preinstall -> rarian-sk-preinstall
lrwxrwxrwx 1 root   root         17 2009-06-09 08:03 scrollkeeper-rebuilddb -> rarian-sk-rebuild
lrwxrwxrwx 1 root   root         17 2009-06-09 08:03 scrollkeeper-uninstall -> rarian-sk-install
lrwxrwxrwx 1 root   root         16 2009-06-09 08:03 scrollkeeper-update -> rarian-sk-update
-rwxr-xr-x 1 root   root       7733 2008-05-03 02:33 scsi_logging_level
-rwxr-xr-x 1 root   root       3272 2008-05-03 02:33 scsi_mandat
-rwxr-xr-x 1 root   root       1061 2008-05-03 02:33 scsi_readcap
-rwxr-xr-x 1 root   root        891 2008-05-03 02:33 scsi_ready
-rwxr-xr-x 1 root   root       3663 2008-05-03 02:33 scsi_satl
-rwxr-xr-x 1 root   root       1050 2008-05-03 02:33 scsi_start
-rwxr-xr-x 1 root   root       1058 2008-05-03 02:33 scsi_stop
-rwxr-xr-x 1 root   root        936 2008-05-03 02:33 scsi_temperature
-rwxr-xr-x 1 root   root      19012 2007-05-04 11:41 sdiff
-rwxr-xr-x 1 root   root      83592 2009-04-24 05:27 sdptool
-rwxr-xr-x 1 root   root     612220 2009-04-13 05:52 seahorse
-rwxr-xr-x 1 root   root     126324 2009-04-14 05:45 seahorse-agent
-rwxr-xr-x 1 root   root     521384 2009-04-13 05:52 seahorse-daemon
-rwxr-xr-x 1 root   root     105504 2009-04-14 05:45 seahorse-preferences
-rwxr-xr-x 1 root   root     156444 2009-04-14 05:45 seahorse-tool
lrwxrwxrwx 1 root   root         11 2009-06-09 08:03 see -> run-mailcap
-rwxr-xr-x 1 root   root        474 2009-02-20 14:09 select-default-iwrap
-rwxr-xr-x 1 root   root       1197 2009-02-16 15:27 select-editor
-rwxr-xr-x 1 root   root       4201 2009-04-08 17:05 select-screen-profile
-rwxr-xr-x 1 root   root       1388 2009-02-16 15:27 sensible-browser
-rwxr-xr-x 1 root   root        845 2009-02-16 15:27 sensible-editor
-rwxr-xr-x 1 root   root        288 2009-02-16 15:27 sensible-pager
-rwxr-xr-x 1 root   root      30172 2008-06-26 19:31 seq
-rwxr-xr-x 1 root   root       4127 2009-03-31 04:02 service
-rwxr-xr-x 1 root   root      65296 2009-04-24 06:32 services-admin
-rwxr-xr-x 1 root   root       9604 2009-02-27 13:35 sessreg
-rwxr-xr-x 1 root   root       9848 2009-02-18 13:43 setarch
-rwxr-xr-x 1 root   root      26560 2008-05-02 19:01 setfacl
-rwxr-xr-x 1 root   root       5476 2009-04-09 19:51 setkeycodes
-rwxr-xr-x 1 root   root       9628 2009-04-09 19:51 setleds
-rwxr-xr-x 1 root   root       5468 2009-04-09 19:51 setlogcons
-rwxr-xr-x 1 root   root       5548 2009-04-09 19:51 setmetamode
-rwxr-xr-x 1 root   root      13736 2009-03-18 19:29 setpci
-rwxr-xr-x 1 root   root       5464 2009-02-18 13:43 setsid
-rwxr-xr-x 1 root   root      22176 2009-02-18 13:43 setterm
-rwxr-xr-x 1 root   root      17972 2009-03-30 18:17 setxkbmap
-rwxr-xr-x 1 root   root      87892 2009-01-28 15:01 sftp
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 sg -> newgrp
-rwxr-xr-x 1 root   root      38420 2008-05-03 02:33 sg_dd
-rwxr-xr-x 1 root   root       9560 2008-05-03 02:33 sg_emc_trespass
-rwxr-xr-x 1 root   root      18140 2008-05-03 02:33 sg_format
-rwxr-xr-x 1 root   root      26192 2008-05-03 02:33 sg_get_config
-rwxr-xr-x 1 root   root      13868 2008-05-03 02:33 sg_ident
-rwxr-xr-x 1 root   root      64088 2008-05-03 02:33 sginfo
-rwxr-xr-x 1 root   root      59400 2008-05-03 02:33 sg_inq
-rwxr-xr-x 1 root   root      67420 2008-05-03 02:33 sg_logs
-rwxr-xr-x 1 root   root      13864 2008-05-03 02:33 sg_luns
-rwxr-xr-x 1 root   root      13716 2008-05-03 02:33 sg_map
-rwxr-xr-x 1 root   root      22140 2008-05-03 02:33 sg_map26
-rwxr-xr-x 1 root   root      30212 2008-05-03 02:33 sgm_dd
-rwxr-xr-x 1 root   root      27320 2008-05-03 02:33 sg_modes
-rwxr-xr-x 1 root   root      18108 2008-05-03 02:33 sg_opcodes
-rwxr-xr-x 1 root   root      38472 2008-05-03 02:33 sgp_dd
-rwxr-xr-x 1 root   root      22412 2008-05-03 02:33 sg_persist
-rwxr-xr-x 1 root   root       9692 2008-05-03 02:33 sg_prevent
-rwxr-xr-x 1 root   root      13976 2008-05-03 02:33 sg_raw
-rwxr-xr-x 1 root   root      18092 2008-05-03 02:33 sg_rbuf
-rwxr-xr-x 1 root   root       9572 2008-05-03 02:33 sg_rdac
-rwxr-xr-x 1 root   root      21936 2008-05-03 02:33 sg_read
-rwxr-xr-x 1 root   root       9792 2008-05-03 02:33 sg_read_buffer
-rwxr-xr-x 1 root   root      13916 2008-05-03 02:33 sg_readcap
-rwxr-xr-x 1 root   root       9792 2008-05-03 02:33 sg_read_long
-rwxr-xr-x 1 root   root      13900 2008-05-03 02:33 sg_reassign
-rwxr-xr-x 1 root   root       9788 2008-05-03 02:33 sg_requests
-rwxr-xr-x 1 root   root       5456 2008-05-03 02:33 sg_reset
-rwxr-xr-x 1 root   root       9672 2008-05-03 02:33 sg_rmsn
-rwxr-xr-x 1 root   root       9704 2008-05-03 02:33 sg_rtpg
-rwxr-xr-x 1 root   root       9776 2008-05-03 02:33 sg_sat_identify
-rwxr-xr-x 1 root   root      13728 2008-05-03 02:33 sg_scan
-rwxr-xr-x 1 root   root      18228 2008-05-03 02:33 sg_senddiag
-rwxr-xr-x 1 root   root      43184 2008-05-03 02:33 sg_ses
-rwxr-xr-x 1 root   root      13916 2008-05-03 02:33 sg_start
-rwxr-xr-x 1 root   root       9736 2008-05-03 02:33 sg_sync
-rwxr-xr-x 1 root   root      18012 2008-05-03 02:33 sg_test_rwbuf
-rwxr-xr-x 1 root   root       9768 2008-05-03 02:33 sg_turs
-rwxr-xr-x 1 root   root       9724 2008-05-03 02:33 sg_verify
-rwxr-xr-x 1 root   root      39256 2008-05-03 02:33 sg_vpd
-rwxr-xr-x 1 root   root      13936 2008-05-03 02:33 sg_write_buffer
-rwxr-xr-x 1 root   root       9808 2008-05-03 02:33 sg_write_long
-rwxr-xr-x 1 root   root      13900 2008-05-03 02:33 sg_wr_mode
-rwxr-xr-x 1 root   root      38432 2008-06-26 19:31 sha1sum
-rwxr-xr-x 1 root   root      46628 2008-06-26 19:31 sha224sum
-rwxr-xr-x 1 root   root      46628 2008-06-26 19:31 sha256sum
-rwxr-xr-x 1 root   root      87588 2008-06-26 19:31 sha384sum
-rwxr-xr-x 1 root   root      87588 2008-06-26 19:31 sha512sum
-rwxr-xr-x 1 root   root      82256 2009-04-24 06:32 shares-admin
-rwxr-xr-x 1 root   root       7655 2009-01-05 14:22 shasum
-rwxr-xr-x 1 root   root      13720 2009-04-09 19:51 showconsolefont
-rwxr-xr-x 1 root   root       9612 2009-03-18 21:19 showfont
-rwxr-xr-x 1 root   root       9592 2009-04-09 19:51 showkey
-rwxr-xr-x 1 root   root       5464 2009-02-27 13:35 showrgb
-rwxr-xr-x 1 root   root      50832 2008-06-26 19:31 shred
-rwxr-xr-x 1 root   root      38472 2008-06-26 19:31 shuf
-rwxr-xr-x 1 root   root      26444 2009-02-10 10:13 size
-rwxr-xr-x 1 root   root      13748 2009-03-18 17:17 skill
-rwxr-xr-x 1 root   root      13724 2009-03-18 17:17 slabtop
lrwxrwxrwx 1 root   root          3 2009-06-09 08:03 slogin -> ssh
-rwxr-xr-x 1 root   root      57564 2009-03-27 05:21 slxdecode
-rwxr-xr-x 1 root   root      88676 2009-03-27 11:42 smartdimmer
-rwxr-xr-x 1 root   root    3892232 2009-03-27 11:19 smbcacls
-rwxr-xr-x 1 root   root    3974472 2009-03-27 11:19 smbclient
-rwxr-xr-x 1 root   root    3892200 2009-03-27 11:19 smbcquotas
-rwxr-xr-x 1 root   root    4001924 2009-03-27 11:19 smbget
-rwxr-xr-x 1 root   root    3858472 2009-03-27 11:19 smbpasswd
-rwxr-xr-x 1 root   root     998024 2009-03-27 11:19 smbspool
-rwxr-xr-x 1 root   root       4910 2009-03-27 11:18 smbtar
-rwxr-xr-x 1 root   root    3855332 2009-03-27 11:19 smbtree
-rwxr-xr-x 1 root   root      15876 2007-11-07 13:04 smproxy
lrwxrwxrwx 1 root   root          5 2009-06-09 08:03 snice -> skill
-rwxr-xr-x 1 root   root      22076 2009-03-18 21:05 soelim
lrwxrwxrwx 1 root   root         33 2009-06-09 08:03 soffice -> ../lib/openoffice/program/soffice
-rwxr-xr-x 1 root   root       3909 2009-03-27 10:33 software-properties-gtk
-rwxr-xr-x 1 root   root      71376 2008-06-26 19:31 sort
-rwxr-xr-x 1 root   root      22096 2009-04-07 19:07 speaker-test
-rwxr-xr-x 1 root   root      18132 2009-02-23 18:32 speechd-synthesis-driver
-rwxr-xr-x 1 root   root      17452 2009-01-05 14:22 splain
-rwxr-xr-x 1 root   root      34348 2008-06-26 19:31 split
-rwxr-xr-x 1 root   root       5472 2009-04-09 19:51 splitfont
-rwxr-xr-x 1 root   root      22016 2009-04-09 03:19 sprof
-rwxr-xr-x 1 root   root     318812 2009-01-28 15:01 ssh
-rwxr-xr-x 1 root   root     100940 2009-01-28 15:01 ssh-add
-rwxr-sr-x 1 root   ssh       83956 2009-01-28 15:01 ssh-agent
-rwxr-xr-x 1 root   root       1452 2009-01-28 15:01 ssh-argv0
lrwxrwxrwx 1 root   root         29 2009-06-09 08:03 ssh-askpass -> /etc/alternatives/ssh-askpass
-rwxr-xr-x 1 root   root       1316 2009-01-28 15:01 ssh-copy-id
-rwxr-xr-x 1 root   root     125648 2009-01-28 15:01 ssh-keygen
-rwxr-xr-x 1 root   root     170880 2009-01-28 15:01 ssh-keyscan
-rwxr-xr-x 1 root   root      88592 2009-01-28 15:01 ssh-vulnkey
-rwxr-xr-x 1 root   root       1074 2009-04-08 19:09 start-pulseaudio-x11
-rwxr-xr-x 1 root   root       4473 2008-05-29 07:53 startx
-rwxr-xr-x 1 root   root      46652 2008-06-26 19:31 stat
-rwxr-xr-x 1 root   root     202616 2008-12-09 13:15 strace
-rwxr-xr-x 1 root   root      26428 2009-02-10 10:13 strings
-rwxr-xr-x 1 root   root     192032 2009-02-10 10:13 strip
-rwsr-xr-x 1 root   root     115136 2009-02-16 21:22 sudo
-rwsr-xr-x 1 root   root     115136 2009-02-16 21:22 sudoedit
-rwxr-xr-x 1 root   root      34344 2008-06-26 19:31 sum
-rwxr-xr-x 1 root   root      11420 2009-04-03 14:07 synclient
-rwxr-xr-x 1 root   root      13772 2009-04-03 14:07 syndaemon
-rwxr-xr-x 1 root   root      28956 2008-07-15 08:06 syslinux
-rwxr-xr-x 1 root   root       1421 2008-07-15 08:06 syslinux2ansi
-rwxr-xr-x 1 root   root         95 2009-04-23 06:08 system-config-printer
-rwxr-xr-x 1 root   root         80 2009-04-23 06:08 system-config-printer-applet
-rwxr-xr-x 1 root   root      22300 2009-04-09 22:04 system-tools-backends
-rwxr-xr-x 1 root   root       9644 2009-02-12 02:50 tabs
-rwxr-xr-x 1 root   root      30260 2008-06-26 19:31 tac
-rwxr-xr-x 1 root   root      50792 2008-06-26 19:31 tail
-rwxr-xr-x 1 root   root      22211 2009-03-17 07:45 tasksel
-rwxr-xr-x 1 root   root       9600 2009-02-18 13:43 taskset
-rwxr-xr-x 1 root   root      99940 2009-03-18 21:05 tbl
-rwxr-xr-x 1 root   root      26072 2008-06-26 19:31 tee
lrwxrwxrwx 1 root   root         24 2009-06-09 08:03 telnet -> /etc/alternatives/telnet
-rwxr-xr-x 1 root   root      84096 2009-01-21 06:27 telnet.netkit
-rwxr-xr-x 1 root   root      26120 2008-06-26 19:31 test
lrwxrwxrwx 1 root   root         26 2009-06-09 08:03 testparm -> /etc/alternatives/testparm
-rwxr-xr-x 1 root   root     785676 2009-03-27 11:19 testparm.samba3
-rwxr-xr-x 1 root   root      13888 2009-02-23 18:32 test-speech
-rwxr-xr-x 1 root   root       1573 2008-05-29 15:55 tgz
-rwxr-xr-x 1 root   root      50792 2009-02-12 02:50 tic
-rwxr-xr-x 1 root   root      13904 2008-11-05 17:14 time
-rwxr-xr-x 1 root   root      98924 2009-04-24 06:32 time-admin
-rwxr-xr-x 1 root   root       9612 2009-03-18 17:17 tload
-rwxr-xr-x 1 root   root       9660 2009-02-12 02:50 toe
-rwxr-xr-x 1 root   root       1589 2009-03-17 04:10 tomboy
-rwxr-xr-x 1 root   root        377 2009-03-17 04:10 tomboy-panel
-rwxr-xr-x 1 root   root      72600 2009-03-18 17:17 top
-rwxr-xr-x 1 root   root      84824 2008-11-05 17:48 toshset
lrwxrwxrwx 1 root   root         23 2009-06-09 08:03 totem -> /etc/alternatives/totem
lrwxrwxrwx 1 root   root         37 2009-06-09 08:03 totem-audio-preview -> /etc/alternatives/totem-audio-preview
-rwxr-xr-x 1 root   root     422148 2009-04-14 05:54 totem-gstreamer
-rwxr-xr-x 1 root   root     138932 2009-04-14 05:54 totem-gstreamer-audio-preview
-rwxr-xr-x 1 root   root     138936 2009-04-14 05:54 totem-gstreamer-video-indexer
-rwxr-xr-x 1 root   root     150560 2009-04-14 05:54 totem-gstreamer-video-thumbnailer
lrwxrwxrwx 1 root   root         37 2009-06-09 08:03 totem-video-indexer -> /etc/alternatives/totem-video-indexer
lrwxrwxrwx 1 root   root         41 2009-06-09 08:03 totem-video-thumbnailer -> /etc/alternatives/totem-video-thumbnailer
lrwxrwxrwx 1 root   root         10 2009-06-09 08:03 touch -> /bin/touch
-rwxr-xr-x 1 root   root       9688 2009-02-12 02:50 tput
-rwxr-xr-x 1 root   root      42516 2008-06-26 19:31 tr
-rwxr-xr-x 1 root   root       8140 2007-12-10 11:33 tracepath
-rwxr-xr-x 1 root   root       9356 2007-12-10 11:33 tracepath6
lrwxrwxrwx 1 root   root         29 2009-06-09 08:03 traceroute6 -> /etc/alternatives/traceroute6
-rwsr-xr-x 1 root   root      12296 2007-12-10 11:33 traceroute6.iputils
-rwxr-xr-x 1 root   root     710076 2009-03-30 05:19 transmission
-rwxr-xr-x 1 root   root     346260 2009-03-18 21:05 troff
-rwxr-xr-x 1 root   root      92296 2009-04-01 21:31 tsclient
-rwxr-xr-x 1 root   root      17956 2009-02-12 02:50 tset
-rwxr-xr-x 1 root   root      34252 2008-06-26 19:31 tsort
-rwxr-xr-x 1 root   root      26048 2008-06-26 19:31 tty
-rwxr-xr-x 1 root   root       6894 2009-04-09 03:03 tzselect
-rwxr-xr-x 1 root   root       1979 2009-04-29 09:24 ubuntu-bug
-rwxr-xr-x 1 root   root      35643 2009-01-25 10:52 ucf
-rwxr-xr-x 1 root   root      19290 2008-05-30 01:22 ucfq
-rwxr-xr-x 1 root   root      10405 2008-05-30 01:22 ucfr
-rwxr-xr-x 1 root   root      17972 2008-06-17 21:55 ucs2any
-rwxr-xr-x 1 root   root       9592 2008-11-04 15:43 ul
-rwxr-xr-x 1 root   root     178740 2009-03-27 02:54 umax_pp
-rwxr-xr-x 1 root   root      14130 2009-03-02 04:07 unattended-upgrade
-rwxr-xr-x 1 root   root      30228 2008-06-26 19:31 unexpand
-rwxr-xr-x 1 root   root        530 2009-04-09 19:51 unicode_stop
-rwxr-xr-x 1 root   root      34284 2008-06-26 19:31 uniq
-rwxr-xr-x 1 root   root      26044 2008-06-26 19:31 unlink
lrwxrwxrwx 1 root   root          4 2009-06-09 08:03 unlzma -> lzma
-rwxr-xr-x 1 root   root         50 2009-04-14 02:26 unopkg
-rwxr-xr-x 1 root   root     130012 2008-11-12 10:11 unzip
-rwxr-xr-x 1 root   root      60000 2008-11-12 10:11 unzipsfx
lrwxrwxrwx 1 root   root         26 2009-06-09 08:03 updatedb -> /etc/alternatives/updatedb
-rwxr-xr-x 1 root   root      34436 2008-11-04 15:37 updatedb.mlocate
-rwxr-xr-x 1 root   root      13856 2009-03-18 21:20 update-desktop-database
-rwxr-xr-x 1 root   root       4232 2009-04-28 05:09 update-manager
-rwxr-xr-x 1 root   root        672 2009-02-24 12:28 update-mime-database
-rwxr-xr-x 1 root   root      42780 2009-02-24 12:28 update-mime-database.real
-rwxr-xr-x 1 root   root      55856 2009-03-27 03:42 update-notifier
-rwxr-xr-x 1 root   root       3331 2009-03-18 19:29 update-pciids
-rwxr-xr-x 1 root   root       5432 2009-03-18 17:17 uptime
-rwxr-xr-x 1 root   root       2695 2009-04-17 14:08 usb-creator
-rwxr-xr-x 1 root   root       5468 2009-03-27 05:21 usb_printerid
-rwxr-xr-x 1 root   root      26076 2008-06-26 19:31 users
-rwxr-xr-x 1 root   root      97512 2009-04-24 06:32 users-admin
-rwxr-xr-x 1 root   root       5468 2009-02-12 09:37 uuidgen
-rwxr-xr-x 1 root   root       2088 2009-02-26 22:21 uxterm
-rwxr-xr-x 1 root   root       1488 2008-05-29 15:55 uz
lrwxrwxrwx 1 root   root         20 2009-06-09 08:03 vi -> /etc/alternatives/vi
lrwxrwxrwx 1 root   root         22 2009-06-09 08:03 view -> /etc/alternatives/view
-rwxr-xr-x 1 root   root      18416 2009-03-19 06:22 viewres
-rwxr-xr-x 1 root   root     638308 2009-03-19 10:31 vim.tiny
-rwxr-xr-x 1 root   root     163388 2009-04-14 04:24 vinagre
-rwxr-xr-x 1 root   root       9624 2009-04-13 17:36 vino-passwd
-rwxr-xr-x 1 root   root      51392 2009-04-13 17:36 vino-preferences
-rwxr-xr-x 1 root   root      21964 2009-03-18 17:17 vmstat
-rwxr-xr-x 1 root   root       5464 2009-03-05 08:50 volname
lrwxrwxrwx 1 root   root         19 2009-06-09 08:03 w -> /etc/alternatives/w
-rwxr-xr-x 1 root   root    1200296 2008-07-21 19:50 w3m
-rwxr-xr-x 1 root   root       1132 2008-07-21 19:49 w3mman
-rwxr-sr-x 1 root   tty       13808 2009-02-18 13:43 wall
-rwxr-xr-x 1 root   root      14156 2009-03-18 17:17 watch
-rwxr-xr-x 1 root   root      34348 2008-06-26 19:31 wc
-rwxr-xr-x 1 root   root        323 2009-04-17 00:08 wftopfa
-rwxr-xr-x 1 root   root     230168 2008-11-11 07:21 wget
-rwxr-xr-x 1 root   root      98032 2009-03-19 05:17 whatis
-rwxr-xr-x 1 root   root       9856 2009-02-18 13:43 whereis
lrwxrwxrwx 1 root   root         10 2009-06-09 08:03 which -> /bin/which
-rwxr-xr-x 1 root   root      22040 2009-04-01 15:35 whiptail
-rwxr-xr-x 1 root   root      38472 2008-06-26 19:31 who
-rwxr-xr-x 1 root   root      26052 2008-06-26 19:31 whoami
-rwxr-xr-x 1 root   root      37712 2008-12-22 07:15 whois
-rwxr-xr-x 1 root   root     371148 2008-11-12 08:12 wodim
-rwxr-xr-x 1 root   root       5456 2008-08-20 04:57 word-list-compress
-rwxr-xr-x 1 root   root      22144 2009-04-08 20:44 wpa_passphrase
-rwxr-xr-x 1 root   root      13784 2009-03-18 17:17 w.procps
lrwxrwxrwx 1 root   root         23 2009-06-09 08:03 write -> /etc/alternatives/write
lrwxrwxrwx 1 root   root         29 2009-06-09 08:03 www-browser -> /etc/alternatives/www-browser
-rwsr-sr-x 1 root   root       9620 2009-04-03 02:43 X
lrwxrwxrwx 1 root   root          1 2009-06-09 08:03 X11 -> .
-rwxr-xr-x 1 root   root     112984 2008-11-05 18:09 x11perf
-rwxr-xr-x 1 root   root       2703 2008-11-05 18:09 x11perfcomp
-rwxr-xr-x 1 root   root      34336 2009-04-07 04:28 xargs
-rwxr-xr-x 1 root   root      34820 2008-06-14 08:41 xauth
-rwxr-xr-x 1 root   root      15172 2008-11-05 18:09 xbiff
-rwxr-xr-x 1 root   root      75616 2009-03-17 22:20 xbrlapi
-rwxr-xr-x 1 root   root      26744 2008-11-05 18:09 xcalc
-rwxr-xr-x 1 root   root      13944 2008-11-05 18:09 xclipboard
-rwxr-xr-x 1 root   root      36344 2008-11-05 18:09 xclock
-rwxr-xr-x 1 root   root      30504 2009-02-27 13:35 xcmsdb
-rwxr-xr-x 1 root   root      14504 2008-11-05 18:09 xconsole
-rwxr-xr-x 1 root   root      13772 2008-11-05 18:09 xcursorgen
-rwxr-xr-x 1 root   root       9808 2008-11-05 18:09 xcutsel
-rwxr-xr-x 1 root   root      14806 2009-02-09 04:00 xdg-desktop-icon
-rwxr-xr-x 1 root   root      39267 2009-02-09 04:00 xdg-desktop-menu
-rwxr-xr-x 1 root   root      15705 2009-02-09 04:00 xdg-email
-rwxr-xr-x 1 root   root      24129 2009-02-09 04:00 xdg-icon-resource
-rwxr-xr-x 1 root   root      28264 2009-02-09 04:00 xdg-mime
-rwxr-xr-x 1 root   root      10229 2009-02-09 04:00 xdg-open
-rwxr-xr-x 1 root   root      19319 2009-02-09 04:00 xdg-screensaver
-rwxr-xr-x 1 root   root        242 2008-10-08 09:45 xdg-user-dir
-rwxr-xr-x 1 root   root      18044 2009-03-09 05:10 xdg-user-dirs-gtk-update
-rwxr-xr-x 1 root   root      17892 2008-10-08 09:45 xdg-user-dirs-update
-rwxr-xr-x 1 root   root      59740 2008-11-05 18:09 xditview
-rwxr-xr-x 1 root   root      26572 2009-03-19 06:22 xdpyinfo
-rwxr-xr-x 1 root   root       5452 2009-03-19 06:22 xdriinfo
-rwxr-xr-x 1 root   root      22080 2009-03-19 06:22 xev
-rwxr-xr-x 1 root   root      14680 2008-11-05 18:09 xeyes
-rwxr-xr-x 1 root   root      23056 2009-03-19 06:22 xfd
-rwxr-xr-x 1 root   root      31284 2009-03-19 06:22 xfontsel
-rwxr-xr-x 1 root   root       5460 2009-03-18 21:19 xfsinfo
-rwxr-xr-x 1 root   root       9572 2009-02-27 13:35 xgamma
-rwxr-xr-x 1 root   root      53300 2008-11-05 18:09 xgc
-rwxr-xr-x 1 root   root      13764 2009-02-27 13:35 xhost
-rwxr-xr-x 1 root   root      13824 2008-05-29 07:53 xinit
-rwxr-xr-x 1 root   root      22224 2009-01-23 08:50 xinput
-rwxr-xr-x 1 root   root       9588 2009-03-30 18:17 xkbbell
-rwxr-xr-x 1 root   root     181764 2009-03-30 18:17 xkbcomp
-rwxr-xr-x 1 root   root      30344 2009-03-30 18:17 xkbevd
-rwxr-xr-x 1 root   root      93840 2009-03-30 18:17 xkbprint
-rwxr-xr-x 1 root   root      18364 2009-03-30 18:17 xkbvleds
-rwxr-xr-x 1 root   root      14332 2009-03-30 18:17 xkbwatch
-rwxr-xr-x 1 root   root      14495 2009-02-27 13:35 xkeystone
-rwxr-xr-x 1 root   root       9688 2009-03-19 06:22 xkill
-rwxr-xr-x 1 root   root      14232 2008-11-05 18:09 xload
-rwxr-xr-x 1 root   root      14352 2008-11-05 18:09 xlogo
-rwxr-xr-x 1 root   root       9576 2009-03-19 06:22 xlsatoms
-rwxr-xr-x 1 root   root       9596 2009-03-19 06:22 xlsclients
-rwxr-xr-x 1 root   root      22024 2009-03-19 06:22 xlsfonts
-rwxr-xr-x 1 root   root      31616 2008-11-05 18:09 xmag
-rwxr-xr-x 1 root   root      53064 2008-11-05 18:09 xman
-rwxr-xr-x 1 root   root      14304 2009-03-19 06:22 xmessage
-rwxr-xr-x 1 root   root      28676 2009-03-17 03:41 xml2po
-rwxr-xr-x 1 root   root      13740 2009-04-08 16:11 xmlcatalog
-rwxr-xr-x 1 root   root      51640 2009-04-08 16:11 xmllint
-rwxr-xr-x 1 root   root      26352 2009-02-27 13:35 xmodmap
-rwxr-xr-x 1 root   root       9692 2008-11-05 18:09 xmore
-rwxr-xr-x 1 root   root    1726396 2009-04-08 21:14 Xorg
-rwxr-xr-x 1 root   root       4965 2004-10-28 17:51 xpath
lrwxrwxrwx 1 root   root         34 2009-06-09 13:34 xpcshell-1.9 -> ../lib/xulrunner-1.9.0.10/xpcshell
-rwxr-xr-x 1 root   root      31448 2009-03-19 06:22 xprop
-rwxr-xr-x 1 root   root      53436 2009-03-27 05:21 xqxdecode
-rwxr-xr-x 1 root   root      46660 2009-02-27 13:35 xrandr
-rwxr-xr-x 1 root   root      22080 2009-02-27 13:35 xrdb
-rwxr-xr-x 1 root   root       9764 2009-02-27 13:35 xrefresh
-rwxr-xr-x 1 root   root     666600 2009-01-27 03:25 xsane
-rwxr-xr-x 1 root   root     117480 2008-10-24 01:49 xscreensaver-getimage
-rwxr-xr-x 1 root   root      16178 2008-10-24 01:48 xscreensaver-getimage-file
-rwxr-xr-x 1 root   root       5044 2008-10-24 01:48 xscreensaver-getimage-video
-rwxr-xr-x 1 root   root      17840 2008-10-24 01:49 xscreensaver-gl-helper
-rwxr-xr-x 1 root   root      25120 2008-10-24 01:48 xscreensaver-text
lrwxrwxrwx 1 root   root         35 2009-06-09 08:03 x-session-manager -> /etc/alternatives/x-session-manager
-rwxr-xr-x 1 root   root      30252 2009-02-27 13:35 xset
-rwxr-xr-x 1 root   root       5472 2009-02-27 13:35 xsetmode
-rwxr-xr-x 1 root   root       9576 2009-02-27 13:35 xsetpointer
-rwxr-xr-x 1 root   root      13748 2009-02-27 13:35 xsetroot
-rwxr-xr-x 1 root   root      17908 2009-02-22 07:27 xsltproc
-rwxr-xr-x 1 root   root      70076 2007-11-07 13:04 xsm
-rwxr-xr-x 1 root   root       9996 2009-02-27 13:35 xstdcmap
-rwxr-xr-x 1 root   root       4093 2009-01-05 14:22 xsubpp
-rwxr-sr-x 1 root   utmp     345364 2009-02-26 22:22 xterm
lrwxrwxrwx 1 root   root         37 2009-06-09 08:03 x-terminal-emulator -> /etc/alternatives/x-terminal-emulator
-rwxr-xr-x 1 root   root      17816 2009-02-27 13:35 xtrapchar
-rwxr-xr-x 1 root   root       9688 2009-02-27 13:35 xtrapin
-rwxr-xr-x 1 root   root       5460 2009-02-27 13:35 xtrapinfo
-rwxr-xr-x 1 root   root       9708 2009-02-27 13:35 xtrapout
-rwxr-xr-x 1 root   root       5516 2009-02-27 13:35 xtrapproto
-rwxr-xr-x 1 root   root       5452 2009-02-27 13:35 xtrapreset
-rwxr-xr-x 1 root   root       5492 2009-02-27 13:35 xtrapstats
lrwxrwxrwx 1 root   root         27 2009-06-09 13:36 xulrunner -> /etc/alternatives/xulrunner
lrwxrwxrwx 1 root   root         35 2009-06-09 13:34 xulrunner-1.9 -> ../lib/xulrunner-1.9.0.10/xulrunner
-rwxr-xr-x 1 root   root      31268 2009-02-27 13:35 xvidtune
-rwxr-xr-x 1 root   root       9584 2009-03-19 06:22 xvinfo
-rwxr-xr-x 1 root   root      22028 2008-11-05 18:09 xwd
lrwxrwxrwx 1 root   root         34 2009-06-09 08:03 x-window-manager -> /etc/alternatives/x-window-manager
-rwxr-xr-x 1 root   root      26104 2009-03-19 06:22 xwininfo
-rwxr-xr-x 1 root   root      26068 2008-11-05 18:09 xwud
lrwxrwxrwx 1 root   root         31 2009-06-09 08:03 x-www-browser -> /etc/alternatives/x-www-browser
-rwxr-xr-x 1 root   root      13820 2009-03-19 10:32 xxd
-rwxr-xr-x 1 root   root     225116 2009-04-08 09:18 yelp
-rwxr-xr-x 1 root   root      26040 2008-06-26 19:31 yes
-rwxr-xr-x 1 root   root       9616 2009-04-09 03:19 zdump
-rwxr-xr-x 1 root   root      62228 2009-04-20 02:13 zenity
-rwxr-xr-x 1 root   root      66532 2006-07-10 09:47 zip
-rwxr-xr-x 1 root   root      27620 2006-07-10 09:47 zipcloak
-rwxr-xr-x 1 root   root       1188 2008-11-12 10:11 zipgrep
-rwxr-xr-x 1 root   root     130012 2008-11-12 10:11 zipinfo
-rwxr-xr-x 1 root   root      23296 2006-07-10 09:47 zipnote
-rwxr-xr-x 1 root   root      27392 2006-07-10 09:47 zipsplit
-rwxr-xr-x 1 root   root      57564 2009-03-27 05:21 zjsdecode
-rwxr-xr-x 1 root   root      88144 2009-03-19 05:17 zsoelim

---

### Post by rolo550 on 2009-06-09
more - reversed

rwxr-xr-x 1 root   root       5484 2009-04-13 19:58 gvfs-monitor-dir
-rwxr-xr-x 1 root   root       5588 2009-04-13 19:58 gvfs-mkdir
-rwxr-xr-x 1 root   root      14020 2009-04-13 19:58 gvfs-ls
-rwxr-xr-x 1 root   root        879 2009-04-13 19:57 gvfs-less
-rwxr-xr-x 1 root   root       9832 2009-04-13 19:58 gvfs-info
-rwxr-xr-x 1 root   root       9856 2009-04-13 19:58 gvfs-copy
-rwxr-xr-x 1 root   root       9716 2009-04-13 19:58 gvfs-cat
-rwxr-xr-x 1 root   root      59848 2009-04-13 07:10 gucharmap
-rwxr-xr-x 1 root   root      80744 2009-04-17 21:29 gtk-window-decorator
lrwxrwxrwx 1 root   root         40 2009-06-09 08:03 gtk-update-icon-cache -> ../lib/libgtk2.0-0/gtk-update-icon-cache
lrwxrwxrwx 1 root   root         42 2009-06-09 08:03 gtk-query-immodules-2.0 -> ../lib/libgtk2.0-0/gtk-query-immodules-2.0
-rwxr-xr-x 1 root   root      13664 2009-04-08 21:14 gtf
lrwxrwxrwx 1 root   root          3 2009-06-09 08:03 gtbl -> tbl
-rwxr-xr-x 1 root   root      22220 2009-01-21 05:20 gst-xmllaunch-0.10
-rwxr-xr-x 1 root   root      22068 2009-01-21 05:20 gst-xmlinspect-0.10
-rwxr-xr-x 1 root   root       1734 2009-04-06 02:53 gst-visualise-0.10
-rwxr-xr-x 1 root   root       9724 2009-01-21 05:20 gst-typefind-0.10
-rwxr-xr-x 1 root   root      23612 2009-03-27 04:12 gstreamer-properties
lrwxrwxrwx 1 root   root         41 2009-06-09 08:03 gstreamer-codec-install -> /etc/alternatives/gstreamer-codec-install
-rwxr-xr-x 1 root   root      22216 2009-01-21 05:20 gst-launch-0.10
-rwxr-xr-x 1 root   root      34632 2009-01-21 05:20 gst-inspect-0.10
-rwxr-xr-x 1 root   root       3173 2009-01-21 05:19 gst-feedback-0.10
-rwxr-xr-x 1 root   root        303 2009-04-17 00:08 gsnd
-rwxr-xr-x 1 root   root        376 2009-04-17 00:08 gslp
-rwxr-xr-x 1 root   root        379 2009-04-17 00:08 gslj
-rwxr-xr-x 1 root   root        381 2009-04-17 00:08 gsdj500
-rwxr-xr-x 1 root   root        378 2009-04-17 00:08 gsdj
-rwxr-xr-x 1 root   root        376 2009-04-17 00:08 gsbj
-rwxr-xr-x 1 root   root       5452 2009-04-17 00:09 gs
-rwxr-xr-x 1 root   root      87804 2009-02-12 03:18 growisofs
-rwxr-xr-x 1 root   root       2248 2008-06-26 19:31 groups
-rwxr-xr-x 1 root   root      75732 2009-03-18 21:05 grotty
-rwxr-xr-x 1 root   root     124980 2009-03-18 21:05 grops
-rwxr-xr-x 1 root   root       2470 2009-03-18 21:05 grog
-rwxr-xr-x 1 root   root      63444 2009-03-18 21:05 groff
-rwxr-xr-x 1 root   root      92672 2009-02-10 10:13 gprof
-rwxr-xr-x 1 root   root       9668 2009-03-31 05:10 gpilot-install-file
-rwxr-xr-x 1 root   root       5436 2009-03-31 05:10 gpilotd-session-wrapper
-rwxr-xr-x 1 root   root      71760 2009-03-31 05:10 gpilotd-control-applet
-rwxr-xr-x 1 root   root      80276 2009-03-31 05:10 gpilotd
-rwxr-xr-x 1 root   root      34768 2009-03-31 05:10 gpilot-applet
lrwxrwxrwx 1 root   root          3 2009-06-09 08:03 gpic -> pic
-rwxr-xr-x 1 root   root       3302 2008-07-30 03:15 gpg-zip
-rwxr-xr-x 1 root   root     243740 2008-07-30 03:16 gpgv
-rwxr-xr-x 1 root   root      34440 2008-07-30 03:15 gpgsplit
-rwxr-xr-x 1 root   root       1512 2008-07-30 03:15 gpg-convert-from-106
-rwxr-xr-x 1 root   root     857572 2008-07-30 03:15 gpg
-rwsr-xr-x 1 root   root      45436 2009-04-04 00:49 gpasswd
-rwxr-xr-x 1 root   root       4087 2009-04-08 16:42 gnome-wm
-rwxr-xr-x 1 root   root      18072 2009-04-13 03:46 gnome-window-properties
-rwxr-xr-x 1 root   root      72420 2009-03-27 04:12 gnome-volume-control
lrwxrwxrwx 1 root   root         41 2009-06-09 08:03 gnome-video-thumbnailer -> /etc/alternatives/gnome-video-thumbnailer
-rwxr-xr-x 1 root   root       9608 2009-03-17 10:34 gnomevfs-rm
-rwxr-xr-x 1 root   root       9608 2009-03-17 10:34 gnomevfs-mv
-rwxr-xr-x 1 root   root      13756 2009-03-17 10:34 gnomevfs-monitor
-rwxr-xr-x 1 root   root       9640 2009-03-17 10:34 gnomevfs-mkdir
-rwxr-xr-x 1 root   root      13960 2009-03-17 10:34 gnomevfs-ls
-rwxr-xr-x 1 root   root      13912 2009-03-17 10:34 gnomevfs-info
-rwxr-xr-x 1 root   root      13776 2009-03-17 10:34 gnomevfs-df
-rwxr-xr-x 1 root   root       9636 2009-03-17 10:34 gnomevfs-copy
-rwxr-xr-x 1 root   root       9632 2009-03-17 10:34 gnomevfs-cat
lrwxrwxrwx 1 root   root         11 2009-06-09 08:03 gnome-umount -> gnome-mount
-rwxr-xr-x 1 root   root      34984 2009-04-13 03:46 gnome-typing-monitor
-rwxr-xr-x 1 root   root      17972 2009-04-13 03:46 gnome-thumbnail-font
lrwxrwxrwx 1 root   root         35 2009-06-09 08:03 gnome-text-editor -> /etc/alternatives/gnome-text-editor
-rwxr-xr-x 1 root   root       1291 2009-03-31 18:09 gnome-terminal.wrapper
-rwxr-xr-x 1 root   root     259648 2009-03-31 18:10 gnome-terminal
-rwxr-xr-x 1 root   root     233324 2009-03-16 16:50 gnome-system-monitor
-rwxr-xr-x 1 root   root      85384 2009-03-16 20:08 gnome-system-log
-rwxr-xr-x 1 root   root      63896 2009-03-27 04:12 gnome-sound-recorder
-rwxr-xr-x 1 root   root      89560 2009-04-13 03:46 gnome-sound-properties
lrwxrwxrwx 1 root   root         50 2009-06-09 13:35 gnome-settings-daemon -> ../lib/gnome-settings-daemon/gnome-settings-daemon
-rwxr-xr-x 1 root   root       9888 2009-04-08 16:42 gnome-session-save
-rwxr-xr-x 1 root   root      55560 2009-04-08 16:42 gnome-session-properties
-rwxr-xr-x 1 root   root     200080 2009-04-08 16:42 gnome-session
-rwxr-xr-x 1 root   root     118952 2009-03-16 20:08 gnome-search-tool
-rwxr-xr-x 1 root   root      55788 2009-03-16 20:08 gnome-screenshot
-rwxr-xr-x 1 root   root      51668 2009-04-11 18:49 gnome-screensaver-preferences
-rwxr-xr-x 1 root   root      14200 2009-04-11 18:49 gnome-screensaver-command
-rwxr-xr-x 1 root   root     142308 2009-04-11 18:49 gnome-screensaver
-rwxr-xr-x 1 root   root      75816 2009-04-08 10:36 gnome-power-statistics
-rwxr-xr-x 1 root   root      71608 2009-04-08 10:36 gnome-power-preferences
-rwxr-xr-x 1 root   root       1385 2009-04-08 10:36 gnome-power-manager-inhibit
-rwxr-xr-x 1 root   root     330532 2009-04-08 10:36 gnome-power-manager
-rwxr-xr-x 1 root   root       1447 2009-04-08 10:36 gnome-power-cmd
-rwxr-xr-x 1 root   root       9592 2009-03-31 05:10 gnome-pilot-make-password
lrwxrwxrwx 1 root   root         16 2009-06-09 08:03 gnome-panel-screenshot -> gnome-screenshot
-rwxr-xr-x 1 root   root     498572 2009-04-17 00:35 gnome-panel
-rwxr-xr-x 1 root   root       5472 2009-03-23 07:02 gnome-open
-rwxr-xr-x 1 root   root      63836 2009-04-13 03:46 gnome-network-properties
-rwxr-xr-x 1 root   root     101032 2009-04-02 16:29 gnome-nettool
-rwxr-xr-x 1 root   root      59708 2009-04-13 03:46 gnome-mouse-properties
-rwxr-xr-x 1 root   root      76712 2009-03-30 08:53 gnome-mount
-rwxr-xr-x 1 root   root        996 2009-04-13 20:11 gnome-language-selector
-rwxr-xr-x 1 root   root     588132 2009-04-13 05:25 gnome-keyring-daemon
-rwxr-xr-x 1 root   root       9812 2009-04-13 05:25 gnome-keyring
-rwxr-xr-x 1 root   root      89036 2009-04-13 03:46 gnome-keyboard-properties
-rwxr-xr-x 1 root   root      55548 2009-04-13 03:46 gnome-keybinding-properties
lrwxrwxrwx 1 root   root          4 2009-06-09 08:03 gnome-help -> yelp
-rwxr-xr-x 1 root   root      22252 2009-04-13 03:46 gnome-font-viewer
lrwxrwxrwx 1 root   root         11 2009-06-09 08:03 gnome-eject -> gnome-mount
-rwxr-xr-x 1 root   root       8580 2009-03-17 03:41 gnome-doc-tool
-rwxr-xr-x 1 root   root       9503 2009-03-17 03:41 gnome-doc-prepare
-rwxr-xr-x 1 root   root      55544 2009-04-13 03:46 gnome-display-properties
-rwxr-xr-x 1 root   root      93000 2009-03-16 20:08 gnome-dictionary
-rwxr-xr-x 1 root   root     105464 2009-04-17 00:35 gnome-desktop-item-edit
-rwxr-xr-x 1 root   root      59664 2009-04-13 03:46 gnome-default-applications-properties
-rwxr-xr-x 1 root   root     113516 2009-04-13 03:46 gnome-control-center
-rwxr-xr-x 1 root   root        168 2009-03-17 13:13 gnome-codec-install
lrwxrwxrwx 1 root   root          9 2009-06-09 08:03 gnome-character-map -> gucharmap
lrwxrwxrwx 1 root   root          9 2009-06-09 08:03 gnome-calculator -> gcalctool
-rwxr-xr-x 1 root   root       5520 2009-03-27 04:12 gnome-audio-profiles-properties
-rwxr-xr-x 1 root   root       2205 2009-04-13 03:45 gnome-at-visual
-rwxr-xr-x 1 root   root      47144 2009-04-13 03:46 gnome-at-properties
-rwxr-xr-x 1 root   root       2205 2009-04-13 03:45 gnome-at-mobility
-rwxr-xr-x 1 root   root        992 2009-04-30 02:26 gnome-app-install
-rwxr-xr-x 1 root   root     205676 2009-04-13 03:46 gnome-appearance-properties
-rwxr-xr-x 1 root   root      72688 2009-04-13 03:46 gnome-about-me
-rwxr-xr-x 1 root   root      37433 2009-05-05 20:41 gnome-about
-rwxr-xr-x 1 root   root        831 2009-03-17 10:28 gmenu-simple-editor
-rwxr-xr-x 1 root   root      22144 2009-05-05 21:16 glxinfo
-rwxr-xr-x 1 root   root       9660 2009-05-05 21:16 glxheads
-rwxr-xr-x 1 root   root      18028 2009-05-05 21:16 glxgears
-rwxr-xr-x 1 root   root       5496 2009-05-05 21:16 glxdemo
-rwxr-xr-x 1 root   root       9660 2009-04-08 09:25 gksu-properties
lrwxrwxrwx 1 root   root          4 2009-06-09 08:03 gksudo -> gksu
-rwxr-xr-x 1 root   root      22600 2009-03-16 08:06 gksu
-rwxr-xr-x 1 root   root      53436 2009-03-27 05:21 gipddecode
-rwxr-xr-x 1 root   root    2131856 2009-03-17 04:53 gimp-console-2.6
lrwxrwxrwx 1 root   root         16 2009-06-09 08:03 gimp-console -> gimp-console-2.6
-rwxr-xr-x 1 root   root    4345608 2009-03-17 04:53 gimp-2.6
lrwxrwxrwx 1 root   root          8 2009-06-09 08:03 gimp -> gimp-2.6
lrwxrwxrwx 1 root   root          2 2009-06-09 08:03 ghostscript -> gs
-rwxr-xr-x 1 root   root      13860 2008-09-27 09:18 ggz-wrapper
-rwxr-xr-x 1 root   root      26364 2008-09-27 09:18 ggz-config
-rwxr-xr-x 1 root   root      38844 2009-03-16 20:08 gfloppy
-rwxr-xr-x 1 root   root      10607 2009-03-27 05:21 getweb
-rwxr-xr-x 1 root   root       4653 2009-03-03 03:20 gettext.sh
-rwxr-xr-x 1 root   root      26900 2009-03-03 03:20 gettext
-rwxr-xr-x 1 root   root       9848 2009-02-18 13:43 getopt
-rwxr-xr-x 1 root   root       9576 2009-04-09 19:51 getkeycodes
-rwxr-xr-x 1 root   root       5448 2008-07-15 08:06 gethostip
-rwxr-xr-x 1 root   root      18272 2008-05-02 19:01 getfacl
-rwxr-xr-x 1 root   root      18252 2009-04-09 03:19 getent
-rwxr-xr-x 1 root   root       5832 2008-11-12 08:12 geteltorito
-rwxr-xr-x 1 root   root      17796 2009-04-09 03:19 getconf
lrwxrwxrwx 1 root   root         11 2009-06-09 08:03 GET -> lwp-request
lrwxrwxrwx 1 root   root          3 2009-06-09 08:03 geqn -> eqn
-rwxr-xr-x 1 root   root     514168 2008-11-12 08:13 genisoimage
-rwxr-xr-x 1 root   root      17892 2009-04-09 03:19 gencat
-rwxr-xr-x 1 root   root     641264 2009-04-14 04:27 gedit
-rwxr-xr-x 1 root   root      88268 2009-04-03 03:26 gdmXnestchooser
lrwxrwxrwx 1 root   root         15 2009-06-09 08:03 gdmXnest -> gdmXnestchooser
-rwxr-xr-x 1 root   root       1939 2009-04-03 03:25 gdmthemetester
-rwxr-xr-x 1 root   root      67764 2009-04-03 03:26 gdmphotosetup
-rwxr-xr-x 1 root   root      76328 2009-04-03 03:26 gdmflexiserver
-rwxr-xr-x 1 root   root      63524 2009-04-03 03:26 gdmdynamic
-rwxr-xr-x 1 root   root       5684 2009-04-03 03:26 gdm-dmx-reconnect-proxy
lrwxrwxrwx 1 root   root         43 2009-06-09 08:03 gdk-pixbuf-query-loaders -> ../lib/libgtk2.0-0/gdk-pixbuf-query-loaders
-rwxr-xr-x 1 root   root       9228 2009-04-20 02:13 gdialog
-rwxr-xr-x 1 root   root       2695 2009-04-01 08:36 gdebi-gtk
-rwxr-xr-x 1 root   root       3933 2009-04-01 08:36 gdebi
-rwxr-xr-x 1 root   root    2997528 2008-09-08 15:50 gdbtui
-rwxr-xr-x 1 root   root      76384 2008-09-08 15:50 gdbserver
-rwxr-xr-x 1 root   root    2997524 2008-09-08 15:50 gdb
-rwxr-xr-x 1 root   root      26088 2009-03-16 19:30 gcov-4.3
lrwxrwxrwx 1 root   root          8 2009-06-09 08:03 gcov -> gcov-4.3
-rwxr-xr-x 1 root   root       1857 2008-01-01 16:53 gcore
-rwxr-xr-x 1 root   root      55148 2009-03-18 16:38 gconftool-2
lrwxrwxrwx 1 root   root         27 2009-06-09 08:03 gconftool -> /etc/alternatives/gconftool
-rwxr-xr-x 1 root   root         68 2009-02-21 01:23 gconfsharp2-schemagen
-rwxr-xr-x 1 root   root      46964 2009-03-18 16:38 gconf-merge-tree
-rwxr-xr-x 1 root   root     114256 2009-03-17 10:13 gconf-editor
-rwxr-xr-x 1 root   root     208068 2009-03-16 19:30 gcc-4.3
lrwxrwxrwx 1 root   root          7 2009-06-09 08:03 gcc -> gcc-4.3
-rwxr-xr-x 1 root   root     133396 2009-03-17 12:55 gcalctool
-rwxr-xr-x 1 root   root       5444 2009-03-27 02:54 gamma4scanimage
-rwxr-xr-x 1 root   root         78 2009-02-11 06:57 gacutil2
-rwxr-xr-x 1 root   root         78 2009-02-11 07:15 gacutil
-rwxr-xr-x 1 root   root      18472 2008-11-12 10:11 funzip
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 ftp -> /etc/alternatives/ftp
-rwxr-xr-x 1 root   root       9912 2009-03-18 21:19 fstobdf
-rwxr-xr-x 1 root   root       1196 2009-04-08 07:50 f-spot-sqlite-upgrade
-rwxr-xr-x 1 root   root        940 2009-04-08 07:50 f-spot-import
-rwxr-xr-x 1 root   root       1861 2009-04-08 07:50 f-spot
-rwxr-xr-x 1 root   root      13720 2009-03-18 21:19 fslsfonts
-rwxr-xr-x 1 root   root       5472 2008-11-04 15:43 from
-rwxr-xr-x 1 root   root      11552 2008-02-01 22:18 fribidi
-rwxr-xr-x 1 root   root       9560 2009-03-18 17:17 free
-rwxr-xr-x 1 root   root       2487 2009-05-14 04:32 foomatic-searchprinter
-rwxr-xr-x 1 root   root      97952 2009-03-30 17:35 foomatic-rip
-rwxr-xr-x 1 root   root      35088 2009-05-14 04:32 foomatic-printjob
-rwxr-xr-x 1 root   root       6423 2009-05-14 04:32 foomatic-ppd-to-xml
-rwxr-xr-x 1 root   root       4000 2009-05-14 04:32 foomatic-ppd-options
-rwxr-xr-x 1 root   root       9189 2009-05-14 04:32 foomatic-ppdfile
-rwxr-xr-x 1 root   root      83376 2009-05-14 04:32 foomatic-perl-data
lrwxrwxrwx 1 root   root         16 2009-06-09 13:33 foomatic-datafile -> foomatic-ppdfile
-rwxr-xr-x 1 root   root     136795 2009-05-14 04:32 foomatic-configure
-rwxr-xr-x 1 root   root       4858 2009-05-14 04:32 foomatic-compiledb
-rwxr-xr-x 1 root   root      42420 2009-05-14 04:32 foomatic-combo-xml
-rwxr-xr-x 1 root   root      18342 2009-03-27 05:21 foo2zjs-wrapper
-rwxr-xr-x 1 root   root       1689 2009-03-27 05:21 foo2zjs-pstops
-rwxr-xr-x 1 root   root     150680 2009-03-27 05:21 foo2zjs-icc2ps
-rwxr-xr-x 1 root   root      66680 2009-03-27 05:21 foo2zjs
-rwxr-xr-x 1 root   root      15994 2009-03-27 05:21 foo2xqx-wrapper
-rwxr-xr-x 1 root   root      66680 2009-03-27 05:21 foo2xqx
-rwxr-xr-x 1 root   root      16751 2009-03-27 05:21 foo2slx-wrapper
-rwxr-xr-x 1 root   root      66648 2009-03-27 05:21 foo2slx
-rwxr-xr-x 1 root   root      17386 2009-03-27 05:21 foo2qpdl-wrapper
-rwxr-xr-x 1 root   root      70780 2009-03-27 05:21 foo2qpdl
-rwxr-xr-x 1 root   root      16779 2009-03-27 05:21 foo2oak-wrapper
-rwxr-xr-x 1 root   root      70840 2009-03-27 05:21 foo2oak
-rwxr-xr-x 1 root   root      18838 2009-03-27 05:21 foo2lava-wrapper
-rwxr-xr-x 1 root   root      67708 2009-03-27 05:21 foo2lava
-rwxr-xr-x 1 root   root      17814 2009-03-27 05:21 foo2hp2600-wrapper
-rwxr-xr-x 1 root   root      71032 2009-03-27 05:21 foo2hp
-rwxr-xr-x 1 root   root      16472 2009-03-27 05:21 foo2hiperc-wrapper
-rwxr-xr-x 1 root   root      70780 2009-03-27 05:21 foo2hiperc
-rwxr-xr-x 1 root   root      30168 2008-06-17 21:55 fonttosfnt
-rwxr-xr-x 1 root   root       3244 2009-04-13 20:11 fontconfig-voodoo
-rwxr-xr-x 1 root   root        339 2009-04-17 00:08 font2c
-rwxr-xr-x 1 root   root      30168 2008-06-26 19:31 fold
-rwxr-xr-x 1 root   root      34260 2008-06-26 19:31 fmt
-rwxr-xr-x 1 root   root       9584 2009-02-18 13:43 flock
lrwxrwxrwx 1 root   root         32 2009-06-09 13:34 firefox-3.0 -> ../lib/firefox-3.0.10/firefox.sh
lrwxrwxrwx 1 root   root         11 2009-06-09 13:34 firefox -> firefox-3.0
-rwxr-xr-x 1 root   root      18420 2008-05-02 19:30 finger
-rwxr-xr-x 1 root   root       4603 2009-03-27 11:18 findsmb
-rwxr-xr-x 1 root   root      24107 2009-01-05 14:22 find2perl
-rwxr-xr-x 1 root   root     141952 2009-04-07 04:28 find
-rwxr-xr-x 1 root   root     355508 2009-04-14 04:56 file-roller
-rwxr-xr-x 1 root   root      13744 2009-03-16 12:32 file
-rwxr-xr-x 1 root   root      22320 2009-02-23 18:32 festival-synthesis-driver
-rwxr-xr-x 1 root   root       9536 2009-03-19 09:04 fc-match
-rwxr-xr-x 1 root   root       9528 2009-03-19 09:04 fc-list
-rwxr-xr-x 1 root   root       9584 2009-03-19 09:04 fc-cat
-rwxr-xr-x 1 root   root      13720 2009-03-19 09:04 fc-cache
-rwxr-xr-x 1 root   root       3550 2009-01-05 15:55 fakeroot-tcp
-rwxr-xr-x 1 root   root       3554 2009-01-05 15:55 fakeroot-sysv
lrwxrwxrwx 1 root   root         26 2009-06-09 13:49 fakeroot -> /etc/alternatives/fakeroot
-rwxr-xr-x 1 root   root      21980 2009-01-05 15:56 faked-tcp
-rwxr-xr-x 1 root   root      17868 2009-01-05 15:56 faked-sysv
-rwxr-xr-x 1 root   root       9784 2009-04-04 00:49 faillog
-rwxr-xr-x 1 root   root      30208 2008-06-26 19:31 factor
-rwxr-xr-x 1 root   root      26072 2008-07-15 08:06 extlinux
-rwxr-xr-x 1 root   root      34332 2008-06-26 19:31 expr
-rwxr-sr-x 1 root   shadow    18472 2009-04-04 00:49 expiry
-rwxr-xr-x 1 root   root      30220 2008-06-26 19:31 expand
-rwxr-xr-x 1 root   root      26440 2009-04-28 04:49 exchange-connector-setup-2.26
lrwxrwxrwx 1 root   root         20 2009-06-09 08:03 ex -> /etc/alternatives/ex
lrwxrwxrwx 1 root   root         50 2009-06-09 13:34 evolution-addressbook-export -> ../lib/evolution/2.26/evolution-addressbook-export
-rwxr-xr-x 1 root   root     122528 2009-05-15 10:12 evolution
-rwxr-xr-x 1 root   root       9664 2009-04-23 06:30 evince-thumbnailer
-rwxr-xr-x 1 root   root     345944 2009-04-23 06:30 evince
-rwxr-xr-x 1 root   root      13996 2009-02-23 18:32 espeak-synthesis-driver
-rwxr-xr-x 1 root   root      14020 2009-02-23 09:17 espeak
-rwxr-xr-x 1 root   root       9604 2009-02-16 23:26 esdsample
-rwxr-xr-x 1 root   root       5456 2009-02-16 23:26 esdrec
-rwxr-xr-x 1 root   root       5448 2009-02-16 23:26 esdplay
-rwxr-xr-x 1 root   root       5456 2009-02-16 23:26 esdmon
-rwxr-xr-x 1 root   root       9584 2009-02-16 23:26 esdloop
-rwxr-xr-x 1 root   root       5464 2009-02-16 23:26 esdfilt
-rwxr-xr-x 1 root   root       2069 2009-02-16 23:26 esddsp
-rwxr-xr-x 1 root   root      13728 2009-02-16 23:26 esdctl
-rwxr-xr-x 1 root   root       2795 2009-04-08 19:09 esdcompat
-rwxr-xr-x 1 root   root       5456 2009-02-16 23:26 esdcat
lrwxrwxrwx 1 root   root          9 2009-06-09 08:03 esd -> esdcompat
-rwxr-xr-x 1 root   root       9548 2009-03-27 05:26 esc-m
-rwxr-xr-x 1 root   root     138256 2009-03-18 21:05 eqn
-rwxr-xr-x 1 root   root        671 2009-04-17 00:08 eps2eps
-rwxr-xr-x 1 root   root     481844 2009-04-14 04:15 eog
-rwxr-xr-x 1 root   root      26912 2009-03-03 03:20 envsubst
-rwxr-xr-x 1 root   root      26052 2008-06-26 19:31 env
-rwxr-xr-x 1 root   root       5476 2008-11-28 02:32 enchant-lsmod
-rwxr-xr-x 1 root   root      13744 2008-11-28 02:32 enchant
-rwxr-xr-x 1 root   root      39219 2009-01-05 14:22 enc2xs
-rwxr-xr-x 1 root   root       9628 2009-05-05 20:32 ekiga-helper
-rwxr-xr-x 1 root   root       3399 2009-05-05 20:32 ekiga-config-tool
-rwxr-xr-x 1 root   root    2232888 2009-05-05 20:32 ekiga
-rwxr-xr-x 1 root   root      22356 2009-03-05 08:50 eject
-rwxr-xr-x 1 root   root      52396 2009-03-19 06:22 editres
lrwxrwxrwx 1 root   root         24 2009-06-09 08:03 editor -> /etc/alternatives/editor
lrwxrwxrwx 1 root   root         11 2009-06-09 08:03 edit -> run-mailcap
-rwxr-xr-x 1 root   root      22236 2009-03-17 18:25 dwell-click-applet
-rwxr-xr-x 1 root   root       1054 2009-04-17 00:08 dvipdf
-rwxr-xr-x 1 root   root      54676 2009-02-12 03:18 dvd+rw-mediainfo
-rwxr-xr-x 1 root   root      42456 2009-02-12 03:18 dvd+rw-format
-rwxr-xr-x 1 root   root      38288 2009-02-12 03:18 dvd+rw-booktype
-rwxr-xr-x 1 root   root      21884 2009-02-12 03:18 dvd-ram-control
lrwxrwxrwx 1 root   root         13 2009-06-09 08:03 dumpkeys -> /bin/dumpkeys
-rwxr-xr-x 1 root   root        593 2009-04-17 00:08 dumphint
-rwxr-xr-x 1 root   root      75436 2008-06-26 19:31 du
-rwxr-xr-x 1 root   root      24077 2009-01-05 14:22 dprofpp
-rwxr-xr-x 1 root   root      83648 2009-01-07 06:32 dpkg-trigger
-rwxr-xr-x 1 root   root      42580 2009-01-07 06:32 dpkg-split
-rwxr-xr-x 1 root   root     100212 2009-01-07 06:32 dpkg-query
-rwxr-xr-x 1 root   root     230352 2009-01-07 06:32 dpkg-deb
-rwxr-xr-x 1 root   root     375340 2009-01-07 06:32 dpkg
-rwxr-sr-x 1 root   mail      14280 2008-11-18 04:46 dotlockfile
-rwxr-xr-x 1 root   root       2402 2009-04-28 05:09 do-release-upgrade
-rwxr-xr-x 1 root   root      17143 2006-11-25 17:13 dirsplit
-rwxr-xr-x 1 root   root      26052 2008-06-26 19:31 dirname
lrwxrwxrwx 1 root   root         12 2009-06-09 08:03 directomatic -> foomatic-rip
-rwxr-xr-x 1 root   root      34272 2008-06-26 19:31 dircolors
-rwxr-xr-x 1 root   root     120168 2009-03-23 04:43 dig
-rwxr-xr-x 1 root   root      19980 2007-05-04 11:41 diff3
-rwxr-xr-x 1 root   root      62716 2007-05-04 11:41 diff
-rwxr-xr-x 1 root   root      12898 2008-07-24 07:54 dh_pysupport
-rwxr-xr-x 1 root   root      26251 2009-04-16 22:57 dh_pycentral
-rwxr-xr-x 1 root   root       9379 2008-11-06 10:13 dh_installxmlcatalogs
-rwxr-xr-x 1 root   root       1761 2006-06-17 10:54 dh_installdefoma
-rwxr-xr-x 1 root   root       1129 2009-01-21 12:14 dh_bash-completion
-rwxr-xr-x 1 root   root      19128 2009-04-24 05:27 dfutool
-rwxr-xr-x 1 root   root       8741 2009-04-03 02:34 dexconf
-rwxr-xr-x 1 root   root     139624 2008-11-12 08:13 devdump
-rwxr-xr-x 1 root   root      35804 2009-03-18 21:20 desktop-file-validate
-rwxr-xr-x 1 root   root      43932 2009-03-18 21:20 desktop-file-install
-rwxr-xr-x 1 root   root       5444 2009-02-18 13:43 delpart
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 defoma-user -> defoma
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 defoma-subst -> defoma
-rwxr-xr-x 1 root   root      17711 2006-06-22 12:43 defoma-psfont-installer
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 defoma-id -> defoma
-rwxr-xr-x 1 root   root       2038 2006-06-17 10:54 defoma-hints
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 defoma-font -> defoma
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 defoma-app -> defoma
-rwxr-xr-x 1 root   root       3622 2006-06-17 10:54 defoma
-rwxr-xr-x 1 root   root       1827 2009-03-24 00:30 debconf-show
-rwxr-xr-x 1 root   root       2985 2009-03-24 00:30 debconf-set-selections
-rwxr-xr-x 1 root   root        647 2009-03-24 00:30 debconf-escape
-rwxr-xr-x 1 root   root       1719 2009-03-24 00:30 debconf-copydb
-rwxr-xr-x 1 root   root        608 2009-03-24 00:30 debconf-communicate
-rwxr-xr-x 1 root   root      11370 2009-03-24 00:30 debconf-apt-progress
-rwxr-xr-x 1 root   root       2758 2009-03-24 00:30 debconf
-rwxr-xr-x 1 root   root       5480 2009-04-09 19:51 deallocvt
-rwxr-xr-x 1 root   root       9880 2009-02-18 13:43 ddate
-rwxr-xr-x 1 root   root     272088 2008-11-04 20:07 dcraw
-rwxr-xr-x 1 root   root      46472 2008-11-04 20:07 dcparse
-rwxr-xr-x 1 root   root       5460 2008-11-04 20:07 dcfujiturn16
-rwxr-xr-x 1 root   root       5448 2008-11-04 20:07 dcfujiturn
-rwxr-xr-x 1 root   root      13756 2008-11-04 20:07 dcfujigreen
-rwxr-xr-x 1 root   root       5468 2008-11-04 20:07 dccleancrw
-rwxr-xr-x 1 root   root      32712 2007-12-05 06:33 dc
-rwxr-xr-x 1 root   root      17912 2009-01-27 08:39 dbus-send
-rwxr-xr-x 1 root   root      13756 2009-01-27 08:39 dbus-monitor
-rwxr-xr-x 1 root   root      22080 2009-01-27 08:39 dbus-launch
-rwxr-xr-x 1 root   root      13676 2009-04-08 21:14 cvt
-rwxr-xr-x 1 root   root      38364 2008-06-26 19:31 cut
-rwxr-xr-x 1 root   root      46664 2009-06-01 10:23 cupstestppd
-rwxr-xr-x 1 root   root       9580 2009-06-01 10:23 cupstestdsc
-rwxr-xr-x 1 root   root      21896 2009-01-19 11:17 cupsprofile
-rwxr-xr-x 1 root   root      34188 2009-04-02 13:26 cups-calibrate
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 ctstat -> lnstat
lrwxrwxrwx 1 root   root         31 2009-06-09 13:34 csv2vcard -> ../lib/evolution/2.26/csv2vcard
-rwxr-xr-x 1 root   root      17888 2008-05-08 09:23 csslint-0.6
-rwxr-xr-x 1 root   root      42596 2008-06-26 19:31 csplit
-rwxr-sr-x 1 root   crontab   31632 2009-05-12 16:49 crontab
-rwxr-xr-x 1 root   root       3899 2009-03-27 09:55 c_rehash
-rwxr-xr-x 1 root   root      25848 2009-04-23 06:57 cpufreq-selector
-rwxr-xr-x 1 root   root     212164 2009-03-16 19:25 cpp-4.3
lrwxrwxrwx 1 root   root          7 2009-06-09 08:03 cpp -> cpp-4.3
-rwxr-xr-x 1 root   root        536 2009-01-05 14:22 cpanp-run-perl
-rwxr-xr-x 1 root   root       3339 2009-01-05 14:22 cpanp
-rwxr-xr-x 1 root   root      22410 2009-01-05 14:22 cpan2dist
-rwxr-xr-x 1 root   root      11837 2009-01-05 14:22 cpan
-rwxr-xr-x 1 root   root       6300 2009-01-05 14:22 corelist
-rwxr-xr-x 1 root   root       7243 2009-01-05 14:22 config_data
-rwxr-xr-x 1 root   root       1067 2009-03-04 13:48 computer-janitor-gtk
-rwxr-xr-x 1 root   root       1057 2009-04-17 00:45 computer-janitor
lrwxrwxrwx 1 root   root         11 2009-06-09 08:03 compose -> run-mailcap
-rwxr-xr-x 1 root   root     216048 2009-04-17 21:29 compiz.real
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 compiz-manager -> compiz
-rwxr-xr-x 1 root   root       3139 2009-04-17 21:29 compiz-decorator
-rwxr-xr-x 1 root   root      12201 2009-04-17 21:29 compiz
-rwxr-xr-x 1 root   root      30172 2008-06-26 19:31 comm
-rwxr-xr-x 1 root   root       9612 2008-11-04 15:43 column
-rwxr-xr-x 1 root   root       5456 2008-11-04 15:43 colrm
-rwxr-xr-x 1 root   root       5460 2008-11-04 15:43 colcrt
-rwxr-xr-x 1 root   root       9564 2008-11-04 15:43 col
-rwxr-xr-x 1 root   root       9580 2009-04-09 19:51 codepage
-rwxr-xr-x 1 root   root      18264 2007-05-04 11:41 cmp
-rwxr-xr-x 1 root   root       5468 2009-02-11 06:58 cli-wrapper
lrwxrwxrwx 1 root   root         44 2009-06-09 08:03 cli-gacutil -> /etc/alternatives/global-assembly-cache-tool
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 cli -> /etc/alternatives/cli
-rwxr-xr-x 1 root   root       9584 2009-03-02 08:22 clear_console
-rwxr-xr-x 1 root   root       5432 2009-02-12 02:50 clear
-rwxr-xr-x 1 root   root      30196 2008-06-26 19:31 cksum
-rwxr-xr-x 1 root   root       9692 2009-04-24 05:31 ck-list-sessions
-rwxr-xr-x 1 root   root       5480 2009-04-24 05:31 ck-launch-session
-rwxr-xr-x 1 root   root      22328 2009-04-24 05:31 ck-history
-rwxr-xr-x 1 root   root     111189 2009-04-08 20:08 ckbcomp
-rwxr-xr-x 1 root   root      14184 2009-04-24 05:27 ciptool
-rwsr-xr-x 1 root   root      27548 2009-04-04 00:49 chsh
-rwxr-xr-x 1 root   root       9576 2009-02-18 13:43 chrt
-rwxr-xr-x 1 root   root       3676 2009-02-18 13:43 chkdupexe
-rwsr-xr-x 1 root   root      32028 2009-04-04 00:49 chfn
-rwxr-xr-x 1 root   root        201 2009-04-28 04:51 checkbox-gtk
-rwxr-xr-x 1 root   root        273 2009-04-28 04:51 checkbox-backend
-rwxr-xr-x 1 root   root      54916 2008-06-26 19:31 chcon
-rwxr-xr-x 1 root   root       9612 2009-02-12 09:37 chattr
lrwxrwxrwx 1 root   root          9 2009-06-09 08:03 charmap -> gucharmap
-rwxr-sr-x 1 root   shadow    49276 2009-04-04 00:49 chage
-rwxr-xr-x 1 root   root       9624 2008-05-02 19:01 chacl
-rwxr-xr-x 1 root   root      22112 2009-02-10 10:13 c++filt
lrwxrwxrwx 1 root   root          5 2009-06-09 08:03 cdrecord -> wodim
-rwxr-xr-x 1 root   root      59640 2009-02-09 03:35 cdparanoia
lrwxrwxrwx 1 root   root         20 2009-06-09 08:03 cc -> /etc/alternatives/cc
-rwxr-xr-x 1 root   root      88144 2009-03-19 05:17 catman
-rwxr-xr-x 1 root   root       3380 2009-04-09 03:04 catchsegv
lrwxrwxrwx 1 root   root          3 2009-06-09 08:03 captoinfo -> tic
-rwxr-xr-x 1 root   root       9628 2009-06-01 10:23 cancel
-rwxr-xr-x 1 root   root       9620 2009-04-02 17:05 canberra-gtk-play
-rwxr-xr-x 1 root   root      22832 2008-11-25 08:25 calibrate_ppa
-rwxr-xr-x 1 root   root      26516 2008-11-04 15:43 calendar
lrwxrwxrwx 1 root   root          4 2009-06-09 08:03 cal -> ncal
-rwxr-xr-x 1 root   root        451 2006-05-07 04:27 c99-gcc
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 c99 -> /etc/alternatives/c99
-rwxr-xr-x 1 root   root        428 2006-05-07 04:28 c89-gcc
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 c89 -> /etc/alternatives/c89
-rwxr-xr-x 1 root   root      36601 2009-01-05 14:22 c2ph
-rwxr-xr-x 1 root   root      21928 2009-02-12 03:18 btcflash
-rwxr-sr-x 1 root   tty        9656 2008-11-04 15:43 bsd-write
-rwxr-xr-x 1 root   root     868660 2009-04-28 05:27 brasero
-rwxr-xr-x 1 root   root      73620 2008-06-18 22:52 bogoutil
-rwxr-xr-x 1 root   root       5825 2008-06-18 22:52 bogoupgrade
-rwxr-xr-x 1 root   root     167860 2008-06-18 22:52 bogotune
-rwxr-xr-x 1 root   root      89372 2008-06-18 22:52 bogolexer
-rwxr-xr-x 1 root   root     168592 2008-06-18 22:52 bogofilter
-rwxr-xr-x 1 root   root       9588 2008-11-05 18:09 bmtoa
-rwxr-xr-x 1 root   root      51304 2009-04-08 10:19 bluetooth-wizard
-rwxr-xr-x 1 root   root      51452 2009-04-08 10:19 bluetooth-sendto
-rwxr-xr-x 1 root   root      55644 2009-04-08 10:19 bluetooth-properties
-rwxr-xr-x 1 root   root      30588 2009-04-08 10:19 bluetooth-browse
-rwxr-xr-x 1 root   root      55480 2009-04-08 10:19 bluetooth-applet
-rwxr-xr-x 1 root   root      80008 2009-04-08 10:19 bluetooth-analyzer
-rwxr-xr-x 1 root   root      76516 2008-11-05 18:09 bitmap
-rwxr-xr-x 1 root   root       1663 2008-06-18 22:52 bf_tar
-rwxr-xr-x 1 root   root       1235 2008-06-18 22:52 bf_copy
-rwxr-xr-x 1 root   root       2156 2008-06-18 22:52 bf_compact
-rwxr-xr-x 1 root   root       2593 2008-06-17 21:55 bdftruncate
-rwxr-xr-x 1 root   root        331 2009-04-17 00:08 bdftops
-rwxr-xr-x 1 root   root       5468 2008-06-17 21:55 bdftopcf
-rwxr-xr-x 1 root   root      67700 2007-12-05 06:33 bc
-rwxr-xr-x 1 root   root        152 2009-04-17 02:53 batch
-rwxr-xr-x 1 root   root       6876 2009-03-02 08:22 bashbug
-rwxr-xr-x 1 root   root      26052 2008-06-26 19:31 basename
-rwxr-xr-x 1 root   root      34316 2008-06-26 19:31 base64
-rwxr-xr-x 1 root   root     117872 2009-03-16 20:08 baobab
lrwxrwxrwx 1 root   root         21 2009-06-09 08:03 awk -> /etc/alternatives/awk
-rwxr-xr-x 1 root   root       9692 2009-03-23 05:20 avahi-set-host-name
lrwxrwxrwx 1 root   root         13 2009-06-09 08:03 avahi-resolve-host-name -> avahi-resolve
lrwxrwxrwx 1 root   root         13 2009-06-09 08:03 avahi-resolve-address -> avahi-resolve
-rwxr-xr-x 1 root   root      13816 2009-03-23 05:20 avahi-resolve
lrwxrwxrwx 1 root   root         13 2009-06-09 08:03 avahi-publish-service -> avahi-publish
lrwxrwxrwx 1 root   root         13 2009-06-09 08:03 avahi-publish-address -> avahi-publish
-rwxr-xr-x 1 root   root      17952 2009-03-23 05:20 avahi-publish
lrwxrwxrwx 1 root   root         12 2009-06-09 08:03 avahi-browse-domains -> avahi-browse
-rwxr-xr-x 1 root   root      22116 2009-03-23 05:20 avahi-browse
lrwxrwxrwx 1 root   root          2 2009-06-09 08:03 atrm -> at
lrwxrwxrwx 1 root   root          2 2009-06-09 08:03 atq -> at
-rwxr-xr-x 1 root   root       9592 2008-11-05 18:09 atobm
-rwsr-sr-x 1 daemon daemon    43196 2009-04-17 02:53 at
-rwxr-xr-x 1 root   root       2044 2008-08-20 04:56 aspell-import
-rwxr-xr-x 1 root   root     141396 2008-08-20 04:57 aspell
-rwxr-xr-x 1 root   root      11316 2009-04-07 19:07 asoundconf
-rwxr-xr-x 1 root   root      13984 2009-04-07 19:07 aseqnet
-rwxr-xr-x 1 root   root      13908 2009-04-07 19:07 aseqdump
-rwxr-xr-x 1 root   root     293652 2009-02-10 10:13 as
-rwsr-xr-x 1 root   root      11048 2007-12-10 11:33 arping
-rwxr-xr-x 1 root   root       9564 2009-03-27 05:21 arm2hpdl
-rwxr-xr-x 1 root   root      18260 2009-04-07 19:07 arecordmidi
lrwxrwxrwx 1 root   root          5 2009-06-09 08:03 arecord -> aplay
-rwxr-xr-x 1 root   root      50896 2009-02-10 10:13 ar
-rwxr-xr-x 1 root   root       1531 2009-05-05 20:50 apturl
-rwxr-xr-x 1 root   root      26208 2009-04-16 23:27 apt-sortpkgs
-rwxr-xr-x 1 root   root       2195 2009-04-16 23:27 apt-mark
-rwxr-xr-x 1 root   root       5212 2009-04-16 23:27 apt-key
-rwxr-xr-x 1 root   root       3007 2009-02-10 07:45 aptitude-run-state-bundle
-rwxr-xr-x 1 root   root       1939 2009-02-10 07:45 aptitude-create-state-bundle
-rwxr-xr-x 1 root   root    2131092 2009-02-10 07:45 aptitude
-rwxr-xr-x 1 root   root     112812 2009-04-16 23:27 apt-get
-rwxr-xr-x 1 root   root     170188 2009-04-16 23:27 apt-ftparchive
-rwxr-xr-x 1 root   root      22192 2009-04-16 23:27 apt-extracttemplates
-rwxr-xr-x 1 root   root       9768 2009-04-16 23:27 apt-config
-rwxr-xr-x 1 root   root      17988 2009-04-16 23:27 apt-cdrom
-rwxr-xr-x 1 root   root      59200 2009-04-16 23:27 apt-cache
lrwxrwxrwx 1 root   root          6 2009-06-09 08:03 apropos -> whatis
-rwxr-xr-x 1 root   root       9572 2009-03-19 06:22 appres
-rwxr-xr-x 1 root   root       1297 2009-04-29 09:24 apport-unpack
-rwxr-xr-x 1 root   root       5651 2009-04-29 09:24 apport-collect
-rwxr-xr-x 1 root   root      10255 2009-04-29 09:24 apport-cli
-rwxr-xr-x 1 root   root       9824 2009-02-26 19:23 apmsleep
-rwxr-xr-x 1 root   root       9612 2009-02-26 19:23 apm
-rwxr-xr-x 1 root   root      18148 2009-04-07 19:07 aplaymidi
-rwxr-xr-x 1 root   root      51736 2009-04-07 19:07 aplay
-rwxr-xr-x 1 root   root       1961 2008-05-29 15:55 amuFormat.sh
-rwxr-xr-x 1 root   root      47400 2009-04-07 19:07 amixer
-rwxr-xr-x 1 root   root      18220 2009-04-07 19:07 amidi
-rwxr-xr-x 1 root   root      42868 2009-04-07 19:07 alsamixer
-rwxr-xr-x 1 root   root       1211 2009-03-17 10:02 alacarte
-rwxr-xr-x 1 root   root      22352 2009-02-10 10:13 addr2line
-rwxr-xr-x 1 root   root       5444 2009-02-18 13:43 addpart
-rwxr-xr-x 1 root   root       9808 2009-04-28 05:18 acpi_listen
-rwxr-xr-x 1 root   root       5684 2009-03-27 03:20 acpi_fakekey
-rwxr-xr-x 1 root   root      14028 2009-04-07 19:07 aconnect
lrwxrwxrwx 1 root   root         11 2009-06-09 13:34 abrowser-3.0 -> firefox-3.0
lrwxrwxrwx 1 root   root         11 2009-06-09 13:34 abrowser -> firefox-3.0
-rwxr-xr-x 1 root   root     105012 2009-01-05 14:23 a2p
-rwxr-xr-x 1 root   root        106 2009-04-18 21:44 2to3-2.6
lrwxrwxrwx 1 root   root          8 2009-06-09 08:03 2to3 -> 2to3-2.6
-rwxr-xr-x 1 root   root      38416 2008-06-26 19:31 [
ro@PC6:~$

---

### Post by synapsys on 2009-06-09
Sorry forgot that would be so long, should have had you grep out firefox.... 
How exactly are you installing/uninstalling firefox please?

---

### Post by rolo550 on 2009-06-09
Synaptic

---

### Post by synapsys on 2009-06-09
I forget what firefox package is called....
Might be firefox or firefox-3.0.10 or something like that.....
First type in terminal:

```
sudo aptitude search firefox
```

Find the latest version then substitute that for 'firefox' in code below

Try this from command line:

```
sudo apt-get remove firefox
sudo apt-get update
sudo apt-get install flashplugin-nonfree
sudo apt-get install firefox 
```

---

### Post by rolo550 on 2009-06-09
ro@PC6:/usr/bin$ firefox-3.5
*NOTICE* No previous firefox profile found, starting with a fresh one
Segmentation fault




plus, the old firefox and firefox 3.0 are still there in the bin folder even though i ran the apt-get remove

again it will still run with sudo

---

### Post by synapsys on 2009-06-09
[http://ubuntuforums.org/archive/index.php/t-1111684.html](http://ubuntuforums.org/archive/index.php/t-1111684.html)

---

### Post by lovinglinux on 2009-06-09
Next time don't remove Firefox. Most Firefox problems are related to corrupted profiles. Just create a new profile and things should work. Sometimes just deleting a single profile file solves the problem, depending on the type of issue. For example, bookmark related problems can be fixed by deleting *places.sqlite*.

Don't forget to backup your profile regularly using [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109).

---

### Post by RCRedneck on 2009-06-11
Gracias Amigo.... It solved my problem!

> **H2SO_four said:**
> try opera :) You may like it.

---

