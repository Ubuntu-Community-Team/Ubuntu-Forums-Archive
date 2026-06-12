---
title: "Invalid GUID when trying to play Enemy territory"
date: 2008-03-16
forum: Gaming &amp; Leisure
---

### Post by cristovaum on 2008-03-16
I keep getting an "You have an invalid GUID" wornig, stoping me from geting conected to Enemy Territory server.

Any help?
Many thanks.

---

### Post by oracel on 2008-03-22
Happens to me too, just installed it today.

---

### Post by cristovaum on 2008-03-22
Try this:

Go to .etwolf folder, then etmain and here see if you find etkey (notice that some files are hiding so use Alt+H to reveal hiding files). Erase this etkey and update pkbuster.

Hope it will solve the problem.:)

---

### Post by Vignesh9 on 2008-11-26
Hasn't helped. I've reveled the hidden files and still can't find et key.

Also, once i start Enemy Territory, i give in the settings that i want, later when i close the game and enter it again the settings are go and i have to give my name and all the settings again. 

Could you please help me.

I really want to get this game running.

---

### Post by niaz12 on 2008-11-26
You have an invalid GUID" wornig, stoping me from geting conected

---

### Post by cristovaum on 2008-11-26
> **cristovaum said:**
> Try this:

Go to .etwolf folder, then etmain and here see if you find etkey (notice that some files are hiding so use ctrl+H to reveal hiding files). Erase this etkey and update pkbuster.

Hope it will solve the problem.:)

Sorry fellas but, the above was what i did and solve my Invalid GUID problem.:(

---

### Post by epitaph on 2008-11-26
Have you tried erasing it entirely and then issuing

```
\pb_cdkeyreg
```

to retrieve a new key?

---

### Post by Vignesh9 on 2008-11-27
I still don't get you?

what code is that, if so can you give the complete code?

---

### Post by epitaph on 2008-11-27
Delete the etkey file in your .etwolf file in your home directory (default location).

Then, launch the game and issue that command in console by pressing tilde (~) and then typing "\pb_cdkeyreg" and pressing enter.

---

### Post by warham on 2009-03-18
When I enter \pb_cdkeyreg it says GuidAuth Packet ignored : File Write Error

I also didn't delete etkey from my etmain folder because I just can't find any. Not when I press ctrl + H, not when I press alt+ H, and not even when I just go to mapoptions and mark show hidden files.

---

### Post by tigergibb on 2009-04-29
This solved my problem:

open terminal
cd ~
chown -R user:group .etwolf

In the last command, replace user and group with your username you use to login to ubuntu

---

### Post by hoscha on 2009-08-01
my etkey does not exist in the "etmain" folder, but yet my XP is still saved when i connect. i wanna re-install enemy territory because my console freezes.  either way where is my etkey and how can i genereate one/? 

i did issue a /pb_myguid  so i know what my guid is, but where is my XP being saved??  i also did a /pb_cdkeyreg and /cl_guid  with the  /pb_cdkeyreg it already said its registred

---

### Post by hoscha on 2009-08-02
nvm, i found it, it a different folder. /home/name/.etwolf/etmain

---

### Post by hoscha on 2009-08-02
after re-install my console still locks up, not every time, but once in awhile. and i cant find a wayto unfreeze it. unless i push Ctrl+Alt+Backspace

---

### Post by andy80 on 2010-06-01
> **epitaph said:**
> Delete the etkey file in your .etwolf file in your home directory (default location).

Then, launch the game and issue that command in console by pressing tilde (~) and then typing "\pb_cdkeyreg" and pressing enter.

Hi, I did this procedure and I get:


]\pb_cdkeyreg
^5PunkBuster Client: Cdkey Registration Request sent to GuidAuth Master at 192.246.40.62:27960 (1668161374)
^5PunkBuster Client: Cdkey/GUID Registration successful (/home/andrea/.etwolf/etmain/etkey)

so it should be ok, but I'm still kicked when I try to connect to any server, in particular to this one: 89.149.229.247:27960

could please anyone test it?

Thanks for your help!

---

### Post by ELD on 2010-06-01
Make sure you install the patch guys, the installer only installs the old version, you need to install the patch as well, this one caught me out.

Odd that they don't make a full installer for the latest version.

---

