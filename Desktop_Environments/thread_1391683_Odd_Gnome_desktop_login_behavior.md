---
title: "Odd Gnome desktop login behavior"
date: 2010-01-27
forum: Desktop Environments
---

### Post by houseworkshy on 2010-01-27
I don't know what is causeing this.  When I boot or reboot I'm taken to the command line at which I have to give my name and password to login to the desktop. Then I have to give my name and password again, with a sudo ( it doesn't work otherwise ) to run the gdm command.  Only then do I get to what would normally happen immediately; the Gnome login screen, where the name and passord go in for the third time.
 
This has happened before and then went away, now it has happened again.  This time the previous program I'd used was wine running a spiderweb demo.  The last occasion was preceeded by wine too.

The first time was with the stable wine from the repositories.  So I  replaced it with the beta wine, which was also from the repositories.

On both occasions I've  had to turn my router off for a while, as when I got to the desktop enviroment I was offline and that was the only thing which seemed to get me back online again.

Does anyone know what what may be causing this and how to fix it please?

---

### Post by warfacegod on 2010-01-27
At a guess, I'd say Wine.


Try disabling it in Startup Applications.

---

### Post by houseworkshy on 2010-01-29
I think that it is wine too.  On taking it off the system the problem has not reccured.  When I have time to spare I'll give it another go and do as you suggest, thanks.

---

### Post by warfacegod on 2010-01-29
Sure. Post back if you have any issues. You should probably mark this as solved though.

---

### Post by houseworkshy on 2010-01-30
Well it seems probable that wine is the cause so by not using it the problem does not recur.  I will mark it as solved when I see a way of using wine and not having the problem.  I've been digging around in the processes trying to work out which one is responsible.  Doesn't look good so far as I don't think wine should inherit the right to change privileges from the time it is installed but that seems to be what is going on.  Most disturbing was on one occasion when it actually changed passwords and forced me to reinstall.  Fortunately I hadn't encrypted my home so using another system on another drive was able to rescue my work.  I'm still looking into that one, fortunately Alt+F2 still works even during a wine crash so lets me get in and try to work out how it does it. It could be that I installed a windows program within 15 minuets ( assuming initial defaults ) of using sudo to install wine but I still don't know.  If it is that then the safe procedure would be to wait at least fifteen minuets after installing wine before putting anything on it.  I've just tried that and put on the same windows program and have not go the problem so far.  Bit out of my depth really.  It's not good though.

---

### Post by warfacegod on 2010-01-30
You don't need to reinstall because of fragged passwords. You can change them with the recovery shell. How exactly are you installing Wine?

---

### Post by houseworkshy on 2010-01-31
I've used synaptic with the standard repositories having enabled the ones which are present but not checked on a fresh install.  I have also added the mediabuntu repositories but nothing else.  It is not such a big deal for me as I can live without wine.  Previously I've only used it for celesta because I didn't like the way add ons, which could be written by anyone, needed to be put outside the home folder with gksu gedits.  I know that malware does exist for Linux, though it generally depends on tricking the user into upping it's privileges, so I'd thought it was safer to bung them on wines virtual c:\ drive instead.  Using a windows version rather than a Linux one because it was *safer* amused me at the time.  It could be that I was wrong about that.  I should add that celesta running on wine did not cause any problems of which I was aware.

---

### Post by warfacegod on 2010-01-31
Celesta is pretty hardware intensive. I've got a P4 2.8 Ghz Hyper Thread and 2 GB RAM and with anything else open, Celesta will bring my laptop to its knees. I imagine under Wine it would be much worse. Anyway, I just wanted to make sure you didn't get it from some shady site telling you to install it by sudoing this and that. Is login still misbehaving? If so, assuming you have a wired internet connection:

```
sudo apt-get purge gdm

sudo apt-get install gdm
```

Do this outside of Ubuntu. Go to a Recovery kernel and drop to shell.

---

### Post by houseworkshy on 2010-01-31
Celestia was happy in wine but this is a duel core with four gig ddr2 ram and I ran the 32 bit version.  GDM is ok now too.  I'm suspecting that there is some bug or vulnerability associated with wine.  As it is something which seems to involve escalated privileges I regard it as a serious one. The fix is simply "don't use wine".  However, I'm having a bit of a dig into it partly for curiosity and party as a learning process.  As my work is on another drive and backed up on CD as long as the problem doesn't actually kill the pc I'm safe to play around.  It's actually rather more fun investigating this than playing the game.  Will have to get on with other things soon so can't throw too much more time at it.

Well I've found out some more.  The game demo which I'm using to test it is Avernum 5 from here [http://www.spiderwebsoftware.com/products.html](http://www.spiderwebsoftware.com/products.html).  I've just discovered another problem.  The game plays in full screen mode, so far I haven't found a way to play it in a window, I think it is one of those which capture the keyboard and mouse.  So far, whilst Alt + F2 works when it actually crashes, I haven't found a wine key which over rides what is running in it, as one has in DosBox.  I posted on the wine section of this forum about this but so far have not had a reply which works.  This makes diagnosis tricky.  Anyway the other problem is that if one leaves the machine alone until the power saving kicks in it gets stuck.  One can not move the mouse or hit a key to bring the display back so one is forced to reboot via the power button.  Again there is an obvious fix for that but it's not right.  Are these are connected perhaps?

I haven't been able to reproduce the password bug as the game which did it was an old one which a friend brought round for me to look at and the CD isn't here any more.  I won't mention which one it was as if, in combination with wine, it can hijack root then I don't think that sort thing should be posted on a public forum; from the point of view of malware writing vandals it would amount to a tip.  This is the fresh install after that incident so the other bugs may not be related to it.

The first bug I mentioned as been reproduced twice now, I think it happens when one puts something in wine soon after installing it.  I tried installing wine a third time.  This time, perhaps by chance (?), I couldn't download winbind at which the bugs didn't assert themselves either, though wine ran ok.   Previous to each try along with uninstalling wine I also deleted the .wine from the home directory but did not remove the links.

Another thing which may be relevant.  I ran tiger, from the repositories.  It is a security diagnostic which I don't really understand but the report looked dreadful. I'll do a proper reinstall when I've finished messing around.  Many of the programs mentioned as not matching the checksums shouldn't even be there as this is a fresh install, or are they simply references to my software sources lists?  Oh I hadn't enabled and set up a firewall, thinking lets just see what it does, so that part isn't strange.  Forgive this but it is HUGE.  Too Huge to post it seems so I'll see if I can put it in the next one.

---

### Post by houseworkshy on 2010-01-31
That didn't work either as I got this;  "Fatal error: Maximum execution time of 60 seconds exceeded in /srv/www.ubuntuforums.org/public_html/includes/functions.php on line 1838"  I'll see if I can do it in a differant format.

---

### Post by houseworkshy on 2010-01-31
Part one

Security scripts *** 3.2.2, 2007.08.28.00.00 ***

Sun Jan 31 12:26:23 GMT 2010

12:26> Beginning security report for desktop (x86_64 Linux 2.6.28-17-generic).



# Performing check of passwd files...

# Checking entries from /etc/passwd.

--WARN-- [pass014w] Login (backup) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (bin) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (daemon) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (games) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (gnats) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (myusername) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (irc) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (libuuid) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (list) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (lp) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (mail) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (man) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (news) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (nobody) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (proxy) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (root) is disabled, but has a valid shell. 

--WARN-- [pass015w] Login ID sync does not have a valid shell (/bin/sync). 

--WARN-- [pass014w] Login (sys) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (uucp) is disabled, but has a valid shell. 

--WARN-- [pass014w] Login (www-data) is disabled, but has a valid shell. 

--WARN-- [pass006w] Integrity of password files questionable (/usr/sbin/pwck 

         -r). 



# Performing check of group files...



# Performing check of user accounts...

# Checking accounts from /etc/passwd.

--WARN-- [acc021w] Login ID avahi-autoipd appears to be a dormant account. 

--WARN-- [acc006w] Login ID gdm's home directory (/var/lib/gdm) has group 

         `gdm' write access. 

--WARN-- [acc021w] Login ID libuuid appears to be a dormant account. 

--WARN-- [acc022w] Login ID nobody home directory (/nonexistent) is not 

         accessible. 

--WARN-- [acc006w] Login ID polkituser's home directory (/var/run/PolicyKit) 

         has group `polkituser' write access. 



# Performing check of /etc/hosts.equiv and .rhosts files...



# Checking accounts from /etc/passwd...



# Performing check of .netrc files...



# Checking accounts from /etc/passwd...



# Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab...

--WARN-- [root003w] Root user has message capability turned on.

---

### Post by houseworkshy on 2010-01-31
Part 2


# Performing check of PATH components...

--WARN-- [path009w] /etc/profile does not export an initial setting for PATH. 

# Only checking user 'root'



# Performing check of anonymous FTP...



# Performing checks of mail aliases...

# Checking aliases from /etc/aliases.



# Performing check of `cron' entries...

--WARN-- [cron004w] Root crontab does not exist 

--WARN-- [cron005w] Use of cron is not restricted 



# Performing check of 'inetd'...

# Checking inetd entries from /etc/inetd.conf



# Performing check of services with tcp wrappers...

# Analysing inetd entries from /etc/inetd.conf



# Performing check of 'services' ...

# Checking services from /etc/services.

--WARN-- [inet003w] The port for service sieve is also assigned to service 

         cisco-sccp. 

--WARN-- [inet003w] The port for service ndtp is also assigned to service 

         pipe_server. 

--WARN-- [inet003w] The port for service ndtp is also assigned to service 

         search. 

--WARN-- [inet003w] The port for service postgres is also assigned to service 

         postgresql. 

--WARN-- [inet003w] The port for service postgres is also assigned to service 

         postgresql. 

--WARN-- [inet003w] The port for service sane is also assigned to service 

         sane-port. 

--WARN-- [inet003w] The port for service webcache is also assigned to service 

         http-alt. 

--WARN-- [inet003w] The port for service webcache is also assigned to service 

         http-alt. 



# Performing NFS exports check...



# Performing check of system file permissions...



# Checking for known intrusion signs...

# Testing for promiscuous interfaces with /bin/ip

# Testing for backdoors in inetd.conf



# Performing check of files in system mail spool...



# Performing check for rookits...

# Running chkrootkit (/usr/sbin/chkrootkit) to perform further checks...



# Performing system specific checks...

# Performing checks for Linux/2...



# Checking boot loader file permissions...

--WARN-- [boot02] The configuration file /boot/grub/menu.lst has group 

         permissions. Should be 0600 

--FAIL-- [boot02] The configuration file /boot/grub/menu.lst has world 

         permissions. Should be 0600 

--WARN-- [boot06] The Grub bootloader does not have a password configured. 



# Checking for vulnerabilities in inittab configuration...



# Checking for correct umask settings for init scripts...

--WARN-- [misc021w] There are no umask entries in /etc/init.d/rcS 



# Checking Logins not used on the system ...



# Checking network configuration

--WARN-- [lin012w] The system accepts ICMP redirection messages 

--FAIL-- [lin016f] The system permits source routing from incoming packets 

--WARN-- [lin017w] The system is not configured to log suspicious (martian) 

         packets 

--FAIL-- [lin019f] The system does not have any local firewall rules 

         configured 



# Verifying system specific password checks...



# Checking OS release...

---

### Post by houseworkshy on 2010-01-31
A truncated part 3

# Checking installed packages vs Debian Security Advisories...



# Checking md5sums of installed files

--FAIL-- [lin005f] Installed file 

         `/usr/share/app-install/desktop/abiword.desktop' checksum differs 

         from installed package 'app-install-data'.
 

The above fail is repeated for every package on the sytem and probably every package in my software list.  There are pages and pages of it.  Then

# Checking installed files against packages...

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.ofmap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.inputmap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.dep' does not 

         belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.ieee1394map' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.seriomap' does 

         not belong to any package. 

--WARN-- [lin001w] File 

         `/lib/modules/2.6.28-17-generic/volatile/wlan_xauth.ko' does not 

         belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/wlan_wep.ko' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/wlan_tkip.ko' 

         does not belong to any package. 

--WARN-- [lin001w] File 

         `/lib/modules/2.6.28-17-generic/volatile/wlan_scan_sta.ko' does not 

         belong to any package. 

--WARN-- [lin001w] File 

         `/lib/modules/2.6.28-17-generic/volatile/wlan_scan_ap.ko' does not 

         belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/wlan_ccmp.ko' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/wlan_acl.ko' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/wlan.ko' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/wl.ko' does 

         not belong to any package. 

--WARN-- [lin001w] File 

         `/lib/modules/2.6.28-17-generic/volatile/ath_rate_sample.ko' does not 

         belong to any package. 

--WARN-- [lin001w] File 

         `/lib/modules/2.6.28-17-generic/volatile/ath_rate_onoe.ko' does not 

         belong to any package. 

--WARN-- [lin001w] File 

         `/lib/modules/2.6.28-17-generic/volatile/ath_rate_minstrel.ko' does 

         not belong to any package. 

--WARN-- [lin001w] File 

         `/lib/modules/2.6.28-17-generic/volatile/ath_rate_amrr.ko' does not 

         belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/ath_pci.ko' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/ath_hal.ko' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/volatile/.mounted' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.symbols.bin' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.alias.bin' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.ccwmap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.isapnpmap' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.pcimap' does 

         not belong to any package. 

--WARN-- [lin001w] File 

         `/lib/modules/2.6.28-17-generic/updates/dkms/nvidia.ko' does not 

         belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.usbmap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.dep.bin' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.alias' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-17-generic/modules.symbols' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.ofmap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.inputmap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.dep' does not 

         belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.ieee1394map' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.seriomap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.symbols.bin' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.alias.bin' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.ccwmap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.isapnpmap' 

         does not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.pcimap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.usbmap' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.dep.bin' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.alias' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/modules/2.6.28-11-generic/modules.symbols' does 

         not belong to any package. 

--WARN-- [lin001w] File `/lib/init/rw/.ramfs' does not belong to any package.

---

### Post by houseworkshy on 2010-01-31
And finally

 Performing check of root directory...



# Checking device permissions...

--WARN-- [dev003w] The directory /dev/block resides in a device directory. 

--WARN-- [dev003w] The directory /dev/char resides in a device directory. 

--FAIL-- [dev002f] /dev/fuse has world permissions 

--FAIL-- [dev002f] /dev/log has world permissions 

--FAIL-- [dev002f] /dev/nvidia0 has world permissions 

--FAIL-- [dev002f] /dev/nvidiactl has world permissions 

--WARN-- [dev003w] The directory /dev/pktcdvd resides in a device directory. 

--WARN-- [dev003w] File /dev/sndstat is a regular file in a device directory. 



# Checking for existence of log files...

--FAIL-- [logf005f] Log file /var/log/btmp permission should be 660 



# Checking for correct umask settings...



# Checking listening processes 

--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 48224 

         (UDP on every interface) is run by avahi. 

--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 5353 (UDP 

         on every interface) is run by avahi. 

--WARN-- [lin002i] The process `dhclient' is listening on socket 68 (UDP) on 

         every interface. 



# Checking sshd_config configuration files...

--FAIL-- [ssh005w] Cannot find a configuration file for SSH. 



# Performing common access checks for root...

--FAIL-- [netw020f] There is no /etc/ftpusers file. 



# Checking ntpd configuration...



# Checking unusual file names...



# Looking for unusual device files...

--ALERT-- [fsys006a] Unexpected device files found: 

crw------- 1 root root 5, 1 Jan 28 11:16 /lib/udev/devices/console

crw-r----- 1 root kmem 1, 2 Jan 28 11:16 /lib/udev/devices/kmem

brw------- 1 root root 7, 0 Jan 28 11:16 /lib/udev/devices/loop0

crw------- 1 root root 10, 200 Jan 28 11:16 /lib/udev/devices/net/tun

crw------- 1 root root 1, 3 Jan 28 11:16 /lib/udev/devices/null

crw------- 1 root root 108, 0 Jan 28 11:16 /lib/udev/devices/ppp

lrwxrwxrwx 1 root root 15 Jan 28 11:16 /lib/udev/devices/stderr -> /proc/self/fd/2





# Checking symbolic links...



# Performing check of embedded pathnames...

12:34> Security report completed for desktop.

---

### Post by houseworkshy on 2010-01-31
Sorry about the size of all that lot, I don't know what is or isn't valid.  Other than changing my user name to "myusername" and missing out duplicate checksum FAILS for everything it is verbatum.

---

### Post by warfacegod on 2010-01-31
What do you expect me to do with *that?*:shock:  [-o<?

---

### Post by warfacegod on 2010-01-31
I just installed tiger on my laptop, I'll get back to you when it's done running. By the way, how looonggg did that take to run?

---

### Post by houseworkshy on 2010-01-31
I made what is left of my mind bubble.  But am I correct in thinking that all is not well.

---

### Post by houseworkshy on 2010-01-31
It ran quite quickly actually, minuets.  To read the report I had to gksu gedit then copied a file onto my desktop so I could play with it and not have a root editor open whilst I was online.  Not that it made much differance now I guess.

---

### Post by warfacegod on 2010-01-31
I don't want to say something and have it be wrong but if I were you, I'd go with my gut. Just from very briefly scanning through that...whatever that is, *my* gut is feeling funny. If my laptop had that, there would be klaxxons going off in my head. I would post a link to this over in the Security forum to see what those guys say.

---

### Post by houseworkshy on 2010-01-31
I agree.  I'm about to ditch the whole op and reinstall ( the same op, love ubuntu ).  It looks like wine may be a potential security problem to me.  As it happens if I have been ripped off all they will have got is some badly writen short stories but if I did banking online ......hummm.  Did your tiger report look ok?  Probably worth knowing if tiger has known issues before hassling the security chaps and maybe casting doubt on wine which may have nothing to do with it.

---

### Post by warfacegod on 2010-01-31
> **houseworkshy said:**
> I agree.  I'm about to ditch the whole op and reinstall ( the same op, love ubuntu ).  It looks like wine may be a potential security problem to me.  As it happens if I have been ripped off all they will have got is some badly writen short stories but if I did banking online ......hummm.  Did your tiger report look ok?  Probably worth knowing if tiger has known issues before hassling the security chaps and maybe casting doubt on wine which may have nothing to do with it.

tiger got stuck. No such file or directory initramsomething. So I killed it. I write poetry and lyrics, of a ridiculously insane nature to be sure.

---

### Post by houseworkshy on 2010-01-31
Cool another writer :)  I do poetry/lyrics as well as prose, though my genius has not yet been recognised.  Well I'll post a link in the security forums and see what they make of it.  I'll also bung on the post I first wrote when the "mystery game" did the password thing without saying what the game was, for the reasons mentioned above, to be complete.  I should probably have done that first.  I can't remember half of what I did when that problem was fresh in my mind.

---

### Post by warfacegod on 2010-01-31
> **houseworkshy said:**
> Cool another writer :)  I do poetry/lyrics as well as prose, though my genius has not yet been recognised.  Well I'll post a link in the security forums and see what they make of it.  I'll also bung on the post I first wrote when the "mystery game" did the password thing without saying what the game was, for the reasons mentioned above, to be complete.  I should probably have done that first.  I can't remember half of what I did when that problem was fresh in my mind.

I recognize my own genius all the time.

---

### Post by houseworkshy on 2010-01-31
I've called the game wingame as if it is a security risk I don't want to post its' name on a public forum.  This is what I wrote when it was fresh in my mind, but didn't post, after the first password changing error. It hadn't occured to me to simply not to mention the name of game.  I was a bit fazed at the time.

"First off this is not a complete report as I'm not that knowledgeable, especially with the 9.10 version of Ubuntu , and I didn't realise the problem until it was too late.  It is highly probable I just did something idiotic.  Also I'm a little peeved and in the mood for a rant, feel free to skip to the last paragraph which is where the kicker is.  Didn't want to post at all really but thought I'd better.  Bearing that in mind here goes.

I'd had some problems with 9.10 but have persevered and via several false starts and reinstalls can now make it all work except for a bit of stalling in video and making libdvd css persist through reboots.  The latter two problems I can live with and are for some other thread, it's not what this one is about.  Yesterday I'd reinstalled, updated, and put in a few of the the extras I like.  I'll mention them in case it matters;  nvidia driver, restricted extras, the rest of open office, scribus, inkscape, gimp gap, kdenlive, audacity, clamtk, firestarter, kompozer, python 3.1 with appropriate IDLE.  I'd also put some add ons into firefox; add to search bar, downthemall, noscript and Ghostery.  The later may be significant as clamAV said that it was a virus.  That was as far as I'd got, bar a few snippets from the internet archive to test my codecs and a couple of manuals which I like to have in  my documents and all had worked, including through reboots.  I hadn't quite finished when a friend called round.

He's a windows games enthusiast and off line, just as well perhaps because he is on the now unsupported XP.  I often let him browse the net to find out how to fix his system again, and download sysinternal type freeware, patches and mods for his games add ilk and then burn them to a disc for when he gets home.  I've also given him 8.04lts with an aptoncd disc ( we have identical hardware ) and lots of debs but I doubt he'll ever use them, so no need for that old discussion again.

Well this time he was very keen for me to see a wingame so I could compare it to a lingame which I'd shown him some time ago.  I resisted, as I like to have open source only software, bar the obvious drivers and extras.  I certainly didn't want the thing, as a writer I respect intellectual property.  Even if I didn't what's the point of stripping naked to wash in the town square fountain and upsetting people when you've got a perfectly good bathroom at home with soap and hot water.  In the end, reasoning that he had paid for and owned the thing so it was hardly piracy and probably, to be honest, because I liked the prospect of saying &#8220;and hey look you can still run most of those old windows games you've got on Linux.&#8221;  I relented.  

So I put in wine, the stable version, unplugged the internet in case it tried to tie the game to my machine.  I remember ms don't always ask about feedback.  As he isn't on line and so hasn't been able register it himself, it might muck things up for him when he finally gets his own connection.  It may even mean that one of us would have to buy another copy, not me as we'd both say, if he wanted to use it on line.  This would be a bit much as he's mad on the thing and I doubt I'd ever play it, too steep a learning curve for an occasional gamer such as myself.  That's not intended as a criticism btw it's just that if I'm going to invest that much time in learning something I'd rather it was an application, such as blender which is next on my recreational list after python.  Different people use pc's for different things, that's all. 
 
I opened the setup.exe with wine for him and let him get on with it.  I could have made a mistake there as it was an old version, and perhaps I should have set wine to be running as 2000 or even 98 instead of leaving the default xp.  Everything else was default too, just as it is when freshly installed from the repro's.  I don't remember the game version, it may even have been the first.  The disk is legitimate and from a reputable retailer, it was an expensive one at the time it came out, which is when he got it.  It ran but insisted on full screen mode.  I've never liked or trusted programs which prevent you from getting at anything else while they run.  The graphics looked a bit old school to me in its default of 800x600  I think, it may even have been the one below that, so we put them up to 1050x1680 at which my fussy lcd monitor complained, which was odd as it was the converse of what I'd expect.  So we put them back and my monitor decided that it didn't like the original resolution either any more.   Once the monitors grumble box vanished we took off and crashed.  Then the program crashed too.  Can't pretend I was that impressed.  The loading bar was nice though; it used a picture instead of being plain.

This is where it gets odd.  I couldn't get out of wine.  Fortunately Alt+F2 worked.  I used it to open the system monitor but couldn't end the process.  On using Alt+F2, the screen went back to low res maximised and I got the graphics of Ubuntu's tool bars back but couldn't use them.   I had a look at the files and it seemed to be doing a lot of piping etc/dev was one of them which is understandable, but there was far too much else, which I can't remember now,  going on.  Didn't like the look of that at all so tried to kill the process, nope.  So then I opened a terminal and &#8220;sudo shutdown -r now&#8221; and thanks for all the fish.  

Now comes what I regard as serious and why felt I had to post.  The game/wine combination had changed my password.  I tried half a dozen times and am sure I made no typing errors and caps lock was just as it should be.  No go.  The only sudo's used in the episode was one when installing wine and the final one to reboot.  I hadn't used the pass phrase option when  I'd set up but as I hadn't got any work on the drive yet anyway it didn't matter so I just reinstalled 9.10 again.  I'm sorry that I don't have more information but I didn't expect to have to do a diagnostic.  I still have a dusty pile of old windows games CD's and floppy's, just in case I feel nostalgic, but don't want to replicate the circumstances nor do I have the time.  I've used wine before to run celestia so I can put extra maps and textures on its virtual c drive rather than use sudo to paste them elsewhere and also to play the spiderweb demos and it has never given me trouble before.  That said I don't think it was in 9.10.   Perhaps someone with the necessary bits and knowledge may like to dig further and find out if it was some passing cosmic wave or whether wine can mess with permissions and change the Ubuntu system password."

---

### Post by houseworkshy on 2010-01-31
> **warfacegod said:**
> I recognize my own genius all the time.

We all do when we are actually writing.  Then we usually hate it and regret all the people we showed it to when it was fresh and then, a few months later when its' cold can actually see whether it was any good or not.
I'll just pop over to the other forum section now and point at this.

---

### Post by warfacegod on 2010-01-31
> **houseworkshy said:**
> We all do when we are actually writing.  Then we usually hate it and regret all the people we showed it to when it was fresh and then, a few months later when its' cold can actually see whether it was any good or not.
I'll just pop over to the other forum section now and point at this.

My genius does not fade with time. Apparently, neither does my ego.

---

### Post by houseworkshy on 2010-01-31
Not a bad thing, without ego one would just give up.  I've posted the link so other than maybe pming an expert with the name of the game that's it.  I'll reinstall after this.  First I suppose I'd better add the sysinfo in case it helps.
System information report, generated by Sysinfo: 01/02/2010 04:24:05
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
	Running Ubuntu Linux, the 5.0 release.
	GNOME: 2.26.1 (Ubuntu 2009-05-06)
	Kernel version: 2.6.28-17-generic (#58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009)
	GCC: 4.3.3 (x86_64-linux-gnu)
	Xorg: unknown (09 April 2009  02:11:54AM)
	Hostname: desktop
	Uptime: 0 days 3 h 28 min

CPU INFORMATION
	AuthenticAMD, AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
	Number of CPUs: 2
	CPU clock currently at 2210.255 MHz with 512 KB cache
	Numbering: family(15) model(75) stepping(2)
	Bogomips: 4420.51
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy

MEMORY INFORMATION
	Total memory: 1860 MB
	Total swap: 5443 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  ATA      
		Model:  ST3250820AS      
	SCSI device -  scsi1
		Vendor:  TSSTcorp 
		Model:  CDDVDW SH-S223B  
	SCSI device -  scsi2
		Vendor:  ATA      
		Model:  ST3250820AS      

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	PCI bridge(s)
		nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
		nVidia Corporation MCP61 PCI Express bridge (rev a2)
		nVidia Corporation MCP61 PCI Express bridge (rev a2)
		nVidia Corporation MCP61 PCI Express bridge (rev a2)
	USB controller(s)
		nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 10)
		nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 20)
	ISA bridge
		nVidia Corporation MCP61 LPC Bridge (rev a2)
		Subsystem: ASUSTeK Computer Inc. Device 8234
	IDE interface
		nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
		Subsystem: ASUSTeK Computer Inc. Device 8234

GRAPHIC CARD
	VGA controller
		nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
		Subsystem: ASUSTeK Computer Inc. Device 8234

SOUND CARD
	Multimedia controller
		nVidia Corporation MCP61 High Definition Audio (rev a2)
		Subsystem: ASUSTeK Computer Inc. Device 8234

NETWORK

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce 6150SE nForce 430
	Card Type: PCI 
	Video RAM: 512 MB
	GPU Frequency: 425 MHz
	Driver version: NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009

On the first two occasions I was using 9.10, after that 9.04.

Well that's that.  Reinstallation time.  Thanks for your help and good luck with the writing.

---

