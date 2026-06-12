---
title: "Moving Home Directory"
date: 2009-05-27
forum: General Help
---

### Post by terrybennett on 2009-05-27
I am a totally new user and I have seen several post on this but it does not work out for me.


I have created a separate partition to use as home.  I have followed several web pages on how to move home but either get error messages or last night could not even boot.  Finally got everything back like it was and can now reboot.   

I am using 9.04 Ubuntu and have /root on sda3.  Home is on sda3  I want to move it to sda4 permanently.

Using the easiest way possible how can I move it and make it stay?

---

### Post by JohnB-nbr on 2009-05-27
terrybennett,

[Here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") is a simple guide that you can use to move your home directory. If you get specific errors, you can post them here.

Thanks

---

### Post by drs305 on 2009-05-27
terrybennet, welcome to the ubuntu forums.

Here is a link for moving home  (Edit added: same link as previous post)
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

I have one suggestion. Making your home on sda4 will use up your last primary partition. You won't be able to add any more partitions in the future. If you make sda4 an extended partition and make your /home sda5, you will be able to create additional logical partitions (sda6, 7, etc) in the future if you wish. It just gives you a bit more flexibility but isn't necessary. It's just a suggestion. I have written the following commands as sda4, which is what you wanted.

There are several guides out there. Some of the older ones fail to take advantage of the "cp" commands feature which now allows preserving file settings/permissions, which makes things simpler.

Here is how I move my $HOME. I am the only user on my computer and this $HOME partition is formatted to ext3. It is based on the link provided previously. The instructions presume you have already created /dev/sda4 and that it is formatted as ext3.

```

sudo blkid | grep "/dev/sda[COLOR="Red"]4[/COLOR]" | awk -F" " '{print $2}'   # Obtain UUID for desired new home partition

sudo cp /etc/fstab /etc/fstab.bak && gksu gedit /etc/fstab &   # Back up fstab and open it for editing
*Add or change the home reference to the following. Add the UUID designation after the = sign*:
UUID=[COLOR="Red"]xxxxx[/COLOR]  /home ext[COLOR="Red"]3[/COLOR] nodev,nosuid 0 2
*Save fstab*

sudo mkdir /newhome   && sudo chown -R *[COLOR="Red"]yourusername[/COLOR]*:  /newhome  # create new home  folder and make yourself the owner
sudo mount /dev/sda[COLOR="Red"]4[/COLOR] /newhome   # mount the new home partition 
sudo cp -P -R  /home  /newhome    # copy the contents of /home folder to the new partition
sudo mv /home /oldhome  &&  sudo mkdir /home  # Rename old home and create empty new /home in the system partition.
sudo reboot  # Restart the computer.

```

---

### Post by terrybennett on 2009-05-27
I had read something about this.   How do i make sda4 as extended?  I used the boot disk and i think gnome partition editor but i did not see an option for extended.  
Can i convert sda4 from primary to extended.  I do not have any data there at this time.


I have one suggestion. Making your home on sda4 will use up your last primary partition. You won't be able to add any more partitions in the future. If you make sda4 an extended partition and make your /home sda5, you will be able to create additional logical partitions (sda6, 7, etc) in the future if you wish. It just gives you a bit more flexibility but isn't necessary. It's just a suggestion. I have written the following commands as sda4, which is what you wanted.

[/code][/quote]

---

### Post by HereInOz on 2009-05-27
In GParted, Logical means Extended.

Also, for the moving of /home to another partition, this one worked for me:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by terrybennett on 2009-05-27
I get to this part but cannot save my changes.  Says I do not have permission.

Reboot fails now as it does not point to the correct /home.

I have rebooted from the CD 

How can I edit and save my file now ??



Edit fstab so that your new home partition actually points to /home (ie. by changing /media/home to /home) 
and finally, remount the partition with: 


> **JohnB-nbr said:**
> terrybennett,

[Here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") is a simple guide that you can use to move your home directory. If you get specific errors, you can post them here.

Thanks

---

### Post by drs305 on 2009-05-27
> **terrybennett said:**
> I get to this part but cannot save my changes.  Says I do not have permission.

Reboot fails now as it does not point to the correct /home.

I have rebooted from the CD 

How can I edit and save my file now ??



Edit fstab so that your new home partition actually points to /home (ie. by changing /media/home to /home) 
and finally, remount the partition with:

So you have followed the wiki to make the change? 

To edit fstab, you must run your editor as root (but read below first):
```

gksudo gedit /etc/fstab

```

But now you will have to mount your system partition first. If you try to run the command from the LiveCD you won't get your real fstab file.

From the LiveCd Desktop, open a terminal (Applications, Accessories, Terminal).
Make a mount point and mount your normal system partition:
```

sudo mkdir /mnt/temp
sudo mount /dev/sd[COLOR="DarkRed"]XX[/COLOR] /mnt/temp  # I believe your system is on sda[COLOR="DarkRed"]3[/COLOR]
cd /mnt/temp
gksudo gedit etc/fstab  # note: do not type "/etc/fstab"

```

Make the change to have /home point to the correct device (sdXX), whatever you decided (sda4, sda5, etc).

---

### Post by terrybennett on 2009-05-27
Okay that worked

System reboots now.   Partition editor shows sda5 as /home

I changed sda4 to extended and set up sda5 as home as i was advised above.

I do not understand why I had to do all this to change fstab.

I was navigating to the right file.  I could tell as it contained changes i made earlier following the instructions.  

Also in /etc there is /old_home and /home.  Is this home just a pointer to the new /sda5/home?

i can delete /old_home now?   i tried dragging to trash but it will not let me.

This is all confusing.  I need a dummies book to get the basics about all these mounts and folders straight .

---

### Post by drs305 on 2009-05-27
Glad everything worked out.

I don't know what was happening with the fstab file originally. Once you got to the LiveCD, however, the real system partition isn't mounted - just the contents of the CD. When you try to open a file from the Desktop, it will either mount the file from the CD or, if it doesn't exist, create a new empty one. So you first have to mount your real system partition so you can access the hard drive's system folders rather than the ones on the CD.

You shouldn't have ended up with any home folders in /etc. You *may* have an empty /home folder which you should just leave alone (and empty). The home folders in /etc and any /oldhome folders can be deleted but a safer thing to do would be to just rename the entire old home folder for a day or two until you are sure you don't need it. Do this with:
```

sudo mv /etc/old_home /etc/old_home1

```

When you are ready to delete it, I would do it with nautilus with admin privileges:
```

gksudo nautilus 

```
Use SHIFT-DEL to remove the folder so it doesn't end up in root's trash. Be careful with this as if you delete the wrong folder with this command you can't easily get it back.

---

### Post by JohnB-nbr on 2009-05-28
Glad to hear it works now Terry. You'll see that you'll learn a lot with Linux ;)

---

