---
title: "usb mp3 player issues"
date: 2006-08-20
forum: Desktop Environments
---

### Post by repins on 2006-08-20
Ok, I have a diamond 1gb usb mp3 player. It had music on it from windows before i made the switch to ubuntu. ubuntu finds it and mounts it fine. so i went into the usb drive and delted the songs that are in there, and loaded new ones. now heres the problem, i went to listen to the new songs that i put in there, and its starts playing the new ones but then it starts playing the old ones that were deleted. Should i format it? and if so how? because it will not let me from disk manangment even if i unmount it.. any help would be greatly appreciated.. TIA

---

### Post by meng on 2006-08-20
Try this - put the drive back into your computer and press ctrl-H to show hidden files and directories. There should be one called .Trash, all your deleted songs are in there. To remove completely, I suggest you configure GNOME/Nautilus this way: from file browser, go Edit > Preferences > Behavior and tick "Include a delete command that bypasses Trash". Then select the file/s you want to delete, and right click > delete. Gone forever.

---

### Post by repins on 2006-08-20
should i delete the folder as well, or just the files?

---

### Post by meng on 2006-08-20
Sure, actually that would be a tad quicker.

---

### Post by repins on 2006-08-20
Ok, great. That seem to do the trick. although it still doesnt delete from the .trash folder, no biggy. Just have to go into the .trash folder to delete them... Thank you very much.

---

### Post by repins on 2006-08-20
Spoke too soon....got to the 3rd track  and it gave me "format error" on the mp3 player. So i followed the same steps, and tried load a totally different album, and its giving me the same error "format error".

---

### Post by meng on 2006-08-20
Are there any other non-mp3 files on this player? Some sort of index file or something? I'm just guessing now, no real experience with the model you have.

---

### Post by repins on 2006-08-20
no, there's only .mp3's

---

### Post by meng on 2006-08-20
I hope the .Trash (or is it .Trash-[username]) is not throwing you off? Were you able to delete it or not? Otherwise you may have to drop to the command line
cd /media/[name of this USB drive]
sudo rm -r .Trash

---

### Post by repins on 2006-08-20
ya, I was able to delete the .Trash-user folder, and it creates a new one anytime you delete... I just reied a couple of things for the sake of trouble shooting. 
1. delete the song's, then go into the .Trash folder to delete the songs.
2. delete the songs, then delete the .Trash folder

Its just really seeming flakey and unpredictable, where one time it would work, then the next it would give me the "format error" again. would maybe the option to format the usb drive work?

---

### Post by meng on 2006-08-20
That's a shame - are you pressing the delete key to move these to trash? I thought you should be able to bypass the problem by right click > delete every time, which should delete without going to trash.
Maybe reformatting will work.

---

### Post by repins on 2006-08-20
Hmmm, well i was using the "del" key instead of right clicking. and this time it seemed to work. i will post back if this odd behavior continues. but that did the trick for now. thanks once again.

---

### Post by repins on 2006-08-23
Alright, yet no dice with this device. yesterday I had the same problem.. also now i cannot delete any of the songs. How would I format for VFAT?

---

### Post by idonthack on 2006-08-29
Some things like USB drives and devices have problems with formatting under linux, so you might need to use Windows. But you can try the command line utility "mkfs.vfat". You need to know the device name, and you must do it while unmounted. Try something like
```
sudo mkfs.vfat /dev/sda1
```

You could type ```
df
``` while it's mounted to see the device name.

Also, sorry for the late reply. I know this is almost a week old but I knew how to do this and it will be good for future reference even if you don't need it anymore.

---

### Post by repins on 2006-08-29
I appreciate your response, and it does seem to be an issue under linux. I did try to format under linux and the same symptoms kept on happening, formatted under windows and it has been working fine.  If there is anything that i can post to help fix it under linux please let me know, because i willing to help out any way i can.

---

