---
title: "Xfce +(4?) for gaming interface?"
date: 2005-06-26
forum: Desktop Environments
---

### Post by Omnios on 2005-06-26
Hio community I have a problem with my frame rates, I have a P4 1.6ghz, 256K RAM and a 64meg nvidia card. In both Gnome and Kde I get clear screen rates of 400-405 but another oddity is if I open up a couple windows while glxgears is running in runs in the 1,000s. My main commercial game is Never Winter nites and has a mouse bug when the frame rate runs real low which it shouldn't be doing. Ive tryed the official drivers and didnt notice any real improvement (current ubuntu "nvidia" drivers are looking good!). 

 Anyways what I think is happening though not shure is that when the game is running the sceen load is still running in the back ground which would explain the high load. My friend played this game on a intel shared ram video card with no problems and also runs well in XP (hopefully my last microsoft purchase! "crosses fingers"). also the reuirments for the game are. 16 MB TNT2-class OpenGL 1.2 compliant video card.

 Anyways what im planning to do it load xfce or Xfce4 to use for launching games hopefully with better game performance. 

 Anyone have any suggestions.

 "Edit: umm forgot what is the difference between Xfce and Xfce4?"

---

### Post by Omnios on 2005-06-26
Just had a brain storm! A game laucher that is configured in your main desktop "gnome etc" launcher kickes you out of gnome etc and puts you into the laucher windows manager interface that allows you to lauch your heavy footprint games.

 So basicly it could have a gnome config program
and a minimal game windows interface.

  This may greatly help low resource machines and even machines that are just winging it.

---

### Post by Omnios on 2005-06-27
K I loaded Xfce4 which is choosable through the sessions manager. Running glxgears I got a +5 fps increase on my nvidia measured by benching logging into gnome then benching gnome. On the upside I found glxgears ran more consistantly in Xfce without the rate drops I usesualy got in gnnome. ALso when running apps while glxgears was running showed more consistant results without huge drops or increases.

 Xfce is fully functional and customizable to suit your gaming needs. I dont have any heavy games installed yet as I did a recent reinstall after borking a chmod "be very carefull with chmod -R 777 ........ ." Also things seemed to load much quicker and smoother in general and this hopefully should carry over to game performance. On the upside being fully functional you may do any game maintance such as lauchfiles etc in Xfce. 

 I plan on installing NWN and Nexuiz this week and will check them out in Xfce to see if there is a real big difference. 

 One not when I log off my screen flashes and I can see a open laptop sized gnome in the background and also in Xfce, is this normal? Kind off woried its running in the background?

 ANyways cheers and happy gamming.

"Edit:' note I changed my color depth from 24 to 16 in xorg.conf and my glx gears whent from 401fps to 795 fps."

---

### Post by smoon on 2005-06-27
[QUOTE=Omnios]Just had a brain storm! A game laucher that is configured in your main desktop "gnome etc" launcher kickes you out of gnome etc and puts you into the laucher windows manager interface that allows you to lauch your heavy footprint games.

 So basicly it could have a gnome config program
and a minimal game windows interface.

  This may greatly help low resource machines and even machines that are just winging it.[/QUOTE]

You might want to try out [Xgame](http://freshmeat.net/projects/xgame/). The GTK+2 Program can be found at [http://www.xs4all.nl/~masterpe/Perl/xgame-gtk2](http://www.xs4all.nl/~masterpe/Perl/xgame-gtk2). I don't really like it's interface, but it does exactly what you suggested.

Maybe someone knows a more userfriendly one? If not and enough people are interested I might write one...

---

### Post by Omnios on 2005-06-27
[QUOTE=smoon]You might want to try out [Xgame](http://freshmeat.net/projects/xgame/). The GTK+2 Program can be found at [http://www.xs4all.nl/~masterpe/Perl/xgame-gtk2](http://www.xs4all.nl/~masterpe/Perl/xgame-gtk2). I don't really like it's interface, but it does exactly what you suggested.

Maybe someone knows a more userfriendly one? If not and enough people are interested I might write one...[/QUOTE]

 Its not so much that people want one its more that they need one. I have a 1.6ghz P4 256meg ram and a nvidia gforce2 100/200 64 meg video card and have a hard time playing some pretty normal games that run ok in XP. Basicly im trying to cut out things running in the background when I go play a game "I even had problems with equake it ran but playability was way off" 

 what would be nice would be something like a wine set up where you put something in the run command like gameapp game-to-run with possibly a game regestry thing to auto find the games. Basicly have to kill everything in the background except possibly root :)  firewall. If you can write something like this I will definatly use it.    :)

---

### Post by Bandit on 2005-06-27
So why dont you just log out and then log in on straight xwindows?
There will not be any desktop enviroment to lag you down.
Just a thought..
Cheers,
Joey

---

### Post by skoal on 2005-06-27
Are you sure you have the "nvidia" binary installed and configured properly? I thought a GeForce2MX pulls in about ~1000FPS in 16bpp.  Maybe bump your resolution down to 800 for particular games.  I do the same for some games, even on my Ti-4600.

Check out [this](http://www.ubuntuforums.org/showthread.php?t=39349&highlight=glxgears) thread and see what other GeForce 2'ers are getting...

\\//_

---

### Post by Omnios on 2005-06-28
This post was first posted 24 hours ago in that time 99 people visited it. That brings me to believe that a gaming interface is of definate interest. Hopefully we may find a solution for better game performance on slower machines.

---

### Post by Bandit on 2005-06-28
[QUOTE=Omnios]This post was first posted 24 hours ago in that time 99 people visited it. That brings me to believe that a gaming interface is of definate interest. Hopefully we may find a solution for better game performance on slower machines.[/QUOTE]
Yea, remove Intel and install AMD :D
Was I thinking outloud again  :???:

---

### Post by Omnios on 2005-06-30
Installed Plane Shift which is a ram heavy game, at times I can play it in gnome but last night the game kept timing out loading lighting afrfects and going poof because the the system was 100% swampt. So I loaded it up in xfce and it ran real sweet. Hardly no problems at all and the system load was much more reasonable. In gnome my resorces where swampt out but in xfce it was running at about 50% to 75%.

 Im going to load Never winter nights and see how that game behaves in xfce. I used Xfce 4 becuse of all the gnome and Kde compatability, It will run gnome apps so should lessen any problems with games set up for gnome.

 Cheers and happy low end gamming.

---

### Post by Omnios on 2005-06-30
Added a Pole to the top of the thread if there is an interest maybe we can sway someone to develop somthing and have it as an Ubuntu feature. Please take the time to vote!

---

### Post by Omnios on 2005-07-01
poll bump.

---

### Post by Omnios on 2005-07-02
> You might want to try out Xgame. The GTK+2 Program can be found at [http://www.xs4all.nl/~masterpe/Perl/xgame-gtk2](http://www.xs4all.nl/~masterpe/Perl/xgame-gtk2). I don't really like it's interface, but it does exactly what you suggested.

Maybe someone knows a more userfriendly one? If not and enough people are interested I might write one... 

 Tryed using Xgame but found it didnt realy have any help files to read. Also had a problem that the game I play needs to be launched in root and the game wouldn't launch. Also found when comming out of the laucher that the screen came out in either root or some unknown account (I only have one account). Um anyone have any suggestions?

---

### Post by Omnios on 2005-07-05
Poll Bump!

---

### Post by Omnios on 2005-07-07
Poll Bump

---

### Post by Omnios on 2005-07-13
Tested out Never Winter Nights in Xfce and Ice today. The difference in nwn was dramatic. In Gnome nwn multiplayer was unplayable wich I think is because of ram usage. In Ice it was still unplayable but I think this is due to it not being configured properly. In Xfce it was playable to the extent of being jittery to fairly smooth. This is strange because I had it installed many months ago and it was playable in gnome before. The bottom line is that it whent from unplayable to playable so it is sort of proven that xfce could take a borderline playable game and make it playable on systems with limited ram.  Im going to try this with Nexuiz, it is playable in Gnome but gets jittery at times.

 As to a game custom game laucher I would recomend a system that takes the ram and forces it into swap till the person exits the game. I found that my system likes using 30 to 50% as cach and does not like letting it go. 

 Lastly does anyone know how to set up ice so it takes up a min of resources. I need to config the desktop for min processor memory useage so its available for gamming. 

 So far Xfce looks very promising!

 Edit: tryed Nexuiz in Xfce and the the difference in performance is amazing. Very smooth, controlls worked better and overall spead was greatly improved. Whant from so so to very playable.

---

### Post by Omnios on 2005-07-15
Thought of an interesting game launcher for linux that may work. The laucher would suspend all non essencial programs and destop items to disk and lauch on a blank background. The basis would be get all non game essencial stuff from active ram such as cach and running items to suspend freeing up ram for gamming. I tryed using xgame-gtk2 and realy didnt notice a Difference in performamce with NWN. 

 Never Winter Nights is kind of bothering me as before my Linux reformat a couple months ago it was running other than a known mouse problem which was fixed with a community patch. It at least was playable. Now that I have reinstalled it it is totaly unplayable in Gnome. I mouse click to move and the character moves a few seconds later rendering the game totaly unplayable. Its a bit better in Xfce but I think its a network problem rather than a game issue as even with less background ram used the problem is still there. 

 Makes me wonder is there is something heavy running in the background like a server as my computer is over double the min requirments of this game.

---

### Post by Omnios on 2005-07-18
Um an interesting thought about celeron processors with gamming. I dont have a celeron processor so I can not test this out but it may be possible to improve game performance by using Ice or Xfce to launch games. These Desktops have a smaller ram processor signature and could in theary improve game performance somewhat though I can not check this out due to lack of a celeron computer.

Cheers

---

### Post by Omnios on 2005-07-21
When I fist installed Ubuntu 5.04 it seemed to run a lot smoother than it has been running now with a lot of higher end games just bearly working. With kernal changes and installing a lot of programs from synaptic to check them out some games whent from barely playable to unplayable. Originaly I thought it had to do with the Nvidia drivers as most of the games seemed ok in Win XP and a bit choppy in Linux. By comparisen when I first installed Never Winter Nights after many months ago it perfomed better online than when run In XP less jittery. 

 This thread was originaly made to adress a ram usage issue pertaining to ram intensive games and found that ram usage can dramaticaly affect game play which may have to do with bottlenecking effecting overall performace. On day I looked into what was using a lot of resources and found clam anti virus was using huge amounts of ram and ininstalled it which nearly cut ram usage in half. Also we are talking about actual ram usage not cach here. Anyways I logged into Never Winter Nites and shure anouph the game is almost playable now with a few cut outs which leads me to believe there is another app running taking up ram and processor power while I am trying to play this game.

 Not 100% shure but I may have memory leakes but this sounds more like a program periodicly running using up ram and processor power such as a mail checker etc. Im going to try NWN in Xfce is getting rid of clam makes a big difference there. 

 From what I have seen so far low ram and processor usage makes a big difference so far and definatly can make a unplayable game playable but more inportantly it should make playing Quake type games much more playable and hopefully improve your gaming performace with smoother and less jittery performance. Lastly making your gaming experience more enjoyable.

---

### Post by Omnios on 2005-07-23
Did some more reading and found that as far as light lauchers Xfce is a memory hog thought it has gnome integration. Does anyone else know of a light wieght WM that is easy to set up and use for game launching. Had a hell of a time trying to config ICE.

---

### Post by Omnios on 2005-10-02
Excuse the editorrial lol.

 Xubuntu is in developement and hopefully will be done soon, from what I could make out is that Xubuntu will be available on sysnaaptic when it is ready hopefully available without lite software packages. This hopefully will allow for a easy to install and use lite windows sesion for launching and configuring games from within XFCE. I will not see how good it is as a light game launcher but anything that takes up small amounts of resaaurces is a big inprovement. 
Also I was using Never Winter nights to test the WMs but my install is currupt and  originaly was waiting till they fixed it then  later till 5.10 comes  out  (its 5CDs + the linux patches downloads + a 100 meg unpdate patch).

---

### Post by ygarl on 2005-10-03
I use Windowmaker and Fluxbox. Fluxbox is perhaps a bit lighter on resources as it comes in the box, so to speak.
Windowmaker and Fluxbox does NOT copy the Gnome/Kde menu items so I just scribbled down the name of my fave games and thier startup options and VOILA! - lightweight gaming machine!

Seems to work with everything *I* tried, but as always YMMV...

---

