---
title: "ut2004 install, help please"
date: 2006-09-30
forum: Gaming &amp; Leisure
---

### Post by confuzzedintelguy on 2006-09-30
Hello i had just bought ut2004 dvd and i would like to install it how ever i dont seem to have the linux-installer.sh on my disc i was wondering if there is a nether way to install it.

---

### Post by Perfect Storm on 2006-10-01
```
cd /into/the/CD/with/ut2004
ls -a

```
please post the output.

---

### Post by confuzzedintelguy on 2006-10-01
here you go

> matt@matt-desktop:/media/DVD-RW$ cd /media/cdrom0
matt@matt-desktop:/media/cdrom0$ ls -a
.   AutoRunData  Autorun.inf  Disk2  Disk4  Manual.pdf
..  AutoRun.exe  Disk1        Disk3  Disk5
matt@matt-desktop:/media/cdrom0$


BTW this is the ut2004 editors choice mega pack dvd

---

### Post by Perfect Storm on 2006-10-01
Try have a look on the subfolders disks

---

### Post by confuzzedintelguy on 2006-10-01
I have checked all folders and there is no .sh file at all :( if i can find someone who has it on there disk can i have them send me the file and use it from my home folder or does it HAVE to be on the disk.

---

### Post by Perfect Storm on 2006-10-01
I really don't know, sorry :-/

---

### Post by confuzzedintelguy on 2006-10-01
By any chance do you have ut and the installer if so is there any way you could email it to me i would like to try as if it doesnt work i will just have to go track down a nether copy tomorrow.  Also thank you for the help i was starting to wonder if any one was gana help ](*,)

---

### Post by Perfect Storm on 2006-10-01
I'll look into it, but I have a very new DVD verion of it, so It might not work.

---

### Post by confuzzedintelguy on 2006-10-01
Thank you ugh i cant believe this lol i have been googleing for hours looking for somthing or someone who has had the same problem and it would seem i am the only lucky person to have this problem.

---

### Post by Perfect Storm on 2006-10-01
Well, I'm uploading the linux installer at this moment, so we just have to see if it works.

---

### Post by devils_casper on 2006-10-01
what are the contents of Disk1, 3 and 5 ? are there any .iso files ?
AutoRun.exe means, its a Windows based DVD. you must have .iso files in DVD.




casper

---

### Post by aidanr on 2006-10-01
it's not in the Disk1 folder is it? that would be the cd it would be on if you had the cd version, also the installer is 28mb so good luck getting someone to email it to you

btw is Disk1 a folder or a file?

---

### Post by confuzzedintelguy on 2006-10-01
nope no iso files on the dvd at all a lot of .cab files though aidanr it is not in the disk one folder

---

### Post by Perfect Storm on 2006-10-01
Done, I have uploaded the linux installer to a server: [http://www.filelodge.com/files/room38/1059449/Ubuntu/linux-installer.sh](http://www.filelodge.com/files/room38/1059449/Ubuntu/linux-installer.sh)

Just copy it to your Desktop and run it from there.

---

### Post by confuzzedintelguy on 2006-10-01
also sorry for the files you wanted to know about 

[quote=Disk1 Folder]Setup.bpm, data1.cab, data1.hdr, data2.cab, engine32.cab, layout.bin, setup.exe, setup.ibt, setup.ini, setup.inx and setup.ins[/quote]

[quote=Disk3 Folder]data4.cab[/quote]

[quote=Disk5 Folder]data6.cab[/quote]

---

### Post by confuzzedintelguy on 2006-10-01
Thank you very much downloading now to give it a try i will be back in a couple mins to let you all know if it worked or not.

---

### Post by confuzzedintelguy on 2006-10-01
ok it asks "Please mount the Unreal Tournament 2004 Play Disc CDROM."  "Choose Yes to retry, No to cancel"

now the dvd is mounted and is mounted to /media/cdrom however fstab has my dvd drive mounted /dev/hdc /media/DVD-RW {by the way yes i umounted it before i remounted it to cdrom) should i try changeing /dev/hdc to cdrom i know in gentoo that is how the cdrom is supose to be mounted but this is far from gentoo lol

---

### Post by aidanr on 2006-10-01
i doubt it, the installer is probably searching all the drives looking for certain files, and the dvd layout you described is different from what it's looking for

the cd version has no cab files, the contents of the cd's are the same as what ends up on your harddrive, ie the system, textures folders etc

i'd say your outta luck with that dvd, you could bring it back where you bought it, or borrow the cd's/proper dvd off someone or get a torrent of it and use the cd key from the dvd

---

### Post by confuzzedintelguy on 2006-10-01
i figured just as much but i am gana try to install one more time right now i am in xubuntu i am not sure if it matters or not but i will try a clean install of ubuntu and see what happens it was time for a format anyhow chances are i will just have to go a buy a nether dvd tomorrow.

Thanks every one for the help.

---

### Post by confuzzedintelguy on 2006-10-01
ok so i went and bought a nether dvd version to have the same problem no linux installer and when i try the one i got from artificial it does the same thing asks me to mount the play disc.  Now i sit with two brand new copys of ut and no way to install them i tried wine it installed but wont play it starts but the textures are all screwed up and what not.  Can some one please tell me what would cause this my pc specs are Pentium 4 2.0a | MSI Neo 2 Platinum 865pe | nvidia 6200 | liteon light scrib DVD-RW and NEC DVD drive | 80gb hdd

---

### Post by confuzzedintelguy on 2006-10-01
anyone? i would really like to get this thing to work i just dont understand why the file wouldnt show up i mean i am sure there is a way to get it installed i tried the export thing i have seen many times on here to help with the please insert disck problem but it didnt work.

---

### Post by S1NGH on 2006-10-02
AI - could you please re-upload the linux-installer.sh file. My friend gave me a copy of UT2004 and i can't copy the linux-installer.sh from the dvd, i get a data error (cyclic redundancy... something..) while coping it to the desktop

---

### Post by Perfect Storm on 2006-10-02
[http://www.filelodge.com/files/room38/1059449/linux-installer.sh](http://www.filelodge.com/files/room38/1059449/linux-installer.sh)

---

### Post by Perfect Storm on 2006-10-02
> **confuzzedintelguy said:**
> ok so i went and bought a nether dvd version to have the same problem no linux installer and when i try the one i got from artificial it does the same thing asks me to mount the play disc.  Now i sit with two brand new copys of ut and no way to install them i tried wine it installed but wont play it starts but the textures are all screwed up and what not.  Can some one please tell me what would cause this my pc specs are Pentium 4 2.0a | MSI Neo 2 Platinum 865pe | nvidia 6200 | liteon light scrib DVD-RW and NEC DVD drive | 80gb hdd

The reason why that your ut2004 copis doesn't have any linux installer baffles me, but again I buy almost all my games a tuxgames.com (which are guarentee have linux installer with them). If I was you I'll go back and get my money back.

---

### Post by Rhubarb on 2006-10-02
Maybe this problem is just specific to the Editor's Choice Edition DVD?
I dunno.
Firstly, if possible, get your money back.  You might be able to try a non ECE UT2004 DVD if your local store has one in stock.
The ECE pack can be downloaded free from [www.unrealtournament.com](www.unrealtournament.com) anyway.
I'm quite disappointed about the UT2004 **ECE** in general, as it has poor Linux support (still managed to get the ECE pack working in Ubuntu though).

---

### Post by aidanr on 2006-10-02
have a look at the packaging aswell, if it has a tux icon on it then you're good to go

bring those dvd's back and get a refund

the only thing i can think of is that maybe for the ECE dvd they had to pack more stuff onto the dvd and therefore needed to compress it, and chose a not so linux friendly installer, hence all the .cab files

thats just a guess though

---

### Post by confuzzedintelguy on 2006-10-02
i dont think it is an ECE issue these are both the brand new ECE MP dvd's which i finally found someone who has the same problem on the epic forums how ever there is no information that could help me on installing it right now i am trying to track down a nether one but this time i am looking for the cd set.  Also dont get me wrong i would order from tuxgames if they didnt gouge the hell out of prices i am not willing to pay 40 bucks + shipping for a game that costs 9.99 :/

---

### Post by aidanr on 2006-10-02
you want [this]("http://www.amazon.com/Atari-Unreal-Tournament-2004-CD-ROM/dp/B0000BVGOM/sr=8-3/qid=1159820958/ref=pd_bbs_3/002-2113947-2145602?ie=UTF8&s=videogames") one, although it says it can only ship us, i also found it on amazon.co.uk

---

### Post by confuzzedintelguy on 2006-10-03
Yeah thanks i emailed Epic so i will wait a couple more days to hear from them and go from there i will more then likely end up buying it used considering i only need the disks as i have 2 brand new keys right here.

wow that really needed to be edited **[SIZE="4"][COLOR="Red"]WARNING:do not post when tired and barely able to see[/COLOR][/SIZE]**

---

### Post by Perfect Storm on 2006-10-03
Best of luck, confuzzedintelguy :) 

Please report back when you have new stuff about your issue.

---

### Post by justin whitaker on 2006-10-03
> **confuzzedintelguy said:**
> anyone? i would really like to get this thing to work i just dont understand why the file wouldnt show up i mean i am sure there is a way to get it installed i tried the export thing i have seen many times on here to help with the please insert disck problem but it didnt work.

Try this hack:

Copy the installer, and the disk contents, onto your HD in a folder somewhere, and install from there. When the installer asks for the play CD, remount the DVD drive. 

That hack helped me install CS:S. Might work for you.

---

### Post by CornMaster on 2007-01-30
I will be getting a copy similar to this, with no Linux installer.  I should be able to get the installer from a friend, and I suspect that taking the .cab files, and making them into .iso would be a possible solution.  I'll give it a shot, and I'll let you know how it goes.  Might also be possible to just extract the files from the .cabs in windows and use them in Linux...not sure about that though.  And not really an option for those who don't have windows.

---

