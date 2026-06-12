---
title: "At Work Major Problem Please Help :)"
date: 2006-02-02
forum: Desktop Environments
---

### Post by fletch331360 on 2006-02-02
this is all my fault but i was trying to change the read only status of my external hard drive and i followed some bad directions and apparently changed the permissions to my computer all together. :cry: 

i am now at work and can not access ubuntu which i run evolution and keep all of my customer information. i do not know linux well enough to boot to a command line somehow and maybe fix this isuue.

below is a copy of what happens when i fire up ubu.

please help if you can.

thanks in advance


Your $HOME/.dmrc file has incorrect permissions and
is being ignored. This prevents the default session and
language from being saved. File should be owned
by user and have 644 permissions



Your session only lasted less than 10 seconds. If you
have not logged out yourself, this could mean that
there is some installation problem or that you may be 
out of diskspace. try logging in with one of the failsafe 
sessions to see if you can fix this.

DETAILS:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sean"
/etc/gdm/Xsession:Beginning session setup...

Could not set mode 0700 on private per-user gnome configuration directory ' /home/sean/.gnome2_private/': Operation not permitted

---

### Post by kaamos on 2006-02-02
Did you make changes to your /etc/fstab ?

If it is only a problem with the file (and not drive!) permissions, you could perhaps fix it with```
sudo chown *username*:*username* /home/*username* -R
```
This owns everything in your homedirectory to you, so you hopefully get permissions to read/write.

---

### Post by LanceM on 2006-02-02
To get to a failsafe terminal, at the login screen, click on Sessions and one of the select failsafe options.

---

### Post by fletch331360 on 2006-02-02
well the problem is that i can not log in.

i get the error that is listed above and then i get a big LOGIN: screen and when i enter my username and password i get the :

> Your $HOME/.dmrc file has incorrect permissions and
is being ignored. This prevents the default session and
language from being saved. File should be owned
by user and have 644 permissions


Your session only lasted less than 10 seconds. If you
have not logged out yourself, this could mean that
there is some installation problem or that you may be
out of diskspace. try logging in with one of the failsafe
sessions to see if you can fix this.

DETAILS:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sean"
/etc/gdm/Xsession:Beginning session setup...

Could not set mode 0700 on private per-user gnome configuration directory ' /home/sean/.gnome2_private/': Operation not permitted 



then if i try to log in as root with my password it says " the system administrator is not allowed to login from this screen"

so i can not get into the os. i think the solution would be to get to a command line during startup and fix the permissions but i could be wrong and i do not know how to get to a command line during startup or what to type.

thanks

---

### Post by fletch331360 on 2006-02-02
[QUOTE=kaamos]Did you make changes to your /etc/fstab ?

If it is only a problem with the file (and not drive!) permissions, you could perhaps fix it with```
sudo chown *username*:*username* /home/*username* -R
```
This owns everything in your homedirectory to you, so you hopefully get permissions to read/write.[/QUOTE]

i tried this in the failsafe terminal and i get " must be setuid root "

---

### Post by krusbjorn on 2006-02-02
Have you tried selecting Recovery Mode from the GRUB-menu at bootup and enter the command suggested above?

---

### Post by fletch331360 on 2006-02-02
[QUOTE=krusbjorn]Have you tried selecting Recovery Mode from the GRUB-menu at bootup and enter the command suggested above?[/QUOTE]

ok i did that and i get " /etc/sudoers is owned by gid 1000, should be 0 "


i am currently at " root@sean:~# "

---

### Post by krusbjorn on 2006-02-02
Sound slike you would need to do "chown 0:0 /etc/sudoers" first.

Strange though that it's owned by your main user account. If that user owns your whole file system you should make everything 'cept /home/ owned by root.

---

### Post by fletch331360 on 2006-02-02
[QUOTE=krusbjorn]Sound slike you would need to do "chown 0:0 /etc/sudoers" first.

Strange though that it's owned by your main user account. If that user owns your whole file system you should make everything 'cept /home/ owned by root.[/QUOTE]

i tried the "chown 0:0 /etc/sudoers" and then "sudo chown username:username /home/username -R" and nothing changed.

i am in serious need of my contacts and i thank everyone for helping me.

i have to run out for an hour but i will look at and try all suggestions when i return.

thanks again

---

### Post by krusbjorn on 2006-02-02
[QUOTE=fletch331360]i tried the "chown 0:0 /etc/sudoers" and then "sudo chown username:username /home/username -R" and nothing changed.

i am in serious need of my contacts and i thank everyone for helping me.

i have to run out for an hour but i will look at and try all suggestions when i return.

thanks again[/QUOTE]

In "sudo chown -R username:username /home/username" you have to change "username" to your own username on all three places.
So if your username is sean, its:
> 
sudo chown -R sean:sean /home/sean

---

### Post by fletch331360 on 2006-02-02
[QUOTE=krusbjorn]In "sudo chown -R username:username /home/username" you have to change "username" to your own username on all three places.
So if your username is sean, its:[/QUOTE]

i get " /etc/sudoers is owned by gid 1000, should be 0 "

---

### Post by krusbjorn on 2006-02-02
So what does it say when you do "chown 0:0 /etc/sudoers"?

---

### Post by fletch331360 on 2006-02-02
[QUOTE=krusbjorn]So what does it say when you do "chown 0:0 /etc/sudoers"?[/QUOTE]

it does nothing but give me the command line " root@Sean:~# "

here is what i did to get me in this mess

>    1. Open terminal
   2. cd /media
   3. (Login as root) sudo su
   4. (type) chown -R root:<user> /<usbdisk>
   5. (type) chmod g+w <usbdisk>
   6. (logout of root) exit

    *note - remove < > <user> = substitute your user name
    <usbdisk> = substitute your actual file or folder name.


---

### Post by krusbjorn on 2006-02-02
My guess is that at the step 4 (**4. (type) chown -R root:<user> /<usbdisk>**), you put a space between "/" and the path to your usb-disk, which means that every file on your computer now is owned by user "root" and group <user>.

***If that is the case***, you sure have a real mess. I dont really know of a good solution. I myself would do the following:

chown -R  <your username>:<your username> /home/<your username>
chmod -R 755 /home/<your username>

and then do, for all the directories in / except /home:

chown -R root:root /directory (replace "directory" with "etc", "apt", "usr" etc etc)

But **NOTE** that this is what i would do, and i'm dont even know if it would mess up your system more than it already is. I dont know if there are files outside your home directory that you need to be the owner of to have a functioning system. The commands above makes every file in your home directory owned by you, and all files outside of your home directory owned by root.

So if you choose to perform this, please be sure that you did what i stated in the first paragraph in this post, and dont blame me if your computer explodes.

Otherwise, wait until someone who knows more about linux than i do answers. I bet there are better ways to do this. But I dont know of them, and since you seemed to be in a hurry, i just wanted to post this as a possible solution that *might* work, if you are desperate ;)

Again, dont trust me.

Good luck!

---

### Post by fletch331360 on 2006-02-02
i am desperate but i agree with your statement that is probably an easier way and hopefully someone will read this and have an easy answer.

fyi- i tried your suggestion and the  > chmod -R /home/<your username> 755  gave me  > invalid mode string: '/home/sean'

i cant believe i did this and  i have now lost almost an entire day of work. i have to fix this by tomorrow.

thanks for your help and anyone else that can get me thru this

---

### Post by krusbjorn on 2006-02-02
The invalid mode string is because 755 is supposed to be BEFORE the directory, for example:

chmod -R 755 /home/sean

Sorry, mistake from my side. Edited the post above if you decide to do it anyway later.

---

### Post by fletch331360 on 2006-02-02
[QUOTE=krusbjorn]The invalid mode string is because 755 is supposed to be BEFORE the directory, for example:

chmod -R 755 /home/sean[/QUOTE]

ok i followed your directions 


> chown -R root:root /directory (replace "directory" with "etc", "apt", "usr" etc etc)

but i only did the ones you mentioned here because i didnt know what the etc.. are

i am now able to login and i am able to get to my evolution \\:D/   but when i try to configure my network connection because it wont log into my network i get 

> Failed to run network-admin as user root:
Child terminated with 1 status

i can at least open evolution now and if i really messed thigs up i could at the least save my emails and contacts and reinstall

maybe if i just " chown -R " the rest of the etc... you were talking about i would be ok though.

is the etc... you are talking about all the folders in my File System folder?

i cant thank you enough for your help so far

---

### Post by krusbjorn on 2006-02-02
Great!

Type "cd /". That means you go to the "root directory", meaning top of the catalogue structure. Then type "ls" and you will get a list of directories. Those directories are what "etc etc etc" meant in my post.

On my installation (which probably is more or less identical to yours, these are:
bin
boot
debootstrap
dev
etc
initrd
lib
media
mnt
opt
proc
root
sbin
srv
sys
tmp
usr
var

But perhaps you should let it be now that it almsot works ;)

---

### Post by fletch331360 on 2006-02-02
[QUOTE=krusbjorn]Great!

Type "cd /". That means you go to the "root directory", meaning top of the catalogue structure. Then type "ls" and you will get a list of directories. Those directories are what "etc etc etc" meant in my post.

On my installation (which probably is more or less identical to yours, these are:
bin
boot
debootstrap
dev
etc
initrd
lib
media
mnt
opt
proc
root
sbin
srv
sys
tmp
usr
var

But perhaps you should let it be now that it almsot works ;)[/QUOTE]


well iwent thru all of them and media and proc would not work but the rest went thru fine.

however it did not change the fact that i cant get to my network settings or sound card or a lot of other stuff. i can though get my email and contacts so thank you very much and i am just going to flush the whole computer. it probably needed it anyway :mrgreen:

---

### Post by krusbjorn on 2006-02-02
Haha, okay. Well, glad you got ahold of your files before nuking the hard drive anyways :D

---

### Post by art on 2006-02-02
Just before you flush the computer and have got all your emails copied maybe first try rebooting and see if after that you can get network working. Otherwise you can always reinstall.

---

### Post by fletch331360 on 2006-02-02
i will try that this evening. 

thanks

---

