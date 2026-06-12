---
title: "Desktop Icon Positioning"
date: 2015-10-06
forum: Desktop Environments
---

### Post by kaz-kanso on 2015-10-06
I am working on a project where we are using a Ubuntu distribution pre-configured with some software that we have created. The problem that I am facing is with the configuration of the desktop environment.

Essentially, there are two processes that are being followed, the initial installation and then the upgrade. First, for the initial installation we generate the ext4 partition via a number of scripts that install a fresh Ubuntu, creates the user and configures many UI settings using gsettings and gvfs-set-attribute, and of course installs that software that we are distributing. Once booted into this image, all settings have taken effect as expected.

The approximate steps that are followed to configure the UI in the installation image are as follows:

1) create the .desktop file manually on the desktop, and mark as executable
2) chroot into the root fs, and change to the desired user.
3) use dbus-launch to create the dbus session [inside the chroot]
4) use gvfs-set-attribute to set the icon position [inside chroot]
5) run sync to ensure all settings are saved to disk [inside chroot]
6) kill the dbus session & exist chroot

For the upgrade process things are a little different. There are times when this upgrade will need to create a new desktop icon, and position it using the same method as before. However this is not always successful, sometimes it works sometimes it does not. The events that are performed in this case are as follows:

1) User runs the update program
2) .desktop is created on the users desktop and marked as executable
3) use gvfs-set-attribute to set the icon position (this is using the users login dbus session)
4) perform sync and wait 10 seconds
5) move the newly created desktop file to some temporary location and then back to its original position (this forces the desktop to refresh the gvfs information, including the icon position)

Without waiting in step 4 is only works approx 50% of the time, with the wait it works 90/95% of the time. I am sure there is a better way of doing this, but have had difficulties in finding it.

Ideally, it would be possible to position the icon before its created, however that does not seem to be possible as gvfs-set-attribute will complain about non-existent file.

I suspect the problem is the hacky way I move the desktop icon, then move it back almost instantaneously to force the icon location to be reloaded and take effect instantly. Without doing this the user will need to manually refresh the desktop to see the new icon position. Is there a better way of doing this?

---

