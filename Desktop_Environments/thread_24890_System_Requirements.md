---
title: "System Requirements?"
date: 2005-04-08
forum: Desktop Environments
---

### Post by aukar on 2005-04-08
Anyone can tell me about the minimum and recommended system requirements for Kubuntu for i386..?

Sorry guys if already posted.. I simply cannot find it in the Kubuntu site.

Thank! :wink:

---

### Post by bored2k on 2005-04-08
For an OK performance, I would say 700mhz processor with about 128mb ram should do good. You can get it to work on a lot lower machines, but for that I suggest lighter environments like XFCE or IceWM or Fluxbox.

---

### Post by Marcke on 2005-04-08
[QUOTE=bored2k]I suggest lighter environments like XFCE or IceWM or Fluxbox.[/QUOTE]

Is there a decent user-base when you have problems with these distro's?
And where can you download those?

Wannes

---

### Post by bored2k on 2005-04-08
[QUOTE=Marcke]Is there a decent user-base when you have problems with these distro's?
And where can you download those?

Wannes[/QUOTE]
 Chances are you're not going to have problems with them. Fluxbox may be hard on users, but XFCE is basically the GNOME-Lite wich has a good user base. XFCE, you might want to look in other directions.

---

### Post by aukar on 2005-04-08
:shock: I just posted my question 4 minutes ago!!!!  This one  is an amazing community.

Thanks bored2k!

---

### Post by az on 2005-04-08
[QUOTE=Marcke]Is there a decent user-base when you have problems with these distro's?
And where can you download those?

Wannes[/QUOTE]


they are not distros, but packages.

Enable the universe repository and install XFCE4 or icewm.  Or both.
Logout and then log back in after changing the session choice.

Ask here if you have any problems...

---

### Post by vinthund on 2005-04-30
[QUOTE=azz]they are not distros, but packages.

Enable the universe repository and install XFCE4 or icewm.  Or both.
Logout and then log back in after changing the session choice.

Ask here if you have any problems...[/QUOTE]


Not a problem but a question.

I a different thread I asked about lowest decent system requirements for Ubuntu and here I was redirected. So, what would you say they are? And if it is recommended to use lighter desktops than gnome on older computers - how to install them right from the start? I cannot remember Ubuntu installer asking me about desktop choice.

regards,

MV

---

### Post by az on 2005-04-30
"I a different thread I asked about lowest decent system requirements for Ubuntu and here I was redirected. So, what would you say they are`"

That is very personnal.  I am running it on a p166 with 96 megs of ram and a p200Mhx with 64 megs of ram.  The ubuntu desktop is very slow, so I use Icewm and XFCE4.  Your mileage may vary.  I would install the complete Ubuntu Gnome desktop on a 400 MHz system with 128 megs of ram.

Your mileage may vary.


"And if it is recommended to use lighter desktops than gnome on older computers - how to install them right from the start? I cannot remember Ubuntu installer asking me about desktop choice."

No, by default you get the default Gnome desktop.

Boot the installer with the "server" option.  You get a base system which takes up 350 megs of disk space.

Boot into your new system and log in.

sudo nano /etc/apt/sources.list
and comment out the universe repos.
sudo apt-get update
sudo apt-get install xdm xterm menu x-window-system-core icewm mozilla-firefox abiword
or
sudo apt-get install gdm menu epiphany-browser x-window-system-core fluxbox abiword

or
sudo apt-get install gdm xfce4 mozilla-firefox

Mix and match, have fun.

---

### Post by KDE-fan on 2005-04-30
I would recommend more than 128 megabytes RAM; KDE can easily use 110 mb of memory without even a single open program.

---

### Post by bored2k on 2005-04-30
[QUOTE=KDE-fan]I would recommend more than 128 megabytes RAM; KDE can easily use 110 mb of memory without even a single open program.[/QUOTE]
 And who said its going to use KDE ?If  you read the other posts youll see were aiming for an XFCE/lighter DM box.

---

### Post by KDE-fan on 2005-04-30
OK, sorry about that. I didn't read all the posts before replying. I think it you should use Ubuntu instead of Kubuntu if you want to install XFCE though,

---

### Post by moopere on 2005-04-30
[QUOTE=KDE-fan]OK, sorry about that. I didn't read all the posts before replying. I think it you should use Ubuntu instead of Kubuntu if you want to install XFCE though,[/QUOTE]

It won't make any difference because to get the lightest possible install you will start with the 'server' option.  This is ubuntu-base (I believe) and  is exactly the same on both ubuntu and kubuntu.

After the base, you'll install whatever desktop environment you choose - XFCE for instance.

On the subject of XFCE....anyone notice how slow rev 4.x is compared to 3.x?  Its written now using gtk libraries I believe....is this common link with gnome (ie, GTK) also why gnome is so slow?

Cheers,
Craig

---

### Post by vinthund on 2005-05-02
hello,

thanks for the replies. I shall try to use it in following days on my friend's computer.

---

### Post by satbunny on 2006-01-04
Thanks, will try the lean version.

---

### Post by nathanielC on 2006-08-21
Minimum system requirements have been covered on ubuntu.com:
[http://www.ubuntu.com/download/releasenotes/606#head-e15a51f7ff4cac464dfd54cbed7506ef13814de3](http://www.ubuntu.com/download/releasenotes/606#head-e15a51f7ff4cac464dfd54cbed7506ef13814de3)

---

### Post by dsmturbo on 2006-08-23
Running Kubuntu 6.06 (newest) here and slow on a PIII 600 w/256mb
 
Trying to install Ubuntu now on a Duron 1ghz w/256mb shared ram and install is slow as crap, tried it 3 times already. It gets hung up after I choose language.

---

### Post by az on 2006-08-23
> **dsmturbo said:**
> Running Kubuntu 6.06 (newest) here and slow on a PIII 600 w/256mb
 
Trying to install Ubuntu now on a Duron 1ghz w/256mb shared ram and install is slow as crap, tried it 3 times already. It gets hung up after I choose language.

Ubuntu 6.06 runs just fine on a P II, 400 MHz.  I would call it reasonably slow.  On my 600 MHz machine, I find nothing lacking.

As for your 256 meg shared machine, how much ram is shared with the video card?  To install using anything but english, you really need to have the full 256 megs of ram.

---

### Post by moopere on 2006-08-23
> **azz said:**
> Ubuntu 6.06 runs just fine on a P II, 400 MHz.  I would call it reasonably slow.  On my 600 MHz machine, I find nothing lacking.

As for your 256 meg shared machine, how much ram is shared with the video card?  To install using anything but english, you really need to have the full 256 megs of ram.

IMHO there is still something seriously wrong with gnome-ubuntu, the user experience is anything but snappy on anything that isn't state of the art.  It drives me nuts on the 2GHz Pentium M on my laptop (512MB RAM) - its perfectly fine, in fact quite quick enough on a 3GHz HT machine with 1GB RAM.

The interesting thing is that this perceived slowness is 'GUI user experience' related....the machine itself is not slow, running aptitude (or any other non gnome app) for instance from a VT is as quick as you'd expect.

I'm not going to hijack the thread with a kde versus gnome red herring, but on my (multiple) machines KDE doesn't suffer the same GUI latencies that gnome seems to which frustrates the hell out of me.  

I'm thinking GTK is in some way to blame because XFCE, whilst light, is also not nearly as quick as it used to be in the V3.x series before the gtk transistion.

Cheers,
Craig

---

### Post by in_flu_ence on 2007-01-05
I have a Compaq V2102AP desktop with 'Edgy' installed.

Currently with 512mb memory and a 80gb 5400rpm hdd. However, the speed in gnome seems to be getting slow and I usually use about 3-4 programs simultaneously (e.g. firefox, openoffice, amsn).

Do you think I should upgrade ram or it is the harddisk problem?

> top - 01:06:38 up  9:46,  2 users,  load average: 0.19, 0.24, 0.32
Tasks: 107 total,   1 running, 105 sleeping,   0 stopped,   1 zombie
Cpu(s):  4.3%us,  0.3%sy,  0.0%ni, 95.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    482288k total,   475640k used,     6648k free,    13356k buffers
Swap:  1413680k total,   152624k used,  1261056k free,   170584k cached

Read about the recommended system requirement but seems like I need more??

---

### Post by boogiepop88 on 2007-02-21
> **aukar said:**
> :shock: I just posted my question 4 minutes ago!!!!  This one  is an amazing community.

Thanks bored2k!


the best! ):P

---

### Post by forrestguide on 2007-02-22
> **bored2k said:**
> For an OK performance, I would say 700mhz processor with about 128mb ram should do good. You can get it to work on a lot lower machines, but for that I suggest lighter environments like XFCE or IceWM or Fluxbox.

I've tried a couple of times on  my Compaq Armada.  It's 700mhz with 128 megs but clearly my computer is not up to the task.  I'm trying a copy of 6.10. Maybe that's my problem.

I guess I'll just have to bite the bullet and upgrade memory.  The Compaq can take up to 512 and I guess that's where I'm headed.  I'm looking forward to the change, I need to learn.

Greg

---

### Post by stchman on 2007-05-03
> **forrestguide said:**
> I've tried a couple of times on  my Compaq Armada.  It's 700mhz with 128 megs but clearly my computer is not up to the task.  I'm trying a copy of 6.10. Maybe that's my problem.

I guess I'll just have to bite the bullet and upgrade memory.  The Compaq can take up to 512 and I guess that's where I'm headed.  I'm looking forward to the change, I need to learn.

Greg

You need more RAM.  Ubuntu needs at least 256MB RAM to run properly.  RAM is pretty cheap, try ebay.  I bought a 512MB PC2-DDR2 module for like $40.

---

### Post by stchman on 2007-05-03
> **in_flu_ence said:**
> I have a Compaq V2102AP desktop with 'Edgy' installed.

Currently with 512mb memory and a 80gb 5400rpm hdd. However, the speed in gnome seems to be getting slow and I usually use about 3-4 programs simultaneously (e.g. firefox, openoffice, amsn).

Do you think I should upgrade ram or it is the harddisk problem?



Read about the recommended system requirement but seems like I need more??


According to Compaq your PC is a laptop.  I am going to assume that your processor speed is better than 1.5GHz.  I have a Celeron M 1.73GHz laptop and it ran OK with 512MB RAM, but I did notice performance improvments in multiple apps running when I upgraded to 1GB.  If not multi-tasking it ran ok.  Get some more RAM as memory is cheap.

---

### Post by stchman on 2007-05-03
> **moopere said:**
> IMHO there is still something seriously wrong with gnome-ubuntu, the user experience is anything but snappy on anything that isn't state of the art.  It drives me nuts on the 2GHz Pentium M on my laptop (512MB RAM) - its perfectly fine, in fact quite quick enough on a 3GHz HT machine with 1GB RAM.

The interesting thing is that this perceived slowness is 'GUI user experience' related....the machine itself is not slow, running aptitude (or any other non gnome app) for instance from a VT is as quick as you'd expect.

I'm not going to hijack the thread with a kde versus gnome red herring, but on my (multiple) machines KDE doesn't suffer the same GUI latencies that gnome seems to which frustrates the hell out of me.  

I'm thinking GTK is in some way to blame because XFCE, whilst light, is also not nearly as quick as it used to be in the V3.x series before the gtk transistion.

Cheers,
Craig

Ubuntu 6.10 runs fine on my 1.73GHz Celeron laptop with 1GB and that is nowhere near state of the art.  As a matter of fact my laptop is considered entry level.

---

### Post by mithion on 2007-05-31
> **stchman said:**
> You need more RAM.  Ubuntu needs at least 256MB RAM to run properly.  RAM is pretty cheap, try ebay.  I bought a 512MB PC2-DDR2 module for like $40.

I agree, I've tried Ubuntu on 3 different systems and the ram is the component that affects performance the most.  Although Ubuntu will run on 128 meg of ram, you will see a vast improvement with 256 meg and more.  I was able to run it on a P3 500MHz with 128 of ram but it was sluggish.  Adding another 256 to bring it up to 384 did a lot.  Make no mistake, it won't be "snappy" on a 500MHz system, but at least you'll get a state of the art operating system that runs ok.

A distribution such as Ubuntu won't bring back your old legacy system to life.  It will work on old systems, but will do so slowly.  Ubuntu really shines though on moderately modern computers (older Pentium IV for example with 512 ram +) where its speed will completely obliterate that certain rival... Winblows I think its called.  For a Pentium II based system, I recommend Vector linux standard edition or Slackware which are the lightest of big full featured distros.  The first Ubuntu distro only came out in 2004 so its support for older PC isn't as good as the tried and true Slackware.  But if you've got the rig and run Ubuntu, boy are you in for a treat.  And that's my two cents.l

---

### Post by shae on 2007-05-31
For acceptable performance with a default i386 install of kubuntu, I would suggest at least 512 MB of ram and a modern processor (Pentium M, Pentium 4, or AMD64 or better).  This would provide you with a smooth system.  If you enjoy multitasking I recommend a dual core processor and at least 1 GB of ram.

---

### Post by kikin568 on 2007-11-18
I Have an old 700mhz and 128 Mb RAM, I try to put ubuntu but is too  slow, what linux do you recomend for me?

---

### Post by the_eternal_dark on 2007-11-27
kikin568, go to .[http://wiki.fluxbuntu.org/index.php?title=Get]("http://wiki.fluxbuntu.org/index.php?title=Get") and try that out. It should run pretty decently.

---

