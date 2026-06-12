---
title: "A guide to easy instant backups to a network drive."
date: 2009-01-06
forum: General Help
---

### Post by brallan on 2009-01-06
Chances are, if you have a number of desktops & laptops on a network and a network drive, you have wanted a simple and powerful way to do backups. This guide uses two tools, [Samba]("http://us3.samba.org/samba/")'s [smbmount]("http://en.wikipedia.org/wiki/Smbmount") to mount the network drive on the local filesystem, and the amazingly useful [grsync]("http://www.opbyte.it/grsync/") backup tool.

Unfortunately, the current graphical interfaces to samba such as Places>Network> or within nautilus File>Connect to Server> will not allow you to use grsync. Rsync is an incredibly useful tool for backups, because it only requires you to write the files which have changed, making backups of many Gigabytes extremely easy (after the first, of course)

The following command will install grsync, and smbmount on your machine:

```
sudo apt-get install smbfs grsync
```

Now lets mount the network drive on the local filesystem. We will need to create a directory as mountpoint:

```
sudo mkdir /mnt/networkdrive
```

Next we can mount a Samba share using smbmount. I am assuming your network drive has a share enabled, a folder which other computers on the network can see. Smbmount mounts a Samba share to your local file system as if it were a directory on your hard disk. now we're going to make a file with the username and the password to access this samba share. While you can specify the user name and the password directly in the command mountsmb command, that's not especially secure, since they are then recorded in the .bash_history file. For better security, save credentials in a text file:

```
sudo gedit /root/.smb_credentials
```

and type in your username and password:

```
username=<my user name>
password=<my password>

```

Make sure it has a blank line at the end. Now make it unreadable except by root:

```
sudo chmod 600 /root/.smb_credentials
```

next change the smbmount command to include your share details:

```
sudo smbmount //smb/share /mnt/networkdrive/ -o credentials=/root/.smb_credentials,uid=YourUserID,gid=YourGroupID 0 0
```

//smb/share refers to the path to the samba share, it is likely an IP like //192.168.15.7/Documents/, and share is the name of the shared directory. /mnt/networkdrive refers to the mount point we created earlier. the uid and gid commands will allow you to mount it as your user rather than as root.

if you get an error which reads:

```
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```
or ```
mount error 5 = Input/output error
```


then you will likely need to use these three commands:

```
sudo su
echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
exit
```

before repeating the above smbmount command. I'm not really sure why, but it works for me in 8.04, 8.10, and 9.04 on various machines.

Once the Samba share has been mounted, you can back up local files and directories on it using rsync, or grsync, the graphical front end to rsync. It also allows you to create and manage multiple backup profiles (called sessions). To create a new profile, press the program's Add button, give the profile a name, and press OK. You can then enter the paths to the source and destination directories and specify the desired options by ticking check boxes. If you are not sure what each check box does, hover the mouse over it to see a pop-up window with a brief explanation.

That's all there is to it. Once you have the basic backup system in place, you can improve it. For example, you can create a simple bash script that runs the specified rsync commands, and you can schedule backups using tools like KCron.

special thanks to [Dmitri Popov]("http://www.linux.com/feature/118225") on which this guide is largely based.

---

### Post by brallan on 2009-07-23
Go figure, I found out that the drive DOES get mounted when you use the Connect to Server option in nautilus, and that address is inside:

~/.gvfs/

don't see it in nautilus? press "CTRL + h" to show hidden files and directories.

that is to say, something like:

/home/username/.gvfs/public en 192.168.15.99/

("en" is Spanish, in english its probably "in" "on" or "at".)

if i am trying to access the files on:

smb://192.168.15.99/public/

and the above full /.gvfs/ address can be pasted into grsync and it works quite nicely as a proper mount point, taking out the unnecessary step of logging on as root and modifying that config file... unless of course, you want to back up your /home/username directory. In that case, it may give you errors by trying to recursively copy the .gvfs folder. The "don't leave filesystem" option in grsync may help, or else add the "additional options" under advanced options, type ```
--exclude=.gvfs
```

hopefully one day this GUI will allow the ability choose the mountpoint - something easier to deal with like /mnt/networkdrive or /media/LANdisk and that nautilus will not hide its location, nor put it inside the /home directory, which you are very likely wanting to backup using a network drive.

---

