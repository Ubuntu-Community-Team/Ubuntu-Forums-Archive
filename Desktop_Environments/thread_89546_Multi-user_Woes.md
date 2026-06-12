---
title: "Multi-user Woes"
date: 2005-11-12
forum: Desktop Environments
---

### Post by thedevilsjester on 2005-11-12
Everytime I insert a CD, hook up a usb device (camera, usb drive, etc...), it loads it up in all logged in accounts.  This effect is mainly seen with CDs that play on both accounts simultainously, or CDs/USB/etc.. that the 'first one to get to it' gets ownership, so the rest of the users cannot access, or mount it.

Is there any fix for this?

---

### Post by Remmelas on 2005-11-13
if all your users belong to the same group, you could set the device as their GID in the fstab file.

---

### Post by thedevilsjester on 2005-11-13
The problem is with the auto mount system, and I cannot put everything in the fstab because for the most part all of the usb devices are dynamic.  I dont know how many will be connected, or what type, or what slot, at any one time.  So creating an fstab entry for that is kind of complicated.

For the time being I have disabled all automounting functionality, until these issues are worked out by the various software projects, but am having difficulty finding an option that shows an icon for a device on the desktop (where a double click mounts and opens it, etc...) like I used to have in kde (without having to have an fstab entry)

---

### Post by dbott67 on 2005-11-13
We ***could*** do something about the other users.  I know some people... 

But remember, if I do this for you... ;)

-Don Corleone

---

### Post by thedevilsjester on 2005-11-13
That doesnt really solve the problem though, does it ? :)

Even with fstab entries for my cdrom, I cant seem to get a media desktop icon (with the mount/unmount/eject/ect... options)  Anyone know how?  It was very simple in KDE, but I dont want to have to switch to kde just to get decent desktop icons.

---

### Post by dbott67 on 2005-11-13
It doesn't fix the problem, but at least it stops the complaining!  Okay... I'll put away my 'smart aleck' hat.  :)

There is a 'Disk Mounter'  applet for the panels (see screenshot).

What happens if you switch users and then unplug & re-connect the device?  Are the permissions set for the current user?

If this is the case, perhaps you could (or the script writers among us) write a script that users could run that would unmout & re-mount the device.

Or maybe I do not fully understand the nature of your problem...

-Dave

---

### Post by thedevilsjester on 2005-11-13
It doesnt matter what user I am, when I connect a device it matters what user gets to it first.

Let me explain, if I have two users logged in, and I insert a CD,  BOTH accounts will simultainously attempt to mount/play/etc... the cd.  Which ever one gets to it first, gets control.  (I.E. if the 2nd account was just a hair slower for some reason, the 1st account would grab it)   For CDs this is really bad because even though only one user has ownership of it, it will still start the media player on BOTH accounts, playing the same cd at the same time.   It also makes it impossible for user 2 to unmount the cd and put in a new one if they want to change (assuming user 1's account grabbed the ownership first), they have to switch to the other person (which isnt always possible with password protection) and log them out, or unmount the cd from their account.

Its worse with my USB cameras and other devices because whoever gets it first, has complete ownership of it, and the other user cannot even access it.  (I.E. my wife plugs the camera in, while logged into her account, and my account grabs it, she cannot view/copy/import/etc... the images, it says access denied.  However if her account was faster (or I wasnt logged in too) then all is well)

A disk mounter on the task bar is not a good solution (not to mention its a really horrible disk mounter, kde has a much nicer one), I need a desktop icon, just like the ones that the automounter creates, and just like the ones that KDE has,but I dont want to have to install kde for such a simple thing.

---

