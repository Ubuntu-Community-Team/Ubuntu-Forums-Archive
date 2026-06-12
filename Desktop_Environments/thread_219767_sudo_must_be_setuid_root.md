---
title: "sudo: must be setuid root"
date: 2006-07-20
forum: Desktop Environments
---

### Post by beesforbreath on 2006-07-20
I'm unable to perform any sudo operations because of this error message
> must be setuid root
I've read through the forums and I believe the issue is with the fact that I chowned the /usr/ directory. My question is: how do I change it back to root so I can use sudo?

---

### Post by lprimm on 2006-07-28
Yeah - I did the same thing... did you figure/find a way to fix it? (other than reinstalling....)

---

### Post by TheBlackNoodle on 2006-07-28
If the problem is just that you chowned /usr, try rebooting with the Ubuntu Live CD. Open a terminal and do the following...

sudo mkdir /mnt/ubuntu
sudo mount /dev/hda1 /mnt/ubuntu
sudo chown -r root /mnt/ubuntu/usr
sudo umount /mnt/ubuntu

I'm assuming your install is on /dev/hda1. If it's not, you'll have to change that part to match your setup.

But you should be able to do all the maintenance you need from the Live CD.

If the problem is not only that you chowned /usr, I can't guarantee this will work.

---

### Post by BLTicklemonster on 2006-09-05
I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

### Post by ferd on 2006-09-06
Thank you so much. I had struggled with this for days and did finally reinstall. This will save me 4 hours if I am ever dumb enough to chown usr again.

---

### Post by Naikei on 2006-09-11
> **BLTicklemonster said:**
> 

ls -l usr/bin/sudo 

chown root:root /usr/bin/sudo

chmod 4755 /usr/bin/sudo

reboot

Thankyou so much :D. I am one tired, happy, sleeping without "WHAT COULD IT BE!?" tonight, user. Because of you.
Haha.
Cheers
Naikei

---

### Post by taff99 on 2006-10-28
Thanks for the advice, it work for me to.

Shame I let my chmod run from / without noticing it ..

I now have another message up after I try SUDO

Sudo: /etc/sudoers is mode 0777, should be 0440

I also have a nice message at login about $HOME... 

A nice evening ahead ......

Thanks

---

### Post by tom35i on 2006-11-20
Hey i hav the same problem with setuid but when i type into the terminal 
ls -l usr/bin/sudo
i get
ls: usr/bin/sudo: No such file or directory
please help it is now beena few weeks and is starting 2 piss me off:mad:  ThAnK U

---

### Post by funk19 on 2006-12-04
> **tom35i said:**
> Hey i hav the same problem with setuid but when i type into the terminal 
ls -l usr/bin/sudo
i get
ls: usr/bin/sudo: No such file or directory
please help it is now beena few weeks and is starting 2 piss me off:mad:  ThAnK U

You are missing a backslash. Try this:

```
ls -l /usr/bin/sudo
```

---

### Post by saadakhtar on 2006-12-05
> **taff99 said:**
> Thanks for the advice, it work for me to.

Shame I let my chmod run from / without noticing it ..

I now have another message up after I try SUDO

Sudo: /etc/sudoers is mode 0777, should be 0440

I also have a nice message at login about $HOME... 

A nice evening ahead ......

Thanks

[B]GOTO RECOVERY MODE
ONCE YOU ARE LOGGED IN UNDER ROOT,
TYPE IN:           *chmod 0440 /etc/sudoers* 

PRETTY OBVIOUSLY

HOPE THIS HELPS[/B]

---

### Post by EvilChipmunk on 2006-12-05
you can eliminate the problem with setting up the root passwork

sudo su
<pass>
passwd

---

### Post by Dogfighter on 2007-07-05
> **BLTicklemonster said:**
> I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```
had a smimilar result, but it didnt solve the problem for me. :(




> **BLTicklemonster said:**
> but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.
whenever i try chwon it tells me "chwon unknown command" :/
and the second one alone doesnt help.

> **EvilChipmunk said:**
> you can eliminate the problem with setting up the root passwork

sudo su
<pass>
passwd
when i try to do so i get the same error "sudo: must be setuid root".

any ideas?

oh btw im using ubuntu 7.04. faisty (sp?)

*EDIT* i actually found the problem.

BLTicklemonster wrote "chwon" which i assumed is right but of course its chown :D
so, problem solved and im happy :)

---

### Post by zeekay on 2007-08-20
> **Naikei said:**
> Thankyou so much :D. I am one tired, happy, sleeping without "WHAT COULD IT BE!?" tonight, user. Because of you.
Haha.
Cheers
Naikei

That solved for me too. Thanks. :)

---

### Post by kandhala on 2007-08-31
Thanks to Mr Monster for giving this Good Info.
with regards,
kandhala

---

### Post by djknorr75 on 2007-09-16
Diddo!  Thanks for posting this....maybe there should be some kind of warning for us noobs when we go changing the permissions for /usr?  :)

Also, if I only have one user on my pc, why can't I own everything?  :)

---

### Post by DorianScholz on 2007-10-12
I had a similar problem and even after trying your solution I got:
```

$ sudo
sudo: must be setuid root
$ su
setgid: Operation not permitted

```

I had to do one more thing to get sudo and su back:
```

chmod 4755 /bin/su

```
this changed the permissions of su:
```

from
-rwxr-xr-x 1 root root  27140 2006-12-19 21:35 su
to ^here
-rwsr-xr-x 1 root root  27140 2006-12-19 21:35 su

```
see the 'x' vs. the 's'...

hope that helps!
cheers

---

### Post by TeaSwigger on 2007-10-13
> **djknorr75 said:**
> Also, if I only have one user on my pc, why can't I own everything?  :)

You do. That's what sudo's for hehe  Why? For one thing, you may be the only user on your PC, but you're most decidedly not the only user on the internet. ;)

Some precautions in place and presto, you don't need that big biz $oftware $uite (plus $ub$cription$ for updates plus...) "for your security." :)

---

### Post by Pyrollis Ah Firos on 2007-10-14
I posted this in other thread but I'm not getting any replies so I'm posting my comment here. Hope you all can help! Thanks in advance!

__________________________

This is the same error message I got recently.

It's strange that I got it just now. I was doing my usual business last night and the network was fine and all. Today, I saw that my computer has shut down from a different distro and I tried to boot it back in that distro but the GDM error came up so I decided to go back to my usual distro; Ubuntu 6.06. When I went back in and for some reason the network isn't working right, I can't sudo for anything, and I can't even get some programs (synaptic, network configuration, programs that requires sudo to be executed) to run. I double clicked on one program. It would either not appear at all, or shows up then disappears after a while. The not appear at all part is the most common problem. So far what I did last night was delete some files and I didn't think it would be that harmful to Ubuntu. It was some general files and not of any importance to the Ubuntu kernel. Could it be because I accidentally deleted something critical? I can log in my account but no network, can't do sudo (I keep getting the same message, sudo: must be setuid root) and I have tried the method mentioned above but no luck. I'm not sure if this is important but when I logged in my account in recovery mode, I saw this message, "-bash: no job control in this shell". I'm not sure if I'm supposed to have job control or is it just the default message? Also, when I tried to go from my user account to root, su root, I typed in the password but it said, invalid password, sorry.

Oh yeah, I also tinkered with the /etc/fstab file to make the usb device from nouser to user so I can automatically have my USB drive mounted when I plug it in. Could it be part of the reason why I'm experiencing this?

---

### Post by freeky on 2007-11-01
If i dont have recovery mode enabled then reinstalling is the only way out?

Regards
Sandeep

---

### Post by hooah212002 on 2007-11-18
> **BLTicklemonster said:**
> I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.


Worked for me.....the second time. The first time I just typed in exit and I guess it didnt save changes. Thanks BLTicklemonster

---

### Post by Aeolien on 2007-11-21
No. I'm assuming that when you turn your computer on, it just proceeds to the log in screen (i.e. you are not dual-booting).

If that is the case, edit your GRUB configuration file (which you hopefully don't need to sudo to do) with the command:

```
gedit /boot/grub/menu.lst
```

Near the top, you should see a paragraph that says

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

Change that so it says:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

And reboot. You should be presented with an option to the recovery mode.


If this doesn't work, or your system is different in some way, let me know!

---

### Post by rexxxlo on 2007-11-22
i did this too im on the live cd trying to fix it and replied to save the page !

---

### Post by EGRAD on 2007-11-24
I have the same problem. But I can't boot in recovery mode. It gets stuck. at 

[0.624000] ..TIMER:VECTOR=0X30 APICL=0 PINL=2 APIC2=-1 PIN2=-1

i have no ideas. Any help would be great. 

Thanks

---

### Post by graabein on 2007-12-22
I screwed up users and groups after a reinstall, when trying to connect old user directories to new users... I get this when I try to enter user-admin:

```
$ sudo users-admin
sudo: /etc/sudoers is owned by uid 1000, should be 0
$ ls -al /etc/sudoers
-r--r----- 1 graabein root 496 2007-12-22 01:36 /etc/sudoers
```

So how do I rectify this? I have changed all my files to graabein user I think... Not just in /home catalog. Sigh... Is there a script to run to get back to normal settings perhaps?



Edit: OK, I booted into recovery mode and changed owner of /etc/sudoers to root and that solved it. But I still need to change file rights back to normal -- whatever that might be.

---

### Post by StitchJAcket on 2008-01-06
Omg this helped sooo mucH
I was unable to do any of my updates finally had some free time to find the issuE
Or should i saY
ResolutioN
Found this bulletin and got everything working agaiN
ThankS

---

### Post by younfox on 2008-03-18
Okay,  I read over all da messages, but  it doesn't work for me.
I type to terminal dis:
 ls -l /usr/bin/sudo -> i got this message:
 -rwsr-xr-x 1 hana root 91776 2007-06-15 14:49 /usr/bin/sudo -> okay da problem is here, there is hana not root,
then i type this:
chown root:root /usr/bin/sudo ->i got dis message:
chown: "/usr/bin/sudo" owner's changing.This operation is not accepted. -> WHY?
then i type the :
chmod 4755 /usr/bin/sudo ->but is unnecessary like the reboot.
I tried it so much but nothing.
Anybody some idea?

---

### Post by CromagTheTech on 2008-04-25
I'm a noob. I admit it. while trying to install something i chmod 777 -R /usr/bin . Now i get the "sudo: must be setuid root" thing. None of these above suggestions have helped. I can ls -l /usr/bin/sudo I get
-rwsr-sr-x 1 root root 91776 bla blah /usr/bin/sudo
i can't just chown root:root /usr/bin/sudo because it says i dont have permission so I put sudo chown root:root /usr/bin/sudo
and then it goes back to the prompt. next I sudo chmod 4755 /usr/bin/sudo and i get sudo: must be setuid root and thus I'm still stuck with the same problem I had. Anybody got any suggestions as to why it works with EVERYONE else but me?

---

### Post by coolnezz on 2008-05-02
**Thanks!  It worked for me.** :)


> **BLTicklemonster said:**
> I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

