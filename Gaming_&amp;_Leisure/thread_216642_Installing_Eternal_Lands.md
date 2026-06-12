---
title: "Installing Eternal Lands"
date: 2006-07-15
forum: Gaming &amp; Leisure
---

### Post by tx1138 on 2006-07-15
Hi all. I am very new to Ubuntu, and linux altogether, and I was wondering if I could possibly trouble someone to simply show me how to install a game called 'eternal lands'. I would really appreciate it :)

Thanks in advance, tx. :)

---

### Post by Perfect Storm on 2006-07-16
unpack it, then
```
cd /into/the/unpacked/folder
chmod 775 sh el.x86.linux.bin
sudo sh el.x86.linux.bin
```

As it says on their page
> To play on Linux:
Download the zip file, and unzip it.
cd to the directory where you installed it.
chmod to 775 and execute el.x86.linux.bin
edit el.ini and change datadir to where you unzip everything
Also, the zip file has no base directory, so you should unzip it in a new directory you create.

---

### Post by tx1138 on 2006-07-18
yer but I have no idea what cd to the directory means, or chmod or edit el.ini. But nvm, I'm all over it heh.

---

### Post by Arnez on 2006-07-19
I'm kinda new as well (but learning fast)- when I follow those instructions I get:

:~/games/eternal$ chmod 775 sh el-130.x86.linux.bin
chmod: cannot access `sh': No such file or directory
:~/games/eternal$ sudo sh el-130.x86.linux.bin
Password:
el-130.x86.linux.bin: el-130.x86.linux.bin: cannot execute binary file

any help would be appreciated.

Update- ok I figured out the chmod part, but still can't execute the file

---

### Post by Perfect Storm on 2006-07-19
```
chmod 775 el-130.x86.linux.bin
```

then try with
```
sudo sh el-130.x86.linux.bin
```

or

```
sudo ./el-130.x86.linux.bin
```

---

### Post by Arnez on 2006-07-19
Thanks! Looks like I'm missing a shared binary ( libSDL_net-1.2.so.0 )

I think I can figure it out.

---

### Post by Clockwise on 2006-07-22
So what do you search on the Ubuntu packages? ](*,) ](*,)

---

### Post by Perfect Storm on 2006-07-22
you can make a search in synaptic on **libsdl**

---

### Post by Clockwise on 2006-07-22
What do you search up for Enternal Lands on the Ubuntu Synaptic Package Manager? Or do you download it from [http://www.eternal-lands.com/page/download.php?](http://www.eternal-lands.com/page/download.php?)
Does the To Play Linux works for Ubuntu?

---

### Post by Perfect Storm on 2006-07-22
You need to download it from the link you showed.

---

### Post by Clockwise on 2006-07-22
I was deleting ](*,)

---

### Post by Clockwise on 2006-07-22
Does Eternal Lands work for Ubuntu?

---

### Post by Perfect Storm on 2006-07-23
Yes, it does. Just follow the instructions.

---

### Post by Cyraxzz on 2006-07-23
experienced players of Eternal Lands: how would you rate it?, 0 to 10?

---

### Post by Clockwise on 2006-07-23
How do you follow the instructions? I mean what do you use with it?

---

### Post by Perfect Storm on 2006-07-23
You open the terminal (Applications tab ---> Accessories ---> terminal).

Then move to the place you saved the file eg. to your desktop:
```
cd Desktop
```

then follow the guide which are describe in the link I provided earlier. If you run into trouble, just post back.

---

### Post by Clockwise on 2006-07-24
So I put it to the desktop and then I do the instructions on the website that I downloaded Eternal Lands?[-(

---

### Post by Gorlist on 2006-07-24
Hi, just tried installing the game but it comes up with:

./el-130.x86.linux.bin: error while loading shared libraries: libcal3d.so.11: cannot open shared object file: No such file or directory

when I run:

sudo ./el-130.x86.linux.bin



Ideas?

---

### Post by Perfect Storm on 2006-07-24
```
sudo apt-get install libcal3d11c2a
```

Make sure that universe is enable in your sourcelist.

---

### Post by Perfect Storm on 2006-07-24
> **Clockwise said:**
> So I put it to the desktop and then I do the instructions on the website that I downloaded Eternal Lands?[-(

Yes. Download to Desktop. Then:
```
cd Desktop
chmod 775 sh el.x86.linux.bin
sudo sh el.x86.linux.bin
```

You might run into some libs that aren't installed, but we'll take one at the time.

---

### Post by Clockwise on 2006-07-24
I can't execute the program.

---

### Post by Perfect Storm on 2006-07-24
Please post the the exact things you write and the output of the terminal, it makes it easier to see what's up.

---

### Post by Gorlist on 2006-07-25
Hi, when I go to select a character ingame it comes up with:

[INDENT]el-130.x86.linux.bin: model.cpp:50: CalModel::CalModel(CalCoreModel*): Assertion  `pCoreModel' failed.
Aborted[/INDENT]

Anyideas?

---

### Post by UltraSonicSite on 2006-08-08
I myself am getting this problem as well. All directions were followed to the best ofmy ability and understanding but am recieving the same error the above user is getting.

---

### Post by vloveya08 on 2006-08-09
Ok, I'm trying to install this program...

I get all the way to entering

sudo ./el-130.x86.linux.bin

And an error comes up:

error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory

I have the extra repositories open and looked through the Synaptic and found two packages that looked like might be what it was looking for:

libsdl-net1.2
libsdl-net1.2-dev

Checked the first one for installation.  Read the description for the second one and realized that yes, I do need it.  Second one comes up with screen saying "Mark additional required changes?" click Mark.  Comes up with unresolvable dependencies: needs libsdl1.2-dev which is not anywhere in my list for synaptic.  I have had a few little problems with the extra repositories before in that 2 files couldn't be accessed for some reason.  Didn't think too much of it but I'm wondering if maybe that could be in those two repositories I can't access?

Also, I tried going through Terminal to get the dependent file that I can't see in Synaptic and it comes up with other dependencies that aren't in Synaptic...HELP!

---

### Post by precinto on 2006-09-05
I managed to install the program without problem. But now, even if I have modified el.ini (to use full screen and to tell the program where de data dir is), it just shows a small non-resizable window and I can't get to create a new character. As soon as I click on Human or Elf or whatever the windows closes.
Just after loading it says it cannot find the books and some other thing in /usr/local/games/el/...

Why doesn't it respond to my el.ini file? Do I have to reinstall it in usr/local/games for it to work?

Update: Ok, I reinstalled it where it said and it works... now i just have to learn how to play... :)

---

### Post by lamego on 2006-09-14
I have created a .deb package for Dapper to make the installation easier, it will install a launcher on the games menu.
[http://www.getdeb.net/getdeb.php?file=eternallands_1.3.2-1_i386.deb](http://www.getdeb.net/getdeb.php?file=eternallands_1.3.2-1_i386.deb)

---

### Post by Xceptiona1 on 2006-09-21
Lamego, thanks for creating the package, that makes it simple as heck!

---

### Post by Xter on 2006-09-23
Lamego! the Deb package doesnt seem to work, or am I stupid? When I click the launcher on the games menu nothing happens except a error message 

[12:23:28] Error: Can't open file "/home/zekeroberga123/.elc//el.ini
[12:23:28] Failure reading el.ini

Please help me!

---

### Post by BlacKat_K on 2006-09-26
Lamego thank you so much for the deb.I couldnt have done it myself :D One question though,do i have to apply the update package from the EL site too?And how do i do that?
EDIT: The games server just change and i cant upload el.ini file because "i'm not owner" ](*,)  WTF??

---

### Post by Roberto Rosselli on 2006-09-27
Lamego, thx for the deb package. After I installed it I met two problems though:

1. the game didn't start, I created a little script to cd in the game directory and run the binary;

2. the game crashes quite often: not only that, it completely freezes my Ubuntu box. Any idea why it happens? might it be related to 1.? Are there patches to apply to the game?

Thanks in advance,

Roberto

---

### Post by Roberto Rosselli on 2006-09-28
OK, completely different problem on my laptop (Acer 1360): game starts, I login typing user/password and immediately after that (before I can see the game screen) the game exits with this message:

X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  14287
  Current serial number in output stream:  14288

Really a pity, I'd like to play under Ubuntu Linux, not Windows! :(

Ciao

---

### Post by Rogue5 on 2010-03-20
I have this game installed, and it runs fine, and I can see some characters in the game, and all of the terrain looks fine so far, but my character and a few others look funky.  They flash all black then the 3do's begin to change color and sometimes I can see a piece of the character that actually is, but most of the time it just looks funky and black.  The shape of the character is right however, just the color scheme. 


Any idea's?

---

