---
title: "GUIDE: karmic + sdlmame + wah!cade"
date: 2009-11-18
forum: Gaming &amp; Leisure
---

### Post by _mikec_ on 2009-11-18
I have a been playing with a bash script for a day now, it isn't my script (*[COLOR=DarkSlateGray]credits [/COLOR][COLOR=Blue][Jeremy Wininger]("http://www.alphaboxmedia.net/arcade/")[/COLOR]*) but i have modified/deleted many things, updated it, improved it, and sharing it after i was happy with end results. So, I personally consider the script my own, but the idea is not mine. Please link back to this Ubuntu thread if you want to share the script with your friends.

** Post back your thoughts and recommendations so i can update/modify the script.
*** [COLOR=Blue]Script Last modified: Wednesday Nov 18, 2009[/COLOR]*
***** Base operation system version changed from Ubuntu -> to Xubuntu 9.10, please download and install Xubuntu 9.10.***

_**Steps**_

**1)** Install Xubuntu 9.10
  * the current stable version, released in October 2009, codenamed Karmic Koala.*[INDENT]**a)** [[COLOR=Blue]download[/COLOR]]("http://www.xubuntu.org/get")
[/INDENT]**2)** After you have successfully installed Xubuntu, do not tweak it just yet. Since i assume you will be using this new installation for arcade gaming on a pc inside a cabinet and not for personal or business use, you need to first see if you can follow these few simple steps. 


**3)** Download the bash script and TAKE a look inside it. Make sure everything you need is in place. You need basic understand of the coding, i am sure everyone using Linux have basic coding understandings :)[INDENT]**a)** Download the attachment and edit line 5 if needed or uncomment line 4 and delete line 5
[/INDENT]**4)** Start a new terminal (gnome-terminal) and in the terminal type what you see in section 'b' below (step 4a), change the path to where you saved the 'cabsetup.sh' script (cabsetup.tar.gz). Type the root password. This will begin the arcade installation process by displaying a few options in front you. Keep the terminal on top of all your windows (right-click on the title bar and select 'Always On Top')[INDENT]** a)** Applications / Accessories / Terminal
** b)** sudo sh /home/arcade/Downloads/cabsetup.sh
[/INDENT]**5)** The first thing you want to do obviously is to uninstall packages you do not need and to update and upgrade your system. This will slim down the system but it will keep essentials packages for system maintenance in case something goes wrong, we do not want to reinstall Xubuntu, just follow the numbers in the terminal. If you need so, write down the location the script will give you at the end of step 'c', it's important but not necessary ![INDENT]**a) **Uninstall packages you do not need
**b)** Install packages and update the system
**c)** Setup SDLMAME directory structure
** d)** Remove all arcade packages and files
[/INDENT]**6)** After you've completed step 5, you can quit the script.


**7)** Next we need to install the best recommended video driver for your system. Regardless if you have an ATI or NVIDIA graphic card, the installation is the same. Please refer to the proper Ubuntu Forum section for help if you have issues with this step, as this Ubuntu Forum section is only for Gaming & Leisure, you can always post a link in this thread after you added your issue in the proper Ubuntu Forum section.[INDENT]**a)** System / Administration / Hardware Drivers
** b)** activate the recommended driver and when done, close it
**c)** reboot (bookmark this page for later references)
[/INDENT]**8)** After your system reboots, you need to start copying all your games to the location you saved earlier in step 5 section 'c', where it said to upload all your games to a specific location. You only want to do this to avoid repeating the step of generating the XML game list, you need to do this each time you add/remove games. If you have your games saved on another device and need help mounting devices with normal user permissions like cds/dvds/usbs/usb hard drives/ etc... Please search the Ubuntu Forums first and refer to previous solutions found by other Ubuntu satisfied users (just like me) remember this section is only for Gaming & Leisure.


**9)** After you have uploaded your games, we move on to configure wah!cade. It should be mostly all configured already, thanks to our default settings we did in step 5 section 'c'. If you need further analysis on configuring wah!cade, you can refer to the official wah!cade guide on the official website.[INDENT]** a)** [COLOR=Blue][official Wah!Cade guide]("http://www.anti-particle.com/wahcade_quick.shtml")[/COLOR]
**b)** Applications / Games / Wah!Cade Setup Editor
**c)** go to Keys tab:
      - review, keep or change following keys;

[LIST]
[*]UP_1_GAME *#move up one game in list *
[*]DOWN_1_GAME *#move down one game in list *
[*]UP_1_PAGE *#move up 1 page in list *
[*]DOWN_1_PAGE *#move down 1 page in list *
[*]UP_1_LETTER *#move back one letter (e.g. from game Dxxxx to Cxxxx) *
[*]DOWN_1_LETTER *#move forward one letter (e.g. from game Dxxxx to Exxxx)*
[*]EXIT_TO_WINDOWS *#exit Wah!Cade (back to desktop)*
[/LIST]
**d) **go to Wah!Cade tab:
       - biggest Layout offered in this guide is 1024x768
       - check mark 'Play Music From' option and enter a path where you have your music
       - do the same for Movies..
       - leave the rest as default
**e)** go to Emulators tab:
       - Leave all as default, except if you want to add more Emulators and Artwork
**f) **go to M.A.M.E. Only tab:
       - find XML / Data File, at the end there is a button to generate the XML file, click it.
**g)** **Important**, before you close, save the configure file! in _F_ile / _S_ave or Crtl + S
[/INDENT][B]

10)[/B] At this point we are almost done, you can start testing your games by running the wah!cade package. Fire it up and check it out if you want to, there's no rush yet. Your games should be listed, ready to be selected and play one of them, if not, go back to step 9 and make sure you have wah!cade properly configured. 90% of all errors are corrected in wah!cade setup editor. The wah!cade default controls below are for reference only, [COLOR=Blue][click here]("http://www.anti-particle.com/projects/wahcade/KEYS")[/COLOR] to see a complete list of the default keys. I use the X-Arcade Dual Joystick ONLY, i have not yet properly configured the keys 100%, please do not ask me.

[LIST]
[*]game selection down one - down key (player one joystick down)
[*]game selection next letter - right key (player one joystick right)
[*]game selection up one - up key (player one joystick up)
[*]game selection previous letter - left key (player one joystick left)
[*]game start - 1 key (player one button #1)
[*]menu - esc key (player one and two buttons at the same time)
[*]menu selection - 1 key (player one button #1)
[*]menu exit - esc key (player one and two buttons at the same time)
[/LIST]

**11)** After you are happy with your wah!cade configuration, it's time to configure gnome to launch it at boot time. Since, normally, arcade cabinets run 24/7 and linux is so stable, you can leave it running without any doubts. The problem here will be the electricity bill, this is another subject. While you have the Startup Applications Preferences window open, you can take the time to review the list and disable packages you do not need. If you are unsure about an application, do not disable, remove or edit it!. After you are done adding wah!cade to the Startup Applications Preferences you can close the window.[INDENT]**a)** System / Preferences / Startup Applications
**b)** click Add button
**c)** type the name: Wah!Cade
**d)** type the command: wahcade -f
**e)** type the comment: Arcade Gaming
[/INDENT]esac
Done!.

Before you reboot, i assume you want to enable auto-login of your account, because next time you reboot, Wah!Cade will start automatically in full screen mode. 


[LIST]
[*]- You have completed all the steps.
[*]- Successfully added your games.
[*]- Tested your joystick(s).
[*]- Tested wah!cade
[/LIST]

You can now go work in building your own professional cabinet. Please feel free to share your own story, thoughts, suggestions, code snippets (or complete rewrites) and your pictures.

                                 _**References**_
 
[LIST]
[*][[COLOR=Blue]Download     Xubuntu[/COLOR]]("http://www.xubuntu.org/get")
[*][[COLOR=Blue]Documention     for Xubuntu 9.10[/COLOR]]("https://wiki.ubuntu.com/Xubuntu")
[*][COLOR=Blue][Landscape,     to monitor your Arcade System]("http://www.canonical.com/projects/landscape/landscape-tour/") [[Purchase     require - ]("http://www.canonical.com/projects/landscape/landscape-tour/like-it/")[60     Days Trial]("http://www.canonical.com/projects/landscape/landscape-tour/like-it/")][/COLOR]
[*][COLOR=Blue][anti-particle.com:     wah!cade]("http://www.anti-particle.com/wahcade.shtml")[/COLOR]
[*][COLOR=Blue][Build     Your Own Arcade Control]("http://www.arcadecontrols.com/arcade.htm")[/COLOR]
[*][COLOR=Blue][MAMEWorld - The largest MAME Resource on the Net]("http://mameworld.info/")[/COLOR]
[*][COLOR=Blue][Welcome     to Ultimarc.com home page]("http://www.ultimarc.com/")[/COLOR]
[*][COLOR=Blue][Xgaming:     X-Arcade Indestructible Arcade Gaming For Your Home]("http://www.xgaming.com/")[/COLOR]
[*][COLOR=Blue][SDLMAME     for Ubuntu]("http://sdlmame.wallyweek.org/")[/COLOR]
[*][COLOR=Blue][Ubuntu     -- Details of sdlmame in karmic]("http://packages.ubuntu.com/karmic/sdlmame")[/COLOR]
[*][COLOR=Blue][Game Trailers]("http://www.gametrailers.com/")[/COLOR]
[/LIST]
 
Good Luck,


*_**Futher Updates see post below**_*

---

### Post by _mikec_ on 2009-11-21
[COLOR=DarkRed][U][B]post saved for futher updates

[/B][/U][COLOR=Black]I will be working on making my own Ubuntu remix using Xubuntu desktop, it requires less ram than Ubuntu or Kubuntu and since the computer i am using has little amount of ram i choosed Xubuntu ... I will be starting by next week Dec. 14th 2009. The script will be updated too. 

If you have Ubuntu already installed and wish to switch to Xubuntu (XFCE Ubuntu instead of Gnome) follow the guide here: (in my mind you're using a fresh Ubuntu installation and do not need to backup anything)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Do not know which Ubuntu release to use ? go here:
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

A lot of good Tutorials are found on the same site too.
[/COLOR][/COLOR]

---

### Post by dislocated on 2009-11-27
Thanks for the info! I'm soon going to be building a MAME cabinet with the kids to set up in the games room. I'm sure this info will come in handy. I'll let you know how it goes.

I'm stalling on buying some hardware to run MAME inside the cabinet, though. Not sure exactly how powerful (read expensive) it needs to be. Any suggestions?

---

### Post by _mikec_ on 2009-11-28
> **dislocated said:**
> I'm stalling on buying some hardware to run MAME inside the cabinet, though. Not sure exactly how powerful (read expensive) it needs to be. Any suggestions?

It all depends in the games you have or how many you have.

I have a 2002 old pc i want to through inside the cabinet; AMD Athlon XP 2.17Ghz, 512MB Ram, NVIDIA GeForce 4 128MB RAM.. It hangs when i try to load some of the games or just becomes very slow.. I have no problem playing PAC-MAN. I've read people having much cheaper computers running the games without problems.

I will recommend you read this Wikipedia: [http://en.wikipedia.org/wiki/MAME#Emulation_philosophy](http://en.wikipedia.org/wiki/MAME#Emulation_philosophy)

---

### Post by _mikec_ on 2009-11-29
if someone wants to modify the grub2 boot image to make your machine unique.
follow the steps in -> [http://ubuntuforums.org/showthread.php?t=1296225](http://ubuntuforums.org/showthread.php?t=1296225)

---

### Post by slave-zeo on 2010-01-11
> **_mikec_ said:**
> I have a been playing with a bash script for a day now, it isn't my script (*[COLOR=DarkSlateGray]credits [/COLOR][COLOR=Blue][Jeremy Wininger]("http://www.alphaboxmedia.net/arcade/")[/COLOR]*) but i have modified/deleted many things, updated it, improved it, and sharing it after i was happy with end results. So, I personally consider the script my own, but the idea is not mine. Please link back to this Ubuntu thread if you want to share the script with your friends.

** Post back your thoughts and recommendations so i can update/modify the script.
*** [COLOR=Blue]Script Last modified: Wednesday Nov 18, 2009[/COLOR]*

_**Steps**_

**1)** Install Ubuntu 9.10
  * the current stable version, released in October 2009, codenamed Karmic Koala.*[INDENT]**a)** [COLOR=Blue][download]("http://www.ubuntu.com/getubuntu/download")[/COLOR]
** b)** [COLOR=Blue][installation guide]("https://help.ubuntu.com/9.10/index.html")[/COLOR]
[/INDENT]**2)** After you have successfully installed Ubuntu, do not tweak it just yet. Since i assume you will be using this new installation for arcade gaming on a pc inside a cabinet and not for personal or business use, you need to first see if you can follow these few simple steps. 


**3)** Download the bash script and TAKE a look inside it. Make sure everything you need is in place. You need basic understand of the coding, i am sure everyone using Linux have basic coding understandings :)[INDENT]**a)** Download the attachment and edit line 5 if needed or uncomment line 4 and delete line 5
[/INDENT]**4)** Start a new terminal (gnome-terminal) and in the terminal type what you see in section 'b' below (step 4a), change the path to where you saved the 'cabsetup.sh' script (cabsetup.tar.gz). Type the root password. This will begin the arcade installation process by displaying a few options in front you. Keep the terminal on top of all your windows (right-click on the title bar and select 'Always On Top')[INDENT]** a)** Applications / Accessories / Terminal
** b)** sudo sh /home/arcade/Downloads/cabsetup.sh
[/INDENT]**5)** The first thing you want to do obviously is to uninstall packages you do not need and to update and upgrade your system. This will slim down the system but it will keep essentials packages for system maintenance in case something goes wrong, we do not want to reinstall Ubuntu, just follow the numbers in the terminal. If you need so, write down the location the script will give you at the end of step 'c', it's important but not necessary ![INDENT]**a) **Uninstall packages you do not need
**b)** Install packages and update the system
**c)** Setup SDLMAME directory structure
** d)** Remove all arcade packages and files
[/INDENT]**6)** After you've completed step 5, you can quit the script.


**7)** Next we need to install the best recommended video driver for your system. Regardless if you have an ATI or NVIDIA graphic card, the installation is the same. Please refer to the proper Ubuntu Forum section for help if you have issues with this step, as this Ubuntu Forum section is only for Gaming & Leisure, you can always post a link in this thread after you added your issue in the proper Ubuntu Forum section.[INDENT]**a)** System / Administration / Hardware Drivers
** b)** activate the recommended driver and when done, close it
**c)** reboot (bookmark this page for later references)
[/INDENT]**8)** After your system reboots, you need to start copying all your games to the location you saved earlier in step 5 section 'c', where it said to upload all your games to a specific location. You only want to do this to avoid repeating the step of generating the XML game list, you need to do this each time you add/remove games. If you have your games saved on another device and need help mounting devices with normal user permissions like cds/dvds/usbs/usb hard drives/ etc... Please search the Ubuntu Forums first and refer to previous solutions found by other Ubuntu satisfied users (just like me) remember this section is only for Gaming & Leisure.


**9)** After you have uploaded your games, we move on to configure wah!cade. It should be mostly all configured already, thanks to our default settings we did in step 5 section 'c'. If you need further analysis on configuring wah!cade, you can refer to the official wah!cade guide on the official website.[INDENT]** a)** [COLOR=Blue][official Wah!Cade guide]("http://www.anti-particle.com/wahcade_quick.shtml")[/COLOR]
**b)** Applications / Games / Wah!Cade Setup Editor
**c)** go to Keys tab:
      - review, keep or change following keys;

[LIST]
[*]UP_1_GAME *#move up one game in list *
[*]DOWN_1_GAME *#move down one game in list *
[*]UP_1_PAGE *#move up 1 page in list *
[*]DOWN_1_PAGE *#move down 1 page in list *
[*]UP_1_LETTER *#move back one letter (e.g. from game Dxxxx to Cxxxx) *
[*]DOWN_1_LETTER *#move forward one letter (e.g. from game Dxxxx to Exxxx)*
[*]EXIT_TO_WINDOWS *#exit Wah!Cade (back to desktop)*
[/LIST]
**d) **go to Wah!Cade tab:
       - biggest Layout offered in this guide is 1024x768
       - check mark 'Play Music From' option and enter a path where you have your music
       - do the same for Movies..
       - leave the rest as default
**e)** go to Emulators tab:
       - Leave all as default, except if you want to add more Emulators and Artwork
**f) **go to M.A.M.E. Only tab:
       - find XML / Data File, at the end there is a button to generate the XML file, click it.
**g)** **Important**, before you close, save the configure file! in _F_ile / _S_ave or Crtl + S
[/INDENT][B]

10)[/B] At this point we are almost done, you can start testing your games by running the wah!cade package. Fire it up and check it out if you want to, there's no rush yet. Your games should be listed, ready to be selected and play one of them, if not, go back to step 9 and make sure you have wah!cade properly configured. 90% of all errors are corrected in wah!cade setup editor. The wah!cade default controls below are for reference only, [COLOR=Blue][click here]("http://www.anti-particle.com/projects/wahcade/KEYS")[/COLOR] to see a complete list of the default keys. I use the X-Arcade Dual Joystick ONLY, i have not yet properly configured the keys 100%, please do not ask me.

[LIST]
[*]game selection down one - down key (player one joystick down)
[*]game selection next letter - right key (player one joystick right)
[*]game selection up one - up key (player one joystick up)
[*]game selection previous letter - left key (player one joystick left)
[*]game start - 1 key (player one button #1)
[*]menu - esc key (player one and two buttons at the same time)
[*]menu selection - 1 key (player one button #1)
[*]menu exit - esc key (player one and two buttons at the same time)
[/LIST]

**11)** After you are happy with your wah!cade configuration, it's time to configure gnome to launch it at boot time. Since, normally, arcade cabinets run 24/7 and linux is so stable, you can leave it running without any doubts. The problem here will be the electricity bill, this is another subject. While you have the Startup Applications Preferences window open, you can take the time to review the list and disable packages you do not need. If you are unsure about an application, do not disable, remove or edit it!. After you are done adding wah!cade to the Startup Applications Preferences you can close the window.[INDENT]**a)** System / Preferences / Startup Applications
**b)** click Add button
**c)** type the name: Wah!Cade
**d)** type the command: wahcade -f
**e)** type the comment: Arcade Gaming
[/INDENT]esac
Done!.

Before you reboot, i assume you want to enable auto-login of your account, because next time you reboot, Wah!Cade will start automatically in full screen mode. 


[LIST]
[*]- You have completed all the steps.
[*]- Successfully added your games.
[*]- Tested your joystick(s).
[*]- Tested wah!cade
[/LIST]

You can now go work in building your own professional cabinet. Please feel free to share your own story, thoughts, suggestions, code snippets (or complete rewrites) and your pictures.

                                 _**References**_
 
[LIST]
[*][COLOR=Blue][Download     Ubuntu]("http://www.ubuntu.com/getubuntu/download")[/COLOR]
[*][COLOR=Blue][Documention     for Ubuntu 9.10]("https://help.ubuntu.com/9.10/index.html")[/COLOR]
[*][COLOR=Blue][Landscape,     to monitor your Arcade System]("http://www.canonical.com/projects/landscape/landscape-tour/") [[Purchase     require - ]("http://www.canonical.com/projects/landscape/landscape-tour/like-it/")[60     Days Trial]("http://www.canonical.com/projects/landscape/landscape-tour/like-it/")][/COLOR]
[*][COLOR=Blue][anti-particle.com:     wah!cade]("http://www.anti-particle.com/wahcade.shtml")[/COLOR]
[*][COLOR=Blue][Build     Your Own Arcade Control]("http://www.arcadecontrols.com/arcade.htm")[/COLOR]
[*][COLOR=Blue][MAMEWorld - The largest MAME Resource on the Net]("http://mameworld.info/")[/COLOR]
[*][COLOR=Blue][Welcome     to Ultimarc.com home page]("http://www.ultimarc.com/")[/COLOR]
[*][COLOR=Blue][Xgaming:     X-Arcade Indestructible Arcade Gaming For Your Home]("http://www.xgaming.com/")[/COLOR]
[*][COLOR=Blue][SDLMAME     for Ubuntu]("http://sdlmame.wallyweek.org/")[/COLOR]
[*][COLOR=Blue][Ubuntu     -- Details of sdlmame in karmic]("http://packages.ubuntu.com/karmic/sdlmame")[/COLOR]
[*][COLOR=Blue][Game Trailers]("http://www.gametrailers.com/")[/COLOR]
[/LIST]
 
Good Luck,


*_**Futher Updates see post below**_*

While I appreciate you hacking away at MY script to improve it, I do not appreciate you linking directly to files on MY server with out asking me. That is bad form, my friend.

I spent a long time working on the scripts initial release and working on the configuration files for Wah!Cade. Please ask next time and you can have my blessings to link to what ever you want.

---

### Post by _mikec_ on 2010-01-17
> While I appreciate you hacking away at MY script to improve it, I do not appreciate you linking directly to files on MY server with out asking me. That is bad form, my friend.

I spent a long time working on the scripts initial release and working on the configuration files for Wah!Cade. Please ask next time and you can have my blessings to link to what ever you want.Well, i should of link them somewhere else then, perhaps my web site, it just gives you more traffic on your site reason why i linked to your site (if you want more exposure of your site, if not i am sorry). 

I am asking you perhaps now ? 

I do apologize for any misunderstandings.

I am sure others including me do appreciate your work on files for Wah!Cade. If you decide on improving it, please inform us so we can share it and make good use of them. 

I would of at least appreciated that you do not vote no in the poll...

Cheers,
mike

---

### Post by chuckyp on 2010-01-18
This guide is nice and a big help for people wanting to build a linux mame cabinet. I would like to see someone get a terminal based linux mame cabinet working. Because X is not needed for sdlmame to run at all. I've played with getting one going with out X and here are a few of the problems I ran in to:

sdlmame runs slower for than mame in dos. This can be seen in games like killer instinct is playable in mame but on sdlmame it runs slower.

I also could not get sound working in sdlmame with out X installed. For somereason xubuntu-desktop or ubuntu-desktop has a package that makes sound work.

Getting proper video to work with sdlmame in terminal is a real strugle with ubuntu. They have completely removed frame buffer drivers etc...

---

### Post by _mikec_ on 2010-01-27
chuckyp, thanks for your reply, for now i've been working on a custom version of OpenSUSE 11.2 because it is easier for me to create my own distro using the SuseStudio online, i have chosen the XFCE 4 for this because it is the smallest way to create a nice and easy to use desktop. There's also other WM but it gets complicated to get everything working properly.... Also, the reason why i dropped Ubuntu is because almost nobody responded to this guide.

cheers and good luck!

---

