---
title: "XPS17 - NVidia GT555M - Display Troubles"
date: 2012-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by besoul on 2012-04-25
Hi everyone,

Please I really need your help,

I just bought a new computer DELL XPS17 with a graphic card GeForce GT555M, but the fact is I have many troubles with this graphic card.

I tried to install the latest version of Ubuntu, but I have a black screen at restart; then I decided to install the previous one, 10.04, I succeeded, but with low-graphics, so I can't work on it.

I read on some topics that it came from Optimus, and that I should install Bumblebee. I tried without any success.

Please, help me guys... I'm desperate...

---

### Post by piperbarb on 2012-04-25
[LEFT]Go to the following thread, [http://ubuntuforums.org/showthread.php?t=1898373](http://ubuntuforums.org/showthread.php?t=1898373) and scroll down to the post by spawes, dated Jan 17, 2012.  Follow the instructions there (do a clean install), and it will work perfectly.  It is important that you set acpi=off.  You can also check [http://ubuntuforums.org/showthread.php?t=1898373](http://ubuntuforums.org/showthread.php?t=1898373), for more detailed information.

This will let you install 11.10 and then be able to install bumblebee, albeit, at 720x480 (until you install bumblebee & reboot).

I followed those instructions and it worked like a champ.  I have the same Dell and everything worked perfectly after installing bumblebee.  No problems with anything.  I installed 11.10 on my Dell L702x back in early March and haven't looked back.  you'll be very happy you did.

Good luck.

[/LEFT]

---

### Post by J4C0814N on 2012-04-25
I had the same issues with mine.

What I ended up doing was installing 10.04. Once that was installed I did an upgrade to 12.04 and just skipped 11 all together.. ([alt+F2] then type update-manager -d) then up the top there was the option to upgrade to 12.04) I could not upgrade to any 11 build either.

I have been using 12.04 for about a week now, installing bumblebee fixes alot of issues and everything works except for the wireless driver (for the intel 1030) 

If you dont want to do the upgrade method the final build is scheduled to be released any day now I believe and that should work straight from the disk.

---

