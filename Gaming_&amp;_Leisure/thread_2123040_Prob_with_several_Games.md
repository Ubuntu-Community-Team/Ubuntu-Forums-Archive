---
title: "Prob with several Games"
date: 2013-03-06
forum: Gaming &amp; Leisure
---

### Post by 3dmatrix on 2013-03-06
I am very new to Gaming on Ubuntu and so I have listed the problems that I am facing with several games.

**Open Arena** :
Working fine

**Alien Arena** : 
No response

**Urban Terror** : 
Keyboard stops working, there is always a square box near the shooter's hand of about 3cm x 3cm in 800x600 resolution. Do not know how to play it in stand alone version.

**Counter Strike Condition Zero** :
How can we install it ?

**Quake** : 
Missing data; see /usr/share/doc/quake/README.Debian

**Quake 3 Arena** : 
Use game-data-packager to build and install the quake3-data package.
You will need these two files:

--------------- baseq3/pak0.pk3

From a Quake III Arena CD-ROM or installation

size: 479493658 bytes
md5sum: 1197ca3df1e65f3c380f8abc10ca43bf
sha1sum: 9d588ea65e92944d3e23eeb6ec08f1dd666f4658
sha256sum: 7ce8b3910620cd50a09e4f1100f426e8c6180f68895d589f80e6bd95af54bcae

--------------- linuxq3apoint-1.32b-3.x86.run

From any mirror of ftp.idsoftware.com, Gentoo or FreeBSD: for instance try
[http://www.filewatcher.com/m/linuxq3apoint-1.32b-3.x86.run.30923961.0.0.html](http://www.filewatcher.com/m/linuxq3apoint-1.32b-3.x86.run.30923961.0.0.html)

size: 30923961 bytes
md5sum: c71fdddccb20e8fc393d846e9c61d685
sha1sum: 802d84af0d515db50a496c4c55d1f1c4f40a9239
sha256sum: c36132c5556b35e01950f1e9c646235033a5130f87ad776ba2bc7becf4f4f186

If possible help

.

---

### Post by mastablasta on 2013-03-07
what are your system specs?

---

### Post by 1204 on 2013-03-07
Well quake games are commercial so you need original data files from disc (or if you have digital copy, take pk3-files from install folder). Counter Strike CZ: Install Steam and play, it's native linux: [http://store.steampowered.com/app/80/](http://store.steampowered.com/app/80/)

---

### Post by oldos2er on 2013-03-07
For Quake, I use darkplaces: [http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/)

---

### Post by 3dmatrix on 2013-03-07
Actually I am new to these terms  :)  what is this Dark places ? I am interested in Urban Terror but not able to ubderstand what is going wrong with it.

---

### Post by 1204 on 2013-03-08
> **3dmatrix said:**
> Actually I am new to these terms  :)  what is this Dark places ? I am interested in Urban Terror but not able to ubderstand what is going wrong with it.We are not wizards, please at least provide your system information: cpu, gpu, ram, ubuntu version, 64 or 32 bit, what urban terror version you have etc.

---

### Post by myromance123 on 2013-03-08
Do you have the _graphics drivers_ installed for your graphics card? Any time you have an issue with several games, it usually comes down to the graphics driver being at fault. If you just installed Ubuntu, and haven't done anything else then we can safely assume you are running off the Open Source graphics drivers. While these are great for some games, they are in no way up to par in terms of performance that the official drivers from AMD and Nvidia offer.

It's always best to make sure that first you have the right graphics drivers installed. Then we can delve deeper and trouble shoot the specific problems you have with each game. For Counter Strike Condition Zero, you will need to purchase the game from Steam. If you don't have Steam installed, you can get it for FREE from the Ubuntu Software Center. Can't find the Ubuntu Software Center? Just hit your Windows-key on your keyboard and search for "Software", and you'll find it :)

Not sure what your graphics card is? Open a Terminal and Enter this:
```
sudo lspci | grep -i vga
```

Below is a simple guide on installing the proprietary graphics drivers for your system, if you haven't done so. I make no assumption to what your hardware is, except that it is NOT Optimus or AMD Hybrid graphics. If you're using a laptop/notebook/netbook, then don't follow this guide just yet. Share with us your system information first.

[B]---------------------------
NOTE: before trying to install the drivers like below, please update Ubuntu and do the following to keep yourself safe from experiencing problems later on.

Open a Terminal and input this:
sudo apt-get install linux-headers-generic

Hit enter, and when it asks for your password just put it in and hit Enter again. It may ask [Y/n], just hit "y" and Enter again. Now you're ready to follow the below instructions.
---------------------------[/B]

In Ubuntu's Dash, search for System Settings. On the top right select the "Additional Drivers" tab.

If you're using an AMD/ATi card, make sure that you have fglrx-updates or I think it's now called post-release driver selected. Then hit Apply Changes and restart your computer.

If you're using an Nvidia card, make sure you have the 310 drivers selected (will be called experimental-310, you can try experimental-304 too). Then hit Apply Changes and restart your computer.

If you're using an Intel Integrated graphics card, then you shouldn't have to do anything. It should already be installed automatically.

Hopefully this helps you, but this might not be the issue you're having either. I personally use the Nvidia 310 experimental drivers, and can play all my games at 1080p with full settings.

If you could help list your graphics card Vendor Name and model that would be great (e.g Nvidia GTX 680 or AMD/ATi HD7970).

P.S: If you don't know how to find the Terminal, just open Ubuntu's Dash and search for 'Terminal' without the quotes.

---

### Post by 3dmatrix on 2013-03-08
> **1204 said:**
> We are not wizards, please at least provide your system information: cpu, gpu, ram, ubuntu version, 64 or 32 bit, what urban terror version you have etc.

I am sorry for my ignorance. I am just a normal Ubuntu 'user'. It would have been nice if you had given me some codes that I could enter to check all the specs and tell you. For example i was not able to figure out details of my GPU, till 'myromance123' told me those codes.

[B]Ubuntu 12.04 32 bit Gnome
CPU : Intel Pentium B950 2.1GHz x 2
RAM : 2 Gb
GPU : VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)[/B]

---

### Post by 3dmatrix on 2013-03-08
Thank you so much for the info. I have posted some details of my sys config in the earlier post.
Does that help or you would like to know more details of my system ?

---

### Post by 3dmatrix on 2013-03-08
I am able to run Urban Terror to some extent. I have attached some snapshots.
I am interested in playing in a stand alone version. Is it possible ? If so how ?
If I start server it seems i am the only one moving around in the system like a ghost  :) seems it is only for local network.
If i try to play on internet then i am not shown any list of servers.
But I would still like to play stand alone - if possible.
Any other suggestion ?

What about the other games that are not working ?

---

### Post by 1204 on 2013-03-09
Thanks, now it's bit easier. You should update Intel graphics driver and you'll get much better performance. Glasen repository gives latest intel drivers
```
sudo add-apt-repository ppa:glasen/intel-driver && sudo apt-get update && sudo apt-get upgrade
```

Then enable SNA acceleration, which gives nice fps boost
```
sudo gedit /etc/X11/xorg.conf
```
Then paste this and save
```
Section "Device"
 Identifier    "Card0"
 Driver    "intel"
 Option    "AccelMethod" "sna"
EndSection
```

---

### Post by 1204 on 2013-03-09
About other games, have you installed Steam? When you are registered you can add your Condition Zero serial key and install game [http://store.steampowered.com/about/](http://store.steampowered.com/about/)
> **3dmatrix said:**
> I am able to run Urban Terror to some extent. I have attached some snapshots.
I am interested in playing in a stand alone version. Is it possible ? If so how ?
If I start server it seems i am the only one moving around in the system like a ghost  :) seems it is only for local network.
If i try to play on internet then i am not shown any list of servers.
But I would still like to play stand alone - if possible.
Any other suggestion ?Urban Terror is multiplayer game so it's not possible to play single player game. You maybe can add bots when you play local network game. It's easier to play online and that server problem is maybe solved in this post [http://ubuntuforums.org/showthread.php?t=753017&p=5163038#post5163038](http://ubuntuforums.org/showthread.php?t=753017&p=5163038#post5163038)

---

### Post by myromance123 on 2013-03-09
Just some advice, since you're using an Intel Integrated graphics card it might be best to use Ubuntu 13.04 when it comes out.

I've been running Ubuntu 13.04 on my Intel 945GME (very low end old hardware), and it is so much better than Ubuntu 12.04 and 12.10. I can play Counter Strike, Half Life, Minecraft and Cubemen. Whereas when I tried with Ubuntu 12.10 and 12.04, I couldn't get Minecraft to even start.

This is before they've even added Mesa 9.1 (right now it's just Mesa 9.0.2). Definitely upgrade to Ubuntu 13.04 when you can, it's worth it from my personal experience.

---

### Post by 1204 on 2013-03-09
> **myromance123 said:**
> Just some advice, since you're using an Intel Integrated graphics card it might be best to use Ubuntu 13.04 when it comes out.

I've been running Ubuntu 13.04 on my Intel 945GME (very low end old hardware), and it is so much better than Ubuntu 12.04 and 12.10. I can play Counter Strike, Half Life, Minecraft and Cubemen. Whereas when I tried with Ubuntu 12.10 and 12.04, I couldn't get Minecraft to even start.

This is before they've even added Mesa 9.1 (right now it's just Mesa 9.0.2). Definitely upgrade to Ubuntu 13.04 when you can, it's worth it from my personal experience.But that Glasen Intel repository solves this problem and gives the latest drivers. Ubuntu 12.10 and 13.04 are kind of beta releases, so it may give bunch of other stability issues.

---

### Post by myromance123 on 2013-03-09
> But that Glasen Intel repository solves this problem and gives the latest drivers. Ubuntu 12.10 and 13.04 are kind of beta releases, so it may give bunch of other stability issues. 

I definitely agree, which is why I said change to Ubuntu 13.04 once it's released. Not right now :)

Adding PPA's can get messy, so if 3dmatrix later on doesn't want to have to use it I am just suggesting an alternative route (which is Ubuntu 13.04).

EDIT: Some additional information, I've been running Ubuntu 13.04 on two laptops at home for the past month. My HP DV3500 (2009 model) and my sister's Asus laptop (2011 model). Even with updates, I'm impressed. No crashes, or blackscreens. No compiz constantly crashing. The newest machine with Ubuntu 13.04 is the HP Mini I talked about. You can see me do a little stress test of it in this video:
[https://www.youtube.com/watch?v=n-_dq5XMOsE]("https://www.youtube.com/watch?v=n-_dq5XMOsE")

---

### Post by Irritant on 2013-03-09
One of your biggest problems is you're trying to run Opengl games on an integrated Intel graphics processor.  You really should consider investing in an Nvidia or ATI graphic card.

---

### Post by 1204 on 2013-03-09
> **myromance123 said:**
> I definitely agree, which is why I said change to Ubuntu 13.04 once it's released. Not right now :)Okay let's say both ways are good. :) Are you using SNA acceleration? Sna may be buggy sometimes, because it's under development (I haven't had any issues), but it's definitely faster. [http://www.phoronix.com/scan.php?page=article&item=intel_sna_july2012&num=2](http://www.phoronix.com/scan.php?page=article&item=intel_sna_july2012&num=2)

---

### Post by 3dmatrix on 2013-03-09
Can you tell me from where I could download 13.04 ?  :)
Just for trying !

Is this the link :  [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)   ?

---

### Post by Hajime Ryudo on 2013-03-09
Also same deal

---

### Post by 3dmatrix on 2013-03-09
Tried 13.04 as live CD but could not make out much difference in graphics.
Is there any way i could install the intel drivers from that cd ?

---

### Post by 1204 on 2013-03-10
> **3dmatrix said:**
> Tried 13.04 as live CD but could not make out much difference in graphics.
Is there any way i could install the intel drivers from that cd ?What's wrong with [glasen ppa]("http://ubuntuforums.org/showthread.php?t=2123040&page=2&p=12548961#post12548961")? I've used that for years on my laptop and no problems. Only faster and better.

---

### Post by 3dmatrix on 2013-03-10
Why is the Quake series and Alien Arena not working and how can I make it work ?

"[I]Quake :
Missing data; see /usr/share/doc/quake/README.Debian

Quake 3 Arena :
Use game-data-packager to build and install the quake3-data package.
You will need these two files:[/I]"

---

### Post by 1204 on 2013-03-11
Well why not Quake Live instead? It's free to play and better than quake/quake3 [http://www.quakelive.com/](http://www.quakelive.com/)

---

### Post by myromance123 on 2013-03-11
If you aren't seeing much difference in gaming performance with the current Ubuntu 13.04, you should see some improvements in the coming weeks once they include Mesa 9.1. I apologise if it's not what you were expecting.

As far as I know, you can't transfer the drivers from the CD. 

Some bad news regarding your Quake series game, I quote this:
>  This package contains no data files. To use it, you will need to either

install the commercial Quake data, or alternative free data files such as OpenQuartz.

This means you don't have the data files, which could be things like the maps or player models and sounds. Did you purchase Quake?

What is the problem you're getting with Alien Arena?
There's two ways I know of that allow you to install Alien Arena easily. They are the Ubuntu Software Center, or PlayDeb.

Checking the USC, it looks like it's updated to the latest Alien Arena. It should work.

---

### Post by 3dmatrix on 2013-03-11
> **myromance123 said:**
> If you aren't seeing much difference in gaming performance with the current Ubuntu 13.04, you should see some improvements in the coming weeks once they include Mesa 9.1. I apologise if it's not what you were expecting.

As far as I know, you can't transfer the drivers from the CD. 

Some bad news regarding your Quake series game, I quote this:


This means you don't have the data files, which could be things like the maps or player models and sounds. Did you purchase Quake?

What is the problem you're getting with Alien Arena?
There's two ways I know of that allow you to install Alien Arena easily. They are the Ubuntu Software Center, or PlayDeb.

Checking the USC, it looks like it's updated to the latest Alien Arena. It should work.

I did not run games on 13.04. I just tried 13.04 from Live CD. So can not comment on the gaming performance. I just felt that it could not solve the graphics related problems that I am facing in 12.04.

Alien Arena is already installed from the Ubuntu Repo but when I click on the link in the menu it just does not responds.

---

### Post by myromance123 on 2013-03-11
Alright, I went ahead and tested Alien Arena in Ubuntu 12.10.

It works. However, I read in the reviews that Ubuntu 12.04 may have permission problems. It's a simple fix, but before we jump to conclusions, let's run the game via Terminal.

Open any Terminal, and in it Enter this:
```
alien-arena
```

Please post any sort of errors you get from doing this. Hopefully this will shed some light on what the problem is being caused by.

---

### Post by 3dmatrix on 2013-03-11
I think you are right its a permission related prob :
[B][I]
alien-arena[/I][/B]
ln: failed to create symbolic link `/home/user/.config/alien-arena/data1': Permission denied
using /home/user/.config/alien-arena/arena for writing
Could not exec default.cfg
Could not exec config.cfg
Could not exec profile.cfg
Console initialized.
--------- [Loading Renderer] ---------
Master server at 69.136.224.226:27900
Sending shutdown to 69.136.224.226:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx

---

### Post by myromance123 on 2013-03-11
Alright, first go to your Home folder. In the Window manager at the top, click View -> Show Hidden Files.

Look for a folder called .config
Go inside it, and you should see a folder called alien-arena.

Now we are going to change it's permissions. Open a new Terminal. Type this in it:
```
sudo chmod -R 777 <the_alien_arena_file_goes_here>
```

Don't hit Enter yet! Drag the alien-arena folder into the Terminal and now it's ok to Hit Enter.
That should change the folder and all it's data files permissions to normal.

Example of when I do the command on my computer
```
sudo chmod -R 777 '/home/ismail/.config/alien-arena' 
```

---

### Post by 3dmatrix on 2013-03-13
Thanx it worked.
But can we play Alien Arena as stand alone game ?
I am not getting any server list.

---

### Post by myromance123 on 2013-03-13
> **3dmatrix said:**
> Thanx it worked.


Glad you got it working :)
> But can we play Alien Arena as stand alone game ?
Yes you can. Just click Single Player, and you'll jump into a game with bots.

---

### Post by 3dmatrix on 2013-03-13
> **myromance123 said:**
> Glad you got it working :)

Yes you can. Just click Single Player, and you'll jump into a game with bots.

Yes i tried that and i do jump in to a game but 'without anyone else there' I just move around like a ghost collecting weapons  :)

Can you kindly tell me if there is any security issue in online gaming ? If so what precautions we should take and how to choose a good and safe server ?

---

### Post by 1204 on 2013-03-14
Also [Enemy Territory (youtube)]("http://youtube.com/watch?v=om0D_s1SBCM") is nice game and works perfectly on your pc. [http://filebase.trackbase.net/et/full/et260b.x86_full.zip](http://filebase.trackbase.net/et/full/et260b.x86_full.zip)

---

### Post by myromance123 on 2013-03-14
> **3dmatrix said:**
> Yes i tried that and i do jump in to a game but 'without anyone else there' I just move around like a ghost collecting weapons  :)

Can you kindly tell me if there is any security issue in online gaming ? If so what precautions we should take and how to choose a good and safe server ?

That's very strange! I tested Alien Arena once more to see if I did anything differently, but I haven't. It should be, you click Singleplayer then choose a difficulty (I chose Easy) and it loads the map. Then you auto-spawn, and theres a 25 second time wait before the match starts. After that, it's go time and bots appear automatically. I honestly don't know why you have no bots, unless the version of Alien Arena in 12.04 is an older version. 

I have Alien Arena version 7.65 in Ubuntu 12.10 (you can see the game version in the USC under "More info"). I do have PlayDeb installed, _which might be why my version of Alien Arena is the **latest.**_

Here's the link to PlayDeb:
[http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)

Here's the link to Alien Arena on PlayDeb:
[http://www.playdeb.net/software/Alien%20Arena](http://www.playdeb.net/software/Alien%20Arena)

There should not be any sort of security issues when gaming online, I assure you it's very safe :)
Especially since you're playing from Ubuntu, which is a Linux distro.

---

### Post by 3dmatrix on 2013-03-14
> **myromance123 said:**
> That's very strange! I tested Alien Arena once more to see if I did anything differently, but I haven't. It should be, you click Singleplayer then choose a difficulty (I chose Easy) and it loads the map. Then you auto-spawn, and theres a 25 second time wait before the match starts. After that, it's go time and bots appear automatically. I honestly don't know why you have no bots, unless the version of Alien Arena in 12.04 is an older version. 


Yes it works exactly like that but there are no bots and also it is not able to display the list of servers for online play. Which port / service do i need to open in my firewall ?

---

### Post by myromance123 on 2013-03-14
> **3dmatrix said:**
> Yes it works exactly like that but there are no bots and also it is not able to display the list of servers for online play. Which port / service do i need to open in my firewall ?

If you're playing Singleplayer with bots, you don't need to open any ports. This is because you're playing a game locally, not through a router. There really should be bots automatically. Are you sure you have version 7.65 installed?

---

### Post by 3dmatrix on 2013-03-16
> **myromance123 said:**
> If you're playing Singleplayer with bots, you don't need to open any ports. This is because you're playing a game locally, not through a router. There really should be bots automatically. Are you sure you have version 7.65 installed?

I will check the version and inform you.
I know for single player we do not need to open ports but for online gaming ?

In Urban Terror it some times says Ping too high, what does that mean ? There is always a long list of servers how can we make out which server is better or the level of players ? How can i save a few server's links (favourites) and keep joining any of those servers instead of searching from the long list every time ?

---

### Post by myromance123 on 2013-03-16
> **3dmatrix said:**
> I know for single player we do not need to open ports but for online gaming ?
I've been playing Alien Arena for quite some time, but I've never had to open ports for online gaming. You should be fine without opening any ports.

The only time you'll really need to open a port, is when you want to host a dedicated server.

> In Urban Terror it some times says Ping too high, what does that mean ?
This means the server is too far away from you, and your connection to it is bad. You will lag if you join the game.

> There is always a long list of servers how can we make out which server is better or the level of players ?
The word "Ping" on the top right corner of the server list is clickable. Click it, and it will show you servers which have low ping. These servers are the ones you'll have the best connection on, hopefully with minimal lag.

> How can i save a few server's links (favourites) and keep joining any of those servers instead of searching from the long list every time ?
This is very easy. Highlight one of the servers in the list by clicking it once, then at the bottom there's a text that says "Add To Favourites". This will add that particular server to your favourites list.

Now, to join a server you've favourited there's another Text below that says Source: Internet. Click that until it says Source: Favourites. Now you should be able to see all your favourited servers.

I hope that helps a bit :)

---

### Post by 3dmatrix on 2013-03-16
Thats a nice explanation :) Thanx !
Do we have any good car racing or flight combat game for Ubuntu ?
Like Need For Speed ?

---

### Post by myromance123 on 2013-03-16
You're welcome :)

> Do we have any good car racing or flight combat game for Ubuntu ?

Nothing like Need For Speed, but there are quite a few racing games you can look into.

Speed Dreams: [Link]("http://www.speed-dreams.org/")
RC Mini Racers: [Link]("https://apps.ubuntu.com/cat/applications/decane-rcminiracers/")
Vdrift: [Link]("http://vdrift.net/")

I'm not sure about flight combat games. Last flight combat game I played was on PS1 :P

---

