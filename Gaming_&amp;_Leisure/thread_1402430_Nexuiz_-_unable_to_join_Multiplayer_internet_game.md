---
title: "Nexuiz - unable to join Multiplayer internet game"
date: 2010-02-09
forum: Gaming &amp; Leisure
---

### Post by Original Brownster on 2010-02-09
Hi all,
I hope someone can help with this, I'm running ubuntu 9.10 x_64 version, geforce 8600GT card.
Installed nexuiz from the repo's and downloaded the map pack from the Nexuiz site.
I can play single player no probs, I can create a server and play against bots no problem but when I try and join any multiplayer internet game everything seems to be loading fine, the screen goes to the text console and I see it load everything like maps, wav sound files, sometimes it downloads a map if I don't have it, then the last info line at the bottom of the screen says 'downloading csprogs.dat' first it says 0% then after a few seconds says 100% and then nothing happens, meanwhile I can see the chat from within the game and the frags rolling up the screen, 

anyone got any ideas what I'm doing wrong? :confused:

Thanks,

---

### Post by tommcd on 2010-02-09
First, the downloading of maps that you do not have is normal. I get that all the time.
Now to your problem:
Try using the Nexuiz straight from the Alien Trap website. You can download it from here:
[http://alientrap.org/nexuiz/](http://alientrap.org/nexuiz/)
It is a pretty big download, about 800+MB. Download it to your /home directory.
Then right-click on the zip file you downloaded and choose "extract", or whatever it says. Or open a terminal and run:
```
 unzip nexuiz-252.zip 
```
Then open a terminal and cd (change directory) to the nexuiz directory that was created when you unzipped the nexuiz file that you downloaded:
```
cd Nexuiz
```
Or it may be named nexuiz with a lower-case n:
```
 cd nexuiz 
```
To start the game from the terminal, you will need to use one of the 64bit launchers since you are using 64bit Ubuntu. So just run:
```
./nexuiz-linux-x86_64-sdl
```
This should launch the game and get you into any multiplayer game. This is how I have always run Nexuiz. This way you can get the newest versions of nexuiz when they are released from the Alien Trap site without having to wait for the Ubuntu devs to add it to the Ubuntu repos.

Rationale for this:
I have just noticed that if I try to launch nexuiz by running:
```
./nexuiz-linux-sdl.sh 
```
then I get the same error message. The  nexuiz-linux-sdl.sh is a generic launcher that is supposed to run the game whether you are using 32bit or 64bit linux. But if I use the specific ./nexuiz-linux-686-sdl  for 32bit linux or the ./nexuiz-linux-x86_64-sdl for 64bit linux, then I don't get this problem. The nexuiz that you installed from the Ubuntu repos may be tring to run the generic nexuiz-linux-sdl.sh launcher. So you then get that error message. 

Note: Running Nexuiz this way will not conflict with the nexuiz you have installed from the Ubuntu repos.
Hope this helps. Write back with your results.

BTW, We both have the same nvidia graphics cards. The 8600GT will run nexuiz just fine!

BTW #2, Your profile says you are running 7.10 Gutsy. Please update your profile so everyone knows what version of K/X/Ubuntu you are running.

---

### Post by Original Brownster on 2010-02-09
Thanks for the help much appreciated. I downloaded the latest release from alientrap.org and installed it as you suggested. Tried running the nexuiz-linux-x86_64.sdl and same problem.
Tried removing the deb package and no difference. 
Tried running the .glx file and same thing. 

Each time it seems to load everything then just stops at the loading csprogs.dat line.

Should I check any other setting do you think? could it be because I'm on x_64 architecture?

---

### Post by tommcd on 2010-02-10
> **Original Brownster said:**
> Thanks for the help much appreciated. I downloaded the latest release from alientrap.org and installed it as you suggested. Tried running the nexuiz-linux-x86_64.sdl and same problem.
The way I suggested running nexuiz in my last post does not really install the game. The nexuiz package from Alien Trap is a stand-alone package that just runs from your /home directory by launching the 32bit or 64bit executable.
> **Original Brownster said:**
> 
Tried running the .glx file and same thing. 
Hmmm, that is the next thing that I would have suggested.
> **Original Brownster said:**
> 
Should I check any other setting do you think? could it be because I'm on x_64 architecture?
I don't know what else you could do at this point.
The problem is not 64bit linux (as far as I know anyway). Nexuiz includes executables for 32bit and 64bit linux. I can run nexuiz from my 64bit Slackware 13 with no problems. I use 32bit Ubuntu though, so I can't check this on a 64bit Ubuntu system.
I tried googling this issue. There is not much info about it that I could find. The only info I found was about compiling the development builds of nexuiz from svn that do not really apply here.

---

### Post by Original Brownster on 2010-02-10
Well thanks for your help, I'm at a loss what to try next.

---

### Post by ruslanix on 2012-10-26
I have the same problem.
Maybe someone find solution.
Please .....

---

