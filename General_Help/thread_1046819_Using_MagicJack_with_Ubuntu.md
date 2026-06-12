---
title: "Using MagicJack with Ubuntu?"
date: 2009-01-21
forum: General Help
---

### Post by crazeepingu on 2009-01-21
Hi I would like to ask the community if any one could get the MagicJack to work on Ubuntu? If you did can you please let me know how did you get it to work? I am a new comer to the world of Ubuntu and Linux so would appreciate if someone can guide me to use this usb based MagicJack. Just for some one who does not know what is magicjack here is the website: [www.magicjack.com](www.magicjack.com)

Thanks in advance and looking forward to the responses...

---

### Post by fastpakr on 2009-02-03
I'm looking for the same thing.  So far, no luck with VirtualBox or Wine.

---

### Post by Jbunker on 2009-04-22
> **crazeepingu said:**
> Hi I would like to ask the community if any one could get the MagicJack to work on Ubuntu? If you did can you please let me know how did you get it to work? I am a new comer to the world of Ubuntu and Linux so would appreciate if someone can guide me to use this usb based MagicJack. Just for some one who does not know what is magicjack here is the website: [www.magicjack.com](www.magicjack.com)

Thanks in advance and looking forward to the responses...
I installed the magicjack in windows vista, and I have skype installed on the Ubuntu Partion. You can go to skype click on audio settings and skype recognizes the usb handset provided by magicJack. Just select the option and your magic jack with a cordless headset will work on skype dial tone and all. Remember this, when your on the Net yur on the net. Telephone, Tv, radio, data, all hooks to the same pipe line, (the backbone) usually hits fiberoptics in its path providing high speed. Since Ip phone calls are low quality grade audio, it takes up very little bandwith.. I will working on code fix to make the magic jack work on ubuntu OS, So join this thread and we can do it together the Ubuntu Way.  I think the answer is within the skype code written for Ubuntu.

Ping me now and lets get started with ideas. YES WE CAN make this happen

---

### Post by Cybie257 on 2009-04-22
I was reading a forum where the inventor of Magic Jack was replying to other users. 

He is working on a Linux version as of right now. He has had high demand and promises to have something within (can't remember the exact) a certain timeframe. So, until then, looks like the Skype idea might be something. I'll have to give it a try. 

As for Vbox, I never had luck getting it to work, but was able to with VMWare workstation. It seems that VBox really lacks in proper USB support, but it's getting better as time goes by from what I see. Overall, I like the way and speed that VBox works compared to VMWare, although VMWare has had lots of time, money, and effort put into the research and development, so certain areas are definitely ahead of everything else. 

-Cybie

Added: 
> Mac OS X support has been added to magicJack. Could Linux compatibility be coming down the pipe?

DB: Yes, and because the of the similarities between the Mac and Linux OSes, we should be able to support Linux fairly soon.

MORE Added:

> April 21st, 2009
Linux compatibility: Mac and PC users have been using magicJack for some time now, but Linux has been left out in the cold&#8211;but not much longer. According to Borislow, Linux compatibility should be available &#8220;3rd quarter of this year.&#8221;  This addition will be available to both current and new magicJacks.

---

### Post by tubunu on 2009-04-23
I installed Ubuntu 9.04 today. Magic Jack was plugged in because I'd forgotten to remove it. I swear when I popped in the live Jaunty CD I saw Magic Jack icon on my Ubuntu desktop and when I picked up the receiver I heard the tone. I was so happy it finally worked, I decided to install Jaunty as soon as possible. To my surprise, after installing the system Magic Jack is no longer recognised. Can anyone confirm that MJ works under live CD? That would be something, and maybe the issue could be solved?

---

### Post by motiboosh on 2009-04-24
With Ubuntu 9.04, when magicjack connected:
I get the dial tone and it's icon is mounted on the desktop, but can't make the calls. Please help!

---

### Post by tubunu on 2009-04-24
I, on the other hand, cannot mount magic jack at all. How did you mount it on the desktop?

When inserted it says USB Drive (in Places/Computer), right click and Mount volume: "Unable to mount location" :(

---

### Post by tonyps on 2009-04-24
Which version of Skype did you get installed and if you would not mind, how did you do it? I am a first time user with Ubuntu and would dearly like to get Skype going..
Thanks..
tony  (tonyps@verizon.net)

---

### Post by motiboosh on 2009-04-24
I only installed Ubuntu 9.04, which made no difference with or without Skype version 2.0.0.72-1_i386.deb.

---

### Post by sports fan Matt on 2009-04-24
This would be great if this is true with the developer of MJ listening...

---

### Post by natrixgli on 2009-04-24
Hi, Guys:

On VoIP devices the dial tone is usually produced by the device itself for no other reason than to make the user feel more like they're using a traditional telephone.

So it's possible the MJ device was simply playing back an audio file.

Cheerio,

-n8

---

### Post by sTpny on 2009-05-17
I'm working on getting my MagicJack to work through VirtualBox-bin. So far, no luck, but I think I'm getting close, and I have heard that some people have had success with this.  If I can figure it out.. I'll post the solution here, and also upload a video tutorial to youtube. If any of you figure it out before me, please do the same. 

Also.. No, It doesn't work with the liveCD. It just pretends like its working. Dial Tone, but nothing else. 

At the moment, I've had to make a dedicated windows system for my MagicJack, which really sucks, but only because windows really sucks. Good luck to everyone trying to crack this egg, and thumbs down to those who have and haven't shared the details of how. Shame on you!

---

### Post by coskierken on 2009-05-18
I have got it to work in VMware Workstation(64) with an XP(32bit) virtual.  I tried Vista 64 in Workstation and it did not seem to work as well.  The trick is to unmount the magicjack device when it shows up on the desktop.  I told a buddy in Orlando to do this in Virtualbox and his worked, but it was choppy.  VM Workstation code is probably tighter.  Granted, I am 64 Jaunty with specs below and his is AMD64 X2.  When you run VM Workstation, it will tell you the device must be released, so you just answer yes and keep going.  Just make sure your USB is active upon start of running the XP virtual.  Now, it will take up resources while running a virtual in Jaunty.  One of my 4 cores is always cycling to 100% but it does not bother me.  I think this is more due to VM worksation than Magicjack.  Good Luck!

The reason some are hearing a dialtone through Skype is the USB audio device of Magicjack.  You can pick it in Skype as the audio source and use the handset.  I use the Logitec Wireless headsets with mic and they are great for this.  I am not chained to the desktop.  I have not tried the bluetooth in Jaunty yet.

_________________________________________________

MSI G45M mb/8g 1066 ram/Q9550 OCed to 3.4Ghz with Noctura NG-C12P HSF/WD 640 black HD 7200rpm-32M cache/Hitachi 1Tb hd 7200-16M cache/Nvidia GTS250 1G DDR3/AeroCool Case (great case)/ Tuniq 550W PSU.

---

### Post by hawkiye on 2009-07-23
Any updates on this? I tried to load VMware player with no luck, it put it in the synoptic packages so I installed and still can't find where to install so I can use it. I even tried that Chrysaor script and it hung asking me where to put the binary files...sigh

 Can you tell I am a complete newb to ubuntu? However I am determined to be MS free ASAP. I love ubuntu so far but just haven't had the time to dig in to cut the learning curve like I need to. 

Anyway this is my first post and would love to get magic jack usuable. I would use ekiga or twinkle but MJ is cheaper and I still have some windows boxes I can use it on, till that glorius day I don't need them anymore. 

it amazing some enterprising geek has not created a magic jack equivelent for linux there is a nice little corner of the market ripe for the picking

---

### Post by redxine on 2009-07-29
They said they'd have Linux support a year ago, and I'm tired of waiting. So I set out to get it working one way or another. The method I have found so far is completely against their TOS, but it works. The idea is to sniff the SIP credentials from the card durring the registration process.

First, you'll need a Windblow$ box to register with. Follow the usual instructions to get the magicjack up and running. After you register, download [This utility]("http://revolution.hackthisbox.com/joo/component/content/article/1-latest-news/39337"), extract, configure, and run to get the SIP credentials.

Once you have all the goodies, time to relieve your suffering and switch to ubuntu. I got it working with wengo phone so far, so you'll need to install that. Then it's a simple matter of plugging in the sip information. The server should look like proxy1.majorcity.talk4free.com (Like proxy1.Atlanta.talk4free.com) - Be sure to check the port numbers - the proxy uses 5070. If registration is successful you should be able to place calls nearly immediately. If you want you can use the dongle for audio but dialing numbers doesn't work.

---

### Post by t4thfavor on 2009-07-29
After you sniff the SIP creds you could then plug them into ekiga, and just use the magic jack device as an audio device. Then you could make and recieve calls from the softphone, but using a regular phone as the "headset" device.

This also means you could set up an asterisk server to register to the magic jack servers and use it as a "trunk". Pretty cool technology, even if its not intended to work that way.

---

### Post by HappyFeet on 2009-07-30
Just have a dedicated PC for magic jack. The rest is easy.

---

### Post by crwebcraft on 2009-08-04
> **sTpny said:**
> I'm working on getting my MagicJack to work through VirtualBox-bin. So far, no luck, but I think I'm getting close, and I have heard that some people have had success with this.  If I can figure it out.. I'll post the solution here, and also upload a video tutorial to youtube. If any of you figure it out before me, please do the same. 

Also.. No, It doesn't work with the liveCD. It just pretends like its working. Dial Tone, but nothing else. 

At the moment, I've had to make a dedicated windows system for my MagicJack, which really sucks, but only because windows really sucks. Good luck to everyone trying to crack this egg, and thumbs down to those who have and haven't shared the details of how. Shame on you!

I have MagicJack running.

1) Read the User Man, pg.21, you will need to install a couple of other pkgs before virtualbox.  Use Synaptic to download and install them.
2) Get Sun Microsystems' Sun VirtualBox Ver. 3.0.2. or higher [http://www.virtualbox.org/](http://www.virtualbox.org/)  Save and then use GDebi to install it.
3) Launch VirtualBox and setup a new machine, you will need a valid install disk for either windows or mac. Read the manual.  
4) After installing either windows or mac on the virtual box, you will need to shut it down so you can access the settings options.  Right click on the machine name and select settings.
5) Plug the MagicJack in so the system sees it and then select USB Filters and then select the second one down, autoconfigure using device settings, and save.  Eject MagicJack using Places > Home Folder, then click the the eject button on MgicJack when it goes away remove MagicJack.
6) Restart your virtual machine, and after everything boots up, plug in MagicJack.  It may show up on your workspace desktop, until virtualbox tells the system to pass control of it.  It will then disappear and show up in the virtualbox.
7) Click on devices > USB Devices > Tick on Tigerjet Network, Inc 
8 ) The MagicJack will do it's download and then initialize.
9) You may need to allocate a little more RAM but not very much.  Make small adjustments start out with the minimum required for the system you installed and then add a little at a time until you reach a happy point.  Too much and your base system will hit the swap so hard you'll think you have a comode-door 64.

Hope this helps, and I am making these assumptions and because it's what I am using:
Host: Ubuntu 9.04 Juanty
RAM: 1.256GB
HD: 150GB  Not really too important just make sure you have enough to give the virtualbox and not hobble your real system.
CPU: 1.6GHz or as many multicores as you can afford.  I would not recommend anything slower than 1.6GHz 32bit, or you are likely to have audio quality problems
144 12oz cans of Mt. Dew.

Cheers!

---

### Post by HtmlGifted on 2009-08-11
hay all this forum is very use full. but I am new to ubuntu.. very new.. and have switched completely.. no windows duel boot for me.. Windows.. blows...  any ways... Have my magic jack plugged in to my tower but does not want to show up as an icon on the desk top. when I tried the wubi version it showed up.. what am i doing wrong.........


Remember Have very little cmd line use in root terminal.. like to cmd lines thats about.. It...


Help..

Thanks all.

---

### Post by liquidbraino on 2011-01-19
[QUOTE=crwebcraft;7730626]I have MagicJack running.

1) Read the User Man, pg.21....

What user manual?
Where can it be found?

---

### Post by liquidbraino on 2011-01-19
[QUOTE=crwebcraft;7730626]I have MagicJack running.

1) Read the User Man, pg.21....

What user manual? (ubuntu user man? MJ user man?)
Where can it be found?

---

### Post by liquidbraino on 2011-01-19
> **crwebcraft said:**
> I have MagicJack running.

1) Read the User Man, pg.21, you will need to install a couple of other pkgs before virtualbox.  Use Synaptic to download and install them.

Cheers!

Thanks for the information! But - two questions:

What user manual would that be (Ubuntu? Magic Jack?)
And where would I acquire it?

Superthanks! :)

---

### Post by liquidbraino on 2011-01-19
> **Jbunker said:**
> I installed the magicjack in windows vista, and I have skype installed on the Ubuntu Partion. You can go to skype click on audio settings and skype recognizes the usb handset provided by magicJack. Just select the option and your magic jack with a cordless headset will work on skype dial tone and all. 

I tried this - it didn't work. I don't see any "audio setting" in skype. I see "options" and under "options" it says "sound devices". Under Microphone it says: "pulseaudio servere (local)" and for says the same thing under "Speaker" but doesn't allow for any other options. I'm using Skype Beta 2.1 for Linux.

---

### Post by liquidbraino on 2011-01-19
> **Jbunker said:**
> I installed the magicjack in windows vista, and I have skype installed on the Ubuntu Partion. You can go to skype click on audio settings and skype recognizes the usb handset provided by magicJack. Just select the option and your magic jack with a cordless headset will work on skype dial tone and all. 

Tried this. Doesn't work - I didn't see anything that said "audio setting". I saw "options" and then "sound devices" in that & "mic" plus "speaker" under that - but the only option available for each is "pulseaudio server (local)". It doesn't say anything about Magic Jack.

---

### Post by CR4ZYC on 2011-02-11
Seems like no body is interested in this any more.
Instructions were posted 2 years ago and no ... success stories....????:confused:

---

### Post by TBABill on 2011-02-11
No but NetTalk looks promising. No OS needed! Plugs right into the router so you don't even have to have a computer powered on to use it. No more ads, no more accidentally closing the app. I'm thinking hard about getting it myself and costs just a bit more (like $79?). Can't recall but looks great for Linux users.

---

### Post by liquidbraino on 2011-02-12
I just switched to Skype. 
Problem solved.

---

### Post by williamts99 on 2011-02-12
> **CR4ZYC said:**
> Seems like no body is interested in this any more.
Instructions were posted 2 years ago and no ... success stories....????:confused:


It seems that previously you could extract your SIP password and make it work with any SIP compatible softphone.  They changed the way their software works, and the old methods do not apply any more.

I have been using Google Voice and it works perfectly, no need for MJ.  \ I have a friend that uses MJ and has nothing but problems, and that is on the days that it works.

---

### Post by CR4ZYC on 2011-02-12
Thanks for the info,  I might just have to switch too! :(

---

