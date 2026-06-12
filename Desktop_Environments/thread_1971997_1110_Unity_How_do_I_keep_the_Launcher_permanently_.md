---
title: "11:10: Unity: How do I keep the Launcher permanently displayed?"
date: 2012-05-03
forum: Desktop Environments
---

### Post by welshmike on 2012-05-03
I'm finding that I use the 11:10 Unity Launcher somewhat like I used to use the bottom panel of 10.10.
It is a little annoying that it pops out when the cursor is at the left hand edge of a window.
I'd like to have the Launcher permanently on the screen with application screens using only the rest of the screen.
Will anyone advise please?

[B]The solution was to install the CompizConfig Settings Manager (ccsm) application from the Software Center, run it from the Dash, in it under Desktop click and enable Ubuntu Unity Plugin, then in tab Behaviour - Hide Launcher - Never

Phew!!![/B] 	](*,)

**Arghh$$$  I just installed [COLOR="Orange"]_12.04_[/COLOR] on my wife's PC and guess what? [COLOR="Orange"]_[B]The default for the Launcher is to be permanently on the (left hand) side of the screen**._[/COLOR]:)[/B]

---

### Post by fholson on 2012-05-03
I used CCSM to try to make this change ( 1) never hide launcher)
and 2) reduce launcer icon size and 3) show icon for show desktop.
After checking these, I clicked close on ccsm and it closed but the changes
did not take affect.  Is there a "do it now" button or maybe the equivalent of sudo or something I'm missing?  

I'm using Unity-2d ( I think, how do I check)
with newly installed Ubuntu 12.04.  BTW I tried making change 1 and 2
another way (from getting started stuff I think) that also did not work
tho I may have set to hide launcher there but could not disable it again.

FRed

---

### Post by welshmike on 2012-05-03
I did (1) and (2) but not yet (3). So thanks for the prompt I will do that now. **Errm? but how?**

---

### Post by fholson on 2012-05-03
Further down on the "Experimental" page is an option to
"Show Desktop Icon in Launcher" ...  I still have not gotten
changes to take effect.  Fred

---

### Post by welshmike on 2012-05-03
> **fholson said:**
> Further down on the "Experimental" page is an option to
"Show Desktop Icon in Launcher" ...  I still have not gotten
changes to take effect.  Fred

I am running 11.10 here and there is no such option. See this screenshot:
[IMG]http://www.winchesternw.org.uk/compiz.png[/IMG]

---

### Post by Starfleet on 2012-05-03
My own experience with ccsm is that it often doesn't work well with Unity and it's launcher, and can often screw up your grahics. I've noticed this on several computers. I've moved on to 12.04LTS and ccsm screwed up my Unity desktop a treat, like it did 11.10. But in 12.04 I've found the controls for altering the size of the launcher and icons, and if to display the launcher or hide it, and the sensitivity of the action needed to display a hidden launcher by right clicking the desktop. It's all there.

---

### Post by fholson on 2012-05-03
Mike: Yes, in CCSM in Ununtu 12.04 -- Ubuntu Unity Plugin        
/ Experimental there are a lot more items 26).  

Starfleet: Thanks for sharing your experience with CCSM. 

I tried the instructions in the 12.04 help app:
(Search for: Change the size of icons in the launcher )   
and they did not work for me either.       
I did not find the slider it describes!
                                          
I did get the launcher to stay revealed the I'm not sure 
how I did it.

---

### Post by fholson on 2012-05-04
I finally found some descent information about CCSM:                       
[http://wiki.compiz.org/CCSM](http://wiki.compiz.org/CCSM)                                                
     
I also found which version of CCSM I'm using: Version: 0.9.5.92
This is available in CCSM: >Preferences >About                                  
    
Also my CCSM is using GConf Configuration Backend.                
    
My hunch is that generally what CCSM actually does (in this case)
is modify gconf.xml files tho I have not found an example.   
Almost an example is the file:
~/.gconf/desktop/gnome/background/%gconf.xml
which contains info about the image I use for my desktop.
Not really an example since I do not see a way to set this with CCSM.

I like to be able to look at the basics and not just depend on gui
tools.  I wish there was a list of features and the corresponding file
and xml snippets for the options for that feature.  Anyone know of 
such a thing.  Some CCSM source code (or related) file must have such 
info tho I have not tracked it down.  Anyone know specifics?

Fred

---

### Post by zombifier25 on 2012-05-04
fholson, Look into ~/.gconf/apps/compiz-1

---

### Post by fholson on 2012-05-06
Zombifier25, thanks, some how I missed that. I found that:
~/.gconf/apps/compiz-1/plugins/unityshell/screen0/options/%gconf.xml
contains:             
    <entry name="icon_size" mtime="1336069141" type="int" value="32"/>
but my launcher icons seem to still be the default size (46 pixels I think).   

Fred

---

### Post by welshmike on 2012-05-08
I've just done a clean install of 12.04 and guess what the default is? The Launcher is permanently displayed. So the 12.04 developers realised the better default.:cool:

---

