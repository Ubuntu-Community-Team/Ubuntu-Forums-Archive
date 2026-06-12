---
title: "how to access my mp3 player from the CLI"
date: 2009-05-12
forum: General Help
---

### Post by madjo on 2009-05-12
Hi all,

I have a Cowon D2, and in previous versions of Ubuntu, whenever I connected that mp3-player to my computer, it would mount the device as /media/D2 and /media/disk (if there was a SD-card in it).

Now, in 9.04, however, it doesn't get mounted in /media at all.

I can access the device from a filemanager, but I have no idea where I can find it in the command line.
This is the line I see in the address-bar: gphoto2://[usb:005,004]/store_00010001

But I would really love to be able to access my mp3-player from the CLI, as I am used to SSH into my desktop/fileserver and manage my mp3-player through there.

Is there a way to do that? 

Would removing the libgphoto package help?
*update* I tried the above, but the packages listed that would get removed with it, makes me think that it's too important for the health of the system to be removed. So that can't be it.

Also, my mp3-player is set to MTP, because the Audible functionality demands it. So that's not a solution, besides that, I would like to make a backup of my mp3-player first before I would change such a setting, and when I tried that yesterday, the copying failed for a large number of files, so I haven't been able to make a decent backup of it.

---

### Post by madjo on 2009-05-13
Status update, I have changed the setting on my mp3-player from MTP to MSC, and now 9.04 recognizes the player as a /dev/sdX device. 
But it would be nice to have had someone chime in here to tell why the behaviour changed between 8.10 and 9.04.

---

### Post by __Nathan_ on 2009-06-08
i have had exact same problem as you with my Sony Walkman. its frustrating because it keeps coming up as gphoto2://[usb:005,004]

i am not sure i understand how you were able to fix it. please help if you can?

---

