---
title: "Xfce - How to Launch Shotwell &amp; Download Images?"
date: 2013-05-17
forum: Desktop Environments
---

### Post by 2CV67 on 2013-05-17
Previously, using Lubuntu, whenever I hot-plugged my camera (Panasonic TZ18) then I automatically was offered a choice of "Open in File-Manager or Open Shotwell".

Since shifting to Xfce, I can't get this procedure to auto-launch.

As soon as I hot-plug the camera, it appears in Thunar, but nothing happens.
I need to click on the camera in Thunar (to mount it?) then run "/usr/bin/shotwell" in Terminal before Shotwell opens & sees the camera.

I suppose my problem is that I don't really understand the options in "Settings > Removable Drives and Media".
I tried "Cameras > Import digital photographs when connected > Command: /usr/bin/shotwell" but that makes no difference.
I also tried "Storage > Mount removable drives when hot-plugged & Mount removable media when inserted" (without fully understanding what that means) but that makes do difference either.

Thanks for any advice!

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/camera_zps3d167b72.jpg[/IMG]

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/storage_zpsba774377.jpg[/IMG]

---

### Post by 2CV67 on 2013-05-18
OK - I installed "autofs" & now everything works just fine.

How was I supposed to know that????  :confused:

---

### Post by 2CV67 on 2013-05-18
Well - this is wierd...

Last night I installed "autofs" using Synaptic.
Synaptic included some other items I did not note.

This morning, I hot-plugged the camera & it immediately brought up the dialogue "Import Photos or Ignore" & when I clicked "Import Photos" it opened Shotwell with the camera ready for download.

I thought I had won - & marked the thread [SOLVED].

This afternoon, after a reboot, I hot-plugged the camera again - nothing!!

I read a bit about autofs & decided it was pretty complicated & maybe superfluous with the existing facility for handling Removable Drives & Media (is it - I really can't see what I should be using?).
So I used Synaptic to uninstall autofs, to start again from a clean sheet.
I noticed it didn't uninstall any other items.

Out of curiosity, I hot-plugged the camera again - and got the dialogue, Shotwell & download!

I thought I had won, again, but without understanding how.

I checked it again & it worked again.

Then I rebooted - and it doesn't work!

This is way beyond me.

What do I need, to get a camera to auto-mount with xfce?

What diagnostics can I run to see what is happening & what is not working?

Thanks!

---

### Post by Buntu Bunny on 2013-05-18
I agree this is puzzling. According to the Shotwell help files, Shotwell should automatically detect the camera and open. I use Xfce and it always does so for me. Have you checked preferences from shotwell's edit menu?

---

### Post by mansonfan78 on 2013-05-19
Have you checked your camera's settings?  Most have a setting as to how they're recognized by a computer: digital camera or mass storage device.  Other than that it couldn't really hurt to use synaptic to completely remove shotwell (incl. conf. files) and then reinstall it.  Or maybe try another program.  With me F-spot never properly worked but Shotwell did, maybe it's the other way around for you.

---

### Post by 2CV67 on 2013-05-22
Isn't it Thunar VolMan which is supposed to be reacting to the camera by mounting it & calling Shotwell?

I have played a lot with this problem & get 2 kinds of result:
1. Camera shown as mounted in Thunar > Dialog to Download or Ignore > Shotwell OK.
2. Camera in Thunar but not mounted > Nothing else. (unless I mount it in Thunar & /usr/bin/shotwell in terminal).

Yesterday I visited my 12.04Xfce "spare wheel" installation.
I ticked the same options in VolMan as above & it worked perfectly 5 times in a row.
I thought that proved it worked OK.

Then I switched back to my main 12.10Xfce installation & that worked 5 times out of 6...

Wierd...

---

### Post by 2CV67 on 2013-05-31
Done a lot more playing here & all I know is - it's not repeatable!

Using my main Xfce-Ubuntu-12.10 set-up, sometimes the camera is mounted & sometimes not, but I can't find what's different.

Other tests, using the same PC & the same camera, have included:
- 12.10 with Lubuntu desktop - works every time (choice of Shotwell or FileManager).
- 12.04 with Xfce desktop - works every time.

Back in 12.10 Xfce, I accidentally selected the "Pictbridge" option on the camera instead of the correct "PC" option.
That immediately opened Shotwell (no option & camera does not appear at all in Thunar) & I could download pictures OK.
That surprised me as I understood Pictbridge was for talking to printers, not PCs.
But it also works every time & in fact I am now using that as my default procedure!

I would still like to find out what is failing with the correct procedure though.
In that case, the camera appears in Thunar but is not mounted.
It has to be a VolMan problem doesn't it?
Are there no diagnostics anywhere?

Thanks!

---

### Post by scruffyeagle on 2013-06-04
I'm far from being an expert, but I had a thought about this.  Is it possible the failures are happening when some other particular program is running? Like, conflicts, or resources being tied up?

---

### Post by 2CV67 on 2013-10-28
Still erratic behaviour.

Basically hot-plugged camera always appears in Thunar but is usually not mounted & does not launch any further action, like opening Shotwell.
But sometimes it does appear as mounted & opens shotwell...

Is this Bug #1210898?
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1210898](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1210898)

---

