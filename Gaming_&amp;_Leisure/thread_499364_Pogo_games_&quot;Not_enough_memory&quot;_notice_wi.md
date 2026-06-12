---
title: "Pogo games &quot;Not enough memory&quot; notice with Feisty/Firefox"
date: 2007-07-12
forum: Gaming &amp; Leisure
---

### Post by StarsAndBars14 on 2007-07-12
Is anyone else having this problem when trying to open games up on Pogo.com?  For the past few days I've been seeing those notices when trying to play *any* game other than "Jacks or Better".  

And for certain games, such as Jungle Gin, this issue has persisted for more than half a year.

Nothing seems to help it, not switching from Firefox to Epiphany or disabling core memory limits. 

My Java is at the most recent version available (1.6.0_01 as per installation instructions on java.com, upgraded from the 1.6.0 in Synaptic) and I have no other applications running at play time.  I clear the applet cache religiously too so I don't know what's going on.  

Is there any other way I can fix this problem?  Because if I don't, I'm about ready to start one of those online petitions for the people at Pogo Games to offer something more than half-assed n*x advice such as "Close any other applications you may have running."

(Okay, now the browser is crashing completely when I try to load a game up!! This is insane!)

(Edit #2:  There's obviously way enough free memory for Pogo to run, since I just on an idea typed "free -s 1" into an open terminal and as I was being taken into the game got this: )

> 
   shared    buffers     cached
Mem:        516148     505984      10164          0       7388     198552
-/+ buffers/cache:     300044     216104
Swap:      1012960      28856     984104

             total       used       free     shared    buffers     cached
Mem:        516148     507364       8784          0       7388     198552
-/+ buffers/cache:     301424     214724
Swap:      1012960      28856     984104

             total       used       free     shared    buffers     cached
Mem:        516148     507476       8672          0       7388     198556
-/+ buffers/cache:     301532     214616
Swap:      1012960      28856     984104

             total       used       free     shared    buffers     cached
Mem:        516148     507724       8424          0       7388     198560
-/+ buffers/cache:     301776     214372
Swap:      1012960      28856     984104

             total       used       free     shared    buffers     cached
Mem:        516148     507724       8424          0       7388     198564
-/+ buffers/cache:     301772     214376
Swap:      1012960      28856     984104

             total       used       free     shared    buffers     cached
Mem:        516148     507724       8424          0       7388     198564
-/+ buffers/cache:     301772     214376
Swap:      1012960      28856     984104


Help will, of course, be appreciated.

---

### Post by TrashmanL on 2007-08-15
Sorry that I won't be of assistance here, but I figure I'd add my problem to this thread rather than starting a new one. Every Pogo game I've tried has run fine on my computer, except one, Dice City Roller.

I have a 1.33 GHz AMD Athlon processor with a VIA Chipset
512 MB of RAM
Dual boot system Windows 98SE/Ubuntu 7.04 "Fiesty Fawn"
(I have also used a Dapper Drake Live CD)

I have no slow down issues in Windows. I was originally using the Dapper Drake CD with the Blackdown Java 1.4 plugin. When I'd try to play Dice City, actions would happen out of order and my computer would slow down tremendously while playing.

I have since upgraded to a full install of Fiesty Fawn and have almost the same problem. It no longer slows my entire computer down, I can perform other tasks just fine while playing, but the game itself is still giving my trouble. When I upgraded my java to 1.6.0, it looked like it might actually work. I was able to play the first round, all 3 rolls, without a problem, then when the auction screen came up, the problems came back. I've used Firefox, Seamonkey, and Opera, symptoms are identical in all 3. (I haven't yet tried a "No Auction" room... that possibility just occured to me... but I do like the auctions). I've cleared my Cache, I've tried increasing the available disk space to Java, and tried decreasing it too (neither seemed to have an effect, either positively or negatively). 

I'm seeing if anyone else has this problem and what kind of computer they're using if they do or don't have a problem. 

These are the questions I have in mind. I'm not thinking someone here can answer them, but here they are: Does Ubuntu just use up too many resources on my old computer? Or is the Java plugin for Ubuntu just not up to spec yet? Or is there a bug in Dice City Roller that only becomes apparent when using Linux?

---

### Post by TrashmanL on 2007-08-16
Hey, StarsandBars, I thought about your problem a little more, and I remember I had the same problem once, but in Windows. In Windows, my Java cache was too restricted. The same setting is also in Linux, so it might be the same problem. 

You've probably thought of this already, especially since you said you've cleared the applet cache, but just in case you overlooked it, go to your Java Plugin Control Panel, under the "General" tab click on "Temporary Files Settings" and under "Disk Space" there's a slider bar and number under "Set the amount of disk space for storing temporary files:" make sure that's not a real low number... make it something large.

The other thing I can think of is make sure you have the proper permissions set for the cache folder. Perhaps jacks or better is small enough that it stays in memory and doesn't need the disk cache, but everything else does and it can't write to it for some silly reason.

Just a couple ideas.

---

### Post by Pysco on 2007-12-30
My problem with the pogo site is that it tells me I am missing the required plug ins to play. I have java and everything else I need. It is all updated and it is all the most recent. The help page tells me nothing and everything I have tried has failed. When I go to view the plug ins  it tells me I need, there are none listed. 

I've read posts about pogo not working in Firefox, but I never had problems playing pogo while using Firefox on Windows, it's just with Ubuntu that I can't seem to get it to work. 

(I just finally got my mom to switch to Ubuntu and she has been bugging me to fix Pogo for her.)

Any help is appreciated.

---

### Post by elenigma on 2008-01-04
Hi , I just installed ubuntu gutsy,  for the fourth time!  I too am not able to play my favorite game on pogo,pogo bowl.  Just when I think I have everything covered and this time it will work , I go to pogo, load the game, no problem, go to pick up the ball, nothin! wont let me pick up the ball  or if it does there is a huge  delay  it is just impossable.,  Why so many installs you ask?? because being a newbe   to umbuntu and computers for that matter,  I mistakingly think I can fix this!  then I proceed to delete something vital and its back to the drawing board!  One thing leaves me puzzled about the notice of not enough memory,  believe me I havent got a clue what all of that was about, but I did notice what appeared to be other users?  and swapping something?  Is there a file sharing or memory sharing program installed and running on the umbutu system. I hope someone helps soon.  Need to bowl lol!

---

### Post by TrashmanL on 2008-01-24
Pysco,

Pogo (other than Dice City Roller) is working fine for me, using Firefox or even SeaMonkey. 

What version of Java did you install? What method did you use to install it? Have you checked your Java Control Panel to make sure the Firefox plugin is enabled?

---

### Post by TrashmanL on 2008-01-24
Ha! Just before I posted that, I upgraded my version of Seamonkey. After I posted, I went to Pogo.com and got the same error you got, Pysco! 

My Firefox has no problem, though, even after upgrading it multiple times. 

However, they work off the same plug-in structure, so try this.

Go to Help/About Plug-ins in Firefox

This should give you a list of your plugins. If java is not there, you don't have the plugin in the Firefox plugin directory. It may have been uninstalled on an upgrade of Firefox, or, may not be there if you installed Firefox after you installed Java for some reason. Or, maybe just a fluke. If it is there, you need to make sure Java enabled in your preferences.

If you know stuff about linux: Use su to go to your firefox plugin directory (mine is /usr/lib/firefox/plugins  ...  I think that's the default) and create a symbolic link to libjavaplugin.so
 
If you don't know stuff about linux: try uninstalling Java, then reinstalling Java. If that doesn't work, post on here again and I'll give you a step by step on how to do it (or, someone else might if I don't get to you in time). One problem will be, depending on your config and java version, it may be installed to a different place than mine, so it might get tricky.

---

### Post by TrashmanL on 2008-02-17
I don't know if anyone's even paying attention to this thread, but thought I'd give an update.

I got Dice City Roller to work (sort of)

It still doesn't work in the Native Firefox or Seamonkey I have installed, but strangely, since the last WINE update, it now works (abeit weirdly) using the WINDOZE version of Firefox in Ubuntu. (Before the WINE update, I got a Java error saying that Java couldn't communicate with the server on all Pogo games)

Dice City Roller is a very buggy game, i think. I don't think the issue is with any version of Linux, I think it's with the game. Even in Windows, I have the problem of the game trying to take over my other windows that are open on the screen and, sometimes, even the desktop. It makes it so that sometimes I have to click in weird places to get the game to react in another window, and often makes it unplayable even in Windows. This bug apparently just makes it freeze in Linux.

In a strange way, running it in WINE makes it a little bit more stable than it is even in native Windows. Instead of jumping from window to window, my WINE Desktop blanks (I haven't tried using it without the WINE Desktop yet... but I've noticed that, in general, most of my windows programs work better if I use the Desktop instead of trying to run them in their own window), leaving just the game itself on the screen. I don't even see the Firefox border, just the Dice City Roller game itself. I think there's some kind of compensation in Wine going on that stops what Windows otherwise lets it do, but leads to this other weird phenomenon.

Unfortunately, I seem unable to chat in the Pogo Chat box while I play. That's not a big deal to me, though, I just like being able to play. Though, If I try to hard to chat, Firefox crashes on me... so I learned not to do that.

So, if anyone else is having trouble with Pogo Games, try using Wine.

---

