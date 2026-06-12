---
title: "How to install TTF fonts from Windows?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by ChrisTheGeek on 2005-10-18
Hello,

I'm trying to get some TTF fonts from Windows installed so I can view some reports correctly.  I've installed the mstccorefonts package and that worked correctly.  There are however a few additional fonts that I'd like to install manually - for example guramond.

After googling around I've become extremely confused by font-servers, x-configs and goodness knows what.  I think I've found out how to install the fonts for Open Office but I'd prefer to install them for the whole system.

I would be very grateful if somebody could let me know the following in understandable terms:

1. The directory or directories I need to copy my TTF files to
2. How to let the system know about the new fonts
3. If not automatic, how to let Open Office know about the new fonts

Many thanks!

---

### Post by flaming_monkey on 2005-10-18
1. fonts just for you live in ~/.fonts 
    fonts for all users /usr/share/fonts/truetype

2. Run fc-cache - build font information cache files
```
sudo fc-cache
```

3. Restart Open Office. If that doesn't work, log-out and in again.

---

### Post by David Marrs on 2005-10-18
[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts)

In step 3, msttcorefonts is the package you need to install

---

### Post by flaming_monkey on 2005-10-18
NOTE:
I followed that guide and altered my local.conf, Steps 4,5, and it screwed my fonts up. I would advise you to miss those out and test you system first. If you need to, you can always alter the file later.

---

### Post by ChrisTheGeek on 2005-10-20
Thankyou for the replies, I'm still having trouble with it though.

I did the following:

sudo -s
cd /usr/share/fonts/truetype
mkdir extra
cd extra
cp ~/documents/fonts/*.ttf .
fc-cache
exit

This put garamond and a few other fonts in a new subdirectory under /usr/share/fonts/truetype.  The cache program worked but I still can't see garamond in open office.  I tried restarting gnome and trying again but they still weren't there.  I've also tried looking at the fonts available in gedit but they weren't there either.  Any ideas?

Thanks again.

---

### Post by manicka on 2005-10-20
you just need to copy the fonts into /usr/share/fonts/truetype. You don't need the extra directory. The easiest way if this still won't work is to place the ttf's in the .fonts folder in your home directory. This will only work for your login, but it will work.

---

### Post by ChrisTheGeek on 2005-10-20
I've tried putting the TTFs straight in /usr/share/fonts/truetype, running fc-cache, logging on again and the fonts were still not visible in open office or gedit.

So I created a .fonts directory in my home directory and put the files in there.  I then ran 'sudo fc-cache' and logged in again.  This time the garamond font was visible in gedit but still a no show in open office.  Actually, when I chose garamond in gedit the program crashed :(

---

### Post by ChrisTheGeek on 2005-10-25
Am I right in thinking TTF files are independent of operating system?  I still can't get this font working and was wondering if it was because it came from my Windoze box?

---

### Post by SilentCacophony on 2005-10-25
[QUOTE=ChrisTheGeek]Am I right in thinking TTF files are independent of operating system?  I still can't get this font working and was wondering if it was because it came from my Windoze box?[/QUOTE]

Hi. TTF surely is a portable format. I copy them from my Windows 98 installation every time I install Ubuntu. I also just copy them to ~/.fonts, and generally don't even need to run fc-cache afterwards, for the apps that I commonly use to see them.

---

### Post by arXonik on 2005-10-25
hi, the guide by **flaming_monkey** completely worked for me. you don't need to do the changes system wide if its only you using the system, I like to do everything i can within my own home directory, the problem  may be the rights, since you created the directory .fonts, copied the fonts and ran the *fc-cache* command in your home directory in .fonts as root, there might be some issues (am not sure, I am a linux newbie) but would guess that could cause some trouble, because you don't have the rights to that entire .fonts dir.

If it's only you using the computer and there are no other users, just copy all the fonts you wish to use into your own .fonts directory within your home directory, DON'T DO IT AS SUDO, but from your own account! change into the .fonts directory and run *fc-cache* (NO SUDO EITHER, and i would advise you not to use the *sudo -s* command at all, you can mess up your system bad that way :rolleyes: ) and just to make sure log out and log back in into the gnome session, worked for me perfectly, even without logging out and in. cheers :KS

---

### Post by ChrisTheGeek on 2005-10-25
I've found the problem, the font files had the wrong owner since they were originally copied off my Windows partition!  A quick 'sudo chown' sorted that out and I now finally have the fonts working!

Thanks a lot for all the help!

---

