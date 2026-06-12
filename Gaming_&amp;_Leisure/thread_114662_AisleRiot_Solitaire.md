---
title: "AisleRiot Solitaire"
date: 2006-01-09
forum: Gaming &amp; Leisure
---

### Post by txcrittr on 2006-01-09
I just loaded Ubuntu 5.10 a couple of days ago.  First Linux experience.  Today I was going thru the AileRiot list of games and in the middle of one of the games (I can't say which) AisleRiot shut down.  Now when I try to start the game it shows a tab on the application bar (at the bottom of hte screen) momnetairily and the mouse pointer turns into the "radar sweep" or stop watch then the tab in the app bar goes away the mouse pointer goes to normal and no AisleRiot appears.  Having just switched from windoze, I turned ths computer off, waited a couple of minutes and rebooted.  Still same situation.  Is AisleRiot prone to breaking?  How do I fix it?

---

### Post by DirtDawg on 2006-01-09
I think your aisleriot problem is rare. I found [another thread]("http://www.ubuntuforums.org/showthread.php?t=1144&highlight=solitaire") addressing a similar problem, but I don't understand it, maybe you will. 

If you're itching to play solitaire, I would recommend installing Pysol, which can be found in the repositories (synaptic package manager). 

If you want the problem fixed, sorry but I can't help. Hopefully someone who knows more than I do will see this. 

Good Luck and sorry for the only so-so help :???:

---

### Post by mcduck on 2006-01-09
you could try to reinstall or (completely) remove and reinstall aisleriot with synaptic. There may also be a hidden file storing aisleriot's settings under your home dir, and removing that might solve your problem too.

---

### Post by txcrittr on 2006-01-09
Thanks for the input.  I kind of think it may have something to do with permissions.  I found the other thread too - and found it thouroughly confusing.  But it did give me the idea to try opening AisleRiot in a terminal window.    " /usr/games/sol "  That gives the following error

ERROR: Unbound variable: droppable?

But when I prefix that command with SUDO  "  sudo /usr/games/sol "
I am asked for a password and upon  entering the appropriate response AisleRiot starts.  

Am i correct in thinking that permissions may be an issue?

More info.  After I played a couple of hands of several games in AisleRiot, the terminal console that I used to open AisleRiot has several occurences of the following error message.

I/O warning : failed to load external entity "/root/.gnome2/yelp-bookmarks.xbel"

(gnome-help:15217): Gtk-CRITICAL **: gtk_stock_lookup: assertion `stock_id != NULL' failed


The "gnome-help" reference # is different in each occurence.

Does this offer any clues?

---

### Post by leech on 2006-01-09
That's really odd, I don't even have a .gnome2/yelp-bookmarks.xbel file and it's working fine here, though I'm using the development release.

I'm guessing that there is a configuration problem somewhere in your gnome.  I would 'rm -r .gnome2' from the terminal, though this of course will reset all your gnome stuff to default, it could fix your problem.

Doesn't sound like a permissions issue, but a settings issue, since as runnng it under sudo is looking for the settings in /root/.gnome2/ rather than /home/<username>/.gnome2

Leech

---

### Post by txcrittr on 2006-01-09
Is there a "list" parameter for the rm function rather than -r (I assume "reset")?

rm -r .gnome2  seems like a pretty drastic response  - I think that yelp file refers to a webpage - when I click the Online Help button it takes me to a site which has yelp as the "last" directory  something like "http://ubuntucommunity.org/yelp". I don't think that's the exactly correct URL - just an example.  


Thanks

---

### Post by leech on 2006-01-09
To clarify, rm is remove and -r means recurisve.  So that will remove your .gnome2 folder.  The only settings that will be lost are any tweaks you've done to gnome (like panel applets you've added, or your wallpaper settings.)  

You can do an 'ls .gnome2' and it'll show you all the files and folders that are in the directory.

Leech

---

### Post by txcrittr on 2006-01-10
Ok 

I tried complete removal of gnome-games.  Shutdown the computer.  Install gnome-games.  

No change.

Tried "rm -r .gnome2" 

No change.  I can still start and play the game with sudo but not from the menu link nor thru  a terminal console without sudo.

"sudo /usr/games/sol"  works - but with the same error message as noted above when help is accessed.

"/usr/games/sol"  tries to start the app - but it just dies.  Same message as earlier too.

Now what?  Bugzilla?

---

### Post by leech on 2006-01-10
Check what aislerot says under gconf.  Could be just a bad gconf setting somewhere.  Mine is working fine, but I'm not sure no one else is having problems.

Leech

---

### Post by txcrittr on 2006-01-10
How do I do that?  gconf /usr/games/sol in a terminal console?

---

### Post by txcrittr on 2006-01-10
Ok  - I found the file actually 2 xml files 
/home/desktop/apps/aisleriot has one %gconf.xml file 
 Its  about 400 lines and 11.4K long and looks like some kind of history maybe.

/home/desktop/apps/aisleriot/rules has another %gconf.xml, pasted below. 

<?xml version="1.0"?>
<gconf>
        <entry name="Backbone" mtime="1136752764" schema="/schemas/apps/aisleriot/rules/Backbone"/>
        <entry name="Klondike" mtime="1136668095" schema="/schemas/apps/aisleriot/rules/Klondike"/>
</gconf>

---

### Post by leech on 2006-01-11
There is an easier way...  

Applications -> System Toos -> Configuration Editor.

(Can't remember, but I think this has changed in Dapper, but it should be there in Breezy.  Under Dapper you have to unhide it in the Alacarte Menu.)

Leech

---

### Post by txcrittr on 2006-01-11
Ok - found the AisleRiot files in config manager.   What am I looking for in the settings?

---

### Post by txcrittr on 2006-01-11
The thought just occured to me.  When I tried "rm -r .gnome2", I removed the /username/gnome2 directory,  NOT  /root/gnome2.  
Should I kill the root directory?

---

### Post by pannerrammer on 2006-01-12
My wif'es pc lost the ability to play "Aisleriot Solitaire" before xmas.
I read all the posts and can't get it back either. Spent ages, etc. I gave up. 
The next day she thanked me for fixing it.... 

"Freecell Patience" (a little further down) seems to be the same thing!

---

### Post by txcrittr on 2006-01-15
Finally found a fix!!!!,,,, In another post.  Looks like maybe a bug to me but I dunno.  

To recap the problem:
I could not Start Aisleriot from the Applications > Games menu 
I could not Start the program via a terminal console "  /usr/games/sol  "
I COULD Start Aiskeriot via a terminal console "  sudo /usr/games/sol  "
Tried COMPLETE Removal and reinstall - No effect.
Tried "  rm -r gnome2.conf - No effect.


***********       SOLUTION       **************************
Looked at Applications > System Tools > Configuration Editor, then went to 
Aps > Aisleriot.
The "game_file" field had   " elevator.scm  " 
I changed the "game_file" to "  klondike.scm  "

Now Aisleriot will launch from the Applications > Games menu

---

