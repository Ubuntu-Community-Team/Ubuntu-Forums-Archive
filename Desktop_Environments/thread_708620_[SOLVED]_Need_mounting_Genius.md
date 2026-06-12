---
title: "[SOLVED] Need mounting Genius"
date: 2008-02-26
forum: Desktop Environments
---

### Post by MacDuff on 2008-02-26
This belongs on the Network section but multiple postings there have not produced any responses so please forgive me.

I have been trying to auto-mount a DNS-323 NAS device on a network containing a Ubuntu box for almost two weeks without success.  
The NAS contains two volumes, Volume-1 and Volume-2. The network consists of a Windows XP Box and an Ubuntu 7.10 box. The NAS appears on a Windows Network immediately it is booted.  The two volumes are identified on the XP box as drives "V" and "W" which were assigned when setting up the NAS using the windows software with which it is shipped.

Unlike Windows computers, the NAS does not appear in the Ubuntu (Gnome desktop) network using [Places], [Network].  BUT I can mount it and view its contents by using [Places], [Connect to Server[, [Service Type: Windows share[, and entering the IP address 192.168.1.175.

Although I can see the NAS and can drag and drop items from/to it, I cannot make applications on the Ubuntu box interact with it.  Mount or permission problem?.

I can however, manually mount the device to /media/RAID and /media/OnLineBAK , using command lines, and then use it with applications.

My problem is that I cannot mount the device automatically using fstab. 

When I try to insert a line in fstab that should mount the device, Ubuntu takes a long time to re-start and then when I try to view the device using a file manager, it takes a minute or more for the file manager to display the directory and the mount point is not visible let alone what it should contain.

I must have have read every posting about mounting samba shares and tried every suggestion but none of them work for me. 

Here is the info on one of the mount points:
File Name: RAID
Location /media
File Type: folder (inode/directory)
Permission drwxr-xr-x
Owner:Group  root:root

The last few lines of fstab are:

proc /proc proc defaults 0 0
# Entry for /dev/hdb2 :
UUID=814e801c-320a-4130-8d29-5787d967b7a9 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdb5 :
UUID=ad7a3348-7766-44c7-9347-ed6a7891eb76 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

#Don't know what the line below does
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 

#The line below should mount the NAS but it just causes problems
//192.168.1.175/Volume_1 /media/RAID smbfs auto,credentials=/etc/smbcredentials,workgroup=DHLTD,gid=smb,uid=1000,fmask=770,dmask=770,rw 0 0


The only other clue I have found is that when I re-boot with the problem line in fstab,  the close pauses and displays the following lines before re-start:

NetworkManager: <WARN> nm_signal_handler()| Caught signal 15, shutting down normally.
NetworkManager: <info> Caught termination signal
NetworkManager: <debug> [1204060254, 740049] nm_print_open_socks()| Open Sockets List:
NetworkManager: <debug> [1204060254, 740098] nm_print_open_socks()| Open Sockets List Done:
NetworkManager: <WARN> nm_hal_definit()| libhal shutdown failed - Connection is closed

So where is the problem?

I have posted several pleas for help in the past week and have received no response.  There must be someone out there who knows enough about Ubuntu and/or Linux to suggest something else I can try even if nobody knows how to fix the problem.

There is a post-script.  Apparently the DNS-323 formats drives using an ext2 or ext3 file system yet uses a Windows OS for network communication.  I would not think that is important but who knows?

Thanks for any crumbs you can throw my way.

---

### Post by pdub on 2008-02-26
I have the exact same NAS working with Gutsy and Vista.

Here is the line from my fstab

```
//192.168.10.10/Volume_1 /DMedia cifs credentials=/home/sam/.smbcredentials,uid=sam,gid=users 0 0
```

The smbcredentials file should probably be in your home folder, like mine. My smbcredentials file contains the username and password that were created on the DNS-323 using the web interface.

Here is the mount point.

```
drwxr-x-r-x   8 sam users     0 2008-02-18 19:20 DMedia
```

I am using cifs instead of smbfs, see this thread.

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

I would recommend that you remove and re-create your mount points first. I initially had a problem with slow boot so I deleted the DMedia folder and re-created it. If you are the primary user, you should likely own the folder, like I do.

Hope this helps.

---

### Post by MacDuff on 2008-02-27
Thanks pdub:

I will try that tomorrow.  Too tired to do more tonight.  I have a question regarding your reply however.

you added some code:
> Here is the mount point.

Code:

drwxr-x-r-x   8 sam users     0 2008-02-18 19:20 DMedia



Where does this come from and where do I put it?  That may seem like a stupid question and maybe it is. I can hardly keep my eyes open.  It's been a long day spent fighting with a wireless router on a client's Windows network system.

---

### Post by pdub on 2008-02-27
In your post you listed the mount point as:

```
File Name: RAID
Location /media
File Type: folder (inode/directory)
Permission drwxr-xr-x
Owner:Group root:root
```


So mine is

```
File Name: DMedia
Location /
File Type: folder (inode/directory)
Permission drwxr-xr-x
Owner:Group sam:users
```

If you wish to change your settings you can use chown to take ownership of the folder, like this:

```
sudo chown your_user_name_here /media/RAID
```

---

### Post by MacDuff on 2008-02-27
Well pdub, that did change things somewhat.  I seem to recall that I am back at the point I was at two weeks ago.

I moved  the .smbcredentials file to /home/mac as you suggested

changed ownership of the two mount points as you suggested. They now show up as:
/media/OnLineBAK
Type folder
Permission drwxrwxr-x
Owner:Group  mac:root

/media/RAID
Type folder
Permission drwxrwxr-x
Owner:Group  mac:root

I replaced the commands in fstab as suggested.  They now read:
//192.168.1.175/Volume_1 /Media/RAID cifs credentials=/home/mac/.smbcredentials,uid=mac,gid=users 0 0 
//192.168.1.175/Volume_2 /Media/OnLineBAK cifs credentials=/home/mac/.smbcredentials,uid=mac,gid=users 0 0

Oh, yes, and I added a user and password to the DNS-323, which had not been there before and I made sure they were the same as those I use to run my Ubuntu system.

But the NAS still does not mount. The good things are that boot-up has speeded up and it takes only an instant to view the contents of /media and when I look in/media, the mount points are still visible but there is nothing in them.

And people think that accounting is difficult... not a patch on this, thankfully.

I really do appreciate you suggestions and there must be a solution.  There always seems to be but it is sometimes very obscure.  Do you have any more sage advice to offer?

---

### Post by MacDuff on 2008-02-27
Just noticed another tiny problem.  I can no longer see any devices on the windows network.

Selecting [Places], [Network], displays an icon for Windows Network but opening that only produces a blank screen.  There used to be a Windows XP computer there and of course there should also be the DNS-323 NAS but nada.

Does this provide a further clue as to what may be wrong?

Addendum:  After commenting out the mount lines in fstab and re-starting the Ubuntu box, I can again see the Samba shares (XP Box and Virtual machine on Ubutntu Box0 but not, of course the DSN-323

---

### Post by pdub on 2008-02-27
When you created the user account on the DNS-323 did you give the account permissions to the volumes? This is done in the Advanced tab under the Network Access section.

Unless you changed it on your system, the media folder is lowercase (media not Media). Linux is case sensitive.

//192.168.1.175/Volume_1 /**Media**/RAID cifs credentials=/home/mac/.smbcredentials,uid=mac,gid= users 0 0

---

### Post by MacDuff on 2008-02-27
CRAP!  Have you ever wanted to beat yourself about the head and didn't have a club handy?

I KNEW that Linux commands are case sensitive (but years of Window OS in various flavours have spoiled me).  I don't know how many times I looked at every character of those commands to check for accuracy and did not notice the upper case "M" in media.

That fixed the problem.  I owe you a big one.

As for your other suggestion that I give mount permissions to the volumes in the DNS-323 setup routine, I had a look at that but it appears that I have to set permissions for each folder and cannot grant permission for the entire volume.  Of course I could very well be wrong about that too.  If you know a way to grant blanket permission without having to define each folder, please let me know.

Thank you most sincerely for the helpful suggestions and particularly  for finding and pointing out my error.  

Mac

---

### Post by pdub on 2008-02-27
Cool, glad to help.

---

