---
title: "Warning DBuserror.org.freedesktop.DBUS.Error.NoReply"
date: 2009-01-10
forum: Desktop Environments
---

### Post by bd@cb8be8510 on 2009-01-10
When a mount a cdrom with a large number of pictures, I always get a dialogbox with the following message : DBuserror.org.freedesktop.DBUS.Error.NoReply : Did not receive a reply. Possible cause include: the remote application did not sent a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection was broken.

This happens to be only a warning as after a few seconds, the cdrom gets mounted and the files are being displayed. Looks as if the timeout set is too sharp for my hardware. How can I prevent this message as it seems rather harmless, but is rather annoying when you mount a cdrom.

---

### Post by cguy on 2009-02-03
I experience this problem when I unmount a phone card.

Does anyone have an answer for this?

---

### Post by cguy on 2009-02-05
So?

---

### Post by nohammer on 2009-05-23
It looks like I only have the problem with cd\dvd I burnt in windows. Anything I burnt in linux or if its a manufactured cd it mounts fine.


-----------------------------------------------------------------------------------------
Sorry for the bump - I just installed a new SATA optical drive (Samsung SH-S223F) and now I'm getting this error whenever I try to mount a 2nd CD\DVD in a session. THe first one is fine, but the 2nd one results in this error in Gnome

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


Using 8.10 with all of the most recent kernel upgrades. I've checked my fstab and it still includes the line
/dev/cdrom       /media/cdrom0   is09660 ro,users,noauto       0       0

I have also changed it to
/dev/sc0       /media/cdrom0   auto ro,users,noauto       0       0

and other combinations.


I have also tried commenting out the CDROM line in fstab and letting HAL take care of it but I still get this error message.

I don't want to have to reinstall or changed my BIOS settings to treating SATA drives as IDE

Exact error
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by AndThenWhat on 2009-06-06
I am having the same problem when I try to connect to a site using FTP.

```
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply
```

---

### Post by nohammer on 2009-06-22
bump - its not a critical issue but I would like to know what is going on.

---

### Post by deusdiabolus on 2009-07-15
I am also getting the same response when I try to access a Windows-based MP3 jukebox in my home network (it is an Escient E2-160, for anyone who might know a way to make this work).  Under a Windows system, the jukebox's hard drive is accessed by inputting "//:(server name)".  Since I first started using Ubuntu in May, I haven't been able to figure out how to access the jukebox over the network.  Yesterday I looked at the network listings and there it was (I think it has something to do with running the jukebox, which caused the network to finally notice it - I don't use it often).  But when I tried to access the folder containing all the music, I received the following message:

[INDENT]*Sorry, could not display all the contents of "content on [servername]": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.*

[/INDENT]I know that the directory normally takes a long time to load (it's a 160GB hard drive that is about 85% full), so I like the others in this thread would like to know if there is anything I can do to adjust the time the system waits for the directory to load, if that is the issue.  Thank you in advance.

---

### Post by jdorenbush on 2009-12-11
I am getting this error message too. I get it sometimes when trying to browse FTP or save PHP files with Text Editor. Going to keep looking for a solution...

---

### Post by WolfRage on 2009-12-14
I get this message when I try to browse a computer located in the network folder. I really want it fixed, because I now have to type in the location manually. "smb://<computerName>/<shareFolder>/"

---

### Post by andthen.. on 2009-12-29
I get this message when I unmount an MP3 stick after putting music on it and also sometimes with another data stick.

It seems it times out before it has finished transferring data/unmounting & I cant seem to unmount the stick properly.

This has corrupted some data on the stick before. 

It seems the mp3 stick becomes idle and stops replying to my laptop before the laptop is finished transferring data.

---

### Post by jimi_bond on 2010-02-03
I've just upgraded to 9.10 and I get the same error message "Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus) Please select another viewer and try again" when I try to access shared directories on my windows PC. This is a real pain as I need to copy files from to and fro between my ubuntu PC and my windows PC. Has anyone got any idea?
It worked fine before I upgraded. I've reinstalled all the samba stuff.

---

### Post by jimi_bond on 2010-02-03
I found a workaround by setting up a directory in my media directory

mkdir /media/stuart_02

then adding this line to the bottom of my /etc/fstab file

//[IP_ADDRESS_OF_SHARE]/[SHARE_NAME] /media/stuart_02 smbfs rw,auto,user=[USERNAME],password=[PASSWORD]	0 0

thats the user name and password of the PC were the folder is you wish to mount, in my case the windows PC.

you can then either reboot or run this command

sudo mount -a

and you should see an icon appear on your desktop.

---

### Post by iposner on 2010-04-12
I get this message trying to connect to a Windows share. I completely reinstalled my machine from scratch apart from the Home folder (separate partition). It still occurs. Strangely it's only occurring on one machine out of two. Both machines are x64 running 64-bit Lucid Lynx 10.04 fully patched.

---

### Post by JoeWheeler on 2010-04-13
I'm getting this when trying to connect to windows via samba, also running lucid beta 2

---

### Post by iposner on 2010-04-13
OK - It turns out that my Bookmarks in nautilus that were links to SMB shares caused the error - but navigating through the network seemed to work fine. Perhaps something has changed in the format of these bookmarks in nautilus which is conflicting with dbus?

---

### Post by iposner on 2010-04-13
On further investigation, it looks like one of my shares is working properly, but the other shares on the same machine (a Nas running debian sarge) are producing the error. I'm now comparing each of the shares, but it looks like the Bookmark issue was a red-herring.

---

### Post by jdorenbush on 2010-04-14
Since updating to 10.04 I've been seeing this error message a lot more. It happens sometimes when I try to connect to my site's FTP via Nautilus.

This comes with other FTP-related problems I've been having when using Nautilus. When editing live pages with gedit sometimes saving will hang for 30-40 seconds and then it will just give up. I usually have to close it down and disconnect from FTP and then reconnect and try again. Sometimes browsing folders will hang too. Just overall bad connection when using Ubuntu + Nautilus + FTP. Never had this problem on Windows before.

---

### Post by bear7 on 2010-04-15
I received the same message(U9.10). I solved the problem by using these commands:
```
sudo apt-get purge samba
sudo apt-get install samba
sudo dpkg-reconfigure nautilus
```
Looks good. Didn't get any error so far.

---

### Post by jdorenbush on 2010-04-16
> **bear7 said:**
> I received the same message(U9.10). I solved the problem by using these commands:
```
sudo apt-get purge samba
sudo apt-get install samba
sudo dpkg-reconfigure nautilus
```
Looks good. Didn't get any error so far.

```
sudo apt-get purge samba
```
"Package samba is not installed, so not removed"

```
sudo apt-get install samba
```
"Depends: samba-common (=2:3.4.6~dfsg-1ubuntu2) but 2:3.4.7~dfsg-1ubuntu3 is to be installed"
"Depends: libwbclient0 (=2:3.4.6~dfsg-1ubuntu2) but 2:3.4.7~dfsg-1ubuntu3 is to be installed"

Didn't work out very well on my end. :\

---

### Post by nepenthes on 2010-05-06
> **jdorenbush said:**
> Since updating to 10.04 I've been seeing this error message a lot more. It happens sometimes when I try to connect to my site's FTP via Nautilus.

This comes with other FTP-related problems I've been having when using Nautilus. When editing live pages with gedit sometimes saving will hang for 30-40 seconds and then it will just give up. I usually have to close it down and disconnect from FTP and then reconnect and try again. Sometimes browsing folders will hang too. Just overall bad connection when using Ubuntu + Nautilus + FTP. Never had this problem on Windows before.

Exactly the same experience for me. Since 10.4 the FTP situation worsened quite a bit. I have to try several times (with above error) until I can connect. There must be somewhere a setting where we can increase that error-timeout.
GEdit for FTP saves sometimes and sometimes not, about the same for 9.10. In my experience this happens after the FTP connection idles for a while. It's not so annoying though, one 'cancel' then save again and it works.

I barely remember Windows though. Is that an Operating system? ;)

---

### Post by Alex1331 on 2010-05-28
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I have the same problem with Ubuntu 10.04.

Sometimes gEdit overwrites a remote file with an empty file, and all my php code gets deleted. It wont manage to save a file if the FTP connection has not been in use recently.

Something  else that has been a problem is that it will not always unmount an FTP  directory.

This is really annoying!

---

### Post by Altreus on 2010-06-11
Hi all

I've been having a similar problem with the Windows network. Luckily for me, the samba share is actually on a Linux server so I could log in and see what was going on.

The first thing I tested was whether it could actually find the server. I removed my details from the Gnome keyring. This would decide whether it got a response for authentication. Short answer, it did. I gave it my auth details and *then* got the dbus error message.

Since I knew the IP address I tried this:

```
# smbmount //<IP>/<dir> /mnt/smbdrive/<dir> -ouser=<username>,password=<pass>
```

smbmount complains about not being able to mount a root directory, which is why I have had to add <dir> into these.

Interesting response, however:

```
mount error(113): No route to host
```

But pinging <IP> receives responses.

It is at this point I tried again in Nautilus and lo and behold I can browse the network.

I have a feeling the dbus timeout error is not lying. The first ping back from the server was 2.6ms; the rest were of the order of 0.5ms.

I am therefore wondering whether the pinging of it (or sshing into it) did something with a cache, that then causes the server to respond within good time for dbus to mount it.

I will keep playing with this to see what I can find.

Apologies that this does not help people with local drive issues :<

---

### Post by nikobe on 2010-06-29
I had the same problem on mounting windows shares (from a small business 2008 server) which I'd opened fine the previous day. The only change between then and now is running updates but I sadly didn't pay attention to what updated.

Anyway reinstalling Samba then restarting Nautilus fixed it for me, a few folders still moaned with the same message but a quick F5 on that page and try again worked in most cases.

---

### Post by jal_nl on 2010-08-17
I recently installed 10.04, and since then my FTP locations all produce the DBus error. No problems of this kind ever occurred in 9.10. FTPing from the shell doesn't pose any problems. This is indeed quite annoying - I hate it when stuff breaks after an update.

---

### Post by UAA on 2010-09-16
I have this message and I fixed it on Lucid by running seahorse and removing the password of the shared folders. though I didn't change the passwords lately.

I had the problem while trying to mount windows shares from nautilus. the old shortcuts to the share were not working (the same error message).

After I deleted the stored passwords the share is working again.

---

### Post by kris.developer on 2010-09-20
I also received this message after shutting down without unmounting a ftp location. The error was fixed by deleting the saved information for the ftp location from the keyring/ Passwords & Encryption key program.

---

### Post by ego1 on 2010-09-23
> **UAA said:**
> I have this message and I fixed it on Lucid by running seahorse and removing the password of the shared folders. though I didn't change the passwords lately.

I had the problem while trying to mount windows shares from nautilus. the old shortcuts to the share were not working (the same error message).

After I deleted the stored passwords the share is working again.

This worked for me.
Thanks

---

### Post by Alex1331 on 2010-09-30
It did not work for me...

> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I hate when files get overwritten with a empty file, or the whole files dissapears.(FTP, gEdit)
Please, PLEASE tell me how i can solve this problem :/

---

### Post by ciscophoneguy on 2010-10-08
I'm having the exact same problem with window shares. Copying large files and small files alike. Anyone know a way to fix this please....

---

### Post by Alex1331 on 2010-10-10
The problem still exists in 10.10. :(

---

### Post by Robert-H on 2010-10-16
I think this problem started when I upgraded to Lucid and I hoped it would go away with Maverick but it's still just as bad. I don't see any useful solutions posted here???

---

### Post by Bogusz on 2010-10-21
SOLUTION: use program seahorse and delete the key for the share. Seahorse can be found under applications/accessories/passwords and keys. After deleting the key (simply right click on the line and select delete from a context menu which appeared)  click again on your saved share and retype password. It should work then even with the same password. I am using 10.04 LTS - Lucid Lynx and this occured after an update. I will do an update now and will post if this occured again after todays update of the system.

---

### Post by Bogusz on 2010-10-21
UPDATE: yes I can confirm, this problem came after system update again, and the above solution (<1 min) solved it again. So it is now a programmers issue.

---

### Post by Simon Corlett on 2010-11-14
Hi, ubuntu newby here.

I too am getting this error message running on ubuntu 10.10 i have tried the above fix but do not find a key for the connection in seahorse in order for to delete it.

I have tried the following;

Set up webdav connection to remote server - polls for 5mins then returns error
set up smb connection to remote server - instant return of the error message. 

seahorse is not registering any keys for the connections I have made.

I am able to boot into ubuntu 9.04 and set up connections without a problem.

I have also tried coping the key's across from the older install without any success 

I have tried setting up another administrator account on 10.10 and setting up the connections only to receive the same error. 

it seams to me there is an issue with either the network manager not writing details to seahorse or seahorse not recording the details. again I am a newby so please take my observations as such.

if someone could help as I am hoping to use this machine as a remote office but need access to my files. 

may try setting a new install up in virtual box to see if I am getting the same problem.

---

### Post by Simon Corlett on 2010-11-14
OK tried a few more things to help you rule them out.

Installed in virtula box. - same error.
Reinstalled all network manager packages in synaptic package manager
as above for seahorse 

error message still happening.

I am runnning ubuntu 64bit and 32bit in virtual box same errors.

I hope all this helps someone find out what's going on here.

Thanks.

---

### Post by B Crowther on 2010-11-17
This problem has been driving me mental for several weeks.  My 32 Bit netbook works fine connecting to servers via SSH, the 64 bit desktop gives me grief (both run Ubuntu 10.10.)

I have been able to get the desktop to connect sometimes by deleting the .SSH/known_hosts file in my home folder, but it has been a case of trying, trying, trying before it will connect.

After reading the suggestion in this thread about deleting the keyrings in Seahorse, I can reliably connect again.  Sure, I have to type in my password each time, but it does work.

Seahorse seems to cause a lot of strife, and I cannot fathom why this only happens on one of my two machines.

---

### Post by Bas232 on 2010-11-20
Same here as well.
SMB is very weird; it errors a lot, but Windows machines connect to my Debian-samba without any problems.
Also to home dirs, but Ubuntu 10.10 32bit refuses.
And other shares simply error a lot like all others have too.

---

### Post by bcampbell on 2010-11-27
Same for me.. it is weird.. I had a hard time connecting to my DNS-323. It wouldn't find it in the windows network. So I added a few lines some config file to resolve the ip address and it finally showed up. Now when I access the drive with the most data "Volume_2" it spins forever and gives me that crazy error. Volume_1 seems to work fine. I can access them both from any Windows OS or Mac OS.

---

### Post by PRZDLRD on 2011-01-18
Same problem with connecting to network folder bookmarks on a winxp network machine with shared folders.

HOWEVER, a KUBUNTU 10.10 install did not have this problem. (Connecting to same winxp machine)

Another item of interest, once I create the bookmark to the shared folder, sometimes it works, sometimes it gives the DBus error. I have several network folders bookmarked and sometimes opening another folder, then return the one I want will open it. The manual network open always works.

---

### Post by rburkhardt on 2011-02-09
did you find out the answer to this question, cause I am having the same issue when trying to browse my windows server. Thank you

---

### Post by WolfRage on 2011-02-09
For those having this error with a Windows networked drive, the solution that I found was to remap the drive using Samba for file sharing rather than the current Ubuntu solution. [http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

---

### Post by marantis on 2011-02-12
> **UAA said:**
> I have this message and I fixed it on Lucid by  running seahorse and removing the password of the shared folders. though  I didn't change the passwords lately.

I had the problem while trying to mount windows shares from nautilus.  the old shortcuts to the share were not working (the same error  message).

After I deleted the stored passwords the share is working again.

this works for me, too
thanks

another good tip is to use additional the fstab with a smbfs mount then u'll have a 2nd way to check the smb environment

for this u have to install additonal the smb file system with 

=> sudo apt-get install smbfs

edit the /etc/fstab and add the line

\\[pc]\[share] /mnt/[new-dir] smbfs rw,auto,uid=1000,gid=100,user=[win-user],password=[win-pass] 0 0

* the [new-dir] has to be created by you
* save this file and remount all with 

=> sudo mount -a

if the mount works with the smbfs but not with nautilus then it's a  nautilus, password, gnome problem. if it not works with smbfs, too then  its a common smb/network problem.

---

### Post by nonkreon on 2011-04-10
have you guys tried 
```
sudo update-apt-xapian-index
```
rebuilding xapian did the trick for multi problem for me :)

---

### Post by stormdragon2976 on 2011-06-10
> **nonkreon said:**
> have you guys tried 
```
sudo update-apt-xapian-index
```
rebuilding xapian did the trick for multi problem for me :)
Thanks! this worked for me. It's great to have FTP access from Nautilus again.

---

### Post by doclalor on 2011-07-02
> **kris.developer said:**
> The error was fixed by deleting the saved information for the ftp location from the keyring/ Passwords & Encryption key program.

For me too! (1) Use APPLICATIONS -> ACCESSORIES -> PASSWORDS... and delete the user/pw info. (2) Retry to connect. 

It worked for me. Thanks.

---

### Post by yooozy on 2011-08-24
I got the same problem when I plugged my ipad, 
none above solved my problem!!

---

### Post by X9Tim on 2011-10-06
Just upgraded to Maverick. Plugged in my iPhone. Got this message :(

I have NEVER managed to successfully mount my phone in Ubuntu. 
Thank goodness I still have iTunes in WinXP...

[this is my only real reason for keeping Windows, but I can find no help]

---

