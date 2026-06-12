---
title: "Users: root"
date: 2006-01-04
forum: Desktop Environments
---

### Post by tatacalu on 2006-01-04
Hi there!

I have a big problem: i cannot login with root username. It says that username/password incorrect.

I logged in with my administrator account, I changed the password for the root user, but still nothing... I just can't log in.

Any suggestions? Should I reinstall Ubuntu ? :confused: 

Thanks

---

### Post by Juergen on 2006-01-04
> Any suggestions? Should I reinstall Ubuntu ?
You shouldn't (have tried to) change the root-pwd. (I don't know what went wrong, though)

Did you read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) ?

I use Ubuntu from nearly day 1, and so far never needed to login as root!
If you really want a longer lasting session as root in an xterm, you can always do a 'sudo -s'

---

### Post by tatacalu on 2006-01-04
Well, the thing is that I need to login as root because the system doesn't allow me to browse my NTFS partitions on the hard-drive (I also have installed WinXP). When I try to browse one of the NTFS partitions it just says that I don't have access to it without asking me a password, and I'm fed up with browsing from the Hard Drives option from the Administration menu or sth like that.

For example in xmms I can't add a dir from those partitions because it won't browse them.

Another problem was that I couldn't compile a package because the console said that I don't have full rights or sth like that.....

any ideas ?

---

### Post by tatacalu on 2006-01-04
I suppose that I should enable the root user support....
> sudo passwd root - i should type "passwd" or umm.. the administrator password ?

---

### Post by escape on 2006-01-04
^^^ Yes, you would just want to use passwd. The passwd file contains a list of users on the computer, and as a command I believe it adds users.

---

### Post by aysiu on 2006-01-04
[QUOTE=tatacalu]Well, the thing is that I need to login as root because the system doesn't allow me to browse my NTFS partitions on the hard-drive (I also have installed WinXP). When I try to browse one of the NTFS partitions it just says that I don't have access to it without asking me a password, and I'm fed up with browsing from the Hard Drives option from the Administration menu or sth like that.[/QUOTE] See the fourth link of my sig.

If, for some reason, that seems too complicated, press Alt-F2 and type ```
gksudo nautilus
``` It's easier and faster than logging out, logging in as root, logging out again, and logging in as user again.

---

### Post by Juergen on 2006-01-04
>  sudo passwd root
This asks for the **new** root password, input will be hidden.

And for browsing your windows partitions, you should alter your fstab-entry for that partition (with sudo ;-) ), so that users have access.
I don't have a link at hand, but I'm sure there is an entry in the wiki for this.

For compiling you usually don't need to be root.
Only for the last step, the install. And that should then work with
```
sudo make install
```

If you really want to go the root-way, so do.
But it's really easy to go without...

---

### Post by tatacalu on 2006-01-04
Thank you for your help, i managed to solve the problem: now I can lo gon as the ROOT user! :KS

But, the final question is: How do I set in System->Administration->Login Screen Setup in the General tab the automatic login username as **root** ? In that drop-down box I only see the administrator username (the only user I created [at the installation]).

---

### Post by tatacalu on 2006-01-05
Anyone ? Any idea would be welcomed !!! :???:

---

### Post by mcduck on 2006-01-05
[QUOTE=tatacalu]Anyone ? Any idea would be welcomed !!! :???:[/QUOTE]
you really shouldn't do that. It will completely ruin your system's security. Running as root is bad, automatic login to root and running always as root is even worse.

I've been running Ubuntu for over 10 months now, and I've never found any good reason to even enable the root account.

---

### Post by PlatinumPlus on 2006-01-05
I am getting 

Conversation with su failed 

when I try to change the Date and Time. My Synaptic Package Manager is not running but it was running when I was using the Live CD. apt-get is working though. Update Manager just gets the mouse pointer 'dancing' then nothing, no message, no error nothing.

At times it says my root password is incorrect but I can use it at the console when I type su.

Is this normal?

---

### Post by aysiu on 2006-01-05
See the third link of my sig or the sixth post in this thread.
There's absolutely no reason you need to log in as root.

---

### Post by tatacalu on 2006-01-05
I gave you a reason earlier:
My NTFS partitions have shortcuts on the desktop: **hda1** and **hda6**. Whan I try to access them I get the message that I don't have the permission to do that. It doesn't even ask me for a password! Just denies my access.
:???: 

You say that logging in as root is bad for the security... hmm... from which point of view? I am the only user of my computer.

---

### Post by pieboy314 on 2006-01-05
[QUOTE=aysiu]See the third link of my sig or the sixth post in this thread.
There's absolutely no reason you need to log in as root.[/QUOTE]

I need to log in as root to follow these instructions...

> “Could not look up Internet address for %machinename, this will prevent Gnome from working correctly. It may be possible to correct the problem by adding %machinename to the file /etc/hosts.”
[Log in anyway?] or [Try again].

The error message is displayed after the user has entered their password and before the GNOME GUI finishes loading. Should you wish to deal with the problem the solution is offered in the message. If you are not a Linux newbie your course of action is obvious. If you are a Linux newbie, read on...

SOLUTION
Open a Terminal window in Gnome and become root.
Issue the following commands:

# cp /etc/hosts /etc/hosts.fc1setup
# vi /etc/hosts

In the vi editor type “a” to go into insert mode. After the current last line of the file add the line:

127.0.0.1 %machinename
(Remember to replace %machinename with the name of your system.)

Type [Esc] ZZ to save the file and exit.
Close the Terminal window.

since I get this error. any other ideas?? 

**complete newbie here :rolleyes:

---

### Post by pieboy314 on 2006-01-05
found another fix for the same problem, but it also requires me to log in as root

:( 

[http://ubuntuforums.org/showthread.php?t=60695&highlight=prevent+Gnome+working](http://ubuntuforums.org/showthread.php?t=60695&highlight=prevent+Gnome+working)

---

### Post by briancurtin on 2006-01-05
use sudo

sudo cp /etc/hosts /etc/hosts.fc1setup
sudo vi /etc/hosts

you do not need to be root, as said before. [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by pieboy314 on 2006-01-05
thanks... I read RootSudo, now I understand my root problem...

this is not working for me. I am guessing that I do not run these commands in a terminal...? arrg, such a newb again

billpayer@:~$ sudo cp /etc/hosts /etc/hosts.fc1setup
sudo: unable to lookup  via gethostbyname()
billpayer@:~$ sudo vi /etc/hosts
sudo: unable to lookup  via gethostbyname()
billpayer@:~$

---

### Post by briancurtin on 2006-01-05
no you actually did it right, but i dont know anything about the "gethostbyname()" problem you had.

---

### Post by hillbilly on 2006-01-05
[QUOTE=tatacalu]I gave you a reason earlier:
My NTFS partitions have shortcuts on the desktop: **hda1** and **hda6**. Whan I try to access them I get the message that I don't have the permission to do that. It doesn't even ask me for a password! Just denies my access.
:???: 

You say that logging in as root is bad for the security... hmm... from which point of view? I am the only user of my computer.[/QUOTE]


Its actually for protection from yourself. When you are root, you can unknowingly and needlessly modify files which you shouldnt. Now if you were not logged in as root, then you would get prompted for the passwd, meaning you are getting "pinged" that you are doing some system-centric task and you should be on your toes ;) !!

And as for not being able to access your mounted windows partition unless you are root, my guess is that you have not mounted them with the proper options. Check fstab.
you should have an entery similar to the one below
```

/dev/hda7            /mnt/Win/C            ntfs    ro,user,auto    0       0

```

In coloumns 5, user means any ordinary user can use it. If you change it to "users" it wont work and only root can access the mounted filesystem.

---

### Post by ysse on 2006-01-05
[QUOTE=tatacalu]I gave you a reason earlier:
My NTFS partitions have shortcuts on the desktop: **hda1** and **hda6**. Whan I try to access them I get the message that I don't have the permission to do that. It doesn't even ask me for a password! Just denies my access.
:???: [/QUOTE]
Ubuntu installation gets the permissions a bit wrong for NTFS partitions. I had the same problem as you at first. The solution is to change how the NTFS partitions are mounted. The file /etc/fstab says what file systems are mounted by default. You could use ```
sudo gedit /etc/fstab
``` to change it.

Then you change the lines for /dev/hda1 and /dev/hda6 to be like
```
/dev/hda1       /windows/C      ntfs    nls=utf8,umask=0222      0       0
```
Your mount points will likely be different from mine (/windows/C). The important part is the umask=0222.

[QUOTE=tatacalu]You say that logging in as root is bad for the security... hmm... from which point of view? I am the only user of my computer.[/QUOTE]
There are many reasons not to use root. The account that every hacker tries to target is root. On a computer with an enabled root account, a hacker only has to get  the password right, and then everything is wide open. Without root, a hacker also has to find out which username to attack, which might make it an order of magnitude harder. 

Using sudo, you only have full privileges while you need them, and not when you are tired and make a stupid mistake.

---

### Post by ysse on 2006-01-05
Beat me to it, hillbilly!

---

### Post by pieboy314 on 2006-01-05
[QUOTE=briancurtin]no you actually did it right, but i dont know anything about the "gethostbyname()" problem you had.[/QUOTE]

oh oh... I think that the "gethostbyname()" problem is caused by my bad hosts file, however I get permission errors when I try to correct the host file, which leads me to believe I will need to change it via sudo method.. which of course leads me back to my problem...

I beleive they call it a "catch-22"

any suggestions? ???

---

### Post by GeneralZod on 2006-01-05
[QUOTE=pieboy314]oh oh... I think that the "gethostbyname()" problem is caused by my bad hosts file, however I get permission errors when I try to correct the host file, which leads me to believe I will need to change it via sudo method.. which of course leads me back to my problem...

I beleive they call it a "catch-22"

any suggestions? ???[/QUOTE]

That's awkward :) If you have a live CD such as Knoppix (or one of the (K)Ubuntu ones!) it's relatively easy to fix; otherwise, simply rebooting into safe mode (I forget exactly what it's called on the grub menu - "failsafe" perhaps, or "recovery mode") will dump you straight into a root shell where you should be able to make the change.  Good luck!

---

### Post by hillbilly on 2006-01-05
[QUOTE=pieboy314]oh oh... I think that the "gethostbyname()" problem is caused by my bad hosts file, however I get permission errors when I try to correct the host file, which leads me to believe I will need to change it via sudo method.. which of course leads me back to my problem...

I beleive they call it a "catch-22"

any suggestions? ???[/QUOTE]


Check out this thread [http://ubuntuforums.org/showthread.php?t=112939&highlight=gethostbyname](http://ubuntuforums.org/showthread.php?t=112939&highlight=gethostbyname)

I believe the person had the same problem as you are having.

---

### Post by pieboy314 on 2006-01-05
> **GeneralZod]That's awkward :) If you have a live CD such as Knoppix (or one of the (K)Ubuntu ones!) it's relatively easy to fix said:**
> 

I have a few live CD such as Ubuntu & SuSe, being a newbie I am not sure what to do to fix the problem upon booting up with them, but purhapse if I try it later,  it will come to me.

[QUOTE=hillbilly]Check out this thread [http://ubuntuforums.org/showthread.php?t=112939&highlight=gethostbyname](http://ubuntuforums.org/showthread.php?t=112939&highlight=gethostbyname)

I believe the person had the same problem as you are having.

yep, I think that dude has the same problem, I am not sure that he resolved it either, but I will try to deciper that thread futher

being a newbie to Linux this is all extra taxing naturally, but it is nice to be challanged again. ;) 

a co-worker tells me that there should be a vi command to overwrite the hosts file under my default login? ???

---

### Post by hillbilly on 2006-01-05
[QUOTE=pieboy314]
a co-worker tells me that there should be a vi command to overwrite the hosts file under my default login? ???[/QUOTE]

Why dont you try what General Zod says. If you are able to login through failsafe or recovery mode (chosing the appropriate OS options from grub menu) and if you are in a root shell, then all you have to do is "vi /etc/hosts" and fix it. It looks like the easiest option.

And as far as an option using vi from your regular login, I personally dont think its possible, but I dont know for sure. Or maybe your co worker meant using "sudo vi  " ;) !!

---

### Post by pieboy314 on 2006-01-05
[QUOTE=hillbilly]Why dont you try what General Zod says. If you are able to login through failsafe or recovery mode (chosing the appropriate OS options from grub menu) and if you are in a root shell, then all you have to do is "vi /etc/hosts" and fix it. It looks like the easiest option.[/QUOTE]

when I boot in failsafe the terminal window is the same as under a normal boot, still prompts me for my username and password and still do not have permission to change /etc/hosts ...... :mad:

---

### Post by PlatinumPlus on 2006-01-06
[QUOTE=aysiu]See the third link of my sig or the sixth post in this thread.
There's absolutely no reason you need to log in as root.[/QUOTE]

Cool. I it's all starting to make sense now :KS

---

### Post by pieboy314 on 2006-01-06
just FYI for anyone who might be following my problem along this thread, I did get a root terminal via the grub menu (option shortly after the bios login and before the graphical boot) and I changed my /etc/hosts file.... but it did not help either of my issues. :( 

I will re-install. (the bonus of playing on a non-crital machine)

---

