---
title: "problems with file manegment since upgrade"
date: 2009-01-05
forum: Desktop Environments
---

### Post by linette on 2009-01-05
Hi everyone,
I've been having some problems with my system since the upgrade from Hardy to Ibex.

The summary is, nautilus seems to be slowing down and breaking and I'm getting a lot of Dbus errors.

More detail:

I first spotted the problems when trying to manage my phone with bluetooth (which worked pretty well under hardy)

It will start of connecting well and at a fair speed.  I'll do some file operations (maybe copy some files, maybe delete) and it will be fine for a little while, but will slow down.
I'll get a dialogue box that says "preparing to delete" or "preparing to copy" which will sit there for several minutes.  If I hit the cross icon it seems to do nothing.

If I try again it seems to disconnect/unmount the device.
If I try to browse the device again I get the message: 

"Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again."

delete from phone with usb cable:
Everything was working fine at first, then I started getting errors.  Having just successfully deleted a few images from my phone, I try and delete the next one and get:

"Error deleting file: -1: Unspecified error"
then if i try to delete the same file again, in the same fashion I get the error message:
"Error deleting file: -2: Bad parameters"
And it always worries me when I do an identical action and get a different message.

I thought this oddness was restricted to the phone, but then when a chum was logged in to their user account, I got the error that they didn't have the user permission to eject a CD (they were using the hardware eject button), and a similar Dbus error to the one above.  After a log out and a log back in they could eject with no problems.

I'm a n00b, and only just learning how to escape windows, so when it comes to troubleshooting and log file etc, I'm not even sure where to begin.  Any help people can give for the above problem is very gratefully received!!!

---

