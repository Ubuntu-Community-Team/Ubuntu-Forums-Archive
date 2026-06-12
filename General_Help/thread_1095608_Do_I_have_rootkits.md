---
title: "Do I have rootkits?"
date: 2009-03-13
forum: General Help
---

### Post by linuxisevolution on 2009-03-13
I installed rkhunter and this is the output, thanks!:
**(just pay attention to the *warning* messages that I bolded*)**
```


Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
  **  Checking for prerequisites                               [ Warning ]**

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    **ADM Worm                                                 [ Warning ]**
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
   ** Phalanx Rootkit (strings)                                [ Warning ]**
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    **Checking for possible rootkit strings                    [ Warning ]**

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing Linux specific checks
  [B]  Checking kernel module commands                          [ Warning ]
    Checking kernel module names                             [ Warning ][/B]

[Press <ENTER> to continue]


Checking the network...

  Performing check for backdoor ports
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
**    Checking for local startup files                         [ Warning ]**
    Checking local startup files for malware                 [ Skipped ]
 **   Checking system startup files for malware                [ Warning ]**

  Performing group and account checks
**    Checking for passwd file                                 [ Warning ]**
    Checking for root equivalent (UID 0) accounts            [ Skipped ]
**    Checking for passwordless accounts                       [ Warning ]**
    Checking for passwd file changes                         [ Skipped ]
    Checking for group file changes                          [ Skipped ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
**    Checking for syslog configuration file                   [ Warning ]**

  Performing filesystem checks
**    Checking /dev for suspicious file types                  [ Warning ]**
    Checking for hidden files and directories                [ None found ]


```

---

### Post by lovinglinux on 2009-03-13
I'm not an expert on rkhunter, but I guess you have some rootkits and other bad stuff going on. My rkhunter log does not show any of these warnings, except for the last one, which is kind of normal.

---

### Post by lykwydchykyn on 2009-03-13
Is that all the output there is?  When I've gotten warnings from rkhunter, it usually explains the warnings at the end of the output.

---

### Post by hansdown on 2009-03-13
Hi linuxisevolution.

Have you updated your rkhunter recently?

---

### Post by doas777 on 2009-03-13
also be sure to check the log. the output tells you "warning" but usually the log will tell you what it is warning you about.

the last paragraph of the output should show you where the log is stored (should be /var/log/rkhunter.log)

---

### Post by Shazaam on 2009-03-13
First update rkhunter...
```
sudo rkhunter --update
```
Run it then go to /var/log/rkhunter.log for a full read.
```
gksudo gedit /var/log/rkhunter.log
```

---

### Post by linuxisevolution on 2009-03-14
I have updated it after the install.

It only takes about a minutes to quickly fly through the not found or warnings. Please help:

```

[22:44:29] Running Rootkit Hunter version 1.3.0 on winrid-desktop
[22:44:29]
[22:44:29] Info: Start date is Fri Mar 13 22:44:29 EDT 2009
[22:44:29]
[22:44:29] Checking configuration file and command-line options...
[22:44:29] Info: Detected operating system is 'Linux'
[22:44:29] Info: Found O/S name: Ubuntu 8.04.2
[22:44:29] Info: Command line is /usr/bin/rkhunter -r /home/winrid --check
[22:44:29] Info: Environment shell is /bin/bash; rkhunter is using dash
[22:44:29] Info: Using configuration file '/etc/rkhunter.conf'
[22:44:29] Info: Installation directory is '/usr'
[22:44:29] Info: Using language 'en'
[22:44:29] Info: Using '/var/lib/rkhunter/db' as the database directory
[22:44:29] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[22:44:29] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[22:44:29] Info: Using '/home/winrid' as the root directory
[22:44:29] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[22:44:29] Info: No mail-on-warning address configured
[22:44:29] Info: X will automatically be detected
[22:44:29] Info: Using second color set
[22:44:29] Info: Found the 'diff' command: /usr/bin/diff
[22:44:29] Info: Found the 'file' command: /usr/bin/file
[22:44:29] Info: Found the 'find' command: /usr/bin/find
[22:44:29] Info: Found the 'ifconfig' command: /sbin/ifconfig
[22:44:30] Info: Found the 'ip' command: /sbin/ip
[22:44:30] Info: Found the 'ldd' command: /usr/bin/ldd
[22:44:30] Info: Found the 'lsattr' command: /usr/bin/lsattr
[22:44:30] Info: Found the 'lsmod' command: /sbin/lsmod
[22:44:30] Info: Found the 'lsof' command: /usr/bin/lsof
[22:44:30] Info: Found the 'mktemp' command: /bin/mktemp
[22:44:30] Info: Found the 'netstat' command: /bin/netstat
[22:44:30] Info: Found the 'perl' command: /usr/bin/perl
[22:44:30] Info: Found the 'ps' command: /bin/ps
[22:44:30] Info: Found the 'pwd' command: /bin/pwd
[22:44:30] Info: Found the 'readlink' command: /bin/readlink
[22:44:30] Info: Found the 'sort' command: /usr/bin/sort
[22:44:30] Info: Found the 'stat' command: /usr/bin/stat
[22:44:30] Info: Found the 'strings' command: /usr/bin/strings
[22:44:30] Info: Found the 'uniq' command: /usr/bin/uniq
[22:44:30] Info: System is not using prelinking
[22:44:30] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[22:44:30] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[22:44:30] Info: Stored hash values did not use a package manager
[22:44:30] Info: The hash function field index is set to 1
[22:44:30] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[22:44:30] Info: Previous file attributes were stored
[22:44:30] Info: Enabled tests are: all
[22:44:30] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[22:44:30] Info: All ksyms and kallsyms checks will be skipped - neither file is present on the system.
[22:44:30]
[22:44:30] Checking if the O/S has changed since last time...
[22:44:30] Warning: The O/S name or version has changed since the last run:
[22:44:30]          Old O/S value: Ubuntu 8.04.2    New value: 
[22:44:30]          Because of the change(s) the file properties checks may give some false-positive results.
[22:44:30]          You may need to re-run rkhunter with the '--propupd' option.
[22:44:30]
[22:44:30] Warning: WARNING! It is the users responsibility to ensure that when the '--propupd' option
           is used, all the files on their system are known to be genuine, and installed from a
           reliable source. The rkhunter '--check' option will compare the current file properties
           against previously stored values, and report if any values differ. However, rkhunter
           cannot determine what has caused the change, that is for the user to do.
[22:44:30]
[22:44:30] Starting system checks...
[22:44:30]
[22:44:30] Checking system commands...
[22:44:30] Info: Starting test name 'system_commands'
[22:44:30]
[22:44:30] Performing 'strings' command checks
[22:44:30] Info: Starting test name 'strings'
[22:44:30] Scanning for string /usr/sbin/ntpsx               [ OK ]
[22:44:30] Scanning for string /usr/lib/.../ls               [ OK ]
[22:44:30] Scanning for string /usr/lib/.../netstat          [ OK ]
[22:44:30] Scanning for string /usr/lib/.../lsof             [ OK ]
[22:44:30] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[22:44:30] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[22:44:30] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[22:44:30] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[22:44:30] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[22:44:30] Scanning for string /usr/lib/.../psr              [ OK ]
[22:44:30] Scanning for string /usr/lib/.../find             [ OK ]
[22:44:30] Scanning for string /usr/lib/.../pstree           [ OK ]
[22:44:30] Scanning for string /usr/lib/.../slocate          [ OK ]
[22:44:30] Scanning for string /usr/lib/.../du               [ OK ]
[22:44:30] Scanning for string /usr/lib/.../top              [ OK ]
[22:44:30] Scanning for string /usr/lib/...                  [ OK ]
[22:44:30] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[22:44:30] Scanning for string /usr/lib/.bkit-               [ OK ]
[22:44:30] Scanning for string /tmp/.bkp                     [ OK ]
[22:44:30] Scanning for string /tmp/.cinik                   [ OK ]
[22:44:30] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[22:44:30] Scanning for string /lib/.sso                     [ OK ]
[22:44:30] Scanning for string /lib/.so                      [ OK ]
[22:44:30] Scanning for string /var/run/...dica/clean        [ OK ]
[22:44:30] Scanning for string /var/run/...dica/xl           [ OK ]
[22:44:30] Scanning for string /var/run/...dica/xdr          [ OK ]
[22:44:30] Scanning for string /var/run/...dica/psg          [ OK ]
[22:44:30] Scanning for string /var/run/...dica/secure       [ OK ]
[22:44:30] Scanning for string /var/run/...dica/rdx          [ OK ]
[22:44:30] Scanning for string /var/run/...dica/va           [ OK ]
[22:44:30] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[22:44:30] Scanning for string /usr/bin/.etc                 [ OK ]
[22:44:30] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[22:44:30] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[22:44:30] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[22:44:30] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[22:44:31] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[22:44:31] Scanning for string /bin/sysback                  [ OK ]
[22:44:31] Scanning for string /usr/local/bin/sysback        [ OK ]
[22:44:31] Scanning for string /usr/lib/.tbd                 [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[22:44:31] Scanning for string /usr/info/.torn/sh*           [ OK ]
[22:44:31] Scanning for string /usr/src/.****/.1addr         [ OK ]
[22:44:31] Scanning for string /usr/src/.****/.1file         [ OK ]
[22:44:31] Scanning for string /usr/src/.****/.1proc         [ OK ]
[22:44:31] Scanning for string /usr/src/.****/.1logz         [ OK ]
[22:44:31] Scanning for string /usr/info/.t0rn               [ OK ]
[22:44:31] Scanning for string /dev/.lib                     [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib                 [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib             [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[22:44:31] Scanning for string /dev/.lib/lib/scan            [ OK ]
[22:44:31] Scanning for string /usr/src/.****                [ OK ]
[22:44:31] Scanning for string /usr/man/man1/man1            [ OK ]
[22:44:31] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[22:44:31] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[22:44:31] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[22:44:31]
[22:44:31] Performing 'shared libraries' checks
[22:44:31] Info: Starting test name 'shared_libs'
[22:44:31] Checking for preloading variables                 [ None found ]
[22:44:31] Checking for preload file                         [ Not found ]
[22:44:31] Info: Starting test name 'shared_libs_path'
[22:44:31] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[22:44:31]
[22:44:31] Performing file properties checks
[22:44:31] Info: Starting test name 'properties'
[22:44:31] Warning: Checking for prerequisites               [ Warning ]
[22:44:31]          The local host configuration or operating system has changed.
[22:44:33]
[22:44:33] Checking for rootkits...
[22:44:33] Info: Starting test name 'rootkits'
[22:44:33]
[22:44:33] Performing check of known rootkit files and directories
[22:44:33] Info: Starting test name 'known_rkts'
[22:44:33]
[22:44:33] Checking for 55808 Trojan - Variant A...
[22:44:33]   Checking for file '/home/winrid/tmp/.../r'      [ Not found ]
[22:44:34]   Checking for file '/home/winrid/tmp/.../a'      [ Not found ]
[22:44:34] 55808 Trojan - Variant A                          [ Not found ]
[22:44:34]
[22:44:34] Checking for ADM Worm...
[22:44:34] Warning: ADM Worm                                 [ Warning ]
[22:44:34]          The file '/home/winrid/etc/passwd' does not exist!
[22:44:34]
[22:44:34] Checking for AjaKit Rootkit...
[22:44:34]   Checking for file '/home/winrid/dev/tux/.addr'  [ Not found ]
[22:44:34]   Checking for file '/home/winrid/dev/tux/.proc'  [ Not found ]
[22:44:34]   Checking for file '/home/winrid/dev/tux/.file'  [ Not found ]
[22:44:34]   Checking for file '/home/winrid/lib/.libgh-gh/cleaner' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/lib/.libgh-gh/Patch/patch' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/lib/.libgh-gh/sb0k' [ Not found ]
[22:44:34]   Checking for directory '/home/winrid/dev/tux'   [ Not found ]
[22:44:34]   Checking for directory '/home/winrid/lib/.libgh-gh' [ Not found ]
[22:44:34] AjaKit Rootkit                                    [ Not found ]
[22:44:34]
[22:44:34] Checking for aPa Kit...
[22:44:34]   Checking for file '/home/winrid/usr/share/.aPa' [ Not found ]
[22:44:34] aPa Kit                                           [ Not found ]
[22:44:34]
[22:44:34] Checking for Apache Worm...
[22:44:34]   Checking for file '/home/winrid/bin/.log'       [ Not found ]
[22:44:34] Apache Worm                                       [ Not found ]
[22:44:34]
[22:44:34] Checking for Ambient (ark) Rootkit...
[22:44:34]   Checking for file '/home/winrid/usr/lib/.ark?'  [ Not found ]
[22:44:34]   Checking for file '/home/winrid/dev/ptyxx/.log' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/dev/ptyxx/.file' [ Not found ]
[22:44:34]   Checking for directory '/home/winrid/dev/ptyxx' [ Not found ]
[22:44:34] Ambient (ark) Rootkit                             [ Not found ]
[22:44:34]
[22:44:34] Checking for Balaur Rootkit...
[22:44:34]   Checking for file '/home/winrid/usr/lib/liblog.o' [ Not found ]
[22:44:34]   Checking for directory '/home/winrid/usr/lib/.kinetic' [ Not found ]
[22:44:34]   Checking for directory '/home/winrid/usr/lib/.egcs' [ Not found ]
[22:44:34]   Checking for directory '/home/winrid/usr/lib/.wormie' [ Not found ]
[22:44:34] Balaur Rootkit                                    [ Not found ]
[22:44:34]
[22:44:34] Checking for BeastKit Rootkit...
[22:44:34]   Checking for file '/home/winrid/usr/sbin/arobia' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/sbin/idrun' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/elm/arobia/elm' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/elm/arobia/elm/hk' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/elm/arobia/elm/sc' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[22:44:34]   Checking for directory '/home/winrid/lib/ldd.so/bktools' [ Not found ]
[22:44:34] BeastKit Rootkit                                  [ Not found ]
[22:44:34]
[22:44:34] Checking for beX2 Rootkit...
[22:44:34]   Checking for directory '/home/winrid/usr/include/bex' [ Not found ]
[22:44:34] beX2 Rootkit                                      [ Not found ]
[22:44:34]
[22:44:34] Checking for BOBKit Rootkit...
[22:44:34]   Checking for file '/home/winrid/usr/sbin/ntpsx' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/.../ls' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/.../netstat' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/.../lsof' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[22:44:34]   Checking for file '/home/winrid/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/.../uconf.inv' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/.../psr' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/.../find' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/.../pstree' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/.../slocate' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/.../du' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/.../top' [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/usr/lib/...' [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/usr/lib/.../bkit-ssh' [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/usr/lib/.bkit-' [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/tmp/.bkp'  [ Not found ]
[22:44:35] BOBKit Rootkit                                    [ Not found ]
[22:44:35]
[22:44:35] Checking for CiNIK Worm (Slapper.B variant)...
[22:44:35]   Checking for file '/home/winrid/tmp/.cinik'     [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/tmp/.font-unix/.cinik' [ Not found ]
[22:44:35] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[22:44:35]
[22:44:35] Checking for Danny-Boy's Abuse Kit...
[22:44:35]   Checking for file '/home/winrid/dev/mdev'       [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/libX.a' [ Not found ]
[22:44:35] Danny-Boy's Abuse Kit                             [ Not found ]
[22:44:35]
[22:44:35] Checking for Devil RootKit...
[22:44:35]   Checking for file '/home/winrid/var/lib/games/.src' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/dev/dsx'        [ Not found ]
[22:44:35]   Checking for file '/home/winrid/dev/caca'       [ Not found ]
[22:44:35] Devil RootKit                                     [ Not found ]
[22:44:35]
[22:44:35] Checking for Dica-Kit Rootkit...
[22:44:35]   Checking for file '/home/winrid/lib/.sso'       [ Not found ]
[22:44:35]   Checking for file '/home/winrid/lib/.so'        [ Not found ]
[22:44:35]   Checking for file '/home/winrid/var/run/...dica/clean' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/var/run/...dica/xl' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/var/run/...dica/xdr' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/var/run/...dica/psg' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/var/run/...dica/secure' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/var/run/...dica/rdx' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/var/run/...dica/va' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/var/run/...dica/cl.sh' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/bin/.etc'   [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/var/run/...dica' [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/var/run/...dica/mh' [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/var/run/...dica/scan' [ Not found ]
[22:44:35] Dica-Kit Rootkit                                  [ Not found ]
[22:44:35]
[22:44:35] Checking for Dreams Rootkit...
[22:44:35]   Checking for file '/home/winrid/dev/ttyoa'      [ Not found ]
[22:44:35]   Checking for file '/home/winrid/dev/ttyof'      [ Not found ]
[22:44:35]   Checking for file '/home/winrid/dev/ttyop'      [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/bin/sense'  [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/bin/sl2'    [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/bin/logclear' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/bin/(swapd)' [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/bin/snfs'   [ Not found ]
[22:44:35]   Checking for file '/home/winrid/usr/lib/libsss' [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/dev/ida/.hpd' [ Not found ]
[22:44:35] Dreams Rootkit                                    [ Not found ]
[22:44:35]
[22:44:35] Checking for Duarawkz Rootkit...
[22:44:35]   Checking for file '/home/winrid/usr/bin/duarawkz/loginpass' [ Not found ]
[22:44:35]   Checking for directory '/home/winrid/usr/bin/duarawkz' [ Not found ]
[22:44:36] Duarawkz Rootkit                                  [ Not found ]
[22:44:36]
[22:44:36] Checking for Enye LKM...
[22:44:36]   Checking for file '/home/winrid/etc/.enyelkmHIDE^IT.ko' [ Not found ]
[22:44:36] Enye LKM                                          [ Not found ]
[22:44:36]
[22:44:36] Checking for Flea Linux Rootkit...
[22:44:36]   Checking for file '/home/winrid/etc/ld.so.hash' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/bin/ssh2d'  [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/lib/ldlibns.so' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/lib/ldlibpst.so' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/lib/ldlibdu.so' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/lib/ldlibct.so' [ Not found ]
[22:44:36]   Checking for directory '/home/winrid/lib/security/.config/ssh' [ Not found ]
[22:44:36]   Checking for directory '/home/winrid/dev/..0'   [ Not found ]
[22:44:36]   Checking for directory '/home/winrid/dev/..0/backup' [ Not found ]
[22:44:36] Flea Linux Rootkit                                [ Not found ]
[22:44:36]
[22:44:36] Checking for FreeBSD Rootkit...
[22:44:36]   Checking for file '/home/winrid/usr/lib/.fx/sched_host.2' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/lib/.fx/random_d.2' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/lib/.fx/set_pid.2' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/lib/.fx/cons.saver' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/bin/sysback'    [ Not found ]
[22:44:36]   Checking for file '/home/winrid/usr/local/bin/sysback' [ Not found ]
[22:44:36]   Checking for directory '/home/winrid/usr/lib/.fx' [ Not found ]
[22:44:36]   Checking for directory '/home/winrid/usr/lib/.fx/adore' [ Not found ]
[22:44:36] FreeBSD Rootkit                                   [ Not found ]
[22:44:36]
[22:44:36] Checking for ****`it Rootkit...
[22:44:36]   Checking for file '/home/winrid/dev/proc/fuckit/hax0r' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/dev/proc/fuckit/hax0rshell' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/dev/proc/fuckit/config/lports' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/dev/proc/fuckit/config/rports' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/dev/proc/fuckit/config/rkconf' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/dev/proc/fuckit/config/password' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/dev/proc/fuckit/config/progs' [ Not found ]
[22:44:36]   Checking for file '/home/winrid/dev/proc/system-bins/init' [ Not found ]
[22:44:36] ****`it Rootkit                                   [ Not found ]
[22:44:36]
[22:44:36] Checking for GasKit Rootkit...
[22:44:36]   Checking for file '/home/winrid/dev/dev/gaskit/sshd/sshdd' [ Not found ]
[22:44:36]   Checking for directory '/home/winrid/dev/dev'   [ Not found ]
[22:44:36]   Checking for directory '/home/winrid/dev/dev/gaskit' [ Not found ]
[22:44:36]   Checking for directory '/home/winrid/dev/dev/gaskit/sshd' [ Not found ]
[22:44:36] GasKit Rootkit                                    [ Not found ]
[22:44:36]
[22:44:36] Checking for Heroin LKM...
[22:44:36]   Checking for kernel symbol 'heroin'             [ Skipped ]
[22:44:36] Heroin LKM                                        [ Not found ]
[22:44:36]
[22:44:36] Checking for HjC Kit...
[22:44:36]   Checking for directory '/home/winrid/dev/.hijackerz' [ Not found ]
[22:44:36] HjC Kit                                           [ Not found ]
[22:44:36]
[22:44:36] Checking for ignoKit Rootkit...
[22:44:36]   Checking for file '/home/winrid/lib/defs/p'     [ Not found ]
[22:44:36]   Checking for file '/home/winrid/lib/defs/q'     [ Not found ]
[22:44:36]   Checking for file '/home/winrid/lib/defs/r'     [ Not found ]
[22:44:36]   Checking for file '/home/winrid/lib/defs/s'     [ Not found ]
[22:44:37]   Checking for file '/home/winrid/lib/defs/t'     [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/defs/p' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/defs/q' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/defs/r' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/defs/s' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/defs/t' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/.libigno/pkunsec' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[22:44:37]   Checking for directory '/home/winrid/usr/lib/.libigno' [ Not found ]
[22:44:37]   Checking for directory '/home/winrid/usr/lib/.libigno/.igno' [ Not found ]
[22:44:37] ignoKit Rootkit                                   [ Not found ]
[22:44:37]
[22:44:37] Checking for ImperalsS-FBRK Rootkit...
[22:44:37]   Checking for directory '/home/winrid/dev/fd/.88' [ Not found ]
[22:44:37]   Checking for directory '/home/winrid/dev/fd/.99' [ Not found ]
[22:44:37] ImperalsS-FBRK Rootkit                            [ Not found ]
[22:44:37]
[22:44:37] Checking for Irix Rootkit...
[22:44:37]   Checking for directory '/home/winrid/dev/pts/01' [ Not found ]
[22:44:37]   Checking for directory '/home/winrid/dev/pts/01/backup' [ Not found ]
[22:44:37]   Checking for directory '/home/winrid/dev/pts/01/etc' [ Not found ]
[22:44:37]   Checking for directory '/home/winrid/dev/pts/01/tmp' [ Not found ]
[22:44:37] Irix Rootkit                                      [ Not found ]
[22:44:37]
[22:44:37] Checking for Kitko Rootkit...
[22:44:37]   Checking for directory '/home/winrid/usr/src/redhat/SRPMS/...' [ Not found ]
[22:44:37] Kitko Rootkit                                     [ Not found ]
[22:44:37]
[22:44:37] Checking for Knark Rootkit...
[22:44:37]   Checking for file '/home/winrid/proc/knark/pids' [ Not found ]
[22:44:37]   Checking for directory '/home/winrid/proc/knark' [ Not found ]
[22:44:37] Knark Rootkit                                     [ Not found ]
[22:44:37]
[22:44:37] Checking for Li0n Worm...
[22:44:37]   Checking for file '/home/winrid/bin/in.telnetd' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/bin/mjy'        [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/1i0n.sh' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/hack.sh' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/bind' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/randb' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/scan.sh' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/pscan' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/star.sh' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/scan/bindname.log' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/1i0n.sh' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/lib/netstat' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[22:44:37] Li0n Worm                                         [ Not found ]
[22:44:37]
[22:44:37] Checking for Lockit / LJK2 Rootkit...
[22:44:37]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[22:44:37]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[22:44:38]   Checking for directory '/home/winrid/usr/lib/libmen.oo/.LJK2' [ Not found ]
[22:44:38] Lockit / LJK2 Rootkit                             [ Not found ]
[22:44:38]
[22:44:38] Checking for Mood-NT Rootkit...
[22:44:38]   Checking for file '/home/winrid/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/_cthulhu/mood-nt.init' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/_cthulhu/mood-nt.conf' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/_cthulhu/mood-nt.sniff' [ Not found ]
[22:44:38]   Checking for directory '/home/winrid/_cthulhu'  [ Not found ]
[22:44:38] Mood-NT Rootkit                                   [ Not found ]
[22:44:38]
[22:44:38] Checking for MRK Rootkit...
[22:44:38]   Checking for file '/home/winrid/dev/ida/.inet/pid' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/dev/ida/.inet/ssh_host_key' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/dev/ida/.inet/ssh_random_seed' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/dev/ida/.inet/tcp.log' [ Not found ]
[22:44:38]   Checking for directory '/home/winrid/dev/ida/.inet' [ Not found ]
[22:44:38]   Checking for directory '/home/winrid/var/spool/cron/.sh' [ Not found ]
[22:44:38] MRK Rootkit                                       [ Not found ]
[22:44:38]
[22:44:38] Checking for Ni0 Rootkit...
[22:44:38]   Checking for file '/home/winrid/var/lock/subsys/...datafile.../...net...' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/var/lock/subsys/...datafile.../...port...' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[22:44:38]   Checking for file '/home/winrid/var/lock/subsys/...datafile.../...file...' [ Not found ]
[22:44:38]   Checking for directory '/home/winrid/tmp/waza'  [ Not found ]
[22:44:38]   Checking for directory '/home/winrid/var/lock/subsys/...datafile...' [ Not found ]
[22:44:38]   Checking for directory '/home/winrid/usr/sbin/es' [ Not found ]
[22:44:38] Ni0 Rootkit                                       [ Not found ]
[22:44:38]
[22:44:38] Checking for Ohhara Rootkit...
[22:44:38]   Checking for file '/home/winrid/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[22:44:38]   Checking for directory '/home/winrid/var/lock/subsys/...datafile...' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[22:44:39] Ohhara Rootkit                                    [ Not found ]
[22:44:39]
[22:44:39] Checking for Optic Kit (Tux) Worm...
[22:44:39]   Checking for directory '/home/winrid/dev/tux'   [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/usr/bin/xchk' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/usr/bin/xsf' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/usr/bin/ssh2d' [ Not found ]
[22:44:39] Optic Kit (Tux) Worm                              [ Not found ]
[22:44:39]
[22:44:39] Checking for Oz Rootkit...
[22:44:39]   Checking for file '/home/winrid/dev/.oz/.nap/rkit/terror' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/dev/.oz'   [ Not found ]
[22:44:39] Oz Rootkit                                        [ Not found ]
[22:44:39]
[22:44:39] Checking for Phalanx Rootkit...
[22:44:39]   Checking for file '/home/winrid/usr/share/.home.ph1/cb' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/etc/host.ph1'   [ Not found ]
[22:44:39]   Checking for file '/home/winrid/bin/host.ph1'   [ Not found ]
[22:44:39]   Checking for file '/home/winrid/usr/share/.home.ph1/phalanx' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/usr/share/.home.ph1' [ Not found ]
[22:44:39] Phalanx Rootkit                                   [ Not found ]
[22:44:39]
[22:44:39] Checking for Phalanx Rootkit (strings)...
[22:44:39] Warning: Phalanx Rootkit (strings)                [ Warning ]
[22:44:39]          The file '/home/winrid/bin/hostname' does not exist!
[22:44:39]
[22:44:39] Checking for Portacelo Rootkit...
[22:44:39]   Checking for file '/home/winrid/var/lib/.../.ak' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../.hk' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../.rs' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../.p' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../getty' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../lkt.o' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../show' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../nlkt.o' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../ssshrc' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../sssh_equiv' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../sssh_known_hosts' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/var/lib/.../sssh_pid' [ Not found ]
[22:44:39]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[22:44:39] Portacelo Rootkit                                 [ Not found ]
[22:44:39]
[22:44:39] Checking for R3dstorm Toolkit...
[22:44:39]   Checking for file '/home/winrid/var/log/tk02/see_all' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/bin/.../sshd/sbin/sshd1' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/bin/.../hate/sk' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/bin/.../see_all' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/var/log/tk02' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/var/log/tk02/old' [ Not found ]
[22:44:39]   Checking for directory '/home/winrid/bin/...'   [ Not found ]
[22:44:39] R3dstorm Toolkit                                  [ Not found ]
[22:44:39]
[22:44:39] Checking for RH-Sharpe's Rootkit...
[22:44:39]   Checking for file '/home/winrid/bin/lps'        [ Not found ]
[22:44:39]   Checking for file '/home/winrid/usr/bin/lpstree' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/usr/bin/ltop'   [ Not found ]
[22:44:39]   Checking for file '/home/winrid/usr/bin/lkillall' [ Not found ]
[22:44:39]   Checking for file '/home/winrid/usr/bin/ldu'    [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/lnetstat' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/wp'     [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/shad'   [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/vadim'  [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/slice'  [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/cleaner' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/include/rpcsvc/du' [ Not found ]
[22:44:40] RH-Sharpe's Rootkit                               [ Not found ]
[22:44:40]
[22:44:40] Checking for RSHA's Rootkit...
[22:44:40]   Checking for file '/home/winrid/bin/kr4p'       [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/n3tstat' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/chsh2'  [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/bin/slice2' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[22:44:40]   Checking for directory '/home/winrid/etc/rc.d/rsha' [ Not found ]
[22:44:40]   Checking for directory '/home/winrid/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[22:44:40] RSHA's Rootkit                                    [ Not found ]
[22:44:40]
[22:44:40] Checking for Scalper Worm...
[22:44:40]   Checking for file '/home/winrid/tmp/.a'         [ Not found ]
[22:44:40]   Checking for file '/home/winrid/tmp/.uua'       [ Not found ]
[22:44:40] Scalper Worm                                      [ Not found ]
[22:44:40]
[22:44:40] Checking for Sebek LKM...
[22:44:40]   Checking for kernel symbol 'adore or sebek'     [ Skipped ]
[22:44:40] Sebek LKM                                         [ Not found ]
[22:44:40]
[22:44:40] Checking for Shutdown Rootkit...
[22:44:40]   Checking for file '/home/winrid/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/man/man5/.. /.dir/see' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/man/man5/.. /.dir/nscd' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/man/man5/.. /.dir/alpd' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/etc/rc.d/rc.local ' [ Not found ]
[22:44:40]   Checking for directory '/home/winrid/usr/man/man5/.. /.dir' [ Not found ]
[22:44:40]   Checking for directory '/home/winrid/usr/man/man5/.. /.dir/scannah' [ Not found ]
[22:44:40]   Checking for directory '/home/winrid/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[22:44:40] Shutdown Rootkit                                  [ Not found ]
[22:44:40]
[22:44:40] Checking for SHV4 Rootkit...
[22:44:40]   Checking for file '/home/winrid/etc/ld.so.hash' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/lib/libext-2.so.7' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/lib/lidps1.so'  [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/sbin/xntps' [ Not found ]
[22:44:40]   Checking for directory '/home/winrid/lib/security/.config' [ Not found ]
[22:44:40]   Checking for directory '/home/winrid/lib/security/.config/ssh' [ Not found ]
[22:44:40] SHV4 Rootkit                                      [ Not found ]
[22:44:40]
[22:44:40] Checking for SHV5 Rootkit...
[22:44:40]   Checking for file '/home/winrid/etc/sh.conf'    [ Not found ]
[22:44:40]   Checking for file '/home/winrid/dev/srd0'       [ Not found ]
[22:44:40]   Checking for directory '/home/winrid/usr/lib/libsh' [ Not found ]
[22:44:40] SHV5 Rootkit                                      [ Not found ]
[22:44:40]
[22:44:40] Checking for Sin Rootkit...
[22:44:40]   Checking for file '/home/winrid/dev/.haos/haos1/.f/Denyed' [ Not found ]
[22:44:40]   Checking for file '/home/winrid/dev/ttyoa'      [ Not found ]
[22:44:40]   Checking for file '/home/winrid/dev/ttyof'      [ Not found ]
[22:44:40]   Checking for file '/home/winrid/dev/ttyop'      [ Not found ]
[22:44:40]   Checking for file '/home/winrid/dev/ttyos'      [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/lib/.lib'   [ Not found ]
[22:44:40]   Checking for file '/home/winrid/usr/lib/sn/.X'  [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/lib/sn/.sys' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/lib/ld/.X'  [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/man/man1/...' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/man/man1/.../.m' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/man/man1/.../.w' [ Not found ]
[22:44:41]   Checking for directory '/home/winrid/usr/lib/sn' [ Not found ]
[22:44:41]   Checking for directory '/home/winrid/usr/lib/man1/...' [ Not found ]
[22:44:41]   Checking for directory '/home/winrid/dev/.haos' [ Not found ]
[22:44:41] Sin Rootkit                                       [ Not found ]
[22:44:41]
[22:44:41] Checking for Slapper Worm...
[22:44:41]   Checking for file '/home/winrid/tmp/.bugtraq'   [ Not found ]
[22:44:41]   Checking for file '/home/winrid/tmp/.uubugtraq' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/tmp/.bugtraq.c' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/tmp/httpd'      [ Not found ]
[22:44:41]   Checking for file '/home/winrid/tmp/.unlock'    [ Not found ]
[22:44:41]   Checking for file '/home/winrid/tmp/update'     [ Not found ]
[22:44:41]   Checking for file '/home/winrid/tmp/.cinik'     [ Not found ]
[22:44:41]   Checking for file '/home/winrid/tmp/.b'         [ Not found ]
[22:44:41] Slapper Worm                                      [ Not found ]
[22:44:41]
[22:44:41] Checking for Sneakin Rootkit...
[22:44:41]   Checking for directory '/home/winrid/tmp/.X11-unix/.../rk' [ Not found ]
[22:44:41] Sneakin Rootkit                                   [ Not found ]
[22:44:41]
[22:44:41] Checking for Suckit Rootkit...
[22:44:41]   Checking for file '/home/winrid/sbin/initsk12'  [ Not found ]
[22:44:41]   Checking for file '/home/winrid/sbin/initxrk'   [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/bin/null'   [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/share/locale/sk/.sk12/sk' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/etc/rc.d/rc0.d/S23kmdac' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/etc/rc.d/rc1.d/S23kmdac' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/etc/rc.d/rc2.d/S23kmdac' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/etc/rc.d/rc3.d/S23kmdac' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/etc/rc.d/rc4.d/S23kmdac' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/etc/rc.d/rc5.d/S23kmdac' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/etc/rc.d/rc6.d/S23kmdac' [ Not found ]
[22:44:41]   Checking for directory '/home/winrid/dev/sdhu0/tehdrakg' [ Not found ]
[22:44:41]   Checking for directory '/home/winrid/etc/.MG'   [ Not found ]
[22:44:41]   Checking for directory '/home/winrid/usr/share/locale/sk/.sk12' [ Not found ]
[22:44:41]   Checking for directory '/home/winrid/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[22:44:41] Suckit Rootkit                                    [ Not found ]
[22:44:41]
[22:44:41] Checking for SunOS Rootkit...
[22:44:41]   Checking for file '/home/winrid/etc/ld.so.hash' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/lib/libext-2.so.7' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/bin/ssh2d'  [ Not found ]
[22:44:41]   Checking for file '/home/winrid/bin/xlogin'     [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/lib/crth.o' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/lib/crtz.o' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/sbin/login'     [ Not found ]
[22:44:41]   Checking for file '/home/winrid/lib/security/.config/sn' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/lib/security/.config/lpsched' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/dev/kmod'       [ Not found ]
[22:44:41]   Checking for file '/home/winrid/dev/dos'        [ Not found ]
[22:44:41] SunOS Rootkit                                     [ Not found ]
[22:44:41]
[22:44:41] Checking for SunOS / NSDAP Rootkit...
[22:44:41]   Checking for file '/home/winrid/usr/lib/vold/nsdap/.kit' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/lib/vold/nsdap/defines' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/lib/vold/nsdap/patcher' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/lib/vold/nsdap/pg' [ Not found ]
[22:44:41]   Checking for file '/home/winrid/usr/lib/vold/nsdap/cleaner' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/lib/vold/nsdap/utime' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/lib/vold/nsdap/crypt' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/lib/vold/nsdap/findkit' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/lib/vold/nsdap/sn2' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/lib/vold/nsdap/sniffload' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/lib/vold/nsdap/runsniff' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/lib/lpset'  [ Not found ]
[22:44:42]   Checking for directory '/home/winrid/usr/lib/vold/nsdap' [ Not found ]
[22:44:42] SunOS / NSDAP Rootkit                             [ Not found ]
[22:44:42]
[22:44:42] Checking for Superkit Rootkit...
[22:44:42]   Checking for file '/home/winrid/usr/man/.sman/sk' [ Not found ]
[22:44:42] Superkit Rootkit                                  [ Not found ]
[22:44:42]
[22:44:42] Checking for TBD (Telnet BackDoor)...
[22:44:42]   Checking for file '/home/winrid/usr/lib/.tbd'   [ Not found ]
[22:44:42] TBD (Telnet BackDoor)                             [ Not found ]
[22:44:42]
[22:44:42] Checking for TeLeKiT Rootkit...
[22:44:42]   Checking for file '/home/winrid/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/man/man3/.../cl' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/ptyr'       [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/ptyp'       [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/ptyq'       [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/hda06'      [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/info/libc1.so' [ Not found ]
[22:44:42]   Checking for directory '/home/winrid/usr/man/man3/...' [ Not found ]
[22:44:42]   Checking for directory '/home/winrid/usr/man/man3/.../lsniff' [ Not found ]
[22:44:42]   Checking for directory '/home/winrid/usr/man/man3/.../TeLeKiT' [ Not found ]
[22:44:42] TeLeKiT Rootkit                                   [ Not found ]
[22:44:42]
[22:44:42] Checking for T0rn Rootkit...
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/t0rns' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/du' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/ls' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/t0rnsb' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/ps' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/t0rnp' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/find' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/ifconfig' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/pg' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/ssh.tgz' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/top' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/sz' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/login' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/1i0n.sh' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/pstree' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/mjy' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/sush' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/tfn' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/name' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/dev/.lib/lib/lib/getip.sh' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/info/.torn/sh*' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/src/.****/.1addr' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/src/.****/.1file' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/src/.****/.1proc' [ Not found ]
[22:44:42]   Checking for file '/home/winrid/usr/src/.****/.1logz' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/usr/info/.t0rn' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/dev/.lib'  [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/dev/.lib/lib' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/dev/.lib/lib/lib' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/dev/.lib/lib/lib/dev' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/dev/.lib/lib/scan' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/usr/src/.****' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/usr/man/man1/man1' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/usr/man/man1/man1/lib' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/usr/man/man1/man1/lib/.lib' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[22:44:43] T0rn Rootkit                                      [ Not found ]
[22:44:43]
[22:44:43] Checking for Trojanit Kit...
[22:44:43]   Checking for file '/home/winrid/bin/.ls'        [ Not found ]
[22:44:43]   Checking for file '/home/winrid/bin/.ps'        [ Not found ]
[22:44:43]   Checking for file '/home/winrid/bin/.netstat'   [ Not found ]
[22:44:43]   Checking for file '/home/winrid/usr/bin/.nop'   [ Not found ]
[22:44:43]   Checking for file '/home/winrid/usr/bin/.who'   [ Not found ]
[22:44:43] Trojanit Kit                                      [ Not found ]
[22:44:43]
[22:44:43] Checking for Tuxtendo Rootkit...
[22:44:43]   Checking for file '/home/winrid/dev/tux/.addr'  [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/.cron'  [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/.file'  [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/.log'   [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/.proc'  [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/crontab' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/df' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/dir' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/find' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/ifconfig' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/locate' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/netstat' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/ps' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/pstree' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/syslogd' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/tcpd' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/top' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/updatedb' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/dev/tux/backup/vdir' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/dev/tux'   [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/dev/tux/ssh2' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/dev/tux/backup' [ Not found ]
[22:44:43] Tuxtendo Rootkit                                  [ Not found ]
[22:44:43]
[22:44:43] Checking for URK Rootkit...
[22:44:43]   Checking for file '/home/winrid/usr/man/man1/xxxxxxbin/find' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/usr/man/man1/xxxxxxbin/du' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/usr/man/man1/xxxxxxbin/ps' [ Not found ]
[22:44:43]   Checking for file '/home/winrid/tmp/conf.inf'   [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/usr/man/man1/xxxxxxbin' [ Not found ]
[22:44:43] URK Rootkit                                       [ Not found ]
[22:44:43]
[22:44:43] Checking for VcKit Rootkit...
[22:44:43]   Checking for directory '/home/winrid/usr/include/linux/modules/lib.so' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/usr/include/linux/modules/lib.so/bin' [ Not found ]
[22:44:43] VcKit Rootkit                                     [ Not found ]
[22:44:43]
[22:44:43] Checking for Volc Rootkit...
[22:44:43]   Checking for directory '/home/winrid/var/spool/.recent' [ Not found ]
[22:44:43]   Checking for directory '/home/winrid/var/spool/.recent/.files' [ Not found ]
[22:44:44]   Checking for directory '/home/winrid/usr/lib/volc' [ Not found ]
[22:44:44]   Checking for directory '/home/winrid/usr/lib/volc/backup' [ Not found ]
[22:44:44] Volc Rootkit                                      [ Not found ]
[22:44:44]
[22:44:44] Checking for X-Org SunOS Rootkit...
[22:44:44]   Checking for file '/home/winrid/usr/lib/libX.a/bin/tmpfl' [ Not found ]
[22:44:44]   Checking for file '/home/winrid/usr/lib/libX.a/bin/rps' [ Not found ]
[22:44:44]   Checking for file '/home/winrid/usr/bin/srload' [ Not found ]
[22:44:44]   Checking for file '/home/winrid/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[22:44:44]   Checking for file '/home/winrid/usr/sbin/modcheck' [ Not found ]
[22:44:44]   Checking for directory '/home/winrid/usr/lib/libX.a' [ Not found ]
[22:44:44]   Checking for directory '/home/winrid/usr/lib/libX.a/bin' [ Not found ]
[22:44:44]   Checking for directory '/home/winrid/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[22:44:44]   Checking for directory '/home/winrid/usr/share/man...' [ Not found ]
[22:44:44] X-Org SunOS Rootkit                               [ Not found ]
[22:44:44]
[22:44:44] Checking for zaRwT.KiT Rootkit...
[22:44:44]   Checking for file '/home/winrid/dev/rd/s/sendmeil' [ Not found ]
[22:44:44]   Checking for file '/home/winrid/dev/ttyf'       [ Not found ]
[22:44:44]   Checking for file '/home/winrid/dev/ttyp'       [ Not found ]
[22:44:44]   Checking for file '/home/winrid/dev/ttyn'       [ Not found ]
[22:44:44]   Checking for file '/home/winrid/rk/tulz'        [ Not found ]
[22:44:44]   Checking for directory '/home/winrid/rk'        [ Not found ]
[22:44:44]   Checking for directory '/home/winrid/dev/rd/s'  [ Not found ]
[22:44:44] zaRwT.KiT Rootkit                                 [ Not found ]
[22:44:44]
[22:44:44] Performing additional rootkit checks
[22:44:44] Info: Starting test name 'additional_rkts'
[22:44:44]
[22:44:44]   Performing Suckit Rookit additional checks
[22:44:44]     Checking /sbin/init link count                [ OK ]
[22:44:44]     Checking for hidden file extensions           [ None found ]
[22:44:44]     Running skdet command                         [ Skipped ]
[22:44:44] Info: Unable to find the 'skdet' command
[22:44:44]   Suckit Rookit additional checks                 [ OK ]
[22:44:44]
[22:44:44]   Performing check of possible rootkit files and directories
[22:44:44] Info: Starting test name 'possible_rkt_files'
[22:44:44]     Checking for file '/home/winrid/dev/sdr0'     [ Not found ]
[22:44:44]     Checking for file '/home/winrid/tmp/.syshackfile' [ Not found ]
[22:44:44]     Checking for file '/home/winrid/tmp/.bash_history' [ Not found ]
[22:44:44]     Checking for file '/home/winrid/usr/info/.clib' [ Not found ]
[22:44:44]     Checking for file '/home/winrid/usr/sbin/tcp.log' [ Not found ]
[22:44:44]     Checking for file '/home/winrid/usr/bin/take/pid' [ Not found ]
[22:44:44]     Checking for file '/home/winrid/sbin/create'  [ Not found ]
[22:44:44]     Checking for file '/home/winrid/dev/ttypz'    [ Not found ]
[22:44:44]     Checking for directory '/home/winrid/usr/bin/take' [ Not found ]
[22:44:44]     Checking for directory '/home/winrid/usr/src/.lib' [ Not found ]
[22:44:44]     Checking for directory '/home/winrid/usr/share/man/man1/.1c' [ Not found ]
[22:44:44]     Checking for directory '/home/winrid/lib/lblip.tk' [ Not found ]
[22:44:44]     Checking for directory '/home/winrid/usr/sbin/...' [ Not found ]
[22:44:44]     Checking for directory '/home/winrid/usr/share/.gun' [ Not found ]
[22:44:44]   Checking for possible rootkit files and directories [ None found ]
[22:44:44]
[22:44:44]   Performing check for possible rootkit strings
[22:44:44] Info: Starting test name 'possible_rkt_strings'
[22:44:44] Warning: Checking for possible rootkit strings    [ Warning ]
[22:44:44]          No system startup files found.
[22:44:44]
[22:44:44] Performing malware checks
[22:44:45] Info: Starting test name 'malware'
[22:44:45]
[22:44:45] Info: Test 'deleted_files' disabled at users request.
[22:44:45] Info: Starting test name 'running_procs'
[22:44:45]   Checking running processes for suspicious files [ None found ]
[22:44:45]
[22:44:45] Info: Test 'hidden_procs' disabled at users request.
[22:44:45]
[22:44:45] Info: Test 'suspscan' disabled at users request.
[22:44:45]
[22:44:45]   Performing check for login backdoors
[22:44:45] Info: Starting test name 'other_malware'
[22:44:45]     Checking for '/home/winrid/bin/.login'        [ Not found ]
[22:44:45]     Checking for '/home/winrid/sbin/.login'       [ Not found ]
[22:44:45]   Checking for login backdoors                    [ None found ]
[22:44:45]
[22:44:45]   Performing check for suspicious directories
[22:44:45]     Checking for directory '/home/winrid/usr/X11R6/bin/.,/copy' [ Not found ]
[22:44:45]     Checking for directory '/home/winrid/dev/rd/cdb' [ Not found ]
[22:44:45]   Checking for suspicious directories             [ None found ]
[22:44:45]
[22:44:45]   Checking for software intrusions                [ Skipped ]
[22:44:45] Info: Check skipped - tripwire not installed
[22:44:45]
[22:44:45]   Performing check for sniffer log files
[22:44:45]     Checking for file '/home/winrid/usr/lib/libice.log' [ Not found ]
[22:44:45]   Checking for sniffer log files                  [ None found ]
[22:44:45]
[22:44:45] Performing trojan specific checks
[22:44:45] Info: Starting test name 'trojans'
[22:44:45]   Checking for enabled inetd services             [ Skipped ]
[22:44:45] Info: Check skipped - file '/home/winrid/etc/inetd.conf' does not exist.
[22:44:45]
[22:44:45]   Performing check for enabled xinetd services
[22:44:45]   Checking for enabled xinetd services            [ Skipped ]
[22:44:45] Info: Check skipped - file '/home/winrid/etc/xinetd.conf' does not exist.
[22:44:45] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[22:44:45]
[22:44:45] Performing Linux specific checks
[22:44:45] Info: Starting test name 'os_specific'
[22:44:45]   Checking kernel module commands                 [ Warning ]
[22:44:45] Warning: The modules file '/home/winrid/proc/modules' is missing.
[22:44:45] Info: Using modules pathname of '/home/winrid/lib/modules'
[22:44:45]   Checking kernel module names                    [ Warning ]
[22:44:45] Warning: The kernel module directory '/home/winrid/lib/modules' is missing.
[22:44:47]
[22:44:47] Checking the network...
[22:44:47] Info: Starting test name 'network'
[22:44:47] Info: Starting test name 'ports'
[22:44:47]
[22:44:47] Performing check for backdoor ports
[22:44:47]   Checking for UDP port 2001                      [ Not found ]
[22:44:48]   Checking for TCP port 2006                      [ Not found ]
[22:44:48]   Checking for TCP port 2128                      [ Not found ]
[22:44:48]   Checking for TCP port 14856                     [ Not found ]
[22:44:48]   Checking for TCP port 47107                     [ Not found ]
[22:44:48]   Checking for TCP port 60922                     [ Not found ]
[22:44:48]
[22:44:48] Performing checks on the network interfaces
[22:44:48] Info: Starting test name 'promisc'
[22:44:48]   Checking for promiscuous interfaces             [ None found ]
[22:44:48]
[22:44:48] Info: Test 'packet_cap_apps' disabled at users request.
[22:44:50]
[22:44:50] Checking the local host...
[22:44:50] Info: Starting test name 'local_host'
[22:44:50]
[22:44:50] Performing system boot checks
[22:44:50] Info: Starting test name 'startup_files'
[22:44:50]   Checking for local host name                    [ Found ]
[22:44:50] Info: Starting test name 'startup_malware'
[22:44:50]   Checking for local startup files                [ Warning ]
[22:44:50] Warning: No local startup files found.
[22:44:50]   Checking local startup files for malware        [ Skipped ]
[22:44:50] Warning: No local startup files found.
[22:44:50]   Checking system startup files for malware       [ Warning ]
[22:44:50] Warning: No system startup files found.
[22:44:50]
[22:44:50] Performing group and account checks
[22:44:50] Info: Starting test name 'group_accounts'
[22:44:50]   Checking for passwd file                        [ Warning ]
[22:44:50] Warning: Password file /home/winrid/etc/passwd does not exist.
[22:44:50]   Checking for root equivalent (UID 0) accounts   [ Skipped ]
[22:44:50] Warning: Password file /home/winrid/etc/passwd does not exist.
[22:44:50]   Checking for passwordless accounts              [ Warning ]
[22:44:50] Warning: No shadow/password file found.
[22:44:50] Info: Starting test name 'passwd_changes'
[22:44:50]   Checking for passwd file changes                [ Skipped ]
[22:44:50] Warning: Password file /home/winrid/etc/passwd does not exist.
[22:44:50] Info: Starting test name 'group_changes'
[22:44:50]   Checking for group file changes                 [ Skipped ]
[22:44:50] Warning: Group file /home/winrid/etc/group does not exist.
[22:44:50]   Checking root account shell history files       [ None found ]
[22:44:50]
[22:44:50] Performing system configuration file checks
[22:44:50] Info: Starting test name 'system_configs'
[22:44:50]   Checking for SSH configuration file             [ Not found ]
[22:44:50]   Checking for running syslog daemon              [ Found ]
[22:44:51]   Checking for syslog configuration file          [ Warning ]
[22:44:51] Warning: The syslog daemon is running, but no configuration file can be found.
[22:44:51]
[22:44:51] Performing filesystem checks
[22:44:51] Info: Starting test name 'filesystem'
[22:44:51]   Checking /dev for suspicious file types         [ Warning ]
[22:44:51] Warning: /dev does not exist.
[22:44:51]   Checking for hidden files and directories       [ None found ]
[22:46:10]
[22:46:10] Checking application versions...
[22:46:10] Info: Starting test name 'apps'
[22:46:10]   Checking version of Exim MTA                    [ OK ]
[22:46:10] Info: Application 'exim' version '4.69' found.
[22:46:10]   Checking version of GnuPG                       [ OK ]
[22:46:11] Info: Application 'gpg' version '1.4.6' found.
[22:46:11] Info: Application 'httpd' not found.
[22:46:11] Info: Application 'named' not found.
[22:46:11]   Checking version of OpenSSL                     [ OK ]
[22:46:11] Info: Application 'openssl' version '0.9.8g' found.
[22:46:11] Info: Application 'php' not found.
[22:46:11] Info: Application 'procmail' not found.
[22:46:11] Info: Application 'proftpd' not found.
[22:46:11]   Checking version of OpenSSH                     [ OK ]
[22:46:11] Info: Application 'sshd' version '4.7p1' found.
[22:46:11] Info: Applications checked: 4 out of 9
[22:46:11]
[22:46:11] System checks summary
[22:46:11] =====================
[22:46:11]
[22:46:11] File properties checks...
[22:46:11] Required commands check failed
[22:46:11] Files checked: 0
[22:46:11] Suspect files: 0
[22:46:11]
[22:46:11] Rootkit checks...
[22:46:11] Rootkits checked : 79
[22:46:11] Possible rootkits: 0
[22:46:11]
[22:46:11] Applications checks...
[22:46:11] Applications checked: 4
[22:46:11] Suspect applications: 0
[22:46:11]
[22:46:11] The system checks took: 1 minute and 41 seconds
[22:46:11]
[22:46:11] Info: End date is Fri Mar 13 22:46:11 EDT 2009


```

---

### Post by adult swim on 2009-03-14
i dont really know anything about rootkits, but the majortiy of your log that throws up errors is showing that rkhunter is looking in the wrong places for the files.  take this warning for example ```
Warning: The modules file '/home/winrid/proc/modules' is missing.

``` there shouldnt be a /home/winrid/proc/modules file, it is located at /proc/modules and the same goes for every other one that say warning or not found.
EDIT looking again at the log, it says ```
[22:44:29] Info: Using '/home/winrid' as the root directory

```  is there an option to change the root directory from /home/winrid to /

---

### Post by dcstar on 2009-03-14
> **linuxisevolution said:**
> I have updated it after the install.

It only takes about a minutes to quickly fly through the not found or warnings. Please help:

```

..........
[22:46:11] System checks summary
[22:46:11] =====================
[22:46:11]
[22:46:11] File properties checks...
[22:46:11] Required commands check failed
[22:46:11] Files checked: 0
[22:46:11] Suspect files: 0
[22:46:11]
[22:46:11] Rootkit checks...
[22:46:11] Rootkits checked : 79
[22:46:11] **Possible rootkits: 0**
[22:46:11]
[22:46:11] Applications checks...
[22:46:11] Applications checked: 4
[22:46:11] **Suspect applications: 0**
[22:46:11]
[22:46:11] The system checks took: 1 minute and 41 seconds
[22:46:11]
[22:46:11] Info: End date is Fri Mar 13 22:46:11 EDT 2009


```

Do you understand what that means?

---

### Post by heindsight on 2009-03-14
According to your log, you ran rkhunter as:
```
/usr/bin/rkhunter -r /home/winrid --check
```
That means that it tried to treat your home directory as the root of the filesystem. The warnings it gave were all related to not being able to find various files it was looking for, because those files don't (and shouldn't) exist under your home directory.

I believe the -r option of rkhunter is intended for use in situations such as when you are booting from a live CD and have your normal root partition mounted somewhere other than /

To get better results, you should run rkhunter as:
```
sudo rkhunter --check
```

---

### Post by doas777 on 2009-03-14
> **heindsight said:**
> According to your log, you ran rkhunter as:
```
/usr/bin/rkhunter -r /home/winrid --check
```
That means that it tried to treat your home directory as the root of the filesystem. The warnings it gave were all related to not being able to find various files it was looking for, because those files don't (and shouldn't) exist under your home directory.

I believe the -r option of rkhunter is intended for use in situations such as when you are booting from a live CD and have your normal root partition mounted somewhere other than /

To get better results, you should run rkhunter as:
```
sudo rkhunter --check
```

I concur, that appears to be much of the problem.

---

