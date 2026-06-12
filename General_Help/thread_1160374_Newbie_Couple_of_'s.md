---
title: "Newbie Couple of ?'s"
date: 2009-05-15
forum: General Help
---

### Post by s15199d on 2009-05-15
So, I'm an Ubuntu user for about an hour now, and I've got a few questions already.

I apologize in advance for the newbieness.  I come from PC land if that helps


[LIST=1]
[*]I need Flash support in Firefox and I was presented with 3 options.  I'm not sure which one I should go with...I just want Flash to work
[LIST=1]
[*]swfdec
[*]Adobe Flash player (this is what I'm guessing)
[*]gnash
[/LIST]
 
[*]iTunes...before I jumped in I read something about using Wine for iTunes...can someone fill in the blanks
[*]What are Fiesty & Fiesty Fawn?
[*]There are a bajillion lists of "must-have" apps for Ubuntu...is there a definitive list I should be looking reading?
[LIST=1]
[*]Antivirus?
[*]Malware/Adware?
[*]etc.
[/LIST]
 
[*]I'm running a dual-boot with Win XP...can I set Win XP as the default?  If not, my wife is gonna freak when she see's that screen for the first time.
[*]I'm sure there will be more, and I promise to Google the answers as much as possible.
[/LIST]
Thank in advance for your assistance and patience!

Excited to be playing w/ Ubuntu!!

---

### Post by kanikilu on 2009-05-15
> **s15199d said:**
> [*]I need Flash support in Firefox and I was presented with 3 options.  I'm not sure which one I should go with...I just want Flash to work

I use the one from Adobe (I think it's **flashplugin-nonfree** in synaptic)

> iTunes...before I jumped in I read something about using Wine for iTunes...can someone fill in the blanks

I've never tried, but check out the WineHQ's AppDB for first-hand reviews of running applications under Wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

Personally, I use Amazon MP3 and eMusic for 99% of my music, and only rarely have to boot into Windows for iTunes.

> What are Fiesty & Fiesty Fawn?

They are the same, it's kind of confusing, but there are generally 3 ways people reference an Ubuntu release:

- Official version number (9.04)
- Full codename (Jaunty Jackalope)
- Abbreviate codename (Jaunty)

I'd say the first and third are the most common.

For more information and history: [https://wiki.ubuntu.com/DevelopmentCodeNames](https://wiki.ubuntu.com/DevelopmentCodeNames)

> There are a bajillion lists of "must-have" apps for Ubuntu...is there a definitive list I should be looking reading?
Not really - it depends on what you want to do. My list of must haves may be totally irrelevant to someone else, while a programmer's must haves would be useless to me. Just let people know exactly what it is you want to do, and you should get plenty of suggestions.

> [LIST=1]
[*]Antivirus?
[*]Malware/Adware?
[*]etc.
[/LIST]
There are antivirus scanners for Linux, but I think they are mainly meant for applications like mail servers, or people who receive files from Windows and then want to scan them before sending them on to someone else. Most people will tell you not to bother, but it's really up to you - it certainly couldn't *hurt* to scan something before sending it on to a Windows user...
 
> I'm running a dual-boot with Win XP...can I set Win XP as the default?  If not, my wife is gonna freak when she see's that screen for the first time.

Heh, yeah, you can. You'd either need to edit grub's menu.lst file, or simply install a package called "startupmanager" where you can set this in a GUI.

---

### Post by prem1er on 2009-05-15
> **s15199d said:**
> So, I'm an Ubuntu user for about an hour now, and I've got a few questions already.

I apologize in advance for the newbieness.  I come from PC land if that helps


[LIST=1]
[*]I need Flash support in Firefox and I was presented with 3 options.  I'm not sure which one I should go with...I just want Flash to work
[LIST=1]
[*]swfdec
[*]Adobe Flash player (this is what I'm guessing)
[*]gnash
[/LIST]
 
[*]iTunes...before I jumped in I read something about using Wine for iTunes...can someone fill in the blanks
[*]What are Fiesty & Fiesty Fawn?
[*]There are a bajillion lists of "must-have" apps for Ubuntu...is there a definitive list I should be looking reading?
[LIST=1]
[*]Antivirus?
[*]Malware/Adware?
[*]etc.
[/LIST]
 
[*]I'm running a dual-boot with Win XP...can I set Win XP as the default?  If not, my wife is gonna freak when she see's that screen for the first time.
[*]I'm sure there will be more, and I promise to Google the answers as much as possible.
[/LIST]
Thank in advance for your assistance and patience!

Excited to be playing w/ Ubuntu!!

Welcome to ubuntu!

1. Your first choice should be to try and install the Adobe file from their website.  Most users have success with that version. 

2. If you are planning on keeping you're dual boot there is really no reason to use Wine to run iTunes.  What do you want iTunes on Ubuntu for, to simply play music, or also to sync your iPod? There is lots of software for both these tasks.  If you are using it to sync, than it can also depend on your iPod version.  Write back with yours.

3. Fiesty/Fiesty Fawn is just a release of Ubuntu.  Each release has a name that coordinates with the current release number of Ubuntu.  The most recent is Jaunty Jackalope.  Each new version increases the name by one letter in the alphabet.

4. No need real need for antivirus/antimalware on linux.

---

### Post by s15199d on 2009-05-15
y'all are great!  Thanks for the quick responses!

I guess I'm a Jaunty user...woot!

I'll hold off on antivirus/anti-malware for now...I realize linux is low on the bad guys' list...but if anyone has any recommendations I'm all ears.

iTunes...i have an iPhone 3G and would love to be able to sync inside of Ubuntu...yes I have dual boot, I'd like to try and use Ubuntu for everything going forward...if I can

---

### Post by s15199d on 2009-05-15
went to Adobe to get the flash player and I got a bunch of options I chose the "YUM" option...they gave me an *.rpm file that I can't open/run...suggestions?

Again...thanks for your patience!

---

### Post by s15199d on 2009-05-15
This this says it all about iTunes on Ubuntu...a little disheartening

[http://www.psychocats.net/ubuntu/itunes#runitunes](http://www.psychocats.net/ubuntu/itunes#runitunes)

i'm going to look into (iPod managers) Amork & Banshee as it suggests

---

### Post by kanikilu on 2009-05-15
> went to Adobe to get the flash player and I got a bunch of options I chose the "YUM" option...they gave me an *.rpm file that I can't open/run...suggestions

Ubuntu is Debian based, so you are looking for a "deb" package.

---

### Post by kanikilu on 2009-05-15
> **s15199d said:**
> This this says it all about iTunes on Ubuntu...a little disheartening

[http://www.psychocats.net/ubuntu/itunes#runitunes](http://www.psychocats.net/ubuntu/itunes#runitunes)

i'm going to look into (iPod managers) Amork & Banshee as it suggests

I use a combination of **Banshee** and **gtkpod**. The old version of **Amarok** was really good too, but I haven't had anything but trouble with the new version :(

---

### Post by Therion on 2009-05-15
> **s15199d said:**
> iTunes...i have an iPhone 3G and would love to be able to sync inside of Ubuntu...
Is it *possible*?   Yes.   Is it *easy*?   No.

Apple has been pretty thorough in its preventing your iPhone from synch'ing with anything other than iTunes.  In order to do it with Ubuntu, you would need to access to the iPod’s iTunes database via an SSH server over a wireless connection. The USB protocol is encrypted and, last I heard, has not yet been hacked.

---

### Post by prem1er on 2009-05-15
Download the .tar.gz file

Open up a terminal and run these commands.

```

cd /path/to/the/file
tar -xvf filename.tar.gz
cd (into the unzipped file)
./configure
make
sudo make install

```

---

### Post by kanikilu on 2009-05-15
> **s15199d said:**
> I'll hold off on antivirus/anti-malware for now...I realize linux is low on the bad guys' list...but if anyone has any recommendations I'm all ears. There are several free-for-home-use options from commercial vendors (e.g. Avast!, AVG). For open source, check out **clamtk**.

> iTunes...i have an **iPhone 3G** and would love to be able to sync inside of Ubuntu...yes I have dual boot, I'd like to try and use Ubuntu for everything going forward...if I can I don't have an iPhone, but I think I read somewhere that non-jailbroken iPhone's and iPod Touch's won't work :(

---

### Post by s15199d on 2009-05-15
Thank you all...got the *.deb file that Kanikilu recommended...and ran that...now Flash is cooking...

looking into iPod managers now...

---

### Post by s15199d on 2009-05-15
STOKED i just used the terminal for the first time to get the SUM startup manager

it's not that hard when someone gives you the commands here's what I ran:

sudo apt-get install startupmanager

no idea what that really meant, but I suppose I'll find out in time.

It worked and I reconfigured my boot options...guess i'll see if that worked the next time I boot...

THANK YOU all for your input!  Y'all have been great!  Off exploring for now and finding new questions I'm sure...

In my best Arnold impersonation...I'll be back!

---

