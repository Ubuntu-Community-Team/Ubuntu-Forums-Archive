---
title: "How do I give myself root privileged?"
date: 2005-04-27
forum: Desktop Environments
---

### Post by epb613 on 2005-04-27
I have searched the forums for the last 20 minutes and can't find anything.

I have been using Ubuntu for over a month now and I'm really getting tired of this sudo thing. I know that being root is unsecure and dangerous, but it's a risk I'm willing to take. Could someone tell me how to give myself root privileges (so that I don't have to keep typing sudo and entering passwords)? Thanks in advance.

---

### Post by sethmahoney on 2005-04-27
If I remember correctly, you can always login as root instead of yourself.

---

### Post by fng on 2005-04-27
applications -> system tools -> root terminal

there you go :)

---

### Post by tread on 2005-04-27
[Unofficial Ubuntu Guide](http://www.ubuntuguide.org/) 

You should find a lot of information there.

---

### Post by DJ_Max on 2005-04-27
[QUOTE=sethmahoney]If I remember correctly, you can always login as root instead of yourself.[/QUOTE]
 Yes & No.
Yes being it's possible
No being it's not the smartest thing to do.

Just create yourself a root account, there are a bunch of threads covering the same topic, otherwise, RTFM.

---

### Post by epb613 on 2005-04-27
Thanks for the quick responses but I still have my problem. 

1) I don't want to log in as root because I want to keep my user settings. (ie: home directory, bookmarks)...

2) A root terminal won't work because that doesn't give me root access in the gui. I specifically want to be able to do root tasks in the GUI. (ie: move around files outside my home directory in nautilus).

3) I have just gone over the Guide 2 more times and I can't find instructions on what I am trying to do.

I may not have been clear before. What I'm trying to do is make it so that I can edit/copy/create/delete files using the GUI file manager. Typing sudo nautilus doesn't do the trick because then it thinks I am root and thus I lose my preferences.

Thanks in advance for your help.

---

### Post by bored2k on 2005-04-27
1)  You can just move your configuration files [they are hidden]. But thats not good

2) To open root GUI applications, run sudo application name. For example
sudo nautilus will open nautilus with root access. You can edit your visudo to avoid inputting your password.

3) What preferences are this dude? just copy your .nautilus files to root's.
You can make your user account have 777 access to everything if you dont want sudo nautilus. But you're just locking yourself.

---

### Post by epb613 on 2005-04-27
I'm not sure what 777 access is. All I want to do is make my user account the exact equivalent of a root account. Meaning I would never have to type in my password and I would never get "access denied"'s. Can such a thing be done.

---

### Post by bored2k on 2005-04-27
[http://ubuntuguide.org/4.10/index.html#usesudowithoutpasswordprompt](http://ubuntuguide.org/4.10/index.html#usesudowithoutpasswordprompt)
You can chmod 777 something to get full access. man chmod for info. Or you can chown, chgroup, man those too.

---

### Post by epb613 on 2005-04-27
Ok, I think I see what your saying now. I can use chmod to make my username the owner of every file on the system. But still, for example, when I want to apt-get, won't I still have to do it as sudo? Can I make it that I have the privilege to apt-get?

---

### Post by bored2k on 2005-04-27
Again [http://ubuntuguide.org/4.10/index.html#usesudowithoutpasswordprompt](http://ubuntuguide.org/4.10/index.html#usesudowithoutpasswordprompt) .

If you do that, you wont be asked for passwd everytime you sudo.

Chmod doesnt change owners, chown does. 

You could always make yourself part of the root group, but doing so the havok you can potentially make is unpleasant.

---

### Post by epb613 on 2005-04-27
[QUOTE=bored2k]Again [http://ubuntuguide.org/4.10/index.html#usesudowithoutpasswordprompt](http://ubuntuguide.org/4.10/index.html#usesudowithoutpasswordprompt) .

If you do that, you wont be asked for passwd everytime you sudo.

Chmod doesnt change owners, chown does. 

You could always make yourself part of the root group, but doing so the havok you can potentially make is unpleasant.[/QUOTE]
 Yes! Thats's what I want to do - make myself part of the root group. I don't care if it's dangerous blah blah some evil man on the internet might trick me into deleting my whole partition blah blah I might press the wrong the button and blow up my computer and and all the surrounding small countries blah blah (I may have had a bit of a tough day). I just want to do it. Ok, so how?

---

### Post by epb613 on 2005-04-27
Bleh. Actually on second thought it didn't work. I went to Users and groups and made my main group be root. Then when I tried to create a new folder in the / directory, it told me permission denied.

---

### Post by bored2k on 2005-04-27
[QUOTE=epb613]Bleh. Actually on second thought it didn't work. I went to Users and groups and made my main group be root. Then when I tried to create a new folder in the / directory, it told me permission denied.[/QUOTE]
 WHAT is the problem with linux asking you for a password ? Do you want to create something in / ? create it with sudo nautilus then change permissions, et voila. Not even think about playing with system files. You get asked for passwd for your own safety. It's a firewall to protect you against yourself, just like [http://ubuntuforums.org/showpost.php?p=150182&postcount=2](http://ubuntuforums.org/showpost.php?p=150182&postcount=2)

---

### Post by epb613 on 2005-04-27
It's not typing in passwords which I mind so much. It's being locked out of my system that I find unreasonable. I understand that this was done for my protection but I'm not interested. Is there any way I can bypass it?

---

### Post by fourfats on 2005-04-29
you can do 
```
sudo -s 
```
or
```
sudo su
``` 
those will make you root user.
and if you want su to work without sudo then when you are in root user with the above commands type:
```
passwd
``` 
and give a root password. afterwards you can use su and give the root password like how other linuxes are. this way you dont have to keep using sudo

---

### Post by Gowator on 2005-04-29
Ubuntu is already horribly insecure but why not just add your user to the root group if you don't care about security?  

/etc/passwd and /etc/group 
after this your home dir files will have differnt privs but it won't actually matter since you will be able to accidentally delete them anyway.

---

### Post by Leigh on 2005-04-29
[QUOTE=Gowator]Ubuntu is already horribly insecure...[/QUOTE]

Could you elaborate further on this, please?  I'm new to all this but was VERY interested in your comment.

---

### Post by Stormy Eyes on 2005-04-29
[QUOTE=Leigh]Could you elaborate further on this, please?  I'm new to all this but was VERY interested in your comment.[/QUOTE]

Ignore him. He doesn't understand the rationale behind disabling the root account and using sudo to run individual commands as yourself but with elevated privileges. Read ["Sudo in a Nutshell"](http://www.courtesan.com/sudo/intro.html) if you're interested.

---

### Post by Leigh on 2005-04-29
Maybe I got the wrong end of the stick, but I understood him to say that Ubuntu - the operating system - is insecure like Windows XP is insecure, not the "logging-in-as-root" part, hence my interest.

---

### Post by Stormy Eyes on 2005-04-29
[QUOTE=Leigh]Maybe I got the wrong end of the stick, but I understood him to say that Ubuntu - the operating system - is insecure like Windows XP is insecure, not the "logging-in-as-root" part, hence my interest.[/QUOTE]

That's what I think he's saying too, but he's griped in other threads about sudo and about how using sudo to grant root privileges on an "as needed" basis is insecure.

---

### Post by epb613 on 2005-04-29
[QUOTE=Gowator]Ubuntu is already horribly insecure but why not just add your user to the root group if you don't care about security?  

/etc/passwd and /etc/group 
after this your home dir files will have differnt privs but it won't actually matter since you will be able to accidentally delete them anyway.[/QUOTE]

Can you elaborate a little more? What do I change in these files? I think in the group file I just have to add my name after the final ´:´ on the root line, but what do I change in the passwd file?

Thanks in advance.

---

### Post by nad on 2005-04-29
You need to log out and log back in (or is it restart) for the change that you made in post# 13 to take effect.

How apropos, #13.

---

### Post by epb613 on 2005-05-01
Ah, very nice. Now of course, being a newbie, I screwed up my system. Well, not to quite that extent. Eventhough I´m actually more comfortable with sudo now, I still wanted to try out to see what it would be like. Anyhow, the way I did it was through Kuser. When I changed my group though, it lost my home directory and log-in script. I changed my directory back to /home/user-name but I don´t what my login script should be. Should it be sh or bash (or nothing)?

---

### Post by 23meg on 2005-05-01
do a search on the forums (and elsewhere if it's not here) on "sudo timeout". somewhere you should be able to adjust how long the sudo command takes to time out (i think it defaults to 5 minutes). so if you make it, say, 30 minutes you won't be asked for a password once you've executed a command with sudo for the next 30 minutes.i'm not sure if this can be set to infinite, but if it can i think you'll benefit from that ;)

---

### Post by 23meg on 2005-05-01
you might also like [this trick](http://www.ubuntuforums.org/showthread.php?t=24008). and check the man pages for the **gksudo** command.

---

### Post by XDevHald on 2005-05-01
[QUOTE=sethmahoney]If I remember correctly, you can always login as root instead of yourself.[/QUOTE]

If you mean by terminal, yes, if by login screen from boot, sys won't let root be logged in from the main login screen, would be nice, and if there is a way, I'll post it unless someone else has done it already.

---

### Post by 23meg on 2005-05-01
you can enable logging in as root by going into system/administration/login screen setup/security and ticking the "allow root to login with gdm" box.

---

### Post by Gowator on 2005-05-02
[QUOTE=Stormy Eyes]Ignore him. He doesn't understand the rationale behind disabling the root account and using sudo to run individual commands as yourself but with elevated privileges. Read ["Sudo in a Nutshell"](http://www.courtesan.com/sudo/intro.html) if you're interested.[/QUOTE]


Having any user (like www) be able to change the root password is insecure...
a cgi script with sudo passwd root is a bit obvious!  Ubuntu just bypasses the traditional security model that programmers (Gnome) have programmed for....  

if he doesn't want prompting for passwords and doesn't care about security then the easiest thing to do is run as root ....

Its horribly insecure, it gives a chance to delete all your files but if someone doesn't want to remember a password its really not much else you can do apart from smartcards etc.  

if they don't want to be called root they can be anything they want to slong as they are in the group and have a UID of 0!

---

### Post by Gowator on 2005-05-02
[QUOTE=23meg]you can enable logging in as root by going into system/administration/login screen setup/security and ticking the "allow root to login with gdm" box.[/QUOTE]
You also need to do this if you decide yo make your user ID = 0 and have a root account with a different name.  

However as I said doing this bypasses much of the native safely of linux...  
like not wearing a seatbelt is more safe but you have to clip it in everytome!

---

### Post by gunnyman on 2005-05-02
WARNING
POTENTIALLY DANGEROUS INFO HERE THAT CAN TOTALLY HOSE A LINUX SYSTEM


ok in a nutshell:



go to gdm settings and allow root logins
set a root password with sudo passwd root
logoff
log in as root
open nautilus
navidgate to your username's home folder
check show hidden in the view menu
select everything in that folder and COPY
navigate to your /root folder (this is root's home folder) 
PASTE 
log out 
log back in as root and your root desktop and settings will be same as your regular user name.

Have fun and remember when your system gets messed up, you did it yourself.
Linux's built in protections were bypassed.

---

### Post by XDevHald on 2005-05-02
[QUOTE=gunnyman]WARNING
POTENTIALLY DANGEROUS INFO HERE THAT CAN TOTALLY HOSE A LINUX SYSTEM


ok in a nutshell:



go to gdm settings and allow root logins
set a root password with sudo passwd root
logoff
log in as root
open nautilus
navidgate to your username's home folder
check show hidden in the view menu
select everything in that folder and COPY
navigate to your /root folder (this is root's home folder) 
COPY 
log out 
log back in as root and your root desktop and settings will be same as your regular user name.

Have fun and remember when your system gets messed up, you did it yourself.
Linux's built in protections were bypassed.[/QUOTE]
 To be a bit more specific could you post where to go, this way some people can do this step by step?

/Including myself ;)

---

### Post by gunnyman on 2005-05-02
if you can't figure those things out on your own, you have NO BUSINESS running as root.
 ](*,)

---

### Post by XDevHald on 2005-05-02
[QUOTE=gunnyman]if you can't figure those things out on your own, you have NO BUSINESS running as root.
 ](*,)[/QUOTE]


LOL, that was a joke gunnyman, I am talking about users that are a few months new into Ubuntu, not for me lol.

And yes I do agree, if you can't figure these steps out, then you need to read a guide or manual on these steps or figure out how to open these apps up.

---

### Post by gunnyman on 2005-05-02
Sorry, I missed the joke.
I just can't get my head around what the original poster's problem with entering a password when doing potentially dammaging stuff.
I meant no offense.

---

### Post by epb613 on 2005-05-02
[QUOTE=gunnyman]WARNING
POTENTIALLY DANGEROUS INFO HERE THAT CAN TOTALLY HOSE A LINUX SYSTEM


ok in a nutshell:



go to gdm settings and allow root logins
set a root password with sudo passwd root
logoff
log in as root
open nautilus
navidgate to your username's home folder
check show hidden in the view menu
select everything in that folder and COPY
navigate to your /root folder (this is root's home folder) 
COPY 
log out 
log back in as root and your root desktop and settings will be same as your regular user name.

Have fun and remember when your system gets messed up, you did it yourself.
Linux's built in protections were bypassed.[/QUOTE]
 This is not what I originally wanted to do (now I know - what I wanted to do was add myself to the root group) but I think this is actually a much better solution. Thank you.

Also, for the billionth time, the reason I wanted root privileges was not because I'm to lazy to type in my password. It's for the situations where you're not even given the option to type your password. For example, if you want to manage your files (those outside your home directory) inside nautilus or konqueror.

---

### Post by Gowator on 2005-05-03
[QUOTE=epb613]This is not what I originally wanted to do (now I know - what I wanted to do was add myself to the root group) but I think this is actually a much better solution. Thank you.

Also, for the billionth time, the reason I wanted root privileges was not because I'm to lazy to type in my password. It's for the situations where you're not even given the option to type your password. For example, if you want to manage your files (those outside your home directory) inside nautilus or konqueror.[/QUOTE]

and for the billionth time there is a reason you can'tr move those files without root priv's...  

what you are asking is like taking a rev limiter off a performance car..  its there for a reason and 
> if you can't figure those things out on your own, you have NO BUSINESS running as root. is very true.  It is there for a reason which is stop and think.  If you don't understand why then looking it up makes you aware of the dangers.  usually man pages also say why sometihng is locked/protected and you can then unlock it while understanding the probs.

---

### Post by audax321 on 2005-05-03
[QUOTE=epb613]This is not what I originally wanted to do (now I know - what I wanted to do was add myself to the root group) but I think this is actually a much better solution. Thank you.

Also, for the billionth time, the reason I wanted root privileges was not because I'm to lazy to type in my password. It's for the situations where you're not even given the option to type your password. For example, if you want to manage your files (those outside your home directory) inside nautilus or konqueror.[/QUOTE]

Actually, you could just do:

```
sudo nautilus --browser
```
OR
```
sudo konqueror
``` 

to run it as root, or just make a launcher with the following command (under Gnome, I have no clue about KDE) to be run:

```
gksudo "nautilus --browser"
``` 

That will give you access to every file if you ever need it.

 :)

---

### Post by Thyrth on 2005-05-03
# If you are tired of typing "sudo" all the time, switch to root user by issuing
"sudo -s -H" followed by user password

---

### Post by epb613 on 2005-05-04
Gowator, my point was to prevent what was to come three posts later - Thyrth's post:
epb613: Also, for the billionth time, the reason I wanted root privileges was not because I'm to lazy to type in my password.
3 posts later...
Thyrth: # If you are tired of typing "sudo" all the time, switch to root user by issuing
"sudo -s -H" followed by user password

By the way, Thyrth, and everyone else, I don't mean to act ungrateful for your help - it fixed my problems and taught me lots of new stuff. I just find some of the posts in this thread quite comical.

audax321, sudo konqueror doesn't work (or at least it returns lots of error messeges). kdesu konqueror does though. And in the end, this is the route I'm actually taking.

---

### Post by TravisNewman on 2005-05-04
I don't care how new you are, there are some things you need to do and this user was asking how to do it. In the future, please be more considerate toward new users-- they need to know how to do things too, and we aren't an "RTFM" community.

---

### Post by Gowator on 2005-05-05
[QUOTE=panickedthumb]I don't care how new you are, there are some things you need to do and this user was asking how to do it. In the future, please be more considerate toward new users-- they need to know how to do things too, and we aren't an "RTFM" community.[/QUOTE]


sure I find reinstall fixes many problems ?  

if someone wants to do something which they dont realise the consequences of its better to tell them to RTFM than blindly say 


sudo rm -rf / 

as a way to delete all the .jpg files on the system....  which it will!  along with everything else.  various people gave advice as to what to read to understand why on top which is even better and several actually told him....  

if he wants to bork his box then he can choose to ignore the RTFM since he has several solutions...

---

### Post by Zillion on 2005-05-05
Ok, I am pretty new too. I figured how to mount my fat32 partitions at startup. Now the mounted folders are located in the media folder. I made shortcuts and want to place them on my desktop. But the system keeps complaining I dont have right to do that. How stupid is that.. 

I tried sudo nautilus, but it still says I dont have rights to copy the shortcuts I made in the media folder to my desktop.. how can I do that? And why the hell is that so dang tight secured, makes no sense to me that I cant even copy somthing to my desktop  :?

---

### Post by gunnyman on 2005-05-05
you can change ownership of the directory you mounted with the chown command
sudo chown -R username:username /mountpoint

---

### Post by jean on 2005-05-05
When i installed linux and ran it for the first time,i was asked for a username and password,so i chose one....but now i wanna try being the root user, so i  type 'su' and it prompts me for a password....i know it sounds stupid,but i have no clue what my root password is,i never chose one during or after the installation??...What do i do to become the root??..Thanx!!

---

### Post by BAshworth on 2005-05-05
[QUOTE=jean]When i installed linux and ran it for the first time,i was asked for a username and password,so i chose one....but now i wanna try being the root user, so i  type 'su' and it prompts me for a password....i know it sounds stupid,but i have no clue what my root password is,i never chose one during or after the installation??...What do i do to become the root??..Thanx!![/QUOTE]

Ubuntu doesn't use the standard root user account, so when prompted for a password, use your normal account's password.

---

### Post by jean on 2005-05-05
Already tried that....didnt work for some reason!!

---

### Post by Gowator on 2005-05-05
sudu passwd root


(from a terminal) and set the root passsword to something you remember.  
then try 
su

More information: [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by arnieboy on 2005-05-05
u sound a little confused here (for one thing u want root access and then u say u dont want to log in as root). I would suggest you take a look at my HOWTO [http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053)
This will tell u how to login to X as root. Even if u dont want to do that atleast it will set your root password and u can do a "su" and become root temporarily.
sudo sucks at times, I agree but there are a million ways to circumvent it. If u are interested u can use the following nautilus script :
[http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here)
to open nautlius as root in any directory from nautilus itself by just right clicking on a file in nautilus and clicking "open root nautilus here". If u dont know how to install a nautilus script, let me know.

---

### Post by 23meg on 2005-05-05
epb613: you might also be interested in the "root nautilus here" nautilus script, here: [http://g-scripts.sourceforge.net/cat-executing.php](http://g-scripts.sourceforge.net/cat-executing.php)

---

### Post by jiro on 2005-05-05
[QUOTE=gunnyman]you can change ownership of the directory you mounted with the chown command
sudo chown -R username:username /mountpoint[/QUOTE]

I have a similar problem, and using chown as suggested above did not work. I just installed Kubuntu, defining a 32FAT partition to be mounted as /MyDocuments. This partition is fully accessible to Win2K, but read-only under Linux because it's owner and group are set to "root".

Changing ownership using chown resulted in an "operation not permitted" error.

Changing permissions using chmod also did not work (I tried "sudo chmod 777" and also "sudo chmod a+rw".)

Also, I changed my root password and tried the same things from a root console, with the same no luck.

And, I tried changing the permissions by doing a "kdesu konqueror" (equivalent to Nautilus on gnome) and then using the gui - which also failed.

Any suggestions, anyone? All I want is to have a partition with read/write access both in Win2K and Linux. There must be some solution I haven't tried yet...

---

### Post by Professor X on 2005-05-05
You can't change permissions of a FAT32 filesystem while the fileystem is mounted.  You need to unmount the filesystem, then chmod 0755 /MyDocuments.  Now edit your /etc/fstab so that it contains something like this:```


/dev/<FAT32 partition> /MyDocuments vfat users,defaults,umask=000 0 0
```

---

### Post by jiro on 2005-05-05
Thanks! Since I did do a "kdesu kate /etc/fstab" (kdesu b/c I'm in KDE, not gnome) and then restarted the system, I don't understand why I needed to chmod the folder as well. But I did, and things are looking good!

---

### Post by epb613 on 2005-05-06
Yeah that script does sound cool. How do you implement it?

---

### Post by jiro on 2005-05-06
[QUOTE=epb613]Yeah that script does sound cool. How do you implement it?[/QUOTE]
 I think the best thing to do, should be done during the initial installation when setting up your partitions. I defined a FAT32 partition with the options set to "defaults." Instead, I should have overrided the defaults by setting "users,gid=users,umask=000".

What I actually did (after Kubuntu was already installed and running) was:

(1) unmount the partition: "sudo umount /FOLDERNAME" (my partition was mounted at /MyDocuments; yours may likely be called /windows or /dos).

(2) change the ownership of the folder: "sudo chown yourname:yourname /FOLDERNAME" (where "yourname" would be the user name you normally boot on). This step might not be necessary.

(3) change the permissions of the folder: "sudo chmod 777 /FOLDERNAME". This step might also be unnecessary, because (I think) editing fstab (next step) does the same thing.

(4) edit fstab: "kdesu kate /etc/fstab" opens up a text editor of the "fstab" file. Modify the options setting for the FAT32 partition by deleting "defaults" and setting instead "users,gid=users,umask=000".

(5) save fstab and restart your computer.

Again, some of these steps may be unnecessary. I don't know enough to say. But this is what worked for me.

---

