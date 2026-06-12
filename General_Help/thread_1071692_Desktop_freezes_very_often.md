---
title: "Desktop freezes very often"
date: 2009-02-16
forum: General Help
---

### Post by mikedmor on 2009-02-16
I hope im in the right place to post this.

for the past week i have been on [https://answers.launchpad.net/ubuntu/](https://answers.launchpad.net/ubuntu/) for the last week trying to get support on this problem and they have not been any help at all.

about a year ago i installed ubuntu on the same system and it ran perfectly, i stopped using it though because of the work it took to maintain it. Just recently i decided to get back into it and have noticed some MAJOR improvements, but as you may have guessed my pc is now upgraded since then and i keep having a problem where it freezes very often.

most of the time these freezes occur when i running firefox but it has happened outside of firefox on occasions, i have tried checking to see if anything was taking up all my resources as i was told to on launchpad.net and nothing was taking up anything more then 1% and that was the resource monitor itself. 

im hoping to get some help here so i can really fully migrate my desktop over to ubuntu (ie get rid of windows) since i have it now completely on my laptop with no problem.

I am duel booting with windows vista ultimate, windows 7 and Ubuntu at the moment and it is all setup to work using windows boot manager. from there i can boot into GRUB and start Ubuntu. My system specs are this:

Processor: AMD Phenom(tm) 9950 Quad-Core Processor (4 CPUs), ~2.6GHz
Memory: 6.00 GB RAM
Hard Drive: WDC WD1001FALS-00J7B0
Video Card: NVIDIA GeForce 9600 GT
Motherboard: MSI K9N SLI-F V.2 (MS-7390-010)

i have tried to fresh install it 6 times and i know the cd isnt defected cause its the same one i used to install Ubuntu on my pc in the past week.

if you need any more information please feel free to ask. I really wanna migrate over to Ubuntu completely cause my windows vista is only the 30 day trial and i have to reinstall every thirty days, and windows 7 beta is only going to work up till april, unless i remove internet and i dont really wanna do that.

PLEASE HELP!!

-mike

---

### Post by HermanAB on 2009-02-16
Divide and conquer.  Eg, unplug the CDROM drive and see if it still freezes up.

Cheers,

Herman

---

### Post by mikedmor on 2009-02-16
THANK YOU for the fast reply first off

second that didnt work. it actually froze as soon as i got past the login screen. which reminds me it has never froze on the login screen its always after i login (i checked this by leaving my pc on the login screen for about a day and it still didnt freeze but as soon as i loged in and navigated in firefox for about 5 min it froze.)

also this is a new install, no addons, but i have updated using the update manager and i think i also use the terminal commands too.

sudo apt-get update
sudo apt-get upgrade

---

### Post by bobbob1016 on 2009-02-16
Are you using 64bit, or 32bit?  32bit can only handle 3 or so gigs (maybe 3.5 or 4).  It could be that when your PC tries using 1k more ram than it can handle, it freaks out.

By the way, this is true with most/all OSes, the only way I can see around it is if you somehow set a hard limit into the OS itself so it won't go past 3 gigs, but I have no idea how to do that.

---

### Post by mikedmor on 2009-02-16
that may be an issue. i am using 32bit. But this was never a problem in vista or XP. Does anyone have a work around? or another idea at what it could be?

by the way thank you bobbob1016 for your input.

---

### Post by mikedmor on 2009-02-16
OMG!!! OK OK OK!! IM ON MY DESKTOP AND THERE IS ABSOLUTELY NO FREEZING!!! NOTHING!!!

im not completely sure that taking out two of my 1GB ram sticks and leaving me with 4GB would do anything or has done anything but for the past 10 min i have been on my Desktop without freezing!

Ok OK well since i really really want my ram in my PC, although its not really needed its more of a bragging thing between my friends, does anyone know a work around to fixing this?!?!

THANK YOU SO MUCH bobbob1016!

if anything comes up and it does turn out to freeze i will let you all know, but in the mean time can i get a work around? i will be so happy to have this think working on my Desktop

EDIT: Ok nevermind... five min after posting this it froze... that was definatly the longest it went without freezing though... so it might be the problem... but it still froze so that makes me think its something. else... any more ideas? in the mean time i will try to run it with only 2GB of ram and see how well that works.


EDIT 2: Yeah no luck still freezes, but the freezes are taking much longer to happen and only seems to happen when i click a link in firefox (but im unsure if thats the main cause) If you have any other ideas please! let me know!

---

### Post by bobbob1016 on 2009-02-16
1st, OMG OMG OMG OMG does not help you.
2nd, Take out one more stick.  If that works then that is the issue.  Try installing Ubuntu 64bit.  There are various ways to keeping your data, and 64bit is a little different.  You need to get the amd64 debs, and everything to install.  OR you can keep the 3 gig of ram, either will work.

---

### Post by mikedmor on 2009-02-16
sorry i have just been trying to get this working for the past week now.. its been very very frustrating for me. 

but if you read the edits i posted it still didnt work. i got down to one stick of 1gb ram and still no luck. it seems to freeze after a longer period of time the more i took out but still no luck. And i would rather run 32bit than a 64bit. but now im almost positive its not ram because why would it still freeze when all that was in there was 1GB

---

### Post by Bonsanto on 2009-02-16
I had the same problem, and this forum didn't help. Well Try this.

1.- Do the mem test. to see if soem of your memory rams are broke, If they are buy news.

2.- Try updating the OS.

3.- Try enabling and disabling your SUPER ULTRA AMAZING video card. (I had problems with my Ati I disabled it and now OS works perfect) I can't play anything But the OS doesn't crash.

4.- Try uquitting the video card, and reinstalling all drivers.

---

### Post by bobbob1016 on 2009-02-16
Sorry, my eyes glazed over after the OMG's.  You could also try booting the LiveCD, if that doesn't freeze, then it could be either the HD or the Video Card.  But the HD could be ruled out with a memtest, I think.  And 64bit isn't too different, but if you haven't used Linux before, might want to wait a bit to get some experience, just in case.

---

### Post by mikedmor on 2009-02-16
Bonsanto: Thanks for the reply but 

1.) the ram i have is all new (as of a month ago)
2.) OS is completely up to date (as of 5 hours ago)
3.) Its a new install so no drivers are enabled or even downloaded and all the visual effects are set to "none"
4.) How would i go about doing that? and i will give it a try

bobbob1016: The LiveCD (i burned it myself, ordering one now) did freeze as well, but only in firefox) and i know its not a cd defect because its installed on my laptop just fine and i have never ran into any problems.

and about 64bit its not that i have not used linux enough to use it, i have been off and on linux for the past 5 years now. i know quite enough to get me around. its the fact that after doing my research on 64bit i came across that you cant run Flash in 64bit and that is a MUST have for me. i just would rather not have to deal with any of the limits. (or the download time to get it either)

---

### Post by Bonsanto on 2009-02-17
Quit your Graphic Card. Then restart.

---

### Post by 3rdalbum on 2009-02-17
Bonsanto means: Disable your graphics card driver, either by uninstalling it or by adding:

```
Driver     "nv"
```

to the bit marked Section    "Device" in /etc/X11/xorg.conf

Proprietary graphics card drivers are known to cause kernel panics (freezes).

A 32-bit operating system will not "freak out" when you have more than 4 gigabytes of RAM and it won't try to access more than what it can - it's a physical impossibility. So installing 64-bit Ubuntu, while it's a good idea, is not going to solve your immediate problem. Flash is available on 64-bit, just thought I'd clear up the misconception.

---

### Post by dj722000 on 2009-02-17
Well, one if its a quad core, then its 4 cores on one chip, not 4 cpu's. I'M pretty sure that is a 64 bit chip? Switch over to the 64 bit OS instead of 32 bit. This will help a few things.

1) Use all your ram. (32 bit only sees 3 maybe 4 gig) I think 64 goes up around 16 gig?

2) Get rid of all your errors. (Maybe, maybe not, it worked for me when updated to 64 bit because im using a 64 bit chip) Doesnt matter if WINDOWS has errors using a 32 bit on a 64 bit, these two OS are not each other, cant treat them like it is.

3) Update your firefox plug ins to match the 64 bit or you will have some issues. Search you will find it.(Like now)

4) Kind of doubt this one, but if you want the software, quit using alphas and such. Buy them. Might have an issue on your HDD cause of this, might not be setting up right. ULTIMATE is timing out and 7 is in alpha.

5) If its not the OS, then gut your hardware from your system. Start troubleshooting what the hardware conflict is. Put 1 in at a time and boot. If it passes, put another one in, go until it fails. Just because its new, doesnt make it good.

In my eyes, if your not gonna upgrade to 64 bit, then quit shoving 6 gig into. It doesnt see it anyways let alone use it. So how is this impressing your friends if you cant use it? Also on another note, ULTIMATE and 7 doesnt use the 6 gig either unles you have the 64 bit version. Again only 3 maybe 4 gig at most. Being a Quad Core you should be able to have 512 or 1 gig and the chip will do the rest. Are you sure your HDD is large enough with all this on there? Maybe your swap is running out?

---

### Post by mikedmor on 2009-02-17
well im not planning on using 64bit. And im only 17 years old and still learning i know that only about 3-4 gigs is used (NOW!) i found that out once i bought it. but it still shows up on the system and my friends dont know you cant use it. also i know that a quad core is 4 cores on one chip i just copied and pasted what the description was on the site. 

I will try the drive "nv" thing i have had some expirience with that.

i will come back with an edit explaining how it went.

EDIT: Nope, but it froze differently this time, instead of everything just locking up (ie no mouse movement, keyboard response, etc) all my apps froze, but i could move my mouse and type on my keyboard and move apps around, then it froze completely. so i guess its progress.

---

### Post by cariboo on 2009-02-17
I really would suggest you try a 64bit version, it may solve your problems. 64bit is really no different from 32bit during day to day operations. I'm runnng 32bit Intrepid on my media center and 64bit Jaunty on my main computer, and if you didn't know whch was which you can't tell the difference.

Jim

---

### Post by mikedmor on 2009-02-17
im really not interested in a 64bit system since i have always been on a 32bit.

What are the differences? im reall ynot interested... but i guess i could try. is there a way to install within a 32bit system? or do i have to download it? 

i might just end up waiting another half a year for a big update and try again then... untill then stick with my other two partitions. thanks for the help though guys.

---

### Post by yther on 2009-02-17
OK, I'm going to jump in here because I've seen some weird misconceptions being tossed around that I think I should try to clear up.

To OP:  First, I know your RAM is less than a month old, but it is possible for brand-new memory to have defects.  I would advise booting to a liveCD and running the memory test&#8212;not just for a few minutes, but like all night.  Set it to test ALL of your memory (I think you hit C when it starts and adjust the size), otherwise it will only do it in segments.  After it has made a couple of passes (with 6GB this will take a while), if you don't see any glaring red lines of errors, your memory should be good.  If you do see red error messages, then it is time to troubleshoot the RAM.  Shut down and remove all but one stick, then run the memtest again, let it do one or two complete passes, and move to the next one until you find the one (or more) sticks that are bad.

3rdalbum and dj722000 have good ideas as well.  You want to disable any fancy drivers (such as graphics, wireless) and take your system down to basics.  I do suggest changing to 64-bit version, though mainly for the purpose of using all your nice RAM; 32-bit will only ever use about 3.5 GiB (unless you do something called PAE, which I've never used) so if you keep running 32-bit you've wasted your money.  ;)  I'd suggest you get a 64-bit LiveCD and run from that for a bit, to see if your system is stable.

Another idea:  Next time you have one of these freezes, note what time your computer's clock says.  When you get control back, look through the files in /var/log ("messages" in particular) and see if you see error messages occurring at that time.  If so, google for them or post them here, as they may shed some light on what's happening.

Let us know any results from all of that!  :)

*Edit:  I take your point and sorry to join the folks nagging you about 64-bit.  Most likely, the only real difference you'd see is the slightly better performance if you use a lot of memory.  Other than that, I can't think of a pressing reason unless you want to use it as a troubleshooting step.*

---

### Post by Bonsanto on 2009-02-17
I had the same problem, I don't know How to help you.

---

### Post by mikedmor on 2009-02-17
well imma throw an idea out for grabs, could it be my wifi drivers? i am using the default ubuntu wireless drivers, never thought i needed to go out to get others because it worked just fine. i use to have the freeze problem on my laptop but that was maybe 2 months ago then i found out that my built in wifi card on my laptop was defected and wont stay connected so i use a usb wifi now and kinda think about it since i started using ndiswrapper i have not had any freezing. could it be the fact that ubuntu's built in wireless networking is defected? just a though! please let me know what you think. ask for a log file its really big. do you want me to just post it all here or make a link to a DL page for a TXT file?

EDIT: I just figured i would add what kind of Wireless adapter im using, Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01) - Received from Hardware Testing tool, also for 40 min no freezing after i right clicked and unchecked wireless. So does anyone know how i can remove Ubuntu's default wireless and instead replace it with ndiswrapper? i know how to use ndiswrapper the main question is completely disabling the build in wireless, or could this just be because i never bothered to install the correct/any drivers for my wireless card? and how would i go about installing these without ndiswrapper? thanks yther for the suggestion of disabling wireless. looking forward to your next post!

---

### Post by yther on 2009-02-17
Aha, we might be closing in on the problem!  I mentioned wireless because I always have trouble with it myself.  Intrepid has better support for my card than Hardy did, but I still find that if I am sending a lot of data (such as a torrent, or sending video files to my desktop over rsync) I will get a complete lockup sooner or later.  The whole system freezes and leaves me with CAPS LOCK and SCROLL LOCK blinking, not even the mouse works.  So, I have good reason to be suspicious of wireless drivers!

Disabling yours was a good idea.  Also, since you don't use the built-in card, permanently disabling the drivers from loading would be a good idea as well.  Now, exactly *how* to do that I can't say.  :(

The command "lspci" should contain a line about your built-in wireless card, and "lsusb" should find the USB one.  Then you'd need to find out which kernel module corresponds to the card you *don't* want to enable, and disable that module.

I have not needed to use **ndiswrapper**, but there's a [community help doc]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") about it.

---

### Post by mikedmor on 2009-02-17
well im almost positive that its the wireless now. Absolutely no freezing after over an hour. The flashing CAPS was a problem on my laptop when this occurred. but not on my desktop (could be the fact that i have a $80 gaming keyboard that uses two usb ports at once) but i still feel that its the same.

It did always seem to freeze up when i was within Firefox, which at first led me to believe it was a firefox issue, but that was soon gone when it started freezing at times as soon as i logged in, could be because it was checking for updates and updating my checkgmail program. But for my desktop the wifi card it internal, im sorry for the confusion i trailed off talking about my laptop that does use a usb wifi.

Ask for ndiswrapper i understand it very well and already have a backup on a flash so im going to install it either tonight or tomorrow, im going to have to find out about completely disabling ubuntu's built in wireless so back to the web.

Thanks alot yther for you help! It is greatly appreciated.

i will post again once i figure out the method of doing this for anyone else that may run into this problem, if anyone else already knows how to disable this please let me know.

---

### Post by mikedmor on 2009-02-18
Also i figured i would post the model of my Wireless card. that might give some aid to you guys. :-P 

D-Link DWA-552

Im still working on figuring out how to fix it. if anyone else knows once again please post!

---

### Post by pickboy87 on 2009-02-18
It sounds like the wireless drives. Keep us updated! :D

I would also suggest trying another version (i.e. 8.04) and seeing if that helps any. I know sometimes with certain distros I tend to have odd problems that weren't in the old ones. With 8.10 Firefox seemed to run slow and lag a bit with pages. 8.04 ran smooth and thats currently the OS I'm using now. It's worth a shot, and I know that formating and fresh installing can be a pain in the butt after a while (trust me, it took me about 10 or so installs with 8.10 beta to realize I should be sticking with 8.04 :P)

---

### Post by mikedmor on 2009-02-18
WELL IM GLAD TO ANNOUNCE THAT THE PROBLEM HAS BEEN SOLVED!

it turned out to be the drivers! disabling ubuntu's build in wifi could have been an option but i didnt wanna bother with that. but with a little research i found a solution that look legit (after a bit of modification of my own.)

Here is how i fixed it:

Download the driver for the card.

[http://www.dlink.com/products/support.asp?pid=531&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=531&sec=0#drivers)

Download the latest driver, 4.10 was the latest here, to your home directory, then extract them there.

Now in go to add/remove and install windows wireless drivers, now goto system->Administration->Windows Wireless Drivers

Run the app and then click install new driver, navigate to the drivers you downloaded from dlink, you want the file netathw.inf (NOT netathwx.inf, i think thats 64bit) and install it.

Reboot and enjoy!

Note: Its been 2 hours no freezing with working Internet using this method, so im guessing that thats it fixed! if anything comes up i will let you all know. Thanks for all the help!

---

### Post by Bonsanto on 2009-02-18
My provblem was with the video card hehehe :D

---

### Post by mikedmor on 2009-02-18
yeah that was my first guess. suprissing that the wifi card could cause the whole system to freeze. thats a new one for me.

---

### Post by greylander on 2009-11-19
Hi, I just posted this to another thread, but it is also relevant here.

I have a blank-screen lockup that occurs pretty randomly (avg. uptime of about a day).  This has started recently after installing an Atheros based wireless card.  In the other thread the the OP had discovered and already fixed this problem by installing the proprietary drivers (madwifi), which can be done with 

    System>Administration>Hardware Drivers.

So I have just activated the proprietary drivers myself, and will report back as to whether any crashes occur in the next few days.  Because of the direct correlation of problem starting shortly after installing wireless card, I believe odds are high.

EDIT: oops...didn't notice how old this thread was... anyway, the extra tidbit of info may help someone else searching for a solution to this problem.

---

