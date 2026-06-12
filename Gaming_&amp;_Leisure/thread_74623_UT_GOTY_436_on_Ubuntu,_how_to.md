---
title: "UT GOTY 436 on Ubuntu, how to"
date: 2005-10-12
forum: Gaming &amp; Leisure
---

### Post by BLTicklemonster on 2005-10-12
I had problems getting UT to work in Ubuntu, so I figured I would post this in case anyone else had the same problems.

First, make sure you have your video drivers. I had problems aplenty getting my geForce2 (nvidia-glx) drivers working in Hoary, but it was simple in Breezy, just go to synaptic and find nVidia-glx (pay attention to where it says you must enable once installed!!!) and install it, and then reboot, if you see a splash screen on boot, you got it. 

Get this download: [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51) (actually, chose which one, depending on if you have ut or utgoty) I put it in my /home/myname/ to run it. Go ahead and put cd one in right now so it will be mounted. 

If you put the file anywhere other than /home/yourname/, the open terminal, and cd /tothedirectoryouputitin. (good practice: always put stuff in /home/you/ when you have to install them. delete them later. Terminal defaults to that directory, so it's easier that way)

Type 
```

sh unreal.tournament_436-multilanguage.goty.run 
```

and then install ut. 

Every time I have used this particular download, it puts ut in /home/bill/ut. If it doesn't read on:
[I]
Pay attention to what folder it installed in. I think it defaults to: /usr/local/games/ut/ at least it did for me every time I installed it.

Mind you, when it needs the second cd, it will ask you to mount it. You most likely will not be able to remove your first cd normally, so go to the desktop, find the icon for UTGOY cd1, right click it and press where it says eject. 

Put cd2 in, and wait for autodetect to bring up a window showing the cd's content, this will indicate that the cd is mounted, you can close this window, and proceed with installation of cd2.

Once everything is done, you should see, in the UT install screen at the bottom right hand side, a button that says play. Press it. Now if you get a message warning anything about playing as root, then cancel, and read on, because that is what was messing me up.

Thanks to seethru for this information:
If you had the problem I listed with playing as root, then open the terminal, and run this code:

cd /enter/games/directory/here
sudo chown -R yourusername utdirectory

In my case, it was cd /home/bill/games/ut then sudo chown -R bill /home/bill/games/ut and voila, I could now go to Places>Home>games>ut>System and double click on the ut-bin and wait for perhaps 2-3 minutes for ut to come up. Not sure why, but I don't mind. If I pay myself minimum wage for the time I wait, then I more than make up for not using windows, if you know what I mean!!![/I]

Now I'm no linux pro, heck I just installed it and started actually using it for the first time 5 days ago, so if you have any problems, I may not be able to answer them, but someone probably will come along with the answer.

Good luck and have fun. Oh, and drop by [www.theblacklegion.com](www.theblacklegion.com) and say hi, or come to our server 67.19.84.40 and frag with us a bit. We're a Zark Weapons server, so there's no telling what you may find there at any given time, as I'm usually testing new Zark weapons quite a bit there. (how about a rapid firing Redeemer with a sniper scope? It's a madhouse, a madhouse!!! lol)

---

### Post by xequence on 2005-11-02
Does it absolutly need a second CD? My UT: GOTY was only one CD and it works fully on windows.

---

### Post by BLTicklemonster on 2005-11-12
I'm pretty sure that you can install without having to use the second cd, but if you need it, you are just plain out of luck. Just uncheck st3c textures, if that option is available.

---

### Post by Mase on 2005-11-27
Ok well I got the ATI driver to install, gawd I don't know how I managed that one.....lol


But now when I go to install UT, it tells me that I don't have permission, and that I might need to be in Root.  So how do I be in root when installing UT?

Also, are other games able to be installed? Half Life 2? Ut2004? BF2? Quake 4?


Mase

---

### Post by Mase on 2005-11-30
knock knock...........



>  Wednesday Buffet: Newest Philly fan legend
  	
	
The highlight of Sunday afternoon's Eagles-Packers game did not involve Brett Favre, Mike McMahon, or the legend that is Samkon Gado.

 The real highlight of the contest actually came during a stoppage of play when a random fan came running on to the field. He wasn't streaking, he wasn't attacking a coach (hello, Tom Gamboa), and he wasn't stealing the ball and running with it to the opposite end zone (hello, Cincinnati freak).

No, this guy was paying tribute to the deceased.

Yes, Christopher Noteboom, dressed in typical Philadelphia Eagle fan attire (grey hooded sweatshirt, mischievous black snow cap, blue jeans), darted past security and took a knee at the center of Lincoln Financial's 100-yard pitch. Then, in one of the more bizarre moments of the weekend, the young man spread his mother's ashes all over the center of the field. Yep, mommy's ashes &#8212; all over Lincoln Financial Field. 


back to business, any news on how to install UT?  How do I be in Root?

---

### Post by BLTicklemonster on 2005-12-06
Holy cow, Mase, sorry dude.

Okay, get rid of the ut you just made (bah, delete the folder, I did)

Now get this installer instead (pick whichever you use, ut or utgoty, they are both patched 436) [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51) and save it in your /home/yourname/ directory, open the terminal (got the cd in the tray, right?)

and just type in 

sh unrealtournament_whatever one you downloaded.run (I usually just right click on a file, click on rename carefully highlight the entire name plus the extension and paste it in terminal after sh it's easier that way)

and it will not pull and shenannigans on you.

To play, open your home folder and then open the ut folder, and double click on the ut file that has the sh label on it. It loads slow, so be patient.

You can go to /home/mase/ut and (I guess you used mase, right?) (that's click Places>Home Folder) and press ctrl+H and then open the .loki folder, go to System, and you can edit your ini files there. 


I'll post on how to make a launcher on your desktop for it later..

I'll have full instructions on cache cleaning soon, too...

---

### Post by BLTicklemonster on 2005-12-07
Here's how to make a cache cleaner for UT. It takes the files that you download from servers from a temporary folder ( /.loki/ut/Cache) and puts them in the proper places where they belong according to extension, i.e. .utx, .uax, etc.


Go to synaptic package manager, download gawk (just a thingy that is used by cache cleaner. I would tell you exactly what gawk is and what it does, but it's so freaking technical it would make your head explode gelatinous material about the place, rendering your keyboard useless for replying "OMGOMGOMG1337" to this thread when you're done).

Open text editor, and copy and paste the following in to it:

```
#!/bin/bash
cd ~/.loki/ut/Cache || exit 1 # change this to your UT user dir
if [ -f cache.ini ] ; then
{
export utdir="/home/[COLOR="Red"]bill[/COLOR]/ut/" # change this to your main UT folder
gawk -F= ' 
utdir = "${utdir}"
function moveit(targ)
{
print "mv -v "$1".uxx" " " utdir targ substr($2, 1, length($2)-1) | "sh";
}
{
if(match($2,".unr")) moveit("Maps/");
else if(match($2,".utx")) moveit("Textures/");
else if(match($2,".uax")) moveit("Sounds/");
else if(match($2,".umx")) moveit("Music/");
else if(match($2,".u")) moveit("System/");
}
END { close("sh") }' cache.ini
rm *.uxx cache.ini
}
fi;
if [ -f $utdir"System/De.u" ]; then rm $utdir"System/De.u" ;fi  
if [ -f $utdir"System/de.u" ]; then rm $utdir"System/de.u" ;fi
# end script
```

Notice this: /home/[COLOR="Red"]bill[/COLOR]/ut/ . Change according to your personal set up.

Save in /home/you/ as utcleaner. Notice all the pretty colors that the text changed to? This means something important, but I am a total noob, so it's above my pay grade, therefore there's no telling what it means.

Open terminal, and type this:

```
chmod +x utcleaner
```

The file utcleaner is now executable.

To run it, from terminal, type

```
./utcleaner
```

Now to make things cooler, how about a desktop launcher?

Right click on the desktop, click create launcher, name it UTCleaner, go down to where it says command: and put ./utcleaner and check where it says run in terminal (I tried it without running in terminal, and for some reason all it does is delete uxx files, so click on run in terminal for sure). If you want an icon, go ahead and use one. [You can create custom icons, too, if you want to.](http://www.ubuntuforums.org/showthread.php?t=92393). Click OK. 

Now you can double click and clean all your .uxx files. 

Nifty, huh?

THANKS TO ~V~ AT UNREALADMINS.ORG (Who's motto is "There's no place like 127.0.0.1" ) FOR THIS.

---

### Post by BLTicklemonster on 2006-10-31
How to do it in edgy:

[http://ubuntuforums.org/showthread.php?p=1694247#post1694247](http://ubuntuforums.org/showthread.php?p=1694247#post1694247)

---

### Post by Frem on 2006-11-02
I've got the GOTY on one cd also. The installer demands the second CD no matter what I do, and there isn't an option to not install data files.

---

### Post by BLTicklemonster on 2006-11-02
Have you tried to see if it will install using the regular unreal tournament installer? I keep meaning to try that myself to see if it will work.


OMG, HEY DOWN THERE IN LAWERNCEVILLE!

*edit: two years later, it just dawned on me that there's an installer for just the one cd unreal tournament on that page, too.

---

### Post by Drezliok on 2006-11-03
I installed my UT and all of my mods for it through wine. Works like a charm. UT2k4 on the other hand I just got that installed Natively.

---

### Post by BLTicklemonster on 2006-11-03
Really? I checked it out and it worked great, no lag, etc, then I turned it off. Next time I tried to use it, I had this problem:

[http://bugs.winehq.org/show_bug.cgi?id=4391](http://bugs.winehq.org/show_bug.cgi?id=4391)

---

### Post by BLTicklemonster on 2006-11-05
A umod extrator:
[http://ut.abfackeln.com/asu.html?page=install](http://ut.abfackeln.com/asu.html?page=install)

---

### Post by alandiegoantonio on 2007-06-03
Hi, I'm having a problem with UT...

I installed everything like BLTicklemonster said, it worked perfectly (thanx a lot, btw ^^), played all the deathmatch matches then rebboted the laptop for random reasons.

I then launched again ut and there was no sound. What the hell?

I closed ut, tried some mp3 or anything outside of ut and it worked. I relaunched ut and again the game went well but no sound come out.

Can anyone help me? You know, it's not optimal to not hear ppl fragging you from behind ^^

also note I'm a n00b with linux, so be careful of that ^^
I have an ubuntu dapper installation with the KDE package applied later (so it's for most purpose a Kubuntu installation)

Thanx to all those who will help out
Thanx to BLTicklemonster to let me play the game I used to spend hours on when on Win ^^

---

### Post by Jiiprah on 2007-08-25
I installed UT99 with no problems until i started playing. When ever i run around the screen starts shaking. I'm running it in OpenGL and it won't let me change the driver settings. Is there a way to run as Direct 3D or use the UT software rendering?

Before, I ran UT in Wine using Direct 3D.

---

### Post by SharpShuta on 2007-08-26
I need some help with my UT i finished installing it with the 436 patch to istall now when i try to run it i get this error

Assertion failed:Bitmap.Load Fire(Filename)[File:..\..\Engine\Inc\UnEngineWin.h][Line :55]

History:


That's what it is and also i installed it on a laptop

---

### Post by Sera88 on 2007-12-02
Hi!
I have Unreal Tournament GOTY edition (2 CDs) purchased and I tried to install the game onto my Ubuntu Gutsy. I messed almost everything up (first I installed a package and then installed another package on top of that and then I aborted the installation although it was supposed to install still some time and so on... now when I try to run UT from Terminal it says "/usr/local/bin/ut: 29: Syntax error: Bad substitution") and I think the whole installation directory is now absolutely unfunctional.

So how do I uninstall the game? Can I just delete the installation directory? If the game shows in Synaptic, what's its name?

EDIT: Never mind, it's working now. I deleted the installation folder (/usr/local/games/ut) and reinstalled it and used ut-bin to launch the game. So it's solved.

---

### Post by Jiiprah on 2007-12-08
Here is a UT99 Icon that i made:

---

