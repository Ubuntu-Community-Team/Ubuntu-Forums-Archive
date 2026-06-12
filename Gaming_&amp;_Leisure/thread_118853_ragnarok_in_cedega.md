---
title: "ragnarok in cedega"
date: 2006-01-17
forum: Gaming &amp; Leisure
---

### Post by windowmaker on 2006-01-17
i've been trying to get ragnarok online working in cedega 4.3.3 didn't work, so i updated to 5.0.3 and it still doesn't work, do any of you guys know how to get it working?

---

### Post by akurashy on 2006-01-17
I got it up and running but the terrain doesn't work ( I Mean it doesn't load the terrain) 

the how-to is a bit large but i will try my best to explain it

---

### Post by windowmaker on 2006-01-18
please tell!

---

### Post by jeffreyvergara.NET on 2006-01-18
I heard Ragnarok Private servers worked. those with Hack Prevention software wont... like the local ragnarok servers

---

### Post by shade11 on 2006-01-18
You installed Cedega and Point 2 Play right?

---

### Post by jeffreyvergara.NET on 2006-01-18
Cedega only... but I havnt tried ragnarok yet... you might also want to try WINE 0.9.5

---

### Post by windowmaker on 2006-01-18
i've got cedega 5.0.3, version 5.0 and above all come with point2play embedded.

i've also tried wine and crossover office and neither work, and i need to be able to run the ragnarok patcher and the sakray patcher so update it so i can play on the private server >__<

---

### Post by akurashy on 2006-01-18
point2play is stopped.. cedega is with point2play embedded yes

windowmaker i will! :) i just need a bit more of time 

and well to prove that I have here is a screenshot of me playing in a private server

[http://x0ne.net/gallery/v/akurashy/games/Screenshot-6_001.png.html?g2_imageViewsIndex=1](http://x0ne.net/gallery/v/akurashy/games/Screenshot-6_001.png.html?g2_imageViewsIndex=1)

as you see the terrain doesn't load which is what I WANT TO FIX BADLY but still looking around

ragnarok patcher doesn't work in cedega
(they said something about updating it using wine)

---

### Post by Disastorm on 2006-02-11
I was wondering how well this game works in linux, and how hard it is to get working.

---

### Post by Talikar on 2006-02-21
I'm personally beginning to think Ragnarok Online is not worth the amount of trouble to get it working. I've spent countless hours trying to get it to work, and here's the problems:

[quote=Talikar,Feb 21 2006, 11:46 PM]
Ok I've tried multiple programs to try and get Ragnarok Online working under linux.

Wine - Fullscreen runs incredibly slow, and once I get in-game, I'm unable to move, my weight is at 0/0, no items are in my inventory and all the skills are gone, also, chatting doesn't work and the "exit game" function ceases to work as well. Under windowed mode, wine states it's unsupported (the window mode) and although the game runs fast (same problem if I get all the way in) it has a problem where the screen flickers normal/black continuously.

Crossover Office - Same as Wine, wait, it is wine, with a GUI? Hm, I'm sure there's more to this program than that. Anyway, it has the same problems as wine, not much else I can say. The one difference is that SOUND works properly with it.

Cedega - Windowed mode doesn't work worth crap, same problem as Wine. However, under fullscreen the game runs at a decent speed (mind you loading time is extremely slow during the loading screens, same with the two above). However, in the game I have the same problems as the apps above (character froze, no data).

vmware - With experimental Direct 3D support it just opens the window, doesn't display anything in it though, rendering the game impossible to play. It does however play the sound.[/quote]

So I've removed all the programs I tried to get it working with from my PC. Anyone know if there's a way to get it 100% working with the latest free Wine?

Some other information:
I did not try the game on an official server, because I don't have an account anymore (used to be a beta tester way back when iRO was open-beta). Now however I use kRO and Sakray on my own LAN server (which I personally don't think is 'illegal' since it's just me wanting to play by myself without the immaturity that can come with a large server.

Anyway, game doesn't get passed login screens with the regular programs, but with linuxexe.exe (which I found using the winehq site) it works to where I mentioned above in the quoted text area. Don't suppose there's a "better" wine exclusive linux kRO/sak client exe file that would work? :-)

---

### Post by Disastorm on 2006-02-22
i can't even load the game i get a black screen lol

---

### Post by Talikar on 2006-02-23
Nevermind, my way was only a temp. fix, I'll see if I can get it working properly tomorrow.

However, I will say one thing, it seems that one could only get it working locally using a Server Emulator for now. Also, dual booting a windows seems to be needed as well.

---

### Post by Disastorm on 2006-02-23
what vid card do u have? I have a Radeon XpRESS 200m and I was wondering if its even possible at all to get it working with this.  Ive tried and tried for a long time and I can't get anything better than a black screen.

---

### Post by Talikar on 2006-02-23
I'm using an ATi Radeon 9200.

On Cedega 5.1, dual booting Windows 2000 (not sure about other windows Operating Systems) and using a linuxexe.exe client file allows you to get in-game (on a private server). There are two problems though:

1) Loading screens take forever to go through, making your packet time out on most private servers (since they mainly use eAthena and it is set to 60seconds before timing out, doubling it fixes that problem).

2) On a private server that's set to allow you to have 120seconds before a time out, you can load the game, however, when you get in-game you can move around, fight things, etc, but for me I had no items showing, weight at 0/0 (if I picked anything up it would be x/0 and I couldn't fight because of being overburdened). This was fixed by just going through a zone, but, with the slow loading time this gets a little annoying.

Dual booting a windows O/S seems to be needed though (although I haven't tried it without it) Dual booting may answer your black screen issue? Not sure about this though. :(

Does anyone know how to fix Cedega and RO loading times? That would make the game completely playable.

---

### Post by Disastorm on 2006-02-23
do u cedega from your windows partition? anyway I dual boot as well and Ive tried installing ragnarok in my linux partition, and as well ive tried to wine the windows partition and I still get black screen.  Ive tried linuxexe.exe.  I get 
0003:: Bad stuff: client ignore setting select events for 0x9004e500 to 1
 Talikar do u have an Instant Messenger?

Does anyone know if this game works with VMWare?

---

### Post by Talikar on 2006-02-23
You using Regular Wine or Cedega? The regular Wine (from winehq) doesn't play the game very well at all, if one does manage to get it to get even up to the Login screen it's very choppy (rendering the mouse almost useless).

I'm not going to say vmware doesn't work, I only tried it for a little while (turned all Direct 3D stuff on). I downloaded the vmware workstation trial before, set it up to use D3D, and went into RO, it just sat with a blank screen (like your wine does). It only seemed to want to play sound?:confused: Maybe someone else had more luck than I did.

I sort of suggest downloading the cedega_timedemo and testing to see if you can get Ragnarok Online to work with that.

Actually, wait, after thinking it over, I suggest waiting a year or 2 for wine (from winehq) to be better.;) 

At the moment I don't have an account ID on messenger services that I use, sorry. x.x I'm personally just waiting for wine to release a better version or cedega to release a better version, the current ones suck for this game.:mad: 

Lol, then again it's kind of funny. I didn't realize Ragnarok Online was such a complex game that they couldn't make it work properly, yet, counterstrike can work fine under cedega (if steam works, or so I've read).;)

Note: I do have messengers, but I doubt I'd be helpful, I don't really have the game 100% working either.

---

### Post by Disastorm on 2006-02-24
sorry actually i get that error in cedega, in wine i get some different error. (same black screen though)

---

### Post by Talikar on 2006-02-24
Hm, that doesn't make much sense.... I just did a fresh install of ubuntu linux (I did however backup my Ragnarok Online files). I completely removed my windows partition and RO runs just as well as before.... Loading time still sucks though.

Do you have the latest drivers installed for your graphics card?

Also, here's the linuxexe file that "I" have, it 'should' work (this is assuming your file is busted or something, and not something else):
[http://srxw.no-ip.info:4005/linuxexe.zip](http://srxw.no-ip.info:4005/linuxexe.zip)

Edit:
lol, I take a little of that back though, the game doesn't work "just as well as before" it only seemed that way when I first booted it. Without Windows dual booted the game is really choppy though. =P

---

### Post by Disastorm on 2006-02-24
well, like I've said, Ive heard it may be a problem with the ati drivers (yes i have latest ones) and my video card the Radeon Xpress 200m (different chipset than yours).

---

### Post by Talikar on 2006-02-24
Yeah, linux and any ATi card or chip doesn't get along very well. I've resorted to booting into Windows 2000 to do anything lol.

I'll come back to Linux in another year when drivers are more supported (especially my Sound Blaster Live! 24 bit, getting surround 5.1 to work on it is a nightmare, especially since Ubuntu doesn't let me install the latest ALSA drivers configured for it).

;) Could always get a brand new nVidia card.

Hopefully when I come back to linux in a year or so all the apps (like wine) will be updated and work well with RO. Until then, peace all, Linux has been a great learning experience, and I will go back to it eventually. I'll still hang around the forums naturally to see if I can learn any new stuff though.

Good luck with getting RO working all. :cool: 

P.S. sorry I couldn't help, Disastorm. :( 

P.P.S. Is it just me or is there only a handful of people trying to get RO working under wine or cedega?

---

### Post by Disastorm on 2006-02-27
well u just said the loading time was bad, but the rest of the game played well? I dunno about u but i would consider that playable.

---

### Post by Talikar on 2006-02-28
I would normally too, but in Ragnarok Online, for the training you have to go through multiple zones. For job advancements you again have to go through multiple zones. So yes, I agree, the game is playable, if you have the patience to sit through minute long loading screens lol.

It's ok if you just fight in a dungeon though (for leveling) so leveling is fine, it's just the exploring/quests that would take longer than necessary, and parties would hate you if they have to zone (for whatever reason) and wait a minute longer (or more, depends on the zone, some load faster than others) for you.

Once the game works with the regular wine with no dual booting and fast loading screens I'll consider it playable. :P

Also, in an earlier post of mine I mentioned something about having to zone to get some of my stats functioning properly, well, that's not a linux problem, that's a eAthena server problem, happened on winslows while I was testing it (except in winslows loading is faster so the problem isn't so bothersome).

That's my end though, how about you? Can you go in game now?

---

### Post by Disastorm on 2006-03-01
nope still cant load even the login screen.  The only thing I can think of is that its my Radeon XPress 200m.

---

### Post by Talikar on 2006-03-02
[QUOTE=Disastorm]nope still cant load even the login screen.  The only thing I can think of is that its my Radeon XPress 200m.[/QUOTE]
Not sure if this would work since I don't really have a testing environment, but, if you use Cedega, have you tried swiftshader?
[http://www.transgaming.com/swiftshader.php](http://www.transgaming.com/swiftshader.php)

Not sure if it works while dual booting windows though..:(

---

### Post by Stained_Soul on 2006-03-21
Me and a friend got the game up and running to the login screen and the server select screen but for some reason it doesn't connect... anyone have an idea about that?

I'm also interested in the linuxexe.zip file but I've not been able to download it from the winehq page or anywhere else...

If someone could put up a link of something I would be very grateful ^^

---

### Post by Talikar on 2006-03-22
Yeah the connections don't work properly with the original exe file. You can get the linuxexe.exe file from the link below, extract it to your RO folder and use wine to open it, it should work afterwards. I know it does if you connect to a private server and use a data folder with a sclientinfo.xml file.

[http://srxro.no-ip.info:4005/files/linuxexe.exe.tar.gz](http://srxro.no-ip.info:4005/files/linuxexe.exe.tar.gz)

That link should work.

Also, if you get in-game, could you please let me know if loading screens go by fast or if they still are slow? If they're fast, which version of cedega are you using?

---

### Post by Stained_Soul on 2006-04-04
Well I know that it doesn't work with Euphro eather way... but that's all I know for sure... going to try some other free servers to see if it's the same problem. :-k

---

### Post by Stained_Soul on 2006-05-11
The game works with Xaosro and it's no slow loading times... I've got it working perfekt on Ubuntu... :-D

---

### Post by argie on 2006-05-22
In January 2005, I gave this a shot with whatever wine was latest at the time, but that was on RedHat. I have a screenie to prove I got ingame.
[img]http://img151.imageshack.us/img151/5945/screenshot17eq.png[/img]
There's a guide on a private server I used to play on on how to install RO, 
[here]("http://q-ro.net/ragnarok/hi/index.php?option=com_content&task=view&id=23&Itemid=40")
I haven't been able to use because of video driver problems.

---

### Post by Jeef on 2006-08-05
> **windowmaker said:**
> i've been trying to get ragnarok online working in cedega 4.3.3 didn't work, so i updated to 5.0.3 and it still doesn't work, do any of you guys know how to get it working?
Screw Cedega, it sports a nasty backspacing glitch in Ragnarok Online. Install WINE, and use it instead. It's not very difficult to get WINE running Ragnarok Online essentially flawlessly (for private servers, that is). I've been playing it for quite some time using WINE. Regarding Ragnarok Online's configuration itself, you must run it in fullscreen mode (use `wine Setup.exe` in Ragnarok Online's directory to configure this); I also suggest disabling lightmaps, as they can cause problems under WINE. For WINE to run Ragnarok Online properly "in a window," you will need to enable a virtual desktop within WINE (using `winecfg`); mine runs in a 1024x768 virtual desktop, since I run in 1600x1200. WINE's virtual desktop creates the same effect as running Ragnarok Online windowed, so please exhale and rejoice. :)

Here is an example of what my suggestion looks like in the end:
[IMG]http://i7.photobucket.com/albums/y286/akusarujin/Ragnarok/RagnarokWithWINE-Compressed.jpg[/IMG]

---

### Post by sekre on 2006-09-07
Jeef : (Want to confirm) Are you able to play the game without sloppy mouse ?

If so, could you please tell me how. Because when I try to start it using 9.20 I can go ingame, but with major slowdowns on the mouse pointer. Able to connect using my keyboard without problems. Game loads slow, and when I get in I have some major slowdowns and an unuseable mouse =/

I would really appreciate any help, since installing windows and tripple-booting my macbook seems like a total pain in the backside...:P

---

### Post by Lunks on 2007-07-16
I'm not able to use Ragnarok on Cedega.
I can't seem do find sclient.xml (or smth, no xml files at all =\), and I'm not sure what IP my private address is.

I can only go up to login screen, can someone help me? :)

---

### Post by orangebase on 2007-08-10
What do you mean you can only go up to the login screen?

---

### Post by Burbruee on 2007-08-11
I've been trying some private servers in Cedega, but not all work:

AnimaRO: Works perfect, but there's no training, you just get thrown right into RO.
RebirthRO: Does not work, cedega does not open the .exe
TalonRO: Works, but their server is very laggy and not much people on.
EuphRO: Stuck at login-screen, gives message "Could not connect to server" ... If anyone has gotten this server to work, please help out !!!

Those are the ones I've tried. Reason I really want to get on EuphRO is because there are plenty of people online ( 1000+ ) and it's one of the best low-rate servers available.
It gets to login-screen, it feels really bad getting so close! :(

EDIT: I found this on appdb.winehq..

> -Some fixed binary file is not connected server.
Then, you must do follow command. 
 
su
iptables -t nat -A OUTPUT -d Fallacy_IP -j DNAT --to Real_IP
(ex: iptables -t nat -A OUTPUT -d 46.110.101.116 -j DNAT --to 59.0.120.14) 
wine Ragexe.exe -1rag1


Is that something that could let me on the EuphRO server? But I don't know how to get the Server IPs. ( I need 2 of them, right? ) 
I also heard about something called linuxexe for playing on private servers, but if I understand it correctly it's for servers connecting using data folder with sclientinfo.xml file, and none of the servers I have tried out uses that, so I guess it wouldn't help. Can't find any working links to linuxexe either. =/

Please reply! :-D

---

### Post by orangebase on 2007-08-12
What you can do is install Wireshark, open it as root, and then check the packets while you log in. You can look through the list of packets. It's a bit of guessing and checking. Once you find the one you suspect is being sent by your RO client, you can go google your server info. If you indeed have 1000+ players on that server, then you'd probably find the server info easily, especially from sites that teach you how to bot (not that you're going to do that).

Then you can use that command above. I can give more detail if you want.

---

### Post by Burbruee on 2007-08-12
Thanks for your reply. :)

I googled "EuphRO server ip" and found one topic about botting on a forum. However, the post is over a year old so if EuphRO upgraded their servers then there is a possibility that the IP is also outdated.
I will give it a try though. I'll install wireshark and try it. Could be hard to find the correct IP though, even if I close Ktorrent, Skype, Konqueror etc there are still some packets.

But I will try it out. But if I by mistake get the wrong IP, how do I clear the iptable rule I just made?

Thanks. :)

---

### Post by Burbruee on 2007-08-12
Look at this screenshot:

[img]http://img511.imageshack.us/img511/5959/snapshot5pi7.png[/img]

If I ping game.euphrogame.com I get the IP 69.39.226.26, also I downloaded grfedit to check the clientinfo.xml which said game.euphrogame.com in the adress-field and **3872** in the port field.

I tried to do:
sudo iptables -t nat -A OUTPUT -d 69.39.226.26 -j DNAT --to 81.26.227.3

But that didn't work, so I tried to do:
sudo iptables -t nat -A OUTPUT -d 69.39.226.26 -j DNAT --to 195.54.122.204

Which didn't make a difference either..
Help? :)

---

### Post by Burbruee on 2007-08-12
SOLVED! :)
sudo iptables -t nat -A OUTPUT -d 97.109.101.46 -j DNAT --to 69.39.226.26

This worked for me, I can now connect and play on the best low-rate server. :D

---

### Post by streetsurfer on 2007-09-19
doesnt work :(

---

### Post by hikaricore on 2007-09-19
> **streetsurfer said:**
> doesnt work :(

Since you felt like bringing back a thread that no one has posted in for a month, you may want to be more specific.

Looking at your other posts I can see you've had trouble with your ATI card/drivers and are running compiz/beryl.  These could both be factors in your trouble trying to run things.

---

### Post by streetsurfer on 2007-09-19
hehe sry.
I was trying private servers and none of them dont run the sakray patcher.exe
also the ati drivers i have 8.38 dont seem to run it smoothly at all. >.<

Hopefully new drivers can address that (8.42)

right now does anyone know which private servers work with WINE/Cedega and anyone had luck with ATI cards?

---

### Post by dresman on 2007-09-19
:confused:how do u start a new thread?

---

