---
title: "Ok .. BIG problem with my laptop .. i need format and must do it in dos"
date: 2008-12-15
forum: General Help
---

### Post by BlackS3th on 2008-12-15
made a big mistake ...

My friend asked me to lend my pc and he said that he would fix a problem that i had in the graphic card (that didnt played 3D .. only 2D games ) And instead he deleted a package (xorg i think .. i dont remember) that package was the graphic reader package .... so now all i see in my laptop is dos .... 


I must format now ... i have the disc but i dunno how in DOS...


heeeeeeeeeeelp

---

### Post by taurus on 2008-12-15
You mean you need to reinstall Ubuntu?

---

### Post by BlackS3th on 2008-12-15
Here is the deal ... My pc now is like the terminal .... it gets only commands ... i only have the ubuntu cd ... what can i do?

---

### Post by philinux on 2008-12-15
Boot it up and press the esc key when grub appears. Use the down arrow key to highlight the entry with Recovery Mode. Then press enter. You'll get to a little menu. choose xfix then when the menu comes back choose resume normal boot. Post back.

---

### Post by used2bnewb on 2008-12-15
Well if you just need to get rid of everything then

```

cd /
sudo rm -rf *

```
Should do the job quite well

---

### Post by BlackS3th on 2008-12-15
It says when i xfix ... xserver-xorg is not installed... i hit the resume and ... Still all i see is terminal commands and dos stuf...   omg im doomed:-(

---

### Post by BlackS3th on 2008-12-15
Note that im talking through another pc ...

---

### Post by taurus on 2008-12-15
If your friend removed xorg from your machine, just reinstall it.

```
sudo apt-get update
sudo apt-get install xserver-xorg
startx
```

---

### Post by Ayuthia on 2008-12-15
You might try taking a look at /var/log/dpkg.log to see what was removed:
```
sudo cat /var/log|less
```You can scroll by using the arrow keys, page up, page down, home, and end.  Press q to exit.

Once you see the packages removed, you can go back and install it.

---

### Post by BlackS3th on 2008-12-15
..................................................................................................................................



Ok now i thing im ****** .... i did the   


sudo rm -rf * command and now .... my pc opens and says 




GRUB LOADING stage1.5.



GRUB loading, please wait...
Error 15 




Thanks a lot for the guy that gave this command ... THANKS MAN.

---

### Post by anaconda on 2008-12-15
You aren't in DOS.. you are in linux terminal, and you can reinstall aything you need with 
sudo apt-get install xxxxxx
or 
sudo apt-get install --reinstall xxxxxx 

I am not sure what you need to reinstall.. the following packets should be enough:
gdm xorg xserver-xorg xserver-xorg-core

so this command:
sudo apt-get install --reinstall xorg xserver-xorg xserver-xorg-core
should do the trick (I just thought that you propably dont need to reinstall gdm, that is why I didn't include it here.. but installing it wont harm you..)

---

### Post by geirha on 2008-12-15
I'd say boot up in recovery mode, choose to get a root shell, then install ubuntu-desktop
```
aptitude install ubuntu-desktop
```

Should get you back to normal.

EDIT: Ouch, if you ran that rm-command you've deleted all files and folders. Your only option now is to reinstall.

EDIT2: Though if you had files you want to get back, you might be able to get some of them back by using software such as foremost and photorec. See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by anaconda on 2008-12-15
> **BlackS3th said:**
> .

Thanks a lot for the guy that gave this command ... THANKS MAN.

Well.. actually he gave you (almost) what you asked for in the orginal post..

You said you wanted to format your hd.. and the rm - command didn't actually format it, but deleted everything.

yeah..
then all you can do is to reinstall ubuntu from the CD..

Or if you had some REALLY REALLY important stuff on your hd then (I think) it is possible to rescue the needed files with some free rescue program.

---

### Post by BlackS3th on 2008-12-15
Ok.. so .. i insert the cd but it says Error 15 .... what do i do?

---

### Post by anaconda on 2008-12-15
> **BlackS3th said:**
> Ok.. so .. i insert the cd but it says Error 15 .... what do i do?

Sounds like you are still booting from the hard-disk and not the CD. 

The booting order can be changed from your machined BIOS settings. Just make sure the it boots from the CD first (if there is a CD inserted) and then from the hd.

And boot again with the Ubuntu CD and then just proceed with the re-install

---

### Post by geirha on 2008-12-15
It doesn't boot the CD? You might need to enter the BIOS and tell it to try to boot CDs before trying to boot hard drives. To enter the BIOS you typically hit a key like F2, F10 or Delete. It's different from computer to computer, so you'll need to consult the manual to find the correct way to enter the BIOS

---

### Post by BlackS3th on 2008-12-15
ok .. lets see..

---

### Post by BlackS3th on 2008-12-15
ok .. now in boot priority is 

IDE HDD: HITACHI HTS542525K9SA00-(S
IDE CD: HL-DT-ST DVDRAM GSA-T40N-(
PCI BEV:MBA v9.4.5 Slot 0800
USB HDD
USB CDROM
USB FDC
USB key


Now ...priority?

---

### Post by geirha on 2008-12-15
Switch around IDE HDD and IDE CD, so it will try to boot the CD before the HDD.

---

### Post by matey3 on 2008-12-15
The way I understood it is that the xwindows (GUI) does not start automatically?!
Have you tried to type in xdm or gdm or kdm in that command prompt (dos like)screen ?

I would not re-install not unless some thing terrible had happened.
seems like the startup file was edited or was removed?
if so, you can put them back by typing this stuff here;(I think);


sudo update-rc.d -f (kdm or xdm or whatever) defaults

I use gdm myself because it is the only one which lets me log in as root.(too dangerous but I dont care, its a work computer)... ;) lol

OR may be the configuration file is corrupted or the res is set too high?
you can edit that file in the command prompt (DOS) too.
it is called xorg.conf and it is under /etc/X11/
make a backup copy and put it some where 1st.


any way , sorry for this reply cuz I am new to this myself but I have seen few problems like that already.

---

### Post by BlackS3th on 2008-12-15
OK....i got this working .... now all be aweare that i thank you ... And your solution .... wont be forgoten c ya!!!:guitar:

---

### Post by trentscott4 on 2008-12-15
Quoted from the GNU/GRUB manual

15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

[http://users.bigpond.net.au/hermanzo...skPage.html#15](http://users.bigpond.net.au/hermanzo...skPage.html#15)

Re-install Grub: [http://users.bigpond.net.au/hermanzo...bDiskPage.html](http://users.bigpond.net.au/hermanzo...bDiskPage.html)

Or use this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by philinux on 2008-12-15
> **trentscott4 said:**
> Quoted from the GNU/GRUB manual

15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

[http://users.bigpond.net.au/hermanzo...skPage.html#15](http://users.bigpond.net.au/hermanzo...skPage.html#15)

Re-install Grub: [http://users.bigpond.net.au/hermanzo...bDiskPage.html](http://users.bigpond.net.au/hermanzo...bDiskPage.html)

Or use this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

He deleted everything with rm. He has no system to boot.

---

### Post by used2bnewb on 2008-12-15
You asked to format your hard drive and you that's pretty much the same as deleting it all and you would probably have reinstalled anyway. So don't blame me.

You got what you asked for and I'm not saying that in a bad way, what I mean is that you asked how to get rid of all your data (roughly speaking) and I gave you the code to do it and now it's all gone

Just what you asked for, isn't it?

And I specified what the command does, didn't I.

---

### Post by overdrank on 2008-12-15
> **BlackS3th said:**
> ..................................................................................................................................
Ok now i thing im ****** .... i did the   
sudo rm -rf * command and now .... my pc opens and says 

GRUB LOADING stage1.5.
GRUB loading, please wait...
Error 15 
Thanks a lot for the guy that gave this command ... THANKS MAN.
To BlackS3th and used2bnewb, You may look at the FAQ's
[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)
> **used2bnewb said:**
> You asked to format your hard drive and you that's pretty much the same as deleting it all and you would probably have reinstalled anyway. So don't blame me.

And I specified what the command does, didn't I.
You can offer other ideas for users new to Ubuntu, like use the live cd to rescue the data and then install again if need be.

---

### Post by jimmy41 on 2008-12-15
> **used2bnewb said:**
> Well if you just need to get rid of everything then

```

<snip>

```
Should do the job quite well


Actually this wouldn't delete everything.  I figure it will end up deleting something important (or the rm command itself) and just bomb the system...leaving quite a bit of data...useless data but still data.

---

### Post by matey3 on 2008-12-15
> **overdrank said:**
>  You may look at the FAQ's
[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

You can offer other ideas for users new to Ubuntu, like use the live cd to rescue the data and then install again if need be.
Good comment. that is exactly what I thought 1st too,  I remember reading that not too long ago. but just forgot where exactly I read it at?!
thanks for the link/info.

I suggest ppl do practice editing files in the command line (terminal) environment so in a situation like that they wont have to take drastic measures like deleting/formatting everything.

I am still regretting loss of some of my files from when I had to re-format months ago!


PS sorry I made a mistake in my first reply, I said I used xdm , I meant gdm....
I fixed it though...

---

### Post by used2bnewb on 2008-12-15
> **overdrank said:**
> To BlackS3th and used2bnewb, You may look at the FAQ's
[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

You can offer other ideas for users new to Ubuntu, like use the live cd to rescue the data and then install again if need be.

I explained what it does and that's what he asked for ok:mad:

---

### Post by overdrank on 2008-12-15
> **used2bnewb said:**
> I explained what it does and that's what he asked for ok:mad:

I explained my opinion and offered you a link to the forums policy on those commands :popcorn:

---

