---
title: "How to make Network Places mounts &quot;sticky&quot;"
date: 2010-10-08
forum: Desktop Environments
---

### Post by windofkeltia on 2010-10-08
While I realize the undesirable security implications of doing this, I wonder how mounts from my Places -> Network can be automatically preserved between boots?

Yes, I know about Bookmarking in the File Browser, but I'd like the various desktop icons to be there already.

I know it's pure laziness, but indulge me here if possible. Or just slap me; I can take it.

Thanks,

Russ

---

### Post by undfined on 2010-10-08
For Windows shares: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

A GUI tool would be nice...

---

### Post by Morbius1 on 2010-10-08
I used to use entries in fstab to automount remote shares but then I found a remarkable little utility called gigolo:
```
sudo apt-get install gigolo
```And just in case you already don't have it installed:
```
sudo apt-get install fuse
```[COLOR=Blue]**EDIT**[/COLOR]: As noted below by Kronalias you may also need to install gvfs-backends:
```
sudo apt-get install gvfs-backends
```It's considered a network browser but it does have the ability to automount remote shares.

The procedure is relative simple:
When you first bring it up make a change in the preferences:
[B]Edit > Preferences > Interface>
Select "Show Side Panel"[/B]
**Select "Start minimized in the Notification Area"**
**Disable "Show auto-connect error messages"**

Then you browse to the share using the Network Tab on gigolo
Then you bookmark the share by right clicking the share icon and select **"Create Bookmark"**
When you bookmark it select the **"Auto-connect"** option

Then have gigolo start at login:
**System > Preferences > StartUp Applications > Add > Command = gigolo**

[COLOR=Blue] In Xubuntu:[/COLOR]
**Application Menu > Settings > Settings Manager > Session and Startup > Application Autostart > Add > Name = Gigolo , Command = gigolo**

When you login it will automatically mount remote shares and you will see an icon on your desktop. 

[COLOR=Blue]In Xubuntu[/COLOR] an icon is not created on the Desktop so create a launcher for it:

Right Click the desktop > Create Launcher > Name = MyLan, Command:
```
thunar /home/your-user-name/.gvfs
```This auto-connect function has one other feature. If the remote share isn't available or if the connection is lost gigolo will scan the network every 60 seconds ( user adjustable ) and mount it when it finds it.

It will make more sense when you use it and it will take less time to implement than it took for me to try to explain it :wink:

---

### Post by drtanz on 2011-11-02
Thanks, this is what I get when trying to install fuse



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fuse is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'fuse' has no installation candidate

---

### Post by Kronalias on 2011-11-02
Gigolo is slightly borked in that it needs a bit of fuse that isn't installed automatically.

Try this:
sudo apt-get install gvfs-backends

Then Gigolo can be used as described above.

---

### Post by drtanz on 2011-11-04
that worked thanks!

---

