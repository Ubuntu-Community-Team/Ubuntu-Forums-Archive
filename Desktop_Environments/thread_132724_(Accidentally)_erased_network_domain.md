---
title: "(Accidentally) erased network domain"
date: 2006-02-18
forum: Desktop Environments
---

### Post by patrick.ubuntu on 2006-02-18
Hi,
I've done something pretty stupid, but I hope it'll be forgivable given my total noob status.  I was trying to get my eth0 working at work.  Since the domain at work is not "ubuntu", I changed my computer's domain to the work name.  Now, not only can I still not get on the eth0 network, my wireless is not happening.  To complicate matters, when I try to get back into System-> Admin -> Network, the program stutters a bit trying to startup and then closes.  I'm not having any better luck by right clicking the nerwork icon on the taskbar.  Is there any way that I can fix this?  I've really gotten to like Ubuntu, and I'd hate to have to wipe and reinstall.  (This is a dual boot with Windows on a Dell Latitude D610 laptop if that's of any help).  Any help you could offer (and the more specific and step-by-step the better) would be greatly appreciated.
Cheers!

---

### Post by dcstar on 2006-02-18
[QUOTE=patrick.ubuntu]Hi,
I've done something pretty stupid, but I hope it'll be forgivable given my total noob status.  I was trying to get my eth0 working at work.  Since the domain at work is not "ubuntu", I changed my computer's domain to the work name.  Now, not only can I still not get on the eth0 network, my wireless is not happening.  To complicate matters, when I try to get back into System-> Admin -> Network, the program stutters a bit trying to startup and then closes.  I'm not having any better luck by right clicking the nerwork icon on the taskbar.  Is there any way that I can fix this?  I've really gotten to like Ubuntu, and I'd hate to have to wipe and reinstall.  (This is a dual boot with Windows on a Dell Latitude D610 laptop if that's of any help).  Any help you could offer (and the more specific and step-by-step the better) would be greatly appreciated.
Cheers![/QUOTE]
In a terminal:

sudo gedit /etc/hosts

and change the first line to:

127.0.0.1 localhost.localdomain localhost ubuntu

See if that fixes the problem.

---

### Post by patrick.ubuntu on 2006-02-19
Hi,
I appreciate your reply!  The solution you offered seems to be on the right track, but I'm still not able to implement it.  I opened /etc/hosts with gedit and saw where the ubuntu part of the line was indeed missing.  I tried using the terminal to change the file as root, but got the same old error (sudo: unable to lookup via gethostbyname() ).  I also tried the "run as a different user" to no effect at all (just closes).  I also tried the rescue mode command line, which netted the same error message.  I even tried to install some programs I don't need with Automatix just to get in as root to make the changes.  No luck.
Any ideas?
Many thanks in advance!
Cheers,
Patrick

---

### Post by dcstar on 2006-02-19
[QUOTE=patrick.ubuntu]Hi,
I appreciate your reply!  The solution you offered seems to be on the right track, but I'm still not able to implement it.  I opened /etc/hosts with gedit and saw where the ubuntu part of the line was indeed missing.  I tried using the terminal to change the file as root, but got the same old error (sudo: unable to lookup via gethostbyname() ).  I also tried the "run as a different user" to no effect at all (just closes).  I also tried the rescue mode command line, which netted the same error message.  I even tried to install some programs I don't need with Automatix just to get in as root to make the changes.  No luck.
Any ideas?
Many thanks in advance!
Cheers,
Patrick[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=98544e](http://ubuntuforums.org/showthread.php?t=98544e)

---

### Post by patrick.ubuntu on 2006-02-19
Hi,
Thank you for your help in this!
It seems I must not be understanding something though.  I need to change my hostname by logging in as root.  But to log into root on anything, I need the hostname to be right.  The "sudo broken?" thread certainly seems to confirm this.  I can open with gedit /etc/hosts using various techniques, but it will not let me open it as root (even in terminal, which nets the error of unable to gethostbyname()).  If I try using the window browser, I can open the file as read-only and see that I need to add my hostname, but I cannot save it into the drive (since I cannot login to root).  Is there any help you could offer to help get my out of this logic loop?  
Many thanks in advance!
Cheers,
Patrick

---

### Post by Treebeard on 2006-02-19
You can always use the live CD to boot, 
mount your drive and change the /etc/hosts on your drive.

---

### Post by patrick.ubuntu on 2006-02-19
Hi,
I really appreciate all the help I've been getting on this!  People who say that windows is better than linux seem to forget about how friendly the linux helpers are (especially in comparison with Microsoft call center employees)!

So back to the problem at hand.  The "use a live cd" idea kind of worked and kind of didn't.  I used Slax to change the /etc/hosts file so it now reads like it should -

127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

However, I'm still having the same problems with not being able to use sudo and getting the error message at the startup of Gnome not being able to lost onto localhost.  Is there another file that needs to be corrected?

Your help is greatly appreciated!
Cheers,
Patrick

---

### Post by patrick.ubuntu on 2006-02-20
Hi,
Well I gave up on fixing my mistake, but not on Ubuntu.  I've reinstalled and am happy to have a working linux box again.
Thank you for your help in the posts!
Cheers,
patrick

---

