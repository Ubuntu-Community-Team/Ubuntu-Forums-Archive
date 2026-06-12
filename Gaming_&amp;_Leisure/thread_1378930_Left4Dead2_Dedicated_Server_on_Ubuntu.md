---
title: "Left4Dead2 Dedicated Server on Ubuntu"
date: 2010-01-12
forum: Gaming &amp; Leisure
---

### Post by taofd on 2010-01-12
Due to the difficulty in finding any reliable or detailed explanation on how to set up a steam server AND configure it / administer it. I've decided to start this thread (hopefully in the right place).

I share with you my meager learnings in hope that others will pick up where I left off and share their abundant knowledge ;).

I'm an utter noob so this is probably not best practice and I will update this accordingly as other users share their input :). I have also tried to explain everything to the best of my knowledge so that other users can learn as I have.


[CENTER]**LET'S START!!**
-------------------------
[/CENTER]

download this utility from valve: **[http://storefront.steampowered.com/download/hldsupdatetool.bin](http://storefront.steampowered.com/download/hldsupdatetool.bin)**

located under: **[http://store.steampowered.com/about/](http://store.steampowered.com/about/)**

*Make sure you are already in your chosen directory before using this!*
> 
$wget [B][http://storefront.steampowered.com/download/hldsupdatetool.bin](http://storefront.steampowered.com/download/hldsupdatetool.bin)
[/B]I created a new directory under my home directory and dropped the utility into it. It seems other sources online have ranged in their recommendations... anywhere from dropping it under /var/steam to creating user accounts for each server. For simplicity's sake, I'm just putting it under my home dir.

[CENTER]-
[/CENTER]
 
Open up a terminal window and navigate to whichever directory you dropped **hldsupdatetool.bin**

> 
$chmod -x hldsupdatetool.bin
*Allows you to execute hldsupdatetool.bin*

> 
$./hldsupdatetool.bin
[I]
Runs hldsupdatetool.bin and installs steam[/I]

> 
$./steam
*Runs and updates steam*

Run steam and install **Left 4 Dead 2**

> 
$./steam -command update -game left4dead2 -dir ./
[I]
Steam will update/install left4dead2 within your current directory.[/I]

(if you are trying to install a different game, just type './steam -command update' and it should give you a list of arguments and games)

[B]
This may take a while depending on your Internet connection...[/B]:popcorn:
  

**To verify everything downloaded properly...**
> 
$./steam -command update -game left4dead2 -verify_all

You can create a server cfg file by going under <steam_dir>/left4dead2/left4dead2/cfg/ and creating a server.cfg file. I don't believe the cfg/ dir is created by default so go ahead and 

> 
mkdir <steam_dir>/left4dead2/left4dead2/cfg

This is what my server.cfg looks like.

*NOTE: I don't have a rcon_password set because I wouldn't know what to do with it... Where do I even go to connect?*

> 

// Server Name
hostname "<hostname>"

// Lan
sv_lan 1

// Disable Autokick
mp_disable_autokick 1

// Disallow cheats
sv_cheats 0

// Server Hint History??
//sv_clearhinthistory 0

// Enforce File Consistency
sv_consistency 1

// Allow Pause
sv_pausable 0

// Allow Voice
sv_voiceenable 1

// All-talk
sv_alltalk 0

// Region (0- east 1- west) (i think 3 is europe and 4 is australia?)
sv_region 1

//Set Difficulty
z_difficulty normal

//I believe this sets it to 4 player coop mode...
sv_gametypes "coop"


Okay, now that we have the server configured, let's go ahead and start it!

Start the server using srcds_run

> 
./srcds_run -port 27015 -game left4dead2 -maxplayers 4 -ip 129.210.131.56
Sources:


If anyone knows how to actually administer the server while it's running PLEASE LET ME KNOW and I'll add the information!

-----------------

[valve developer wiki (very useful)]("http://developer.valvesoftware.com/wiki/Command_Line_Options#hldsupdatetool_.28Windows.29.2C_Steam_.28Unix.29")

[http://www.arsgeek.com/2008/08/18/how-to-run-a-dedicated-steam-server-on-your-ubuntu-box-countestrike-style/](http://www.arsgeek.com/2008/08/18/how-to-run-a-dedicated-steam-server-on-your-ubuntu-box-countestrike-style/)

[http://jamespo.org.uk/wp/archives/862](http://jamespo.org.uk/wp/archives/862)

[http://forums.steampowered.com/forums/showthread.php?t=292495](http://forums.steampowered.com/forums/showthread.php?t=292495)

---

### Post by vandorjw on 2010-04-21
What are the minimum hardware requirements for hosting a server without too much lag?
Can it be done on a P3 with 256 MB RAM?

internet connection is fine, since it will just go on the local lan only.

I would do this in linux ofcourse.
NO GUI, and nothing else running.

---

### Post by dfreer on 2010-04-22
Just skimmed through your list, looks correct. I've set up and administrated a couple CS:S servers and started a L4D server before (although was fairly dissappointed with the utter lack of control over the L4D server).

You'll want to disable RCON competely rather than just not setting a password, BTW. RCON lets you change maps, kick/ban players, respawn, basically allows you to control the server. You can do this simply from the server itself if you have it handy, but RCON let's you do this remotely while in game.

Since I haven't ran a L4D server since the Demo/first month or so, and never ran a L4D2 server, I don't know if there is any mod's that you can install that will help administrate the server. CS:S had some good ones like Mani's Admin Mod and SourceMod. These let you administrate through an in-game GUI rather than having to pull up console everytime.

Minimum hardware requirements? It's hard to say, generally RAM and Network speed are the major factors. IIRC, I was using around 200-300 MB's of RAM running a GUI-less Debian install with 3 CS:S servers running concurrently (mostly empty though not sure how much RAM will jump up with players). You should be alright for just one game server, maybe google can help find some official statement somewhere (my 10 sec search showed up nothing).

---

### Post by OldSchoolSoldier on 2010-04-30
I think there is a mistake.

---

### Post by wonko on 2010-07-07
When I'm executing "./steam -command update -game left4dead2 -dir ./" I get 
"Checking bootstrapper version ...
Getting version 39 of Steam HLDS Update Tool
Connection Reset"
Anyone have any ideas what might be wrong?

Edit: Nevermind: when I tried again today it worked like a charm - guess the steamservers just went down for a little while...

---

### Post by vandorjw on 2010-07-30
Does the Addon-support work under linux also.
I would like to be able to play the custom maps.

Can someone tell me how to add the maps to the server if it possible.

---

### Post by dfreer on 2010-07-30
It works, just a question of how. If it's the same as counterstrike, there will be a maps folder you can place custom maps in. Then just go up a folder and update the maplist.txt file with the map names, so the server will know they are there.

---

### Post by lx45803 on 2010-07-30
> **taofd said:**
> For simplicity's sake, I'm just putting it under my home dir.
Personally, you should put it in ~/srcds, a Source server usually has 5-7 files and folders it adds to its install directory. I like to keep things clean.

> **taofd said:**
> 
**To verify everything downloaded properly...**
> 
$./steam -command update -game left4dead2 -verify_all

This is completely unnecessary. Unless you have a really unreliable connection, the odds of files being corrupted during a download is tiny. Verifying them just after you've downloaded them is a waste of time.

> **taofd said:**
> 
*NOTE: I don't have a rcon_password set because I wouldn't know what to do with it... Where do I even go to connect?*


Controlling your server via the console can be achieved in several ways.
1. Connect to the server with L4D2 and use the **rcon_password** CVar to specify the password, and the **rcon** command to pass commands to the server.
2. To use the client without connecting, set the **rcon_address** CVar to your server's IP and use the commands above.
3. Run HLSW under wine. HLSW is a great tool for server administration, though if might not be worth the effort unless you want to monitor your server 24/7.
4. Just type commands directly into the server window.
5. Add **-netconport 23 -netconpassword foo** to your server's startup command and telnet into port 23. (This wont work for pre-L4D srcds servers. Also, I've never tried this.)

> **taofd said:**
> 
If anyone knows how to actually administer the server while it's running PLEASE LET ME KNOW and I'll add the information!


Well, let's start you off with a few commands now that you know how to use rcon.

**status** - Shows a list of clients connected to your server, their IPs, pings, SteamIDs, and some other stuff.
**kick** - Kick a player by name.
**banid** - Bans a player by their SteamID.
**banip** - Bans a player by their IP. Usually better to ban via SteamIDs though.
**removeid**
**removeip** - Counterparts to the above.
**help** - Provides help for a specific command.
**say** - Chats using the name 'Console'.


> **cc7gir said:**
> Can someone tell me how to add the maps to the server if it possible.
If the addon comes as a .vpk file, put it in left4dead2/left4dead2/addons. If that folder doesn't exist, create it.

If it's not in .vpk format, ask whoever made the map to do that for you. If you made the map, or can't get in touch with the map maker, go [here]("http://developer.valvesoftware.com/wiki/L4D_Campaign_Add-on_Tutorial#Packaging_and_shipping").





Phew. Anything I missed? :p

---

### Post by Sud4 on 2010-12-18
i already have the package for left 4 dead 2, and dont want to download the entire game from the internet, how can i get the game to work??

---

### Post by mattlach on 2011-01-07
Hey,

I'm trying to install a Counter-Strike Source server, but getting the following odd "permission denied" error.  I ahve tried everything I can think of.

Does anyone have any ideas?  Even if I try to execute as root I get a Permission Denied error.

```

css@Suppository:~/srcds$ wget http://storefront.steampowered.com/download/hldsupdatetool.bin
--2011-01-07 21:42:03--  http://storefront.steampowered.com/download/hldsupdatetool.bin
Resolving storefront.steampowered.com... 208.111.129.60, 68.142.91.151
Connecting to storefront.steampowered.com|208.111.129.60|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3513408 (3.4M) [application/octet-stream]
Saving to: `hldsupdatetool.bin'

100%[======================================>] 3,513,408   1.05M/s   in 3.2s    

2011-01-07 21:42:06 (1.05 MB/s) - `hldsupdatetool.bin' saved [3513408/3513408]
css@Suppository:~/srcds$ chmod +x hldsupdatetool.bin 
css@Suppository:~/srcds$ ./hldsupdatetool.bin
bash: ./hldsupdatetool.bin: Permission denied
```

Thanks,
Matt

---

### Post by dfreer on 2011-01-08
Can you list the permissions of the file, with ls -l?

---

### Post by taofd on 2011-01-09
> **lx45803 said:**
> Personally, you should put it in ~/srcds, a Source server usually has 5-7 files and folders it adds to its install directory. I like to keep things clean.


This is completely unnecessary. Unless you have a really unreliable connection, the odds of files being corrupted during a download is tiny. Verifying them just after you've downloaded them is a waste of time.



Controlling your server via the console can be achieved in several ways.
1. Connect to the server with L4D2 and use the **rcon_password** CVar to specify the password, and the **rcon** command to pass commands to the server.
2. To use the client without connecting, set the **rcon_address** CVar to your server's IP and use the commands above.
3. Run HLSW under wine. HLSW is a great tool for server administration, though if might not be worth the effort unless you want to monitor your server 24/7.
4. Just type commands directly into the server window.
5. Add **-netconport 23 -netconpassword foo** to your server's startup command and telnet into port 23. (This wont work for pre-L4D srcds servers. Also, I've never tried this.)



Well, let's start you off with a few commands now that you know how to use rcon.

**status** - Shows a list of clients connected to your server, their IPs, pings, SteamIDs, and some other stuff.
**kick** - Kick a player by name.
**banid** - Bans a player by their SteamID.
**banip** - Bans a player by their IP. Usually better to ban via SteamIDs though.
**removeid**
**removeip** - Counterparts to the above.
**help** - Provides help for a specific command.
**say** - Chats using the name 'Console'.



If the addon comes as a .vpk file, put it in left4dead2/left4dead2/addons. If that folder doesn't exist, create it.

If it's not in .vpk format, ask whoever made the map to do that for you. If you made the map, or can't get in touch with the map maker, go [here]("http://developer.valvesoftware.com/wiki/L4D_Campaign_Add-on_Tutorial#Packaging_and_shipping").





Phew. Anything I missed? :p

As you can see, I haven't checked this thread in a while XD
When I get more time I'll add the information into the main post :).

Do you by chance know how to change maps? I also had this weird problem  where the map splash wouldn't load and instead a generic l4d splash  would show.

Thanks!

---

### Post by mattlach on 2011-01-09
> **dfreer said:**
> Can you list the permissions of the file, with ls -l?

Thanks for the response.

I think I have narrowed it down to the line in my fstab that mounts the external drive array I use for my /home directory.  It turns out NOTHING will execute anywhere in /home, but if I set up the server in a new folder in the root called /srcds it works just fine...  I guess I just never tried to execute anything there before, as it was just used for storage  (this is my overkill NAS box)

I just can't seem to figure out what is wrong with this line in fstab that would cause this...

```

UUID=db7d26da-73c5-4258-979d-29e91388d752	/home	ext3    auto,users,rw,relatime 0 0
```

You'd think that after 15 years of Linux usage I'd have nailed the fstab configurations by now, but it turns out they still give me a headache :p

---

### Post by dfreer on 2011-01-10
Maybe try specifying exec in the mount options?

---

### Post by mattlach on 2011-01-19
> **dfreer said:**
> Maybe try specifying exec in the mount options?

Weird.

This did work. Thank you very much!

How come I've never needed to use the exec option before? :confused:

---

### Post by dfreer on 2011-01-19
It should be enabled by default, I have no idea why it wasn't for you.

---

### Post by coyotama on 2011-01-31
excellent! you guys are awesome, a very useful thread!

i am interested in spinning an installation cd that installs a l4d2 server, and automatically updates.

it would make installing a dedicated l4d2 server as easy as popping in a cd.

but first, i need to learn how to configure this as though i was going to have a dedicated physical server just for l4d2/tf2/css.

how do i go about doing this right? supposedly, servers are supposed to go in their own user.

does this mean i need to create a special user "srcds" and edit the permissions tightly? how do i configure the user to login and launch the server on boot?

am an ubuntu newbie.. thanks for any help ^^

---

