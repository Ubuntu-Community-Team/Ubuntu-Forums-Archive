---
title: "Help Installing MatLab"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Canuck on 2005-10-17
Hello,

I am having a different problem installing Matlab. I have been following the Wiki guide on how to install it ([https://wiki.ubuntu.com/MATLAB]("https://wiki.ubuntu.com/MATLAB")) and I get the following error when trying to make an image in the temp file.


command used: [COLOR="Blue"]sudo cp -R /media/cdrom1 /tmp/matlab[/COLOR]

Error Received: [COLOR="Red"]cp: reading `/media/cdrom1/win32/help/base/install/pc/mhelp.dat': Input/output error[/COLOR]


Anyone have any suggestions on how to remedy the situation. By the way I am trying to install the student version R14 SP1 and am running Breezy.

Canuck

P.S.  I am very new to Linux so if you have any suggestions on different approaches please keep the instuctions simple.  :)

---

### Post by jdtanner on 2005-10-17
Sounds like you might have a grubby cd-rom disk. Take it out of the drive and give it a bit of a clean and try again. If that doesn't work then ask Mathworks for a new set of installation media.

Cheers,
JohnT

---

### Post by Canuck on 2005-10-17
JohnT,

The CD seems to be ok, it works fine when installing it to windows.  I do know that I am having problems when using totem on this particular file (I tried running the file off the CD)...  Would that cause the error when trying to create the image?

Canuck

---

### Post by jdtanner on 2005-10-18
Hmm, not sure what you mean about Totem. Totem is for playing back video or audio, not for installing Matlab. 

If you have a dual boot with Windows, perhaps you could copy the contents of the cd-rom to a file on that partition (say c:\matlab), then mount that partition from Ubuntu (mount /dev/whatever /mnt/cdrive for example) and copy the files to /tmp/matlab (cp -R /mnt/cdrive/matlab /tmp/matlab)?

Sorry I can't be of more help :-(

JohnT

---

### Post by Canuck on 2005-10-18
JohnT,

No worries!  I shall continue my search for the answer...  42...  Now what was that question again...??? :)  Meanwhile I'll give your idea a try although as I said I am pretty new to this Linux stuff so that approach may lead into a whole new set of questions!

Canuck

---

### Post by neoflight on 2005-11-03
hi,

r u sure the cd rom is cdrom1 not cdrom0?
just wondering. 

i was trying to install student version matlab (yes that stupid one!) and was successful in installing that. it gave the most boring gui ever during the process  (yes i followed the ubuntu wiki and i cud copy the cd to tmp. i think i got some message. error? anyway i ignored it and ran the install command.)

BUT when i tried to run it , it said no such command. i dont know why!
one thing i remember is that there was a message saying "follow the installation procedure from mathworks..." or something like that. and the poor display might be due to my comp having no video card stuff properly installed. i am working on that. 
1. please help me with all these. (nu-b)

2. is there anyway i can make a virtual cd drive for the student matlab version? i tried in XP and was not possible. 

thanks a lot. 
**Ubuntu is great!**

T42, ipw2200, ATI 9600, 512, 40, XP-Ubuntu 5.10.BB [_gnome_-kde]

---

