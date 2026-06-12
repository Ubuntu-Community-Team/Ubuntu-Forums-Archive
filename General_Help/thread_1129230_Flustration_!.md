---
title: "Flustration !"
date: 2009-04-18
forum: General Help
---

### Post by lewtwo on 2009-04-18
I am really, really, really trying to get confortable with Ubuntu but one thing keeps FLUSTRATING me to no end! The paranoid feature of disabling login by 'root'!!!

You can not do anything of any consequnce unless you are logged in as root or you resort to the arcane command line interface!
 Item: System, Administration, users and groups
 Item: System, Administration, Authorizations
 Item: Install software (in this case VmWare workstation 6.5)

OK ... get over it! Figure out how to assign a password to root and move on. So I did that. Installed VMware set up a half dozen machines. Great it work. Then I install (wait for it) NoMachine client server. YEP that works ... almost: You can not login as remotely as root !!!!

OK ... get over it!
System, Administration, Login ... nope you have to be root to use that as well! Attach monitor, keyboard and mouse to machine again. System, Administration, Login and check to be sure every arcane security feature is turned off. System, Administration, Authorizations and make sure user has been granted every right avaialable. Try it again SAM. .... no joy. Go through NoMachine's
configuration files. Nothing there pertaing to loggin in as root. Make user a member of 'root' group, authorize user Create and Delete files on each and every directory in File system. Login via Nomachien as user and run VMWARE .... sorry you are not authorized. Well that is no suprise ... per VMware isntruction you are suposssed to install the software as "the user that will run the virtual machines".

OK ... get over it!
Drag the machine back and reinstall the Monitor, keyboard, mouse. Reformat the hard disk and dod a fresh install. Try to install VMWare as user. No joy. Go through the authorization garbage again. No joy.

Before I reformat the hard disk (again) and install Windwos (because it actually works!) does anyone have any idea how to enable remote login in by root via NoMachine ??

---

### Post by hikaricore on 2009-04-18
I don't really understand what you're talking about or why you feel the need to repeat "get over it" every few lines.
However I think you may want to do a bit of reading on how to access your system with root privileges as a normal user: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Furthermore, threatening to go back to Windows won't really get you far around here.
Most people simply don't care if you use Linux or not with that attitude.

---

### Post by 3Miro on 2009-04-18
The way the root privileges are set, is one of the most powerful security features of Linux.

You need to worry about it only initially (and installing software just asks for the password once, why is it such a big deal). The during normal use, you don't need root password.

---

### Post by nikgare on 2009-04-18
> You can not do anything of any consequnce unless you are logged in as root or you resort to the arcane command line interface!
Item: System, Administration, users and groups
Item: System, Administration, Authorizations
Item: Install software (in this case VmWare workstation 6.5)

This is patently incorrect - if you're going to have a rant about something at least have the good grace to base just a little on fact.

---

### Post by lewtwo on 2009-04-18
> **nikgare said:**
> This is patently incorrect - if you're going to have a rant about something at least have the good grace to base just a little on fact.

It is ABSOLUTLEY correct.

As the "normal" user the Ubuntu install creates one can run these applications ... but that user can not change any of the settings (or in many cases even view the settings). That makes having those applications in the menu system worse than useless. 

I also note that no one could address the address the question which further validates the point.

---

### Post by lewtwo on 2009-04-18
> **3Miro said:**
> The way the root privileges are set, is one of the most powerful security features of Linux.

You need to worry about it only initially (and installing software just asks for the password once, why is it such a big deal). The during normal use, you don't need root password.

It is a BIG DEAL because the software does NOT ask for the password. It just refuses to run unless one is logged is as 'root'. If you install it as 'root' then you can not run the application as another user.

---

### Post by russo.mic on 2009-04-18
It sounds to me like you don't have the slightest idea how sudo and root user privillages work.  Your simply frustrated by something you don't understand.  


This is a problem that plenty of us around here never have, simply because we understand the permissions system.  Windows users have a hard time with this i think, because THERE IS NO PERMISSIONS SYSTEM, the underlying reason for the security flaws.  

what's really sad is that the problem all stems from the lack of it in DOS, and here we are, 20 years later, and still not getting this right.

---

### Post by lewtwo on 2009-04-18
> **russo.mic said:**
> It sounds to me like you don't have the slightest idea how sudo and root user privillages work.  Your simply frustrated by something you don't understand.  


This is a problem that plenty of us around here never have, simply because we understand the permissions system.  Windows users have a hard time with this i think, because THERE IS NO PERMISSIONS SYSTEM, the underlying reason for the security flaws.  

what's really sad is that the problem all stems from the lack of it in DOS, and here we are, 20 years later, and still not getting this right.

Windows does have a "permission system" and it is much more granular than the simple 3 category system offered in linux (you also do not have to drop to the command line administer it). The biggest flaw with Windows AD object based rights is the inability to tell what "objects/resources" a users does have rights to. OH ... to be fair Windows and Linux do share a common problem. Too many Windows applications are written such as to require the user to be an "administrator" to run the application (QuickBooks for example). Poorly engineered applications (in both worlds) contribute more to security risks that "flaws" in either OS.

If anyone runs across this tread looking for the answer to the question of running NOMACHINE as root:
Per NOMACHINE's web site the client can not login as 'root'. This is requested feature (since 2005) that is listed in their roadmap with a low priority. As I am certain that someone will say this a "security" feature I would like to point out that it would be no less secure than running a SSH terminal session as root.

From my perspective NOMACHINE is the only remote GUI interface available in the LINUX world (VNC requires an open session on the target machine ... not to mention it is as slow 90 weight grease in an artic blizard). The need to drag a physical KVM set to the machine and/or the limitation of haveing to use CLI in order to administer the system completely defeats my puposes.

---

### Post by lewtwo on 2009-04-18
> **matrixblue said:**
> 
Then you will have admin rights which include the ability to run programs as root by typing your password.

Not when the programs are not written to prompt for the for the password. Non of the aforementioned applications are written with that option.

But thanks for the suggestion.

---

### Post by matrixblue on 2009-04-18
> **lewtwo said:**
> Not when the programs are not written to prompt for the for the password. Non of the aforementioned applications are written with that option.

But thanks for the suggestion.

All of the System Configurations prompt for your password when you are in the admin group. This won't happen when your user account isn't in the admin group.

To solve the problem use the command I listed to add your account to the admin group.

---

### Post by nikgare on 2009-04-18
> **lewtwo said:**
> It is ABSOLUTLEY correct.


I have no root user on any of my machines, and yet I have the ability to make administrative changes.  According to your statements this is not possible.

Either I am imagining this ability, or your blanket statements are incorrect.

---

### Post by lewtwo on 2009-04-20
> **nikgare said:**
> I have no root user on any of my machines, and yet I have the ability to make administrative changes.  According to your statements this is not possible.

Either I am imagining this ability, or your blanket statements are incorrect.

The statements are correct.
My guess would be that you are are using the CLI "to make administrative changes".

---

### Post by matrixblue on 2009-04-20
You're still misunderstanding what I'm saying to you. The account that you are using is not an administrative account so it can make administrative changes. If you follow the intructions listed in my above posts then your account would made an administrative account and you can do whatever tasks you need to do by typing in your password.

You're using a Desktop User Account right now.

---

### Post by lewtwo on 2009-04-20
> **matrixblue said:**
> All of the System Configurations prompt for your password when you are in the admin group. This won't happen when your user account isn't in the admin group.

To solve the problem use the command I listed to add your account to the admin group.


Negative: 
Not all of the System Configurations prompt for your password.
Noteable exception is "Users and Groups", but I would guess that there are others as well.

Lastly there are other applications that are written such as to require root priviledges and some of these do NOT prompt for a root (aka sudo) password.

---

### Post by lewtwo on 2009-04-20
> **matrixblue said:**
> You're still misunderstanding what I'm saying to you. The account that you are using is not an administrative account so it can make administrative changes. If you follow the intructions listed in my above posts then your account would made an administrative account and you can do whatever tasks you need to do by typing in your password.

You're using a Desktop User Account right now.
>>
root@ub1:/home/xpuseer# adduser xpuseer admin
The user `xpuseer' is already a member of `admin'.
root@ub1:/home/xpuseer# 
<<

Please note that I DO check my facts.

---

### Post by matrixblue on 2009-04-20
Something is messed up with your permissions settings then.

It easiest to back up and re-install. This is not typical Ubuntu behaviour.

---

