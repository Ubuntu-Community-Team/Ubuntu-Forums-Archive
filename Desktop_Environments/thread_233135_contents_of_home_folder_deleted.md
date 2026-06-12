---
title: "contents of home folder deleted"
date: 2006-08-09
forum: Desktop Environments
---

### Post by maniacmusician on 2006-08-09
hey guys,

I think I did something really stupid. I noticed that everytime I ran synaptic and installed stuff, right before installing, it would say "Unable to load gnome frontend. Is libgnome2-perl installed?" (I'm running Xubuntu. 

sooo I decided to install libgnome2-perl to see if it would make the error message go away. Well, after I did that, my xfce session started slowing down more and more until it came to a dead halt and only the mouse would move. So, I restarted X and attempted to log back into XFCE. It gave me an error saying that my $HOME/.dmrc was being ignored (it says that without it, saved sessions and language can't be loaded. also that the home directory should be owned by the user and not writeable by other users) and in a few seconds it reported that /home/user/.ICEAuthority was also missing. So it wouldnt let me start XFCE amd brought me back to GDM. I started a failsafe xterm session and removed libgnome2-perl and the other two packages it made me install (libgnome2-canvas-perl and libgnome2-vfs-perl). I still couldn't log in. I checked my /home/user folder and everything was gone! ls and dir wouldnt give me any output. 

Right now I am installing kubuntu in the hopes that I might be able to use that to log in, but I doubt it as it seems that my entire home folder has vanished. Is this fixable or will I end up reinstalling Xubuntu? (mind you, I only installed it last night anyways. but I already had ssh and nfs set up, and installed a lot of programs as well. so I really really dont want to reinstall).

oh, kubuntu finished installing; same error.

---

### Post by mg3kc on 2006-08-09
err... you could finish what you started doing, which seems to be moving to the Gnome frontend.
sudo apt-get install ubuntu-desktop
-or-
sudo apt-get install xubuntu-desktop 
may help reinstalling xubuntu without having to reinstall your whole system?

---

### Post by maniacmusician on 2006-08-09
I wasn't really trying to move to gnome, it just kept giving me that error. i installed the libs to make it go away...but nothing to lose on that front though, so I'll try it. thanks.

---

### Post by maniacmusician on 2006-08-09
uhh actually, i don't see an apt-get option for reinstall....do i have to remove it and then install it? lol, this blows.

---

### Post by tzulberti on 2006-08-09
You could create another usear, and change the owner of the files (chwon userName files) and copy the files from a home to another...

Take care because there are to commands for adding users: adduser and useradd, but only one of them create the home files.

---

### Post by tzulberti on 2006-08-09
If the user does not have any important file, you could remove it and add it again...

---

### Post by maniacmusician on 2006-08-09
well, there's all my config files (ie, the files for opera would be in .opera). i'll consider that as a last resort. how do you remove a user?

also, the problem is, I think all my files might have just been deleted when the computer crashed. a couple more questions:

is there a way to use chwon recursively so it applies to all files and subfolders? 

and which one of the commands creates the home files? adduser or useradd?

thanks.

---

### Post by maniacmusician on 2006-08-09
i've installed 3 desktops but still nothing. it doesn't let me use chwon either. is there a package i need to install to be able to use it?

maybe i should post the exact error message:

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

then a few seconds after i click OK, another window pops up:

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be running out of diskspace (*I have plenty of diskspace left*). Try logging in with one of the failsafe sessions to see if you can fix this problem.
This window also has "details" in the form of an ~/.xsession-errors file:

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l :0" "maniacmusician"
/etc/gdm/Xsession: Beginning session setup
trying to create local folder /home/maniacmusician/,kde: No such file or directory
trying to create local folder /home/maniacmusician/,kde: No such file or directory
trying to create local folder /home/maniacmusician/,kde: No such file or directory
/usr/bin/startxfce4: X server already running on display :0
xfce4-session: Unable to access file /home/maniacmusician/.ICEauthority: No such file or directory

I should probably add that I am not totally confident that it was the libgnome2 files that caused the problem; that was just my educated guess. At the time this happened, I was also trying to setup a NFS server. I believe the last command I entered was "sudo /etc/init.d/nfs-kernel-server restart" and that seems like a pretty harmless command. i've been thinking about it so much that i'm not even sure if I installed the libgnome2 files before or after i typed that...but those two things were definitely my last acts before it froze up and crashed.

any help would be appreciated, thanks.

---

### Post by maniacmusician on 2006-08-09
alright, guys...here I am, poised on the edge of a big decision. I am right now running the Xubuntu live CD on the damaged computer and getting on the internet from there. I'm debating reinstalling Xubuntu completely, since it seems like all my settings have been wiped; the ssh server i set up, settings for my web browser, all my files, everything. Before i go ahead and jump into the reinstallation, do any of you know of a way to recover deleted files? Forensic detectives use tools frequently to recover deleted files, and i'm sure linux has a few of these handy. If at all possible, I want to get those files back, and bypass the hassle of setting everything up again.

thanks

---

### Post by maniacmusician on 2006-08-09
update: In the live CD environment, i used disks-admin to remount hda1. the files are all still there! why the hell could I not see them when xubuntu boots as normal? 

Anyways, the permissions for my entire home folder are ****** up. it says the owner of the entire folder is 1000. so i tried:

sudo chown maniacmusician /home/maniacmusician

and it told me that maniacmusician is an invalid user. so only a username from the live CD environment can be entered, and the only one is ubuntu. I considered creating a maniacmusician in this environment and then using chown, but I doubt that would work; the dynamics of the user would still be different, because maniacmusician on the hard drive installation is the admin, main user, and all the details wouldn't match up. I'm hoping that the info for the users on my hard drive installation are somewhere on that hard drive and i can somehow export that user here and give him ownership of the folder. But i have no clue how to do that.

Can anyone help me restore the right permissions? Please?? 

Remember, I'm in a live CD environment with hda1 mounted on my desktop. Thanks a bunch

---

### Post by Dr. Nick on 2006-08-10
cool the files are still thier, I really wish I knew this for sure, but Ill explain my logic, Its up to you if youd like to try it

I dont see why making a user on the live cd that is the same as your installed enviro wouldnt work. I know what you mean with the live cd user not having sudo, but I believe that the sudoer file is stored outside of your home folder so it may not matter.

Just curious if you are able to change permissionson the mounted hda1 using the live cd? If you navigate to your hda1 home folder in nautilus from the live cd, can you right click to properties and change permsiions that way? if so you may just set it to where everyone could read it so you might be able to see if when booting off the hd, then once on the hd fix the permissions. Just a idea

I really dont know anything for sure on that, I really need to study permissions in general. Im just glad your files are still their, even if they are hard to access,

Good luck

---

### Post by maniacmusician on 2006-08-10
yes i'm glad they're there too.

when i run thunar with gksu, i can change the permissions, but I can't change the owner. 

the reason I think it won't work to create another user with the same name is that there are a bunch of sub-attributes to a user...such as group, real name, and probably a lot of hidden ones. if any of them vary, it might throw everything off. 

I feel a little shaky about even this little thing, but i will try your suggestion and change all permissions to read/write and see if it boots properly. i'll let you know how it goes. if it fails i'll have to set up the live CD again and enable wireless with ndiswrapper and come back to the forums for more help.

thanks.

---

### Post by maniacmusician on 2006-08-10
nope, that did not work...i suspect because the error message also stated that the owner of a user's folder must be that user and nobody else can be allowed to access it. so i'm back to where I was before

i'm sure someone knows how to fix this...like maybe the godly Ubuntu devs. they should frequent the forums more often lol.

---

### Post by maniacmusician on 2006-08-10
I have come up with another solution...I'm going to make the owner of the folder root, and give the group user read/write access. 

sudo chown root -R ~/Desktop/hda/home/maniacmusician

the -R is for recursiveness. and as for making the group user, I did that through thunar. My reasons for doing this; user encompasses all the users in a group, including the one I created. I suspect it still won't work because *only* maniacmusician is supposed to be able to access it, but i'm definitely willing to try it. if it doesn't work, I will try creating a user called maniacmusician here as a last resort.

---

### Post by kerry_s on 2006-08-10
Try> sudo chmod 644 /home/(your name)

---

### Post by maniacmusician on 2006-08-10
yes, i tried that too. no go. i've tried pretty much everything. I even created a user with the same name and set the ownership right and everything but this seems to get erased. so i'm on the live cd setup again and the ownership of my home folder is back to 1000 (even though i changed it last time). I think the reason for this is that the user maniacmusician doesn't exist on the live cd setup, and it can't display an owner that doesnt exist on the machine. it is worthy of notice that when someone goes to create a new user, the first userid available is 1000. so I think that it is just substituting maniacmusician with 1000 because it does not recognize the username.

so what i'm thinking is that the problem actually lies outside the home folder. something happened that made my hard drive installation ignore my home folder. unfortunately I have no idea how to do this. 

an idea that I do have: copy the contents of my home folder to another location on the computer, and when i reboot in failsafe terminal, to copy those back to my home folder. do you think this is a good idea or could it just cause more problems? I say this because if those files really do exist there, would i be causing trouble by trying to overwrite them? 

so yeah. good idea or not?

---

### Post by Dr. Nick on 2006-08-10
What you could do is copy them to another location just to be safe, I imagine if you tried to copy them back it would overwrite them with the new permissions set by copyting them in the first place.

Hope you get it all straightned out

---

### Post by maniacmusician on 2006-08-10
thanks. anyone else got any suggestions? I would've thought at least that it would generate some interest from the expert users since its just so odd. i'll try the copying thing later today. I didn't sleep all night so i just might settle in for a nap.

---

### Post by pksings on 2006-08-10
go to command line, this is a quicky command line permission tutorial

permissions have three groups 
owner group and other. 

permssions are divided up this way rwx rwx rwx, (read, write, executable) 
for each in the previously stated order. There are octal (funky math) settings for each that can be managed using the chmod command. (change mode)

the values that correspond to the rwx are 421, in that order, add up the numbers you need for the permissions you need. 6 means rw (read/writable), 5 means rx (read,executable), 4 means read-only. 

664 means owner is read/write, group is read/write, other is read-only
755 means owner is read/write/execute, group is read,execute, other is read/execute.


So, change the mode of all your files to allow anybody to use them until you get your machine back running correctly.

chmod -R (note, capital R for recursive)

chmod -R 777 /home/whatever/

Whamo, you can do whatever to your files. Just be sure to change them back if you are suitable paranoid after you resurrect your machine.

Hope this helps.

PK

---

### Post by mssever on 2006-08-10
I just came across this thread. Here are my thoughts:

/etc/passwd might have become corrupt. This is where all the username->uid stuff happens. It should contain a line like ```
scott:x:1000:1000:Scott Severance,,,:/home/scott:/bin/bash
``` (with your info, of course).

Similarly, /etc/group should contain a line like```
scott:x:1000:
```

Then, if you boot into recovery mode (from the Grub menu--press Esc when you first boot if you don't see the GRUB menu), you should be able to do ```
chown -R youruser:yourgroup /home/youruser
```

Apologies if you've tried this already.

EDIT: I think that it would be best to do as much as possible from recovery mode (or a failsafe terminal) to avoid conflicts between your install and the live CD. When you're finished with recovery mode, you can either type reboot, or type telinit 5 to go to full (GDM, etc.) mode. To go to recovery mode from full mode, type sudo telinit 1.

EDIT 2: In recovery mode, you're automatically root.

---

### Post by maniacmusician on 2006-08-10
> **pksings said:**
> go to command line, this is a quicky command line permission tutorial

permissions have three groups 
owner group and other. 

permssions are divided up this way rwx rwx rwx, (read, write, executable) 
for each in the previously stated order. There are octal (funky math) settings for each that can be managed using the chmod command. (change mode)

the values that correspond to the rwx are 421, in that order, add up the numbers you need for the permissions you need. 6 means rw (read/writable), 5 means rx (read,executable), 4 means read-only. 

664 means owner is read/write, group is read/write, other is read-only
755 means owner is read/write/execute, group is read,execute, other is read/execute.


So, change the mode of all your files to allow anybody to use them until you get your machine back running correctly.

chmod -R (note, capital R for recursive)

chmod -R 777 /home/whatever/

Whamo, you can do whatever to your files. Just be sure to change them back if you are suitable paranoid after you resurrect your machine.

Hope this helps.

PK

hi,
I have already tries this, it doesn't work. the error that I get states that the folder and the file .dmrc must be owned by the user and the whole folder must not be writable by anyone other than the user. so when i open it up to anybody, it still doenst let me in.

> **mssever said:**
> I just came across this thread. Here are my thoughts:

/etc/passwd might have become corrupt. This is where all the username->uid stuff happens. It should contain a line like ```
scott:x:1000:1000:Scott Severance,,,:/home/scott:/bin/bash
``` (with your info, of course).

Similarly, /etc/group should contain a line like```
scott:x:1000:
```

Then, if you boot into recovery mode (from the Grub menu--press Esc when you first boot if you don't see the GRUB menu), you should be able to do ```
chown -R youruser:yourgroup /home/youruser
```

Apologies if you've tried this already.

EDIT: I think that it would be best to do as much as possible from recovery mode (or a failsafe terminal) to avoid conflicts between your install and the live CD. When you're finished with recovery mode, you can either type reboot, or type telinit 5 to go to full (GDM, etc.) mode. To go to recovery mode from full mode, type sudo telinit 1.

EDIT 2: In recovery mode, you're automatically root.

Thank you for your suggestion; i will go try it right away.

---

### Post by maniacmusician on 2006-08-10
it didn't work...but I discovered that in recovery mode, while logged in as root, I can see my files. So is there a command to enable root login that I can enter in a terminal? then I can log in as root and be able to use X while I try to fix the problem. 

thanks.

---

### Post by mssever on 2006-08-10
To enable root login, you can do ```
passwd -u root
``` and enter a password. However, it's very likely that GDM forbids root logins. I'll do some checking and see what I can learn.

You say that it didn't work. Can you provide some sample output or error messages? Was your /etc/passwd file correct? If so, what did ls -l show after running chown?

---

### Post by mssever on 2006-08-10
To enable root login in GDM, edit /etc/gdm/gdm.conf. Change AllowRoot to true. You might want to do a search, because it's a long file. Also, a few lines down, there's an option CheckDirOwner. If you set it to false, it appears that it will allow you to logon as your normal user. You might also have to play with the RelaxPermissions directive, but I think that your problem is one of file ownership, not permissions.

---

### Post by maniacmusician on 2006-08-11
I just tried what you suggested; no go. even when i enable root login, gdm tells me that i am entering an incorrect username or psswrd. I'm using root and my regular password (it works for sudo so it's also root's password right?). I also tried setting checkdirowner to false and setting relaxpermissions to 1. nothing. Yeah, i agree, it probably is ownership, but i did chown -R maniacmusician /home/maniacmusician with no luck. I think this is bigger than just gdm..

---

### Post by Dr. Nick on 2006-08-11
i believe if you create a root login to gdm you must specify a root passwoord using the passwd command

[http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password)

---

### Post by maniacmusician on 2006-08-11
ah, thank you, i'll try that too.

---

### Post by Dr. Nick on 2006-08-11
oops, see my edit above, i posted a link, thought i posted it 30mins ago, but forgot to save my edit and just came back to this window :rolleyes::rolleyes:

10 FF tabs gets a bit overwhelming lol

---

### Post by mssever on 2006-08-11
Let me make sure I'm understanding you correctly. Do you mean that after booting in recovery mode, checking /etc/passwd and running chown -R youruser:yourgroup /home/youruser that ls -l still gives the owner of files in your home directory as 1000 instead of your username? Please un-confuse me. :)

---

### Post by maniacmusician on 2006-08-11
ls -l just gives a list of files...am i supposed to provide an argument for it?

it only gives 1000 as the owner when I view the permissions tab from the live cd. as I explained earlier, I think the reason for this is 
> 
is that the user maniacmusician doesn't exist on the live cd setup, and it can't display an owner that doesnt exist on the machine. it is worthy of notice that when someone goes to create a new user, the first userid available is 1000. so I think that it is just substituting maniacmusician with 1000 because it does not recognize the username.


I didnt know you wanted me to supply an argument to ls -l. so for example would i use it this way: ls -l /home/maniacmusician  ?

edit: Also, Dr. Nick, your suggestion didnt work. Well, it worked, but didnt end in what I was hoping for. I succesfully set a password but when I go to log in to GDM with root and the new password, this time it says that "The system administrator is not allowed to login from this screen" or something very close to that. I dont understand why as I edited gdm.conf and set AllowRoot to true

---

### Post by Dr. Nick on 2006-08-11
if you want to go into the gui as root you may be able to do it from recovery console. I dont know if it will mess anyhting up, i doubt it would

just boot into the recovery console so you are root then run 

startx 

and see if that works

---

### Post by mssever on 2006-08-11
> **maniacmusician said:**
> So for example would i use it this way: ls -l /home/maniacmusician  ?
Yes. That's the letter ell, not the number one, by the way. The font on this forum is a little hard to distinguish. It'll give you a bunch of useful info.

> edit: Also, Dr. Nick, your suggestion didnt work. Well, it worked, but didnt end in what I was hoping for. I succesfully set a password but when I go to log in to GDM with root and the new password, this time it says that "The system administrator is not allowed to login from this screen" or something very close to that. I dont understand why as I edited gdm.conf and set AllowRoot to true

Did you restart gdm after editing gdm.conf? ```
sudo /etc/init.d/gdm restart
```
It's possible that there are other settings preventing you from loggin in as root (I haven't tried to do so myself). The reason is that normally, logging in as root--especially in a graphical environment--is a very bad idea. However, I think that your case is an exception.

Your best bet, as I said earlier, is probably to use recovery mode. In case you don't know how to edit files in recovery mode, try using nano (nano filename). In the bar at the bottom of the screen, ^ means Ctrl. So, for example, ^X == Ctrl+X. When you get time, you might want to read man ls for a list of all the things you can do with ls.

Graphical environments are great for normal use, but when it comes to troubleshooting, sometimes you just can't beat the good old command line.

---

### Post by maniacmusician on 2006-08-11
yeah, i'm back on my hard drive installation running as root; thanks for the startx hint nick. 

ls -l /home/maniacmusician reveals this: 

total 16736
drw-r--r-- 2 maniacmusician maniacmusician     4096 Aug  9 04:48 Desktop
drw-r--r-- 2 maniacmusician maniacmusician     4096 Aug  9 02:56 E
lrwxrwxrwx 1 maniacmusician maniacmusician       26 Aug  8 15:39 Examples -> /usr/share/example-content
-rw-r--r-- 1 maniacmusician maniacmusician 17033653 Jul 14 20:53 GoogleEarthLinux.bin
drw-r--r-- 4 maniacmusician maniacmusician     4096 Aug  9 08:53 VMwarePlayer-1.0.1
-rw-r--r-- 1 maniacmusician maniacmusician      478 Aug  9 03:30 automatix.log
drw-r--r-- 2 maniacmusician maniacmusician     4096 Aug  9 09:27 downloads
drw-r--r-- 5 maniacmusician maniacmusician     4096 Aug  9 02:47 easyubuntu
drw-r--r-- 9 maniacmusician maniacmusician     4096 Aug  9 03:21 google-earth
-rw-r--r-- 1 maniacmusician maniacmusician    33686 Aug  5 16:29 jriddell.key
-rw-r--r-- 1 maniacmusician maniacmusician     1787 Aug  5 16:36 quinn1.key
-rw-r--r-- 1 maniacmusician maniacmusician     1690 Aug  5 16:37 quinn2.key
drw-r--r-- 2 maniacmusician maniacmusician     4096 Aug  9 04:29 test


don't know if that helps at all. it looks alright to me. 

I do know how to edit files from terminal; how did you think I edited gdm.conf? 

anyways, this is where i'm at now; logged in as root, can't log in as my normal user. when logged in as root, I can read the contents of my home folder. when logged in as my user in failsafe terminal, I can not see the contents of my home folder. And for some reason, failsafe GNOME doesnt run either. It logs in, nothing happens for a few seconds, and then it takes me back to gdm.

---

### Post by maniacmusician on 2006-08-11
holy crap I think i solved it! and mssever, you'll be surprised to know that the solution lay in a graphical utility. I opened thunar, right clicked on my /home/maniacmusician folder and went to the permissions tab. and this is why i ******* love thunar; there was an option to correct folder permissions! it detected there was something wrong and gave me the option to fix it! i've used this function before, and i havnt seen it in nautilus (not that i use it much). but i like how obvious it is in thunar. anyways, problem is that it's not recursive; will i have to do this seperately for every single file? there's over a thousand. if someone knows how to make this recursive, please please please post it.

thanks.

---

### Post by mssever on 2006-08-11
OK. Everything looks normal. I just re-scanned the previous posts and I'm wondering if we all got a little sidetracked. Wasn't the original problem with .ICEauthority and .dmrc? I'm not sure if this i re-hashing old ground, but here's what I have on my system in relation to these files.

.ICEauthority: permissions: 600; Owner: myuser; contents: binary

.dmrc: permissions: 600; Owner: myuser; Contents:
```
[Desktop]
Session=mwm
```

Right now I'm trying to figure out what those files do.

---

### Post by mssever on 2006-08-11
> **maniacmusician said:**
> holy crap I think i solved it! and mssever, you'll be surprised to know that the solution lay in a graphical utility. I opened thunar, right clicked on my /home/maniacmusician folder and went to the permissions tab. and this is why i ******* love thunar; there was an option to correct folder permissions! it detected there was something wrong and gave me the option to fix it! i've used this function before, and i havnt seen it in nautilus (not that i use it much). but i like how obvious it is in thunar. anyways, problem is that it's not recursive; will i have to do this seperately for every single file? there's over a thousand. if someone knows how to make this recursive, please please please post it.

thanks.

Didn't see this before I posted the last time.

Any idea what thunar is doing? If you can figure out what permissions it's setting, I can give you a command to do it recursively.

---

### Post by maniacmusician on 2006-08-11
well, the error message i got told me: 
> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other us
so .dmrc is used for remembering which session was last loaded and maybe information about it. Also, it says that the file is supposed to have 644 permissions; i wonder how yours works at 600? maybe 644 is just the threshold of permissions it needs to be at. the error involving .ICEauthority was: 
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l :0" "maniacmusician"
/etc/gdm/Xsession: Beginning session setup
trying to create local folder /home/maniacmusician/,kde: No such file or directory
trying to create local folder /home/maniacmusician/,kde: No such file or directory
trying to create local folder /home/maniacmusician/,kde: No such file or directory
/usr/bin/startxfce4: X server already running on display :0
xfce4-session: Unable to access file /home/maniacmusician/.ICEauthority: No such file or directory

i dont know what that file does. i dont think we were too sidetracked...the permissions for the entire folders were screwed up. thunar tells me that they were inconsistent and the "correct folder permissions" button restores consistency.

edit: didnt see your second post before i posted; but i think i answered your question. though i dont know how i can figure out what command it uses...

---

### Post by mssever on 2006-08-11
So it sounds like only a couple of files need different permissions after all. I don't know why I didn't think to ask about the permissions of your home directory.

So, does everything work now?

---

### Post by maniacmusician on 2006-08-11
the exact text that thunar gives me. before I press the button, there is a warning that says:

> the folder permissions are inconsistent. You may not be able to work with files in this folder

and after I press the button, a prompt comes up:
> 
Correct folder permissions automatically?

The folder permissions will be reset to a consistent state. Only users allowed to read the contents of this folder will be allowed to enter the folder afterwards.

basically asks me to confirm that I want to do this. then i click the button, and it happens.

---

### Post by maniacmusician on 2006-08-11
> **mssever said:**
> So it sounds like only a couple of files need different permissions after all. I don't know why I didn't think to ask about the permissions of your home directory.

So, does everything work now?

well it'll be a while before that happens...i have to manually correct the permissions for every folder in my home dir. i dont want to go and try to login when its done halfway, i wanna finish the whole thing. 

i thought it might have something to do with the permissions of my home dir, so i used chmod on it many times, trying out different settings. none of them work. this also happened when I transferred some files from a windows computer. that time also, I used thunar to fix the permissions as i couldnt figure out another way to do it.

---

### Post by mssever on 2006-08-11
OK. Here's what it's doing. Folder permissions are a little different. Execute permissions allow you to read files in a directory and read permissions allow you to list the contents of the directory. So if you have execute permissions but not read permissions, you have to already know the name of what you want to read. It's probably setting 755 on all directories and 644 on all regular files. I think that's the Ubuntu default. Your problems very possibly did come from copying windows files across, since Windows filesystems don't understand Unix permissions.

---

### Post by maniacmusician on 2006-08-11
well I did that on another computer though, not this one. This problem occured the day after I installed Xubuntu on it; no files had been transferred. all I was doing on this computer was setting up an nfs server, and i installed those packages i mentioned in the first post. After that I started to notice X slowing down until it came to a standstill. I restarted X, and from then on wasnt able to log in. you know the rest.

edit: so is there anyway to recursively apply what thunar is doing? this is going to take forever!

---

### Post by mssever on 2006-08-11
If you still have a lot of files to change, you might try to do chmod -R 755 * .* then change all rebular files to 644 by using wildcards. I think that once you get the hang of it, it'll be a lot faster. For example, you could do chmod 644 ab* ac* d* and so forth.

Actually, here's a thought I just had. Save this in a file:
```
function fixPermissions() {
    for i in *; do
        if [ ! -d "$i" ]; then
            chmod 644 "$i"
        else
            chmod 755 "$i"
        fi
    done
}
```
Type source filename, then cd to a directory and type fixPermissions. If my code is bug-free, you should be set.

EDIT: Didn't see your last post, but I think I answered your question anyway (mostly);

---

### Post by maniacmusician on 2006-08-11
> **mssever said:**
> If you still have a lot of files to change, you might try to do chmod -R 755 * .* then change all rebular files to 644 by using wildcards. I think that once you get the hang of it, it'll be a lot faster. For example, you could do chmod 644 ab* ac* d* and so forth.

Actually, here's a thought I just had. Save this in a file:
```
function fixPermissions() {
    for i in *; do
        if [ ! -d "$i" ]; then
            chmod 644 "$i"
        else
            chmod 755 "$i"
        fi
    done
}
```
Type source filename, then cd to a directory and type fixPermissions. If my code is bug-free, you should be set.

EDIT: Didn't see your last post, but I think I answered your question anyway (mostly);


I saved the file in my home dir. I named it fixPermissions. navigated to that dir, typed source fixPermissions (this is what i was supposed to do right?). after that i cd'd to /home, typed fixPermissions and it said command not found.

---

### Post by mssever on 2006-08-11
Hmmm...worked for me. OK, try this. Move that file to /usr/local/bin and chmod +x /usr/local/bin/fixPermissions. Add the loffowing line as the firt line of the file:```
#!/bin/bash
```
Now, if you still have problems, then you're probably typing something wrong.

---

### Post by maniacmusician on 2006-08-11
lol yes i made a stupid mistake...i created the file called fixPermissions, just forgot to paste your code into it. i did it again, and this time, the command fixPermissions went through, but it did not fix my folder permissions. thunar says they are still inconsistent

edit: i'll add that when i typed the command, it went through really quickly...so i dont think it did what it was supposed to. usually recursive commands carried out over a large number of folders take at least a couple of seconds

---

### Post by mssever on 2006-08-11
Just remembered something. The script I gave you won't fix dot files (files with names beginning with a dot). You can either change those manually, or change the for... line to
```
for i in .*; do
```
(at which poing it won't change regular files)

There has to be a way to get them all, but I'd have to delve into the specifics of POSIX regular expressions, which I don't want to do at this time of night.

---

### Post by mssever on 2006-08-11
> **maniacmusician said:**
> lol yes i made a stupid mistake...i created the file called fixPermissions, just forgot to paste your code into it. i did it again, and this time, the command fixPermissions went through, but it did not fix my folder permissions. thunar says they are still inconsistent
Dot folders, or regular ones?

EDIT: Also, this script isn't truly recursive. You have to cd to each directory and run it in each directory. I'm not sophisticated enough to write a truly recursive function in bash on short notice.

---

### Post by maniacmusician on 2006-08-11
well right now its not really "working" on any files...

edir: regular. havnt tried dot folders yet.

---

### Post by mssever on 2006-08-11
> **maniacmusician said:**
> well right now its not really "working" on any files...

edir: regular. havnt tried dot folders yet.

OK, maybe you can post give me the permissions of a file/folder that it was supposed to change, and then the permissions of one that thunar fixed.

---

### Post by maniacmusician on 2006-08-11
here's the ls -l. Desktop is the fixed one. i can't see any visible difference, but thunar says that downloads is inconsistent and i corrected Desktop with thunar

> root@Alexis:/home/maniacmusician# ls -l Desktop downloads
Desktop:
total 4
-rw-rw-r-- 1 maniacmusician maniacmusician 259 Aug 11 02:30 fireglcontrol.desktop

downloads:
total 70464
-rw-rw-r-- 1 maniacmusician maniacmusician 36280264 Aug  9 09:19 VMware-player-1.0.1-19317.i386.rpm
-rw-rw-r-- 1 maniacmusician maniacmusician 35786922 Aug  9 08:58 VMware-player-1.0.1-19317.tar.gz

---

### Post by mssever on 2006-08-11
Here's an impoved/hacked version of the script. You need to source fixPermissions again to apply the changes.
```
function fixPermissions() {
    for i in *; do
        if [ ! -d "$i" ]; then
            chmod -v 644 "$i" # now it lets you know it's doing something
        else
            chmod -v 755 "$i"
        fi
    done
    for i in .*; do
        if [ ! -d "$i" ]; then
            chmod -v 644 "$i"
        else
            chmod -v 755 "$i"
        fi
    done
}
```

---

### Post by mssever on 2006-08-11
We aren't getting the right info from ls. Try ```
ls -dl Desktop downloads
```

---

### Post by maniacmusician on 2006-08-11
nothing happens now either.

> root@Alexis:/home# fixPermissions
root@Alexis:/home# fixPermissions maniacmusician
root@Alexis:/home#


just for extra info I attached a screenshot of the permissions tab of both folders that I checked for  you so you can see what thunar shows me.

---

### Post by mssever on 2006-08-11
I don't see any difference in the two thunar windows, other than the inconsistent notice. Can you post the result of ```
ls -dl . Desktop downloads
``` assuming you're in your home directory? I'm wondering if thunar is hiding some important info.

---

### Post by mssever on 2006-08-11
> **maniacmusician said:**
> nothing happens now either.

Did you notice my edit about having to type source fixPermissions to apply the changes?

---

### Post by maniacmusician on 2006-08-11
root@Alexis:/home/maniacmusician# ls -dl . Desktop downloads
drwxr-xr-x 32 maniacmusician maniacmusician 4096 Aug 11 03:42 .
drwxrwxr-x  2 maniacmusician maniacmusician 4096 Aug  9 04:48 Desktop
drw-rwxr--  2 maniacmusician maniacmusician 4096 Aug  9 09:27 downloads

i'm gonna go take a shower now. gotta head out in a couple of hours. hope you come up with someting. thanks a lot for giving your time by the way; sorry you had to stay up all night

---

### Post by mssever on 2006-08-11
OK. Let's replicate what thunar is doing. We're only going to work on directories here. Here's a new script. Use the same procedure that you used for the previous one.
```
function fixPermissions2() {
    for i in * .*; do # I hope this line is right...
        if [ -d "$i" ]; then
            chmod -v +x "$i"
        fi
    done
}
```

I think the old (modified) script will still do the trick, but just to be safe...

Oh... Here's a bug in both my scripts. If you saved them in /usr/local/bin and so forth, you need to remove the function... line and the last line containing }. If you took the "source" route, than you need to source the file everytime you make changes to it or every time you open a new terminal.

Thanks for the mental stimulation. Yours has certainly been a unique problem. By the way, I noticed that you're a guitarist. Me too!

---

### Post by maniacmusician on 2006-08-11
no i didnt see your edit about having to do source again. I tried the old one again and it gives me this:

> root@Alexis:/home# fixPermissions
mode of `maniacmusician' retained as 0755 (rwxr-xr-x)
mode of `.' retained as 0755 (rwxr-xr-x)
mode of `..' retained as 0755 (rwxr-xr-x)

didnt fix anything. the new one:

> root@Alexis:/home/maniacmusician# source fixPermissions2
root@Alexis:/home/maniacmusician# cd ..
root@Alexis:/home# fixPermissions2
mode of `maniacmusician' retained as 0755 (rwxr-xr-x)
mode of `.' retained as 0755 (rwxr-xr-x)
mode of `..' retained as 0755 (rwxr-xr-x)

still didnt fix permissions :( btw, you were right, we only have to work on folders, not files. files don't give the inconsistent permissions error.

guitar, awesome. what kind of a guitar(s) do you have? do you record your stuff actively?

---

### Post by maniacmusician on 2006-08-11
hey nevermind about the script; i've only got about 30-40 more folders to go, i'll be done in 10 mins. i decided to just delete some dirs that i didnt care about. easier than correcting all of them.  but thank you SOOOO much for all your help through the night. once i'm done i'll try logging in with my username and hopefully this nightmare will be over.

feel free to answer my questions about your guitar(s) though.

---

### Post by maniacmusician on 2006-08-11
lol i made another stupid mistake. i thought i was done, logged out, tried to login, and it gives me the same error. i realized i forgot to do all the dot folders. so i go back and start doing those. it occurs to me; consistency is what thunar was fixing. so why not make everything the same? i did a chmod -R 644. turns out this is a problem. all the folders i had fixed up to this point were made inconsistent again. dont know why this happened but it sure is weird. this makes me apphrehensive that this fix wont work; i'm thinking that the only reason these folders have inconsistent permissions is because i chmod'd them before when i was trying to fix it. i dont know. just thought i'd report this update. now i am once again manually correcting the permissions. just some 400 files left to go lol. but this sure is weird...

---

### Post by maniacmusician on 2006-08-11
as i feared; correcting the permissions problems did not fix it! i still can't log in, it still gives me that same error message. help, anyone?  i won't get back home for a few hours. i can only hope that someone will figure this out.

---

### Post by mssever on 2006-08-11
Don't know if this is irrelevant now, but I woke up with an idea for a truly recursive script that also handles dot files. Sine I've already written it, I'm posting it. Save it in /usr/local/bin and do chmod +x fix-permissions (or whatever you called it). To use it, type fix-permissions ~maniacmusician and it should take care of the rest.
```
#!/bin/bash
function fix() {
        local dir="$1"
        local olddir="$2"
        cd "$dir"
        #echo "\$dir    = $dir"
        #echo "\$olddir = $olddir"
        #echo "pwd     = `pwd`"
        for i in * .[-a-zA-Z0-9_]*; do
                #echo "\$i = ${i}"
                #read dfd
                if [ -d "$i" ]; then
                        #echo "Directory"
                        chmod -v +x "${i}"
                        local dest="${dir}/${i}"
                        #cd "$dest"
                        echo "Entering directory $dest"
                        fix "$dest" "$dir"
                #else echo "Not a directory"
                fi
        done
        echo "Returning to $olddir"
        cd "$olddir"
}

cd "$1"
echo "Starting in `pwd`"
fix `pwd` `pwd`

```
If you have problems with these permissions, change the chmod line to chmod -v 755 "${i}".

I'll write more later. I'm going back to bed now...

---

### Post by mssever on 2006-08-11
The reason that doing chmod -R 644 broke things is that directories have to have the execute bit set (755). If this is still an issue, my latest version of the script will recursively fix this.

Also, are the permissions on .dmrc and .ICEauthority correct now? Let's make sure those are OK. Your previous error message complained about a non-existant .ICEauthority.
```
touch .ICEauthority
chown maniacmusician:maniamusician .ICEauthority .dmrc
chmod 600 .ICEauthority .dmrc
```

My guitar is nothing special--Rogue brand. I don't record or anything. I mostly play for church.

---

### Post by maniacmusician on 2006-08-11
i thought .dmrc was supposed to be 644? i'll try it anyways. i'm all done correcting all the folder permissions. i dont wanna risk chmod on the whole dir again, it was a b*tch to correct them all. 

but i'll try what you posted and post back with results.

---

### Post by maniacmusician on 2006-08-11
okay still didnt work; for some reason, maniacmusician still cannot see its own home folder. i'm pretty sure the permissions are fixed...but something really weird; i logged into a failsafe xterm session. went to /home, typed ls -l and it gave me this (while logged in as maniacmusician)

> drwxr-xr-x 2 root root 0 2006-08-11 23:39 maniacmusician

and when i logged back into recovery mode, went to the same directory, and typed ls -l it said:

> drwxr-xr-x 32 maniacmusician maniacmusician 4096 Aug 11 04:03 maniacmusician

the differences i see are the number 32 (dunno what that means), the owner/group of the files, the number 4096 (number of files? makes sense since the first one shows 0). so whats up with that?

edit: went back to failsafe xterm, typed sudo chown maniacmusician:maniacmusician /home/maniacmusician, and restarted. when i entered failsafe xterm again, it had returned to displaying the owner and group as user. i tried -R for recursiveness but no luck; how could it apply the settings if it couldnt see the content. 

I think that the problem is not in the permissions but in the way that my computer reads those permissions. because obviously the owner and group of that folder and its content is maniacmusician but the system percieves it as root unless i'm in recovery mode, in which case it displays the real facts. so yeah. problem with the way the system reads it, i think.

do you think it is worth it to keep going and try to fix it or should i just reinstsll? on the one hand, I do want a working system again, but on th eother my thirst for knowledge compells me to fix this so i can figure out how this weird phenomenon happened. what do you think?

---

### Post by maniacmusician on 2006-08-13
bump.

---

### Post by maniacmusician on 2006-08-13
Actually, nevermind. This problem might never get solved, and I kind of need a working system. Yes yes, I can keep running my computer and recovery mode and use startx to run X in root mode, but how safe is that? So i decided to do a clean install. I'll just set up my ssh server again. It'll be easier than fixing this lol. For all that helped; thank you so much, I respect that you gave up your time to work on this, but i need a working computer; all my other machines are too slow for regular use. hopefully this won't happen again.

---

