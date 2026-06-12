---
title: "Dominions 2"
date: 2004-11-19
forum: Gaming &amp; Leisure
---

### Post by Perfect Storm on 2004-11-19
For all the Fantasy strategy freaks out there.
 
 Dominions2 works perfect in Ubuntu Linux (also tested it on Mandrake10). It runs both on Linux, mac and win and can be found here: [www.illwinter.com]("http://illwinter.com/")
 Dominions2 can be bought at [url="http://www.gamersfront.com/cgi-bin/store/category.cgi?item=45010&type=store"]Gamers Front
 [/url][url="http://illwinter.com/dom2/screenshots.html"]
 Screenshots of Dominions2[/url]
 
 Play single player or multiplayer with up to 17 players. There's special servers which you can test your godly skills. Normally there's around 100 multiplayer games running each day so you can easely find someone to play against.
 [url="http://illwinter.com/dom2/index.html"]
 More information about Dominions2[/url]
 
 
 Also the good news illwinter is making a Domionions3 :woot:
 
 
 
 Artificial Intelligence

---

### Post by TravisNewman on 2004-11-19
Hmm, looks like a mix between Warcraft and Risk. Interesting.

---

### Post by Perfect Storm on 2004-11-19
Oh, I forgot say that there's a demo of the game which can be found[ here]("http://www.shrapnelgames.com/Illwinter/d2/6.htm")  (limitation only 40 turns and limited spell reseach tree)
 
 Another thing is that Dominions2 is moddable, like : making your own race, spells, units, weapons, maps etc. It's very easy, I'm working on a mod which give you the abilities to play Draconian race (Dragon humanoids) 
 [img]http://thilockdominus.freehomepage.com/images/lofd.jpg[/img]

---

### Post by franx on 2004-11-19
Guys, once I download the demo, where do I decompress the files to?  Thanks for any help.

---

### Post by Perfect Storm on 2004-11-20
Just decompress where you want to (eg: /home/<your place>/dom2)

---

### Post by Perfect Storm on 2004-11-22
**How to install Dominions2 from the CD:**
 
 Open Terminal.
 
 ```

 cd /media/cdrom
 sudo sh unix_install 
```
 
 The terminal change so it says:
 
 > 
 Dominions II install script
 linux-gnu i386
 ---
 Select installation type
 1 Global Installation (require root priviledges)
 2 Local Installation (to ~/dominions2)
  
 _Choose 1_ - if you want so all the users on your computer can play Dom2 (a folder will be created at every users where personal configurations and alike will be saved, first when the user(s) start the game from their domain (/home/<username>/dominions2)). The  important files will be saved at /usr/local/games/dominions2 and the executable file will be saved in /usr/local/bin.
 
 _Choose 2_ - All the files will be saved in /home/<your username>/dominions2.
  
 
 Done. Now you can start Dominions2 by writing dom2 in the terminal or the 'run application' function.
 
 Enjoy.
 
 
 
 
 _**Howto update Dominions2**_
 
 Grab the latest patch [here ]("http://www.shrapnelgames.com/Illwinter/d2/6.htm")
 
 Extract the files.
 
 Open Terminal.
 
 ```

 cd <where you extracted the files>
 sudo cp dom2 /usr/local/bin
 
```
 
 The next thing is to move all the files including the dom2 file (that's why copying in the first place) to /usr/local/games/dominions2
 
 ```
 sudo mv dom2 /usr/local/games/dominions2
 sudo mv army9.trs /usr/local/games/dominions2
 
```
 
 When you're done moving the files, type dom2 and you're running the latest Dominions2 :)

---

### Post by Perfect Storm on 2004-12-29
New Patch is out!!!

Patch 2.15

> 
New Features / Game Balance Changes v2.15:

This seventh patch for Dominions II encompasses new features, game balance changes and bug fixes, plus the Oceana Mod, This version is fully compatible with version 2.12 to 2.14. However players participating in multiplayer games should still use the same version as the host or the unfolding of battles will not be displayed correctly.  If a game uses the Oceania mod then everyone participating must install it. But if it is not enabled the game works as usual.

    * Support for the new Oceania mod that replaces Atlantis with the new Oceania nation that will appear in Dominions III.
    * New monster mod command: #reinvigoration, #siegebonus.
    * New weapon mod commands: #secondaryeffect, #secondaryeffectalways, #twohanded, #fire, #cold, #shock, #explspr.

	

    * Dispel can now be cast under water.
    * Utterdark has been slightly altered.
    *  Numbness castable UW.
    *  Voidlord has become headless.
    *  Smoking Mirror's jaguar shape, MR 5 -> MR 18.

Bug Fixes v2.15:

    * Two Dominions games could get the same temp directory, resulting in errors after a crash (cannot start Dominions again) or when running two games simultaneously.
    * Blood slave sacrifice (Abysia and Mictlan) could corrupt the amount of blood slaves that nation has.
    * Some network fixes.
    * Fixed bug concerning certain spells (e.g. Looming Hell) and sneaking commanders. This bug made the game crash when trying to view the resulting battle.
    * Fixed some typos.
    * Evening Star and the Shrapest Tooth didn't have correct stats.

	

    * Holy deep one now has magic leadership.
    * #nratt changed ATT instead of the nbr of attacks.
    * Thunder whip did not count as a magic weapon.
    * Blink, Rage, Mist of Deception and Lobsters could result in battle inconsistencies.
    * Stability improvement.
    * modding commands #secondarypath and #secondarylevel didn't work properly.
    * No more Theurg attacks during utterdark.
    * No more underwater wolves.
    * No more uw snowfalls.



---

### Post by Perfect Storm on 2005-01-02
Found this:

Command switches for Dominion2 very usefull, though some of the options can be found within Dominions2 gui option list.

-----------------------------------------------------------------------

-v  --version       Print version number and exit
-d                  Increase debug level
-g  --host          Generate new turn and exit
    --verify        Verify all 2h-files and exit (creates .chk files)
    --statfile      Create a player info file after each turn (stats.txt)
    --scoredump     Create a score file after each turn (scores.html)
    --finalhost     Generate new turn, send out final score msg and exit

******* Network Options *******
-C  --tcpclient     Connect to a Dominions multiplayer server
-S  --tcpserver     Start a Dominions multiplayer server
    --ipadr XXX     Use this IP-adr when connecting to server
    --port X        Use this port nbr
    --preexec CMD   Execute this command before each turn generation
    --postexec CMD  Execute this command after each turn generation
-t  --hosttime X Y  Host on day X (0=sunday) hour Y (0-23)
    --minutes X     Set host interval in minutes
-h  --hours X       Set host interval in hours
    --pauseday X    Stop timer on this day (0=sunday)
-q  --quickhost     Host as soon as all turns are done
-n  --nonationsel   No nation selection when resuming a network game
    --noclientstart Clients cannot start the game during Choose Participants
    --uploadtime X  Nbr of minutes before game is created. (default off)
    --closed X      Nation is closed X=nation number (0-16)
    --easyai X      Nation is ai controlled X=nation number (0-16)
    --normai X      Nation is ai controlled X=nation number (0-16)
    --hardai X      Nation is ai controlled X=nation number (0-16)
    --impai X       Nation is ai controlled X=nation number (0-16)

******* New Game Options *******
    --mapfile XXX   Filename of map. E.g. eye.map
    --research X    Research difficulty 0-3 (default 1)
    --hofsize X     Size of Hall of Fame 5-15 (default 10)
    --indepstr X    Strength of Independents 0-9 (default 3)
    --magicsites X  Magic site frequency 0-75 (default 40)
    --eventrarity X Random event rarity 1-2, 1=common 2=rare
    --totalvp X     Vic. points available in the world 0-25
    --capitalvp     One extra victory per capital
    --requiredvp X  Vic. points required for victory (default total/2)
    --vicprov X     Provinces required for victory
    --vicdom X      Dominion points required for victory
    --richness X    World richness 1-3 (default 2)
    --masterpass XX Master password. E.g. masterblaster
    --startprov X   Number of starting provinces (1-9)
    --renaming      Enable commander renaming
    --noscoregraphs Disable score graphs
    --nonationinfo  No info at all on other nations
-M  --enablemod XXX Enable mod XXX. E.g. hoburg.dm

******* Video Options *******
-w  --window        Run Dominions II in a window
-u  --fullscreen    Use the entire screen
    --bitplanes X   Try to use a color depth of X bits per pixel
    --gamma X       Set gamma function (brightness) 0.1 - 5.0 (default=1.0)
-T  --textonly      Use this with --tcpserver to get graphicless server
    --opacity X     Set gui opacity 0 - 100
-r  --res X Y       Set screen resolution / window size (default=800 600)
    --animback      Use animated backgrounds
-a  --noanimback    Don't use animated backgrounds
    --fade          Use fade effects
-f  --nofade        No fade effects
    --nopopups      No helpful popups
    --fps X         Maximum nbr of frames per second (default=50)
    --filtering X   Quality of OpenGL filtering 0-3 (default=2)
-x  --fastgrx       Faster graphics (use 3 times for best performance (-xxx))
-p  --perftest      Run a performance test and exit
    --badmouse      Inverts y-coords in windowed mode. Cures SDL bug on Mac OS X

******* Audio Options *******
-s  --nosound       No sound effects
-m  --nomusic       No music
    --musicvol X    Set music volume, 0-100
    --clickvol X    Set mouse click volume, 0-100
    --arts          Route sound through aRts (default) (Linux only)
-o  --oss           Use direct oss sound output (best quality) (Linux Only)
    --defsound      Use default sound device (Windows only)
    --directsound   Use direct sound  (Windows only)
    --waveout       Use waveout for sound  (Windows only)

---

### Post by HorstJENS on 2005-01-06
I found out that with those commands (in your home directory):

```
[INDENT]cd dominions2
ln -s /mnt/windowsharddisk/games/dom2/mods mods [/INDENT]
```

you can use your mod directory from your existing windows partition for playing dom2 under linux. 
I also found out that my dominions2 runs better under ubuntu than under win98 :-))

---

### Post by Perfect Storm on 2005-01-06
Nice, didn't knew that.

Have you checked the Dom2 forum board? I'm working at a new mod. It's not finish yet but it's based on Warhammer Wood Elves Army.

I made this banner for it 
[IMG]http://thilockdominus.freehomepage.com/images/fol.jpg[/IMG]  And I'm soon finishing the scripting.

---

### Post by HorstJENS on 2005-01-06
[QUOTE=Artificial Intelligence]Nice, didn't knew that.

Have you checked the Dom2 forum board? 
.[/QUOTE]

Yeah, i check the shrapnel boards several times each day. Have to update my Chu-ko-nu mod to the new 1.15 patch. Too bad there is no #castledefensebonus modding command yet..

---

### Post by Perfect Storm on 2005-01-06
Yep, I'm also missing that command. (would fit quiet well for Glade guards  8)  )

---

