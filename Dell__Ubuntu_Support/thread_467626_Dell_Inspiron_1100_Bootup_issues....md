---
title: "Dell Inspiron 1100 Bootup issues..."
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by BlacKoffee on 2007-06-07
Hola all,

I posted on here a bit about a year ago, but never did get my Ubuntu working right. Now, I'm trying it again, and I'm having a new set of issues. 

I just installed Ubuntu (Fiery Fawn version) on my Dell Inspiron 1100 laptop. It went through the setup perfectly, and acted great. I used my entire drive, so I'm not working with a dual boot situation. The problem is this: When I boot up, it doesn't go into the GUI. It will show the "Preparing Linux Kernel..." And all of that good stuff, and acts like it's loading up, but I never get to the desktop. I've already pulled the CD from the drive, and I know that this laptop can handle Ubuntu because I've had it on there before. 

Any ideas guys? I really want to get Ubuntu working so I can learn how to use it and convert my bad boy desktop over to Linux too. I want something better than XP, and I WILL NOT USE VISTA Lol

Help?

Thanks!
BlacKoffee

---

### Post by chuckdashparkerdotnet on 2007-06-08
My wife just spent most of the last 48 hours working on getting Xubuntu 7.04 running on her 1100 (Gnome Feisty was a little memory intensive for her 256mb of RAM).

Works fine now, but she couldn't get it on until she went with the "alternative install disc".    That might be worth your time.

The biggest problem I've seen with this box poking around the boards is the twitchy video issues with the box, which is well documented on this board.  That could be the problem.

I probably wasn't much help - sorry.  Check the search function; there are a lot of people working through issues on this particular laptop.

good luck!
-chuck

---

### Post by BlacKoffee on 2007-06-08
heh, well, it's a dell, what do you expect? lol. I'll give the alternate install disc a try then. My 1100 was upgraded to 512, so it's got a bit more oomph behind it. Heh, not much, but a bit. Hopefully that will work.

Thanks!

[EDIT]: Where can I find that, by the way? Is it just another option on the disc, or is it a download? heh, forgive my noobdom lol

---

### Post by chuckdashparkerdotnet on 2007-06-08
BK,

The alternate install (for standard Gnome/Ubuntu 7.04) is found on the regular download page, [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

make sure you click the little checkbox down toward the bottom to get the "alternate" install (text based rather than GUI).

again, good luck!

-chuck

---

### Post by BlacKoffee on 2007-06-08
I tried the other installer, and it didn't work either. I'm so friggin' STUMPED now :P Anyone have ANY ideas?! The video seems to be working and everything, it just won't boot into the GUI

Aaron

---

### Post by BlacKoffee on 2007-06-10
Can anyone give me any other ideas? I'm dying to get back to using ubuntu!

---

### Post by eapache on 2007-06-10
You say it won't boot into the gui, but what does it give you? A command-prompt? A blank screen?

---

### Post by dougleduck on 2007-07-23
I've got 1100 and don't think I had too many issues installing.

Occasionally I Have a problem when booting that the screen doesn't display anything which is a bit odd. Is this your problem possibly?

Does upgrading from 256MB to 512 MB significantly improve the system anyone know?

---

### Post by TsoTsalagi on 2007-10-17
I just installed Gutsy Gibbon on a Dell Inspiron 1100 (1GB RAM) and am having what appears to be the same problem you described; i.e., the GUI never appears...just a blank screen.  Like yours, mine is totally Linux - no Windoze.

I found that if I press the ESC key just as the initial text appears (about 15 seconds after powering on the PC, so the boot options display), then simply press ENTER (which selects the default/standard boot option), the GUI will load as expected.

I would be interested to know if this suggestion works for you, or not.

-Tso

---

### Post by JG53_Jaguar on 2007-10-17
Make sure you have the latest 1100 Bios update, I used to have this laptop and gave it to my GF. I remember the latest bios fixed some Linux video resolution issue. Also you might want to try 7.10 RC and see if that helps. I installed Ubuntu 6.04 when I used have my 1100 and I had no problems with video or anything gui related.

---

### Post by Mynes on 2007-10-20
I Had to Install 6.06 and Update till 7.10 then i followed instructions and works fine! :)

Ok make sure you have a upgraded to A32 bios..

[http://www.geocities.com/randomnumbergenerator2001/#bios_info](http://www.geocities.com/randomnumbergenerator2001/#bios_info)

and thanks to "nickware"

do this 

To fix this problem:
1. When you start your computer, hit F2 to enter Setup.
2. Alt-P (Turn the page) until you get to the page with the video memory.
3. Change the video memory("looks like a UMA but it is VMA") from 1MB to 8MB
4. Reboot

Works Fine Now! :):lolflag:

From my Post [http://ubuntuforums.org/showthread.php?t=573363](http://ubuntuforums.org/showthread.php?t=573363)

---

