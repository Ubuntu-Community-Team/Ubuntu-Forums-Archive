---
title: "lightdm doesn't start automatically"
date: 2013-03-31
forum: Desktop Environments
---

### Post by rameshg87 on 2013-03-31
Hi,

I know this problem has been discussed before in other threads, but none of them seems to solve my case.

The problem is lightdm doesn't start automatically, and it stops at the terminal.  Then I have to manually do a "sudo service lightdm start" to get it started automatically.

I referred this thread, but still the solution shows doesn't solve my case:
[http://ubuntuforums.org/showthread.php?t=2049203](http://ubuntuforums.org/showthread.php?t=2049203)

/var/log/boot.log
> 
 * Setting sensors limits       ^[[170G ^M^[[164G[ OK ]                         
 * Stopping System V initialisation compatibility^[[74G[ OK ]                   
Rather than invoking init scripts through /etc/init.d, use the service(8)       
utility, e.g. service S20lightdm start                                          
 * Starting KVM^[[74G[ OK ]                                                     
 * Starting System V runlevel compatibility^[[74G[ OK ]         


I tried the below:
> 
$ sudo sudo update-rc.d lightdm defaults
update-rc.d: warning: /etc/init.d/lightdm missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/lightdm already exist.
$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm
$


I tried dpkg-reconfigure of lightdm, uninstall-reinstall lightdm, still it doesn't solve my issue.  

Anyone has any suggestion.  Thanks.

---

### Post by steeldriver on 2013-03-31
You could look in /var/log/lightdm/lightdm.log and /var/log/lightdm/x-0-greeter.log as well, that's where messages about the actual lightdm startup would go I think

---

