---
title: "dcopserver error after login in KDE because of hostname"
date: 2006-07-13
forum: Desktop Environments
---

### Post by linuxnewbie946 on 2006-07-13
"There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read Network Connection List.
//.DCOPserver_**Area 51**_0
Please check that the "dcopserver" program is running!"

Notice I have 'Area 51' in bold above. This will show up later.

I got this error after rebooting from compiling a kernel and changing the hostname. I couldn't get into KDE because of this error. I rebooted and chose failsafe mode for the session ([B]NOT RECOVERY MODE AT THE BOOTLOADER[/B)]and I was able to start my favorite web browser, Firefox. After quite a bit of searching on Google I found 2 things:

chown <yourusernamehere w/o brackets> .ICEauthority
chgrp <yourusernamehere w/o brackets> .ICEauthority
rm -rf /tmp/
mkdir /tmp
rm -rf ~/.ICE
startx

This did not work for me. Instead it showed me a blank screen and I had to do a manual reboot.

The second thing was this:

dcopserver --nosid

or.........

usr/X11R6/bin/dcopserver --nosid

I went into the failsafe session again, started firefox and it hit me. **[SIZE="5"]NO SPACES ARE ALLOWED IN THE HOSTNAME![/SIZE]** I did a little searching on Google and found the file I needed to edit to change the hostname(Area 51) in /etc/hosts/. When I tried to edit the file, I got this message:

unable to lookup Area 51 via gethostbyname()

Great. I need to change the hostname but I can't because the hostname has spaces in it.
Eventually, 2 hours after I screwed up, I found this solution by Mustard here: [http://www.ubuntuforums.org/showthread.php?t=91455&page=2]("http://www.ubuntuforums.org/showthread.php?t=91455&page=2")
He said to reboot into the **RECOVERY MODE AT THE BOOTLOADER** and edit the file as root with this command:

nano /etc/hosts

It worked! This is the file before the edit:

127.0.0.1 localhost localhost Area 51
127.0.1.1 Kubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

And this is the file after the edit:

127.0.0.1 localhost Kubuntu Kubuntu
127.0.1.1 Kubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

After I exited nano (Ctrl-X, Y, Enter)

I entered this command:

hostname TimeWaster

This changed my hostname to TimeWaster (no spaces:D )
And everything worked out happily ever after.

---

