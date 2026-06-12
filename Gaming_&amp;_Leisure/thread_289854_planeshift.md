---
title: "planeshift"
date: 2006-10-31
forum: Gaming &amp; Leisure
---

### Post by haxer on 2006-10-31
Hello i recently detected an mmorpg named planeshift how to install it? please help looks really fun :)

---

### Post by FyreBrand on 2006-11-01
The main site and the forums have explicit instructions on installing the game.

Here is a basic rundown of how I installed the game:
1. Download the latest client

2. From the terminal in the directory of the binary installer: 
```
sudo chmod +x <installer version name>
sudo ./<installer version name>
```Make sure you run as sudo because it wants to install to /opt/planeshift and needs the permission to do so.

3. Answer the questions as the installer asks them.  One important part of the install is when it asks you if you want to set permissions.  If you answer no then it will install the game and only root and anyone in the games group can play it.  You don't want to run an application as root so you would need to add your user to the games group to play.  -OR- You can answer yes that you want to set permissions.  Then it will give you the option to define the owner and group.  You should use your name and groupname at this point.  Example: ```
<your user name>:<your group name>
``` Note that typically your user-name and group-name are the same.  Be sure to separate them with a colon.

4. Answer Yes when it asks you if it should make menu items for you.  This is important because there are 2 different executable commands for starting the game, running the updater, and running the config utility.  The menu items choose the appropriate bin files for you.  Of course you can run all of these from the terminal, but you will have to read about this on their site.

5. After the game is installed run the updater from the games menu.  Be patient because it takes a long time to think about what it's doing.  At least it does for me. So just get a cup of coffee or make a sandwich, but do let it update. This is important.

6. Finally run the Setup/Config utility.  This will let you tell it what resolution to run at and if it should run full-screen or windowed.  I prefer full screen, but whatever you like.  Don't adjust the other options unless you understand them and know what you're doing.

Here are some other tips about the game:
- They are a very nice community of players and developers/GM's but they have some rules and they enforce them.  So read the rules before you start.
- One rule is naming conventions.  Make your name a fantasy style RP name.  Don't use silly or vulgar names or it will be changed for you.
- They strongly encourage RP.  Talking out of character isn't really allowed.  If you are going to do this use the tell/whisper function so no one else can hear you.
- Register on their forums and introduce yourself.  They are pretty friendly.
- Have fun.  It's a fun game and the developers have done a good job.

**Just a reminder: Read their installation instructions. Really!**

---

### Post by ryanisablond on 2006-11-10
> **FyreBrand said:**
> 
**Just a reminder: Read their installation instructions. Really!**
Don't forget to take your own advice, friend. ;) The binary available for download needs the following before it can be executed:
```
chmod +x PlaneShift_CBV0.3.016.bin
```
Straight off of their website: [http://laanx.fragnetics.com/index.php?page=linux](http://laanx.fragnetics.com/index.php?page=linux).

---

### Post by FyreBrand on 2006-11-10
> **ryanisablond said:**
> Don't forget to take your own advice, friend. ;) The binary available for download needs the following before it can be executed:
```
chmod +x PlaneShift_CBV0.3.016.bin
```
Straight off of their website: [http://laanx.fragnetics.com/index.php?page=linux](http://laanx.fragnetics.com/index.php?page=linux).

Thank, *friend*, I updated the instructions.  I have had no problems installing the game.  Just to be clear that is a basic idea of the install.  That is why I said **read the site instructions first**.

---

### Post by MaximB on 2006-11-11
and one very important thing :
YOU MUST REGISTER AT THEIR OFFICIAL SITE TO LOG IN TO THE GAME !

---

