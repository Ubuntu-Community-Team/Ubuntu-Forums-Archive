---
title: "Mega Games Pack For WINE/Windows Games (Online Edition)"
date: 2011-10-25
forum: Gaming &amp; Leisure
---

### Post by GlennLChugg on 2011-10-25
[IMG]http://img692.imageshack.us/img692/91/splashns.jpg[/IMG]
Free Mega Games Pack (Online Edition)
Free MGP is now an online Repository of games you can download, the games are compatible with Windows and WINE/Linux.

[[IMG]http://img851.imageshack.us/img851/2441/mgpinstall.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/851/mgpinstall.jpg/") [[IMG]http://img15.imageshack.us/img15/6733/miniinstaller.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/15/miniinstaller.jpg/") [[IMG]http://img23.imageshack.us/img23/1667/mgplauncher.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/23/mgplauncher.jpg/")
.The screenshots are the installer, the MiniInstaller and the Launcher.

With the Custom Games installer and the Games Launcher to categorize, show screen shots, descriptions and a direct link to the homepage, you will be finding out about the games before you even start them. The Launcher makes it simple enough to find and run games that your 4 year old will be happy to use it.

All the games in this pack are Open Sourced or Freeware, this means you can share this disk with anyone legally. All of the games have been tested to work with Ubuntu Linux with WINE, Windows XP and Windows 7 x64 but should work fine for any Microsoft XP and above Operating System. Many of the games are low end, so any PC from all ages and graphics can run them, the few included that require a higher end system only take up a little amount of disk space so you can install every one of the games and ignore the ones that do not work, without them using any system resources.

All the games are created to be semi portable using LastOS very own Permanent Portable Games (ppGames) system, these will automatically sort shortcuts in to your start menu and if you need to re install they can be installed/stored on a separate drive and by using SetupS Control panel to re integrate the Shortcuts (terminal: wine "/home/$USER/.wine/drive_c/Program Files/SetupS.SendTo/SetupScp.exe") just pick the Preferences tab and tick ppGames then press 'Okay'. None of the games require uninstalling, if you no longer want a game on your PC, simply browse your HDD and delete the folder with the game inside.

To set the games to install to a separate drive to Windows, simply press the Options button and change the ppGames Drive letter. Please note that hiding items will un-check them if made visible again. The ssWPI installer has the power to detect games you already have installed and hide them from the installer.

If you install the Games Launcher you will be able to use it to view/find your games to pick one to play, the launcher also allows you to add games to a favorites category so you can quickly put all your favorite games into one easy to find place. The Games Launcher also includes Database Technology that will allow you to instantly start the Games Launcher without needing to scan your PC for new items, there is a "(Re)Scan Games" button on the Launcher context menu to preform this task. To add new games you must learn about SetupS Builder from Team LastOS

* You MUST have WINE 1.3.30+ installed for Free MGP to work in Linux *

Get the Latest WINE from WineHQ Downloads, to setup the PPA:
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

----------------

You have two options to begin installing the games, even tho the first option is shorter, it doesn't give you all the extras that Option 2 does (Desktop shortcut, SetupS tools, extra runtimes):-

Option 1:
Download the .zip version below and extract it to your desktop or home folder.
[http://www.lastos.org/team/Public/MGPs/Mega.Games.Pack.Installer.zip](http://www.lastos.org/team/Public/MGPs/Mega.Games.Pack.Installer.zip)

You can then run the 'Installer' by double clicking on 'ssWPI.exe'

Option 2:
Download The latest 'SetupS Sendto Suite' from the pinned thread in the link below:
[http://www.lastos.org/index.php?forums/setups.6/](http://www.lastos.org/index.php?forums/setups.6/)

Install SetupS by Double Clicking the 'SetupS.SendTo.Suite_v8.11.10.0_ssApp.exe' file in your '~/Downloads/' folder, this will install SetupS. You can read more about SetupS at [www.LastOS.org]("http://www.LastOS.org")

Then Download the .apz version below:
[http://www.lastos.org/team/Public/MGPs/Mega.Games.Pack.Installer_ppApp.apz](http://www.lastos.org/team/Public/MGPs/Mega.Games.Pack.Installer_ppApp.apz)
Double click 'Mega.Games.Pack.Installer_ppApp.apz' in your '~/Downloads/' and SetupS will install it and place a shortcut to 'Games Installer' on your desktop and in your menu.

if you do not wish to use the 'Installer' you can manually download a game from the Repository: ([http://www.lastos.org/team/LastOS/FreeMGP](http://www.lastos.org/team/LastOS/FreeMGP)) and SetupS 'SetupS Sendto Suite' can install them directly by double clicking on the downloaded .pgz games.

Extras: (This requires you have SetupS installed, '.apz' are like '.pgz' but for applications)
[http://www.lastos.org/team/Public/MGPs/Gamers.Runtimes_v2.0_ssApp.apz](http://www.lastos.org/team/Public/MGPs/Gamers.Runtimes_v2.0_ssApp.apz)
> Many games have required extras to be installed before they work, this is a collection of:
* OpenAL
* Fonts
* PhysX 9.10.514
* VC Redist 2005
* VC Redist 2008
* Kels Runtimes (For many games)
* Games for Windows LIVE 3.1 (Allows offline mode)
* XNA Framework 3.1 and 4.0
* Adobe Shockwave Player 11.6.1.629 Slim (only works in 32-bit browsers)
* Adobe Flash Player 11.0.1.152 ActiveX (32-bit) - for Internet Explorer browser
* Adobe Flash Player 11.0.1.152 Plugin (32-bit) - for Firefox and Opera browsers----------------

Once you have the installer on your OS your able to run it, pick games to install by browsing through the online repository.

* I recommend you install 'Games Launcher' *

Games Launcher:
You will find this in the 'Other' Category of the 'Games Installer', it will place a shortcut on the desktop and in the menu for 'Games Launcher', the 'Launcher' allows you to view the same information for the WINE/Windows games you've already installed from the 'Installer', but allows you to Launch them directly and with the StartWait Technology -

StartWait:
A tool I made that if a game crashes/stops or wont close it gives you an easy option to recover your desktop, simply pressing Ctrl + Break will close ANY game (Global Hotkey) and if the desktop resolution is detected as different to when the game was ran it'll switch it back to the original size again. It is also displayed in the System Tray (near the clock), for the times you've alt tabed out of a game and it wont go back in to it.

----------------

If you wish to backup the downloaded games, they are placed in '~/.wine/drive_c/windows/LastOS/mgprepository', You can either place them back there or place them in '~/.wine/drive_c/ppGamesInstalls'

You can place the whole lot on a USB/DVD/Folder and it will be portable to install/use in Windows or Linux:
/Mega.Games.Pack.Installer/(Put the installer here)
/ppGamesInstalls/(Put all the .pgz here)

So long as the 'ppGamesInstalls' folder is in a parent folder of 'Mega.Games.Pack.Installer' it will detect the '.pgz' (games) you include inside it. The screenshots and Descriptions are part of the .pgz so they do not need to be included. If you choose this method you must (Re)Scan the items if you add or remove any '.pgz' from the 'ppGamesInstalls' folder, we use a Database/Cache to speed up loading The installer and the Launcher.

When you install a '.pgz' they will install to '~/.wine/drive_c/ppGames', if you have more than Drive C: (winecfg or using Windows), then you can use the 'Games Installer' Option screen to change which drive the games will be installed to, this comes in handy for windows users who need to re-install their OS.

* (Re)Scanning when you make changes to your installed games or 'pgz' you include in a 'ppGamesInstalls' folder is the only way they will be shown/available from the 'Installer/Launcher' *

(Re)Scan is a Context Menu item in the 'Installer/Launcher'.

SetupS comes with the tools and help needed to make your own Games compatible to include in '/ppGamesInstalls', the tools is called 'ssEditor', SetupS will place a 'Fix_SetupS_Linux.bash' on your desktop when you install it, by making this script execuatble (Properties Context Menu in Nautilus), and running it, you will get 'Scripts/SetupS' and 'Scripts/ssEditor' in your Nautilus context menu. This will allow you to easily edit/make '.pgz'.

----------------

**Special Thanks to:**
[http://www.caiman.us/](http://www.caiman.us/)
[http://games.softpedia.com/](http://games.softpedia.com/)
[http://www.indiegames.com/](http://www.indiegames.com/)
[http://www.gametop.com/](http://www.gametop.com/)
[http://www.freegamepick.com/en/](http://www.freegamepick.com/en/)
[http://www.nowstat.com/](http://www.nowstat.com/)
[http://www.acid-play.com/](http://www.acid-play.com/)
[http://www.brothersoft.com/games/](http://www.brothersoft.com/games/)
[http://www.freewarefiles.com/category/games.php](http://www.freewarefiles.com/category/games.php)

For providing Download Links, Descriptions and Screenshots to many included games.

And of cause, the games creators/artists/testers for their passion and time making these games exist.

**304 Windows & WINE compatible games:**
```
5 Days A Stranger
6 Days A Sacrifice
7 Days A Skeptic
A - B - O - O
A Game About Bouncing
Absolute Survival
Aladdin Puzzle
Alex Kidd Is Back
Alien Breed
Alpha Six
An Untitled Story
Antz
Apprentice 1 Deluxe
Arkan Ball
Assault Cube
Attack Of The Groox 1
Aztec Challenge
Azteca
Babble
Ball Racer
BCs Quest
Beacon
Bernard n Hank
Blobs 2
Blocco
Bobble Dragons Adventure
Boulder Remake
Boulder Rocks! 3D
Bowling Evolution
Bowling PC
Boxes
Bridge Builder
Brix Quest
Bubbilistik
Bug Defender
Bunny Girl Must Die
Burning Sand
Byte Ality Tower Defense
Cake Queen
Cartoonix
Caterpillars- The Revenge
Cave Story
Caveman Craig
Cedric And The Revolution
Chaks Temple
Champ
Charma
Chromatron
Cosmoball
Cosmos Quest 1
Cosmos Quest 2
Cosmos Quest 3
Crack Attack
Crazy Birds
Crazy Lunch
Crazy Over Goo
Crillion GPI
Crimson Road
Cube Lines
Dart' M Up
Dead City
Deflektor X4
Deluxe Pacman
Desert Hawk
Destructivator
Digdug Aftershock
Dink Smallwood
Dizzy Yolk Folk Adventures
Dont Save The Princess
Doogleberry 2
DROD
Dung
DX Ball
Echoes
Egyptian Ball
Eldorado Puzzle
Extreme Racers
Fantastic Blood Boy
Fingers Malone
Fishie Fishie
Flash Tower Defense Games
Flip Out
Flip Side Divine
Floating Islands Game
Flock
Free Civilization
Free Solitaire 3D
Frozen Fruits
Games Launcher
Gelatin Joe
Gene Rally
Ghost Busters
GhostBusters 3D Back in Action
Ghouls N Ghosts Remix
Giddy 3
Glest 2
Gnome Garden Carnage
Go Cat
Gradle - Unison
Great Secrects Da Vinci
Grey Matter
Grid Wars
Guardian Of Paradise
Gunroar
h2o
Habitat For Horror
Halo Zero
Hangaroo
Highway Pursuit
HitBlock
Hornado
Hot Ninja Moon Moon
I - Mones - Dragon
Implausible Mission
Incinerate
J2O
Jet Set Willy 4
Jezzballix
JFK Reloaded
Jolly Lines
Jumper 1
Jumper 2
Jumper 3
Jumping Jackson
Jumpman
K Ball
Kaboodle
Karoshi 2
Karoshi Factory
King's Valley 2
Kiwi
Knock
Knytt
Kulkis 2
Lander Reloaded
Light Cycle 3D
Link Em Bamboo
Linx
Little Fighter 2
Little Machines Go Deeper
Logigun
Loopy Puzzle
Lost Labyrinth
Mahjong Champ
Maniac Mansion DeLuxe
Marble Insanity
Mario Forever - Block Party
Mario Games
Marker World
Meatboy
Mighty Jill Off
Millenipede
Miner 2049er Again
Missile Storm
Mono
Motoracing
Mr Blocko Super Tournament Edition
Mu Cade
Mubbly Tower
Muon
Mystery Of Unicorn Castle
N
Narbacular Drop
Natto Cat
Nelly Cootalot
NemeGraphe
Neo Sonic 3R
NES quest
Net Hack
Neverball
Ninjah
Nonosweeper
Notrium
Nuclear Motocross
Numpty Physics
Ocular Ink
Oh Mummy
Once In Space
Open Yahtzee
Organism
Out Of Order
P n P
Pandora
Pangic Plus
Paroxysm
Patrol Falcon
Pearl Hunter
Pekka Kana 2
Penguin Command
Penguin Vs Yeti
Pharaoh Puzzle
Pingus
Pipe Walker
Pix Pang
Plasma Pong
Plasmaworm
Pogo Sticker
Pointless 2
Poker TH
Pool'm Up
Principles Of Evil 1
Principles Of Evil 2
Pumpkinoid
Punishment 2
Push Push Penguin
Pushover
Quack Shoot
Quadrax 3
Quadrax 4
Quadrax 5
Quadrax 6
Quest For Yrolg
Racing Pitch
Rainbow Web 2
Rainy Day
Ray Hound
Reactor 9
Real Bowling
Real Dominoes
Return To Sector 9
Rhacp3
Rick Dangerous II
RIP3
Robbie Swifthand and the Orb of Mystery
Rollerway
Rollin
Rolling Madness 3D
Rom Check Fail
Route 960
Royal Solitaire
Run Or Be Mechanically Separated
Saut
Scorched 3D
Seven Minutes
Shining Force
Sky Battle
Sky Battle WW2
Skydiving Academy
Snake Slider
Snoopy
Soldat
Solitaire Isle
Sore Ghoulies
Soul Fu
Splatter Zombie
Spooky Castle
Squish
Stair Dismount
Stardrone
Steam Punk Rally
Stick Soldiers
Stopple
Stranded 2
Street Wise
Stunt Dirt Bike 2
Sumotori Dreams
Super Mario Blue Twilight DX
Super Mario Kart
Super Turtle Toss
Super Tux
Swarm
T2002
Techno Sylph
Temporal
The Goonies
The Lost Castle
The Spirit Engine
The Yore
This Game Is Wizard
Toribash
Tower Circle
Tower Of Goo Unlimited
Track Balls
Trash Killer 2
Travel Agency
Treasure Hunter Man
Trilby's Notes
Tripline
Truck Dismount
Turbopac
Ultimate Stunts
Uncertain
Under World 2
Underland
Updraft
Uplighter
Vacuum Magic
Vegetable Tactics
Venture Arctic
Virtual Silence
Warning Forever
Warzone2100
Wicked Defense
Word Hunt
Wordline
Worph
X Moto
Yahtzee 123
Yellow Shape
Yume Nikki
Z Doom
Zak 2
Zelda - Seeds of Darkness
Zenbondage
Zep's Dreamland
```If you reinstall your OS (or WINE) you may need to run 'ppGamesRegister' to place any registry information back on the new OS's registry, just download, extract and run the following to re-enable your ppGames Collection:
[http://www.lastos.org/team/Public/MGPs/ppGamesRegister.exe.zip](http://www.lastos.org/team/Public/MGPs/ppGamesRegister.exe.zip)

You can just reinstall the games again instead, but it takes a lot longer.

---

### Post by mastablasta on 2011-10-27
nice selection.
 
quite a few of these games have their linux version. it owuld be a shame to put them through wine and loose performance because of it.

---

### Post by GlennLChugg on 2011-10-27
Well it can also be used in Windows, but mostly I included them because it's easier to include the complete packages for the SetupS, than to start a validated Repository of Linux games. The ones that were on Ubuntu or PlayDeb are part of the [Linux MGP collection]("http://ubuntuforums.org/showthread.php?t=1858387") but any others are not included to install, of cause you can play any Linux game through the MGP if it's on the local system, but you'll have to supply your own screenshot for them (Double clicking the screen shot in Linux MGP).

---

### Post by GlennLChugg on 2011-10-30
If anyone has taken the time to test this please let me know (post a reply), I am still actively working on this one as it's used for more than just the games under windows, it also has an Application Repository, they work with WINE, but I've not spent time testing which ones work properly yet :)

---

### Post by PaulInBHC on 2011-10-30
I applaud your effort with this and the other version. I'll see if I can give it a look next weekend.

---

