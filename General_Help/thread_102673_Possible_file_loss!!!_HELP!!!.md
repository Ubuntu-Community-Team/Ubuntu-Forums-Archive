---
title: "Possible file loss!!! HELP!!!"
date: 2005-12-12
forum: General Help
---

### Post by aruckert on 2005-12-12
I just downloaded photos from my camera. I saved them in my home directory and I could see them prefectly.

I tried to move them to a vfat partition where I keep my personal data. I used Nautilus.
1- Ctrl-X on the folder where the photos were (home folder, / ext3 partition),
2- Ctrl-V on the folder where I wanted them (/media/hda5 vfat partition).

Nautilus created the folder but did not copy the files!!! The files seem to have banished!!!

Does anyone have an idea? Please!

---

### Post by carlosqueso on 2005-12-12
yikes! Can you Ctrl-V them back in your home?

---

### Post by aruckert on 2005-12-12
Nop :-(

The clipboard is empty!

---

### Post by carlosqueso on 2005-12-12
Dang, methinks they're gone...try checking for them from windows, if they don't appear, I don't know what to say to you.

---

### Post by doitashimashite on 2005-12-12
You could try a find like this:

find / -name "DSC*" | more

where "DSC" would be the first part of the image names.
They might pop up where you wouldn't expect them.

Well, good luck.

---

### Post by aruckert on 2005-12-12
I'll try that. Thanks for your help!

Do you think I should submit this as a bug?

---

### Post by aruckert on 2005-12-12
I found the files in a folder called Templates inside my home folder.... :D 

Does anyone have an idea of why (WHY?! WHY?!) did Nautilus do such a thing?

Thanks everyone for your help! :-)

---

### Post by mherring on 2005-12-12
I have argued that computers are not deterministic---because we can never know all the variables.
Was /media/xxx mounted at the time?  (Being in media makes me think it was an external usb)
I would always COPY between 2 Nautilus windows by dragging the icons.

---

### Post by blair on 2005-12-12
On critical files, it is always safer to copy, then verify the target is OK, then delete, as opposed to cut/paste. Remember that standard support for NTFS is fairly new in the Linux world. M$ hasn't been terribly forthcoming with interface specs, the file system has itself morphed over each of te last few Windows releases and also most Linux developers aren't terribly predisposed to making Linux interoperate with a crappy OS. 

One way of reducing your risk here is to put your Windows OS and apps on one NTFS partition, create a second FAT partition for your Windows data, then create additional partitions for your Linux distro. You will have much less risk reading/writing to the FAT partition than you will to the NTFS partition. As such, you can reliably make the FAT partition accessible both within Windows and Linux, meaning your data files are always accessible, regardless of what OS you boot into.

---

### Post by aruckert on 2005-12-21
[QUOTE=blair]On critical files, it is always safer to copy, then verify the target is OK, then delete, as opposed to cut/paste.[/QUOTE]

You are right. I should have done that!

[QUOTE=blair]Remember that standard support for NTFS is fairly new in the Linux world.... One way of reducing your risk here is to put your Windows OS and apps on one NTFS partition, create a second FAT partition for your Windows data, then create additional partitions for your Linux distro...[/QUOTE]

I agree! That`s exactly how my system is configured! :smile:

---

