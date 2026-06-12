---
title: "americas army 2.81 Help install"
date: 2007-06-11
forum: Gaming &amp; Leisure
---

### Post by brasilforce on 2007-06-11
I have downloaded the linux file americasarmy-lnxded-281.tar.bz2
size 2.1gb and last ununtu disto 7.04


i extract the tar.bz2 and the only file executable i have is a Server.bin at americas army System folder , I cant see any run file as reported in version 2.50 or 2.70 in another related game posts

what do i have do for install Americas army .2.81 in linux
(Not the w32 version whit wine)

Im very noob in linux but i test too many distros and ubunto for me the best one, GREAT JOB UBUNTO TEAM !!!

P.S 
Any help will be aperciated thank you all

---

### Post by hikaricore on 2007-06-11
Making nearly the same post twice is frowned upon.

You will not get help any quicker than if you had just waited on a possible response to your post in this thread:

[http://ubuntuforums.org/showthread.php?t=425997&page=4](http://ubuntuforums.org/showthread.php?t=425997&page=4)

In fact, repeat posting with likely cause you to be ignored or responded to in a similar manner as I have.

---

### Post by brasilforce on 2007-06-11
Thanks for the adivise i will try delete the another one

any way here is the files i got in System folder

user@user-desktop:~/Desktop/aops-lnxded-2.8.1$ dir
Animations  KarmaData  Logs  Maps  Sounds  StaticMeshes  System  Textures
user@user-desktop:~/Desktop/aops-lnxded-2.8.1$ cd Sytem
bash: cd: Sytem: Ficheiro ou directoria inexistente
user@user-desktop:~/Desktop/aops-lnxded-2.8.1$ cd System
user@user-desktop:~/Desktop/aops-lnxded-2.8.1/System$ dir
aa.sdk.key.data        CountryFlags.ini                npcaicc.decision.xml
aa.sdk.rsa.data        creditsarmy.txt                 NPCAICC.speech.xml
AdditionalCredits.txt  credits.txt                     overview.txt
AGP_AI.u               D3DDrv.int                      Packages.md5
AGP_Armory.u           DBAuth.u                        partners.ini
AGP_Characters.u       DBMBS.so                        pb
AGP_Effects.u          Default.ini                     PunkBusterEULA.rtf
AGP_Gameplay.u         DefUnrealEd.ini                 Save
AGP_Game.u             DefUser.ini                     server-bin
AGP.int                Descriptions                    server.ini
AGP_Interface.int      Distribution.ini                services.ini
AGP_Interface.u        Editor.int                      Setup.int
AGP_Inventory.u        Editor.u                        Skins.int
AGP_Objects.u          Engine.int                      SoftDrv.int
AGP_Script.u           Engine.u                        splash.bmp
AGP_Security.u         FanSites.ini                    sso.public.rsa.key
AGP.u                  Fire.u                          Startup.int
AGP_UI.u               FSTS.u                          tournament.ini
AGP_Utils.u            GamePlay.int                    tours.ini
AGP_Vehicles.int       GamePlay.u                      UnrealEd.int
AGP_Vehicles.u         Help.ini                        UnrealEd.u
ALAudio.int            IpDrv.int                       UPlaylists.ini
ArmyGameEULA.rtf       IpDrv.u                         User.ini
ArmyOpsGlossary.txt    KeyBindings.ini                 UTelnet.u
ArmyOpsReadMe.txt      libdbauth.so                    UWeb.int
BUGSUBMIT.url          libgmp.so                       Vehicles.int
Build.ini              Links.ini                       WeaponMods.ini
conf                   LipSincData                     Window.int
Config                 mbs.demo.server.public.rsa.key  WinDrv.int
Core.int               mbs.demo.server.rsa.key         XInterface.int
Core.u                 MBSFilters.ini                  XInterface.u
user@user-desktop:~/Desktop/aops-lnxded-2.8.1/System$

---

### Post by hikaricore on 2007-06-11
This is technically the _other one_.

I think you may have missed my point.

---

### Post by brasilforce on 2007-06-11
Thank you for answer me so fast but , im a noob who likes linux  a lot , so i still leanig how to use it

I igot the file from americas army page and link you give me is very old its about 2,60 and i know is a linux version 2,70 
But do you mean i can only run a server whit americasarmy-lnxded-281.tar.bz2 but not play the game ?

thanks for your help
 :)

---

### Post by noerrorsfound on 2007-06-11
2.6 was the last client released for Linux. Any versions after only have a server for Linux.

---

### Post by brasilforce on 2007-06-13
Thanks for answer my question noerrorsfound and hikaricore's ,
but i figure  that my self last , any way here how to run the server in linux

INSTALATION

Either initiate a SSH connection to the remote server or, if you're in front of it, open a terminal and type (as a normal user, running the server as root is not recommended):
CODE

$ wget [http://treefort.icculus.org/armyops/americasarmy-lnxded-281.tar.bz2](http://treefort.icculus.org/armyops/americasarmy-lnxded-281.tar.bz2)


Uncompress the archive by running the following command. A new directory called aops-lnxded-2.8.1 will be created:
CODE

$ bzip2 -cd americasarmy-lnxded-281.tar.bz2 | tar xf -


CD to the System directory inside the newly created one:
CODE

# cd aops-lnxded-2.8.1/System



CONFIGURATION

Here, you'll find the configuration file that holds the basic server settings that can safely be changed in order to have the server listed on the AA in-game browser. Most of them are self-explanatory so I won't explain them all. In the System directory, open the file server.ini in your favorite text editor and modify the following settings so it suits your needs and likings:

[Engine.GameReplicationInfo]
ServerName=Your Name for the Server
ShortServerName=YN-SRV
AdminName=Your name
AdminEmail=Your email

[Engine.AccessControl]
AdminPassword=Password used to connect to the server as an administrator
GamePassword=Password required to join the server
PlayerAdmin=Username of the player who will have admin abilities
PlayerAdmin=A second admin player. Add more lines for more admins

[IpDrv.GameSpyQR]
IP=Enter the external IP if your server has two or more interfaces

[DBAuth.DBAuth]
GameServerIP=Your external Internet IP again

Save the file

ACTIVATE PunkBuster

Change directory to System/pb and using a text editor, create the file pbsvgame.cfg. Then add the following line to it:

sv_punkbuster 1

START THE SERVER

Change directory back to System/ and run:
CODE

$ screen <press enter>
$ ./server-bin ServerType MapName -nohomedir ini=server.ini log=LogName


..where
ServerType can be GLOBAL or LAN
MapName can be any map name (Border.aao, HQ_Raid.aao etc)
LogName can be anything you want the log file to be named.

So, starting a server in Internet mode will be possible with the command:
CODE

$ ./server-bin GLOBAL Border.aao -nohomedir ini=server.ini log=aao.log


Congratulations, you now have a working AA server!

---

