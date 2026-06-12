---
title: "could not update ICEauthority, problem with the configuration server, .nautilus error"
date: 2010-01-05
forum: Desktop Environments
---

### Post by Redsandro on 2010-01-05
[COLOR="DarkRed"]Late edit: **Problem solved.** You cannot have an **encrypted home dir**ectory and **auto-login** at the same time. If your problem is similar but different it probably involves **having an ecrypted home dir and some features that are not compatible with it**.

[SIZE="1"]Original first post follows.[/SIZE][/COLOR]
______________________________________________________


After updates I could not boot normal anymore (freeze right after GRUB). I booted into recovery mode, rebooted, and it worked again. But ever since, I get the following message:

*"could not update ICEauthority file"*

It is already owned by me with 600 permissions. I tried setting it to 644 but it doesn't change a thing.

When I press close, the next message pops up:

[i]"There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"[/i]

When I press close, the next message pops up:

[i]"**Nautilus could not create the following required folders: /home/user/Desktop, /home/user/.nautilus.**
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.[/i]"

But those folders already exists as me:me 755.

A few times after closing all these messages my desktop would appear normally and everything worked. But now I don't get past the empty desktop with a mouse cursor anymore. So I am in trouble.

---

### Post by ticthak@AOL.com on 2010-01-05
running into a similar problem w/ almost all significant updates, I at least can access a DE (defaults to Gnome right now) by using the recovery boot into a root console- I "su" w/o a password, then "startx"

~$: su
~$: startx

---

### Post by Redsandro on 2010-01-05
Yes me too, I can recovery boot and do some stuff to start Gnome. But one time it crashed in the menu where my keyboard wouldn't type anything other than "**>**". I ctrl+als+F3'ed to tty3 and I could normally start Gnome from there.

What is the last change you remember since you had this problem? I remember I chose to automatically login my user, did some updates and shut down my computer.

---

### Post by drs305 on 2010-01-05
There are several bug reports about similar occurrences. Each of your posts have at least one mention of similar behavior. 

Solutions varied, but each of these worked for at least one individual:

```
sudo chmod a+rwx /tmp
```

Deleting files because the partition was full.  Added: One user mentioned his /tmp was full, but perhaps he had a separate partition or poorly worded the post.

Disabling automatic login.

I can't vouch that any will work, but you can look through the bug report for yourself. The report goes back quite a way, so I'd concentrate on posts from the past several months.

Good luck to all of you.

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215")

---

### Post by Redsandro on 2010-01-05
Thanks for mentioning this.
However, my /**tmp** is **777** and **df -h** sais my partitions are at least 40% empty.

I cannot change autologin without rebooting, where the fun part is that my shares and webserver work normally without Gnome and they're in use at the moment. I can reboot and try later, but it's a pretty bad workaround to not use a feature that I actually want to use. :P

How else can I remote wake up my computer and remote log in my shared desktop? :)

---

### Post by Redsandro on 2010-01-07
Please, someone knowledgable, tell us how to fix!

My Ubuntu machine is annoying right now having everything to do from recovery mode. When I boot, everything fails *as if* my home folder is mounted read-only. But it is not! If I switch to CLI, I can write files and dirs.



Ohyeah the recovery boot menu is also flawed. Keyboard doesn't respond and gives errors like this, always the same but color may vary :P :

[img]http://ubuntuforums.org/attachment.php?attachmentid=142832&stc=1&d=1262907620[/img]

At least it makes it look like there is indeed a problem with mounting the file systems. But when I swap to the next tty, everything works, is writable, and I can start X just fine.

What can I tell you to help me fix this?
Only other thing I can think of: My home folder is encrypted. And all errors seem to have to do with writing* problems in my home dir. But then again like I said, I can acces/read/write my homedir just fine from CLI.

*) ICEauthority, /home/user/Desktop, /home/user/.nautilus. and all...

---

### Post by Redsandro on 2010-01-07
Another discovery, also handy for **ticthak@AOL.com**:

You don't have to startx from the recovery console to log in normally.

When your startup fails with the ICE errors, you can switch to a different TTY, login, and restart X from there:

> **$** sudo service gdm stop
**$** sudo service gdm start[SIZE="1"][happyhamster told me]("http://ubuntuforums.org/showthread.php?p=8628353#post8628353")![/SIZE]

This brings you back to the login screen. You can log in normally now!

I am beginning to suspect this is a problem with autologin in combination with home folder encryption and some order of things done invented for 9.10 (Karmik).

---

### Post by Redsandro on 2010-01-08
Look like **drs305** was right after all. Disabling my autologin caused my problems to go away. So I was right too. This is stupid. I cannot autologin. Once again 9.10 proves to be a diarriarelease.

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

### Post by Redsandro on 2010-04-08
Thanks for sharing. Now you have autologin with an encrypted homedir? I thought that was not possible.

---

### Post by robinvanleeuwen on 2010-10-18
My guess is that it has someting to do with access to the /tmp directory. I started having this problem when i changed /tmp in my fstab to tmpfs filesytstem. The problem went away again when i commented it out:


#tmpfs	/tmp	tmpfs	defaults,noexec,nosuid	0	0

---

### Post by Redsandro on 2010-10-18
So the problem is either writability of /tmp/ or /home/, or encryption thereof.

I hope they have fixed the error messages into something clearer and disabled autologon for encrypted homes (or fixed it) by now.

I wouldn't know, because I'll skip 10.10 and the next release until there's another LTS release.

---

### Post by came2die on 2010-10-25
Hello guys, I have a big problem.

The same thing happened to me as described in the first post. The problem is that I lost all the data in home directory. /home/void/ is almost empty. There is only /Desktop folder and it's empty. I would like to get my documents, nothing else.

This could happen because I did the following:

sudo mkdir /home/void/Desktop
           /home/user/.nautilus

I understand why the /Desktop folder is empty. I just don't get it why there are no other folders (is it possible that my command overwrote the whole stuff?) in /home/void.

If I screwed it up big time, is it possible to retrieve those files in /home/void/Documents. I didn't use my computer so I assume those files aren't overwritten yet.

Regards
came2die

---

### Post by drs305 on 2010-10-25
Edit: Informed this was an encrypted partition - so ... nevermind.
came2die,

Open a file browser as root so you can see all the files on your system. This will help if your files were assigned permissions which prevent you from seeing them as a normal user.

```
gsku nautilus /home
```

If you know the name of one of the files you are looking for, you can also search for it with this command:```

sudo find / -type f -iname <filename>
```
If you find the files, run "ls -la /<path to files>" and post the results so we can see where they are and what permissions they have that are preventing you from viewing them.

---

### Post by Redsandro on 2010-10-25
@**drs305**: That will not work, as the files are hidden inside **ecryptfs**.

@**came2die**:

If you have the same problem as described in the first post, it means that your home directory is encrypted and could not be mounted.

This encrypted home **is not actually in your home directory**, that's why it's empty when it cannot be mounted.

I also think (not sure though) that when you start creating folders in your (empty) home directory while it is not mounted, your encrypted home directory cannot be mounted anymore.

After your first boot, you have been given the opportunity to see a passphrase for manually mounting your home dir. If you wrote it down you can mount your dir and recover your files. If not, DO NOT CHANGE YOUR PASSWORD until you fixed the problem.

How to fix? First of all, remove any custom files and folders from the home dir that is supposed to be empty while it isn't mounted. Second, undo the steps that lead to this problem (for example, having autologin + home encryption at the same time).

---

### Post by came2die on 2010-10-25
drs305, thank you for your effort but Redsandro is right :)

Redsandro, I deleted all the files that are not needed. I assume that my own personal password is not the same thing as the passphrase you are talking about :)?

The question is, how do I solve this? I don't use auto login, but I do have my /home encrypted. How do I remove this (can you point me to a good guide, I found this: [http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/](http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/) but I don't want to screw it up).

P.S.: I didn't do any changes on my machine, "it just happened" (if you can believe that :D), not even an update (if I remember right).

Thank you for your help.

---

### Post by Redsandro on 2010-10-25
Indeed, it's not the same.

Your entire home directory is encrypted with a random passphrase, for example **g546yv3c**. This passphrase is encoded with your password, for example **came4u**. Now if your original encrypted data cannot be found and you never wrote down the passphrase [SIZE="1"](**g546yv3c**)[/SIZE], you're gonna have a problem when you change your password [SIZE="1"](**gcame4u**)[/SIZE] because the password-encoded passphrase will not get updated. The problem is for fixing the error, but will not remove your actual home unless you reinstall over the same home partition for some reason.

Anyway,

Every [encrypted home]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") is usually located in 
**/home/.ecryptfs/username/.ecryptfs/** for password and mount data, and
**/home/.ecryptfs/username/.Private/** for your files.

To get the passphrase back, chdir to your **/username/.ecryptfs/** and enter:
**ecryptfs-unwrap-passphrase wrapped-passphrase** and use your original password.

Make sure this folder also contains the files **auto-mount** and **auto-unmount**. It probably does, but if not, create these files and see if your problem is solved.

Now mounting the **/username/.Private/** is something I'd have to google myself so I suggest you do this instead, although maybe it's better to undo the steps that lead to this error in the first place so that you can boot normally again. :)

-edit-

If it really *just happened*, I'm affraid something in your encrypted home might have broken that causes it to be unmountable.
Note that I have had many problems that seemingly *just happened* too, but often there secretly was some cause anyway. For example, if you're used to the installation process and do it on autopilot, I think since 10.04 updates are configured to be *automatic*.

-edit-

Guide seems o.k. never tried something like that. Should work, as long as you don't forget to move EVERYTHING (hidden dotfiles etc.).
Quick glance spots one mistake:
**chown username.username Private** should be **chown username[COLOR="DarkRed"]:[/COLOR]username Private**

---

### Post by came2die on 2010-10-25
I found this: [http://wiki.archlinux.org/index.php/System_Encryption_with_eCryptfs](http://wiki.archlinux.org/index.php/System_Encryption_with_eCryptfs)

I created /home/void/Private
and tried to mount with

```
sudo mount -t ecryptfs /home/username/.Private /home/username/Private -o ecryptfs_cipher=aes,ecryptfs_key_bytes=16,key=passphrase
```

It did the job, but now, there are the same folders/files in /Private as they are in /.Private ---> were not decrypted :)

Please keep in mind, that I just want to get those data and I'll reinstall ubuntu again (had problems with ubuntu for some months now and I am eager to see what 10.04 has to offer :)).

Any suggestions how to decrypt them?

---

### Post by Redsandro on 2010-10-25
I have no manual experience on this. But according to the [link]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") I gave you, there's an extra step since 9.04 for decrypting filenames:

> [list=1][*]If you use encrypted filenames (standard in Ubuntu >= 9.04) you have to do the following first:

[list][*]sudo ecryptfs-add-passphrase --fnek  
[*]Passphrase:  (Enter the mount passphrase you recorded when you setup the mount--this passphrase is different from your login passphrase.) 
[*]You should now get two lines looking like this: 
[*]Inserted auth tok with sig [9986ad986f986af7] into the user session keyring  
[*]Inserted auth tok with sig [76a9f69af69a86fa] into the user session keyring  (write down the second value in the square brackets) 
[/list]
[*]Mount using sudo: 
[list][*]sudo mount -t ecryptfs /home/.ecryptfs/username/.Private /home/username/Private  
[*]Selection: 3  (use a passphrase key type) 
[*]Passphrase:  (Enter the mount passphrase you recorded when you setup the mount--this passphrase is different from your login passphrase.) 
[*]Selection: aes  (use the aes cipher) 
[*]Selection: 16  (use a 16 byte key) 
[*]Enable plaintext passthrough: n  
[*]Enable filename encryption: y  (This and the following options only apply if you are using filename encryption) 
[*]Filename Encryption Key (FNEK) Signature:  (the value you wrote down from the second line above)
[/list][/list]

---

### Post by came2die on 2010-10-25
Thank you for your help. I managed to found all the files I was looking for in those folders (it was a bit messy but I found them). Maybe I was naive because I thought that when I do everything like I should do (mount it), everything will be exactly like before :)

Thank you again, I wouldn't do it without your help :)!

---

### Post by Redsandro on 2010-10-25
Well, if you do everything correctly, everything actually should be like before, in exactly the same folders and names. :(

I think you did something wrong or something changed after an update. But since you already copied them, make sure your files are readable and not still encrypted after copying.

---

### Post by demosthenesk on 2010-12-26
In my case, i had installed Dazuko from Avira antivirus.
The installation of antivirus had edit the fstab.

The result was the system to be unable to mount /home partition.

I alt+ctr+f1 to console terminal
login as root
edit /etc/fstab with pico and made rems the dazuko entries.

reboot and all was fine!

:KS

---

### Post by johnaaronrose on 2011-01-28
I am now getting 'Problem with configuration server  /usr/lib/libgconf2-4/gconf-sanity-check exit with status 256'. I've  tried logging in with Session of 'Failsafe Gnome' -  sometimes it's OK  & sometimes it isn't.
 
 PS I first used sudo chown user:user /home/user/.* to correct the.ICEauthority problem following advice in thread 
[http://ubuntuforums.org/showthread.php?p=10405265#post10405265](http://ubuntuforums.org/showthread.php?p=10405265#post10405265)
Perhaps I should have used sudo chown /user:user /home/user/.ICEauthority rather than sudo chown user:user /home/user/.*
I've subsequently tried sudo chmod 1777 /tmp, which made no difference.

Is the solution to completely remove (i.e. with -purge option or equivalent in Synaptic) nautilus, delete the .ICEauthority file for each user & install nautilus?

---

### Post by johnaaronrose on 2011-01-30
Login is now working fine. I found a message (I've forgotten where) about 'deleting' .ICEauthority. The suggested method is:
mv /home/user/.ICEauthority /home/user/.ICEauthority.bak 
(where user is your login id).

This has the advantage that the .ICEauthority file can be restored by
mv /home/user/.ICEauthority.bak /home/user/.ICEauthority 
 even if the above method doesn't work.

Since both my login users only gave a 'blank' desktop (i.e. no menus or  quick launch icons) when I attempted the standard login, I logged into  the user with administrative privileges by changing the Session (at the  bottom of the screen) to root login (i.e. not one of the Gnome ones)  after selecting/keying in the login id but before keying in the  password.

After login I discovered that a much smaller .ICEauthority file had been  created (1kb versus 60+) for that user. I opened a Terminal &  repeated the command for my other user but with sudo before mv. I then  restarted and was able to login for my first Administrative user, logout  & login successfully for my second Desktop user.

---

### Post by ShakeyJake on 2011-02-04
FWIW, I had the same problem with a different cause.

I had the exact same errors but when I went to chown the /ICEauthority file it told me it couldn't find it. When I couldn't see anything in my /home folder I opened /etc/fstab to find this:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda1 during installation
UUID=b03620db-bf58-45bf-8f20-0234c4c1c403 /               ext4    errors=remount-ro noatime 0       1

# /home was on /dev/sdb1 during installation
[B][U]# Commented out by Dropbox
#[/U][/B] UUID=287c7f8b-ebee-48e3-a930-a19f1fcf628c /home           ext3    defaults        0       2

# /storage was on /dev/sdc1 during installation
UUID=f5d435e4-b40a-42c7-adbf-9cffee75c03b /storage        ext3    defaults        0       2

#Ramdisk
tmpfs /media/ramdisk tmpfs size=1024M,nr_inodes=10k,mode=777 0 0

#Swap space
UUID=748c8408-0076-4c13-9c05-a427af72e3b2	swap	swap	defaults	0	0

```

Dropbox had commented out my /home hard disk entirely, which I guess is a permissions issue of sort but it's not actually .ICEauthority's fault. Remove the bold and underlined text in front of the home line and all should be well.

Don't know why it happened, but it did and it seems to be Dropbox's fault. Colour me unimpressed. I know this is very specific to a small group of people and won't fix it for most people but if (like me) you have those errors above and the methods relating to your .ICEauthority file aren't working then check your /etc/fstab. :)

---

### Post by Coastalguy on 2011-02-22
As a new user, after reading these 3 pages of "all over the place" responses, my head is spinning.... 

As I am getting the same errors, when booting up and after entering my password, ending up with a black desktop screen, I just want to be able to get into Gnome to make a fix that I believe caused my problem. That is installing psydm, and removing the "create on boot" check on the home directory (I thought I was removing another directory from my Windows drive = sda1). 

Can anyone just provide a simple way I can get back into the GUI desktop to accomplish this, rather than all of the very high level fixes that have been given so far????

---

### Post by Redsandro on 2011-02-22
Bottom line: It's a very *versatile error* with *many possible causes*. Believe me everyone prefers a simple solution over a complicated one.

*For me*, 
**Workaround**: Disable autologin on encrypted home
**Prevention**: Do not encrypt account that will autologin
**Fix**: Does not exist on 10.04.

But as other people stated, there could be many unrelated reasons for you to have the same error.

---

### Post by thanasis57 on 2011-07-28
Same problem here. But:
-NO autologin
-NO encryption
as previously suggested.

I had my original root account ("thanasis") and created a new one ("testing"). The original one worked fine, and only the new one had this issue.

Nothing except the Desktop folder was created in my "testing" account. So, as suggested elsewhere, I tried to create and give permissions to the .ICEauthority file as root (sudo touch+chown+chmod). No success. The file was NOT created!

An accident that may shed some light: I accidentally chowned to "testing:testing" the .ICEauthority file from my root (thanasis) account. Then I chowned it back to "thanasis:thanasis". However the problem now appeared in my original account (thanasis) as well!

Fortunately I had a backup which I restored and the error disappeared.

Probable conclusion: the permissions are not correctly handled in general? Is this some more fundamental error in gnome after some recent update?

---

### Post by Redsandro on 2011-07-29
[QUOTE=thanasis57;11096037]Same problem here. But:
I tried to create and give permissions to the .ICEauthority file as root (sudo touch+chown+chmod). No success.[QUOTE]

.ICEauthority and everything else in home should be owned by **testing:testing**, not by **root**. I know that much, hope it works. :)

---

### Post by thanasis57 on 2011-07-29
> **Redsandro said:**
> [QUOTE=thanasis57;11096037]Same problem here. But:
I tried to create and give permissions to the .ICEauthority file as root (sudo touch+chown+chmod). No success.[QUOTE]

.ICEauthority and everything else in home should be owned by **testing:testing**, not by **root**. I know that much, hope it works. :)

Exactly. I meant that I logged in as root and tried to give testing:testing ownership to .ICEauthority. That failed.

**Update:** I also tried to install another desktop (lxde), or do a fsck upon boot, as suggested in other posts. Failure.

I finally gave up and did a fresh install of my system (attention: I did not format the /home partition and I gave the same username/password to my admin account during install). With Linux magic my system was up and running with latest updates and all programs in less than 2 hours, with all my settings preserved! (in the config dotfiles in /home/thanasis)
How long would this have taken in Windose?

---

### Post by Redsandro on 2011-07-29
Funny you mention this. I just reinstalled Windows 7 yesterday. Forgot to turn on RAID in BIOS. Now I need to Reinstall Windows a-fricking-gain.

In Linux, it's no problem. I need Windows for work. Adobe stuff doesn't play well in Linux. I am guessing Linux lacks sophisticated API's.

---

