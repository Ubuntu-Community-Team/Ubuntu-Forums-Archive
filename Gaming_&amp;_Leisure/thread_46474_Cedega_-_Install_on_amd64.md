---
title: "Cedega - Install on amd64?"
date: 2005-07-04
forum: Gaming &amp; Leisure
---

### Post by filemanager on 2005-07-04
I'm a noob, so could someone please explain to me in high detail how to install Cedega?

I followed <a href="http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64">these </a> directions. I seem to have a new folder called "TransGaming_Drive"

But I can't figure out how to install games using it.

I have The Sims 2 in my CD ROM, but when I run "cedega setup.exe" or "cedega /media/cdrom0/setup.exe" it gives me this error:

root@calvin3:/home/jen # cedega /media/cdrom0/setup.exe
/usr/lib/transgaming_cedega//winex/bin/wine: error while loading shared libraries: libwine.so: cannot open shared object file: No such file or directory

I tried installing point2play, but during the setup (same installation page as link above), I get this error:

root@calvin3:/home/jen # gedit .point2play/.winex_ver/winex-4.3.1/bin/winex3

(gedit:8510): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Someone please help :(

---

### Post by filemanager on 2005-07-05
I seem to have gotten Point2Play installed, and it then went and re-installed Cedega. Now I just have to figure out how Point2Play works.

I click the "Install" button on the toolbar, link to the CD rom and put the game title in, but when I hit "OK" or whatever, it puts the game name in the left window, but then it doesn't do anything.

---

### Post by DancingSun on 2005-07-05
I don't think Cedega is AMD64 compatible.  I don't have experience with it, but I did come across a couple of threads discussing the installation of Cedega on AMD64 Ubuntu.  Some people have gone the chroot32 route to get it working.

Try searching the forums.

Edit: Nevermind, just decoded your um...http link :D

---

### Post by Kemotaha on 2005-07-05
I have it running fine on my machine.  Mind you I am in the process of moving so I don't have it with me at the time.  I followed the steps on the WIKI and have gotten a fair number of games working.  

One thing I do to see if something is really happening is opening up the system monitor tool and watch the processes.  You can tell if it is doing something.

Let me know if you have any specific questions that I might help with.

---

### Post by WMCoolmon on 2005-07-06
Is there any difference, in terms of compatibility, between installing using the unofficial wiki instructions, or chrooting it?

I've got Cedega installed in my native 64-bit environment (using the 32-bit libs right now), but have yet to actually be able to _play_ a game. Farthest I've gotten is the Half-life 2 main screen. (But sound doesn't work)

---

### Post by Kemotaha on 2005-07-06
I don't know because I have never used the chroot environment.  I like to fiddle but it seems like too much of a hassle.  Because of that I have never found out.  I use point2play almost exclusively. I couldn't get anything to go using the full version of point2play.  I had to use the small version.  Then I had to add to the lib path in the winex file and I have everything working including sound.  The only problem I have is the font is sometimes screwed up in HL2, but you can still read it.

---

### Post by valadil on 2005-07-06
If this is an option for you, you should try installing games in an existing windows system, then rebooting to linux and emulating the already installed game.  In my experience, the installer of any given game is as likely to fail as the game itself.  

You can also try running smallish windows apps that aren't games just to see if cedega works properly.  I think I've had luck with winamp and aim as test apps.

---

### Post by Jet2k5 on 2005-07-07
Hmm what about this wiki?  Is [this ](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64) you are talking about?  

How well have you guys gotten this to work on Linux?  I'm so freaking nervous about building my 64-bit machine and games not workin!!! that's what the machine is for!!!!

---

### Post by Kemotaha on 2005-07-07
[QUOTE=Jet2k5]Hmm what about this wiki?  Is [this ](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64) you are talking about?  

How well have you guys gotten this to work on Linux?  I'm so freaking nervous about building my 64-bit machine and games not workin!!! that's what the machine is for!!!![/QUOTE]
 yep that is the WIki.  I have gotten a fair number of games to run.  If you see my previous post I don't have my machine handy but I know I have these working:

Warcraft3
Diablo2
HL2/Steam
Pirates!

I can't remember any others off the top of my head.  Hope that helps

---

### Post by Jet2k5 on 2005-07-07
Thanks for the post guy.  Really is good to hear that.  Please keep an eye out for the 64-bit section of the board since I'm going to be ordering my part in about 2 weeks or so.  Soo sometime this week or next week I'm going to make a post with my specs.  This way you guys can tell me if something doesn't work well on Linux and I can buy something that does. 

I've been googling for the past 2 weeks and it looks like most of the stuff is going to work.  The only things that really worry me right now is the onboard audio which is controlled by nforce4.  The chip is called Realtek 850, from looking on this forum it seems to work but not that great.   The other is the LAN Chip, I can't decide which one of the 2 chips it is .. just wit ti'll I'm make the post and you will have full details.

*EDIT* by the way did you need to set up the 32-bit chroot thingy to get cedega working or no?

---

### Post by filemanager on 2005-07-07
[QUOTE=valadil]If this is an option for you, you should try installing games in an existing windows system, then rebooting to linux and emulating the already installed game.  In my experience, the installer of any given game is as likely to fail as the game itself.  

You can also try running smallish windows apps that aren't games just to see if cedega works properly.  I think I've had luck with winamp and aim as test apps.[/QUOTE]
 Interesting idea. How do you emulate the already installed game?

---

### Post by Kemotaha on 2005-07-08
[QUOTE=Jet2k5]Thanks for the post guy.  Really is good to hear that.  Please keep an eye out for the 64-bit section of the board since I'm going to be ordering my part in about 2 weeks or so.  Soo sometime this week or next week I'm going to make a post with my specs.  This way you guys can tell me if something doesn't work well on Linux and I can buy something that does. 

I've been googling for the past 2 weeks and it looks like most of the stuff is going to work.  The only things that really worry me right now is the onboard audio which is controlled by nforce4.  The chip is called Realtek 850, from looking on this forum it seems to work but not that great.   The other is the LAN Chip, I can't decide which one of the 2 chips it is .. just wit ti'll I'm make the post and you will have full details.[/QUOTE]

I am using the NForce on board sound and have no problem.  I am only using the nvidia ethernet port.  I haven't tried the other one.  I forget what the chip is.  Funny thing is that windows blues screens when I use that ethernet port in dual boot.  I have to switch it when I go into Windows.  Oh Well.

[QUOTE=Jet2k5]
*EDIT* by the way did you need to set up the 32-bit chroot thingy to get cedega working or no?[/QUOTE]

I didn't use a chroot environment.

---

### Post by Jet2k5 on 2005-07-08
What I meant by the question and it's now clear to me, is I know you don't need the 32-bit chroot mode to get Cedega working since it install on 64-bit.  But as far as the games?  Do the games have to be run from a chroot mode, or can they be run from your regular /home/username.  

Sorry I'm not used to using Cedega and less 32-bit chroot mode :)

---

### Post by Kemotaha on 2005-07-10
I only use point2play and you can run it from your home.  It also installs an icon in the menu that I use to access it.  Then I run all my games from the point2play interface.  I believe you can run your games just using cedega from your home directory but I haven't done it much.  I hope that helps.

---

