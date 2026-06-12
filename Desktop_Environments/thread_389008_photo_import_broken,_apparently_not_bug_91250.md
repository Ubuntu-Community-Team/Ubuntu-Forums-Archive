---
title: "photo import broken, apparently not bug 91250"
date: 2007-03-20
forum: Desktop Environments
---

### Post by alexyz on 2007-03-20
edit:  solved by reformatting the camera's memory card.

---

Photo import from Canon S400 broke a couple weeks ago.  It must be [bug 9150]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")
except the behavior is different than everyone else is reporting.

1) I don't get any error messages.  I don't see "Could not claim the IO device" or anything for that matter, it just doesn't work.

2) It doesn't work as follows:  plug in camera, it's detected.  Click on import photos, the Import Photos dialog pops up.  Click on Import, nothing happens.  No errors, nothing in any log I can find.

3) When I look for a mount I can't find one.  Where is it mounted anyhow?  I guess /dev/sda - it's not there.  But the usb monitoring utilities look normal (there's a Canon camera there).

4) Tried the bug fix, editing the rules file - nothing changes.

5) I can't import from f-spot either.  Instead I get the message, "Received error 'Directory exists' while connecting to camera."  hmm... if I run from a command line I see a stack trace:

  Error DirectoryExists: LibGPhoto2.GPhotoException: Directory exists
    at LibGPhoto2.CameraFilesystem.ListFolders (System.String folder, LibGPhoto2.Context context) [0x00000] 
    at GPhotoCamera.GetFileList (System.String dir) [0x00000] 
    at GPhotoCamera.GetFileList () [0x00000] 
    at GPhotoCamera.InitializeCamera () [0x00000] 
    at MainWindow.ImportCamera (System.String camera_device) [0x00000] 

Based on some web searching, I seem to be the only person in the world who's ever encountered that error.

6) Boot windows, everything works fine.


That f-spot error is trying to tell me what's wrong.  Also the mounting weirdness - shouldn't there just be another drive there, like with a usb drive?  I've never looked before, just did the import.

I hate booting windows to deal with this, help!  I'm in the middle of a trip and taking tons of pictures every day.  :-(

---

### Post by lovelylake on 2007-03-22
I'm using digiKam to import pictures. In it I had to go to Camera --> Add camera. And then click auto detect.

---

### Post by alexyz on 2007-03-22
> **lovelylake said:**
> I'm using digiKam to import pictures. In it I had to go to Camera --> Add camera. And then click auto detect.

digikam detects the camera fine, but doesn't see any pictures on it.  Thanks for the suggestion though.  :-?

---

### Post by alexyz on 2007-03-23
Solved by reformatting the camera's memory card.  :-D

Wish I figured that out a few weeks ago, I wasted a lot of time.

---

