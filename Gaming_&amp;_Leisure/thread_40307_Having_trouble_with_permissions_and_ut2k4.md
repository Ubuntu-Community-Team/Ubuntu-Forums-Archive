---
title: "Having trouble with permissions and ut2k4"
date: 2005-06-08
forum: Gaming &amp; Leisure
---

### Post by porkwarbler on 2005-06-08
Hi everyone, I'm new to Linux and Linux gaming. I have just finished setting up a triple boot machine for games running Windows XP, Win ME and Ubuntu Linux. Though the terminal is a bit daunting to me I have been able to Install video drivers for my FX 5900 by coming to these forums and cutting and pasting from the Unofficial starter guide into the terminal. Let me say first that I find Ubuntu to be incredibly impressive. I wish I had started with linux and not windows. Windows has made me very used to installing, patching and playing. With Linux, I find the Gui easy to work with, but the permission thing really really frustrates me. I succesfully installed ut2k4 and tested it with my user account. It launched and I decided to patch the game first with the bonus pack and then the 3355 patch. Since I am unfamiliar with the terminal and it frankly intimidates me, I cut and pasted the commands to enable the root account to log in with GNOME and I manually copied the patch folders into the ut2004 directory. Well the game seems to work properly If I am logged in as root. Both the patches seem to have installed properly, but now I can't launch the game as my default user. I guess to avoid all of this I would have installed the game to my default user's home directory, but I decided to install to the regular usr/local/games instead. I guess I could delete the directory as root and start over, but I wouldn't learn anything that way. Any help with this would be greatly appreciated. Oh, If you are wondering what a porkwarbler is, I can't answer that. It just popped into my head, and I figured no one else was using it.

---

### Post by ZeroA4 on 2005-06-08
Don't fear the bash! It's cool!

You should be able to play by entering "ut2004" at the run dialog or at the dreadfull command line! But it should also show up as a icon in Programs - Other or something like it...
I Have UT 2004 installed here and the icons where created by the installer.

By the way... do you know Red Orchestra ? It is a mod for UT2004.

---

### Post by Curlydave on 2005-06-08
Red Orchestra rocks. Alot. It has some bugs though associated with the OpenGL emulator UT2k4 uses as some of its effects (rain, modeled scopes specifically) use DX-specific code. 

Great game, but I don't want to think about the [lack of] performance I'd get trying to run it in Linux.

---

### Post by porkwarbler on 2005-06-08
Thanks for the replies, guys. I did find the shortcut. The game actually ran the first time. After I installed the patches it only would launch if I was logged in as root with the GNOME interface. I think somehow the permissions got screwed up after I patched it. Whats weird is that when I launch it as my default user the intro window pops up for a split second and then disappears and the program won't launch. If I'm logged in as root, the game launches properly. I'm gonna try to uninstall it as root and then reinstall to my home directory and see if that fixes it. Thanks again for your help.

---

### Post by Curlydave on 2005-06-08
Quick question that might seem random: Are you using the 64-bit install?

I'm asking because I used to use it, and running UT2k4 would work until I installed the ECE/patch, at which point it woulnd't run anymore. It turns out that a second binary was in the folder that indicated 64, and running that would work. The shortcut it puts in the gnome menu is not the 64-bit shortcut, and wouldn't run. I don't know if that binary existed before the patch, I just know that the original binary died after the patch and I had to use the 64 bit one.

(PS: try RO, it rocks!)

---

### Post by professor_chaos on 2005-06-10
As a related note from a somewhat new (compared to some) linux user.
Don't shy away from the terminal. There is real power there.
The more you use it, the more your will find the gui a distraction.

My 2 cents.
Good luck with your gaming. I love UT2004 and although Red Orchestra was a bit buggy (any grenede caused complete shell shock and white screen) it really has potential. Until recently I never knew linux had such gaming potential. I now spend more time gaming on ubuntu than my xbox.

---

