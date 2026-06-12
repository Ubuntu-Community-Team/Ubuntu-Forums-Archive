---
title: "Scrabble for Ubuntu?"
date: 2007-01-12
forum: Gaming &amp; Leisure
---

### Post by atarileaf on 2007-01-12
Anyone know of a good Linux version of the boardgame Scrabble? I tried the one called Scrabble through Synaptic but its pretty bad. Are there others or am I stuck trying to get a Windows version working through wine?

---

### Post by Perfect Storm on 2007-01-13
ProScrabble - [http://logical-games.mcctm.com/scrabble.html](http://logical-games.mcctm.com/scrabble.html)

PyScrabble - [http://pyscrabble.sourceforge.net/](http://pyscrabble.sourceforge.net/)

---

### Post by wilki on 2007-01-26
> **atarileaf said:**
> Anyone know of a good Linux version of the boardgame Scrabble? I tried the one called Scrabble through Synaptic but its pretty bad. Are there others or am I stuck trying to get a Windows version working through wine?

Hi -there is a version called xscrabble which I think is quite good but not easy to install on Debian/Ubuntu.
Below are instructions:
I have tried various ways of getting this nice little game on Ubuntu.
It is available for various Linux distros in rpm format and it has also been ported for the MAC X.
There is no version though for Debian/Ubuntu that I can find.I submitted a request to Ubuntu asking them if they could come up with a version.
Meanwhile I tried the latest tarball version downloaded from   a Linux software site
but it did not install.
I tried using the 'alien' package to convert the rpm package to deb.With some rpm's the converison worked well enough to allow an install but the actual program failed.
I installed all the libXaw libraries (needed I believe to work the widgets) using the software installer package and libXaw8 from Ubuntu's download page (Ubuntu -- Package Download Selection)and tried all of the above again. I even tried adjusting the makefile according to the instructions written as Linux guru stuff on the web.  

Eventually I came across a tarball downloaded from Matt Chapman's web page the writer of the xscrabble program back in 1994.
Found at:
[http://www.belgarath.org/programs](http://www.belgarath.org/programs)

and this worked. You will note that this is version 1 and not the 2 series which I believe has been amended by someone else.
Once extracted using the archive roller-I just extracted to my Desktop -it extracts to a folder called xscrabble-the readme file in the extracted folder needs to be read!
If like me you are not a Linux guru it can at first glance be a bit intimidating but in actual fact is quite straightforward.

First change directory in your terminal program to where you extracted the tarball.In my case this was 
cd / home/ross/Desktop/xscrabble -note the capital D for Desktop.
then run
sudo xmkmf
make Makefiles
make

Once the build process was run I copied the three files OSPD3.gz, scrabble permutations and xscrabble.scores from the Desktop folder xscrabble to my home directory in a folder I  called xscrabble(different from the one on my desktop). As instructed in the readme file I renamed Xscrabble.ad to Xscrabble and I simply placed this in my home directory outwith the xscrabble folder that I had created.
During the build process two executable files are created in the src folder in the extracted folder-xscrabble- on your desktop. These are xscrab and xscrabble I copied these to folder
/usr/games -you will need to use sudo nautilus in the terminal command line to allow you to do this(gives nautilus super user rights). This puts the two executables in a directory contained in the $PATH variable .

The game works by typing xscrabble in the terminal command line.
You might see some warnings written about fonts when the program initiates but the program seems to work well enough and will do me until some wizard comes up with a tailor made for Debian/Ubuntu.

---

### Post by atarileaf on 2007-01-26
Thanks. For $10, I picked up the official Scrabble Complete, but its for Windows. I should research and see if it works well under wine.

---

### Post by disturbedite on 2007-02-12
i got scrabble complete (third edition) too.  from what i read around online, its the best scrabble game ever (when it works).  unfortunately, apparently the developers didn't do a very good job with it.  (its not very compatible with winxp either).

i haven't submitted the test data to the wineappdb yet  but i can tell you, for me at least, (on kubuntu feisty herd 3, i386, wine 0.9.30), it doesn't work well.  i haven't been able to get into actual gameplay cuz the game keeps freezing.  its apparently a normal occurence for the game to "freeze" during the intro, but if you keep pressing enter it "should" get you past there.  it does with wine most of the time.  it freezes for me randomly in the pre-game menus upon clicking.  that even occurs with all the special effects and audio turned off.

maybe you should try pyscrabble.  i grabbed the source, but i don't have any experience with python so basically i don't know what to do with it....

---

### Post by atarileaf on 2007-02-13
Yes I've been reading how badly this game works sometimes and I have it installed on XP. I did notice something though, at least in my case. I had installed the game and it worked fine. Sometime later I installed Zonealarm and after that, the game wouldn't load, just a blank screen. Once I uninstalled Zonealarm, Scrabble worked fine again. 

Not the best designed game I guess but my wife loves it. Hopefully it will work under wine some day soon and we won't have to worry about it.

---

### Post by disturbedite on 2007-02-13
yeah, the developers did a crappy job developing it, to put it nicely...  ;)

and i don't think they bothered to release a winxp patch either.

---

### Post by atarileaf on 2007-02-13
Same thing with one of my other favorite games - Virtual Pool 3. It gives me fits under XP, but great under 98. Hey, I should see if that works under wine!

---

### Post by cdevilrun on 2007-02-13
This works in Firefox under Ubuntu. I find it to be a fun way to Scrabble it up online.

[http://www.scrabulous.com/](http://www.scrabulous.com/)

---

### Post by disturbedite on 2007-02-13
> **cdevilrun said:**
> This works in Firefox under Ubuntu. I find it to be a fun way to Scrabble it up online.

[http://www.scrabulous.com/](http://www.scrabulous.com/)

interesting.  thanks for the heads up!  i'd give you a kudos if this forum had em like the kubuntu forums...

---

### Post by jake3988 on 2007-02-14
If you want a scrabble clone that's online to face real people... goto games.yahoo.com and click on LIterati.

Its IS scrabble... except for name, slightly different scoring, and more possible words (all it does is check against dictionary.com, even if its an acronym, if it has an entry, it accepts it).

---

### Post by sanderella on 2007-11-17
The Internet Scrabble Club. [www.isc.ro](www.isc.ro).

You need to download Wordbiz from ISC, and you need "Java 6 Runtime" - file attached below.

Download Wordbiz.jar to your desktop. Open and extract the files to a new folder in your Home Folder. Right click on Wordbiz jar and click on Open with Java 6 Runtime. You will get the ISC screen to log on and fill in your details, then you can start playing! :KS

---

### Post by KhaaL on 2007-11-17
Wow, im amazed noone has mentioned [http://www.betapet.com]("http://www.betapet.com") yet. It's very big in sweden, but they have a (not as big) english version too. They have rankings and a dictionary for computer words if thats your flavor. Oh, and it's in flash too!

---

### Post by DarkSim on 2007-11-17
There is quackle. They even have it set up in a .deb package.

[http://quackle.poslfit.com/](http://quackle.poslfit.com/)

---

### Post by hikaricore on 2007-11-17
> **DarkSim said:**
> There is quackle. They even have it set up in a .deb package.

[http://quackle.poslfit.com/](http://quackle.poslfit.com/)

That actually looks like a very nice and well-rounded scrabble program.

Nice find.

---

### Post by MichiganMan on 2007-11-29
> **DarkSim said:**
> There is quackle. They even have it set up in a .deb package.

[http://quackle.poslfit.com/](http://quackle.poslfit.com/)

Wow, I was really starting to despair, but this is, well, like he said above, a great find.  Thanks.  Got my mother on Ubuntu.  I had been bragging about the wealth of Linux software out there when she asked me if there was a scrabble game she could play locally.  This saved me.  I'm a bit surprised that this isn't in the repositories yet.

---

### Post by BigSilly on 2007-11-30
Hey, Quackle looks like a great program, but for some reason after installing it I can't find it anywhere. It's not in the games section, and I can't seem to find it in the filesystem at all. I've tried typing quackle into a terminal but it just says command not found. 

What did I do? :confused:

EDIT: Ah, I'm sorted. You type quacker, not quackle. Sorry for any confusion.

---

### Post by zealbert on 2008-04-07
I downloaded quackle, and it works well, but could anybody tell me how to display the bonus squares on the board? I did click on the icon that says "display bonus squares", but nothing happens.
Thanks!

---

### Post by EdGato on 2008-04-30
> **sanderella said:**
> The Internet Scrabble Club. [www.isc.ro](www.isc.ro).

You need to download Wordbiz from ISC, and you need "Java 6 Runtime" - file attached below.

Download Wordbiz.jar to your desktop. Open and extract the files to a new folder in your Home Folder. Right click on Wordbiz jar and click on Open with Java 6 Runtime. You will get the ISC screen to log on and fill in your details, then you can start playing! :KS

Hi. I'm stuck at the language selection screen. Pressing the Enter key or clicking OK doesn't work.

---

### Post by nbhat on 2008-08-27
I managed to compile and run after getting libxmu-dev and libxwa7. Thanks to instructions from wilki. But I was thinking it would be computer vs human. Looks like its a mutiplayer game ..

---

### Post by riger99 on 2009-10-24
> **KhaaL said:**
> ...but they have a (not as big) english version too...

No they don't.

---

### Post by atentik on 2010-05-06
Where does this game get installed. Can't find it in "Games"..

---

### Post by Fitch on 2011-03-19
Zealbert.

For the full info, go to:
[http://games.groups.yahoo.com/group/quackle/message/1935](http://games.groups.yahoo.com/group/quackle/message/1935)

You will have to have a board handy to put the bonus squares in the right place.

Atlentic:

Edit your applications menu (right click between "Applications" and "Places")
Go to "Games"  and add new item.
And remember it's Quacker, not Quackle

---

