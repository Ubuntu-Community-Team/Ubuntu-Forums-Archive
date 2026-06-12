---
title: "how automount sshfs filesystems automatically at startup"
date: 2005-12-01
forum: Desktop Environments
---

### Post by afonit on 2005-12-01
does anyone have any experience in automounting sshfs directorys on startup?

I did not see a how to in the howto section, and I have put this together from places on the web, but it still doesn't work, 

could someone please enlighten me on where I am going wrong?



1. add the 'fuse' into
/etc/modules


2. insert into /etc/fstab

sshfs#username@serverip:/Volumes/alt/location/ /media/location/ fuse defaults 0 0


but it fails to load on startup.

---

### Post by dlai on 2006-01-10
well i got some of the way with this... and now i'm stuck...
first of all you'll have to create a public key...make sure the passphrase is the same as the the one you login with.
```
ssh-keygen -t dsa
```
then copy it to the host computers directory
```
scp .ssh/id_dsa.pub user@host:/directory
```
login with ssh on the host
```
ssh -C user@host
```
copy the key into the right directory:
```
cat id_dsa.pub >> .ssh/authorized_keys
```
add the ssh key to the agent (i think).
```
ssh-add
```
install libpam-ssh
```
sudo apt-get install libpam-ssh
```
open up /etc/pam.d/kdm
```
auth       required     pam_nologin.so
auth       required     pam_env.so
+++auth       sufficient   pam_ssh.so
session    required     pam_limits.so
+++session    optional     pam_ssh.so
```
add the lines with +++



now you login to your ssh account when you login... but how to make it mount the sshfs... we are still to find out... it has something to do with pam-mount (maybe)....

---

### Post by schilcha on 2006-01-10
There was a similar thread some weeks back... I don't know, if the suggestions helped that user -- the thread stopped without clear conclusion. Anyways, maybe there's something in it that helps.

[http://www.ubuntuforums.org/showthread.php?t=104441](http://www.ubuntuforums.org/showthread.php?t=104441)

Good Luck!

---

### Post by dlai on 2006-01-11
Well I actually got very close to how to do this... It seems the libpam-mount is to old, to mount sshfs... therefore one would have to install it from source (0.10 or above).. I installed it, though it needed an upgrade of both libglib and libssl (both from source). And I'm pretty sure i wrote the things correct to mount it. In /etc/security/pam_mount.conf you write:
```
volume <user(* for any user)> fuse - "sshfs#user@server:/directory/blabla" <mountpoint> <mount-options> - - 
```
and in /etc/pam.d/login you write:

```
.....
# Disallows other than root logins when /etc/nologin exists
# (Replaces the `NOLOGINS_FILE' option from login.defs)
auth       requisite  pam_nologin.so
+++ auth     optional  pam_mount.so use_first_pass

......
# Prints the status of the user's mailbox upon succesful login
# (Replaces the `MAIL_CHECK_ENAB' option from login.defs). You
# can also enable a MAIL environment variable from here, but it
# is better handled by /etc/login.defs, since userdel also uses
# it to make sure that removing a user, also removes their mail
# spool file.
session    optional   pam_mail.so standard noenv
+++ session  optional  pam_mount.so
@include common-password
```

and in /etc/pam.d/kdm you write

```
@include common-password
@include common-session

auth       required     pam_nologin.so
auth       required     pam_env.so
auth       sufficient   pam_ssh.so
+++auth       optional     pam_mount.so use_first_pass
session    required     pam_limits.so
session    optional     pam_ssh.so
+++session    optional     pam_mount.so
```

I think this is all we should do... but I might have lost something by installing from source. I dunno....

---

### Post by kciampi319 on 2007-08-07
i made this script to start hamachi then load a drive with sshfs on startup.  you are going to need to chmod +x this script after you make it and add it to your startup programs.  it is kind of long because it will attempt to load the drive 5 times maximum  over about a minute and a half on start up.  It will always attempt to mount with sshfs on lan first and will use hamachi if you are not on your home network.  I commented the script to death so you can modify it to whatever you want to do.  There is one important thing that is not mentioned in the comments.  you must put a file in the drive being mounted.   this script checks to see if that file exists in order to determine if the drive is mounted or not.  in my script that file was named /media/NetworkedExt/.thispartitionismounted.txt so just change it to whatever you want.  everything else i will put in bold that needs to be REPLACEDwithYOURconfigs.  good luck.
> 

#!/bin/bash
exec 
#the following command is needed unless you use a script to start tuncfg in /etc/init.d. The drawback to not 
#doing the init.d script is that you will be prompted for your admin password at every login. 
#gksudo tuncfg
hamachi start
ab=9
bb=2
d=1
#this sleep is not needed if you uncomment gksudo tuncfg
sleep 3

#all exit points will run hamachi get-nicks before exiting the 20 second sleep allows hamachi to fully initialize
while [ $ab = 9 ]; do
#check to see if its already mounted and exits if it is
	if [ -f /media/NetworkedExt/.thispartitionismounted.txt ]; then
		echo "its already mounted"
		sleep 20
		exec hamachi get-nicks
		exit 0			
		ab=8
		bb=3
		fi	
#if its not already loaded this sleep acts a spacer between attempts allowing a network connection to be #established.  It then attempts to connect to the server on lan and mount the drive	
sleep 10
		if [ $bb = 2 ]; then
		sshfs LOGIN@LANADDRESS:FOLDERTtoMOUNT 'MOUNTPOINT'
		fi
#this checks if the drive was mounted and exits if it is.
		if [ -f /media/NetworkedExt/.thispartitionismounted.txt ]; then
		echo "mounted on home network"
#this display command and the two lines following are used open and close a picture 
#file to display the echo message when terminal is closed. there is another one later in the file
		display MOUNTEDonHOMEnetworkPICTUREfile &  
		sleep 1
		killall display
		echo "success"
		sleep 20
		exec hamachi get-nicks
		exit 0		
		ab=8
		bb=3
		fi	
#if it is not already mounted this will mount the folder on hamachi
		if [ $bb = 2 ]; then
		sshfs LOGIN@LANADDRESS:FOLDERTtoMOUNT 'MOUNTPOINT'
		echo "$d" 
		fi
#this is a counter.  It allows the loop to run a maximum of five times
		if [ $d = 5 ]; then
		echo "unable to start"
		sleep 20
		exec hamachi get-nicks
		exit 0 
		fi	
#this checks to see if hamachi loaded to folder and exits if it has.
		if [ -f /media/NetworkedExt/.thispartitionismounted.txt ]; then
		display MOUNTEDonHAMACHInetworkPICTUREfile &
		sleep 1
		killall display	
		echo "success"
		sleep 20
		exec hamachi get-nicks
		exit 0
		ab=8
		bb=3
		fi
#this is the other part of the counter that adds 1 to the value of d when it reaches the end of the loop
		let d=d+1
done
#this program will never actually reach here it is just left over from its original version
echo "success"
sleep 20
exec hamachi get-nicks
exit 0

---

### Post by kciampi319 on 2007-08-08
sorry but there is a slight error in the script.
the only difference is that i added the & at the end of the mount to command to keep it from hanging and never continuing the loop 

> #!/bin/bash
exec
#the following command is needed unless you use a script to start tuncfg in /etc/init.d. The drawback to not
#doing the init.d script is that you will be prompted for your admin password at every login.
#gksudo tuncfg
hamachi start
ab=9
bb=2
d=1
#this sleep is not needed if you uncomment gksudo tuncfg
sleep 3

#all exit points will run hamachi get-nicks before exiting the 20 second sleep allows hamachi to fully initialize
while [ $ab = 9 ]; do
#check to see if its already mounted and exits if it is
if [ -f /media/NetworkedExt/.thispartitionismounted.txt ]; then
echo "its already mounted"
sleep 20
exec hamachi get-nicks
exit 0
ab=8
bb=3
fi
#if its not already loaded this sleep acts a spacer between attempts allowing a network connection to be #established. It then attempts to connect to the server on lan and mount the drive
sleep 10
if [ $bb = 2 ]; then
sshfs LOGIN@LANADDRESS:FOLDERTtoMOUNT 'MOUNTPOINT' &
sleep 5
fi
#this checks if the drive was mounted and exits if it is.
if [ -f /media/NetworkedExt/.thispartitionismounted.txt ]; then
echo "mounted on home network"
#this display command and the two lines following are used open and close a picture
#file to display the echo message when terminal is closed. there is another one later in the file
display MOUNTEDonHOMEnetworkPICTUREfile &
sleep 1
killall display
echo "success"
sleep 20
exec hamachi get-nicks
exit 0
ab=8
bb=3
fi
#if it is not already mounted this will mount the folder on hamachi
if [ $bb = 2 ]; then
sshfs LOGIN@LANADDRESS:FOLDERTtoMOUNT 'MOUNTPOINT' &
sleep 5
echo "$d"
fi
#this is a counter. It allows the loop to run a maximum of five times
if [ $d = 5 ]; then
echo "unable to start"
sleep 20
exec hamachi get-nicks
exit 0
fi
#this checks to see if hamachi loaded to folder and exits if it has.
if [ -f /media/NetworkedExt/.thispartitionismounted.txt ]; then
display MOUNTEDonHAMACHInetworkPICTUREfile &
sleep 1
killall display
echo "success"
sleep 20
exec hamachi get-nicks
exit 0
ab=8
bb=3
fi
#this is the other part of the counter that adds 1 to the value of d when it reaches the end of the loop
let d=d+1
done
#this program will never actually reach here it is just left over from its original version
echo "success"
sleep 20
exec hamachi get-nicks
exit 0

---

### Post by jcollins on 2007-11-26
I wrote an easy script to tackle this problem. You will need to do as dlai says above and save the password so it does not need to be entered.
NOTE: You MUST have sshfs installed.

1. In the terminal:
```
sudo gedit connect
```

2. In a text editor:
```
ip=[COLOR="Red"]XXX.XXX.XXX.XXX[/COLOR]
user=[COLOR="Red"]user[/COLOR]
dir=[COLOR="Red"]/home/user[/COLOR]
r=1
c=0
until [ $r = 0 ]
do
if test $c -gt 120
then
exit 1
fi
ping -c 2 $ip
r=$?
c=`expr $c + 1`
sleep 5
done
sshfs $user@$ip:$dir /media/sshDrive 
```
You will need to fill in your IP address OR domain name for[COLOR="Red"] XXX.XXX.XXX.XXX[/COLOR].
The '[COLOR="Red"]user[/COLOR]' needs to be replaced with the user name being logged into on the server.
Also [COLOR="Red"]/home/user[/COLOR] needs to be replaced with whatever directory you want to access on the server.
This script will compensate for connection times (such as wireless) at boot and will automatically execute when the internet signal is received.

3. Save the script and exit. Now in the terminal you need to make it executable by typing:
```
sudo chmod +x connect
```

4. Now we need to make it execute at startup. Go to 'System' and then 'Preferences' and finally click 'Sessions.' Click the add button and type in any name, for command click browse and navigate to your 'connect' file. Enter a description such as 'Connect to living room hard drive' if desired.

5. Click OK and you are done.

---

### Post by Oswald1 on 2008-01-13
How about this one:

Basically something like the script proposed by jcollins would be a good starting point for this, but what if I want to do this from my laptop and at times I do it over LAN and at times over internet.

My setup is such that when I'm home I must ssh the servers ip and when not I must ssh a domain name provided by dyndns.

In a nut shell I would need an addition to the previous script which would first somehow figure out whether I'm home or not and assign the ip variable accordingly.

Any ideas?


Cheers.

---

### Post by jcollins on 2008-01-13
By modifying my last script a bit, I came up with a solution for your problem.

```
ip=[COLOR="Red"]XXX.XXX.XXX[/COLOR]
domain=[COLOR="Red"]YOURDOMAIN.DOMAIN[/COLOR]
user=[COLOR="Red"]user[/COLOR]
dir=[COLOR="Red"]/home/user[/COLOR]
r=1
c=0
a=$(( $c % 2 ))
until [ $r = 0 ]
do
a=$(( $c % 2 ))
if [ $a -eq 0 ]
then
nip=$ip
fi
if [ $a -eq 1 ]
then
nip=$domain
fi
if test $c -gt 120
then
exit 1
fi
ping -c 2 $nip
r=$?
c=`expr $c + 1`
sleep 5
done
sshfs $user@$nip:$dir /media/sshDrive
```

Save and CHMOD as above.

NOTE: You still have to have your password saved in a manner such as this:
[http://www.linux-hero.com/howto/passwordless-ssh-logins]("http://www.linux-hero.com/howto/passwordless-ssh-logins")

Or just copy/paste this:
```
ssh-keygen -t rsa
```
```
cat ~/.ssh/id_rsa.pub | ssh [COLOR="Red"]remote_machine[/COLOR] "cat - >> ~/.ssh/authorized_keys"
```
```
chmod 700 .ssh
chmod 644 .ssh/authorzied_keys
```
Change remote_machine to ip or domain.
Good luck! Hope it works!

---

### Post by monkeyking on 2008-01-14
I was playing around with this a year ago.
And I did the following.

1.  installed ssh-installkeys. And ran it on the remote computers
2. added mystuff to the fstab.
3. made a mount script that reads fstab, and logins.
4. made a unmount script that unmounts all sshfs mounts.

ad3. this one I made runable and put in /etc/networking/if-up.d/
ad4. this one I made runable and punt in /etc/networking/if-down.d/

This way, if I loose connection everything will be unmounted autimaticly,
and when the network comes back on, it logins in automaticly.

This works fine for med.

I didn't play around with libpam, no need.

---

### Post by Oswald1 on 2008-01-14
@jcollins: This got me halfway there. I also think there is nothing actually wrong with your script. It works nicely at home, but now at office I'm facing a new problem: Apparently one can't ping a host which is behind dyndns OR I just can't ping my adsl-box from outside home.

There is a Antiprobing tab in the adsl-box's web configuration and I've set it to respond to ping from wan and lan and also added firewall rules to allow ping to go back and forth. Still no response.

I was thinking of a workaround of this sort:

```

ip=XXX.XXX.XXX.XXX
user=user
dir=/home/user
r=1
c=0
until [ $r = 0 ]
do
ping -c 2 $ip
r=$?
c=`expr $c + 1`
if test $c -gt 30
then
r = 0
ip = DOMAIN NAME
fi
sleep 5
done
sshfs $user@$ip:$dir /media/sshDrive

```

This isn't that good though, as it will keep on trying to ping the lan version and after that it'll simply try to sshfs over internet without checking wether it can be done or not.

The best solution would be to fix the ping-problem and use the 'original' version, but I haven't figured it out yet. Another solution would be to replace ping with something else to check wether the host can be found.


p.s. A n00b question: In
ping -c 2 $ip
r=$?
Does the r=$? line mean that you take the result of the previous line and assign it to r? That $? part doesn't really ring a bell for me...

---

### Post by jcollins on 2008-01-14
@monkeyking, yes this is one way, actually the most common way. I used to do it this way until I made this script because it is a better way for me. Instead of using fstab, I made a script that tries for 10 minutes to connect. That way here on campus, it gives me time to connect to the wireless network or just do whatever and it will automatically wait and connect once a ping has been established.

@Oswald1 Yes, the problem may lie in the IP, if there is a computer on your work network with the same IP as your home computer, it will try to connect to that one. If you believe this is the problem just switch the IF blocks around, that test $a.

And not a very newbie question, but $? returns the exit status of the previous program. By that I mean, if the ping is unsuccessful, $? will be 1, if it is successful it will be 0. Good question.

BTW the line "a=$(( $c % 2 ))" checks if '$c' is even or odd, if you were wondering.

EDIT: also if you launch it in the terminal you can see what is going on. If it is just alternating a ping between your home and domain, that means the domain is unreachable. Get back to me and I will try to help you.

---

### Post by Oswald1 on 2008-01-14
Alright, thanks for these.

Still, I don't think switching the IF parts around would help in my situation. I mean wouldn't that result in just first trying to ping my public ip and on the second round my private ip and so on. My problem is that my public ip doesn't ping, so anyways both of the tests will result in no ping when at office.

I found some random site saying that at times ISP's block pings. This might be my case and if it is then there's probably not much I can do.

However I came up with another kind of test. I can't check if it works from work right now but tomorrow I will. Anyway at home it seems to work and I see no reason why it wouldn't work elsewhere.

1. create an empty file sshpingdummy in my homedir on the server (i.e. nano sshpingdummy)
2. substitute the line 
ping -c 2 $nip
 with
scp $user@$nip:~/sshpingdummy .

What it does is it tries to ssh-copy the empty file and use the return state of scp to determine if a connection could be made or not.

This should work when ever ssh will work, which is exactly what is needed. As a plus one can disable outside ping responses (not really a problem for me here...) which is considered a security problem by some.

Something wrong with my reasoning here?


btw the 10 minute delay when connecting is one of the things i like about jcollins' solution as i must login through a web form at work before I can access the internet so nothing happening right at startup would work (i.e. fstab is a no go).


edit: I guess something like "rm sshpingdummy" could be entered at the very end of the script if the empty file bothers someone.
edit2: A critical typo...

---

### Post by jcollins on 2008-01-14
Try this one out. Not the way I would normally do it, but desperate times call for desperate measures.
Now it just pings google.com to see if there is an active internet connection and just tries to connect to both home and work. 

```
ip=XXX.XXX.XXX.XXX
domain=DOMAIN.COM
user=user
directory=/home/user
r=1
c=0
until [ $r -eq 0 ]
do
c=`expr $c + 1`
if [ $c -gt 120 ]
then
zenity --error --text="SSH connection timed out."
exit 1
fi
ping -c 2 64.233.161.18
r=$?
sleep 1
done
sshfs $user@$domain:$directory /media/sshShare
s=$?
sshfs $user@$ip:$directory /media/sshShare
t=$?
u=`expr $s + $t`
if [ $u -ne 0 ]
then
zenity --error --text="Error connecting to SSH share. Error Code: $s/$t"
exit 1
fi

```

Since it is kind of going in there blindly, I have put in some error dialogs so if the operation is unsuccessful, you will know. It can either time out or just not connect. Both of which will generate an error.

Good luck!

---

### Post by Oswald1 on 2008-01-15
Everything seems to work right now. As an iteration, here is the working script.

```

ip=xxx.xxx.xxx.xxx
domain=domain.com
user=myusername
dir=/dirtobemounted
r=1
c=0
a=$(( $c % 2 ))
until [ $r = 0 ]
do
a=$(( $c % 2 ))
if [ $a -eq 0 ]
then
nip=$ip
fi
if [ $a -eq 1 ]
then
nip=$domain
fi
if test $c -gt 120
then
exit 1
fi
scp $user@$nip:~/sshpingdummy .
r=$?
c=`expr $c + 1`
sleep 5
done
sshfs $user@$nip:$dir /wheretomount

```

Here one has to create an empty file sshpingdummy on the server in your home directory and of course do the passwordless login stuff and chmodding of the script file etc.

I think I prefer using scp for testing the connection as sshfs feels a bit overkill for this purpose.

---

