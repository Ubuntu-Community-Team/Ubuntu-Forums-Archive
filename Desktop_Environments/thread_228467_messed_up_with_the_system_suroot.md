---
title: "messed up with the system su/root"
date: 2006-08-03
forum: Desktop Environments
---

### Post by rafalr on 2006-08-03
Hi,

It looks like I messed up with the system su/root behaviour. The effect is that I can now see/access only a very limited scope of System menu.

- While trying to solve (quite common now with Ubuntu 6) problem of kppp, I had to manually edit /etc/ppp/pap-secrets to be able to use gnome-ppp
- it would not let be sudo edited so I had no choice but to set root account (sudo passwd root)
- I then edited the file (I did so using konqueror launched as su, not from terminal as sudo -i, which I now know was bad thing to do); but the gnome-ppp works perfectly now.

Then I locked the root account (sudo -1 root or something like that).

In the meantime I was trying to set-up a shortcut to launch clamav GUI from panel in sudo mode, so I dit put a command "sudo clamav" with option to launch in terminal to be able to input password. Then I launched this and it worked fine. Now I know I should have input rather "gtsudo clamav" as something could have been (or actually has been ?) messed up.

Also, for some time (matter of days, possibly not related to operations above), konqueror would simply shut down reporting error 11 enytime I tried to open "/usr/bin" catalogue (it did shut down as both user and su account).

After the messing described above was done:
- konqueror would not let me use the su mode neither after inputing the user nor su password (reported either "communication with 'su' broken, or "su error")
- I was not able to acces Synaptic (I was not recognised as authorised user).

I was then trying again to fight as root and again enabled root account and logged to terminal as su instead of sudo su or sudo -s or sudo -i. As this was useless i disabled/locked root again.

After logoff/login (which went without problem) I can only see part of the System->Administartion menu (I can not see/access Synaptic, for example).

The problem seems to be that system does not properly recognise the sudo/root users. Now, what did I do wrong and how to repair it ?

I did read the available HOWTOs and screened this forum already, but did not see case like this one. I use Ubuntu 6.06 with Gnome, but also use some KDE based applications that I like (but did not install the whole KDE environment, only the minimum required dependencies).

Your help really appreciated as after a number of nights spent on configuring ALL stuff (and there has been a lot) - I hate idea of reinstalling the whole system.

Rafal

---

### Post by rafalr on 2006-08-04
Hi,

I did some more investigation on the PC and am now pretty sure the effect I reached is that I stripped my user of sudo rigts. Furthermore, I actually did  not unlock root account as I used command "sudo passwd -1 root" instead of "sudo passwd -l root" (I misspelled 1 instead of l).

Also, the system is mute - it says gstreamers are not installed (which is not true), and actually i have no access to any application requiring user password.

Now as my user is not sudoer anymore I can not deactivate root and most possibly can not make myself a sudoer back. It seems the only option is to use su to return my sudo rights - do you know how to do it ?

Oh, and when I type the "users" command it shows my user twice - is that normal or it means system logged me twice ?

Rafal

---

### Post by cantormath on 2006-08-04
> **rafalr said:**
> Hi,

I did some more investigation on the PC and am now pretty sure the effect I reached is that I stripped my user of sudo rigts. Furthermore, I actually did  not unlock root account as I used command "sudo passwd -1 root" instead of "sudo passwd -l root" (I misspelled 1 instead of l).

Also, the system is mute - it says gstreamers are not installed (which is not true), and actually i have no access to any application requiring user password.

Now as my user is not sudoer anymore I can not deactivate root and most possibly can not make myself a sudoer back. It seems the only option is to use su to return my sudo rights - do you know how to do it ?

Oh, and when I type the "users" command it shows my user twice - is that normal or it means system logged me twice ?

Rafal

Let me get this right, you are not able to login as rafalr and 
rafa1r@laptop:~$sudo <any command>?

you say this is because you accidently disable your sudo.  Is your user still part of the "admin" group?  You need you user to be added to the admin group to sudo stuff.

There is nothing wrong with su root or sudo -i in terminal, for certain things, but as you know, you dont want be logging in in as root in the gui all the time, so this is definitely a high priority.

Another thing, when you post a thread, instead of adding three posts in the beginning, you should just edit, using the scissor icon in the bottom right, so that others don't think the question has been answered.


about your sound.
When you say that the system is mute, you mean that just movies wont play, or there is not system sound at all?  
If its just movies, and you are having codec problems too, maybe you want to try this.  
[Automatix.]("http://www.ubuntuforums.org/showthread.php?t=203294") 
It installs all the right sound/video codecs, Mplayer and FF plugins, dvd codecs, etc.  Its cool, and way easy, and it might fix the no movie sound situation.  Be careful, if you installs stuff with it, make sure that when it prompts you to set your repo back to normal, you do so, unless you want your sources.list that way.

---

### Post by wieman01 on 2006-08-04
To give your sudo authority, do this:

Change user:
> su root
No type in root password (if you have one).

Add admin rights to your user:
> sudo adduser <Your_User> admin

This is it.

**>> Edit <<**

Sorry, read your second post just now. Need to find out what you can do myself.

---

### Post by wieman01 on 2006-08-04
Another thing is (in case you have not set the root password) to boot Ubuntu in recovery mode. 

Recovery mode gives your normal user root authority by default. So if you execute the second command you should be able to add admin rights to your normal user.

---

### Post by azmrb on 2006-08-04
I accidentally did something like this myself.

Make sure to check 2 files in /usr/bin

sudo
sudoedit

make sure that root is owner of both and that they have the proper
permissions.  I don't remember exactly but one of them has to be
rws NOT rwx for the owner(root)

---

### Post by catlett on 2006-08-04
As long as you can still use su, you will be able to get sudo powers back. Being a member of the administration group will give you root/sudo powers.
```
su
```
```
adduser rafalr adminn
```
If the files mentioned previously ( sudo, sudoedit) need their permissions changed, you can do it with nautilus
```
su
```
```
nautilus
```
That will launch nautilus as root. Browse to /usr/bin and when you get to sudo right click on it to get the options menu. Select properties and then select the permissions tab. Enable read, write and execute for others and groups. That will open it up to everyone. That is fine if you are the only one on the computer but if their are other users this will open the file to them.
If you still find things messed up for some unknown reason, you can create a new user with sudo powers and use that user or use that user's sudo powers to straighten stuff out.
To make a new user with sudo powers
```
su
```
```
adduser john
```
To give sudo powers, edit /etc/sudoers as root
```
su
```
```
visudo
```
edit this in under root  all,...
```
john              ALL=(ALL) ALL
```
To make john an administrator as well
```
su
```
```
adduser john admin
```

---

### Post by rafalr on 2006-08-05
Hello all,

Thank you for all good hints - it is a bit difficult for me now to quickly come back (I do not have network now with those problems and have to use other PCs).

What I am going to do is first check / edit the attributes of those two sudo related files (I still have valid root access) and if this is either OK or does not helps I will edit visudo as root to make sure my user can still sudo, if this still does not help I will add another user with sudoe rights.

Will come back and brief what I did and with what results.

Thanks again,
Rafal

---

### Post by rafalr on 2006-08-07
Hello again,

1. I did check that 
"sudo
sudoedit 
make sure that root is owner of both and that they have the proper
permissions. I don't remember exactly but one of them has to be
rws NOT rwx for the owner(root)"

they are both owned by root, have x for user/group/all, and have SUID set

2. I did visudo edit the sudoers file and added "rafal" (my user) as ALL/ALL/ALL, I am now sudo:
- the "sudo whoami" returns "root"
- "gksudo nautilus" places me at /root.

3. it seems however that something is messed up at the interface layer with hardware, and I feel completely lost here:
- I can not see big part of the System menu (for example Synaptic, Update manager, Network Admin), while I can launch properly all of them from terminal (gksudo ...)
- the system is *mute* (no sound at all, incl system sounds on start up) and reports my sound card has not been configured (while before that everything was perfectly OK for system sounds, music, videos with all codecs present)
- the software can not see my modem now (gnome-ppp, network-admin, while kppp reports "no access / no permission")
- launching "network-admin" as sudo is successful, but returns error "GnomeUI warning: while connecting to session manager : Authentication Rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed"
- I have no access to USB memory: I am reported system can not launch pmount, also unmounting fails (error: USB is not set in fstab and I am not root)

Is that repairable ?
I am getting mentally prepared to a very sad scenario of re-installation ... 

rafal

---

### Post by Malac on 2006-08-07
This may not be related but I had a similar problem with sound and a few other things not working after messing with user permissions.
It turned out my privileges had been stripped to bare minimum in "Users and Groups". I fixed it by doing the following:
```
su
```Enter root password.
```
users-admin
```Then find and highlight your user in the list and choose [Properties].
Hit the "User privileges" Tab and tick all.
This sorted the problem for me.

Hope this helps.

---

### Post by rafalr on 2006-08-07
Malac,

You are a genius !:mrgreen: 

Having not much hope to have the problem solve by your cure, I decided this is going to be the last thing I will try before backuping my data (one night) and doing complete re-install (another 4 nights).

But it did work ! It took me just 10 seconds to recover to normal, stabile state:
- I have access to complete System menu
- I have sound
- I have access to modem and dial up services
- I have access to USB.

Indeed, the users-admin panel (the "advanced" tab) showed my user had *no* of the available privilidges available - all of the privilidges have been zeroed.

I owe you at least a big beer ...
Rafal

---

### Post by catlett on 2006-08-07
I love a good ending. Thanks for the inpurt malac. After I ran your commands I realised what that window was. It is the "Users and Groups". I never give that system tool much thought but it appears to be very powerful as well as convenient.
Just to add to the thread if someone is searching for an answer and doesn't have a root passwrod, "users and groups" can be accessed from the top panel by System<Administration<Users and Groups. It will prompt for a password but you enter your user password.
rafalr, sorry I didn't have the solution. Luckily malac came in at the 11th hour to save the day.:-D 
Next time I'll be sure to mention "users and groups'" permissions tab.

---

### Post by Malac on 2006-08-07
> **rafalr said:**
> Malac,

You are a genius !:mrgreen: 


Finally my true worth is recognised :-D

Glad I could help Rafal. That virtual beer tastes good. ;)

I went with the su thing as I thought the Panel way would still be blocked if Rafal couldn't sudo

---

