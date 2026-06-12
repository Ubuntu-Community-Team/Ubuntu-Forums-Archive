---
title: "Alice in Wonderland chapter 2 ...noobie trys to game with Wine Nvidia"
date: 2006-09-04
forum: Gaming &amp; Leisure
---

### Post by roboghast on 2006-09-04
Alice in Wonderland Noobie travels in Ubuntu Chapter 2 “Let's Try Wine?” 

The noob speaks...

Hmm – I must game. I mean why have a computer unless you can have fun? 

OK So far I have tried to tried install about 3 games – the only one I got to Work is Wolfenstein ET – and that has such a slow frame rate it sucks -- a 3 second slide show. 

I don't know why. I have tried to figure out how to make my Nvidia 6800 ultra/GT work but after a week – puh! 

I have tried to find out how to install drivers – but the forums kinda stink at giving specific information that works. Seems that more time should have been put into proper English and communication skills at our public schools...

anyways. so I said to myself “I'll go to that IRC chat thingy” after all, its on the home page support – sounds good - my x server was all messed up from trying to install my nvidia drivers (wherever they are) so I used the LiveCD. 

opened the application found the server found the chat room – ugh. read the chat – hmm most of the chat is not about support... OK I'll ask my question. “trying to install nvidia drivers and I can't get back into my desktop – seems that the Xorg.config file is messed up? I am running LiveCD now is there anyway to fix that Xorg.config file? 

I got Crickets. (chirping in the background)

one guy eventually said I should mount my hard drive (since I wsa using LiveCD. 
tried – but like all easy-to-use- terminal commands if you don't know the +d uoga blah blah for the command you are screwed. It didn't work...

waited... waited... 

asked again for help 

*crickets* hmm says 700 people are on...? yea right, probably the freenode server...

figured out this wasn't going to help

OK leave IRC “support” – I figured out how to cut and past the backup file using nano all by myself. 

Ok next morning I decide – OK lets try WINE  W00T!! 
– maybe just maybe I can get some fun to run. YEA THATS IT LETS GO BACK TO WINDOWS  APPLICATIONS LOL 
yea I know its not windows, but since the LINUX game stuff farts-out lets try anything...

went to their website (and had an experience typical of Linux) [http://www.winehq.com/](http://www.winehq.com/)

Ok seems easy to download. here is the link to download the Ubuntu wine files...

hmm. why can't they just have a download button? hmm ok have to use that Synaptic Package Manager – oo fun – talk about cryptic searches for files your not sure will even run! 

OK I'll Play along!! 

says to cut and paste the deb thing and ADD it to the repositories –OK DONE 

reload....

hmm TYPICAL this URL doesn't say what specific file to GET!! lol 
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

“simply click reload and search for the package 'wine' for installation” Why is that word “SIMPLY” seem like a sick joke? The problem is this is ambiguous. what is the NAME?? what does it load where is it found?? how do I start it? 

ok this is the list that the Synaptic thing gave me..I had to do a search for “wine” btw something they didnt tell me to do to try to find the thing. So I searched the files...

These are the files the “wine” search came up with: KDE FTP client – WTF does this have to do with WINE? well its on the list...
“Video deinterlacer plugins from the DScaler project” what?? this isnt a WINE thing – doesn't even mention wine why does it show up in the menu search for WINE?? lol

another file on the list “Microsoft Windows Compatibility Layer (Dummy Package)” Well that is for me cause i'm a dummy – but its not the file the WINE HQ is talking about - 

another file listed “libwine-dev” that goes with the one above – hmm still no installer 

another file listed Tellico says its “collection manager for books, videos, music” what the ***?? another miss for the search for WINE FILES? 

OK now we get to the files with wine in them on the list : WINE Microsoft Windows Compatibility Layer (Binary Emulator and Library) W00T!! Finally

but hmm doesnt say its an INSTALLER and since Wine HQ didnt give me the name of the specific file who knows if this is the right one? its unofficial too? could be some retard put it in the repository? and its going to mess up my system? who knows? 

lets see the other files.... “wine-dev” Microsoft Windows Compatibility Layer (Development files) what is that? read it... hmm what does DEV mean anyways? I dont want to develop anything I just want to play a cool game. 

last file on the list is “winefish” omg what is that?? read it... “Winefish is a GTK+ based LaTeX editor, which was forked from Bluefish.” oh well who knows? 

OK so I conclude!!! DOWNLOAD WINE!! Microsoft Windows Compatibility Layer (Binary Emulator and Library)!!! whatever it is

so I download it – it finishes downloading.... close the Synaptic thingy...

ok lets find the files – hmm nothing in the “applications”... nothing in the “places” menu... hmm nothing in the “system” menu... hmm.. nothing on my desktop -- sigh – ok lets file search 

oo found them! 11 files.... hmm what to do? click on some – they fart. nothing. some pretty png files... they just sit there...

NOTHING IN THE WINE FILES THAT SAYS “INSTALLER” or “INSTALL” lol

OK now what – oh lets look back on the Wine HQ website....I'm sure they will tell me what to do now :) 

hmmmm the download page doesn't say anything about where the file is where it starts yada yada – OK look for a different link!! 

lets see... oo “Getting help” link! that sounds like what I need!! wow lots of stuff here lets try the WINE FAQ – hmm....half of it is the usual balony – general questions that no one cares about... OK here we go 

**“Installing and Configuring Wine”** --ok cool! 
FIRST QUESTION
[B]“5.1. How do I compile the Wine distribution source code?
See the README ([http://source.winehq.org/source/README](http://source.winehq.org/source/README)) for instructions. Additionally, you may want to set the TMPDIR environment variable TMPDIR=~/tmp or TMPDIR=/tmp (if you are root). “[/B]

WHAT?? COMPILE? crap --i'm no programmer. OMG I got to go into terminal?? CAN”T ANYONE JUST MAKE AN INSTALL program???

scroll down FAQ.... look for somethin else...

OO here is something!!!
[B]6. About running Wine
6.1. How do I run an MS Windows program under Wine?
When invoking Wine, you must specify the entire path to the executable, or by file name only. For example to run Windows' solitaire, type any of the following: 
wine sol or wine sol.exe (using the search path to locate the file). 
wine c:\\windows\\sol.exe (using a DOS file name). 
wine /usr/windows/sol.exe (using a UNIX file name). 
wine "c:\windows\sol.exe" (using quoted DOS file name). 
The path of the file will also be added to the path when a full name is supplied on the command line. [/B]


WAIT!!! I dont want to run Windows, just WINE omg I got to go into the terminal again. I want to use this from the desktop??
holy cow, scrolling down it just refers me to more documents – man just to play a game I'm going to have to take WINE 101 and get a certification license – I just want to play a game!! 

well forget it – Wine looks too complicated. Too many variables to set up and that means too many mistakes – It looks like it will take me a week just to learn it – and I still don't have my Nvidia accelerated 3d stuff set up  - Thats another horrible story itself. 

Well I guess ill try something else. In the mean time, “Mines 2.14.3” anyone? I am pathetic.

love, 
roboghast

---

### Post by jISh on 2006-09-04
Hmm..
Open a terminal and type
sudo apt-get install nvidia-glx

Then:
sudo nano -w /etc/X11/xorg.conf #(dont miss that capital X)

Go to Device and change "nv" to "nvidia"
CTRL+O and enter to save, CTRL+X to quit

Reboot. nVidia card should work.

sudo apt-gt install wine

WINE is installed. Now tweaking games and things to run IS difficult usually when run through WINE. However if you can't get your Linux games to run with good performance you won't get the WINE games to. Try running your enemy territory again after reboot and see if it works!

EDIT: Sorry I had no patience to read your entire post. You did get WINE installed. There is no GUI for WINE though, unless you consider winecfg run from the terminal. Just try running a Windows EXE and you should have an option to run it in WINE.

---

### Post by kiwi_bloke on 2006-09-04
I know the feeling . . . maybe this howto [http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585) can help you. I followed the instructions and it worked for my Ubuntu 6.06. I could even install my Office 2000 Word, Excel and Powerpoint apps. (to maintain compatibility with school). Good luck.

---

### Post by Wally on 2006-09-04
I'm with you man, I've had mixed success with wine.  
A couple of problems I fixed:
-If you are getting rid of a proviously botched install, make sure you totally nuke any leftover folders.  I had a .wine in my root folder, how I managed to get it there in the first place is a mystery.
-Go to Apps> Sys Tools> Menu Editor, Add a New Menu called Wine, then on the right side add a new entry called Wine Configurator.  In the command box enter winecfg.  winecfg opens a window that lets you set up things like your fake drive structure (take the autodetect route) and determine which version of windows to associate with each installed game.
-Back to the Menu Editor.  Add another entry for Wine File Manager with the command winefile.  Winfile is an app that gives you a kinda sorta file browser inside your fake windows world.  From there you can open a CD and double click your setup.exe then cruise to the installed game's folder to double click on LEGORacer.exe

I've had some luck with Wolfenstein and Unreal.  I'd really like to get my Interstate '76 running though.  

Good luck dealing with the un-obvious.

---

