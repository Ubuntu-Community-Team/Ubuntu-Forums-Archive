---
title: "rename mounted volume"
date: 2008-04-26
forum: Desktop Environments
---

### Post by jamaas on 2008-04-26
I just upgraded to 8.04 from 7.10 and it found my M$ partition and mounts it but I can not change the name of the volume on my desktop, no "rename" on the left-click list, and can not change it when I go to properties.  Have I missed something or is this a little bug?  Also after the upgrade, my network drives have disappeared, would be nice to get them back.  Relative noob here, thanks for any/suggestions.

Jim

---

### Post by sicofante on 2008-04-26
Well, this is some design failure (again... :-(). It makes "some" sense that mounted volumes cannot be renamed by non-root users, and you're not a root user by default in Ubuntu so your mounted drives showing up in your desktop have their "Rename..." right-clic menu entry greyed out.

But you can run gksu nautilus from a terminal or Alt-F2 to gain root privileges, go to "Computer", right clic on the volume you want to rename and voila, the "Rename..." menu entry is right there in pure black on white.

But don't get too excited. Trying to do so will show you an error message (see attached picture), no matter if you unmount the volume first or not.

For now, changing a volume's name takes some knowledge about the partition's type, then using the right tool, as explained here:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

(EDIT: And don't forget to restart your computer after you do this. No, Ctrl+Alt+Backspace won't do.)

Really, Nautilus should do just that when you select "Rename..." from the right-clic menu. I just don't get why there's an option that will yield the same error in every circumstance, with an error message not saying anything useful to mere mortals.

I suppose it's time for a bug report... :-(

---

### Post by jamaas on 2008-04-27
That worked ... but a bit convoluted!  Thanks a bunch.

Jim

---

### Post by sicofante on 2008-04-27
You're welcome. It seems this bug is an old one. I've tried to revive it here

[https://bugs.launchpad.net/ubuntu/+bug/107306](https://bugs.launchpad.net/ubuntu/+bug/107306)

but I'm not sure I've got it right (the bug is till tagged as "Invalid" ). Feel free to add your experience to that bug report.

---

### Post by autocrosser on 2008-04-27
I have been posting the current work-around--I'm not the author (can't remember who it was)--this was found during Hardy testing-----


EUREKA!
i scoured the net and the forums and was able to gerry-rig a work-around. i don't remember where all i got this information, so if it looks familiar or you found similar stuff, please let me know so i can give the true geniuses credit.

the problem seems to be with the information hal is giving gvfs; apparently it's a "known-issue," as i bleary-eyed read through hundred of launchpad posts. i don't know if this solution is a permanent fix, but it worked for me right now and i don't see any negative effects.

step 1:
create a directory in your /usr/share/hal/fdi/information directory to hold the new .fdi files we're going to be creating. the posts i've read seem to have the number "90" before the name and although i didn't see anything mandating this, it's probably a good idea.
Code:

sudo mkdir /usr/share/hal/fdi/information/90media

step 2:
"discover" the uuid for the volumes which aren't being displayed properly. you could use either the kde-hal-device-manager program or the much simpler cli command
Code:

ls -l /dev/disk/by-uuid

step 3:
now, we have to place files in our newly created directory for each of the "misbehaving" drives. the files are simple xml and the syntax is pretty easy. once again, the numbering scheme seems to come into play, so i named my internal backup drive file "90-backup.fdi."
Code:

sudo nano /usr/share/hal/fdi/information/90media/90-backup.fdi

and in that new file type:
Code:

<?xml version="1.0" encoding="UTF-8"?><!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
  <match key="info.category" string="volume">
  <match key="volume.uuid" string="your_volume's_uuid">
  <merge key="volume.label" type="string">the name you want for the volume</merge>
  </match>
  </match>
</device>
</deviceinfo>

step 4:
do that for all of your volumes, following the simple xml syntax and restart. voila.

---

### Post by sicofante on 2008-04-27
> **autocrosser said:**
> now, we have to place files in our newly created directory for each of the "misbehaving" drives.
I'm not sure we're taking about the same here. There are no "misbehaving" drives. All drives respond the same to the same "Rename..." request, it's not just a per-drive issue. The problem is the behaviour of that Nautilus right-click menu option, not just renaming the volumes, which can be easily done using labels on the partitions or by applying your solution.

---

### Post by autocrosser on 2008-04-27
This is just another way to rename your drives--wording not mine...

Advantage to this method: change stays with the drive as long as the UUID is not changed----:)

---

