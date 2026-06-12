---
title: "Rootkit check"
date: 2008-12-29
forum: General Help
---

### Post by transform100 on 2008-12-29
Hello, I have been running Ubuntu for about 2 years now and it's great, I never thought of running chkrootkit or rkhunter. If someone could check my logs I would be very grateful.

**chkrootkit**

```
ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `crontab'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not infected
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not infected
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not infected
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/firefox-3.0.5/.autoreg /usr/lib/xulrunner-1.9.0.5/.autoreg /lib/modules/2.6.27-9-generic/volatile/.mounted /lib/init/rw/.ramfs

Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for rootedoor... nothing found
Searching for ENYELKM rootkit default files... nothing found
Searching for common ssh-scanners default files... nothing found
Searching for suspect PHP files... nothing found
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[5249], /sbin/dhclient3[5872])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted

```

**rkhunter**

```
[01:43:02] Running Rootkit Hunter version 1.3.2 on lendon-laptop
[01:43:02]
[01:43:02] Info: Start date is Mon Dec 29 01:43:02 CST 2008
[01:43:02]
[01:43:02] Checking configuration file and command-line options...
[01:43:02] Info: Detected operating system is 'Linux'
[01:43:02] Info: Found O/S name: Ubuntu 8.10
[01:43:02] Info: Command line is /usr/bin/rkhunter -c --skip-keypress
[01:43:02] Info: Environment shell is /bin/bash; rkhunter is using dash
[01:43:02] Info: Using configuration file '/etc/rkhunter.conf'
[01:43:02] Info: Installation directory is '/usr'
[01:43:02] Info: Using language 'en'
[01:43:02] Info: Using '/var/lib/rkhunter/db' as the database directory
[01:43:02] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[01:43:02] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[01:43:02] Info: Using '/' as the root directory
[01:43:02] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[01:43:02] Info: No mail-on-warning address configured
[01:43:02] Info: X will be automatically detected
[01:43:02] Info: Using second color set
[01:43:02] Info: Found the 'diff' command: /usr/bin/diff
[01:43:02] Info: Found the 'file' command: /usr/bin/file
[01:43:03] Info: Found the 'find' command: /usr/bin/find
[01:43:03] Info: Found the 'ifconfig' command: /sbin/ifconfig
[01:43:03] Info: Found the 'ip' command: /sbin/ip
[01:43:03] Info: Found the 'ldd' command: /usr/bin/ldd
[01:43:03] Info: Found the 'lsattr' command: /usr/bin/lsattr
[01:43:03] Info: Found the 'lsmod' command: /sbin/lsmod
[01:43:03] Info: Found the 'lsof' command: /usr/bin/lsof
[01:43:03] Info: Found the 'mktemp' command: /bin/mktemp
[01:43:03] Info: Found the 'netstat' command: /bin/netstat
[01:43:03] Info: Found the 'perl' command: /usr/bin/perl
[01:43:03] Info: Found the 'ps' command: /bin/ps
[01:43:03] Info: Found the 'pwd' command: /bin/pwd
[01:43:03] Info: Found the 'readlink' command: /bin/readlink
[01:43:03] Info: Found the 'sort' command: /usr/bin/sort
[01:43:03] Info: Found the 'stat' command: /usr/bin/stat
[01:43:03] Info: Found the 'strings' command: /usr/bin/strings
[01:43:03] Info: Found the 'uniq' command: /usr/bin/uniq
[01:43:03] Info: System is not using prelinking
[01:43:03] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[01:43:03] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[01:43:03] Info: Stored hash values did not use a package manager
[01:43:03] Info: The hash function field index is set to 1
[01:43:03] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[01:43:03] Info: Previous file attributes were stored
[01:43:03] Info: Enabled tests are: all
[01:43:03] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[01:43:03] Info: Found ksym file '/proc/kallsyms'
[01:43:03]
[01:43:03] Checking if the O/S has changed since last time...
[01:43:03] Info: Nothing seems to have changed
[01:43:03]
[01:43:03] Starting system checks...
[01:43:03]
[01:43:03] Checking system commands...
[01:43:03] Info: Starting test name 'system_commands'
[01:43:03]
[01:43:03] Performing 'strings' command checks
[01:43:04] Info: Starting test name 'strings'
[01:43:04] Scanning for string /usr/sbin/ntpsx               [ OK ]
[01:43:04] Scanning for string /usr/lib/.../ls               [ OK ]
[01:43:04] Scanning for string /usr/lib/.../netstat          [ OK ]
[01:43:04] Scanning for string /usr/lib/.../lsof             [ OK ]
[01:43:04] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[01:43:04] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[01:43:04] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[01:43:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[01:43:05] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[01:43:05] Scanning for string /usr/lib/.../psr              [ OK ]
[01:43:05] Scanning for string /usr/lib/.../find             [ OK ]
[01:43:05] Scanning for string /usr/lib/.../pstree           [ OK ]
[01:43:05] Scanning for string /usr/lib/.../slocate          [ OK ]
[01:43:05] Scanning for string /usr/lib/.../du               [ OK ]
[01:43:05] Scanning for string /usr/lib/.../top              [ OK ]
[01:43:05] Scanning for string /usr/lib/...                  [ OK ]
[01:43:05] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[01:43:05] Scanning for string /usr/lib/.bkit-               [ OK ]
[01:43:05] Scanning for string /tmp/.bkp                     [ OK ]
[01:43:05] Scanning for string /tmp/.cinik                   [ OK ]
[01:43:05] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[01:43:05] Scanning for string /lib/.sso                     [ OK ]
[01:43:05] Scanning for string /lib/.so                      [ OK ]
[01:43:05] Scanning for string /var/run/...dica/clean        [ OK ]
[01:43:05] Scanning for string /var/run/...dica/xl           [ OK ]
[01:43:06] Scanning for string /var/run/...dica/xdr          [ OK ]
[01:43:06] Scanning for string /var/run/...dica/psg          [ OK ]
[01:43:06] Scanning for string /var/run/...dica/secure       [ OK ]
[01:43:06] Scanning for string /var/run/...dica/rdx          [ OK ]
[01:43:06] Scanning for string /var/run/...dica/va           [ OK ]
[01:43:06] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[01:43:06] Scanning for string /usr/bin/.etc                 [ OK ]
[01:43:06] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[01:43:06] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[01:43:06] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[01:43:06] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[01:43:06] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[01:43:06] Scanning for string /bin/sysback                  [ OK ]
[01:43:06] Scanning for string /usr/local/bin/sysback        [ OK ]
[01:43:06] Scanning for string /usr/lib/.tbd                 [ OK ]
[01:43:06] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[01:43:06] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[01:43:06] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[01:43:06] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[01:43:06] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[01:43:07] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[01:43:07] Scanning for string /usr/info/.torn/sh*           [ OK ]
[01:43:07] Scanning for string /usr/src/.****/.1addr         [ OK ]
[01:43:07] Scanning for string /usr/src/.****/.1file         [ OK ]
[01:43:07] Scanning for string /usr/src/.****/.1proc         [ OK ]
[01:43:08] Scanning for string /usr/src/.****/.1logz         [ OK ]
[01:43:08] Scanning for string /usr/info/.t0rn               [ OK ]
[01:43:08] Scanning for string /dev/.lib                     [ OK ]
[01:43:08] Scanning for string /dev/.lib/lib                 [ OK ]
[01:43:08] Scanning for string /dev/.lib/lib/lib             [ OK ]
[01:43:08] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[01:43:08] Scanning for string /dev/.lib/lib/scan            [ OK ]
[01:43:08] Scanning for string /usr/src/.****                [ OK ]
[01:43:08] Scanning for string /usr/man/man1/man1            [ OK ]
[01:43:08] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[01:43:08] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[01:43:08] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[01:43:08]
[01:43:08] Performing 'shared libraries' checks
[01:43:08] Info: Starting test name 'shared_libs'
[01:43:08] Checking for preloading variables                 [ None found ]
[01:43:08] Checking for preload file                         [ Not found ]
[01:43:08] Info: Starting test name 'shared_libs_path'
[01:43:08] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[01:43:09]
[01:43:09] Performing file properties checks
[01:43:09] Info: Starting test name 'properties'
[01:43:09] Checking for prerequisites                        [ OK ]
[01:43:09] /bin/bash                                         [ OK ]
[01:43:09] /bin/cat                                          [ OK ]
[01:43:09] /bin/chmod                                        [ OK ]
[01:43:10] /bin/chown                                        [ OK ]
[01:43:10] /bin/cp                                           [ OK ]
[01:43:10] /bin/date                                         [ OK ]
[01:43:10] /bin/df                                           [ OK ]
[01:43:11] /bin/dmesg                                        [ OK ]
[01:43:11] /bin/echo                                         [ OK ]
[01:43:11] /bin/ed                                           [ OK ]
[01:43:11] /bin/egrep                                        [ OK ]
[01:43:11] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[01:43:12] /bin/fgrep                                        [ OK ]
[01:43:12] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[01:43:12] /bin/fuser                                        [ OK ]
[01:43:12] /bin/grep                                         [ OK ]
[01:43:12] /bin/ip                                           [ OK ]
[01:43:12] /bin/kill                                         [ OK ]
[01:43:13] /bin/login                                        [ OK ]
[01:43:13] /bin/ls                                           [ OK ]
[01:43:13] /bin/lsmod                                        [ OK ]
[01:43:13] /bin/mktemp                                       [ OK ]
[01:43:13] /bin/more                                         [ OK ]
[01:43:13] /bin/mount                                        [ OK ]
[01:43:13] /bin/mv                                           [ OK ]
[01:43:14] /bin/netstat                                      [ OK ]
[01:43:14] /bin/ps                                           [ OK ]
[01:43:14] /bin/pwd                                          [ OK ]
[01:43:14] /bin/readlink                                     [ OK ]
[01:43:14] /bin/sed                                          [ OK ]
[01:43:14] /bin/sh                                           [ OK ]
[01:43:15] /bin/su                                           [ OK ]
[01:43:15] /bin/touch                                        [ OK ]
[01:43:15] /bin/uname                                        [ OK ]
[01:43:15] /bin/which                                        [ OK ]
[01:43:15] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[01:43:15] /bin/dash                                         [ OK ]
[01:43:16] /usr/bin/awk                                      [ OK ]
[01:43:16] /usr/bin/basename                                 [ OK ]
[01:43:16] /usr/bin/chattr                                   [ OK ]
[01:43:16] /usr/bin/cut                                      [ OK ]
[01:43:16] /usr/bin/diff                                     [ OK ]
[01:43:16] /usr/bin/dirname                                  [ OK ]
[01:43:17] /usr/bin/dpkg                                     [ OK ]
[01:43:17] /usr/bin/dpkg-query                               [ OK ]
[01:43:17] /usr/bin/du                                       [ OK ]
[01:43:17] /usr/bin/env                                      [ OK ]
[01:43:17] /usr/bin/file                                     [ OK ]
[01:43:17] /usr/bin/find                                     [ OK ]
[01:43:17] /usr/bin/GET                                      [ OK ]
[01:43:18] /usr/bin/groups                                   [ OK ]
[01:43:18] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[01:43:18] /usr/bin/head                                     [ OK ]
[01:43:18] /usr/bin/id                                       [ OK ]
[01:43:18] /usr/bin/killall                                  [ OK ]
[01:43:18] /usr/bin/last                                     [ OK ]
[01:43:18] /usr/bin/lastlog                                  [ OK ]
[01:43:18] /usr/bin/ldd                                      [ OK ]
[01:43:19] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[01:43:19] /usr/bin/less                                     [ OK ]
[01:43:19] /usr/bin/locate                                   [ OK ]
[01:43:19] /usr/bin/logger                                   [ OK ]
[01:43:19] /usr/bin/lsattr                                   [ OK ]
[01:43:19] /usr/bin/lsof                                     [ OK ]
[01:43:19] /usr/bin/mail                                     [ OK ]
[01:43:20] /usr/bin/md5sum                                   [ OK ]
[01:43:20] /usr/bin/mlocate                                  [ OK ]
[01:43:20] /usr/bin/newgrp                                   [ OK ]
[01:43:20] /usr/bin/passwd                                   [ OK ]
[01:43:20] /usr/bin/perl                                     [ OK ]
[01:43:20] /usr/bin/pstree                                   [ OK ]
[01:43:21] /usr/bin/rkhunter                                 [ OK ]
[01:43:21] /usr/bin/runcon                                   [ OK ]
[01:43:21] /usr/bin/sha1sum                                  [ OK ]
[01:43:21] /usr/bin/size                                     [ OK ]
[01:43:21] /usr/bin/sort                                     [ OK ]
[01:43:21] /usr/bin/stat                                     [ OK ]
[01:43:22] /usr/bin/strace                                   [ OK ]
[01:43:22] /usr/bin/strings                                  [ OK ]
[01:43:23] /usr/bin/sudo                                     [ OK ]
[01:43:23] /usr/bin/tail                                     [ OK ]
[01:43:23] /usr/bin/test                                     [ OK ]
[01:43:23] /usr/bin/top                                      [ OK ]
[01:43:23] /usr/bin/touch                                    [ OK ]
[01:43:23] /usr/bin/tr                                       [ OK ]
[01:43:24] /usr/bin/uniq                                     [ OK ]
[01:43:24] /usr/bin/users                                    [ OK ]
[01:43:24] /usr/bin/vmstat                                   [ OK ]
[01:43:24] /usr/bin/w                                        [ OK ]
[01:43:24] /usr/bin/watch                                    [ OK ]
[01:43:25] /usr/bin/wc                                       [ OK ]
[01:43:25] /usr/bin/wget                                     [ OK ]
[01:43:25] /usr/bin/whatis                                   [ OK ]
[01:43:25] /usr/bin/whereis                                  [ OK ]
[01:43:25] /usr/bin/which                                    [ OK ]
[01:43:25] /usr/bin/who                                      [ OK ]
[01:43:26] /usr/bin/whoami                                   [ OK ]
[01:43:26] /usr/bin/mawk                                     [ OK ]
[01:43:26] /usr/bin/lwp-request                              [ OK ]
[01:43:26] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[01:43:26] /usr/bin/bsd-mailx                                [ OK ]
[01:43:26] /usr/bin/w.procps                                 [ OK ]
[01:43:26] /sbin/depmod                                      [ OK ]
[01:43:27] /sbin/ifconfig                                    [ OK ]
[01:43:27] /sbin/ifdown                                      [ OK ]
[01:43:27] /sbin/ifup                                        [ OK ]
[01:43:27] /sbin/init                                        [ OK ]
[01:43:27] /sbin/insmod                                      [ OK ]
[01:43:27] /sbin/ip                                          [ OK ]
[01:43:28] /sbin/lsmod                                       [ OK ]
[01:43:28] /sbin/modinfo                                     [ OK ]
[01:43:28] /sbin/modprobe                                    [ OK ]
[01:43:28] /sbin/rmmod                                       [ OK ]
[01:43:28] /sbin/runlevel                                    [ OK ]
[01:43:29] /sbin/sulogin                                     [ OK ]
[01:43:29] /sbin/sysctl                                      [ OK ]
[01:43:29] /sbin/syslogd                                     [ OK ]
[01:43:29] /usr/sbin/adduser                                 [ OK ]
[01:43:29] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[01:43:30] /usr/sbin/chroot                                  [ OK ]
[01:43:30] /usr/sbin/cron                                    [ OK ]
[01:43:30] /usr/sbin/groupadd                                [ OK ]
[01:43:30] /usr/sbin/groupdel                                [ OK ]
[01:43:30] /usr/sbin/groupmod                                [ OK ]
[01:43:30] /usr/sbin/grpck                                   [ OK ]
[01:43:31] /usr/sbin/nologin                                 [ OK ]
[01:43:31] /usr/sbin/pwck                                    [ OK ]
[01:43:31] /usr/sbin/tcpd                                    [ OK ]
[01:43:31] /usr/sbin/unhide                                  [ OK ]
[01:43:32] /usr/sbin/useradd                                 [ OK ]
[01:43:32] /usr/sbin/userdel                                 [ OK ]
[01:43:32] /usr/sbin/usermod                                 [ OK ]
[01:43:32] /usr/sbin/vipw                                    [ OK ]
[01:43:32] /usr/sbin/unhide-linux26                          [ OK ]
[01:43:34]
[01:43:34] Checking for rootkits...
[01:43:34] Info: Starting test name 'rootkits'
[01:43:34]
[01:43:34] Performing check of known rootkit files and directories
[01:43:34] Info: Starting test name 'known_rkts'
[01:43:34]
[01:43:34] Checking for 55808 Trojan - Variant A...
[01:43:34]   Checking for file '/tmp/.../r'                  [ Not found ]
[01:43:34]   Checking for file '/tmp/.../a'                  [ Not found ]
[01:43:34] 55808 Trojan - Variant A                          [ Not found ]
[01:43:35]
[01:43:35] Checking for ADM Worm...
[01:43:35]   Checking for string 'w0rm'                      [ Not found ]
[01:43:35] ADM Worm                                          [ Not found ]
[01:43:35]
[01:43:35] Checking for AjaKit Rootkit...
[01:43:35]   Checking for file '/dev/tux/.addr'              [ Not found ]
[01:43:35]   Checking for file '/dev/tux/.proc'              [ Not found ]
[01:43:35]   Checking for file '/dev/tux/.file'              [ Not found ]
[01:43:35]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[01:43:35]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[01:43:35]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[01:43:35]   Checking for directory '/dev/tux'               [ Not found ]
[01:43:35]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[01:43:35] AjaKit Rootkit                                    [ Not found ]
[01:43:35]
[01:43:35] Checking for aPa Kit...
[01:43:35]   Checking for file '/usr/share/.aPa'             [ Not found ]
[01:43:35] aPa Kit                                           [ Not found ]
[01:43:35]
[01:43:35] Checking for Apache Worm...
[01:43:35]   Checking for file '/bin/.log'                   [ Not found ]
[01:43:35] Apache Worm                                       [ Not found ]
[01:43:35]
[01:43:35] Checking for Ambient (ark) Rootkit...
[01:43:35]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[01:43:35]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[01:43:36]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[01:43:36]   Checking for directory '/dev/ptyxx'             [ Not found ]
[01:43:36] Ambient (ark) Rootkit                             [ Not found ]
[01:43:36]
[01:43:36] Checking for Balaur Rootkit...
[01:43:36]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[01:43:36]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[01:43:36]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[01:43:36]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[01:43:36] Balaur Rootkit                                    [ Not found ]
[01:43:36]
[01:43:36] Checking for BeastKit Rootkit...
[01:43:36]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[01:43:36]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[01:43:36]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[01:43:36]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[01:43:36]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[01:43:36]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[01:43:36]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[01:43:36]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[01:43:36]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[01:43:36]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[01:43:36] BeastKit Rootkit                                  [ Not found ]
[01:43:37]
[01:43:37] Checking for beX2 Rootkit...
[01:43:37]   Checking for directory '/usr/include/bex'       [ Not found ]
[01:43:37] beX2 Rootkit                                      [ Not found ]
[01:43:37]
[01:43:37] Checking for BOBKit Rootkit...
[01:43:37]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../find'           [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../du'             [ Not found ]
[01:43:37]   Checking for file '/usr/lib/.../top'            [ Not found ]
[01:43:37]   Checking for directory '/usr/lib/...'           [ Not found ]
[01:43:37]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[01:43:37]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[01:43:38]   Checking for directory '/tmp/.bkp'              [ Not found ]
[01:43:38] BOBKit Rootkit                                    [ Not found ]
[01:43:38]
[01:43:38] Checking for CiNIK Worm (Slapper.B variant)...
[01:43:38]   Checking for file '/tmp/.cinik'                 [ Not found ]
[01:43:38]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[01:43:38] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[01:43:38]
[01:43:38] Checking for Danny-Boy's Abuse Kit...
[01:43:38]   Checking for file '/dev/mdev'                   [ Not found ]
[01:43:38]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[01:43:38] Danny-Boy's Abuse Kit                             [ Not found ]
[01:43:38]
[01:43:38] Checking for Devil RootKit...
[01:43:38]   Checking for file '/var/lib/games/.src'         [ Not found ]
[01:43:38]   Checking for file '/dev/dsx'                    [ Not found ]
[01:43:38]   Checking for file '/dev/caca'                   [ Not found ]
[01:43:38] Devil RootKit                                     [ Not found ]
[01:43:38]
[01:43:38] Checking for Dica-Kit Rootkit...
[01:43:38]   Checking for file '/lib/.sso'                   [ Not found ]
[01:43:38]   Checking for file '/lib/.so'                    [ Not found ]
[01:43:38]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[01:43:38]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[01:43:38]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[01:43:38]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[01:43:38]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[01:43:39]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[01:43:39]   Checking for file '/var/run/...dica/va'         [ Not found ]
[01:43:39]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[01:43:39]   Checking for file '/usr/bin/.etc'               [ Not found ]
[01:43:39]   Checking for directory '/var/run/...dica'       [ Not found ]
[01:43:39]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[01:43:39]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[01:43:39] Dica-Kit Rootkit                                  [ Not found ]
[01:43:39]
[01:43:39] Checking for Dreams Rootkit...
[01:43:39]   Checking for file '/dev/ttyoa'                  [ Not found ]
[01:43:39]   Checking for file '/dev/ttyof'                  [ Not found ]
[01:43:39]   Checking for file '/dev/ttyop'                  [ Not found ]
[01:43:39]   Checking for file '/usr/bin/sense'              [ Not found ]
[01:43:39]   Checking for file '/usr/bin/sl2'                [ Not found ]
[01:43:39]   Checking for file '/usr/bin/logclear'           [ Not found ]
[01:43:39]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[01:43:39]   Checking for file '/usr/bin/snfs'               [ Not found ]
[01:43:39]   Checking for file '/usr/lib/libsss'             [ Not found ]
[01:43:39]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[01:43:39] Dreams Rootkit                                    [ Not found ]
[01:43:39]
[01:43:39] Checking for Duarawkz Rootkit...
[01:43:40]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[01:43:40]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[01:43:40] Duarawkz Rootkit                                  [ Not found ]
[01:43:40]
[01:43:40] Checking for Enye LKM...
[01:43:40]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[01:43:40] Enye LKM                                          [ Not found ]
[01:43:40]
[01:43:40] Checking for Flea Linux Rootkit...
[01:43:40]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[01:43:40]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[01:43:40]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[01:43:40]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[01:43:40]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[01:43:40]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[01:43:40]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[01:43:40]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[01:43:40]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[01:43:40]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[01:43:40]   Checking for directory '/dev/..0'               [ Not found ]
[01:43:40]   Checking for directory '/dev/..0/backup'        [ Not found ]
[01:43:40] Flea Linux Rootkit                                [ Not found ]
[01:43:41]
[01:43:41] Checking for FreeBSD Rootkit...
[01:43:41]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[01:43:41]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[01:43:41]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[01:43:41]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[01:43:41]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[01:43:41]   Checking for file '/bin/sysback'                [ Not found ]
[01:43:41]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[01:43:41]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[01:43:41]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[01:43:41] FreeBSD Rootkit                                   [ Not found ]
[01:43:41]
[01:43:41] Checking for ****`it Rootkit...
[01:43:41]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[01:43:41]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[01:43:41]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[01:43:41]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[01:43:41]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[01:43:41]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[01:43:41]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[01:43:41]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[01:43:41] ****`it Rootkit                                   [ Not found ]
[01:43:42]
[01:43:42] Checking for GasKit Rootkit...
[01:43:42]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[01:43:42]   Checking for directory '/dev/dev'               [ Not found ]
[01:43:42]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[01:43:42]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[01:43:42] GasKit Rootkit                                    [ Not found ]
[01:43:42]
[01:43:42] Checking for Heroin LKM...
[01:43:42]   Checking for kernel symbol 'heroin'             [ Not found ]
[01:43:42] Heroin LKM                                        [ Not found ]
[01:43:42]
[01:43:42] Checking for HjC Kit...
[01:43:42]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[01:43:42] HjC Kit                                           [ Not found ]
[01:43:42]
[01:43:42] Checking for ignoKit Rootkit...
[01:43:42]   Checking for file '/lib/defs/p'                 [ Not found ]
[01:43:42]   Checking for file '/lib/defs/q'                 [ Not found ]
[01:43:42]   Checking for file '/lib/defs/r'                 [ Not found ]
[01:43:42]   Checking for file '/lib/defs/s'                 [ Not found ]
[01:43:42]   Checking for file '/lib/defs/t'                 [ Not found ]
[01:43:42]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[01:43:42]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[01:43:43]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[01:43:43]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[01:43:43]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[01:43:43]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[01:43:43]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[01:43:43]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[01:43:43]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[01:43:43] ignoKit Rootkit                                   [ Not found ]
[01:43:43]
[01:43:43] Checking for ImperalsS-FBRK Rootkit...
[01:43:43]   Checking for directory '/dev/fd/.88'            [ Not found ]
[01:43:43]   Checking for directory '/dev/fd/.99'            [ Not found ]
[01:43:43] ImperalsS-FBRK Rootkit                            [ Not found ]
[01:43:43]
[01:43:43] Checking for Irix Rootkit...
[01:43:43]   Checking for directory '/dev/pts/01'            [ Not found ]
[01:43:43]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[01:43:43]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[01:43:43]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[01:43:43] Irix Rootkit                                      [ Not found ]
[01:43:43]
[01:43:43] Checking for Kitko Rootkit...
[01:43:43]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[01:43:43] Kitko Rootkit                                     [ Not found ]
[01:43:43]
[01:43:43] Checking for Knark Rootkit...
[01:43:44]   Checking for file '/proc/knark/pids'            [ Not found ]
[01:43:44]   Checking for directory '/proc/knark'            [ Not found ]
[01:43:44] Knark Rootkit                                     [ Not found ]
[01:43:44]
[01:43:44] Checking for Li0n Worm...
[01:43:44]   Checking for file '/bin/in.telnetd'             [ Not found ]
[01:43:44]   Checking for file '/bin/mjy'                    [ Not found ]
[01:43:44]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[01:43:44]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[01:43:44]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[01:43:44]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[01:43:45]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[01:43:45] Li0n Worm                                         [ Not found ]
[01:43:45]
[01:43:45] Checking for Lockit / LJK2 Rootkit...
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[01:43:45]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[01:43:46]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[01:43:46]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[01:43:46] Lockit / LJK2 Rootkit                             [ Not found ]
[01:43:46]
[01:43:46] Checking for Mood-NT Rootkit...
[01:43:47]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[01:43:47]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[01:43:47]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[01:43:47]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[01:43:47]   Checking for directory '/_cthulhu'              [ Not found ]
[01:43:47] Mood-NT Rootkit                                   [ Not found ]
[01:43:47]
[01:43:47] Checking for MRK Rootkit...
[01:43:47]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[01:43:47]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[01:43:47]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[01:43:47]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[01:43:47]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[01:43:47]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[01:43:47] MRK Rootkit                                       [ Not found ]
[01:43:47]
[01:43:47] Checking for Ni0 Rootkit...
[01:43:47]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[01:43:47]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[01:43:47]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[01:43:48]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[01:43:48]   Checking for directory '/tmp/waza'              [ Not found ]
[01:43:48]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[01:43:48]   Checking for directory '/usr/sbin/es'           [ Not found ]
[01:43:48] Ni0 Rootkit                                       [ Not found ]
[01:43:48]
[01:43:48] Checking for Ohhara Rootkit...
[01:43:48]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[01:43:48]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[01:43:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[01:43:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[01:43:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[01:43:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[01:43:48]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[01:43:48] Ohhara Rootkit                                    [ Not found ]
[01:43:48]
[01:43:48] Checking for Optic Kit (Tux) Worm...
[01:43:48]   Checking for directory '/dev/tux'               [ Not found ]
[01:43:48]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[01:43:48]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[01:43:48]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[01:43:48] Optic Kit (Tux) Worm                              [ Not found ]
[01:43:48]
[01:43:48] Checking for Oz Rootkit...
[01:43:48]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[01:43:48]   Checking for directory '/dev/.oz'               [ Not found ]
[01:43:49] Oz Rootkit                                        [ Not found ]
[01:43:49]
[01:43:49] Checking for Phalanx Rootkit...
[01:43:49]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[01:43:49]   Checking for file '/etc/host.ph1'               [ Not found ]
[01:43:49]   Checking for file '/bin/host.ph1'               [ Not found ]
[01:43:49]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[01:43:49]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[01:43:49] Phalanx Rootkit                                   [ Not found ]
[01:43:49]
[01:43:49] Checking for Phalanx Rootkit (strings)...
[01:43:49]   Checking for string 'phalanx'                   [ Not found ]
[01:43:49] Phalanx Rootkit (strings)                         [ Not found ]
[01:43:49]
[01:43:49] Checking for Portacelo Rootkit...
[01:43:49]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../.p'             [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../getty'          [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../show'           [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[01:43:49]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[01:43:50]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[01:43:50]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[01:43:50]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[01:43:50] Portacelo Rootkit                                 [ Not found ]
[01:43:50]
[01:43:50] Checking for R3dstorm Toolkit...
[01:43:50]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[01:43:50]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[01:43:50]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[01:43:50]   Checking for file '/bin/.../see_all'            [ Not found ]
[01:43:50]   Checking for directory '/var/log/tk02'          [ Not found ]
[01:43:50]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[01:43:50]   Checking for directory '/bin/...'               [ Not found ]
[01:43:50] R3dstorm Toolkit                                  [ Not found ]
[01:43:50]
[01:43:50] Checking for RH-Sharpe's Rootkit...
[01:43:50]   Checking for file '/bin/lps'                    [ Not found ]
[01:43:50]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[01:43:50]   Checking for file '/usr/bin/ltop'               [ Not found ]
[01:43:50]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[01:43:51]   Checking for file '/usr/bin/ldu'                [ Not found ]
[01:43:51]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[01:43:51]   Checking for file '/usr/bin/wp'                 [ Not found ]
[01:43:51]   Checking for file '/usr/bin/shad'               [ Not found ]
[01:43:51]   Checking for file '/usr/bin/vadim'              [ Not found ]
[01:43:51]   Checking for file '/usr/bin/slice'              [ Not found ]
[01:43:51]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[01:43:51]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[01:43:51] RH-Sharpe's Rootkit                               [ Not found ]
[01:43:51]
[01:43:51] Checking for RSHA's Rootkit...
[01:43:51]   Checking for file '/bin/kr4p'                   [ Not found ]
[01:43:51]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[01:43:51]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[01:43:51]   Checking for file '/usr/bin/slice2'             [ Not found ]
[01:43:51]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[01:43:51]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[01:43:51]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[01:43:51]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[01:43:51] RSHA's Rootkit                                    [ Not found ]
[01:43:51]
[01:43:51] Checking for Scalper Worm...
[01:43:51]   Checking for file '/tmp/.a'                     [ Not found ]
[01:43:51]   Checking for file '/tmp/.uua'                   [ Not found ]
[01:43:52] Scalper Worm                                      [ Not found ]
[01:43:52]
[01:43:52] Checking for Sebek LKM...
[01:43:52]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[01:43:52] Sebek LKM                                         [ Not found ]
[01:43:52]
[01:43:52] Checking for Shutdown Rootkit...
[01:43:52]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[01:43:52]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[01:43:52]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[01:43:52]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[01:43:52]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[01:43:53]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[01:43:53]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[01:43:53]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[01:43:53] Shutdown Rootkit                                  [ Not found ]
[01:43:53]
[01:43:53] Checking for SHV4 Rootkit...
[01:43:53]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[01:43:53]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[01:43:53]   Checking for file '/lib/lidps1.so'              [ Not found ]
[01:43:53]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[01:43:53]   Checking for directory '/lib/security/.config'  [ Not found ]
[01:43:53]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[01:43:53] SHV4 Rootkit                                      [ Not found ]
[01:43:53]
[01:43:53] Checking for SHV5 Rootkit...
[01:43:53]   Checking for file '/etc/sh.conf'                [ Not found ]
[01:43:53]   Checking for file '/dev/srd0'                   [ Not found ]
[01:43:53]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[01:43:53] SHV5 Rootkit                                      [ Not found ]
[01:43:53]
[01:43:53] Checking for Sin Rootkit...
[01:43:53]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[01:43:53]   Checking for file '/dev/ttyoa'                  [ Not found ]
[01:43:53]   Checking for file '/dev/ttyof'                  [ Not found ]
[01:43:53]   Checking for file '/dev/ttyop'                  [ Not found ]
[01:43:53]   Checking for file '/dev/ttyos'                  [ Not found ]
[01:43:54]   Checking for file '/usr/lib/.lib'               [ Not found ]
[01:43:54]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[01:43:54]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[01:43:54]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[01:43:54]   Checking for file '/usr/man/man1/...'           [ Not found ]
[01:43:54]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[01:43:54]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[01:43:54]   Checking for directory '/usr/lib/sn'            [ Not found ]
[01:43:54]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[01:43:54]   Checking for directory '/dev/.haos'             [ Not found ]
[01:43:54] Sin Rootkit                                       [ Not found ]
[01:43:54]
[01:43:54] Checking for Slapper Worm...
[01:43:54]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[01:43:54]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[01:43:54]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[01:43:54]   Checking for file '/tmp/httpd'                  [ Not found ]
[01:43:54]   Checking for file '/tmp/.unlock'                [ Not found ]
[01:43:54]   Checking for file '/tmp/update'                 [ Not found ]
[01:43:54]   Checking for file '/tmp/.cinik'                 [ Not found ]
[01:43:54]   Checking for file '/tmp/.b'                     [ Not found ]
[01:43:54] Slapper Worm                                      [ Not found ]
[01:43:54]
[01:43:54] Checking for Sneakin Rootkit...
[01:43:54]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[01:43:55] Sneakin Rootkit                                   [ Not found ]
[01:43:55]
[01:43:55] Checking for Suckit Rootkit...
[01:43:55]   Checking for file '/sbin/initsk12'              [ Not found ]
[01:43:55]   Checking for file '/sbin/initxrk'               [ Not found ]
[01:43:55]   Checking for file '/usr/bin/null'               [ Not found ]
[01:43:55]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[01:43:55]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[01:43:55]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[01:43:55]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[01:43:55]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[01:43:55]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[01:43:55]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[01:43:55]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[01:43:55]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[01:43:55]   Checking for directory '/etc/.MG'               [ Not found ]
[01:43:55]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[01:43:55]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[01:43:55] Suckit Rootkit                                    [ Not found ]
[01:43:55]
[01:43:55] Checking for SunOS Rootkit...
[01:43:55]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[01:43:55]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[01:43:56]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[01:43:56]   Checking for file '/bin/xlogin'                 [ Not found ]
[01:43:56]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[01:43:56]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[01:43:56]   Checking for file '/sbin/login'                 [ Not found ]
[01:43:56]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[01:43:56]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[01:43:56]   Checking for file '/dev/kmod'                   [ Not found ]
[01:43:56]   Checking for file '/dev/dos'                    [ Not found ]
[01:43:56] SunOS Rootkit                                     [ Not found ]
[01:43:56]
[01:43:56] Checking for SunOS / NSDAP Rootkit...
[01:43:56]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[01:43:56]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[01:43:56]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[01:43:56]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[01:43:56]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[01:43:56]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[01:43:57]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[01:43:57]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[01:43:57]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[01:43:57]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[01:43:57]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[01:43:57]   Checking for file '/usr/lib/lpset'              [ Not found ]
[01:43:57]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[01:43:57] SunOS / NSDAP Rootkit                             [ Not found ]
[01:43:57]
[01:43:57] Checking for Superkit Rootkit...
[01:43:57]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[01:43:57] Superkit Rootkit                                  [ Not found ]
[01:43:57]
[01:43:57] Checking for TBD (Telnet BackDoor)...
[01:43:57]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[01:43:57] TBD (Telnet BackDoor)                             [ Not found ]
[01:43:57]
[01:43:57] Checking for TeLeKiT Rootkit...
[01:43:57]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[01:43:57]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[01:43:57]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[01:43:57]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[01:43:57]   Checking for file '/dev/ptyr'                   [ Not found ]
[01:43:57]   Checking for file '/dev/ptyp'                   [ Not found ]
[01:43:58]   Checking for file '/dev/ptyq'                   [ Not found ]
[01:43:58]   Checking for file '/dev/hda06'                  [ Not found ]
[01:43:58]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[01:43:58]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[01:43:58]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[01:43:58]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[01:43:58] TeLeKiT Rootkit                                   [ Not found ]
[01:43:58]
[01:43:58] Checking for T0rn Rootkit...
[01:43:58]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[01:43:58]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[01:43:59]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[01:43:59]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[01:43:59]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[01:43:59]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[01:43:59]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[01:43:59]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[01:43:59]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[01:43:59]   Checking for directory '/dev/.lib'              [ Not found ]
[01:43:59]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[01:43:59]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[01:43:59]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[01:43:59]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[01:43:59]   Checking for directory '/usr/src/.****'         [ Not found ]
[01:43:59]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[01:43:59]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[01:44:00]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[01:44:00]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[01:44:00] T0rn Rootkit                                      [ Not found ]
[01:44:00]
[01:44:00] Checking for Trojanit Kit...
[01:44:00]   Checking for file '/bin/.ls'                    [ Not found ]
[01:44:00]   Checking for file '/bin/.ps'                    [ Not found ]
[01:44:00]   Checking for file '/bin/.netstat'               [ Not found ]
[01:44:00]   Checking for file '/usr/bin/.nop'               [ Not found ]
[01:44:00]   Checking for file '/usr/bin/.who'               [ Not found ]
[01:44:00] Trojanit Kit                                      [ Not found ]
[01:44:00]
[01:44:00] Checking for Tuxtendo Rootkit...
[01:44:00]   Checking for file '/dev/tux/.addr'              [ Not found ]
[01:44:00]   Checking for file '/dev/tux/.cron'              [ Not found ]
[01:44:00]   Checking for file '/dev/tux/.file'              [ Not found ]
[01:44:00]   Checking for file '/dev/tux/.log'               [ Not found ]
[01:44:00]   Checking for file '/dev/tux/.proc'              [ Not found ]
[01:44:00]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[01:44:00]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[01:44:01]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[01:44:01]   Checking for directory '/dev/tux'               [ Not found ]
[01:44:01]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[01:44:01]   Checking for directory '/dev/tux/backup'        [ Not found ]
[01:44:01] Tuxtendo Rootkit                                  [ Not found ]
[01:44:01]
[01:44:01] Checking for URK Rootkit...
[01:44:02]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[01:44:02]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[01:44:02]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[01:44:02]   Checking for file '/tmp/conf.inf'               [ Not found ]
[01:44:02]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[01:44:02] URK Rootkit                                       [ Not found ]
[01:44:02]
[01:44:02] Checking for VcKit Rootkit...
[01:44:02]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[01:44:02]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[01:44:02] VcKit Rootkit                                     [ Not found ]
[01:44:02]
[01:44:02] Checking for Volc Rootkit...
[01:44:02]   Checking for directory '/var/spool/.recent'     [ Not found ]
[01:44:02]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[01:44:02]   Checking for directory '/usr/lib/volc'          [ Not found ]
[01:44:02]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[01:44:02] Volc Rootkit                                      [ Not found ]
[01:44:02]
[01:44:02] Checking for X-Org SunOS Rootkit...
[01:44:02]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[01:44:02]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[01:44:03]   Checking for file '/usr/bin/srload'             [ Not found ]
[01:44:03]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[01:44:03]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[01:44:03]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[01:44:03]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[01:44:03]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[01:44:03]   Checking for directory '/usr/share/man...'      [ Not found ]
[01:44:03] X-Org SunOS Rootkit                               [ Not found ]
[01:44:03]
[01:44:03] Checking for zaRwT.KiT Rootkit...
[01:44:03]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[01:44:03]   Checking for file '/dev/ttyf'                   [ Not found ]
[01:44:03]   Checking for file '/dev/ttyp'                   [ Not found ]
[01:44:03]   Checking for file '/dev/ttyn'                   [ Not found ]
[01:44:03]   Checking for file '/rk/tulz'                    [ Not found ]
[01:44:03]   Checking for directory '/rk'                    [ Not found ]
[01:44:03]   Checking for directory '/dev/rd/s'              [ Not found ]
[01:44:03] zaRwT.KiT Rootkit                                 [ Not found ]
[01:44:03]
[01:44:03] Performing additional rootkit checks
[01:44:03] Info: Starting test name 'additional_rkts'
[01:44:03]
[01:44:03]   Performing Suckit Rookit additional checks
[01:44:03]     Checking /sbin/init link count                [ OK ]
[01:44:04]     Checking for hidden file extensions           [ None found ]
[01:44:04]     Running skdet command                         [ Skipped ]
[01:44:04] Info: Unable to find the 'skdet' command
[01:44:04]   Suckit Rookit additional checks                 [ OK ]
[01:44:04]
[01:44:04]   Performing check of possible rootkit files and directories
[01:44:04] Info: Starting test name 'possible_rkt_files'
[01:44:04]     Checking for file '/dev/sdr0'                 [ Not found ]
[01:44:04]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[01:44:04]     Checking for file '/tmp/.bash_history'        [ Not found ]
[01:44:04]     Checking for file '/usr/info/.clib'           [ Not found ]
[01:44:04]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[01:44:04]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[01:44:04]     Checking for file '/sbin/create'              [ Not found ]
[01:44:04]     Checking for file '/dev/ttypz'                [ Not found ]
[01:44:04]     Checking for directory '/usr/bin/take'        [ Not found ]
[01:44:04]     Checking for directory '/usr/src/.lib'        [ Not found ]
[01:44:04]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[01:44:04]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[01:44:05]     Checking for directory '/usr/sbin/...'        [ Not found ]
[01:44:05]     Checking for directory '/usr/share/.gun'      [ Not found ]
[01:44:05]   Checking for possible rootkit files and directories [ None found ]
[01:44:05]
[01:44:05]   Performing check for possible rootkit strings
[01:44:05] Info: Starting test name 'possible_rkt_strings'
[01:44:05] Info: Found local startup file: /etc/rc.local
[01:44:05]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[01:44:05]     Checking for string '****'                    [ Not found ]
[01:44:05]     Checking for string 'backdoor'                [ Not found ]
[01:44:05]     Checking for string 'vt200'                   [ Not found ]
[01:44:05]     Checking for string '/usr/bin/xstat'          [ Not found ]
[01:44:05]     Checking for string '/bin/envpc'              [ Not found ]
[01:44:05]     Checking for string 'L4m3r0x'                 [ Not found ]
[01:44:05]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[01:44:06]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[01:44:06]     Checking for string '/dev/sgk'                [ Not found ]
[01:44:06]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[01:44:06]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[01:44:06]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[01:44:06]     Checking for string '/lib/.sso'               [ Not found ]
[01:44:06]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[01:44:06]     Checking for string '/dev/caca'               [ Not found ]
[01:44:06]     Checking for string '/dev/ttyoa'              [ Not found ]
[01:44:06]     Checking for string 'syg'                     [ Not found ]
[01:44:07]     Checking for string '/dev/pts/01'             [ Not found ]
[01:44:07]     Checking for string 'tw33dl3'                 [ Not found ]
[01:44:07]     Checking for string 'psniff'                  [ Not found ]
[01:44:07]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[01:44:07]     Checking for string 'promiscuous'             [ Not found ]
[01:44:07]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[01:44:07]     Checking for string '/dev/xdta'               [ Not found ]
[01:44:07]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[01:44:07]     Checking for string 'in.inetd'                [ Not found ]
[01:44:07]     Checking for string '#<HIDE_.*>'              [ Not found ]
[01:44:07]     Checking for string 'bin/xchk'                [ Not found ]
[01:44:07]     Checking for string 'bin/xsf'                 [ Not found ]
[01:44:07]   Checking for possible rootkit strings           [ None found ]
[01:44:08]
[01:44:08] Performing malware checks
[01:44:08] Info: Starting test name 'malware'
[01:44:08]
[01:44:08] Info: Test 'deleted_files' disabled at users request.
[01:44:08] Info: Starting test name 'running_procs'
[01:44:08]   Checking running processes for suspicious files [ None found ]
[01:44:08]
[01:44:08] Info: Test 'hidden_procs' disabled at users request.
[01:44:08]
[01:44:08] Info: Test 'suspscan' disabled at users request.
[01:44:08]
[01:44:08]   Performing check for login backdoors
[01:44:08] Info: Starting test name 'other_malware'
[01:44:08]     Checking for '/bin/.login'                    [ Not found ]
[01:44:08]     Checking for '/sbin/.login'                   [ Not found ]
[01:44:08]   Checking for login backdoors                    [ None found ]
[01:44:08]
[01:44:08]   Performing check for suspicious directories
[01:44:08]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[01:44:08]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[01:44:09]   Checking for suspicious directories             [ None found ]
[01:44:09]
[01:44:09]   Checking for software intrusions                [ Skipped ]
[01:44:09] Info: Check skipped - tripwire not installed
[01:44:09]
[01:44:09]   Performing check for sniffer log files
[01:44:09]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[01:44:09]   Checking for sniffer log files                  [ None found ]
[01:44:09]
[01:44:09] Performing trojan specific checks
[01:44:09] Info: Starting test name 'trojans'
[01:44:09] Info: Using inetd configuration file '/etc/inetd.conf'
[01:44:09]   Checking for enabled inetd services             [ OK ]
[01:44:09]
[01:44:09]   Performing check for enabled xinetd services
[01:44:09]   Checking for enabled xinetd services            [ Skipped ]
[01:44:09] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[01:44:09] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[01:44:09]
[01:44:09] Performing Linux specific checks
[01:44:09] Info: Starting test name 'os_specific'
[01:44:09]   Checking kernel module commands                 [ OK ]
[01:44:09] Info: Using modules pathname of '/lib/modules/2.6.27-9-generic'
[01:44:10]   Checking kernel module names                    [ OK ]
[01:44:10]
[01:44:10] Checking the network...
[01:44:10] Info: Starting test name 'network'
[01:44:10] Info: Starting test name 'ports'
[01:44:10]
[01:44:10] Performing check for backdoor ports
[01:44:10]   Checking for UDP port 2001                      [ Not found ]
[01:44:10]   Checking for TCP port 2006                      [ Not found ]
[01:44:10]   Checking for TCP port 2128                      [ Not found ]
[01:44:10]   Checking for TCP port 14856                     [ Not found ]
[01:44:10]   Checking for TCP port 47107                     [ Not found ]
[01:44:11]   Checking for TCP port 60922                     [ Not found ]
[01:44:11]
[01:44:11] Performing checks on the network interfaces
[01:44:11] Info: Starting test name 'promisc'
[01:44:11]   Checking for promiscuous interfaces             [ None found ]
[01:44:11]
[01:44:11] Info: Test 'packet_cap_apps' disabled at users request.
[01:44:11]
[01:44:11] Checking the local host...
[01:44:11] Info: Starting test name 'local_host'
[01:44:11]
[01:44:11] Performing system boot checks
[01:44:11] Info: Starting test name 'startup_files'
[01:44:11]   Checking for local host name                    [ Found ]
[01:44:11] Info: Starting test name 'startup_malware'
[01:44:11] Info: Found local startup file: /etc/rc.local
[01:44:11]   Checking for local startup files                [ Found ]
[01:44:11]   Checking local startup files for malware        [ None found ]
[01:44:11] Info: Found system startup directory: /etc/init.d
[01:44:13]   Checking system startup files for malware       [ None found ]
[01:44:13]
[01:44:13] Performing group and account checks
[01:44:13] Info: Starting test name 'group_accounts'
[01:44:13]   Checking for passwd file                        [ Found ]
[01:44:13] Info: Found password file: /etc/passwd
[01:44:13]   Checking for root equivalent (UID 0) accounts   [ None found ]
[01:44:13] Info: Found shadow file: /etc/shadow
[01:44:13]   Checking for passwordless accounts              [ None found ]
[01:44:13] Info: Starting test name 'passwd_changes'
[01:44:13]   Checking for passwd file changes                [ None found ]
[01:44:13] Info: Starting test name 'group_changes'
[01:44:13]   Checking for group file changes                 [ None found ]
[01:44:13]   Checking root account shell history files       [ None found ]
[01:44:14]
[01:44:14] Performing system configuration file checks
[01:44:14] Info: Starting test name 'system_configs'
[01:44:14]   Checking for SSH configuration file             [ Not found ]
[01:44:14]   Checking for running syslog daemon              [ Found ]
[01:44:14]   Checking for syslog configuration file          [ Found ]
[01:44:14] Info: Found syslog configuration file: /etc/syslog.conf
[01:44:14]   Checking if syslog remote logging is allowed    [ Not allowed ]
[01:44:14]
[01:44:14] Performing filesystem checks
[01:44:14] Info: Starting test name 'filesystem'
[01:44:14] Info: SCAN_MODE_DEV set to 'THOROUGH'
[01:44:17]   Checking /dev for suspicious file types         [ Warning ]
[01:44:17] Warning: Suspicious file types found in /dev:
[01:44:17]          /dev/shm/pulse-shm-2529837409: data
[01:44:17]   Checking for hidden files and directories       [ None found ]
[01:44:17]
[01:44:17] Checking application versions...
[01:44:17] Info: Starting test name 'apps'
[01:44:17]   Checking version of Exim MTA                    [ OK ]
[01:44:17] Info: Application 'exim' version '4.69' found.
[01:44:18]   Checking version of GnuPG                       [ OK ]
[01:44:18] Info: Application 'gpg' version '1.4.9' found.
[01:44:18] Info: Application 'httpd' not found.
[01:44:18] Info: Application 'named' not found.
[01:44:18]   Checking version of OpenSSL                     [ OK ]
[01:44:18] Info: Application 'openssl' version '0.9.8g' found.
[01:44:18] Info: Application 'php' not found.
[01:44:18] Info: Application 'procmail' not found.
[01:44:18] Info: Application 'proftpd' not found.
[01:44:18] Info: Application 'sshd' not found.
[01:44:18] Info: Applications checked: 3 out of 9
[01:44:18]
[01:44:18] System checks summary
[01:44:18] =====================
[01:44:18]
[01:44:18] File properties checks...
[01:44:18] Files checked: 127
[01:44:18] Suspect files: 0
[01:44:18]
[01:44:18] Rootkit checks...
[01:44:18] Rootkits checked : 109
[01:44:18] Possible rootkits: 0
[01:44:18]
[01:44:18] Applications checks...
[01:44:18] Applications checked: 3
[01:44:18] Suspect applications: 0
[01:44:18]
[01:44:18] The system checks took: 1 minute and 15 seconds
[01:44:19]
[01:44:19] Info: End date is Mon Dec 29 01:44:19 CST 2008
```

---

### Post by scorp123 on 2008-12-29
"nothing found" is self-explanatory, don't you think? :D

Besides: Why are you even scanning for rootkits? Are you running a server with 100's of other users on it, each with their own shell accounts, many users maybe even with "sudo" priviledges ... ?

If not and if you're the only user on this machine and if you only install software via the "synaptic" package manager then you can save yourself these hassles because it's highly unlikely that you got infected with a rootkit in the first place.

---

