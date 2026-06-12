---
title: "ubuntu randomly crashes?"
date: 2009-04-15
forum: General Help
---

### Post by blandino123 on 2009-04-15
hey guys i am about 90% noob to linux as ive used it in the past but i have no idea how to code or anything.last night i did a total upgrade to ubuntu 8.10 because i was tired of vista.then i tryed to upgrade to 9.04 and i feel asleep XD im guessing that while installing my pc shut down because i think i set it for that (IDK?) now i have a small little thing next to my volume (like a red ball with a line in the middle) saying that some updates are missing and i should install them.but when i try to do this...the install just closes out of no where! the broken dependecies part is that i tried installing gfire and it told me about it. so any help for a noob?):P..while trying to install flash player i also get something about broken packages....ok last thing.. heres an error message i get when i go to add/remove 

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'....BTW i tryed using the bug reporter..but not even that works

---

### Post by blandino123 on 2009-04-15
hey guys i am about 90% noob to linux as ive used it in the past but i have no idea how to code or anything.last night i did a total upgrade to ubuntu 8.10 because i was tired of vista.then i tryed to upgrade to 9.04 and i feel asleep XD im guessing that while installing my pc shut down because i think i set it for that (IDK?) now i have a small little thing next to my volume (like a red ball with a line in the middle) saying that some updates are missing and i should install them.but when i try to do this...the install just closes out of no where! the broken dependecies part is that i tried installing gfire and it told me about it. so any help for a noob?..while trying to install flash player i also get something about broken packages....ok last thing.. heres an error message i get when i go to add/remove

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'....BTW i tryed using the bug reporter..but not even that works

---

### Post by LoloftheRings on 2009-04-15
Why don't you try running 'sudo apt-get update' and 'sudo apt-get install -f' in terminal?
the terminal can be found in Applications -> Accesoires -> Terminal
This is what usually happens when aborting while updating or installing software.

I think there should be a one-click solution in the notification, as this is pretty hard to fix if you don't know anything about apt and the command line.

Welcome back in the wonderful world of Linux, mate!

---

### Post by blandino123 on 2009-04-15
> **LoloftheRings said:**
> Why don't you try running 'sudo apt-get update' and 'sudo apt-get install -f' in terminal?
the terminal can be found in Applications -> Accesoires -> Terminal
This is what usually happens when aborting while updating or installing software.

I think there should be a one-click solution in the notification, as this is pretty hard to fix if you don't know anything about apt and the command line.

Welcome back in the wonderful world of Linux, mate!


hey thanks for the reply. when i ran sudo apt-get update it started downloading some packages and then i get this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem...i ran this command and it tells me dpkg: requested operation requires superuser privilege when theres only one user which is me and im sure im administrator

---

### Post by snowpine on 2009-04-15
> **blandino123 said:**
> hey thanks for the reply. when i ran sudo apt-get update it started downloading some packages and then i get this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem...i ran this command and it tells me dpkg: requested operation requires superuser privilege when theres only one user which is me and im sure im administrator

Try:

sudo dpkg --configure -a

---

### Post by blandino123 on 2009-04-15
dpkg: parse error, in file `/var/lib/dpkg/updates/0054' near line 1:
 field name `4ee2de117e9587bafc95afe4c8d0470b' must be followed by colon
 i get this error message.. and guys F it im thinking of just re-installing ubuntu since i dont have anything that i can lose

---

### Post by riza hylviu on 2009-04-15
hi
i am a noob too, but i have read something about upgrading ubuntu and  the most people think its better to make a new install and not upgrading. 
so you can try the ext4 filesystem too

---

### Post by bobbob1016 on 2009-04-15
> **blandino123 said:**
> ...i ran this command and it tells me dpkg: requested operation requires superuser privilege when theres only one user which is me and im sure im administrator

Just so you know, since you said you're new to Linux, you are *technically* NOT admin.  That is one of the things that makes Linux more secure.  Ubuntu is set up to keep you as a normal user, not an admin, and prompt you for your password before letting you do admin things.  When you enter your password, you are admin ONLY in that window/program.

To help you with your problem, I think it might be that you went to 9.04, Jaunty.  Jaunty isn't out yet, almost but not yet.  It's beta software now, and isn't expected to be 100% stable yet, although it should be close.

Yes you can upgrade the beta to the final version, so once you get it stabilized, and working, you don't have to reinstall or anything to get full 9.04.

Edit:  Also, please don't do a post with all caps, and never with something like "OHH EMM GEE", a lot of people will go right past your post.

---

### Post by blandino123 on 2009-04-15
> **bobbob1016 said:**
> 
Edit:  Also, please don't do a post with all caps, and never with something like "OHH EMM GEE", a lot of people will go right past your post.

alright lesson learned XD!

i know that 9.04 should be here 100% in a couple of days but for know i guess ill just back up to 8.10 and chill while it gets better.also ive been thinking of installing kubuntu because it looks alot more user friendly..any advise? keep ubuntu or upgrade to kubuntu?

---

### Post by Linux&amp;Gsus on 2009-04-15
> **blandino123 said:**
> also ive been thinking of installing kubuntu because it looks alot more user friendly..any advise? keep ubuntu or upgrade to kubuntu?

That's a matter of personal preference. What is user friendly for one person can be total useless for someone else.
Having said that, I personally prefer KDE and therefore run Kubuntu. Just try it, if you like keep. Otherwise use Ubuntu or Xubuntu or what ever else you like the best. It's your choice. ;)

Cheers,
L&G

---

### Post by blandino123 on 2009-04-15
> **Linux&Gsus said:**
> That's a matter of personal preference. What is user friendly for one person can be total useless for someone else.
Having said that, I personally prefer KDE and therefore run Kubuntu. Just try it, if you like keep. Otherwise use Ubuntu or Xubuntu or what ever else you like the best. It's your choice. ;)

Cheers,
L&G
 k thanks for the advise..oh and btw everybody i just reinstalled ubuntu..thats what makes this os so great its fast and simple WOOT

---

### Post by blandino123 on 2009-04-15
ok im typing this very fast cuz i dont want my pc to crash while i write this. before int he past when i used to use wubi i got trown off linux because my pc would just shutdown out of no where..as in  my pc just shut down ..no warning. now this just happened! WTF! this also happened to me last night while installing ubuntu which really scared me.i have a toshiba satelite L305D-S5881.this really scares the shirt out of me when it happens.so ANY HELP PLEASE

---

### Post by blandino123 on 2009-04-15
idk why before in the past when i used to use wubi i got trown off linux because my pc would just shutdown out of no where..as in my pc just shut down ..no warning. now this just happened! WTF! this also happened to me last night while installing ubuntu which really scared me.i have a toshiba satelite L305D-S5881.this really scares the shirt out of me when it happens.so ANY HELP PLEASE idk why this happens.only happens on ubuntu not on vista.HELP

---

### Post by Monotoko on 2009-04-15
Right, first thing to do is not panic, if you are duel booting and still have them both and vista isnt doing anything odd, your fine, you still have one....its just ubuntu, now we need to figure out the problem logically...what happens when it shuts down....does it reboot or just shutdown?

Also, have a look at your log (System menu > Choose Administration > System Log) and tell me if you see anything out of the ordinary at the time in which is happens, if you dont understand, post the output of your log of roundabout when it happens here.

Are you running Duel-boot or Wubi (Did you install from inside windows?)

---

### Post by blandino123 on 2009-04-15
> **Monotoko said:**
> Right, first thing to do is not panic, if you are duel booting and still have them both and vista isnt doing anything odd, your fine, you still have one....its just ubuntu, now we need to figure out the problem logically...what happens when it shuts down....does it reboot or just shutdown?

Also, have a look at your log (System menu > Choose Administration > System Log) and tell me if you see anything out of the ordinary at the time in which is happens, if you dont understand, post the output of your log of roundabout when it happens here.

Are you running Duel-boot or Wubi (Did you install from inside windows?)

no i completely got rid of windows. i used my whole hard drive for ubuntu.when i hit shut down..it just shuts down.when i restart it rrestarts. on both i get some words saying loading blah blah then i get the ubuntu thing loading and here i am

---

### Post by tripolitan on 2009-04-15
Sounds like a heat issue. Boot into Windows, see if the same happens. If it does, it is heat-related problem. If it does not, you may have bum install of ubuntu. try re-installing.

Sounds like you have a laptop and a PC? Next time, please post your Ubuntu version and your PCs hardware.

---

### Post by tripolitan on 2009-04-15
> **blandino123 said:**
> ..when i hit shut down..it just shuts down.when i restart it rrestarts. on both i get some words saying loading blah blah then i get the ubuntu thing loading and here i am

sounds like it is working?

---

### Post by blandino123 on 2009-04-15
ok umm
here you go

toshiba satelite L305D-S5881. AMD Turion(tm) X2- Dual Core Mobile RM-70 Procesor 3 gb ram  2ghz 200 gb hard drive. i currently have northing but ubuntu on my computer.at least that what i think.when installing ubuntu i picked so that it uses all 200gb of my hard drive and im guessing it deleted vista because it automatically boots into ubuntu. i dont see why it can be a heat problem because when i used vista my pc went up to 220 F with no troubles (i ran on high power) and i havent used much of my cpu  ( as in get 100% cpu usage) ive installed ubuntu 2 times now today..first it was good but i installed 9.04 and it fukled up my ubuntu..so i desided to re install.

---

### Post by tripolitan on 2009-04-15
220F??? that is HOT, are you sure you're getting the correct temperature value?
What did you install before the (beta) 9.04 that worked? was it 8.04 or 8.10 by any chance?

---

### Post by blandino123 on 2009-04-15
> **tripolitan said:**
> 220F??? that is HOT, are you sure you're getting the correct temperature value?
What did you install before the (beta) 9.04 that worked? was it 8.04 or 8.10 by any chance?

no no 9.04 did not work thats the reason why i reinstalled 8.10 and it was 8.10 before i installed 9.04 (confusing aint it:p)

---

### Post by William Anderson on 2009-04-15
hi,

when you say "shutdown" do you mean that the power to the computer suddenly went off, or did the os actually shut down, with the status bar and all?  

first thing i would do is run memtest86 and make sure that there was no problems with bad ram. to do this, when booting press escape at the grub prompt and select memtest86 from the boot options.

another possibility that has happened to me with two Toshiba laptops that i owned in the past is that the power socket is separating from the mother board. coupled with a dead battery this would cause the power to the laptop to just go off when the power cord is moved. short term fix is to hold the power cable in a way that assures the socket connects to the power contacts on the motherboard, but ultimately the socket will need to be re-soldered.

hope this helps,
William

---

### Post by roger_1960 on 2009-04-15
Hi

I had a similar problem when installing ubuntu on an old Toshiba laptop (S1800-514)  It was an overheating problem - the fan did not seem to run until after the install.  I solved it by taking the case off the laptop whilst installing - its OK now!

---

### Post by tripolitan on 2009-04-15
But is your system working now? and did you know that 8.04 is supported longer than 8.10? and that you should always look for the "stable" version of any Linux flavour? :)

---

### Post by blandino123 on 2009-04-15
:(i run 
toshiba satelite L305D-S5881. AMD Turion(tm) X2- Dual Core Mobile RM-70 Procesor 3 gb ram 2ghz 200 gb hard drive
 
i installed ubuntu 8.10 last night and it was pretty perfect.during install my computer crashed(crashed as in just shut down out of no where..idk how to describe it any beter just shut down all off) i waited a couple of minutes retryed the install and it went well. i installed the updates until i went online and read about "ubuntu 9.04" i was like wooooooo. i used the command to get to the thing to download and install automatically.it begun. and i feel as sleep XD!i wake up in the mornning and my pc is off.i didnt know whether my pc crashed or was set to turn off after a couple of hours so i didnt worry.if u lookat some of my posts i describe how my 9.04 just didnt work.i got error messages while openning almost every program which didnt allow me to open them. i tryed redoing the install and it just told me i was missing some things. after putting yes the install just crashed. it gave me a command i put it in terminal..gave me another..gave me another...until i decided to just re install ubuntu 8.10 with the disc i had made ( hached checked it after download and checked it after burn) so the disk was good.i reinstalled and it went well. my pc crahsed a couple of times but i didnt mind. just posted on here to see if i could get some help.then i was on Gfire irc chat and they where telling me how i should try to install 9.04 again that it might work so i said heck why not?i then proceded to start the install. it was downloading  and i left my room for about 30 minutes.i come back and my pc is off. ii just said WTF!i tryed to start up my pc but it got to the loading screen and then my screen turned black.i said OMFG! and i booted into my cd. when i picked install ubuntu my pc froze for 5 minutes and crashed.i waited 10 minutes turned my pc back on (normal boot) and again it freezed and crashed... i waited booted from disc and again frezed and crash. ok now i just reinstalled my vista and pc is working fine. BUT IM NOT SATISFIED WITH VISTA I WANT TO BECOME A UBUTER!!!! I AM TIRED OF WINDOWS! (LOL) i dont know if anyone is actually going to read tru that or is even gunna help me but i sure hope someone does! thnks

---

### Post by Monotoko on 2009-04-15
A lot to take in there, not gonna critisize, but more people may read if you use paragraphs.

Anyways, onto your problem. Ubuntu 9.04 is still a beta version, you are aware of that arnt you? I would just keep with 8.10 for now, 8.04 is also a long term release and is still going to be supported for a few years yet, because of that, it will be the most stable version (8.04 was definatly the most stable version iv had this computer run)

Also you say it just shuts down...have you checked your log to maybe find out why this is? Have you ever had this problem in Windows, it could be that your computer is overheating. Also check the system logs (System -> Administration -> Log file viewer) see if you find anything of suspicion around the time it closes down.

---

### Post by blandino123 on 2009-04-15
> **Monotoko said:**
> 
Also you say it just shuts down...have you checked your log to maybe find out why this is? Have you ever had this problem in Windows, it could be that your computer is overheating. Also check the system logs (System -> Administration -> Log file viewer) see if you find anything of suspicion around the time it closes down.

im not running ubuntu..i reinstalled vista just to be able to use my computer XD! but the shutting down only used to happen with ubuntu with some stupid reason. if i can get this solved i can go back to ubuntu for EVA! :D

---

### Post by Vaphell on 2009-04-15
9.04 is in beta stage, if you are inexperienced user you should wait a little.
upgrading versions breaks stuff from time to time, it's probably better to do a fresh install - 8.10 and 8.04 being your options. Upgrade to Jaunty seems to repeatedly ruin your installation. BTW why is your computer crashing all the time? :D

i personally use 8.04 (long term support version) and it's rock solid for me. I don't like tinkering that much to repeat it every 6 months :D

consider leaving some small windows partition just in case. Sometimes you want to use something that is known to cause problems in linux and booting to win can save a lot of time. Also if you like to play games, dual boot is more reliable option.

---

### Post by Monotoko on 2009-04-15
I would advise trying 8.04, and seeing what happens, just make a duel-boot system between Ubuntu and Vista (I used to do that with XP, still need MS for some things lol....regret taking it off and may end up needing it again for a game sometime soon)

Ubuntu gives you the option to just shrink your Windows partition and install ubuntu to the free space, try that.

---

### Post by maheshasolkar on 2009-04-15
Spontaneous shutdowns sounds like a weird problem to me. Are you sure you were connected to AC power when you did the installation? If the battery was running out mid installation, that could render the system in a bad state.

---

### Post by blandino123 on 2009-04-15
> **maheshasolkar said:**
> Spontaneous shutdowns sounds like a weird problem to me. Are you sure you were connected to AC power when you did the installation? If the battery was running out mid installation, that could render the system in a bad state.

laptop was conneccted and good. (all 3 lights where on ) charge,batery,power

---

### Post by blandino123 on 2009-04-15
> **Vaphell said:**
> 9.04 is in beta stage, if you are inexperienced user you should wait a little.
upgrading versions breaks stuff from time to time, it's probably better to do a fresh install - 8.10 and 8.04 being your options. Upgrade to Jaunty seems to repeatedly ruin your installation. BTW why is your computer crashing all the time? :D

i personally use 8.04 (long term support version) and it's rock solid for me. I don't like tinkering that much to repeat it every 6 months :D

consider leaving some small windows partition just in case. Sometimes you want to use something that is known to cause problems in linux and booting to win can save a lot of time. Also if you like to play games, dual boot is more reliable option.
i know but i figured.. use wine for everything from windows that i might need and use google for tother stuff that wine doesnt support XD! by the looks of it 8.044 is my best choice of ubuntu for now

---

### Post by Monotoko on 2009-04-15
Nothing against WINE, but it doesnt run some games half as good as Windows, Sims just as an example (as i found out earlier today) so i would keep Windows and duel-boot

---

### Post by hockeyhead019 on 2009-04-15
yea just to add onto the whole WINE comment if you play any intense game with a high frame rate it's better to stick to windows as some of the games become quite a hassle to use wine with....

as to your problem i honestly don't know what to tell you as this is the first time I've heard of truly random shut downs as others have said I would stay away from the beta until it's officially released

and please try and make a huge post like that a little more split up haha as it makes it soooo much easier for everybody else to read :D

---

### Post by paradigm2 on 2009-04-15
> **blandino123 said:**
> :(i run 
toshiba satelite L305D-S5881. AMD Turion(tm) X2- Dual Core Mobile RM-70 Procesor 3 gb ram 2ghz 200 gb hard drive
 
i installed ubuntu 8.10 last night and it was pretty perfect.during install my computer crashed(crashed as in just shut down out of no where..idk how to describe it any beter just shut down all off) i waited a couple of minutes retryed the install and it went well. i installed the updates until i went online and read about "ubuntu 9.04" i was like wooooooo. i used the command to get to the thing to download and install automatically.it begun. and i feel as sleep XD!i wake up in the mornning and my pc is off.i didnt know whether my pc crashed or was set to turn off after a couple of hours so i didnt worry.if u lookat some of my posts i describe how my 9.04 just didnt work.i got error messages while openning almost every program which didnt allow me to open them. i tryed redoing the install and it just told me i was missing some things. after putting yes the install just crashed. it gave me a command i put it in terminal..gave me another..gave me another...until i decided to just re install ubuntu 8.10 with the disc i had made ( hached checked it after download and checked it after burn) so the disk was good.i reinstalled and it went well. my pc crahsed a couple of times but i didnt mind. just posted on here to see if i could get some help.then i was on Gfire irc chat and they where telling me how i should try to install 9.04 again that it might work so i said heck why not?i then proceded to start the install. it was downloading  and i left my room for about 30 minutes.i come back and my pc is off. ii just said WTF!i tryed to start up my pc but it got to the loading screen and then my screen turned black.i said OMFG! and i booted into my cd. when i picked install ubuntu my pc froze for 5 minutes and crashed.i waited 10 minutes turned my pc back on (normal boot) and again it freezed and crashed... i waited booted from disc and again frezed and crash. ok now i just reinstalled my vista and pc is working fine. BUT IM NOT SATISFIED WITH VISTA I WANT TO BECOME A UBUTER!!!! I AM TIRED OF WINDOWS! (LOL) i dont know if anyone is actually going to read tru that or is even gunna help me but i sure hope someone does! thnks

Very weird.  I wonder if the issue is temp related?  Install speedfan or something like Notebook Hardware control under Vista and see what temperatures you are getting for the CPU and hard disk.  Even if it is okay under windows, this doesn't necessarily mean it is the same in linux although it is more likely.

If you decide to try linux again I would shut the computer off first for several hours prior to the install.  Once installed, shut it off again for a few hours.  Then reboot and try to install the sensors like lm-sensors with the gui applet "sensors-applet" (This will show you on the menu bar the temp of your cpu and hdd) in order to monitor the temp situation in the laptop.

Laptops are notorious for getting too hot so whenever weird intermittent behaviour starts, it is one of the first things I check.

---

### Post by hikaricore on 2009-04-15
So I've merged your mess of threads on the same topic strewn randomly across the forum into one bit mess.
Please in the future stick to one thread per topic and don't repost it all over the forum just because no one replies in 5 minutes.

---

### Post by Linux&amp;Gsus on 2009-04-16
> **blandino123 said:**
> i dont see why it can be a heat problem because when i used vista my pc went up to 220 F with no troubles...

Forgive me for saying this, but I kinda doubt that. 220F would be just over 100C? Your CPU would be fried and in hardware heaven at this point. If it survived it wouldn't be a big surprise to me if the computer act *funny*.
AFAIK a BIOS has a setting at which temp to shutdown a computer to prevent hardware damage, and I thought it's usually somewhere set around 75C which should be ~170F.

I might be wrong, but as far as I remember a CPU doesn't survive boiling temperature.


Boiling greetings,
L&G

---

### Post by tripolitan on 2009-04-16
As I mentioned earlier, your laptop is overheating. If you don't believe me, re-install Windows and see how long it lasts. If it does not crash, keep windows.

---

### Post by blandino123 on 2009-04-16
ok guys i think im sadly going to have to say bye to ubuntu. i dont understand this. i installed ubuntu 8.04 on a flash drive tested the memory both times.before install to flash drive and after. during install after 20% of the install i think my pc shut down. i then let it cool down just in case its a heat problem.(waited 20 minutes) and tryed the install again. crashed again. so idk i think its just my pc..i hear a strange noise inside my laptop when it does shut off but i guess my laptop is jsut sadly not compatable with ubuntu ](*,) *cries* but thanks for all the help guys.

p.s. sorry for my mess of threads. i was desperate for some help XD
and no these crashes NEVER happen in windows -_-

---

### Post by tripolitan on 2009-04-16
I'd hate to say it but you may be in complete denial over this issue.
Your laptop registers 220 on the Fahrenheit scale and shuts down (as it is designed to do) and you keep blaming something else...

Reinstall Windows. When your laptop crashes again, take it to your nearest Toshiba service center, they'll replace the fan or motherboard and it will work fine after that. Then you can check out Ubuntu again with the flash drive. Good luck!

---

### Post by blandino123 on 2009-04-16
> **tripolitan said:**
> I'd hate to say it but you may be in complete denial over this issue.
Your laptop registers 220 on the Fahrenheit scale and shuts down (as it is designed to do) and you keep blaming something else...

Reinstall Windows. When your laptop crashes again, take it to your nearest Toshiba service center, they'll replace the fan or motherboard and it will work fine after that. Then you can check out Ubuntu again with the flash drive. Good luck!


acutally YES! i figured it out its exacly that! while trying to install linux mint (i thought another distribution might work XD) my pc shut down... i felt the bottomof my laptop and it was hot. but what i dont understand is that.. it wassent scorching hot. this hot that it was is the type of hot that my computer usually runs on while using windows (when not running highly demanding programs or running in high power) so what i think is that linux sets my pc to shut down at a sertain tempeature which is low? i guess? but this still doesnt explain for the crashes during the install?i booted into linux mint with a usb which automatically sends me to the desktop with the option to install..i get to the desktop...BANG 30 seconds later shutdown XD!..

ps..
windows can run at extremely high tempeatures (just when i put it on high performance the default temp is 200F and when i use a high demanding game it has gone to 220-235F without a single problem) -_-. i dont get crashes in windows. actually it has never happened to me. idk ubuntu just doesnt like me..a couple months back i installed ubuntu with wubi and guess what happened?!! yeah..exacly.. (ubuntu is mean!!!!!) XD

---

### Post by blandino123 on 2009-04-16
> **Linux&Gsus said:**
> Forgive me for saying this, but I kinda doubt that. 220F would be just over 100C? Your CPU would be fried and in hardware heaven at this point. If it survived it wouldn't be a big surprise to me if the computer act *funny*.
AFAIK a BIOS has a setting at which temp to shutdown a computer to prevent hardware damage, and I thought it's usually somewhere set around 75C which should be ~170F.

I might be wrong, but as far as I remember a CPU doesn't survive boiling temperature.


Boiling greetings,
L&G

yeah i have called toshiba over this issue they told me.." that is completely normal specially if your running in high performance"


ok look guys the normal running tempeature under energy saver in windows is about 160F which by loking around the webz seems to be the point where ubuntu shuts down my computer which i find rather stupid? i dont know if its ubuntu or if its in my bios  because while installing ubuntu my pc shuts down and i say my pc mus tbe running around 180 or so. so if anyone could tell me how can i edit this?

---

### Post by tripolitan on 2009-04-17
No linux distro shuts down a PC due to heat during install. That is the job of BIOS and yes, Ubuntu is evil and evidently, does not like you. :(

I have never ran Ubuntu from USB but just for kicks, try booting off the USB but select noacpi option, if you can. Its a shot in the dark...

If you happen to re-install windows, please come back (to this thread) and post your results.

---

### Post by blandino123 on 2009-04-17
> **tripolitan said:**
> No linux distro shuts down a PC due to heat during install. That is the job of BIOS and yes, Ubuntu is evil and evidently, does not like you. :(

I have never ran Ubuntu from USB but just for kicks, try booting off the USB but select noacpi option, if you can. Its a shot in the dark...

If you happen to re-install windows, please come back (to this thread) and post your results.

hey..last night i said.. since ubuntu doesnt like me? why not try another distribution but similar to ubuntu? so i did.im currently running linux mint felicia. i havent had any abrupt shut downs...but i need some sort of add on or twek to tell me that tempeature of my pc..just in case i do get a shutdown i can see the tempeature at which this happens

---

### Post by blandino123 on 2009-04-18
ok guys i have to say thanks to everyone that reponded in this thread. i have kind of repaired it by formating my HDD..cleanning my fan thingy (it did have some dust bunnies in it).. then reinstalling ubuntu 8.04.after a few bugs i desided to install 8.10 which was a great choice. all my 8.04 bugs are gone now. i installed a cool little program called GKRELLM which tells me everything from cpu usage to tempeatures which is AWESOME! i realised that vista fails hard. vista ran my system at 160-230F while ubuntu runs my system at 100-150F. i love ubuntu and im here to stay now! UBUNTU IS FTW!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:D:D

---

### Post by tripolitan on 2009-04-20
Congrats! 100-150 sounds reasonable, the high temp is probably due to high demand (from the other OS) keep blowing out the dust once in a while. Thanks for the closure. :]

---

