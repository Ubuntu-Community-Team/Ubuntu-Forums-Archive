---
title: "Change the order of startup programs (wireless networking)"
date: 2006-08-06
forum: Desktop Environments
---

### Post by mssever on 2006-08-06
How can I make my wireless connection start either during the boot process (preferred) or before any other program starts at login?

My situation is this: I have several startup programs that require network access in order to function properly, but when I log in the first time after rebooting, wireless networking seems to be the very last thing to be loaded. This means that I have to manually update the weather applet and manually start Tomboy Notes (I've symlinked its data files to an NFS server, for easy file sharing).

If I log out and back in without rebooting, everything works fine because wireless is already up and running.

---

### Post by dennisharrison on 2006-08-06
my wirless is up and running before I log in im pretty sure.  Are you using ndis wrapper for you driver? or a wireless manager program instead of just setting up your wireless connection under network connections?

---

### Post by mssever on 2006-08-06
My wireless card (Broadcom 4306) wouldn't work with ndiswrapper. [This post]("http://www.ubuntuforums.org/showpost.php?p=1251630&postcount=2") shows my wireless setup. As far as I can tell, nm-applet is what starts my wireless card, but I don't know what commands it issues. Using sudo /etc/init.d/networking start does *not* work. I wish it did and could be started the same way as standard ethernet.

---

### Post by simonn on 2006-08-06
```

ls -ld /etc/rc?.d

```

These directories contain symbolic links to the startup scripts located in /etc/init.d.

There is one directory for each run level, 0 to 6 - /etc/rc.[0-6].d, and S - /etc/rcS.d - for system - i.e. run first and for all run levels.

Run levels on ubuntu are defined as below

0	Halt the system.
1	Single-user mode (for special administration).
2-5	Normal operation (user defined).
6	Reboot.

Think of this as having 6 different config.sys and autoexec.bat files.

run level 5 is generally used by default.

If you look in the /etc/rc?.d directories you will see a load of links like:

```

K10something
S30something-else

```

K means kill
S means start

The number is the order in which is should be run, S00runmefirst would be run before S99runmelast, K00killmefirst will be killed before K99killmelast etc.

The name following this is usually the name of the script in /etc/init.d that the symbolic link links to, although in theory this can be anything - only K or S and the number are important.

On Ubuntu it is best to use the command update-rc.d to add and remove links to the init scripts, see man update-rc.d. As update-rc.d modifies files in /etc, it needs to be run as root, i.e. use sudo.

What you need to do is make sure that the wireless script has a lower number than the scripts which need network access to run properly - disclaimer: I do not use wireless on my linux box, so there may be other considerations of which I am unaware.

---

### Post by dennisharrison on 2006-08-06
Ok, I started posting before sim came up with all that info.  Much better information then what I had ;p

[edited : removed useless content]

---

### Post by az on 2006-08-06
> **mssever said:**
> My wireless card (Broadcom 4306) wouldn't work with ndiswrapper. [This post]("http://www.ubuntuforums.org/showpost.php?p=1251630&postcount=2") shows my wireless setup. As far as I can tell, nm-applet is what starts my wireless card, but I don't know what commands it issues. Using sudo /etc/init.d/networking start does *not* work. I wish it did and could be started the same way as standard ethernet.

No.  Get rid of NM-applet and then go to the networking tool in System- Administration.  Configure your wireless and you are good to go.  Your wireless will then work when netwroking is restarted (or started on boot)

---

### Post by mssever on 2006-08-06
There is no init script for wireless networking on my system. The networking script calls "ifup -a", which doesn't start wireless. I'm plenty willing to create the appropriate init script if I only knew what commands to call.

---

### Post by mssever on 2006-08-06
> **azz said:**
> No.  Get rid of NM-applet and then go to the networking tool in System- Administration.  Configure your wireless and you are good to go.  Your wireless will then work when netwroking is restarted (or started on boot)

As far as I can tell, the networking tool doesn't support WPA encryption. It assumes WEP.

EDIT: I just tried putting my WPA key in the box labeled WEP key, just in case it would take either. No dice. Also, when I restart networking, it does try to do a DHCPDISCOVER for eth1 (my wireless card). However, it fails every time. Nm-applet is the only way I've been able to connect.

---

### Post by dennisharrison on 2006-08-06
thats true 
I had to disable wpa and go with mac address filtering. Simply because I couldn't find an easy work around.

---

### Post by mssever on 2006-08-06
> **dennisharrison said:**
> thats true 
I had to disable wpa and go with mac address filtering. Simply because I couldn't find an easy work around.

The problem with MAC address filtering is that it's incredibly easy to spoof. nm-applet does support WPA, even if it starts wireless on login.

---

### Post by dennisharrison on 2006-08-06
what about mac address filtering oddball ip ranges and no dhcp or ssid broadcast? wouldn't you need to know what mac and ip address to spoof? can you get that easily?

---

### Post by mssever on 2006-08-07
> **dennisharrison said:**
> what about mac address filtering oddball ip ranges and no dhcp or ssid broadcast? wouldn't you need to know what mac and ip address to spoof? can you get that easily?

That only provides a small amount of protection. All the necessary information can be obtained by listening in to your network traffic (by merely having a computer within range of your network), since it's sent in cleartext. WEP encryption is easily cracked. There are many programs available for free that will discover and give an attacker all the necessary information.

---

### Post by dennisharrison on 2006-08-07
yeah like the auditor cd I played with a few months ago. you still can't get your wireless to boot first?

---

### Post by mssever on 2006-08-07
No. No success.

---

### Post by dennisharrison on 2006-08-07
bummer.  So wpa is pretty much the only thing to use to stop someone from stealing your hard earned mbits? ;p
and even thats not perfect

so the suggestion you got a few posts back about the start and kill timings didnt help because you don't know exactly what program is being used to initialize your network connection?

---

### Post by mssever on 2006-08-07
> **dennisharrison said:**
> bummer.  So wpa is pretty much the only thing to use to stop someone from stealing your hard earned mbits? ;p
and even thats not perfect

I'm mostly concerned that someone could listen in on my network and steal sensitive information--especially since I make extensive use of NFS, which isn't encrypted. Of course, I could switch to a purely wired network, but I prefer wireless.

> so the suggestion you got a few posts back about the start and kill timings didnt help because you don't know exactly what program is being used to initialize your network connection?

That's correct. However, I've managed to hack together a workaround, which I'm posting here in case it can help anyone.

[LIST=1]
[*]Copy this script and paste in into a new file (I called mine wait-for-network):
```
#!/bin/bash
#
# Wait for Network: Delays execution of the programs listed on the
# command line until networking is available.
# NOTE: Due to a bug somewhere, only one program may be
# specified on the command line.

NFSTESTDIR="/media/scott-desktop/home"

i=1
while ((i <= 25)); do
	echo -n "Network check $i...   "
	ping -c 1 google.com &> /dev/null
	exitStatus=$?
	echo "ping returned $exitStatus"
	if [ $exitStatus -eq 0 ]; then
		OK=1
		break
	fi
	((i += 1))
	sleep 5s
done

if [ $OK -eq 1 ]; then
	for program in `echo $@`; do
		if [ "$program" -eq "tomboy" ]; then
			i=1
			while ((i <= 25)); do
				if [ -e "$NFSTESTDIR" ]; then # check that NFS is up
					$program
					break
				fi
				((i += 1))
				sleep 5s
			done
		else
		$program # Should be $program & but that doesn't work when
		         # called from the startup tool
		fi
	done
	exit 0
fi
exit 1

```
[*]Change the line beginning "NFSTESTDIR=" to point to a directory that will only exist once NFS is up. If you don't use NFS, hack the script to remove the NFS test stuff.
[*]Do "chmod +x wait-for-network" (or whatever you named your file)
[*]Go to System > Preferences > Sessions
[list]
[*]In the "Current session" tab, select nm-applet and set its order to 41 (NOTE: as I was writing this, I noticed that it somehow got reset to 50. I hope I won't have to change this every reboot)
[*]In the "Startup programs" tab, change the entry for the programs that need networking to /path/to/wait-for-network program (eg, /home/scott/bin/wait-for-network tomboy). If the program's command line contains spaces, enclose the program and its options in single quotes.
[/LIST]
[*]Reboot to make sure everything is working properly and enjoy. Note that there might be a significant delay before the program starts, as each time the script checks for connectivity and fails, it waits for 5 seconds before trying again.
[/list]

---

### Post by SishGupta on 2006-08-07
Dont listen to thoes other guys, you pretty much need network manager (nm-applet) for WPA in ubuntu. I think theres some other apps you could use, however network manager is the best and you'd likely have the same problem with other apps.

Here is a linix noob's understanding of the situation. 
Theres 3 parts to network manager: NetworkManager, NetworkManagerDispatcher, nm-applet.

nm-applet is launched by gnome.
If you check out System>Preferences>Sessions and then view the "Startup Programs" tab nm-applet is listed.

What i dont know is if NetworkManager and the Dispatcher are launched by nm-applet or something else in linux. What I do know is that wireless doesnt work untill nm-applet is started.

So to get wireless earlier  you need to make nm-applet launch earlier, but are you able to make nm-applet launch before or earlier in the gnome startup process?

I hope something here helps because I would love earlier wireless as well.

---

### Post by mssever on 2006-08-07
Thanks for the reply. I've read the man pages for NetworkManager and NetworkManagerDispatcher, and I'm not sure whether or not they'll help. It certainly seems that NewworkManager should be started at boot, though. I haven't yet had time to look thouroughly into this.

Also, after reading the man pages for various iw* programs, it seems that iwlist and iwconfig hold the key to having wireless at boot. Again, I haven't had time yet to experiment.

---

