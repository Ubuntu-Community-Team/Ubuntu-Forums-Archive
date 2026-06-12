---
title: "Regnum Online - new Ubuntu Clan !"
date: 2007-12-24
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2007-12-24
So I've been talking with CK some time ago and now I made a new Ubuntu Clan at Alsius realm.

It's called UGA and can be translated to :

Ubuntu Gamers Arena
United Goats of Alsius

The only restrictions are that you must speak English and you MUST be an uthgar  (a goat ;)).

If you want to join our clan please contact in game with :

Maxim The Mad
Maxim The Damned
Macabra (our Spanish-English queen ;)).

Just add us to your buddy list and when you see us online begin the chat.

I remind you again that this clan is from Alsius realm.

Regards
Maxim.

---

### Post by joku_muko on 2007-12-24
I don't play often, but I'll look you up next time I'm on.

---

### Post by nille on 2007-12-26
Too bad I'm in Syrtis :( Perhaps it's time for me to restart and create a new character?

What lvl are the people in the clan?

---

### Post by compiledkernel on 2007-12-26
speaking for the Ubuntu Gamers Arena guys, anywhere from level 1 to level 15ish.

---

### Post by MaximB on 2007-12-26
My 2 characters are 42 and 32 , our queen is 42 (I think) , I got members who are in teir 20's and 30's as well as "fresh noobs" lvl 10+ ;)
We are welcome any goat !

---

### Post by dannyboy79 on 2007-12-26
i signed up and activated my account but I have been reading about problems getting it to work in Gutsy Gibbon. Something about the rolauncher segfaulting? I read this on the regnum forums. Can you provide me any tips for getting this game running on Feisty or Gutsy? I am at work so I can't install it right this second. One machine at home has a XFX Geforce 6200 and the other a MX440. Would either be ok to play the game? Thanks for any info. I would like to join your clan but I have never played this game before (fyi)

---

### Post by MaximB on 2007-12-26
There are many issue with it, but once you overcome them it runs great (not counting the lags which have nothing to do with the client).

Anyway if you have a problem installing or running this game try this command from the CLI : 
rober@rober:~/regnum$ G_SLICE=always-malloc ./rolauncher

---

### Post by dannyboy79 on 2007-12-26
so you're saying that I can use the current linux installer from their website and it'll work with the command that you posted? I read that an earlier installer worked fine but the new one doesn't work. Does anyone still have the old installer that they could upload somewhere and post the link or email it to me, [email]darfsten@hotmail.com[/email]?

---

### Post by nille on 2007-12-26
I'm responsible for one of the Gutsy-threads at the official Regnum forum, and I somehow solved it..

There's another thing you can try:
**MALLOC_CHECK_=0 ./rolauncher**

**EDIT:** The thread I was refering to is this:
[http://www.regnumonline.com.ar/forum/showthread.php?t=16679](http://www.regnumonline.com.ar/forum/showthread.php?t=16679)

---

### Post by compiledkernel on 2007-12-26
For any beginning interested party that joins up, the two mid level Trainers, myself and Saphira will get you on the road if you need a hand.

---

### Post by MaximB on 2007-12-26
> **dannyboy79 said:**
> so you're saying that I can use the current linux installer from their website and it'll work with the command that you posted? I read that an earlier installer worked fine but the new one doesn't work. Does anyone still have the old installer that they could upload somewhere and post the link or email it to me, [email]darfsten@hotmail.com[/email]?

You can't use the old installer even if you got it, it would update itself to the newest prior to installation.
You just need to bypass the "problem" if you will even have that problem with the commands given

And create a character at the Alsius realm - and it better be a Goat ! :D

---

### Post by nille on 2007-12-26
Yeah, time to go goat!

Archer (some kind of, since I have no idea how to play as an archer) or Conjurer? What do we need?


**EDIT:** Choice is simple: Goats can't even become archers. My characters name is Ulmanyar.

---

### Post by compiledkernel on 2007-12-27
Dropped you a PM nille.

---

### Post by MaximB on 2007-12-27
Any goat is welcome, but atm we need more warriors (Barbarians and Knights).

---

### Post by nille on 2007-12-30
I'm at lvl 10 now, should I become Conjurer (my pref) or Warlock (sure elemental is nice)?

---

### Post by compiledkernel on 2007-12-30
Contact Corwyn Gymch or Mamiya in game, and they (or I will) help you.

---

### Post by dannyboy79 on 2007-12-31
i installed it and during the startup, when it's telling you the story, I have no sound? Is that the way it's suppose to be? Also, when I get to chose a character, there's no goats. There's uthgars, is that what you mean?

---

### Post by compiledkernel on 2007-12-31
sudo apt-get install alsa-oss, then run regnum with the command aoss before it. 

Thatll solve your audio problems. 

Uthgars, yes, are the Goat people.

---

### Post by dannyboy79 on 2007-12-31
when you say run ./rolauncher with the aoss command, how exactly do you mean?

---

### Post by compiledkernel on 2007-12-31
user@computer:~$ aoss ./rolauncher

Like that.

---

### Post by dannyboy79 on 2007-12-31
when I exit the game, I am seeing this in the terminal:  Found 4 messages leaked

what does that mean?

Not to mention I just started it with the aoss command you gave me and still no sound in the intro. only text at bottom.

this is lscpi

00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:09.0 FireWire (IEEE 1394): Texas Instruments FireWire Controller (rev 01)
00:0a.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 1

---

### Post by compiledkernel on 2007-12-31
Im not exactly sure, Ive seen that on occasion, but doesnt seem to affect game play much.

---

### Post by dannyboy79 on 2007-12-31
well, if there's no sound, then that's not too fun is it? are you saying that there's no sound in the game?

---

### Post by compiledkernel on 2007-12-31
oh I get sound a plenty, I just have to run it in Alsa oss mode. 

do this. 

sudo apt-get install openal0a 

then do a 


gedit ~/.openalrc

Paste This:

(define devices '(native))

Save the file and try running the game again

---

### Post by dannyboy79 on 2007-12-31
also, I am at the part where I can select to add 5 points to any attribute, do you ahve any sugestions or did I read that I shouldn't hit the plus (+) symbol?
i chose a warrior uthgar

---

### Post by dannyboy79 on 2007-12-31
GOT IT WORKING. 

It was a combination of doing these 3 things:

sudo aptitude install alsa-oss

sudo aptitude install libalut0

and then this:

gedit ~/.openalrc

Paste This:

(define devices '(native))

Then is runs with this command:
./rolauncher

thanks

---

### Post by MaximB on 2008-01-01
For warrior chose strength (all 5 points into it)
For mages chose intelligence
For archers chose dexterity
You can mix points as you see fit, but those are the important ones for each class.

A good website you should look for quests and skills is : [http://www.regnumzg.com.ar](http://www.regnumzg.com.ar)

---

### Post by dannyboy79 on 2008-01-02
well I tried it out and it's pretty cool. This is my first MMOPRG (or whatever the abbreviation is?) I killed the 5 baby cubs, went to see Bred, then got a sword, then killed 3 young wolves,got new armor, then went to kill 3 skeletons and the game just crashed me back to the Ubuntu desktop. Is that because of something on my machine or did the server crash? How can I tell what went wrong? I was running the game in 1024x768x32 resolution. My normal desktop is 1280x1024x24 (i think it's 24 anyway),, when the game crashed, my desktop was like shrunk. I had to move the cursor over to the right to see the whole screen, the desktop would shift over to the right. I just did a ctrl-alt-backspace to restart X. THen I didn't play anymore. It was fun though. 

I need to learn how to find other Ubuntu Clan members within Aslius. I think I can start a private chat with "-chat foo". I was private chatting with another who initiated the private chat but then his name just stayed there next to General and Aslius. I think I am only lvl2.

Most importantly, how do I join the clan?

---

### Post by MaximB on 2008-01-02
First of all you need that your Ubuntu resolution would match the games resolution.
In most ceases it's the game that crashes , server just disconnects.
If you still having problems you can try to play in "Safe mode" which isn't bad at all.

If you want to join our clan I advice you to first reach level 9-10 so you could go out of the noob zone.
Then just add our clan members to your buddy list by this command : 
/budy nameofthebuddy
After that you can see them in your buddy list - green indicates that they are online and free to chat via double click on it's name.

A small part of our Clan members could be found here : [http://gaming.gwos.org/doku.php/clans:uga:regnum](http://gaming.gwos.org/doku.php/clans:uga:regnum)
If you see any goat with the "UGA" name above his head - it's our member ;)

---

### Post by dannyboy79 on 2008-01-02
> **MaximB said:**
> First of all you need that your Ubuntu resolution would match the games resolution.
In most ceases it's the game that crashes , server just disconnects.
If you still having problems you can try to play in "Safe mode" which isn't bad at all.

If you want to join our clan I advice you to first reach level 9-10 so you could go out of the noob zone.
Then just add our clan members to your buddy list by this command : 
/budy nameofthebuddy
After that you can see them in your buddy list - green indicates that they are online and free to chat via double click on it's name.

A small part of our Clan members could be found here : [http://gaming.gwos.org/doku.php/clans:uga:regnum](http://gaming.gwos.org/doku.php/clans:uga:regnum)
If you see any goat with the "UGA" name above his head - it's our member ;)

so I guess I'll try to run the game in 1280x1024x24. What's wierd is that the game was running fine in 1024x768x32 for over an hour. Then all of a sudden I was dropped back to my ubuntu desktop.

My name is ubunthgar in the game. You're saying that I can go to that URL and see people's names that are in teh UGA clan? I understand how to add buddies to my buddy list, but there's a clan list. How do I get added to the clan? I will keep playing until I am at lvl10 but I can add the UGA names to my buddy list whenever correct? Also, are you saying that when I get to lvl10, I'll somehow get the UGA above my characters head?

Thanks maximB

---

### Post by MaximB on 2008-01-02
Add buddies from our clan, when they be online speak with them and they will be sure to add you to our clan.
I give permission to invite people to our clan to any active member above level 10. (not automatically).
The only condition to invite or be invited is that the member must be an uthgar.

And let the dwarfs sue me.

---

### Post by dannyboy79 on 2008-01-02
i can't set my game to 1280x1024x32 because then I get a bunch of pauses. They are all the time but once in awhile (once every 5 seconds) the screen will skip in the intro. I can run it at 1024x768x16 (or was it x32?) and it still skips but way less! My native res for my GeForce 6200 128mb ram 8X AGP is 1280x12024x24. I am using this nvidia driver: 100.14.23
I am about to play again, will see if it crashes. would there be any log anywhere?

---

### Post by MaximB on 2008-01-03
The logs (called crash backreport) are located in your live directory in regnum.
The puses are called lags, usually in the pick hours were 400+ users are online.
It happens to most people, it's not because of your configurations the problem is in their side of things.

---

### Post by dannyboy79 on 2008-01-03
well it didn't crash last night, that was playing at 1024x768x32. So I think it may have just been a glitch or something? I notice that my CPU runs at like 86-90% when playing. I have to be careful and not play when mythtv is recording because then my cpu can't handle it I don't think. It's a E4300 C2D 1.8ghz with 2gb or DDR2 533mhz in a Asrock 775dual-vsta motherboard.

---

### Post by dannyboy79 on 2008-01-04
is anyone aware of how to make the .png I have as my avatar smaller so that I can chose it as an icon for the program launcher that I added to my upper panel to launch Regnum Online?

I saved the pic from the regnum online website, then I opened gimp and made it a png because other icons are png's. then when I went to icon within the app launcher properties, I navigated to the desktop but the .png file wasn't a choice despite it being there on the desktop? Right now the app launcher within my upper panel doesn't have an icon and that looks stupid. Thanks for any help here.

---

### Post by nille on 2008-01-04
dannyboy79:
Open your picture in GIMP, go to Image -> Canvas size.. and make the picture a square (change Offset to get it centered). Then go to Image -> Scale image, and change it to some size like 64x64 or 128x128 (or even 32x32). That'd be a great Icon?

Or use the attached one I just made.

---

### Post by dannyboy79 on 2008-01-04
yeah, but as I said, the picture isn't a choice when it's stored on my desktop? it's really weird. the properties dialog box of the app launcher takes me to a pre-defined location of icons, some are png's some are svg's but as I said, when I navigate to the desktop, it's not there. OR do you think it's not there because it's too large? I'll try this out with the one you uploaded for me. THanks

SOLVED
once I put it in the /usr/share/pixmaps/ folder, I was able to select it, THANKS.

---

### Post by aephex on 2008-01-11
I'm new to both Ubuntu and Regnum. I guess I'd be pretty stupid not to look you guys up in game. >.<;

Let me get a feel for the game and if I decide to stick with it I'll drop a line your way.

---

### Post by dannyboy79 on 2008-01-11
i'm ubunthgar within the game. I am at level 6 and maxim won't add you to clan until you reach level 8. fyi.

---

### Post by compiledkernel on 2008-01-11
Actually, Mamiya and Corwyn Gymch can add, but we can also help you quest complete to get up to level 8, just have to let us know.

---

### Post by MaximB on 2008-01-11
Leveling up to level 10 should take you a few hours.
Then you can get a new subclass and watch for yourself if it's fun for you or not.
If it is then you might apply for the clan, there is no purpose the be in a clan at a level lower then 10 because you will be in other place, far from all others and we couldn't help you much there.

So when you up to level 10 and go to the more mature zone and can say "Yes I like this game" or "No it's not for me" then you could decide to join our clan.

We are not looking for as many members as possible, we are looking for active members.

---

### Post by dannyboy79 on 2008-01-11
> **compiledkernel said:**
> Actually, Mamiya and Corwyn Gymch can add, but we can also help you quest complete to get up to level 8, just have to let us know.

well I haven't played in awhile so that's why I am still at lvl 6. what does, "you help mequest complete" mean? thanks and maybe I'll see you in the game sometime as I have added all those names within my buddy list.

---

### Post by dannyboy79 on 2008-01-11
> **MaximB said:**
> Leveling up to level 10 should take you a few hours.
Then you can get a new subclass and watch for yourself if it's fun for you or not.
If it is then you might apply for the clan, there is no purpose the be in a clan at a level lower then 10 because you will be in other place, far from all others and we couldn't help you much there.

So when you up to level 10 and go to the more mature zone and can say "Yes I like this game" or "No it's not for me" then you could decide to join our clan.

We are not looking for as many members as possible, we are looking for active members.

fair enough.

---

### Post by ScottKidder on 2008-01-16
I started a Goat Warrior, I think I'm level 5 now, I'll probably get 10 tommorow, what  Subclass do you guys recommend?

---

### Post by compiledkernel on 2008-01-16
Barbarian. 

Just contact Mamiya or Corwyn Gymch in game, and theyll set you straight.

---

### Post by ScottKidder on 2008-01-17
I'm level 10, Barbarian. Everyone that has been listed here is never online, I would like to join the clan though.

---

### Post by MaximB on 2008-01-17
Please post your character names here so we can contact you when we'll be online.

---

### Post by ScottKidder on 2008-01-17
Charactor Name is Mavrick(Maverick was Taken) :)

---

### Post by ionredline on 2008-01-18
Wow - I had no idea it would take so long to patch!  Sure wish I knew how to speak spanish....People seem rather friendly in the game... I just don't know what they're saying..

---

### Post by ScottKidder on 2008-01-18
Got a hold of Corwyn and Mamiya, those guys are awesome, and helped me out a lot. This clan definately has potential, UGA fo life!

---

### Post by NeverM$4Me on 2008-01-25
> **ScottKidder said:**
> Got a hold of Corwyn and Mamiya, those guys are awesome, and helped me out a lot. This clan definately has potential, UGA fo life!

Yeah, Corwyn is a great guy. I met him in the game last night and he helped me on how to join the clan. We'll soon be able to fight side by side for Alsius when getting together in game.

---

### Post by nille on 2008-03-11
Anyone still active in the clan? I would gladly join!

Someone who can invite me could perhaps send me a PM, and/or add me in-game. My name is Ulmanyar

---

### Post by Sukarn on 2008-05-03
Guys, I have a weird problem where the game gets stuck randomly. The music keeps playing, but that's it. Nothing else works.
It just happened to me again a couple of minutes ago, just as I accepted a quest, the character bowed down, the quest accepting music played, and the screen froze. The music keeps playing after that but I cannot do anything else.
It happened yesterday when I ran RO from within GNOME, and it happened today when I ran RO on a fresh X server with the only other process on that X-server being gnome-settings-daemon.
I'll try running the game by removing even the gnome-settings daemon, but something tells me that this won't help much.

Oh, and the only way I found to stop the "game" (yes, the process is called game) was to go into a virtual terminal, and type "ps -A | grep game" and then do a "kill -9" on that process because for some reason, the process "game" keeps running even after doing a Ctrl+Alt+Backspace on the X-server, and "killall game" does not stop it.


I'm just level 3 so far and this has happened to me twice already. If this goes on, I don't think I would be able to continue playing this game.


EDIT: The game (along with the X-server) crashed when I click the "Enter game" button in the verification and options window that comes up after logging in, if I do not run gnome-settings-daemon.

---

### Post by nille on 2008-05-04
Try turning off all terrain detail. That made my game crash every fifth minute before I turned it off.. but I don't know if they have fixed it yet (haven't bothered turning it on).

---

### Post by Aetheric on 2008-05-13
Is this clan still active? I just got Regnum play for fun. If someone in game wants to play or group up, I've gotten to lvl 5 already tonight.

My character's name is Graska Whitemane, Uthgar warrior.

---

### Post by cmileto on 2008-05-20
Almost lvl 9 with a goat mage named Goat Lord.  Anyone still around?

---

### Post by Phenax on 2008-05-20
Edit: Nevermind

---

### Post by nille on 2008-05-20
I'm still playing, in Alsius. But I'm not in the UGA Clan, and there are not a lot of members still active. I've seen Macabra from time to time, and another goat for which I can't remember the name. But I don't think anyone can add players to the clan. Perhaps it's fixed, and in that case you could talk to Macabra I think..

---

### Post by slave-zeo on 2009-05-16
Anyone still around here? I just started playing and am looking for some homies.

---

### Post by what, what? on 2009-12-11
is this at all still alive?

---

