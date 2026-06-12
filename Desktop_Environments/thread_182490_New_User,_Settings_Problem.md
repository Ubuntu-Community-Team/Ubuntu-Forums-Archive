---
title: "New User, Settings Problem"
date: 2006-05-26
forum: Desktop Environments
---

### Post by atomic16 on 2006-05-26
So after burning over 15 discs, trying 10 distros I finally got kubuntu to work on my computer. Now there is a problem, I setup a root pasword in the setup, now when I finally load kubuntu up I have a problem. I can not change ANY settings, why? well because the computer won't let me, when I click on the administrator it loads the dialog with a red box around it then an error comes up with soming about SU, which means nothing to me. Now on top it says somthing about the root login. I understan d it is dangerous to use a root login and I really have no idea what Im doing so I would like no to. Can someone please give me instructions on how to correct this. If I do need to use a root login I can do it, just give me detailed instructions please. Thanks.
I have a gateway profile 2, i686 (I think) and Im using 5.1 (I think).

---

### Post by Jucato on 2006-05-26
Can you post the specific error messages that you get, if it isn't too much.

Regarding the root account: In Ubuntu, the root account is disabled, in favor of using *sudo* (or for graphical interface/apps, kdesu for KDE, and gksudo for GNOME). When you created the first user during installation, the password that you gave it will be the password that Kubuntu will ask you to enter whenever it requires root/administrator privileges. For more info, try reading the wiki page:
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

(Btw, you are using Kubuntu 5.10, that's 5 for 2005, and 10 for October :D)

---

### Post by atomic16 on 2006-05-26
ok I have to boot up the computer, that takes a while. I will post the error.

---

### Post by atomic16 on 2006-05-26
OK when I click on Date and time for example it says changes in this section require root access
click the administrator mode button to allow modifactions
I click it
then a read line out lines the dialog and an error comes up
the top reads Error-KDE su
su returned with an error
not much there

---

### Post by Jucato on 2006-05-26
Hmm.. it seems that you are having a problem with the either the su program itself or the kdesud program (KDE su). 

Some questions:
1. Is this a fresh install of Kubuntu? If yes, were there any problems that you encountered when you installed it?
2. does this only happen with the time/date program? how about other things that would require administrator privileges?
3. if you could open up a terminal (look for Konsole in the K Menu), try typing this and see if you get any errors. If you do, take note of them. (Error message, no matter how cryptic, are sometimes helpful, specially if you Google for them).
```
kdesu systemsettings
```

You could also try searching in the forums for help using the search function and entering keywords like: Error KDE su, or something like that. (In fact, you could also try Googling for it).

---

### Post by atomic16 on 2006-05-26
[QUOTE=Fenyx]Hmm.. it seems that you are having a problem with the either the su program itself or the kdesud program (KDE su). 

Some questions:
1. Is this a fresh install of Kubuntu? If yes, were there any problems that you encountered when you installed it?
2. does this only happen with the time/date program? how about other things that would require administrator privileges?
3. if you could open up a terminal (look for Konsole in the K Menu), try typing this and see if you get any errors. If you do, take note of them. (Error message, no matter how cryptic, are sometimes helpful, specially if you Google for them).
```
kdesu systemsettings
```

You could also try searching in the forums for help using the search function and entering keywords like: Error KDE su, or something like that. (In fact, you could also try Googling for it).[/QUOTE]


Yes I just finished installing, and the first run at intalling it it failed, I then used expert mode and it worked.
No every setting besides the desktop and certain other things don't require the admin
That code comes up with the same error.
I have searched for it already, nothing came up, but let me try again.
This looks like it might help [http://docs.kde.org/stable/en/kdebase/kdesu/kdesu.pdf](http://docs.kde.org/stable/en/kdebase/kdesu/kdesu.pdf)
I tried reading but this stuff is still new to me.

---

### Post by Jucato on 2006-05-26
I'm not sure but it the problem might be that you made an expert install rather than the normal one. The expert install creates a root account separate from the normal user account, while the normal install doesn't, in line with Ubuntu's "no root account" principles (see the link I gave above). That might be causing the problem.

Try doing a search, this time using the words: ubuntu, expert, install, kde, su. (in whatever combination/order you prefer). Might turn up something.

---

### Post by atomic16 on 2006-05-26
Hm, can I re create the root acount?
Some results
This is almost my exact problem: [http://www.ubuntuforums.org/archive/index.php/t-75114.html](http://www.ubuntuforums.org/archive/index.php/t-75114.html) I cant seem to find many others.

---

### Post by Jucato on 2006-05-26
some "workarounds" I've found so far (from Ubuntuforums/Google).

1. To change some settings that require administrative privileges, run "kdesu kcontrol" and give the root password you created (rather than running normal kcontrol/system settings and clicking the Administrator Mode).
2. Update KDE: the default install is KDE 3.4.3, the latest is 3.5.2
3. Reinstall kcontrol: uninstall it, then reinstall it (note that this will uninstall a package called kubuntu-desktop, but you can safely reinstall it again with no problems).
4. enable root account.

Only do #4 if you are really sure that you want a root account and you know what you are doing. The expert install creates a root account, so you're one step there already. But if you don't know what you are doing, you can try doing a normal install. 

To enable root account, follow the instructions on the wiki page I linked to. There are instructions there. Good luck! (try searching again in the forums. I seem to have hit some searches using the keywords expert, error, kde, and su.)

---

### Post by atomic16 on 2006-05-26
where can I dowload updates, currently the computer has no internet connection so I will need to burn it. Thanks for all your help.

---

### Post by Jucato on 2006-05-26
Tricky question. It would be hard to do an offline update of KDE since there might be many packages and dependencies to resolve and merely downloading the files might create more problems than solve them.

Do you have an alternate internet connection? If you do, I'd like to suggest that you download the official Release Candidate for the next version of Kubuntu. The next version is scheduled to be released on June 1st (hopefully). The Release Candidate is practically stable and is updated. Here's the link:
[https://lists.ubuntu.com/archives/ubuntu-announce/2006-May/000081.html](https://lists.ubuntu.com/archives/ubuntu-announce/2006-May/000081.html)
The link to the Kubuntu downloads are near the middle-bottom.

If you really can't, then why don't you try the other alternatives I wrote. Also try searching the forums again. I might have missed out on something.

Or maybe you could try reinstalling using the normal install method? It doesn't take as long as installing XP. :D Btw, what problem did you encounter during the first normal install that you did?

If this is your first time to use Kubuntu/Ubuntu, I'm sorry that it has not been that pleasant. I'm not sure if it's really a bug or something, but if it is, it should have been fixed.

---

### Post by atomic16 on 2006-05-26
If I do Kdesu Kcontrol I get the same error again.

---

### Post by Jucato on 2006-05-26
Argh, I'm utterly clueless now on what to do. Do you get the same error message when you run kdesu kcontrol? It might be a su problem after all. 

Try uninstall/reinstall kcontrol. If that still doesn't work, I guess you could try enabling the root account. ([http://wiki.ubuntu.com/RootSudo)](http://wiki.ubuntu.com/RootSudo)). 

You can also have a look at this thread. It seems that the problem is similar to yours (?) [http://www.ubuntuforums.org/showthread.php?t=75114](http://www.ubuntuforums.org/showthread.php?t=75114)

If all else fails, I suggest you could also try the official release candidate I was talking about. 

(Btw, I forgot to mention this. Since you are using Kubuntu, you could also try asking for help at [KubuntuForums.Net]("http://www.kubuntuforums.net/forums"). It's also a forum that caters to Ubuntu users, focusing on Kubuntu/KDE. They might be able to help. Sorry if it's all that I could do. :( )

---

### Post by kko1 on 2006-05-26
Hello.

NOTE: A correction to the instructions added.

[QUOTE=atomic16]Yes I just finished installing, and the first run at intalling it it failed, I then used _expert mode_ and it worked.

I setup a root pasword in the setup[/QUOTE]

I'd like to bump in and try to offer a solution. Your problems stem from the fact that you have installed in expert mode. This means, as I understand it, two things:
- You have the root account enabled.
- _And_ you have the sudo access disabled.

To correct the situation, you only have to change some settings to what they would be, had you done the "default" install. Now, I hope you didn't already do a re-install, for then I would be writing this in vain. ;) If my instructions are too simple, I hope you don't mind. Better to be on the safe side.

First, you need to add yourself to the file */etc/sudoers*. To do this, do:

1. Open up a console, for instance by starting "Konsole".

2. Write "su" (without the quotes), and press return. Provide your _root_ password. You should now be logged in as root. [SIZE="1"](To check this, you can look at the "prompt", i.e. the thing at the start of the command line. If it ends with a "#", you are root, if it ends with a "$", you are a user.)[/SIZE]

[SIZE="1"]Alternatively for phases 1&2, you could go to a "Virtual Terminal" by pressing "Ctrl-Alt-F1" and simply login as root. (You can get back to X/KDE by pressing "Ctrl-Alt-F7".)[/SIZE]

3. Write "nano /etc/group" and press return. You are now editing the file in a text-editor called "nano". Locate the line that begins with "adm" (or "admin"). Add _your username_ to the end of this line, after the ":" sign. It should read like this: ```
"adm:x:4:yourusername".
```

(_Do not change the number_, it is the group's group number. At least there should never be two groups with the same number.)

4. Save the file. In nano, you do this by pressing "Ctrl-X" - it will ask you if you want to save it.

Now, to why we came here in the first place. :p 

5. Write "nano /etc/sudoers". [SIZE="1"]Actually, we should be using "visudo", but since "nano" is more new-user-friendly than "vim", and since I have no way to tell which editor is default for you (I suspect "vim"), we'll do it with "nano".[/SIZE]

You are now editing the file. You should make these sections near the end of the file look like this:

```
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
%adm    ALL=(ALL) ALL
```

_Be careful with the editing - if this file contains errors, sudo will refuse to work. Also note the "%" -sign before "adm"._ It means that all users in the group adm are included.

Save the file and exit the editor.

7. Write "exit" (and press return;)), to exit root mode. [SIZE="2"](Your prompt should again end with "$".)[/SIZE]

_At this point, you should have sudo-rights._ (In KDE, if you start graphical "sudo" programs, you should use "kdesu" instead of "sudo".)



Now, some final clean-up. Removing the "root" user's password from use, which means disabling the root account. 8) 


There is a command for this, but unfortunately there is a bug in Breezy that causes me to recommend you do it by directly editing the file. Do this:
```
sudo nano /etc/shadow
```
Now, provide your _user_ password, as always with sudo. This is also where we test that "sudo" actually works. _If it doesn't work for you yet, don't do the following step, because that will disable your root account._

The first line says something like:
```
root:$1$NrIi8sZK$onjJTOLZcRjTpLMJHCx3M.:13294:0:99999:7:::
```
Replace the load of symbols after "root:" and before ":13294:" [SIZE="1"](the number may be different)[/SIZE] with "*", without the quotes. (For why we do this, see [https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/18937](https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/18937) .) _Do not remove the ":" -signs, and do not touch anything else in the file._

Save the file and exit.

Now, you should be clear to use the system, and can do system maintenance as explained in [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) .

Hope this was of any use to you, and as always, please report back to tell if (and preferably how) you've managed to solve your problem.

kko

---

### Post by kko1 on 2006-05-29
[QUOTE=atomic16]So after burning over 15 discs, trying 10 distros I finally got kubuntu to work on my computer.[/QUOTE]

Bah. This guy was probably up to his 20th distro before I even saw his problem - a few hours later, that is - why did I bother... :mad: 

Well, here's to hoping that the info provided eventually ends up helping someone. ;) 

kko

---

### Post by atomic16 on 2006-05-29
unfortunatly you were to late, I already installed 6.06 which worked perfectly until I started getting disc errors. Im just going to wait until I get my shipit CDs, then I can do a normal install and it will work.

---

### Post by Jucato on 2006-05-29
What disc errors are you getting?

---

### Post by atomic16 on 2006-05-29
Nodes missing, Bad sectors, I use Fsck, I restarted, I did everything. No Luck. thankfully my Shipit CDs will be here in a few days. This all started becuase everytime I burned ubuntu or kubuntu the normall install was corrupt.

---

### Post by Jucato on 2006-05-29
Does this only happen in Ubuntu/Kubuntu, and not in other distros that you have tried? It could be possible that your hard drive might be having some problems.

Also, do you check the md5sum of the ISO's you downloaded, just to make sure that the ISO itself wasn't corrupted during the download. Sometimes, errors in installation can be caused by corrupted ISO's. Bad burns could also be a factor (I take the extra precaution to verify burns always).

Well hopefully you receive your shipit CD soon. I think I'll have to wait for almost a month for them. I ordered anyway so I could give beautiful copies around. :D

---

