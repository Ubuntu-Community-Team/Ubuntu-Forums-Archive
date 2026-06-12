---
title: "Screensaver hangs system"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Garyu on 2006-07-01
I am experiencing a strange problem with the screensavers in Dapper on one of my computers. It has been running Breezy for about 4-5 months without any issues, and now I have upgraded to Dapper. Suddenly, some of the screensavers will hang my system. I tried Ctrl-Alt-F1 and Ctrl-Alt-Backspace to bail out, but nothing works, everything just hangs completely.

I tried opening System-Settings-Screensaver, and the same freeze happens when previewing some of the screensavers. It seems it is the 3D ones that cause the problem, but not all of them. 3D-bubbles work fine, as does 4D-hypertorus. AntInspect seems to work, but Antspotlight hangs the system. 

In Breezy I was able to choose wich screensavers would be used by the random function, but that is not possible in Dapper for some reason. So now I just have it set to Blank screen, which works well enough and I guess that is all I need, but I can't help thinking that I should be able to make this work as it haven't been a problem in the past.

Dapper has identified my videocard (mobo integrated) as "S3 Unichrome Pro VGA Adapter". 

I searched the forum and found similar issues from Breezy and Hoary with ATI cards that lacks drivers, but I don't have an ATI card and also this is something that used to work fine in Breezy but stopped working in Dapper.

So, any suggestions on what I might try to solve this minor, neglectible, but somewhat frustrating problem? :)

---

### Post by cthornhill on 2006-07-02
Garyu,

I have what I think is the same issue. The new MB I installed also has integrated graphics (S3) and has the same freeze issue. I have not tried a screensaver that did not hang yet, but I will try a 2D one and see. I also did not have these issues in Breezy. I am pretty sure my ATI system has a problem after a while though some screensavers are no issue for me most of the time.

I am pretty sure this is a Gnome screensaver issue introduced in Dapper...and I think it needs to be fixed, but I had no replies either to my post. Maybe someone will notice this is a real bug and look at it for those of us with the problem. There is no simple 'don't use a screensaver or power saver' checkbox and I think that is an error in the interface (just my opinion). I agree it is a minor issue until it happens on a server and you can't find it so easily (remote systems). Actually I suspect this is part of the total QA issue I am seeing across the board with this release. They rushed it out, and here we are...I can only hope the support gets better - when the little things slide they indicate bigger issues under the covers. I would rather have fewer releases and less bugs, but that is just me.

---

### Post by cthornhill on 2006-07-02
Got a dupe in here - sorry

---

### Post by mrfelker on 2006-09-21
I have (indeed just had) the same hang on a screensaver in Ubuntu where the only way to exit is a cold boot.  I don't consider this to be trival however.
In this case I  was only in a  browser but if I was in the middle of composing a document in OpenOffice I'd probably have to go the extra  mile to   restore the file.  

My MB is ASUS AN8 SLI with a GeForce 7300GS card.  This freeze happened with earlier iterations of my system.

My CPU is a AMD 64 Single Core 3700.  I am using a RAID 5 configuration over       3 hard disks (actually the minimum  for RAID 5).  From the posts on these           issues  however the configuation is not the  problem - looks like the  kernel.

Marty

---

### Post by nazish on 2006-09-21
i have an ATI XPRESS 200 card and facing the same prob. I noticed this after I installed XGL and Compiz. I dont know why this occurs. But i have disabled screensaver. Waiting for a solution.

---

### Post by jimbob on 2006-09-21
Check out my post from earlier:

"I also have a system with the VIA S3 Unichrome display.

Check out these two links:

[http://www.ubuntuforums.org/showthre...ghlight=K8M800](http://www.ubuntuforums.org/showthre...ghlight=K8M800)
[http://www.ubuntuforums.org/showthre...ghlight=K8M800](http://www.ubuntuforums.org/showthre...ghlight=K8M800)

Everything is working OK on mine as far as it goes but no 3D stuff is available yet.

If you wade through all the forums the general consensus is that we will have to wait for newer drivers to be released.

Make sure you have xserver-xorg-via installed. Ubuntu has the latest available I believe.

I had to go through and delete four of the screensavers because they completely locked up my (actually my lady friend's) system by just selecting them: Flipscreen3D, AntSpotlight, Lattice and Matrixview.

She no longer sees these as selections."
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Matt Yun on 2006-09-21
See this bug report: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/31527](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/31527)

The problem is with the DRI (3d graphics) module implementation in the 2.6.15 kernel, and may not be limited to ATI cards.

I also had the same problem with an ATI Radeon 9200 on a new Dapper install.  Upgrading to the latest 2.6.15-27 kernel fixed the problem for me.

---

### Post by CatKiller on 2006-09-21
As cthornhill pointed out, the change between Hoary and Breezy that's caused you the problem is because of the change from xscreensaver to gnome-screensaver. There are many posts about it, and many posts giving instructions on how to change back, should you wish to.

The problem is that the xscreensaver hacks can request which graphics mode they want to display in, and if xscreensaver can't deliver it because of the graphics card, it just displays a blank screen. gnome-screensaver has no such mechanism, and so tries to load the screensaver anyway, which can cause the computer to crash. Similarly, there is no option in the GUI configuration to pick the list of screensavers that you want to use.

jimbob manually deleted the screensavers, which is quite an exreme solution, but functional. There is a different way to do it, however. If you open the Configuration Editor (gconf-editor) and navigate your way to apps/gnome-screensaver, you'll find a key called themes. This is a list of the screensavers that will be used. Remove them from this list, and they'll not be used. Unfortunately, if you open the gnome-screensaver configuration tool, this key will be reset, which in my case means that you get ugly screensavers, and in yours means that your computer crashes again. Also unfortunately, you won't know which screensavers will crash your computer just from the name.

Best of luck.

---

### Post by Tomy on 2006-09-21
> **jimbob said:**
>  ...

I had to go through and delete four of the screensavers because they completely locked up my (actually my lady friend's) system by just selecting them: Flipscreen3D, AntSpotlight, Lattice and Matrixview.

Thanks for info. 

I have been running with the screensaver set to 'blank' because I wasn't sure which ones would lock up my system.

---

### Post by CatKiller on 2006-09-21
You could try removing the **xscreensaver-gl**, **xscreensaver-gl-extra** and **rss-glx** packages through Synaptic. That should get rid of a bunch of 3D screensavers without having to hunt them down yourself - it seems that these packages also install gnome-screensaver themes.

---

### Post by shane2peru on 2006-09-27
Catkiller,

That is odd, because I have switched my screen saver to the xscreensaver, and am not using the gnome-screensaver.  I still have lockups.  If I use the GlSlideshow my system hangs to where I have to shut it off and restart it.  It won't respond to anything but the power button. ](*,)  I have a Toshiba laptop, and I don't know what drivers I have.  I would really like to use the Slideshow screen saver to rival with the XP system across the room.  That is a noble cause right? :D  

Shane

---

### Post by CatKiller on 2006-09-27
> **shane2peru said:**
> I have a Toshiba laptop, and I don't know what drivers I have.

My mum's got one of those. I hate it ;) I don't really know much about Linux graphics - I've only been using it for a little while myself, and managed to find out just enough to get 3D on one of my two monitors. The best bet is probably to find out what your laptop's graphics capabilities are, and then working out the best way to make use of them. The first step will probably involve reading through the manual or the Toshiba website to find out all the information that you can about the graphics, and then find reviews and posts on forums about what it can and can't do, and the second step might involve the installation of proprietary drivers. There are versions in the repositories, so you can install them with Synaptic. There are many posts on how to do this. I understand that the Ati drivers aren't as good as the Nvidia ones.

Depending on what you find out, either your graphics aren't sufficient to run that particular screensaver, or they are and your configuration needs some tweaking. The GLSlideshow documentation says this: "This program requires a good video card capable of supporting large textures." It could well be that the integrated graphics in your laptop just aren't up to the task.

Happy reading, and let us know when we can do more.

---

### Post by CatKiller on 2006-09-27
> **shane2peru said:**
> That is odd, because I have switched my screen saver to the xscreensaver, and am not using the gnome-screensaver.  I still have lockups.  If I use the GlSlideshow my system hangs to where I have to shut it off and restart it.  It won't respond to anything but the power button. ](*,)

As a quick note on this subject, it's the "Visual" flag on the Advanced Settings page of the GLSlideshow screensaver configuration that defines the type of display that it asks for. If this is set to GL, as I believe the default should be, then it will ask the X server for a display that can do GL. If it gets one, it will display, if not it will display a blank screen. For some reason, this screensaver may be being given a display that it shouldn't. You could check this flag, although I'm not sure in advance exactly what conclusions you could draw from what the setting is. It should be GL though, so change it to that if it isn't.

---

### Post by shane2peru on 2006-09-27
> As a quick note on this subject, it's the "Visual" flag on the Advanced Settings page of the GLSlideshow screensaver configuration that defines the type of display that it asks for. If this is set to GL, as I believe the default should be, then it will ask the X server for a display that can do GL.

That is set to GL, and the screen saver does work for a while, however after x time it just hangs, and no buttons work for it.  Here are my video specs according to [http://linux.toshiba-dme.co.jp/linux/eng/speclist.php3](http://linux.toshiba-dme.co.jp/linux/eng/speclist.php3) 

Display  	 15.0 XGA TFT 1024x768
Display controller 	Intel(R) 855GME
Video RAM 	16MB/64MB

However that doesn't mean much to me.  I'm pretty sure it worked in Breezy without a problem.  And the short 2 days I had Debian installed it worked without a problem.  So I know I can run it for extended periods (8 hours) without a lock up, but not in dapper!  :-k   Thanks for the help!

Shane

---

### Post by CatKiller on 2006-09-28
> **shane2peru said:**
> That is set to GL, and the screen saver does work for a while, however after x time it just hangs, and no buttons work for it.  

That's useful information. You've established that 3D stuff works with your configuration, and that the screensaver isn't fundamentally broken. This is progress.

So, a fairly critical question: when the computer crashes, how hot is it?

---

### Post by shane2peru on 2006-09-28
I don't think it is overheating.  I switched screen savers, and plan on letting it run all day and night.  I will let you know if it crashes.  I did run Breezy, and didn't have this problem though.  It lockes up with a picture on the screen as if the screen saver ran out of pictures (not possible).  Got me.

Shane

---

### Post by shane2peru on 2006-10-03
Ok, I have let my system run overnight, and all day with the screensaver running.  I have been using the one that tells the date and time and bounces all over.  It has not locked up once on me.  It appears to only be the screensaver that is using the pictures.  I have my pictures stored on a fat32 partition for sharing with XP.  I have a link from my home directory to that and just point to that link for the picture folder in the picture screen saver settings.  I don't think that would cause a problem, but I really don't know.  Thanks for the help!

Shane

---

### Post by SonicSteve on 2007-01-30
I may need to start my own thread but...

I have the exact same issue, the difference is I have an ATI radeonVE card (7000 series). Screensavers used to work but now if I even open the screensaver dialogue box the system hangs like bungee jumper. 

Just like you nothing works to get out of it, its hung and hung good. I have no idea how to troubleshoot this.

---

### Post by SonicSteve on 2007-01-30
I should say that when I open the box it doesn't always hang right away. Sometimes I get a few seconds before it happens. To combat this I disabled screensavers, then the system hung, I rebooted and check to see if the changes stuck, they did, and the system hung again because I had to open the screensaver dialogue box. 

Now I just don't touch it. Screensavers are eyecandy anyhow, we really don't need them. Not that I like leaving it broken but it seems I have little choice right now.

---

### Post by Garyu on 2007-01-31
Hey SonicSteve,

have you tried setting your video driver to "VESA"?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by SonicSteve on 2007-02-01
Thanks for the advice,
I actually got it working by following a guide that first crashed my graphics entirely. I then ran the simple tried and true;
sudo dpkg-reconfigure xserver-xorg

---

### Post by SonicSteve on 2007-02-01
> **Garyu said:**
> Hey SonicSteve,

have you tried setting your video driver to "VESA"?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I remember the term VESA but exactly what does it mean here. Is it a reduced 3d mode or if not then what?

---

### Post by Garyu on 2007-02-01
> **SonicSteve said:**
> I remember the term VESA but exactly what does it mean here. Is it a reduced 3d mode or if not then what?

VESA is a standard for video graphics. It is compatible with most graphics cards, but usually does not take advantage of advanced functions. As a general driver though, it usually makes things work fine since most hardware provide at least basic functionality with this driver.

You seem to be familiar with dpkg-reconfigure, but as a tip, if you use the option -p for priority and set it to high (-phigh) as I did in my previous example, you will only have to answer questions with high priority and other questions will be given default values. That way you don't have to answer every question. There are four modes, low, medium, high and critical - depending on how many questions you feel like answering.

---

### Post by SonicSteve on 2007-02-01
Thanks for the dpkg advice,
I'm still quite new to Ubuntu and Linux in General. I still have tons to learn but I'm feeling more and more comfortable with it.

---

### Post by racmar on 2007-06-22
This happens to me also.  I am using Beryl and the MatrixView screensaver.  I have noticed, that I can login to my machine via ssh and I see matrixview is stuck at 100% cpu.  Also, if I do ```
sudo killall matrixview
``` it does not work.  

I have to bring out the big guns with ```
sudo kill -s 9 `pgrep matrixview`
```

---

### Post by cgarre on 2008-05-19
Ok ! Here was my problem (and of course the solution) 
Whenever gnome-screensaver kicks in , it used to hang randomly, sometimes in 1 min, sometimes in 10 mins, sometimes it doesnt hang. As such i didnt know what to do, so i tried seeing if its a specific screensaver thats causing the hang (hang as in nothing works .. even the keyboard dies -i have to power down hardboot). I realized a few screen savers were more prone to hang, but then i was not able to rule out which ones were not causing hang .. finally i got tired and i moved to XscreenSaver (process given here [http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)) and yes from that time atleast it has been 10 hours and no hang as yet .. touch wood) !!! So move to Xscreensaver .. (I am using Gnome on Ubuntu 8.04 Hardy).

---

### Post by racmar on 2008-05-19
@cgarre:

Glad to know you're on the right track.  I've since upgraded from Gutsy to Hardy, and have not seen any Xserver lock-ups over several weeks.  Again, knock on wood.

---

### Post by Leo the Lion on 2008-05-21
I have the same problem with the screensaver hangs. On top of that, if I try to access screensavers through System>Preferences>Screensaver, the system reboots. I have Ubuntu 7.10 running on an HP pavilion dv2000. The graphics card is an Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller. Compiz works just fine.

---

### Post by racmar on 2008-05-21
@LEO,

Have you thought about upgrading to Hardy 8.04?  The *only* remaining problem I have with Hardy is FF3 is not compatible with Google's Toolbar.  But I understand you can still use FF2 somehow.

---

### Post by MC_LA on 2008-05-21
My screensaver hangs in hardy. When I access System>Preferences>Screensaver, the Screensaver window just hangs. There are also a lot of new land minds in Hardy, enter carefully! :-)

---

### Post by racmar on 2008-05-21
Right, I guess I should mention to make a backup if you do want to upgrade.  I have the same chipset ( 3 laptops ) and don't have any screensaver problems now.  But again, just my $0.02

---

### Post by Leo the Lion on 2008-05-21
> **racmar said:**
> @LEO,

Have you thought about upgrading to Hardy 8.04?  The *only* remaining problem I have with Hardy is FF3 is not compatible with Google's Toolbar.  But I understand you can still use FF2 somehow.

Like MC_LA stated, there is still some ironing needed for Hardy, so I'm just waiting. Right now, my computer is extremely stable with Gusty, apart from the screensaver problem, so I'm a bit reluctant to upgrade.

---

### Post by TheAmigo on 2008-06-20
For me (hardy, nVidia, compiz) I didn't have screensaver trouble with the default gnome-screensaver.

But in my desire to run [synergy]("http://synergy2.sourceforge.net/"), I switched from gnome-screensaver to xscreensaver.

Installing the xscreensaver extras too, then the locking started.  I've since started to narrow down which screensavers cause the problem.  Just viewing the screensaver preview causes the same problem.  My testing method is a bit tedious, but it works:  click on each screensaver and if it locks, write down the name (on paper), power off the machine, power back on, and start testing from the next one down.

So far, I found that these cause the problem for me:
 - Braid
 - IMSmap
 - Interaggregate
 - Mismunch

The GL screensavers run just fine, so it's not a 3D issue (for me anyway).  Not sure what these have in common.

Eventually, I'll make it through the rest of the screensaver and have a complete list... then I can uncheck them from the random list in xscreensaver and all will be good. (except that BlueProximity can't unlock xscreensaver)

---

### Post by chadjohnson on 2008-06-22
Here is my list of problem screensavers:
[LIST]
[*]xrayswarm
[*]imsmap
[*]interaggregate
[*]whirlwindwarp
[*]substrate
[*]braid
[*]vermiculate
[*]zoom
[/LIST]

You can remove these with
```

rm -rf `locate -i screensavername`

```

Be careful, though, as some other files on your system may contain in their file names the name of the screensaver you are removing.

---

### Post by iLoveRuby on 2008-07-17
I had the same problem, particularly with 4D Hypertorus.  Since I prefer a blank screen saver anyhow, I just deleted all the screen savers from within the shell.

Open a terminal and enter the following commands:

```
cd /usr/share/xscreensaver/
sudo rm -iv *
cd /usr/share/applications/screensavers/
sudo rm -iv *
```

Once you've done this, you should be able to select the blank screen saver without fear of things freezing.  And presumably you could download other screen savers and things won't freeze.  But since all I want is the blank screen saver, I haven't looked too deeply into why the certain screen savers are causing the freeze.

---

