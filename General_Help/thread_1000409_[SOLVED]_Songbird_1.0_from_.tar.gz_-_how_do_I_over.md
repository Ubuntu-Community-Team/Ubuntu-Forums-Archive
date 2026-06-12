---
title: "[SOLVED] Songbird 1.0 from .tar.gz - how do I overwrite/uninstall?"
date: 2008-12-02
forum: General Help
---

### Post by adamjoz on 2008-12-02
I made a mistake of installing the new release from the .tar.gz rather than .deb file. Having read some posts I realised that it's not a sensible thing, as I can't even find a way to open it. I'm planning to wait for a .deb release in the future.

Q: Will the .deb installation overwrite the current version from .tar.gz or would I need to uninstall it myself. If the latter, what is the easiest way to do it?

Thanks a ton.

---

### Post by spiderbatdad on 2008-12-02
checkinstall is often a good option when installing packages from source:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
basically install it and run checkinstall instead of make install.


Not sure about songbird...look for an uninstall with your search tool...possibly in /usr/local/bin...otherwise manually delete songbird files.

---

### Post by jbrown96 on 2008-12-02
Songbird isn't released as a .deb unfortunately. However, it takes almost no effort to install it. 
1) Extract the tarball. Easiest way to is use the file browse to find it; right click and choose to extract. If it's not in your home folder, move the resulting folder there. Once it is extracted, you can delete the tarball. 
2) Optional. I don't like lots of folders. I rename the Songbird folder to .Songbird The . in front makes it hidden. If you do this, the folder will disappear. I believe that Crtl+H shows hidden folders, if not, show them in the View menu. 
3) Make Songbird executable. In the Songbird folder, there should be a file called Songbird. Right click on it and go to properties. In the permissions tab, check the box to make it executable. You can now open Songbird by double clicking on the icon.
4) Create shortcuts. You can create a panel icon by doing the following. Right click on the top bar and select add to panel. Create custom application launcher. Give it the names and descriptions that you want. For the command, click browse (if you hid the folder earlier, you may need to right click to show hidden folders), locate the Songbird file that we made executable. Click on the spring to load an icon. Browse to the Songbird folder. I can't remember the specific folder, but I think it is chrome. It will simply be an empty folder. Click ok and the icon should be displayed. Select it and you are finished. You can also add an entry to your main menu by going to System-->Preferences-->Main Menu and following the same procedure.

---

### Post by Shazaam on 2008-12-02
Find out where you extracted the tar.gz. Open terminal, cd (change directory) to that location.
Example if you extracted it to your desktop:::
```
cd /home/username/Desktop
```
(where username is YOUR user name)
and enter this...
```
sudo make uninstall
```
Should get rid of it.

---

### Post by adamjoz on 2008-12-02
spiderbatdad: Thanks for the suggestion, I'll def keep that in mind in the future.


jbrown96: I had followed 1) - 3) previously to install it before finding a link to [http://unterhund.wordpress.com/2008/11/26/quick-songbird-1-rc3-linux-installer-update/](http://unterhund.wordpress.com/2008/11/26/quick-songbird-1-rc3-linux-installer-update/)

Does this mean that no files are installed outside of the .Songbird folder during this process? If so, it would seem that deleting the folder would ultimately uninstall the app.

Thanks for 4), I'll try that with some other apps, but for the music player I'd like to go for the safest option for now and wait for the community to submit the .deb file.


Shazaam: Deleted the folder already (I assumed those were the installation files like in Windows, rookie mistake). Thanks for that and I'll try the uninstall command in other cases.


Cheers.

---

### Post by jbrown96 on 2008-12-03
It's just the Songbird folder, but it may store some config items in a hidden folder in your home directory. Probably something like .songbird

---

