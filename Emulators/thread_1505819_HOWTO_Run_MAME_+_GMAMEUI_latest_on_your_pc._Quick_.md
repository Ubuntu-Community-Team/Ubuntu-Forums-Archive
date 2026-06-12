---
title: "HOWTO: Run MAME + GMAMEUI latest on your pc. Quick guideWithout further ado – A qiuck"
date: 2010-06-09
forum: Emulators
---

### Post by deckoff on 2010-06-09
Without further ado &#8211; A qiuck guide  for newbies how to get MAME up and running on your Lucid Ubuntu up and running
 
[LIST=1]
[*]get latest mame from here:      [http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/).     Choose first [mame-common]("http://sdlmame4ubuntu.org/cur/major/pool/unofficial/m/mame/mame-common_0.138-0ubuntu1%7Eww1%7Elucid_all.deb")     which is suitable for your Ubuntu ( Lucid in our case) and let     synaptic package manager install it. Be sure to go with COMMON     FIRST.OTHERWISE YOU WILL GET AN ERROR. Then go and install mame and     mame tools the same way. I choose sdlmame( now officialy merged with     mame) cos this project is alive and updated. You will find XMAME     proposed as a choice more often, but this project is dead now.
[*]Now we have to put GUI for your     convinience  This is the so-called frontend. I like best GMAMEUI.     Still supported and with nice GNOME interface. Run your software     manager, cearch for GMAMEUI, and install it. The shortcut will     appear in Programs &#8211; Games. Well,run it. GMAMEUI will ask you     where your mame app is. It is located in /usr/games. And is called     mame(surprised?) ;) Set a folder you wish for your roms folder. Be     sure to remember what you've chosen
[*]Some settings that can     DRAMATICALLY improve your performance. Go with Options &#8211; Default     Options. In video be sure that for Video mode OpenGL is selected. [U][[IMG]http://img155.imageshack.us/img155/8089/31366605.th.png[/IMG]]("http://img155.imageshack.us/i/31366605.png/")

[/U]
[*]                                  Next, deselect filter in OpenGL : [U][[IMG]http://img526.imageshack.us/img526/5951/23841751.th.png[/IMG]]("http://img526.imageshack.us/i/23841751.png/")

[/U]
[*]                                  AND, FINALLY CHECK PERFORMANCE. MAKE SURE AUTOMATIC FRAMESKIP IS SELECTED.([I] This setting changes performance dramatically for me. Games can change from barely playble to perfect performance with this setting, at least for me :) 
[U][[IMG]http://img411.imageshack.us/img411/73/18418448.th.png[/IMG]](http://img411.imageshack.us/i/18418448.png/)

[/U]

[/I]
[*]That's petty     much all. Go and use your ROMS now, put them in your roms folder,     then : File &#8211; Audit All Games , wait for a while, and double click     your rom and play it
[/LIST]
[I]Some tips:
  [/I]   **TAB** when game started will bring a menu, which will let you change lots of setings, game controls most notable.
 **F11** will show performance. Percents shown better be around 100%. Lower  percents shown mean worse performance.
 

 My PC is IBM Thinkpad x40. It is old enough, and I get nece playing experince &#8211; better than MAME run under XP. These setting work fine for me. If  they dont work for you, fiddle with default options.
 Hope I helped.Now lets play Pacman :)

---

### Post by TempleNav on 2010-06-09
> **deckoff said:**
> Without further ado – A qiuck guide  for newbies how to get MAME up and running on your Lucid Ubuntu up and running
 
[LIST=1]
[*]get latest mame from here:      [http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/).     Choose first [mame-common]("http://sdlmame4ubuntu.org/cur/major/pool/unofficial/m/mame/mame-common_0.138-0ubuntu1%7Eww1%7Elucid_all.deb")     which is suitable for your Ubuntu ( Lucid in our case) and let     synaptic package manager install it. Be sure to go with COMMON     FIRST.OTHERWISE YOU WILL GET AN ERROR. Then go and install mame and     mame tools the same way. I choose sdlmame( now officialy merged with     mame) cos this project is alive and updated. You will find XMAME     proposed as a choice more often, but this project is dead now.
[*]Now we have to put GUI for your     convinience  This is the so-called frontend. I like best GMAMEUI.     Still supported and with nice GNOME interface. Run your software     manager, cearch for GMAMEUI, and install it. The shortcut will     appear in Programs – Games. Well,run it. GMAMEUI will ask you     where your mame app is. It is located in /usr/games. And is called     mame(surprised?) ;) Set a folder you wish for your roms folder. Be     sure to remember what you've chosen
[*]Some settings that can     DRAMATICALLY improve your performance. Go with Options – Default     Options. In video be sure that for Video mode OpenGL is selected. [U][[IMG]http://img155.imageshack.us/img155/8089/31366605.th.png[/IMG]]("http://img155.imageshack.us/i/31366605.png/")

[/U]
[*]                                  Next, deselect filter in OpenGL : [U][[IMG]http://img526.imageshack.us/img526/5951/23841751.th.png[/IMG]]("http://img526.imageshack.us/i/23841751.png/")

[/U]
[*]                                  AND, FINALLY CHECK PERFORMANCE. MAKE SURE AUTOMATIC FRAMESKIP IS SELECTED.([I] This setting changes performance dramatically for me. Games can change from barely playble to perfect performance with this setting, at least for me :) 
[U][[IMG]http://img411.imageshack.us/img411/73/18418448.th.png[/IMG]]("http://img411.imageshack.us/i/18418448.png/")

[/U]

[/I]
[*]That's petty     much all. Go and use your ROMS now, put them in your roms folder,     then : File – Audit All Games , wait for a while, and double click     your rom and play it
[/LIST]
[I]Some tips:
  [/I]   **TAB** when game started will bring a menu, which will let you change lots of setings, game controls most notable.
 **F11** will show performance. Percents shown better be around 100%. Lower  percents shown mean worse performance.
 

 My PC is IBM Thinkpad x40. It is old enough, and I get nece playing experince – better than MAME run under XP. These setting work fine for me. If  they dont work for you, fiddle with default options.
 Hope I helped.Now lets play Pacman :)

Mine doesnt work. I did everything like you said and when I try to use OPENGL plugin the image doesnt work at all. all I get is a black screen with snow on the top of it... Is there something wrong with SDLMAME?

---

### Post by deckoff on 2010-06-09
Hm. most probably OpenGL not installed not supported by hardware. What happens if you try to open a game> I assume the YUV mode is active and selectable. Try playibg with this setting.
Which game did you try?

---

### Post by TempleNav on 2010-06-09
> **deckoff said:**
> Hm. most probably OpenGL not installed not supported by hardware. What happens if you try to open a game> I assume the YUV mode is active and selectable. Try playibg with this setting.
Which game did you try?
 I tried shutting off the GLSL adn it works a lot better now. I am using an ATI 3870 card, I installed the proprietary drivers, so that shouldnt be a problem. Also I found that KOF 98' audits on my windows mame, but oddly doesnt in GmameUI. The only feature that I am missing at this point when you go full screen, there is no 'clean stretch' option. It looks washed out...

---

### Post by deckoff on 2010-06-10
1) Performance - a few reported that turning off OpenGL provides better performance. Disabling GLSL seems to work,s too :) What happens when you press F11 in gamescreen mode - in the upper right corner there is a percent showing, which changes all the time - if it goes around 100%, you are probably doing fine. How does the gameplay feel? that is all that is  important.
2) Audit of games - The most popular emulators for Windows are  mame32 0.90 and 103. At the least, this is my impression. They are based on older versions of mame. sdlmame is based on the latest version of mame. With different versions of mame, the files required to go in the rom have changed(rom dump is different). So, most probably you are using older version of the rom. Mame .133 (or higher)  version of the rom should be used. You can try to run your rom and see which files are reported missing.
3)Full screen - Options - Default Options - Display. There goes this setting : Run in Window. Did you notice it? It has to be **unchecked** to run in full screen
Please report if this solves your problems

---

### Post by cinikal on 2010-07-03
Hi there deckoff! Im Really new to Linux in general so go easy on me. I downloaded the sdlmame file that i needed for my ubuntu 10.04 lucid lynx and i ended up with a .deb file in the /tmp folder. your next step states let synaptics install it? how do i do that. If i right click the file the only thing i see available is "open with gdebi package installer" If i choose that it seems like its going to install but i get "Error: Dependency is not satisfiable: mame-common (= 0.138u2-0ubuntu1~ww1~lucid)" 

To be honest i had tried getting mame running on my own using the ubuntu software center and installing GmameUI thinking it was a complete package but when i ran the program i saw that it asked for the executable for mame. Thats when i did a search and found this page. Do i need to uninstall GmameUI first? does the order matter? and how do i use synaptics instead of Gdebi. I'm sooo confused.... :confused:

Thank you for any help

---

### Post by Objekt on 2010-07-03
> **cinikal said:**
> Hi there deckoff! Im Really new to Linux in general so go easy on me. I downloaded the sdlmame file that i needed for my ubuntu 10.04 lucid lynx and i ended up with a .deb file in the /tmp folder. your next step states let synaptics install it? how do i do that. If i right click the file the only thing i see available is "open with gdebi package installer" If i choose that it seems like its going to install but i get "Error: Dependency is not satisfiable: mame-common (= 0.138u2-0ubuntu1~ww1~lucid)" 

I am having *exactly* the same problem, trying to install the 64-bit .deb of the latest mame release (confusingly, sdlmame changed names to just plain mame).

The file is mame_0.138u2-0ubuntu1~ww1~karmic_amd64.deb, and I downloaded it from the "sdlmame4ubuntu" page ([http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/)).

Thing is, I definitely *DO* have the "mame-common" package installed, according to Synaptic.  So what's the deal?!

Confusingly, the sdlmame devs have chosen to rename their project to simply "mame."  This is the name of the exectuable if you have a recent version (0.138 for example).  I am going to continue to refer to it as "sdlmame" here, to avoid confusing it with the dozens of other mame variations that exist.

To answer your question: No, I don't think it makes any difference whether you install GMAMEUI or sdlmame first.  GMAMEUI does need to have a mame executable.  If you use a recent sdlmame it will be stored in /usr/games/mame (again, they've dropped the "sdl" for no obvious reason, to the confusion of users).  The GMAMEUI executable is there also.

I don't know anything about "gdebi."  I have always had Synaptic Package Manager, but then again I'm using Ubuntu 9.10.  Maybe that's a difference between 9.10 and 10.04.

---

### Post by cinikal on 2010-07-03
can someone just tell me how to get synaptic package manager to install mame-common? I downloaded the correct version and im guessing i had to extract that so i did now i have a mame common folder with a control.tar.gz folder and a data.tar.gz plus a debian binary file. What do i have to do to get synaptic to install this..

---

### Post by cinikal on 2010-07-03
Ok..I figured it out after banging my head. i had the wrong common file to begin with. there is one that has a "u2" in the file name.. that one gave me the error. then i saw another mame-common without the "u2" in it and tried that. then i got a different error. this time dealing with 3 xmame files. so using synaptics i uninstalled all 3 of those files. went back to my "new" mame-common file that i downloaded and double clicked on it and gdebi (which i am assuming is similar to synaptics)installed it flawlessly. I then went back to the sdlmame download page and downloaded the matching mame and mame  tools  files without the "u2" in the file name and installed them in that order and VIOALA!!! Working Mame.

---

### Post by Objekt on 2010-07-03
So...there's some other version of "mame-common" that I need, not the one in the Ubuntu Karmic repository?

I'm pretty sure I had this same problem with the earlier sdlmame version (0.138u1), but I can't remember how I solved it.  bah.

---

### Post by cinikal on 2010-07-03
Im really no expert but if you look at the dropdown list on this page: [http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/)
that first set of downloads Common, tools, and mame that are 0.138u2 didnt work for me. but i tried the next group down, the plain ole' 0.138 and they worked perfectly. i installed the common first then the mame then the mame tools. Hope it helps.

---

### Post by Objekt on 2010-07-04
Oops, I forgot about that stuff.  Here's what worked for me:

0) download all 3 items (mame-common 0.138u2, mame-tools 0.138u2, and mame_0.138u2, all for 64-bit Karmic in my case).

1) remove existing mame-common in Synaptic.

2) run "mame-common_0.138u2-0ubuntu1~ww1~karmic_all.deb".  It will complain, saying you should stick with the older version from the software channel.  That's not what we're doing here, so proceed with the installation anyway.

3) run "mame-tools_0.138u2-0ubuntu1~ww1~karmic_amd64.deb" (that's the 64-bit version - you may need the 32-bit version).  Again, it will complain, saying you should stick with the older version from the software channel.  That's not what we're doing here, so proceed with the installation anyway.

4) finally, run "mame_0.138u2-0ubuntu1~ww1~karmic_amd64.deb" (again, this is the 64-bit version - you may need the i386 version).

5) open GMAMEUI.  It automagically detects & uses the updated MAME executable (now 0.138u2 instead of plain 0.138), since the new 0.138u2 mame has been installed in the same place as the old mame executable.

I was hoping that the new 0.138u2 build might make a few more games start working, but I haven't seen any drastic improvements so far.

---

### Post by BigSilly on 2010-07-04
> **Objekt said:**
> 
I was hoping that the new 0.138u2 build might make a few more games start working, but I haven't seen any drastic improvements so far.

A newer version of MAME is more likely to break compatibility than improve it sadly. It depends on your rom set, as MAME roms update as often as the emulator itself. I still use version 0.130 with GMAMEUI, as I have a full 0.130 romset. If I "upgrade" to the latest version, then I can kiss goodbye to a massive swathe of my favourite games.

MAME can be a real pain in this way, whichever OS you run it on. I was very lucky to get a full set, and I have no intentions of moving from it yet.

Why do you have to install all those files? I just have sdlmame 0.130 64 bit, and I just install that then grab GMAMEUI from the repository. That's enough for me to run the emu without installing mame-common and mame-tools. :confused:

---

### Post by deckoff on 2010-07-08
> MAME 0.138u2**Tuesday, 29th June 2010**

             After a bit of trouble (including a server crash) it's  time for the next unstable release. Grab it for Lucid, Karmic or Hardy.
[LEFT]So, U2 stands for unstable, I went with stable when I installed it, and works great for me.[/LEFT]
[LEFT] Bout the older version - yes, more ROMS are correct, but is much harder to find the older versions than newer.... hence this tutorial...
[/LEFT]

---

### Post by karmila on 2010-09-13
Don't work for me. Crashed as soon as it played :(

---

### Post by SoFl W on 2011-01-01
I have used MAME before under Windows with no problems, I have decided to give it a try under Ubuntu to play one game.  I downloaded "gmameui", and the mame common files, the program starts and seems to run fine.  I downloaded the rom, set up the correct paths,  audit games and the green check mark appears next to the game I want to play.  I go to play it and it tells me the roms are not found and lists the roms.

I seem to remember upgrading MAME under Windows made a lot of the ROMS incompatible.   Am I doing something wrong or is this a mame / rom compatibility issue?

---

### Post by SoFl W on 2011-01-03
Bump.  (Should have waited until after the new year break)

Anyway, I made a slight improvement but it still says it can't find the ROMs.  These are the legal roms from the MAME site.  (I like TARG, I am strange)  It acts like it is going to load, gets to the percentage screen, waits a second or two and then drops out.
Attached are the after audit verify and then the error saying it can't find the roms.

Is it a permission issue?  Do I not have the correct unzip file?

Thanks

EDIT:
I fixed the missing rom problem when it audits the roms correctly.  Goto to the "/etc/mame" directory,  sudo edit the mame.ini file to include your rom directory.  The GMameUI directory options also need to be adjusted as well as the mame.ini file.

---

### Post by gianluca.pettinello on 2011-01-05
I tried to install mame 0.141 and, as mame 0.140, when I launch a game and put in fullscreen, the ram is completely filled by mame task (1.5 GB).
Did somebody of you experienced the same?

Thanks for your help
Gianluca

---

### Post by gianluca.pettinello on 2011-01-05
I discovered that this memory leak is linked to overlay effects. If I put none on effect in mame.ini, memory stay max 200 MB

Any siggestion?

Gianluca

---

### Post by ramiCZ on 2012-02-11
Hi there!

Please, is there an option how to implement or add kaillera client to mame emu? (I own Ubuntu 11:04)
I´ll be so glad for some responses!

Thanks guys!

---

### Post by Mr Thriven on 2012-02-23
I am very new to linux/ubuntu and find that, after installing mame and gmameui I cannot move anything into the roms folder in mame.  It keeps saying "permission denied" Help?

---

### Post by DangerOnTheRanger on 2012-02-24
> **ramiCZ said:**
> Hi there!

Please, is there an option how to implement or add kaillera client to mame emu? (I own Ubuntu 11:04)
I´ll be so glad for some responses!

Thanks guys!

Kaillera is Windows-only; you won't be able to use it on Ubuntu. That said, Kaillera is obsolete anyway - I recommend you take a look at GGPO or Supercade if you want to play your ROMs with others online.


> **Mr Thriven said:**
> I am very new to linux/ubuntu and find that, after installing mame and gmameui I cannot move anything into the roms folder in mame.  It keeps saying "permission denied" Help?

Sounds like the ROMs folder is in a directory that your user account doesn't own - /usr/share, most likely. Try changing the ROM folder path to some place in your home directory.

---

### Post by melendro on 2012-04-29
It seems that gmameui has disappeared in 12.04 "precise".
Is there any alternative to have a GUI for playing MAME games now?
I'm using kubuntu, so a KDE front-end would be better, but a GNOME front-end is also acceptable for me.

---

### Post by masterbyte on 2012-06-10
> **melendro said:**
> It seems that gmameui has disappeared in 12.04 "precise".
Is there any alternative to have a GUI for playing MAME games now?
I'm using kubuntu, so a KDE front-end would be better, but a GNOME front-end is also acceptable for me.
i have the same question...

---

### Post by nll on 2012-06-11
> **melendro said:**
> It seems that gmameui has disappeared in 12.04 "precise".
Is there any alternative to have a GUI for playing MAME games now?
I'm using kubuntu, so a KDE front-end would be better, but a GNOME front-end is also acceptable for me.

Hey, that sucks! Ok,  it was not properly maintained, but it still was the best MAME GUI around.

---

### Post by masterbyte on 2012-06-13
i found a solution...

[http://qmc2.arcadehits.net/wordpress/](http://qmc2.arcadehits.net/wordpress/)

i don't know if is better than GMAMEUI, but it works for me...

---

