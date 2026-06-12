---
title: "What's the Ubuntu 12.10 LTS Root Password"
date: 2012-07-19
forum: Desktop Environments
---

### Post by therack on 2012-07-19
I don't know the root password, Please help.

if I want to authenticate sudo root, I got error with the password I give.

---

### Post by Bill Z on 2012-07-19
There is not a fixed standard root password.  You establish that when you install your OS.  If you don't know it, you will probably have to re-install.

---

### Post by QIII on 2012-07-19
There is no root password by default.  To use sudo, type the password you use to sign in if you installed the OS or have been put in sudoers

---

### Post by QIII on 2012-07-19
> **Bill Z said:**
> You establish that when you install your OS.

Well, not a root password but it sure seems like it for all intents and purposes most users are likely to encounter.  

On install, the login name created is a sudoer.  There is no root password by default.

A sudoer can have "root-like" privileges or "become root" temporarily, but is not root.  There is rarely, if ever, anything one might need to do while actually signed in as root as far as a normal user's needs go.  So Ubuntu has no root password by default.

And you need not reinstall if you have forgotten your login password.  But I don't think that is what you are asking, is it?

---

### Post by critin on 2012-07-19
> **therack said:**
> I don't know the root password, Please help.

if I want to authenticate sudo root, I got error with the password I give.

Make sure the caps lock is on/off, depending on how you created the password.  You use the same (login)  password for all authenticating.  
If using the terminal commands, be sure to use --sudo-- before each command, but not in front of the password.   The password will not show in the terminal.

---

### Post by bogan on 2012-07-19
Hi!, **al**l,

I want to disagree with most of these Posts.

Yes, there is no default root password, but circumstances can arise when you need one.

In one of my 12.04 LTS installations, after an Update, I needed to boot into a root terminal from recovery, only to be greeted with a demand for a root password, or to Press 'D' to return to the recovery menu. It would not accept my user password, despite multiple attempts.

Not getting any help from a Thread in these Forums, I eventually 'cured' it by making the root Password the same as my user password.

Whether that is the OP's problem I do not know, as he/she does not seem to have said why a root password is needed.

Chao!, **bogan.**

---

### Post by critin on 2012-07-19
> **therack said:**
> I don't know the root password, Please help.

if I want to authenticate sudo root, I got error with the password I give.

Scroll about half-way down for info.  The whole page is an informative read though.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by critin on 2012-07-19
> **bogan said:**
> Hi!, **al**l,

I want to disagree with most of these Posts.

Yes, there is no default root password, but circumstances can arise when you need one.

In one of my 12.04 LTS installations, after an Update, I needed to boot into a root terminal from recovery, only to be greeted with a demand for a root password, or to Press 'D' to return to the recovery menu. It would not accept my user password, despite multiple attempts.

Not getting any help from a Thread in these Forums, I eventually 'cured' it by making the root Password the same as my user password.


Chao!, **bogan.**

Searching the threads will call up extra help.  But since you learned to fix it yourself--you'll never forget how you did it.

---

### Post by lJ9%3MR&gt;sa on 2012-07-20
If you absolutely want a root password "su password" (I don't recommend this) then open a Terminal and type ```
[FONT=Courier New]sudo passwd[/FONT]
``` and press enter. You will need to enter your own password then when it asks, type the new root password.

---

### Post by QIII on 2012-07-20
Oh, never mind.  Note to self.  Read carefully before responding.

Keeps one from feeling like an Equus africanus asinus.

---

### Post by QIII on 2012-07-20
> **bogan said:**
> Hi!, **al**l,

I want to disagree with most ...

I'd definitely disable the root password.

If you had first selected "Networking", you would have both enabled networking and mounted your drive with write access and been able to use sudo.

I have not needed to log in as root for many years.  There are very few reasons ever to do that and maintaining an active root password is a grave security risk.

In trying to hack your machine there is no need to guess both username and password.  "root" can now be attacked.

---

### Post by cariboo on 2012-07-20
When using sudo it doesn't switch to the root user, it just escalates the current users privileges. If you need to do a task that needs escalated privileges for longer than the default time out period, use:

```
sudo -i
```

BTW the solution in post #9 only changes the current users password.

---

### Post by QIII on 2012-07-20
> **cariboo907 said:**
> BTW the solution in post #9 only changes the current users password.

Well, now that I actually read the post more carefully, I will grin sheepishly...

Does the Equus africanus asinus grin?

---

### Post by bogan on 2012-07-21
Hi!, **Qlll,**

Thanks for your Post #11.

Actually I had used 'fsck' to set Read/Write, and 'Networking' - which did not work - and also 'dpkg', between repeated attempts to 'Drop to Root Shelll with Networking'.

Every time, I was met by a demand for a Root Password, or returned to the Recovery menu.

As to the security, surely the 'normal' ability to 'Drop to Root Shell', from a Recovery boot, **without the requirement for any password**, is a much more potentially disastrous security breech? 

Edit:  I just recovery rebooted to check out my memory, and 'Networking' still does not work, but I was able to drop to the root shell without a password, nor the need to log-in!!

Chao!,[B] bogan.
[/B]
Reason for editing: updating

---

### Post by zombifier25 on 2012-07-21
> **bogan said:**
> As to the security, surely the 'normal' ability to 'Drop to Root Shell', from a Recovery boot, **without the requirement for any password**, is a much more potentially disastrous security breech?

You can only drop to root prompt if you have physical access to the computer. Then again, if a stranger has physical access to your computer and he/she is determined to hack into it, then all is lost, with or without root.

So it's not a security issue.

---

### Post by QIII on 2012-07-21
When you initially go to the recovery mode, you are mounted read-only.

Going to "Networking" won't do much but start networking and mount your drive with write permissions, then drop you back to the command line.  So it wouldn't appear as if it did much.

Then, when you go to "Root",  you have the ability to do your darndest to bork your machine.

---

### Post by bogan on 2012-07-21
> **zombifier25 said:**
> You can only drop to root prompt if you have physical access to the computer. Then again, if a stranger has physical access to your computer and he/she is determined to hack into it, then all is lost, with or without root.

So it's not a security issue.In that case it is not a security issue either to have a Root password set - even if it is the same as the a user password.

As it happens, multiple other people do have physical access to one of my computers.

Chao!, **bogan.**

---

### Post by QIII on 2012-07-21
But physical access is not the only mode of attack and other modes are much easier if all one has to do is brute force a password assuming that there is a user "root" with a password.

So, in general, it is a security risk.

---

### Post by since on 2012-10-24
hi! ithink you all havent get faced the problem,



i wanna boot ubuntu 12.01 on a PC with no screeen


so i cannot do sudo, passwd, etc....


[B]
whats the default passwd for ubuntu when booting live and wanna connect via SSH / network????
[/B]

thanks
Florian, a Linux user since SUSE LINUX 6.0

---

### Post by snowpine on 2012-10-24
> **since said:**
> hi! ithink you all havent get faced the problem,



i wanna boot ubuntu 12.01 on a PC with no screeen


so i cannot do sudo, passwd, etc....


[B]
whats the default passwd for ubuntu when booting live and wanna connect via SSH / network????
[/B]

thanks
Florian, a Linux user since SUSE LINUX 6.0

Welcome to the forums!

I recommend you make a new thread for your question.

To answer your question, Ubuntu does not run ssh-server by default. You are going to need screen/keyboard access to your Ubuntu server initially to install and configure ssh-server before you can use SSH to connect from other machines.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by since on 2012-10-24
ok thanks. so i will have to manage a screen and kb attached

---

### Post by nothingspecial on 2012-10-24
See here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Closed

---

