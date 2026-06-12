---
title: "jpilot won't sync after edgy upgrade"
date: 2006-10-28
forum: Desktop Environments
---

### Post by TheOldFellow on 2006-10-28
I have used jpilot with my Palm Vx (Serial note, not USB) with bressy for ages.  No problems.  I upgrade to edgy, note that pilot-link is upgraded. Now sync fails:

dlp_ReadSysInfo error
Exiting with status SYNC_ERROR_PI_CONNECT

This happens if the sync is started from the cradle or from jpilot.

Running pilot-xfer directly works fine (i.e edgy has correctly installed pilot-link, and it works)

If anyone else can sync a serial palm with edgy and jpilot, I'd like to know how!

Although I don't like evolution, I tried it with gnome-pilot and that works, but as I say, I don't like evolution at all.

Any tips?

R.

---

### Post by Shay Stephens on 2006-10-29
No solution yet.  I have a usb handspring visor.  Same problem, it won't connect with jpilot but will work with gpilot.

I used to be able to connect on /dev/ttyUSB1.  But now that is gone, and it only shows breifly when I push the sync button on the cradle.  But I have to click on the sync button in the app before I do so on the cradle.  So the two never see each other and no connection can be made.

And the only way I know to add a file in gnome-pilot is to run this from the command line:
```
gpilot-install-file --later "/file/name"
```

When I next sync with gpilot the file gets installed on the pilot, in my case plucker ebooks.  But it is not very convenient to say the least.  I would much rather be able to right click on a file and have that command to install the file run, but don't know how yet.

---

### Post by dretep on 2006-11-03
* bump *

I've got the same issue after upgrading yesterday.  I've been doing some digging but haven't come up with anything yet.  :(

---

### Post by Shay Stephens on 2006-11-03
Still no joy from jpilot land.  So instead I have been working on making gpilot easier to install files.  What I do now is place the files I want to upload in an install folder and then run this script:

```
#!/bin/bash
#Program to install files on my PDA using gpilot.

#install files
function installFiles(){
	cd [COLOR="Red"]/home/user/MyPDA/install[/COLOR]
	gpilot-install-file -now *.*
	}

#delete files
function deleteFiles(){
	rm *.*
	}

#kick of the program
installFiles
#delete files from install folder now that they are uploaded
deleteFiles
```

To make it work for your computer, create an install folder, and just change the path (in red) to the actual path on your computer where the install folder is located.  Save the program somewhere handy and give it execute permissions.  When ran, it will ask you to puch the sync button and when it is done, it will clean out the install folder.

---

### Post by TheOldFellow on 2006-11-18
Bug #68815 in Malone.  Please everyone go and add a comment, then maybe we can get some action.

---

### Post by jonrkc on 2007-01-20
I'm using Dapper 6.06 and here's what happened to me: After some upgrades during the past week or two, JPilot quit working and it's exactly the same problem described here.  Now bear in mind this is Dapper, not Edgy.  So it's something in those upgrades that took place between December 28, 2006 (my last sync--and it was working perfectly every time for months) and probably some time in the first week of January.  

I remember that there was some upgrade that affected the kernel, because nVidia stuff had to be included with it, at least for my system, and I was afraid my nVidia card would not work again and I'd have two days trying to solve that.  But the display was unaffected.  

I want to emphasize that I'm having EXACTLY the same problem as here, same error message, etc.  It seems JPilot would work IF you could press the sync button on the device after it asks you to--JPilot is communicating with the USB device, it says so--but that's impossible because all you can do after initiating connection with the device, which REQUIRES pressing its sync button, is CANCEL the operation.  So an endless loop of frustration.

---

