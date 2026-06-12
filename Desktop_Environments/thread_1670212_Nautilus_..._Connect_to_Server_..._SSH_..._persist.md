---
title: "Nautilus ... Connect to Server ... SSH ... persistent (automate it)"
date: 2011-01-18
forum: Desktop Environments
---

### Post by boondocks on 2011-01-18
In Nautilus, you can click on:
File -> Connect to Server -> SSH
and provide all the necessary information to connect to the specific SSH server.
Then it connects to that server and opens another Nautilus window mounting that SSH connection.

This is great but is there a way to automate this such that ...
Whenever I login to this desktop, it immediately connects to that particular SSH server using the same ssh credentials as mentioned above.
So that I don't have to keep doing this manually, every time I login to the desktop.

---

### Post by nLinked on 2011-11-07
Bump! Looking exactly for this! Any one know. I could use autofs with sshfs but I just want it even more simple with Nautilus remembering to mount my SSH folder on each logon.

Edit: I just tried the following in Terminal:

nautilus sftp://USER@SERVER/home/location-of-folder

Of course the above was with the correct remote path. When I pressed enter, it opened nautilus in that remote SFTP folder. Is there a way to run this on startup, but NOT launch nautilus, just run in the background so it mounts it?

Could maybe do the above and another command to close nautilus but that's a workaround and ugly.

Any ideas?

---

### Post by adroitster on 2012-04-17
> **boondocks said:**
> In Nautilus, you can click on:
File -> Connect to Server -> SSH
and provide all the necessary information to connect to the specific SSH server.
Then it connects to that server and opens another Nautilus window mounting that SSH connection.

This is great but is there a way to automate this such that ...
Whenever I login to this desktop, it immediately connects to that particular SSH server using the same ssh credentials as mentioned above.
So that I don't have to keep doing this manually, every time I login to the desktop.

After logging into the remote SSH folder just bookmark it. Next time it won't automatically mount it but whenever you click on the bookmark you created last time it will mount it . This way you don't have to enter your details each time. Hope that helps.

---

### Post by Morbius1 on 2012-04-17
** Install Gigolo
```
sudo apt-get install gigolo
```** Go through this for a general setup: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

** Open gigolo, then Actions > Connect to Server > SSH

** Create a Gigolo Bookmark and have it Auto Mount
Right Click the gigolo mount icon for the mount > Create Bookmark > Select Auto Mount

**  [COLOR=Blue]Optional[/COLOR]: Set up a link to the mount point in Nautilus

"Connect to Server" in Gigolo or Nautilus itself creates a mount point in a hidden directory so to make it easier to find in your applications create a bookmark in Nautilus:
```
nautilus $HOME/.gvfs
```Then Bookmarks > Add bookmark

When you first login to your machine Gigolo will attempt to connect to the remote machine. If it is not available at that time it will wait until it is and then connect automatically. When you logoff from your desktop the ssh mount is safely unmounted.

---

