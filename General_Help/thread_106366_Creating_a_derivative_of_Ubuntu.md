---
title: "Creating a derivative of Ubuntu"
date: 2005-12-20
forum: General Help
---

### Post by TomB on 2005-12-20
I'm not sure where this is suppose to be posted but here goes.

Where would I need to start to take say Ubuntu (Not LiveCD) and remaster it to create my own version?  Is it pretty much the same process as the LiveCD?  Could anyone point me in the right direction, many thanks in advanced.

TomB

---

### Post by h0und on 2005-12-20
Yeah, this is a subject of particular interest to me as well!  I'd like to see if anyone knows anything about it.

---

### Post by stuporglue on 2005-12-20
I'm also looking at this. I'd like to make an Xubuntu install CD. 

Ubuntu uses d-i, the Debian Installer. Since Debian is an older (bigger?) project, there's more info searching for d-i, than just searching for "custom Ubuntu install CD". 

I think some parts of it will be similar to rebuilding a LiveCD, since the installer is essentially a live Linux session, which runs a specific script/program. 

If you're looking for a regular Ubuntu install, but just don't want to answer the same questions each time, you should just look at preseed files. You can pre-answer most of the installer questions in one of these files and remastering the CD with a new preseed file would be a bit easier, I think.

---

### Post by TomB on 2005-12-20
I would like to remove some packages and replace with others, also change some branding.  So I can just simply follow the LiveCD remastering and edit some extra files pretty much?

---

### Post by stuporglue on 2005-12-21
I don't know for sure, as I haven't had the time to try yet, and my need hasn't overcome my lazyness. :-)

I think so, but you probably also need to watch for the d-i scripts. When you find what tells it the difference between the server and regular installs, then you'll be on the right track.

---

### Post by Marsolin on 2006-03-16
I've been having trouble here.  I can remaster the CD, but it fails when installing to the target.  As a baseline I copied the files to a directory and created a new iso.  That worked, but when I regenerate the Packages and Release files then nothing installs in the tasksel portion.  I suspect it is due to the Release.gpg file.  I created one of my own, but I don't know how to add my key to make it legit.  This is a Debian installer thing because remastering Debian Etch has the same problem.  I was able to remaster Sarge, but that was before apt supported authentication.

Does anyone know how to get past this step?

Basic steps to get started:
1. Mount the dapper install iso
2. Copy the files to a new directory (make sure to get the hidden .disk directory)
3. Change permissions on all of the files to allow them to by written to
4. Add files to the pool
5. Modify the preseed file to include your packages (Kubuntu is better to use here because it has a preseed example)
6. If you change the name of the preseed file, make sure isolinux.cfg gets updated to call the right one
7. Rebuild the Packages and Release (as I mentioned previously, I'm still having problems with this step)
8. Create iso by running "mkisofs -o new-installer.iso -l -r -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table image".  new-installer.iso can be replaced with the filename you want the iso to be.  image can be replaced with the directory your files are in.

Steps 4 through 7 are where I'm currently having issues.  I was able to get these working on the Sarge installer, but not Etch, which Dapper uses.

Chad
[http://linuxappfinder.com](http://linuxappfinder.com)

---

### Post by Marsolin on 2006-03-16
I just found this link to the Wiki.  [https://wiki.ubuntu.com/InstallCDCustomizationHowTo](https://wiki.ubuntu.com/InstallCDCustomizationHowTo)  It clearly explains how to remaster the CD and has the details for the step that is throwing me.  I haven't tried it yet.

Chad
[http://linuxappfinder.com](http://linuxappfinder.com)

---

