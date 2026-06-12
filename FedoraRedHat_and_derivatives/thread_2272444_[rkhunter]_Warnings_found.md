---
title: "[rkhunter] Warnings found"
date: 2015-04-06
forum: Fedora/RedHat and derivatives
---

### Post by michal17 on 2015-04-06
Hello everyone
i just ran rkhunter and it gave me lots of warnings so it got me all worried and im not sure what to do . any suggestion please?
and im on CentOS 6.0. applications:
     - WWW: apache2 / php5 / ssl
     - Base: MySQL5
     - E-mail: qmail
     - FTP: proftpd
     - Admin: Plesk 10

and here is my log , thank you 

```
Please inspect this machine, because it may be infected. Scan log:
[01:00:30] Running Rootkit Hunter version 1.3.4 on ns3301094
[01:00:30]
[01:00:30] Info: Start date is Mon Apr  6 01:00:30 CEST 2015
[01:00:30]
[01:00:30] Checking configuration file and command-line options...
[01:00:30] Info: Detected operating system is 'Linux'
[01:00:30] Info: Found O/S name: CentOS release 6.4 (Final)
[01:00:30] Info: Command line is /usr/local/psa/admin/sbin/modules//watchdog/rkhunter -c --configfile /usr/local/psa/etc/modules/watchdog/rkhunter.conf --cronjob --propupd --createlogfile
[01:00:30] Info: Environment shell is /bin/sh; rkhunter is using bash
[01:00:30] Info: Using configuration file '/usr/local/psa/etc/modules/watchdog/rkhunter.conf'
[01:00:30] Info: Installation directory is '/usr/local/psa'
[01:00:30] Info: Using language 'en'
[01:00:30] Info: Using '/usr/local/psa/var/modules/watchdog/lib/rkhunter/lib/rkhunter/db' as the database directory
[01:00:30] Info: Using '/usr/local/psa/var/modules/watchdog/lib/rkhunter/rkhunter/scripts' as the support script directory
[01:00:30] Info: Using '/usr/local/psa/admin/bin/modules/watchdog /usr/local/bin /usr/local/sbin /bin /sbin /usr/bin /usr/sbin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[01:00:30] Info: Using '/' as the root directory by default
[01:00:30] Info: Using '/usr/local/psa/var/modules/watchdog/lib/rkhunter/lib/rkhunter/tmp' as the temporary directory
[01:00:30] Info: Emailing warnings to 'kontakt@webstar.info.pl' using command '/usr/local/psa/admin/bin/modules/watchdog/send-mail'
[01:00:30] Info: X will be automatically detected
[01:00:30] Info: Found the 'diff' command: /usr/bin/diff
[01:00:30] Info: Found the 'file' command: /usr/bin/file
[01:00:30] Info: Found the 'find' command: /bin/find
[01:00:30] Info: Found the 'ifconfig' command: /sbin/ifconfig
[01:00:30] Info: Found the 'ip' command: /sbin/ip
[01:00:30] Info: Found the 'ldd' command: /usr/bin/ldd
[01:00:30] Info: Found the 'lsattr' command: /usr/bin/lsattr
[01:00:30] Info: Found the 'lsmod' command: /sbin/lsmod
[01:00:30] Info: Found the 'lsof' command: /usr/sbin/lsof
[01:00:30] Info: Found the 'mktemp' command: /bin/mktemp
[01:00:30] Info: Found the 'netstat' command: /bin/netstat
[01:00:30] Info: Found the 'perl' command: /usr/bin/perl
[01:00:30] Info: Found the 'ps' command: /bin/ps
[01:00:30] Info: Found the 'pwd' command: /bin/pwd
[01:00:30] Info: Found the 'readlink' command: /bin/readlink
[01:00:30] Info: Found the 'sort' command: /bin/sort
[01:00:30] Info: Found the 'stat' command: /usr/bin/stat
[01:00:30] Info: Found the 'strings' command: /usr/bin/strings
[01:00:30] Info: Found the 'uniq' command: /usr/bin/uniq
[01:00:30] Info: System is not using prelinking
[01:00:30] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[01:00:30] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[01:00:30] Info: Stored hash values used package manager 'RPM' (md5 function)
[01:00:30] Info: The hash function field index is set to 1
[01:00:30] Info: Using package manager 'RPM' to update the file hash values
[01:00:30] Info: Found the 'rpm' command: /bin/rpm
[01:00:30] Info: Using package manager 'RPM' for file property checks
[01:00:30] Info: Found the 'rpm' command: /bin/rpm
[01:00:30] Info: Previous file attributes were stored
[01:00:30] Info: Current file attributes will be stored
[01:00:30] Info: Enabled tests are: all
[01:00:30] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[01:00:30] Info: Found ksym file '/proc/kallsyms'
[01:00:30]
[01:00:30] Checking if the O/S has changed since last time...
[01:00:30] Info: Nothing seems to have changed
[01:00:30]
[01:00:30] Info: Starting file properties data update...
[01:00:30] Info: Created temporary file '/usr/local/psa/var/modules/watchdog/lib/rkhunter/lib/rkhunter/tmp/rkhunter.dat.MCNYuXwIcu'
[01:00:30] Collecting O/S info...
[01:00:30] Info: Found system architecture: x86_64
[01:00:30] Info: Found release file: /etc/centos-release
[01:00:30] Info: Found O/S name: CentOS release 6.4 (Final)
[01:00:30] Getting file properties...
[01:00:32] Info: Found 41 files in /bin
[01:00:34] Info: Found 53 files in /usr/bin
[01:00:34] Info: Found 18 files in /sbin
[01:00:35] Info: Found 15 files in /usr/sbin
[01:00:35] Info: Found 0 files in /usr/local/bin
[01:00:35] Info: Found 0 files in /usr/local/sbin
[01:00:35] Info: Found 0 files in /usr/libexec
[01:00:35] Info: Found 0 files in /usr/local/libexec
[01:00:35] Info: File updated: searched for 151 files, found 127
[01:00:35] Info: New rkhunter.dat file installed in '/usr/local/psa/var/modules/watchdog/lib/rkhunter/lib/rkhunter/db'
[01:00:35]
[01:00:35] Starting system checks...
[01:00:35]
[01:00:35] Checking system commands...
[01:00:35] Info: Starting test name 'system_commands'
[01:00:35]
[01:00:35] Performing 'strings' command checks
[01:00:35] Info: Starting test name 'strings'
[01:00:35] Scanning for string /usr/sbin/ntpsx               [ OK ]
[01:00:35] Scanning for string /usr/lib/.../ls               [ OK ]
[01:00:35] Scanning for string /usr/lib/.../netstat          [ OK ]
[01:00:35] Scanning for string /usr/lib/.../lsof             [ OK ]
[01:00:35] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[01:00:35] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[01:00:35] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[01:00:35] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[01:00:35] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[01:00:35] Scanning for string /usr/lib/.../psr              [ OK ]
[01:00:35] Scanning for string /usr/lib/.../find             [ OK ]
[01:00:35] Scanning for string /usr/lib/.../pstree           [ OK ]
[01:00:35] Scanning for string /usr/lib/.../slocate          [ OK ]
[01:00:35] Scanning for string /usr/lib/.../du               [ OK ]
[01:00:35] Scanning for string /usr/lib/.../top              [ OK ]
[01:00:35] Scanning for string /usr/lib/...                  [ OK ]
[01:00:35] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[01:00:35] Scanning for string /usr/lib/.bkit-               [ OK ]
[01:00:35] Scanning for string /tmp/.bkp                     [ OK ]
[01:00:35] Scanning for string /tmp/.cinik                   [ OK ]
[01:00:35] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[01:00:35] Scanning for string /lib/.sso                     [ OK ]
[01:00:35] Scanning for string /lib/.so                      [ OK ]
[01:00:35] Scanning for string /var/run/...dica/clean        [ OK ]
[01:00:35] Scanning for string /var/run/...dica/xl           [ OK ]
[01:00:35] Scanning for string /var/run/...dica/xdr          [ OK ]
[01:00:35] Scanning for string /var/run/...dica/psg          [ OK ]
[01:00:35] Scanning for string /var/run/...dica/secure       [ OK ]
[01:00:35] Scanning for string /var/run/...dica/rdx          [ OK ]
[01:00:35] Scanning for string /var/run/...dica/va           [ OK ]
[01:00:35] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[01:00:35] Scanning for string /usr/bin/.etc                 [ OK ]
[01:00:35] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[01:00:35] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[01:00:35] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[01:00:35] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[01:00:35] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[01:00:35] Scanning for string /bin/sysback                  [ OK ]
[01:00:35] Scanning for string /usr/local/bin/sysback        [ OK ]
[01:00:35] Scanning for string /usr/lib/.tbd                 [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[01:00:35] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[01:00:36] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[01:00:36] Scanning for string /usr/info/.torn/sh*           [ OK ]
[01:00:36] Scanning for string /usr/src/.puta/.1addr         [ OK ]
[01:00:36] Scanning for string /usr/src/.puta/.1file         [ OK ]
[01:00:36] Scanning for string /usr/src/.puta/.1proc         [ OK ]
[01:00:36] Scanning for string /usr/src/.puta/.1logz         [ OK ]
[01:00:36] Scanning for string /usr/info/.t0rn               [ OK ]
[01:00:36] Scanning for string /dev/.lib                     [ OK ]
[01:00:36] Scanning for string /dev/.lib/lib                 [ OK ]
[01:00:36] Scanning for string /dev/.lib/lib/lib             [ OK ]
[01:00:36] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[01:00:36] Scanning for string /dev/.lib/lib/scan            [ OK ]
[01:00:36] Scanning for string /usr/src/.puta                [ OK ]
[01:00:36] Scanning for string /usr/man/man1/man1            [ OK ]
[01:00:36] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[01:00:36] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[01:00:36] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[01:00:36]
[01:00:36] Performing 'shared libraries' checks
[01:00:36] Info: Starting test name 'shared_libs'
[01:00:36] Checking for preloading variables                 [ None found ]
[01:00:36] Checking for preload file                         [ Not found ]
[01:00:36] Info: Starting test name 'shared_libs_path'
[01:00:36] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[01:00:36]
[01:00:36] Performing file properties checks
[01:00:36] Info: Starting test name 'properties'
[01:00:36] Checking for prerequisites                        [ OK ]
[01:00:36] /bin/awk                                          [ OK ]
[01:00:37] /bin/basename                                     [ OK ]
[01:00:37] /bin/bash                                         [ OK ]
[01:00:37] /bin/cat                                          [ OK ]
[01:00:38] /bin/chmod                                        [ OK ]
[01:00:38] /bin/chown                                        [ OK ]
[01:00:38] /bin/cp                                           [ OK ]
[01:00:38] /bin/csh                                          [ OK ]
[01:00:38] /bin/cut                                          [ OK ]
[01:00:38] /bin/date                                         [ OK ]
[01:00:38] /bin/df                                           [ OK ]
[01:00:39] /bin/dmesg                                        [ OK ]
[01:00:39] /bin/echo                                         [ OK ]
[01:00:39] /bin/ed                                           [ OK ]
[01:00:40] /bin/egrep                                        [ OK ]
[01:00:40] /bin/env                                          [ OK ]
[01:00:40] /bin/fgrep                                        [ OK ]
[01:00:40] /bin/find                                         [ OK ]
[01:00:40] /bin/grep                                         [ OK ]
[01:00:40] /bin/kill                                         [ OK ]
[01:00:40] /bin/login                                        [ OK ]
[01:00:40] /bin/ls                                           [ OK ]
[01:00:41] /bin/mail                                         [ OK ]
[01:00:41] /bin/mktemp                                       [ OK ]
[01:00:41] /bin/more                                         [ OK ]
[01:00:41] /bin/mount                                        [ OK ]
[01:00:41] /bin/mv                                           [ OK ]
[01:00:41] /bin/netstat                                      [ OK ]
[01:00:41] /bin/ps                                           [ OK ]
[01:00:42] /bin/pwd                                          [ OK ]
[01:00:42] /bin/readlink                                     [ OK ]
[01:00:42] /bin/rpm                                          [ OK ]
[01:00:42] /bin/sed                                          [ OK ]
[01:00:42] /bin/sh                                           [ OK ]
[01:00:42] /bin/sort                                         [ OK ]
[01:00:42] /bin/su                                           [ OK ]
[01:00:42] /bin/touch                                        [ OK ]
[01:00:43] /bin/uname                                        [ OK ]
[01:00:43] /bin/gawk                                         [ OK ]
[01:00:43] /bin/tcsh                                         [ OK ]
[01:00:43] /bin/mailx                                        [ OK ]
[01:00:43] /usr/bin/awk                                      [ OK ]
[01:00:43] /usr/bin/chattr                                   [ OK ]
[01:00:43] /usr/bin/curl                                     [ OK ]
[01:00:43] /usr/bin/cut                                      [ OK ]
[01:00:43] /usr/bin/diff                                     [ OK ]
[01:00:43] /usr/bin/dirname                                  [ OK ]
[01:00:44] /usr/bin/du                                       [ OK ]
[01:00:44] /usr/bin/env                                      [ OK ]
[01:00:44] /usr/bin/file                                     [ OK ]
[01:00:44] /usr/bin/find                                     [ OK ]
[01:00:44] /usr/bin/GET                                      [ OK ]
[01:00:44] /usr/bin/groups                                   [ OK ]
[01:00:44] /usr/bin/head                                     [ OK ]
[01:00:44] /usr/bin/id                                       [ OK ]
[01:00:44] /usr/bin/kill                                     [ OK ]
[01:00:44] /usr/bin/killall                                  [ OK ]
[01:00:45] /usr/bin/last                                     [ OK ]
[01:00:45] /usr/bin/lastlog                                  [ OK ]
[01:00:46] /usr/bin/ldd                                      [ OK ]
[01:00:46] /usr/bin/less                                     [ OK ]
[01:00:46] /usr/bin/locate                                   [ OK ]
[01:00:47] /usr/bin/logger                                   [ OK ]
[01:00:47] /usr/bin/lsattr                                   [ OK ]
[01:00:47] /usr/bin/md5sum                                   [ OK ]
[01:00:47] /usr/bin/newgrp                                   [ OK ]
[01:00:47] /usr/bin/passwd                                   [ OK ]
[01:00:47] Info: Found file '/usr/bin/passwd': it is whitelisted for the 'file immutable-bit' check.
[01:00:48] /usr/bin/perl                                     [ OK ]
[01:00:48] /usr/bin/pstree                                   [ OK ]
[01:00:48] /usr/bin/readlink                                 [ OK ]
[01:00:48] /usr/bin/runcon                                   [ OK ]
[01:00:48] /usr/bin/sha1sum                                  [ OK ]
[01:00:49] /usr/bin/size                                     [ OK ]
[01:00:49] /usr/bin/stat                                     [ OK ]
[01:00:49] /usr/bin/strace                                   [ OK ]
[01:00:49] /usr/bin/strings                                  [ OK ]
[01:00:49] /usr/bin/sudo                                     [ OK ]
[01:00:49] /usr/bin/tail                                     [ OK ]
[01:00:49] /usr/bin/test                                     [ OK ]
[01:00:49] /usr/bin/top                                      [ OK ]
[01:00:50] /usr/bin/tr                                       [ OK ]
[01:00:50] /usr/bin/uniq                                     [ OK ]
[01:00:50] /usr/bin/users                                    [ OK ]
[01:00:50] /usr/bin/vmstat                                   [ OK ]
[01:00:50] /usr/bin/w                                        [ OK ]
[01:00:50] /usr/bin/watch                                    [ OK ]
[01:00:50] /usr/bin/wc                                       [ OK ]
[01:00:50] /usr/bin/wget                                     [ OK ]
[01:00:51] /usr/bin/whatis                                   [ OK ]
[01:00:51] /usr/bin/whereis                                  [ OK ]
[01:00:51] /usr/bin/which                                    [ OK ]
[01:00:51] /usr/bin/who                                      [ OK ]
[01:00:51] /usr/bin/whoami                                   [ OK ]
[01:00:51] /usr/bin/gawk                                     [ OK ]
[01:00:51] /sbin/chkconfig                                   [ OK ]
[01:00:52] /sbin/depmod                                      [ OK ]
[01:00:52] /sbin/fuser                                       [ OK ]
[01:00:52] /sbin/ifconfig                                    [ OK ]
[01:00:52] /sbin/ifdown                                      [ OK ]
[01:00:53] /sbin/ifup                                        [ OK ]
[01:00:53] /sbin/init                                        [ OK ]
[01:00:53] Info: Found file '/sbin/init': it is whitelisted for the 'file immutable-bit' check.
[01:00:53] /sbin/insmod                                      [ OK ]
[01:00:53] /sbin/ip                                          [ OK ]
[01:00:53] /sbin/lsmod                                       [ OK ]
[01:00:53] /sbin/modinfo                                     [ OK ]
[01:00:53] /sbin/modprobe                                    [ OK ]
[01:00:53] /sbin/nologin                                     [ OK ]
[01:00:53] /sbin/rmmod                                       [ OK ]
[01:00:54] /sbin/rsyslogd                                    [ OK ]
[01:00:54] /sbin/runlevel                                    [ OK ]
[01:00:54] /sbin/sulogin                                     [ OK ]
[01:00:54] /sbin/sysctl                                      [ OK ]
[01:00:54] /usr/sbin/adduser                                 [ OK ]
[01:00:54] /usr/sbin/chroot                                  [ OK ]
[01:00:54] /usr/sbin/groupadd                                [ OK ]
[01:00:54] /usr/sbin/groupdel                                [ OK ]
[01:00:54] /usr/sbin/groupmod                                [ OK ]
[01:00:54] /usr/sbin/grpck                                   [ OK ]
[01:00:54] /usr/sbin/lsof                                    [ OK ]
[01:00:54] /usr/sbin/pwck                                    [ OK ]
[01:00:55] /usr/sbin/sestatus                                [ OK ]
[01:00:55] /usr/sbin/tcpd                                    [ OK ]
[01:00:55] /usr/sbin/useradd                                 [ OK ]
[01:00:55] /usr/sbin/userdel                                 [ OK ]
[01:00:56] /usr/sbin/usermod                                 [ OK ]
[01:00:56] /usr/sbin/vipw                                    [ OK ]
[01:00:56] /usr/sbin/xinetd                                  [ OK ]
[01:00:57]
[01:00:57] Checking for rootkits...
[01:00:57] Info: Starting test name 'rootkits'
[01:00:57]
[01:00:57] Performing check of known rootkit files and directories
[01:00:57] Info: Starting test name 'known_rkts'
[01:00:57]
[01:00:57] Checking for 55808 Trojan - Variant A...
[01:00:57]   Checking for file '/tmp/.../r'                  [ Not found ]
[01:00:57]   Checking for file '/tmp/.../a'                  [ Not found ]
[01:00:57] 55808 Trojan - Variant A                          [ Not found ]
[01:00:57]
[01:00:57] Checking for ADM Worm...
[01:00:57]   Checking for string 'w0rm'                      [ Not found ]
[01:00:57] ADM Worm                                          [ Not found ]
[01:00:57]
[01:00:57] Checking for AjaKit Rootkit...
[01:00:57]   Checking for file '/dev/tux/.addr'              [ Not found ]
[01:00:57]   Checking for file '/dev/tux/.proc'              [ Not found ]
[01:00:57]   Checking for file '/dev/tux/.file'              [ Not found ]
[01:00:57]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[01:00:57]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[01:00:57]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[01:00:57]   Checking for directory '/dev/tux'               [ Not found ]
[01:00:57]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[01:00:57] AjaKit Rootkit                                    [ Not found ]
[01:00:57]
[01:00:57] Checking for aPa Kit...
[01:00:57]   Checking for file '/usr/share/.aPa'             [ Not found ]
[01:00:57] aPa Kit                                           [ Not found ]
[01:00:57]
[01:00:57] Checking for Apache Worm...
[01:00:57]   Checking for file '/bin/.log'                   [ Not found ]
[01:00:57] Apache Worm                                       [ Not found ]
[01:00:57]
[01:00:57] Checking for Ambient (ark) Rootkit...
[01:00:57]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[01:00:57]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[01:00:57]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[01:00:57]   Checking for directory '/dev/ptyxx'             [ Not found ]
[01:00:57] Ambient (ark) Rootkit                             [ Not found ]
[01:00:57]
[01:00:57] Checking for Balaur Rootkit...
[01:00:57]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[01:00:57]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[01:00:57]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[01:00:57]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[01:00:57] Balaur Rootkit                                    [ Not found ]
[01:00:57]
[01:00:57] Checking for BeastKit Rootkit...
[01:00:57]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[01:00:57]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[01:00:57]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[01:00:57]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[01:00:57]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[01:00:57]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[01:00:57]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[01:00:57]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[01:00:57]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[01:00:57]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[01:00:57] BeastKit Rootkit                                  [ Not found ]
[01:00:57]
[01:00:57] Checking for beX2 Rootkit...
[01:00:57]   Checking for directory '/usr/include/bex'       [ Not found ]
[01:00:57] beX2 Rootkit                                      [ Not found ]
[01:00:57]
[01:00:57] Checking for BOBKit Rootkit...
[01:00:57]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[01:00:57]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[01:00:57]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[01:00:57]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[01:00:57]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../find'           [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../du'             [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.../top'            [ Not found ]
[01:00:58]   Checking for directory '/usr/lib/...'           [ Not found ]
[01:00:58]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[01:00:58]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[01:00:58]   Checking for directory '/tmp/.bkp'              [ Not found ]
[01:00:58] BOBKit Rootkit                                    [ Not found ]
[01:00:58]
[01:00:58] Checking for CiNIK Worm (Slapper.B variant)...
[01:00:58]   Checking for file '/tmp/.cinik'                 [ Not found ]
[01:00:58]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[01:00:58] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[01:00:58]
[01:00:58] Checking for Danny-Boy's Abuse Kit...
[01:00:58]   Checking for file '/dev/mdev'                   [ Not found ]
[01:00:58]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[01:00:58] Danny-Boy's Abuse Kit                             [ Not found ]
[01:00:58]
[01:00:58] Checking for Devil RootKit...
[01:00:58]   Checking for file '/var/lib/games/.src'         [ Not found ]
[01:00:58]   Checking for file '/dev/dsx'                    [ Not found ]
[01:00:58]   Checking for file '/dev/caca'                   [ Not found ]
[01:00:58] Devil RootKit                                     [ Not found ]
[01:00:58]
[01:00:58] Checking for Dica-Kit Rootkit...
[01:00:58]   Checking for file '/lib/.sso'                   [ Not found ]
[01:00:58]   Checking for file '/lib/.so'                    [ Not found ]
[01:00:58]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[01:00:58]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[01:00:58]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[01:00:58]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[01:00:58]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[01:00:58]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[01:00:58]   Checking for file '/var/run/...dica/va'         [ Not found ]
[01:00:58]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[01:00:58]   Checking for file '/usr/bin/.etc'               [ Not found ]
[01:00:58]   Checking for directory '/var/run/...dica'       [ Not found ]
[01:00:58]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[01:00:58]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[01:00:58] Dica-Kit Rootkit                                  [ Not found ]
[01:00:58]
[01:00:58] Checking for Dreams Rootkit...
[01:00:58]   Checking for file '/dev/ttyoa'                  [ Not found ]
[01:00:58]   Checking for file '/dev/ttyof'                  [ Not found ]
[01:00:58]   Checking for file '/dev/ttyop'                  [ Not found ]
[01:00:58]   Checking for file '/usr/bin/sense'              [ Not found ]
[01:00:58]   Checking for file '/usr/bin/sl2'                [ Not found ]
[01:00:58]   Checking for file '/usr/bin/logclear'           [ Not found ]
[01:00:58]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[01:00:58]   Checking for file '/usr/bin/snfs'               [ Not found ]
[01:00:58]   Checking for file '/usr/lib/libsss'             [ Not found ]
[01:00:58]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[01:00:58] Dreams Rootkit                                    [ Not found ]
[01:00:58]
[01:00:58] Checking for Duarawkz Rootkit...
[01:00:58]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[01:00:58]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[01:00:58] Duarawkz Rootkit                                  [ Not found ]
[01:00:58]
[01:00:58] Checking for Enye LKM...
[01:00:58]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[01:00:58] Enye LKM                                          [ Not found ]
[01:00:58]
[01:00:58] Checking for Flea Linux Rootkit...
[01:00:58]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[01:00:58]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[01:00:58]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[01:00:58]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[01:00:58]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[01:00:58]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[01:00:58]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[01:00:58]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[01:00:58]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[01:00:58]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[01:00:58]   Checking for directory '/dev/..0'               [ Not found ]
[01:00:58]   Checking for directory '/dev/..0/backup'        [ Not found ]
[01:00:58] Flea Linux Rootkit                                [ Not found ]
[01:00:58]
[01:00:58] Checking for FreeBSD Rootkit...
[01:00:58]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[01:00:58]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[01:00:58]   Checking for file '/bin/sysback'                [ Not found ]
[01:00:59]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[01:00:59]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[01:00:59]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[01:00:59] FreeBSD Rootkit                                   [ Not found ]
[01:00:59]
[01:00:59] Checking for ****`it Rootkit...
[01:00:59]   Checking for file '/dev/proc/****it/hax0r'      [ Not found ]
[01:00:59]   Checking for file '/dev/proc/****it/hax0rshell' [ Not found ]
[01:00:59]   Checking for file '/dev/proc/****it/config/lports' [ Not found ]
[01:00:59]   Checking for file '/dev/proc/****it/config/rports' [ Not found ]
[01:00:59]   Checking for file '/dev/proc/****it/config/rkconf' [ Not found ]
[01:00:59]   Checking for file '/dev/proc/****it/config/password' [ Not found ]
[01:00:59]   Checking for file '/dev/proc/****it/config/progs' [ Not found ]
[01:00:59]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[01:00:59] ****`it Rootkit                                   [ Not found ]
[01:00:59]
[01:00:59] Checking for GasKit Rootkit...
[01:00:59]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[01:00:59]   Checking for directory '/dev/dev'               [ Not found ]
[01:00:59]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[01:00:59]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[01:00:59] GasKit Rootkit                                    [ Not found ]
[01:00:59]
[01:00:59] Checking for Heroin LKM...
[01:00:59]   Checking for kernel symbol 'heroin'             [ Not found ]
[01:00:59] Heroin LKM                                        [ Not found ]
[01:00:59]
[01:00:59] Checking for HjC Kit...
[01:00:59]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[01:00:59] HjC Kit                                           [ Not found ]
[01:00:59]
[01:00:59] Checking for ignoKit Rootkit...
[01:00:59]   Checking for file '/lib/defs/p'                 [ Not found ]
[01:00:59]   Checking for file '/lib/defs/q'                 [ Not found ]
[01:00:59]   Checking for file '/lib/defs/r'                 [ Not found ]
[01:00:59]   Checking for file '/lib/defs/s'                 [ Not found ]
[01:00:59]   Checking for file '/lib/defs/t'                 [ Not found ]
[01:00:59]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[01:00:59]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[01:00:59]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[01:00:59]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[01:00:59]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[01:00:59]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[01:00:59]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[01:00:59]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[01:00:59]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[01:00:59] ignoKit Rootkit                                   [ Not found ]
[01:00:59]
[01:00:59] Checking for ImperalsS-FBRK Rootkit...
[01:00:59]   Checking for directory '/dev/fd/.88'            [ Not found ]
[01:00:59]   Checking for directory '/dev/fd/.99'            [ Not found ]
[01:00:59] ImperalsS-FBRK Rootkit                            [ Not found ]
[01:00:59]
[01:00:59] Checking for IntoXonia-NG Rootkit...
[01:00:59]   Checking for kernel symbol 'funces'             [ Not found ]
[01:00:59]   Checking for kernel symbol 'ixinit'             [ Not found ]
[01:00:59]   Checking for kernel symbol 'tricks'             [ Not found ]
[01:00:59]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[01:00:59]   Checking for kernel symbol 'rootme'             [ Not found ]
[01:00:59]   Checking for kernel symbol 'hide_module'        [ Not found ]
[01:00:59]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[01:00:59] IntoXonia-NG Rootkit                              [ Not found ]
[01:00:59]
[01:00:59] Checking for Irix Rootkit...
[01:00:59]   Checking for directory '/dev/pts/01'            [ Not found ]
[01:00:59]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[01:00:59]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[01:00:59]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[01:00:59] Irix Rootkit                                      [ Not found ]
[01:00:59]
[01:00:59] Checking for Kitko Rootkit...
[01:00:59]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[01:00:59] Kitko Rootkit                                     [ Not found ]
[01:00:59]
[01:00:59] Checking for Knark Rootkit...
[01:00:59]   Checking for file '/proc/knark/pids'            [ Not found ]
[01:00:59]   Checking for directory '/proc/knark'            [ Not found ]
[01:00:59] Knark Rootkit                                     [ Not found ]
[01:00:59]
[01:00:59] Checking for Li0n Worm...
[01:00:59]   Checking for file '/bin/in.telnetd'             [ Not found ]
[01:00:59]   Checking for file '/bin/mjy'                    [ Not found ]
[01:00:59]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[01:00:59]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[01:00:59]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[01:00:59]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[01:00:59]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[01:00:59]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[01:01:00]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[01:01:00] Li0n Worm                                         [ Not found ]
[01:01:00]
[01:01:00] Checking for Lockit / LJK2 Rootkit...
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[01:01:00]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[01:01:00]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[01:01:00] Lockit / LJK2 Rootkit                             [ Not found ]
[01:01:00]
[01:01:00] Checking for Mood-NT Rootkit...
[01:01:00]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[01:01:00]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[01:01:00]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[01:01:00]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[01:01:00]   Checking for directory '/_cthulhu'              [ Not found ]
[01:01:00] Mood-NT Rootkit                                   [ Not found ]
[01:01:00]
[01:01:00] Checking for MRK Rootkit...
[01:01:00]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[01:01:00]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[01:01:00]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[01:01:00]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[01:01:00]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[01:01:00]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[01:01:00] MRK Rootkit                                       [ Not found ]
[01:01:00]
[01:01:00] Checking for Ni0 Rootkit...
[01:01:00]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[01:01:00]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[01:01:00]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[01:01:00]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[01:01:00]   Checking for directory '/tmp/waza'              [ Not found ]
[01:01:00]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[01:01:00]   Checking for directory '/usr/sbin/es'           [ Not found ]
[01:01:00] Ni0 Rootkit                                       [ Not found ]
[01:01:00]
[01:01:00] Checking for Ohhara Rootkit...
[01:01:00]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[01:01:00]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[01:01:00]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[01:01:00]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[01:01:00]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[01:01:00]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[01:01:00]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[01:01:00] Ohhara Rootkit                                    [ Not found ]
[01:01:00]
[01:01:00] Checking for Optic Kit (Tux) Worm...
[01:01:00]   Checking for directory '/dev/tux'               [ Not found ]
[01:01:00]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[01:01:00]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[01:01:00]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[01:01:01] Optic Kit (Tux) Worm                              [ Not found ]
[01:01:01]
[01:01:01] Checking for Oz Rootkit...
[01:01:01]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[01:01:01]   Checking for directory '/dev/.oz'               [ Not found ]
[01:01:01] Oz Rootkit                                        [ Not found ]
[01:01:01]
[01:01:01] Checking for Phalanx Rootkit...
[01:01:01]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[01:01:01]   Checking for file '/etc/host.ph1'               [ Not found ]
[01:01:01]   Checking for file '/bin/host.ph1'               [ Not found ]
[01:01:01]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[01:01:01]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[01:01:01] Phalanx Rootkit                                   [ Not found ]
[01:01:01]
[01:01:01] Checking for Phalanx Rootkit (strings)...
[01:01:01]   Checking for string 'phalanx'                   [ Not found ]
[01:01:01] Phalanx Rootkit (strings)                         [ Not found ]
[01:01:01]
[01:01:01] Checking for Phalanx2 Rootkit...
[01:01:01]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[01:01:01]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[01:01:01]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[01:01:01]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[01:01:01]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[01:01:01]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[01:01:01]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[01:01:01]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[01:01:01]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[01:01:01]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[01:01:01] Phalanx2 Rootkit                                  [ Not found ]
[01:01:01]
[01:01:01] Checking for Phalanx2 Rootkit (extended tests)...
[01:01:01]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[01:01:01]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[01:01:01] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[01:01:01]
[01:01:01] Checking for Portacelo Rootkit...
[01:01:01]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../.p'             [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../getty'          [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../show'           [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[01:01:01]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[01:01:01]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[01:01:01] Portacelo Rootkit                                 [ Not found ]
[01:01:01]
[01:01:01] Checking for R3dstorm Toolkit...
[01:01:01]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[01:01:01]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[01:01:01]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[01:01:01]   Checking for file '/bin/.../see_all'            [ Not found ]
[01:01:01]   Checking for directory '/var/log/tk02'          [ Not found ]
[01:01:01]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[01:01:01]   Checking for directory '/bin/...'               [ Not found ]
[01:01:01] R3dstorm Toolkit                                  [ Not found ]
[01:01:01]
[01:01:01] Checking for RH-Sharpe's Rootkit...
[01:01:01]   Checking for file '/bin/lps'                    [ Not found ]
[01:01:01]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[01:01:01]   Checking for file '/usr/bin/ltop'               [ Not found ]
[01:01:01]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[01:01:01]   Checking for file '/usr/bin/ldu'                [ Not found ]
[01:01:01]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[01:01:01]   Checking for file '/usr/bin/wp'                 [ Not found ]
[01:01:01]   Checking for file '/usr/bin/shad'               [ Not found ]
[01:01:01]   Checking for file '/usr/bin/vadim'              [ Not found ]
[01:01:01]   Checking for file '/usr/bin/slice'              [ Not found ]
[01:01:01]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[01:01:01]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[01:01:01] RH-Sharpe's Rootkit                               [ Not found ]
[01:01:01]
[01:01:01] Checking for RSHA's Rootkit...
[01:01:01]   Checking for file '/bin/kr4p'                   [ Not found ]
[01:01:01]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[01:01:01]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[01:01:01]   Checking for file '/usr/bin/slice2'             [ Not found ]
[01:01:01]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[01:01:01]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[01:01:01]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[01:01:01]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[01:01:01] RSHA's Rootkit                                    [ Not found ]
[01:01:01]
[01:01:01] Checking for Scalper Worm...
[01:01:01]   Checking for file '/tmp/.a'                     [ Not found ]
[01:01:01]   Checking for file '/tmp/.uua'                   [ Not found ]
[01:01:01] Scalper Worm                                      [ Not found ]
[01:01:01]
[01:01:01] Checking for Sebek LKM...
[01:01:02]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[01:01:02] Sebek LKM                                         [ Not found ]
[01:01:02]
[01:01:02] Checking for Shutdown Rootkit...
[01:01:02]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[01:01:02]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[01:01:02]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[01:01:02]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[01:01:02]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[01:01:02]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[01:01:02]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[01:01:02]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[01:01:02] Shutdown Rootkit                                  [ Not found ]
[01:01:02]
[01:01:02] Checking for SHV4 Rootkit...
[01:01:02]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[01:01:02]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[01:01:02]   Checking for file '/lib/lidps1.so'              [ Not found ]
[01:01:02]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[01:01:02]   Checking for directory '/lib/security/.config'  [ Not found ]
[01:01:02]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[01:01:02] SHV4 Rootkit                                      [ Not found ]
[01:01:02]
[01:01:02] Checking for SHV5 Rootkit...
[01:01:02]   Checking for file '/etc/sh.conf'                [ Not found ]
[01:01:02]   Checking for file '/dev/srd0'                   [ Not found ]
[01:01:03]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[01:01:03] SHV5 Rootkit                                      [ Not found ]
[01:01:03]
[01:01:03] Checking for Sin Rootkit...
[01:01:03]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[01:01:03]   Checking for file '/dev/ttyoa'                  [ Not found ]
[01:01:03]   Checking for file '/dev/ttyof'                  [ Not found ]
[01:01:03]   Checking for file '/dev/ttyop'                  [ Not found ]
[01:01:03]   Checking for file '/dev/ttyos'                  [ Not found ]
[01:01:03]   Checking for file '/usr/lib/.lib'               [ Not found ]
[01:01:03]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[01:01:03]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[01:01:03]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[01:01:03]   Checking for file '/usr/man/man1/...'           [ Not found ]
[01:01:03]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[01:01:03]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[01:01:03]   Checking for directory '/usr/lib/sn'            [ Not found ]
[01:01:03]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[01:01:03]   Checking for directory '/dev/.haos'             [ Not found ]
[01:01:03] Sin Rootkit                                       [ Not found ]
[01:01:03]
[01:01:03] Checking for Slapper Worm...
[01:01:03]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[01:01:03]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[01:01:03]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[01:01:03]   Checking for file '/tmp/httpd'                  [ Not found ]
[01:01:03]   Checking for file '/tmp/.unlock'                [ Not found ]
[01:01:03]   Checking for file '/tmp/update'                 [ Not found ]
[01:01:03]   Checking for file '/tmp/.cinik'                 [ Not found ]
[01:01:03]   Checking for file '/tmp/.b'                     [ Not found ]
[01:01:03] Slapper Worm                                      [ Not found ]
[01:01:03]
[01:01:03] Checking for Sneakin Rootkit...
[01:01:03]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[01:01:03] Sneakin Rootkit                                   [ Not found ]
[01:01:03]
[01:01:03] Checking for Suckit Rootkit...
[01:01:03]   Checking for file '/sbin/initsk12'              [ Not found ]
[01:01:03]   Checking for file '/sbin/initxrk'               [ Not found ]
[01:01:03]   Checking for file '/usr/bin/null'               [ Not found ]
[01:01:03]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[01:01:03]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[01:01:03]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[01:01:03]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[01:01:03]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[01:01:03]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[01:01:03]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[01:01:03]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[01:01:03]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[01:01:03]   Checking for directory '/etc/.MG'               [ Not found ]
[01:01:03]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[01:01:03]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[01:01:03] Suckit Rootkit                                    [ Not found ]
[01:01:03]
[01:01:03] Checking for SunOS Rootkit...
[01:01:03]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[01:01:03]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[01:01:03]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[01:01:03]   Checking for file '/bin/xlogin'                 [ Not found ]
[01:01:03]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[01:01:03]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[01:01:03]   Checking for file '/sbin/login'                 [ Not found ]
[01:01:03]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[01:01:03]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[01:01:03]   Checking for file '/dev/kmod'                   [ Not found ]
[01:01:03]   Checking for file '/dev/dos'                    [ Not found ]
[01:01:03] SunOS Rootkit                                     [ Not found ]
[01:01:03]
[01:01:03] Checking for SunOS / NSDAP Rootkit...
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[01:01:03]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[01:01:03]   Checking for file '/usr/lib/lpset'              [ Not found ]
[01:01:03]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[01:01:03] SunOS / NSDAP Rootkit                             [ Not found ]
[01:01:03]
[01:01:03] Checking for Superkit Rootkit...
[01:01:03]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[01:01:03] Superkit Rootkit                                  [ Not found ]
[01:01:03]
[01:01:03] Checking for TBD (Telnet BackDoor)...
[01:01:03]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[01:01:04] TBD (Telnet BackDoor)                             [ Not found ]
[01:01:04]
[01:01:04] Checking for TeLeKiT Rootkit...
[01:01:04]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[01:01:04]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[01:01:04]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[01:01:04]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[01:01:04]   Checking for file '/dev/ptyr'                   [ Not found ]
[01:01:04]   Checking for file '/dev/ptyp'                   [ Not found ]
[01:01:04]   Checking for file '/dev/ptyq'                   [ Not found ]
[01:01:04]   Checking for file '/dev/hda06'                  [ Not found ]
[01:01:04]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[01:01:04]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[01:01:04]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[01:01:04]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[01:01:04] TeLeKiT Rootkit                                   [ Not found ]
[01:01:04]
[01:01:04] Checking for T0rn Rootkit...
[01:01:04]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[01:01:04]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[01:01:04]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[01:01:04]   Checking for file '/usr/src/.puta/.1addr'       [ Not found ]
[01:01:04]   Checking for file '/usr/src/.puta/.1file'       [ Not found ]
[01:01:04]   Checking for file '/usr/src/.puta/.1proc'       [ Not found ]
[01:01:04]   Checking for file '/usr/src/.puta/.1logz'       [ Not found ]
[01:01:04]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[01:01:04]   Checking for directory '/dev/.lib'              [ Not found ]
[01:01:04]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[01:01:04]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[01:01:04]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[01:01:04]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[01:01:04]   Checking for directory '/usr/src/.puta'         [ Not found ]
[01:01:04]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[01:01:04]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[01:01:04]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[01:01:04]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[01:01:04] T0rn Rootkit                                      [ Not found ]
[01:01:04]
[01:01:04] Checking for Trojanit Kit...
[01:01:04]   Checking for file '/bin/.ls'                    [ Not found ]
[01:01:04]   Checking for file '/bin/.ps'                    [ Not found ]
[01:01:04]   Checking for file '/bin/.netstat'               [ Not found ]
[01:01:04]   Checking for file '/usr/bin/.nop'               [ Not found ]
[01:01:04]   Checking for file '/usr/bin/.who'               [ Not found ]
[01:01:04] Trojanit Kit                                      [ Not found ]
[01:01:04]
[01:01:04] Checking for Tuxtendo Rootkit...
[01:01:04]   Checking for file '/dev/tux/.addr'              [ Not found ]
[01:01:04]   Checking for file '/dev/tux/.cron'              [ Not found ]
[01:01:04]   Checking for file '/dev/tux/.file'              [ Not found ]
[01:01:04]   Checking for file '/dev/tux/.log'               [ Not found ]
[01:01:04]   Checking for file '/dev/tux/.proc'              [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[01:01:04]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[01:01:04]   Checking for directory '/dev/tux'               [ Not found ]
[01:01:05]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[01:01:05]   Checking for directory '/dev/tux/backup'        [ Not found ]
[01:01:05] Tuxtendo Rootkit                                  [ Not found ]
[01:01:05]
[01:01:05] Checking for URK Rootkit...
[01:01:05]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[01:01:05]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[01:01:05]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[01:01:05]   Checking for file '/tmp/conf.inf'               [ Not found ]
[01:01:05]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[01:01:05] URK Rootkit                                       [ Not found ]
[01:01:05]
[01:01:05] Checking for Vampire Rootkit...
[01:01:05]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[01:01:05]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[01:01:05]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[01:01:05]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[01:01:05] Vampire Rootkit                                   [ Not found ]
[01:01:05]
[01:01:05] Checking for VcKit Rootkit...
[01:01:05]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[01:01:05]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[01:01:05] VcKit Rootkit                                     [ Not found ]
[01:01:05]
[01:01:05] Checking for Volc Rootkit...
[01:01:05]   Checking for directory '/var/spool/.recent'     [ Not found ]
[01:01:05]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[01:01:05]   Checking for directory '/usr/lib/volc'          [ Not found ]
[01:01:05]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[01:01:05] Volc Rootkit                                      [ Not found ]
[01:01:05]
[01:01:05] Checking for X-Org SunOS Rootkit...
[01:01:05]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[01:01:05]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[01:01:05]   Checking for file '/usr/bin/srload'             [ Not found ]
[01:01:05]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[01:01:05]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[01:01:05]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[01:01:05]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[01:01:05]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[01:01:05]   Checking for directory '/usr/share/man...'      [ Not found ]
[01:01:05] X-Org SunOS Rootkit                               [ Not found ]
[01:01:05]
[01:01:05] Checking for zaRwT.KiT Rootkit...
[01:01:05]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[01:01:05]   Checking for file '/dev/ttyf'                   [ Not found ]
[01:01:05]   Checking for file '/dev/ttyp'                   [ Not found ]
[01:01:05]   Checking for file '/dev/ttyn'                   [ Not found ]
[01:01:05]   Checking for file '/rk/tulz'                    [ Not found ]
[01:01:05]   Checking for directory '/rk'                    [ Not found ]
[01:01:05]   Checking for directory '/dev/rd/s'              [ Not found ]
[01:01:05] zaRwT.KiT Rootkit                                 [ Not found ]
[01:01:05]
[01:01:05] Performing additional rootkit checks
[01:01:05] Info: Starting test name 'additional_rkts'
[01:01:05]
[01:01:05]   Performing Suckit Rookit additional checks
[01:01:05]     Checking hard link count on '/sbin/init'      [ OK ]
[01:01:05]     Checking for hidden file extensions           [ None found ]
[01:01:05]     Running skdet command                         [ Skipped ]
[01:01:05] Info: Unable to find the 'skdet' command
[01:01:05]   Suckit Rookit additional checks                 [ OK ]
[01:01:05]
[01:01:05]   Performing check of possible rootkit files and directories
[01:01:05] Info: Starting test name 'possible_rkt_files'
[01:01:05]     Checking for file '/dev/sdr0'                 [ Not found ]
[01:01:05]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[01:01:05]     Checking for file '/tmp/.bash_history'        [ Not found ]
[01:01:05]     Checking for file '/usr/info/.clib'           [ Not found ]
[01:01:05]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[01:01:05]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[01:01:05]     Checking for file '/sbin/create'              [ Not found ]
[01:01:05]     Checking for file '/dev/ttypz'                [ Not found ]
[01:01:05]     Checking for directory '/usr/bin/take'        [ Not found ]
[01:01:05]     Checking for directory '/usr/src/.lib'        [ Not found ]
[01:01:05]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[01:01:05]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[01:01:05]     Checking for directory '/usr/sbin/...'        [ Not found ]
[01:01:05]     Checking for directory '/usr/share/.gun'      [ Not found ]
[01:01:05]   Checking for possible rootkit files and directories [ None found ]
[01:01:05]
[01:01:05]   Performing check for possible rootkit strings
[01:01:05] Info: Starting test name 'possible_rkt_strings'
[01:01:05] Info: Using system startup paths: /etc/rc.d /etc/inittab
[01:01:05]     Checking for string '/dev/proc/****it'        [ Not found ]
[01:01:06]     Checking for string '****'                    [ Not found ]
[01:01:06]     Checking for string 'backdoor'                [ Not found ]
[01:01:06]     Checking for string 'vt200'                   [ Not found ]
[01:01:06]     Checking for string '/usr/bin/xstat'          [ Not found ]
[01:01:06]     Checking for string '/bin/envpc'              [ Not found ]
[01:01:06]     Checking for string 'L4m3r0x'                 [ Not found ]
[01:01:06]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[01:01:06]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[01:01:06]     Checking for string '/dev/sgk'                [ Not found ]
[01:01:06]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[01:01:06]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[01:01:06]     Checking for string '/dev/proc/****it'        [ Not found ]
[01:01:06]     Checking for string '/lib/.sso'               [ Not found ]
[01:01:06]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[01:01:06]     Checking for string '/dev/caca'               [ Not found ]
[01:01:06]     Checking for string '/dev/ttyoa'              [ Not found ]
[01:01:06]     Checking for string 'syg'                     [ Not found ]
[01:01:06]     Checking for string '/dev/pts/01'             [ Not found ]
[01:01:06]     Checking for string 'tw33dl3'                 [ Not found ]
[01:01:06]     Checking for string 'psniff'                  [ Not found ]
[01:01:06]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[01:01:06]     Checking for string '/dev/ptyxx'              [ Not found ]
[01:01:06]     Checking for string '/dev/xdta'               [ Not found ]
[01:01:06]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[01:01:06]     Checking for string 'in.inetd'                [ Not found ]
[01:01:06]     Checking for string '#<HIDE_.*>'              [ Not found ]
[01:01:06]     Checking for string 'bin/xchk'                [ Not found ]
[01:01:06]     Checking for string 'bin/xsf'                 [ Not found ]
[01:01:06]   Checking for possible rootkit strings           [ None found ]
[01:01:06]
[01:01:06] Performing malware checks
[01:01:06] Info: Starting test name 'malware'
[01:01:06]
[01:01:06] Info: Test 'deleted_files' disabled at users request.
[01:01:06] Info: Starting test name 'running_procs'
[01:01:07]   Checking running processes for suspicious files [ None found ]
[01:01:07]
[01:01:07] Info: Test 'hidden_procs' disabled at users request.
[01:01:07]
[01:01:07] Info: Test 'suspscan' disabled at users request.
[01:01:07]
[01:01:07]   Performing check for login backdoors
[01:01:07] Info: Starting test name 'other_malware'
[01:01:07]     Checking for '/bin/.login'                    [ Not found ]
[01:01:07]     Checking for '/sbin/.login'                   [ Not found ]
[01:01:07]   Checking for login backdoors                    [ None found ]
[01:01:07]
[01:01:07]   Performing check for suspicious directories
[01:01:07]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[01:01:07]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[01:01:07]   Checking for suspicious directories             [ None found ]
[01:01:07]
[01:01:07]   Checking for software intrusions                [ Skipped ]
[01:01:07] Info: Check skipped - tripwire not installed
[01:01:07]
[01:01:07]   Performing check for sniffer log files
[01:01:07]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[01:01:07]   Checking for sniffer log files                  [ None found ]
[01:01:07]
[01:01:07] Performing trojan specific checks
[01:01:07] Info: Starting test name 'trojans'
[01:01:07]   Checking for enabled inetd services             [ Skipped ]
[01:01:07] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[01:01:07]
[01:01:07]   Performing check for enabled xinetd services
[01:01:07] Info: Using xinetd configuration file '/etc/xinetd.conf'
[01:01:07]     Checking '/etc/xinetd.conf' for enabled services [ None found ]
[01:01:07]       Found 'includedir /etc/xinetd.d' directive
[01:01:07]     Checking '/etc/xinetd.d/chargen-dgram' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/chargen-stream' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/daytime-dgram' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/daytime-stream' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/discard-dgram' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/discard-stream' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/echo-dgram' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/echo-stream' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/ftp_psa' for enabled services [ Warning ]
[01:01:07]     Checking '/etc/xinetd.d/poppassd_psa' for enabled services [ Warning ]
[01:01:07]     Checking '/etc/xinetd.d/rsync' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/smtp_psa' for enabled services [ Warning ]
[01:01:07]     Checking '/etc/xinetd.d/smtps_psa' for enabled services [ Warning ]
[01:01:07]     Checking '/etc/xinetd.d/submission_psa' for enabled services [ Warning ]
[01:01:07]     Checking '/etc/xinetd.d/tcpmux-server' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/time-dgram' for enabled services [ None found ]
[01:01:07]     Checking '/etc/xinetd.d/time-stream' for enabled services [ None found ]
[01:01:07]   Checking for enabled xinetd services            [ Warning ]
[01:01:07] Warning: Found enabled xinetd service: /etc/xinetd.d/ftp_psa
[01:01:07] Warning: Found enabled xinetd service: /etc/xinetd.d/poppassd_psa
[01:01:07] Warning: Found enabled xinetd service: /etc/xinetd.d/smtp_psa
[01:01:07] Warning: Found enabled xinetd service: /etc/xinetd.d/smtps_psa
[01:01:07] Warning: Found enabled xinetd service: /etc/xinetd.d/submission_psa
[01:01:07]   Checking for Apache backdoor                    [ Not found ]
[01:01:07]
[01:01:07] Performing Linux specific checks
[01:01:07] Info: Starting test name 'os_specific'
[01:01:07]   Checking loaded kernel modules                  [ Warning ]
[01:01:07] Warning: The modules file '/proc/modules' is missing.
[01:01:07] Info: Using modules pathname of '/lib/modules'
[01:01:07]   Checking kernel module names                    [ Skipped ]
[01:01:07] Warning: The kernel modules directory '/lib/modules' is missing or empty.
[01:01:07]
[01:01:07] Checking the network...
[01:01:07] Info: Starting test name 'network'
[01:01:07] Info: Starting test name 'ports'
[01:01:07]
[01:01:07] Performing check for backdoor ports
[01:01:07]   Checking for TCP port 1524                      [ Not found ]
[01:01:07]   Checking for TCP port 1984                      [ Not found ]
[01:01:07]   Checking for UDP port 2001                      [ Not found ]
[01:01:07]   Checking for TCP port 2006                      [ Not found ]
[01:01:07]   Checking for TCP port 2128                      [ Not found ]
[01:01:08]   Checking for TCP port 6666                      [ Not found ]
[01:01:08]   Checking for TCP port 6667                      [ Not found ]
[01:01:08]   Checking for TCP port 6668                      [ Not found ]
[01:01:08]   Checking for TCP port 6669                      [ Not found ]
[01:01:08]   Checking for TCP port 7000                      [ Not found ]
[01:01:08]   Checking for TCP port 13000                     [ Not found ]
[01:01:08]   Checking for TCP port 14856                     [ Not found ]
[01:01:08]   Checking for TCP port 25000                     [ Not found ]
[01:01:08]   Checking for TCP port 29812                     [ Not found ]
[01:01:08]   Checking for TCP port 31337                     [ Not found ]
[01:01:08]   Checking for TCP port 32982                     [ Not found ]
[01:01:08]   Checking for TCP port 33369                     [ Not found ]
[01:01:08]   Checking for TCP port 47107                     [ Not found ]
[01:01:08]   Checking for TCP port 47018                     [ Not found ]
[01:01:08]   Checking for TCP port 60922                     [ Not found ]
[01:01:08]   Checking for TCP port 62883                     [ Not found ]
[01:01:08]   Checking for TCP port 65535                     [ Not found ]
[01:01:08]
[01:01:08] Performing checks on the network interfaces
[01:01:08] Info: Starting test name 'promisc'
[01:01:08]   Checking for promiscuous interfaces             [ None found ]
[01:01:08]
[01:01:08] Info: Test 'packet_cap_apps' disabled at users request.
[01:01:08]
[01:01:08] Checking the local host...
[01:01:08] Info: Starting test name 'local_host'
[01:01:08]
[01:01:08] Performing system boot checks
[01:01:08] Info: Starting test name 'startup_files'
[01:01:08]   Checking for local host name                    [ Found ]
[01:01:08] Info: Starting test name 'startup_malware'
[01:01:08]   Checking for system startup files               [ Found ]
[01:01:08]   Checking system startup files for malware       [ None found ]
[01:01:08]
[01:01:08] Performing group and account checks
[01:01:08] Info: Starting test name 'group_accounts'
[01:01:08]   Checking for passwd file                        [ Found ]
[01:01:08] Info: Found password file: /etc/passwd
[01:01:08]   Checking for root equivalent (UID 0) accounts   [ None found ]
[01:01:08] Info: Found shadow file: /etc/shadow
[01:01:08]   Checking for passwordless accounts              [ None found ]
[01:01:08] Info: Starting test name 'passwd_changes'
[01:01:08]   Checking for passwd file changes                [ Warning ]
[01:01:08] Warning: Unable to check for passwd file differences: no copy of the passwd file exists.
[01:01:08] Info: Starting test name 'group_changes'
[01:01:08]   Checking for group file changes                 [ Warning ]
[01:01:08] Warning: Unable to check for group file differences: no copy of the group file exists.
[01:01:08]   Checking root account shell history files       [ OK ]
[01:01:08]
[01:01:08] Performing system configuration file checks
[01:01:08] Info: Starting test name 'system_configs'
[01:01:08]   Checking for SSH configuration file             [ Found ]
[01:01:08] Info: Found SSH configuration file: /etc/ssh/sshd_config
[01:01:08] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'unset'.
[01:01:09] Info: Rkhunter option ALLOW_SSH_PROT_V1 set to '2'.
[01:01:09]   Checking if SSH root access is allowed          [ Not set ]
[01:01:09]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
[01:01:09]   Checking for running syslog daemon              [ Found ]
[01:01:09]   Checking for syslog configuration file          [ Found ]
[01:01:09] Info: Found syslog configuration file: /etc/rsyslog.conf
[01:01:09]   Checking if syslog remote logging is allowed    [ Not allowed ]
[01:01:09]
[01:01:09] Performing filesystem checks
[01:01:09] Info: Starting test name 'filesystem'
[01:01:09] Info: SCAN_MODE_DEV set to 'THOROUGH'
[01:01:09]   Checking /dev for suspicious file types         [ Warning ]
[01:01:09] Warning: Suspicious file types found in /dev:
[01:01:09]          /dev/md/autorebuild.pid: ASCII text
[01:01:09]          /dev/md/md-device-map: ASCII text
[01:01:09]   Checking for hidden files and directories       [ Warning ]
[01:01:09] Warning: Hidden directory found: /dev/.udev
[01:01:09] Warning: Hidden file found: /usr/share/man/man5/.k5identity.5.gz: gzip compressed data, from Unix, max compression
[01:01:09] Warning: Hidden file found: /usr/share/man/man5/.k5login.5.gz: gzip compressed data, from Unix, max compression
[01:01:09] Warning: Hidden file found: /usr/share/man/man1/..1.gz: gzip compressed data, from Unix, max compression
[01:01:09] Warning: Hidden file found: /usr/bin/.ssh.hmac: ASCII text
[01:01:09] Warning: Hidden file found: /usr/bin/.fipscheck.hmac: ASCII text
[01:01:09] Warning: Hidden file found: /usr/sbin/.sshd.hmac: ASCII text
[01:01:09]
[01:01:09] Checking application versions...
[01:01:09] Info: Starting test name 'apps'
[01:01:09] Info: Application 'exim' not found.
[01:01:09]   Checking version of GnuPG                       [ OK ]
[01:01:09] Info: Application 'gpg' version '2.0.14' found.
[01:01:09]   Checking version of Apache                      [ Warning ]
[01:01:09] Warning: Application 'httpd', version '2.2.15', is out of date, and possibly a security risk.
[01:01:09]   Checking version of Bind DNS                    [ OK ]
[01:01:09] Info: Application 'named' version '9.8.2rc1' found.
[01:01:09]   Checking version of OpenSSL                     [ OK ]
[01:01:09] Info: Application 'openssl' version '1.0.1e-fips' found.
[01:01:09]   Checking version of PHP                         [ OK ]
[01:01:09] Info: Application 'php' version '5.3.3' found.
[01:01:09]   Checking version of Procmail MTA                [ OK ]
[01:01:09] Info: Application 'procmail' version '3.22' found.
[01:01:09]   Checking version of ProFTPd                     [ Skipped ]
[01:01:09] Info: Unable to obtain version number for 'proftpd': version option gives: ProFTPD Version 1.3.3e
[01:01:09]   Checking version of OpenSSH                     [ OK ]
[01:01:09] Info: Application 'sshd' version '5.3p1' found.
[01:01:09] Info: Applications checked: 8 out of 9
[01:01:10]
[01:01:10] System checks summary
[01:01:10] =====================
[01:01:10]
[01:01:10] File properties checks...
[01:01:10] Files checked: 127
[01:01:10] Suspect files: 0
[01:01:10]
[01:01:10] Rootkit checks...
[01:01:10] Rootkits checked : 112
[01:01:10] Possible rootkits: 0
[01:01:10]
[01:01:10] Applications checks...
[01:01:10] Applications checked: 8
[01:01:10] Suspect applications: 1
[01:01:10]
[01:01:10] The system checks took: 34 seconds
```

---

### Post by oldos2er on 2015-04-06
Moved to Other OS Support & Projects, Fedora/Red Hat and derivatives. Centos support forums are at [https://www.centos.org/forums/](https://www.centos.org/forums/)

---

### Post by Habitual on 2015-04-07
> **michal17 said:**
> im not sure what to do . any suggestion please?
```
Please inspect this machine, because it may be infected.
```[B]
Investigate[/B] the files 
I use ```
string /path/to/file
```and
```
file /path/to/file
``` then
 ```
less /path/to/file
``` if it is not a binary.

Examine closely the /etc/rkhunter.conf for the very-much explained 
ALLOWHIDDENFILE and ALLOWHIDDENDIR directives.

Here's a working example of their usage:
```
ALLOWHIDDENFILE=/dev/.initramfs
ALLOWHIDDENDIR=/etc/.java
ALLOWHIDDENDIR=/dev/.udev/db
ALLOWDEVFILE=/dev/.udev/rules.d/root.rules
ALLOWDEVFILE=/dev/.blkid.tab
ALLOWDEVFILE=/dev/.blkid.tab.old
SCRIPTWHITELIST=/usr/sbin/adduser
SCRIPTWHITELIST=/usr/bin/ldd
SCRIPTWHITELIST=/sbin/chkconfig
SCRIPTWHITELIST=/bin/which
```


It is NOT clear to me if you need to run 
```
rkhunter --propupd
``` after editing /etc/rkhunter.conf

I do use 
```
rkhunter --check-config
``` to debug any edits in /etc/rkhunter.conf

Once the file have been examined and the results deemed safe to proceed, then you should run
```
rkhunter --propupd
``` to update the file properties database file.
Then use
```
rkhunter -c -sk  --rwo
``` and examine that output also.

References:
[https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps)

---

### Post by michal17 on 2015-04-07
```


Warning: The command '/sbin/ifdown' has been replaced by a script: /sbin/ifdown: Bourne-Again shell script text executable
Warning: The command '/sbin/ifup' has been replaced by a script: /sbin/ifup: Bourne-Again shell script text executable
Warning: The command '/usr/bin/GET' has been replaced by a script: /usr/bin/GET: a /usr/bin/perl -w script text executable
Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script text executable
Warning: The command '/usr/bin/whatis' has been replaced by a script: /usr/bin/whatis: POSIX shell script text executable
Warning: The following processes are using deleted files:
         Process: /sbin/init    PID: 1    File: /sbin/init
         Process: /usr/sbin/irqbalance    PID: 2690    File: /usr/sbin/irqbalance
         Process: /bin/bash    PID: 2993    File: /bin/bash
         Process: /usr/libexec/mysqld    PID: 3104    File: /tmp/ibD2mpNg
         Process: /usr/bin/perl    PID: 7881    File: /usr/bin/perl
         Process: /usr/bin/perl    PID: 7927    File: /usr/bin/perl
         Process: /usr/bin/perl    PID: 7928    File: /usr/bin/perl
         Process: /usr/sbin/httpd    PID: 10584    File: /etc/pki/nssdb/cert9.db
         Process: /usr/sbin/httpd    PID: 10585    File: /etc/pki/nssdb/cert9.db
         Process: /usr/sbin/httpd    PID: 10589    File: /etc/pki/nssdb/cert9.db
         Process: /usr/sbin/httpd    PID: 10590    File: /etc/pki/nssdb/cert9.db
         Process: /usr/sbin/sshd    PID: 14428    File: /usr/sbin/sshd
         Process: /bin/bash    PID: 14434    File: /bin/bash
         Process: /usr/sbin/httpd    PID: 14612    File: /etc/pki/nssdb/cert9.db
         Process: /usr/sbin/httpd    PID: 14613    File: /etc/pki/nssdb/cert9.db
         Process: /usr/sbin/httpd    PID: 23642    File: /etc/pki/nssdb/cert9.db
Warning: File '/tmp/monitrc.chk' (score: 281) contains some suspicious content and should be checked.
Warning: Checking for files with suspicious contents [ Warning ]
Warning: Found enabled xinetd service: /etc/xinetd.d/ftp_psa
Warning: Found enabled xinetd service: /etc/xinetd.d/poppassd_psa
Warning: Found enabled xinetd service: /etc/xinetd.d/smtp_psa
Warning: Found enabled xinetd service: /etc/xinetd.d/smtps_psa
Warning: Found enabled xinetd service: /etc/xinetd.d/submission_psa
Warning: The modules file '/proc/modules' is missing.
Warning: The SSH configuration option 'PermitRootLogin' has not been set.
         The default value may be 'yes', to allow root access.
Warning: Suspicious file types found in /dev:
         /dev/md/autorebuild.pid: ASCII text
         /dev/md/md-device-map: ASCII text
         /dev/.udev/queue.bin: Non-ISO extended-ASCII text, with no line terminators
         /dev/.udev/db/block:md2: ASCII text
         /dev/.udev/db/block:md1: ASCII text
         /dev/.udev/db/net:eth0: ASCII text
         /dev/.udev/db/block:sda3: ASCII text
         /dev/.udev/db/block:sdb3: ASCII text
         /dev/.udev/db/block:sda4: ASCII text
         /dev/.udev/db/block:sdb4: ASCII text
         /dev/.udev/db/block:sda2: ASCII text
         /dev/.udev/db/block:sda1: ASCII text
         /dev/.udev/db/block:sda: ASCII text
         /dev/.udev/db/block:sdb2: ASCII text
         /dev/.udev/db/block:sdb1: ASCII text
         /dev/.udev/db/block:sdb: ASCII text
         /dev/.udev/db/block:ram3: ASCII text
         /dev/.udev/db/block:ram8: ASCII text
         /dev/.udev/db/block:loop6: ASCII text
         /dev/.udev/db/block:ram12: ASCII text
         /dev/.udev/db/block:loop7: ASCII text
         /dev/.udev/db/block:loop2: ASCII text
         /dev/.udev/db/block:ram0: ASCII text
         /dev/.udev/db/block:ram10: ASCII text
         /dev/.udev/db/block:ram5: ASCII text
         /dev/.udev/db/block:ram13: ASCII text
         /dev/.udev/db/block:ram7: ASCII text
         /dev/.udev/db/block:ram15: ASCII text
         /dev/.udev/db/block:loop3: ASCII text
         /dev/.udev/db/block:ram6: ASCII text
         /dev/.udev/db/block:ram9: ASCII text
         /dev/.udev/db/block:ram2: ASCII text
         /dev/.udev/db/block:ram1: ASCII text
         /dev/.udev/db/block:loop1: ASCII text
         /dev/.udev/db/block:ram4: ASCII text
         /dev/.udev/db/block:ram14: ASCII text
         /dev/.udev/db/block:loop5: ASCII text
         /dev/.udev/db/block:loop0: ASCII text
         /dev/.udev/db/block:loop4: ASCII text
         /dev/.udev/db/block:ram11: ASCII text
         /dev/.udev/db/block:md0: ASCII text
         /dev/.udev/db/misc:kvm: ASCII text
         /dev/.udev/db/usb:2-1: ASCII text
         /dev/.udev/db/usb:1-1: ASCII text
         /dev/.udev/db/block:nbd8: ASCII text
         /dev/.udev/db/block:nbd4: ASCII text
         /dev/.udev/db/block:nbd1: ASCII text
         /dev/.udev/db/usb:usb1: ASCII text
         /dev/.udev/db/block:nbd10: ASCII text
         /dev/.udev/db/block:nbd15: ASCII text
         /dev/.udev/db/block:nbd2: ASCII text
         /dev/.udev/db/usb:usb2: ASCII text
         /dev/.udev/db/block:nbd9: ASCII text
         /dev/.udev/db/block:nbd7: ASCII text
         /dev/.udev/db/block:nbd5: ASCII text
         /dev/.udev/db/block:nbd6: ASCII text
         /dev/.udev/db/block:nbd14: ASCII text
         /dev/.udev/db/block:nbd3: ASCII text
         /dev/.udev/db/block:nbd13: ASCII text
         /dev/.udev/db/block:nbd12: ASCII text
         /dev/.udev/db/block:nbd11: ASCII text
         /dev/.udev/db/block:nbd0: ASCII text
         /dev/.udev/db/usb:usb4: ASCII text
         /dev/.udev/db/usb:usb3: ASCII text
Warning: Hidden directory found: /dev/.udev
Warning: Hidden file found: /usr/share/man/man5/.k5identity.5.gz: gzip compressed data, from Unix, max compression
Warning: Hidden file found: /usr/share/man/man5/.k5login.5.gz: gzip compressed data, from Unix, max compression
Warning: Hidden file found: /usr/share/man/man1/..1.gz: gzip compressed data, from Unix, max compression
Warning: Hidden file found: /usr/bin/.ssh.hmac: ASCII text
Warning: Hidden file found: /usr/bin/.fipscheck.hmac: ASCII text
Warning: Hidden file found: /usr/sbin/.sshd.hmac: ASCII text
Warning: Application 'httpd', version '2.2.15', is out of date, and possibly a security risk.



```

---

### Post by Habitual on 2015-04-07
> **michal17 said:**
> ```


Warning: The command '/sbin/ifdown' has been replaced by a script: /sbin/ifdown: Bourne-Again shell script text executable
Warning: The command '/sbin/ifup' has been replaced by a script: /sbin/ifup: Bourne-Again shell script text executable
Warning: The command '/usr/bin/GET' has been replaced by a script: /usr/bin/GET: a /usr/bin/perl -w script text executable
Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script text executable
Warning: The command '/usr/bin/whatis' has been replaced by a script: /usr/bin/whatis: POSIX shell script text executable
...
Warning: Application 'httpd', version '2.2.15', is out of date, and possibly a security risk.
```

OK. Does the /etc/rkhunter.conf file not explain the options I have given you?

```
ALLOWHIDDENDIR=/dev/.udev/db
SCRIPTWHITELIST=/sbin/ifdown    
SCRIPTWHITELIST=/sbin/ifup      
SCRIPTWHITELIST=/usr/bin/GET    
SCRIPTWHITELIST=/usr/bin/groups 
SCRIPTWHITELIST=/usr/bin/ldd    
SCRIPTWHITELIST=/usr/bin/whatis'
...
APP_WHITELIST="httpd"

```
The rest I leave to you as an exercise.

---

### Post by michal17 on 2015-04-13
sorry, my skills are limited to a minimum. Never never done this before, I execute the following commands?
```
[COLOR=#000000][FONT=Ubuntu Mono]ALLOWHIDDENDIR=/dev/.udev/db[/FONT][/COLOR]SCRIPTWHITELIST=/sbin/ifdown    
SCRIPTWHITELIST=/sbin/ifup      
SCRIPTWHITELIST=/usr/bin/GET    
SCRIPTWHITELIST=/usr/bin/groups 
SCRIPTWHITELIST=/usr/bin/ldd    
SCRIPTWHITELIST=/usr/bin/whatis'
... [COLOR=#000000][FONT=Ubuntu Mono]APP_WHITELIST="httpd"[/FONT][/COLOR]
```

I prefer to ask 3 times before I destroy something.

---

### Post by Habitual on 2015-04-14
> **michal17 said:**
> sorry, my skills are limited to a minimum. Never never done this before, I execute the following commands?
```
[COLOR=#000000][FONT=Ubuntu Mono]ALLOWHIDDENDIR=/dev/.udev/db
[/FONT][/COLOR]SCRIPTWHITELIST=/sbin/ifdown    
SCRIPTWHITELIST=/sbin/ifup      
SCRIPTWHITELIST=/usr/bin/GET    
SCRIPTWHITELIST=/usr/bin/groups 
SCRIPTWHITELIST=/usr/bin/ldd    
SCRIPTWHITELIST=/usr/bin/whatis'
... [COLOR=#000000][FONT=Ubuntu Mono]APP_WHITELIST="httpd"[/FONT][/COLOR]
```

I prefer to ask 3 times before I destroy something.
```
cp /etc/rkhunter.conf /etc/rkhunter.conf.original
``` before editing.
After edits, check the edits with 
```
rkhunter --check-config
```

I think
> **michal17 said:**
> sorry, my skills are limited to a minimum.  Never never done this before, I execute the following commands?
```
[COLOR=#000000][FONT=Ubuntu Mono]ALLOWHIDDENDIR=/dev/.udev/db[/FONT][/COLOR]SCRIPTWHITELIST=/sbin/ifdown
...
``` was a clipboard error.

---

