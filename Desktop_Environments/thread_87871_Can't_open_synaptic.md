---
title: "Can't open synaptic"
date: 2005-11-09
forum: Desktop Environments
---

### Post by meinrad on 2005-11-09
Hi there

I installed Ubuntu on my notebook. But now, I'm not able to start any of the programs of the System->System administration (I don't know the correct name of this pull-down menu, I installed Ubuntu in German, it's the menu where synaptic is)

What did I wrong?

Thanks

Meinrad

---

### Post by adwait on 2005-11-09
try opening a terminal and typing
```
sudo synaptic
```
Enter your own password. See what errors (if any) it gives.

---

### Post by mainform on 2005-11-09
Sorry to hijack the thread a little,

I think I'm having the same problem as meinrad on my desktop, nothing I try to run under System>Administration seems to do anything after I've entered my password - sometimes I see the application trying to start but it appears to quit by itself. Using the terminal doesn't seem to do anything, either.

```
james@synchrotron:~$ sudo synaptic
Password:
james@synchrotron:~$

```

This happens no matter what administrative application I try to run. Interestingly, the first time I tried to use sudo, I got an error telling me I wasn't in the sudoers list :confused: It hasn't done that since. After that, it asks for my password, and presumably I've been sudoed, but nothing seems to happen. I wonder if meinrad has the same problem :???: 

Again, sorry for the hijack, I didn't want to post a new topic when there seemed to be one for my problem already. Any ideas? :)

---

### Post by adwait on 2005-11-09
Hmm........well normally if you are not on the suders list, every time you try to use sudo, it will pop that warning, but still it might help to check if you are indeed on the suders list.
```
sudo visudo 
```

This will open the sudoers file. Check if your name is there in it, eg:
> 
james ALL=(ALL)ALL
or maybe
> %<your group name> ALL=(ALL)ALL

If not, try adding yourself in that format and then save and exit.

---

### Post by meinrad on 2005-11-09
I didn't get the warning with the sudoers list or another warning, But everytime I tried to start a such program, there is no reaction.

What can I do?

Thanks

Meinrad

---

### Post by mainform on 2005-11-09
[QUOTE=adwait]Hmm........well normally if you are not on the suders list, every time you try to use sudo, it will pop that warning, but still it might help to check if you are indeed on the suders list.
```
sudo visudo 
```[/QUOTE]

I'm getting much the same result again, nothing appears to be executing after I've entered my password, no reaction. :confused: I managed to get the warning again after I tried that a few times, though. I could be missing something, but I can't think what. Any ideas?

[SIZE="1"]thanks for putting up with my hijacking meinrad :)[/SIZE]

---

### Post by adwait on 2005-11-09
Hmm, so basically both of you have NO root access?? Try this, while booting, at the grub prompt press 'e'. This will allow you to edit the boor parameters. At the end of the line, add "init = /bin/bash". Now allow GRUB to boot. This should get you into a command line interface. Now run visudo to check if the file is in order and if not make changes and save it. Reboot.

This may not work......have never tried it, but don't worry anything you type at the GRUB prompt will only affect that session, so if adding that line to grub doesn't work....no harm done :).

---

### Post by meinrad on 2005-11-10
I have the root password, why do I gotta start the grub console?

I booted on the Gentoo LiveCD, mounted the root device and chrooted. I typed passwd and entered the new root password, so the bash starting with GRUB isn't needet, I think.

Thanks

Meinrad

---

### Post by adwait on 2005-11-10
Well the root account is disabled by default, so I figured........

Anyway, so if you can login as root now, just check out your sudoers file.

---

### Post by meinrad on 2005-11-22
Hi there

The problem's solved:

I just installed Debian :p  :cool:  :D 

I thought: Why should I use a Linux distribution which is based on Debian instead of using Debian itself.

So, I just installed Debian and it works really well. I don't regret it.
It's not as good as Gentoo :(  , but it's enough.

Bye

Meinrad

---

### Post by Othersider on 2005-11-23
Same problem here, except I want to stick with Ubuntu.

Any program in System > Administration won't run.  I have to open terminal, type in 'su', enter my password, and then execute the program.  gksudo/sudo doesn't do anything.

Any ideas?

---

### Post by fimbulvetr on 2005-11-23
What do you get when you do "sudo ps"?

---

### Post by Othersider on 2005-11-23
Absolutely nothing:
```

me@localhost:~$ sudo ps
me@localhost:~$

```

---

### Post by codejunkie on 2005-11-23
[quote=Othersider]Same problem here, except I want to stick with Ubuntu.

Any program in System > Administration won't run.  I have to open terminal, type in 'su', enter my password, and then execute the program.  gksudo/sudo doesn't do anything.

Any ideas?[/quote] if you chose the expert install option when you installed ubuntu it enables the root account by default and doesn't add your name to the sudoers file, however the administration menu items use sudo instead of su. for example the command to launch synaptic in ubuntu is ```
gksudo synaptic
``` which uses your password, in debian it is 
```
gksu synaptic
```which uses the root password,
since you can use su command to gain root access in a terminal you have two options. you can either edit the .desktop files in the administration menu manually to use gksu instead of gksudo, which is the way longer way around. or just add your username to the sudoers file like this. open a terminal use su to gain root access and then run this command 
```
export EDITOR=gedit && visudo
``` and add your user name to the bottom of the file like this
```
 yourusername ALL=(ALL) ALL
``` save and exit gedit and test your apps that were not working before when it asks for a password use your password not the root accounts hope this helps.

---

### Post by lyly on 2005-11-23
[QUOTE=Othersider]Same problem here, except I want to stick with Ubuntu.

Any program in System > Administration won't run.  I have to open terminal, type in 'su', enter my password, and then execute the program.  gksudo/sudo doesn't do anything.

Any ideas?[/QUOTE]

Do you have scim installed? it does the same for me, gksudo just time out waiting for scim to load, I uninstalled scim and the problem was away... It begin to bug since I installed the scim-m17 package...

---

### Post by fimbulvetr on 2005-11-23
[QUOTE=Othersider]Absolutely nothing:
```

me@localhost:~$ sudo ps
me@localhost:~$

```[/QUOTE]

That's extremely odd, I can't even think of how that can happen. I don't think it's a question of you not being in sudoers, because you'd get an error after trying to authenticate.

Paste the output from:

tail -20 /var/log/auth.log

and maybe a:

sudo strace ps

---

### Post by Othersider on 2005-11-23
codejunkie, thanks so much :).  Your advice worked perfectly.  I should've mentioned that I installed in expert mode (had to provide hdparm to avoid hardware issues).

Thanks for everybody for your help and patience - now all the Administration programs run without a problem.

---

### Post by mikesmind on 2005-11-25
I am having a similar problem.  I can't launch Synaptic from the System>>Administration menu.  I was able to do it yesterday, but not today.  It seems to be the only application affected.  I am able to launch it from a shell.  How do I remove it from the menu and add it back in?  I'm thinking that that might be worth a try.

Thanks! Mike

---

