---
title: "Totem Gstreamer network playback woes"
date: 2006-06-06
forum: Desktop Environments
---

### Post by DancingSun on 2006-06-06
When I start a playback of a video file on a Windows XP machine across the local samba network, the playback won't start until about 30 secs later.

It seems like Totem is buffering the video, but it's actually doing something more wacky.  My monitoring my network in and out rates, I found out that while opening a file, BOTH incoming and outbound traffic transfer at about 250 to 300 KB/s.

On the other hand, opening the same file will yield a 1 second burst of 3 MB/s incoming transfer rate and ~250 KB/s of outbound transfer.  But this only last for like 1 second, and the latency is about the same as opening a file locally.

For files around 180 MB Totem will display a blank screen for about 30 secs and then starts playing the file.  Sometimes the playback will suddenly stop.  But this only consistently happen on the same file at the same stop, so my guess is that file is not "good enough" for Totem.  Note that the same file will play perfectly in Gxine and in the old Totem from Breezy.

For larger files around 300 MB Totem won't even start the playback.  The network activity will stop after about what feels like a minute, and nothing happens on the totem GUI.  No messages whatsoever.

I never have this problem with Breezy, and I even did a clean install for Dapper.

Is anybody else having this problem?

---

### Post by DancingSun on 2006-06-12
Can somebody try this and verify if this problem exists for them?

---

### Post by mgmiller on 2006-06-12
I have a WinXP box that I can connect to with Samba from a Dapper install and Totem streams videos from that without problems. (wmv videos tend to drop a few frames, all other formats ok.)  On a samba share between 2 Dapper boxes, I can't stream wmv, but everything else works great with Totem gstreamer0.10.  The machine I am playing on is a clean install of Dapper and the file server is a 5.04 upgraded to 5.10 upgraded to 6.06.

---

### Post by pinoyskull on 2006-06-20
i have problem playing videos over the network with Totem too, every now and then it will stop then do a buffering, back in Dapper I dont recall my Totem buffering the video

someone got a solution to this?

---

### Post by disturbed1 on 2006-06-20
Define the fileshare in your fstab. The performance is better. Here's the line from my fstab, correct the values for your situation

```

//IP.ADD.OF.WINDOWS.MACHINE/WINDOWS.SHARE.NAME    /media/windows    cifs    username=$username,password=$password,noauto,uid=1000,guid=1000 0    0
``` 
The noauto option won't mount the file system on a reboot, I've had issues not passing that option.

To create the folder to mount the windows share in do this
```

sudo mkdir /media/windows
sudo chown -R 1000:1000 /media/windows

``` 
Creates the directory, and changes the ownership to user id 1000, group id 1000. Make sure the directory name you created matches the directory defined in fstab.

You can create a custom app launcher to mount the share with this command
```

gksudo "mount /media/windows"

``` and check run in terminal.


Since mounting a share using the built in samba file mounter, only apps that use the gnomevfs (Rhythmbox, Totem) can play files on samba shares. Defining a mount point in your fstab, and mounting the share this way will allow any app to read the files (VLC, Mplayer, XMMS)

---

### Post by diesis on 2006-06-24
[QUOTE=DancingSun]Is anybody else having this problem?[/QUOTE]

Yes, I think it's a bug in gnome virtual file system.

I have found that with MPEG video this does not occur, or the performance difference is not noticeable.

The problem is with AVI files: i'm not able to play them from a gvfs location, Totem tries to load the file forever.
If I manually moutn the windows share to a local mount point, the player behaves correctly.

Someone confirm this ?

 --
Diesis

---

### Post by Flavian on 2006-06-25
If I do what disturbed1 has posted I get an error message when I want to acces s the shares: 
**"Unable to mount the selected volume"**
under details:
[b]
"mount: only root can mount //192.168.0.1/florian on /media/florian"
[/b]

---

### Post by disturbed1 on 2006-06-25
[quote=Flavian]If I do what disturbed1 has posted I get an error message when I want to acces s the shares: 
**"Unable to mount the selected volume"**
under details:
[B]
"mount: only root can mount //192.168.0.1/florian on /media/florian"
[/B][/quote]
;) That is a correct error, only root can mount shares.

In a command line by itself
sudo mount /media/florian

Or create a new launcher with this
gksudo "mount /media/florian"

And put a check next to run in terminal.

---

### Post by Flavian on 2006-06-26
Thanks for your answer.
But it doesn't seem to work propperly though :(
Here is the Terminal output:

florian@octavius:~$ sudo mount /media/florian/
Password:
mount: block device //192.168.0.1/Florian is write-protected, mounting read-onlymount: cannot mount block device //192.168.0.1/Florian read-only

I have no idea what's wrong.
Can you maybe help me?

---

### Post by disturbed1 on 2006-06-26
What do you have in your fstab?

The folder that is being shared, do you have write access to it? Windows by default only allows read rights.

Did you chown the folder after you created? In nautilus, as a user, right click on the folder and check the permissions.

---

### Post by Flavian on 2006-06-27
What I have in my fstab is the following:

> //192.168.0.1/Data    /media/data    cifs    username=$username,password=$password,noauto,uid=1000,guid=1000 0    0
//192.168.0.1/Florian    /media/florian    cifs    username=$username,password=$password,noauto,uid=1000,guid=1000 0    0


Call me stupid, maybe I made a stupid mistake.
I did not change the password field to hide my password from you.
Maybe I have to put the password there??
What you see above is 1:1 simply what it says in my fstab.
Also the write permissions seem to be okay:

drwxr-xr-x

---

### Post by disturbed1 on 2006-06-27
Try this ;)

Where it says username=$username,password=$password

username=**Your username to logon to the windows pc**,password=**your windows password**

Depending on which os, and how you set up file sharing, these could be actual values or not. I'll try to explain this the bestway I can ;). My girlfriend uses Windows2000, and I created another user account on her PC. Username=keith, password=password. So I pass those options in my fstab. When we connected an XP machine to our network with guest account sharing we passed these options, username=,password=. Because there was no username nor password needed, but had issues with 100% connectivity, so I created a username and issued a password on that XP machine, and defined the correct values in fstab. You'll have to define the username and password options according to how your windows OS sharing permissions are setup.

---

### Post by Flavian on 2006-06-27
Thank you very much, disturbed1 for your answer :)
OH man, I feel like a total newbie now... (which is partially true though :D)
But that I could have known on my own... 
Thanks man, it works wonderfully now. Thanks for your patience with a newbie like me.

I really enjoy the community and the friendlieness here, compared to other communities I feel very at home here.

Good night
Flo

---

