---
title: "audio fine for local accounts, none for domain accounts"
date: 2005-10-16
forum: Desktop Environments
---

### Post by stevea1210 on 2005-10-16
I have a domain with a win 2k3 domain controller.  I have joined my ubuntu pc's to active directory fine.  I can log in fine with active directory  domain accounts.  However when I do, audio doesn't work.  Sound is fine when I log in with a local account.  Sound played before login is fine.  This isn't a sound card/driver issue.  It is a permissions issue.  The local account is a member of the audio group.  I can't (or at least don't know how to) add the domain accounts to the audio group.  When I go to system-->admin-->users and groups, the domain accounts don't show up (which makes sense).  I have added domain accounts to the sudoers list to see if that helped, it didn't.

How can I add active directory user accounts to a local group? Is there another way to approach this on a domain level?  Any assistance is appreciated.

---

### Post by stevea1210 on 2005-10-18
I figured out most of it on my own.  Still one part I can't get to work as I 'd like it.

```
sudo adduser "DOMAIN\user" audio
```

does the trick.  Keep in mind it may be DOMAIN+user depending on what your winbind separtor is set to in your smb.conf.

That gave one user audio on one PC.  I Prefer to do it on a domain level so I can have all users have audio on all machines without touching each user and each machine.  

I created an AD security group named "linux-audio", and added all users to it.  I tried to add linux-audio to the audio group, but it won't let me add a group to a group.  

Does anyone have any ideas on making this change on a domain level?

---

### Post by bloodyjoergi on 2005-10-27
I have the same problem... how the other users add domain-users to local groups... like audio, cdrom, video, admin, ....

and for what are the winbind options
-c
-C
-x
-X
-o
-O

I can't get any useful information from help... are there any examples for that?

---

### Post by tbaptista on 2005-10-28
I have the same problem.

Can anyone think of a different approach to automate the inclusion of all new accounts from the domain to the required groups?

Best Regards,
Tiago Baptista

---

### Post by bloodyjoergi on 2005-10-30
hmmm...
isn't there a clean solution for that?

no one an idea?

---

### Post by stevea1210 on 2005-10-31
I hacked together a script to make things easier on us.  It will pull all of the users from active directory, and allow you to add them to one or 100 groups.  It works well on my 2k3 domain.  I'd appreciate some feedback from others on it.

Pros:  allows you to add all users in AD to any of the local groups in a few seconds.  Saves time as you don't have to add one user at a time, or one group at a time.

Cons:  adds ALL users as wbinfo -u sees them.  That means computer accounts, and some system accounts get added.  Not the end of the world, but adds a little bloat.  Also it is reactive;  it will add all existing users, but has no function to take care of future users.

Feel free to use, and modify the script as it suits your environment and experience.  I would appreciate hearing how others modify it, to see how the script evolves.  (read goodies I can use myself). 

The script isn't perfect, and may have some typos in it.  I'm ok with that, and if it bothers you, open gedit and have at it ;)

It has to be run as sudo, since the adduser command needs root access.  I reccomend putting the script in its own folder, as it creates two text files during execution (1 for the ad users, 1 for the groups you want to add).

```

#!/bin/bash
# userlist.sh

ROOT_UID=0   # Root has $UID 0.

if [ "$UID" -ne "$ROOT_UID" ]  # adduser needs to be run as root.  This checks for root, and exits if you're not root or sudo.
then

echo "You are just an ordinary user (but mom loves you just the same)."
echo "Unfortunately, mom can't run this script, root needs to."
exit
else
  echo "You are root. Good we can proceed."
echo "Press enter to see a list of all users in you domain"
read
echo "" > GROUPLIST #clear out the grouplist file from previous runs of script to start fresh
N=1           # counter to be able to show how many users were added

wbinfo -u 1>users #writes AD users to file "users"
cat users

echo ""
echo "Above is a list of all of the users in your domain."
echo "All of them will be added to the group or groups  you specify below."
echo "If you wish to edit the list of users added CTRL-c to kill the script,"
echo "and edit the file 'users' in this same folder."
echo "Then edit this script to comment out the line \"wbinfo -u 1>users #writes AD users to file users\""
echo "If you want more functionality than that, add it yo damn self :)"
echo ""
echo "With that out of the way, what group do you want to add users to?"
read GROUPNAME
echo $GROUPNAME >> GROUPLIST
echo ""
while true
do
echo "Would you like to add another group? (y/n)"
  read YN
  case $YN in
    y* | Y* ) echo "What other group?" ; read GROUPNAME ; echo $GROUPNAME >> GROUPLIST ;;
    [nN]* )   echo "ok, we'll move on." ; break ;;
        * ) echo "It's not that hard.  Put a \"y\" or an \"n\" in there.  I'll give you another shot." ;;
esac
done
for GROUPNAME in $(awk 'BEGIN{FS=":"}{print $1}' < "GROUPLIST" ) #loop 1 time for each GROUP
do
N=1
echo ""
echo "Now we'll add users to "$GROUPNAME
echo "press enter to start"
read
for USER in $(awk 'BEGIN{FS=":"}{print $1}' < "users" ) #loop 1 time for each user in users file
#for USER in $(awk "users")
do
  echo $USER
  adduser $USER $GROUPNAME
  let "N += 1"
done 

let "N -=1 "
echo""
echo $N users added to group $GROUPNAME
echo ""
done


fi

exit


```

---

### Post by victor_sina on 2006-09-29
i found a more simple the solution

in the /etc/pam.d/common-auth file put the folowing

auth    required        pam_group.so use_first_pass

and... in the /etc/security/group.conf

 * ; * ; * ; Al0000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner

Thats all

Victor

---

### Post by crmanski on 2006-10-05
Victor,
I just tried this on a dapper ltsp box I am running than authenticates domain accounts. I was wondering if I need to restart any services to make this take effect? Or where in the /etc/pam.d/common-auth file should I place that line? Mine looks like this...
```
auth    sufficient      pam_winbind.so
auth    required        pam_unix.so nullok_secure use_first_pass
auth    required        pam_group.so use_first_pass

```
Thanks,
Craig

> **victor_sina said:**
> i found a more simple the solution

in the /etc/pam.d/common-auth file put the folowing

auth    required        pam_group.so use_first_pass

and... in the /etc/security/group.conf

 * ; * ; * ; Al0000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner

Thats all

Victor

---

### Post by victor_sina on 2006-10-05
hello Craig

Tnis is my /etc/pam.d/common-auth

```
auth    sufficient      pam_winbind.so
auth    required        pam_unix.so use_first_pass
auth    required        pam_group.so use_first_pass
```

in the /etc/security/group.conf

```
.....(a lot of commented stuf) ....
#xsh; tty* ;sword;!Wk0900-1800;sound, play
#xsh; tty* ;*;Al0900-1800;floppy

* ; * ; * ; Al0000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner

#
# End of group.conf file
#
```

You will need to Reboot the ubuntu linux box.

When u login in the ubuntu box with an Active directory account u can see the master volume icon in the right corner of the gnome desktop working.

Regards
Victor

---

### Post by xKid on 2006-10-09
> **victor_sina said:**
> hello Craig

Tnis is my /etc/pam.d/common-auth

```
auth    sufficient      pam_winbind.so
auth    required        pam_unix.so use_first_pass
auth    required        pam_group.so use_first_pass
```

in the /etc/security/group.conf

```
.....(a lot of commented stuf) ....
#xsh; tty* ;sword;!Wk0900-1800;sound, play
#xsh; tty* ;*;Al0900-1800;floppy

* ; * ; * ; Al0000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner

#
# End of group.conf file
#
```

You will need to Reboot the ubuntu linux box.

When u login in the ubuntu box with an Active directory account u can see the master volume icon in the right corner of the gnome desktop working.

Regards
Victor

same for kubuntu ?

---

### Post by victor_sina on 2006-10-09
perhaps...
in debian is working to...

---

### Post by EnglishRob on 2006-11-26
> **victor_sina said:**
> hello Craig

Tnis is my /etc/pam.d/common-auth

```
auth    sufficient      pam_winbind.so
auth    required        pam_unix.so use_first_pass
auth    required        pam_group.so use_first_pass
```

in the /etc/security/group.conf

```
.....(a lot of commented stuf) ....
#xsh; tty* ;sword;!Wk0900-1800;sound, play
#xsh; tty* ;*;Al0900-1800;floppy

* ; * ; * ; Al0000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner

#
# End of group.conf file
#
```

You will need to Reboot the ubuntu linux box.

When u login in the ubuntu box with an Active directory account u can see the master volume icon in the right corner of the gnome desktop working.

Regards
Victor

I've tried doing this on Ubuntu Edgy but I still can't get any sound.  The mixer icon appears but it is disabled (as if the sound is muted).  When I double click the icon I just get an error message about the sound device working.

I tried to follow the instructions [here](http://tech.canterburyschool.org/tech/UbuntuWorkstations) and I can authenticate against the domain server (running Samba 3) but I don't get any sound.

I tried adding 

```
gdm;*;*;Al0000-2400;floppy,audio,cdrom,video,plugdev,scanner
```

and then 

```
*;*;*;Al0000-2400;floppy,audio,cdrom,video,plugdev,scanner
```

to /etc/security/group.conf but I still can't get any sound.

(I also tried the adduser DOMAIN+User to the audio group and this doesn't work either).

Anyone got any ideas?

Rob

---

### Post by TrialAndError on 2007-01-20
Hello EnglishRob!

Did you try ```
id
``` to check whether your configuration is working and you (as a domain-user) belong to the group "audio"?

I guess this is wrong:> Tnis is my /etc/pam.d/common-auth

Code:

auth sufficient pam_winbind.so
auth required pam_unix.so use_first_pass
auth required pam_group.so use_first_passAfter "sufficient", if the condition is a success, no further conditions are checked.

Therefore I suggest this:

```
auth sufficient pam_unix.so
auth required pam_group.so use_first_pass
auth required pam_winbind.so use_first_pass
```

Regards

---

### Post by haganerei on 2007-02-13
This did it!

I installed Ubuntu desktop 6.10 to a vmware machine on my XP workstation with bridged networking. I set it to use the IP addresses of the Domain Controllers as the primary and secondary DNS servers just like our Windows 2000/XP Pro Member Workstations.

I used this guide to bind to our Active Directory Domain running at Windows Server 2003 Functional Level on two Windows Server 2003 SP1 Domain Controllers:
**[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")**

The config files I ended up with:

**/etc/default/ntpdate**
NTPSERVERS="primarydomaincontroller.addomain.com secondarydomaincontroller.addomain.com"
NTPOPTIONS="-u"

**/etc/hosts**
127.0.0.1 workstation.addomain.com localhost workstation

**/etc/krb5.conf**
[logging]
        default = FILE:/var/log/krb5.log

[libdefaults]
        ticket_lifetime = 24000
        clock_skew = 300
        default_realm = ADDOMAIN.COM
        dns_lookup_realm = false
        dns_lookup_kdc = true

[domain_realm]
        .addomain.com = ADDOMAIN.COM
        addomain.com = ADDOMAIN.COM

**/etc/samba/smb.conf**
[global]
        security = ads
        realm = ADDOMAIN.COM
        password server = *
        workgroup = ADDOMAIN
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2
        domain master = no
        local master = no
        preferred master = no
        os level = 0

**/etc/nsswitch.conf**
passwd:         compat winbind
group:          compat winbind
shadow:         compat

**/etc/pam.d/common-account**
account sufficient       pam_winbind.so
account required         pam_unix.so

**/etc/pam.d/common-auth**
auth    sufficient      pam_unix.so
auth    required        pam_group.so use_first_pass
auth    required        pam_winbind.so use_first_pass

**/etc/pam.d/common-session**
session required pam_unix.so
session required pam_mkhomedir.so umask=0022 skel=/etc/skel

**/etc/pam.d/sudo**
auth sufficient pam_winbind.so
auth sufficient pam_unix.so use_first_pass
auth required   pam_deny.so
@include common-account

**/etc/security/group.conf**
* ; * ; * ; Al0000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner

As the initial user I added the following groups via visudo (don't freak this is just for testing--but it does work):
%Domain\ Admins ALL=(ALL) ALL
%Domain\ Users ALL=(ALL) ALL


For what it's worth, the final issue I was trying to resolve was the lack of local rights as an Domain User. In the end it ended up being the specification in **/etc/security/group.conf** and the reordering of the information in **/etc/pam.d/common-auth** that fixed it.

---

### Post by smadon on 2008-01-31
thanks for the how to.
But I couldn't git it right for 1 caractere l or 1

> 
* ; * ; * ; Al0000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner
and not 
* ; * ; * ; A10000-2400 ; floppy, video, audio, cdrom, dip, plugdev, users, scanner


3hours for that :-(

---

