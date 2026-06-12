---
title: "best set up for this old thing?"
date: 2011-06-12
forum: Desktop Environments
---

### Post by smcrossman on 2011-06-12
Not sure this is the right place for this, but here goes.  I have 3 computers with Ubuntu natty installed. 2 are dual boot with Win7 1 is 32bit 1 is 64 bit.  The third one is my original ubuntu machine....its old, noisy but still in many ways more reliable than my current desktop (64 bit). The original HD went out and the factory add on graphics card also died (which is why I have the newer monster).  Turns out the motherboard had an onboard graphics card.  So I've got a 10GB hard drive in it for OS to run on. (hence the switch to linux)

My intent is to use this for mostly data entry and recordkeeping. Originally I thought I'd take my portable HD and use that for my home folder and be fine.  Then I thought I'd like to use that HD for samba srv shares so documents, et al, are available to each of the machines and I don't have to do a lot of syncing.  My hope is to upgrade into a better router/gateway forHD my DSL connection that will allow me to use a usb HD as a network drive. In the meantime it will have to be a slave to one of my machines.

Regardless, as I was sitting and cleaning up some installaltion etc on my oldie I realized that I currently am using 8GB of my available 10.  Do I need to uninstall some of the standard packages and move to lighter ones?  It definitely doesn't support Unity so it's the only one not with it so the graphical interface is going to be different regardless.  I just don't know if I should reformat and do a clean install of another kernel or start removing individual packages.  Also how do I best put the default home location on a usb stick? (I'm looking at using an 8GB one I have here that I've been using to port things from HDmachine to machine.

Suggestions and lessons learned from your experiences appreciated!

---

### Post by wildmanne39 on 2011-06-12
> **smcrossman said:**
> Not sure this is the right place for this, but here goes.  I have 3 computers with Ubuntu natty installed. 2 are dual boot with Win7 1 is 32bit 1 is 64 bit.  The third one is my original ubuntu machine....its old, noisy but still in many ways more reliable than my current desktop (64 bit). The original HD went out and the factory add on graphics card also died (which is why I have the newer monster).  Turns out the motherboard had an onboard graphics card.  So I've got a 10GB hard drive in it for OS to run on. (hence the switch to linux)

My intent is to use this for mostly data entry and recordkeeping. Originally I thought I'd take my portable HD and use that for my home folder and be fine.  Then I thought I'd like to use that HD for samba srv shares so documents, et al, are available to each of the machines and I don't have to do a lot of syncing.  My hope is to upgrade into a better router/gateway forHD my DSL connection that will allow me to use a usb HD as a network drive. In the meantime it will have to be a slave to one of my machines.

Regardless, as I was sitting and cleaning up some installaltion etc on my oldie I realized that I currently am using 8GB of my available 10.  Do I need to uninstall some of the standard packages and move to lighter ones?  It definitely doesn't support Unity so it's the only one not with it so the graphical interface is going to be different regardless.  I just don't know if I should reformat and do a clean install of another kernel or start removing individual packages.  Also how do I best put the default home location on a usb stick? (I'm looking at using an 8GB one I have here that I've been using to port things from HDmachine to machine.

Suggestions and lessons learned from your experiences appreciated!Hi, you could do a minimal install, and only install what you want and what the system needs to run but that is harder to set up you would have to do some work. I do not recommend removing packages with out knowing what they are a lot of people have done that and broke there system in the process. You can look into alternative install on the ubuntu download page. You could consider changing to puppy linux or one of those smaller linux systems like puppy.

---

### Post by smcrossman on 2011-06-13
Thank you for your response!  I looked at the alternative and minimal installs while downloading for the reinstall on the 64 bit monster.  The options are a little mind boggling.  I saw something about a minimal Natty install with options for lighter interfaces for desktop. I'm just a little lost about how they work.  I also didn't get a very clear understanding of how the process really works.  

I will go back and read it again but is there more information/documentation out there that is reliable? Before I can jump into this re-install, I need to finish troubleshooting and fixing the wireless networking in the house. After that maybe I can learn how to set up a VM to try out the different environment options.  I was hoping that someone who had done some kind of customizing of the install process could give me a better idea what is involved.

---

### Post by mister_playboy on 2011-06-14
You don't mention how much RAM the old computer has, but I would think Lubuntu (LXDE desktop) might be a good choice.

While the default install of Lubuntu 11.04 uses 5.9GB and that would still consume more than half the hard drive... is that really a problem?  You can store a whole lot of data/records text in 3-4GB.

Given your stated usage intention, I'm not sure you need to go the route of a custom install just to save some space on a tiny HDD.  If you want to learn something about Linux's internal structure, go ahead, but it doesn't seem strictly necessary.

---

### Post by smcrossman on 2011-06-14
I'm enjoying the learning and all, but I'm not sure I want to learn that in depth if I don't need to.  I'm just so totally new I don't know or even begin to comprehend the subtle differences between the different...uh....versions?  So I will definitely look at Lubuntu.  

Some basics on the PC:  

Pentium4 cpus 2.80 GHz
4 PCI-UHCI & 1 PCI-EHCI
479MiB RaAM (Intell DRAM) I have 4 RAM sticks floating around here, but not sure exactly what they are. I know some were the originals out of this PC....but whether they are any good or if there are slots open ?
Funcitoning integrated Graphics card & sound card; the DVD RW functions well (in Linux it is better than the one I have on my "primary" machine in either Windows or Linux)
and an old PCI Data/FAX Moden v.92

The HD is showing as an ATA Maxtor 91000D5.

Everything is basically Intel labelled

I know it has more usb jacks than my current one.  Its just a little slow, and kind of noisy. Without enough room for any windows OS! (Not anything I will cry about!)

---

### Post by Derek Karpinski on 2011-06-14
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)
 
I just did this last night in Virtualbox.  Basically a full install of 11.04 with unity 3d, open office, chromium, firefox, evolution, full sound, totem, restricted codecs, dvd support..........all for the low price of 2.5GB, and 230MB RAM at idle.
 
It's really easy, but you do need high speed internet unless you know how to use your live CD as a repository.

---

### Post by smcrossman on 2011-06-15
Thanks! Looks like an interesting approach.  If I can just figure out VirtualBox and creating those VMs.  Still a bit over my head.

---

### Post by Derek Karpinski on 2011-06-16
You don't need to install it in a virtual machine.  I just did to see how it worked/if it worked.  I have a install of Ubuntu 11.04 that I'm happy with ATM other than memory usage.
 
If you have more than one PC, and the one you're talking about is not your everyday PC, forget the VM, and just install it natively.
 
I actually did another minimal install in vbox, not using that script above.  Memory usage with Unity was 220MB, and used 1.9G of space.
 
Just try it!  Breaking and fixing stuff is a good way to learn. (as long as it's just a play computer) :D

---

### Post by FormatSeize on 2011-06-16
> **Derek Karpinski said:**
> [http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)
 
I just did this last night in Virtualbox. Basically a full install of 11.04 with unity 3d, open office, chromium, firefox, evolution, full sound, totem, restricted codecs, dvd support..........all for the low price of 2.5GB, and 230MB RAM at idle.
:-s
 
Now do Fedora 15. Go.
Seriously, though. This is pretty impressive. I will definitely have to take a stab at just installing a heck of a lot less stuff when I'm toying around with monsters like Unity and Gnome3, and this makes it easy. 
 
> **Derek Karpinski said:**
> It's really easy, but you do need high speed internet unless you know how to use your live CD as a repository.
I don't have a high speed internet connection. Can the combination of your script and using a live CD as a repository do the trick?

---

### Post by Derek Karpinski on 2011-06-16
I'm not an expert on it.......just messing about.

Here is a 30 page long thread with a bunch of scripts and command line stuff to type in after the minimal install.  I'm almost positive I read something in this thread that details how to use the live CD as a repo. EDIT: here [http://ubuntuforums.org/showpost.php?p=10821306&postcount=293](http://ubuntuforums.org/showpost.php?p=10821306&postcount=293)

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

What I ended up doing was making another VM and used this blog as a guide.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I found installing lightdm as a login manager was good for some more memory.  Although it doesn't look polished.

I like gnome, so I skipped icewm and all the others.

---

### Post by smcrossman on 2011-06-18
I so agree that breaking things is the best way to learn!  Exactly how I'm learning Ubuntu!  I will have to look at the script more in depth, but with minimal install there are a lot of options to figure out, so a script is probably going to save me time and headaches!

Besides I do a lot of tweaking routinely.  I'm pretty sure I will not be using evolution, but I'm still trying to figure out all the ins & outs of that choice.  I just don't have enough options in sorting, coding,filtering, etc of mail in evolution right now using Claws, but haven't looked at calendar or Contacts with that one. Mostly though that will be stored on server share and this pc will only rarely need to look at it.

I still want to play with Lubuntu and Xubuntu just to see how they are really different/similar.   But that is a VM project for when I can get VM figured out!

Looking at doing this over the weekend, so I'll keep you posted on how it works out!

---

### Post by Derek Karpinski on 2011-06-20
Daring!  I like it. :D

The scripts really run themselves.  Some of the questions are a bit ambiguous......'Do you want Ubuntu to look better?' Of course I do......but at what expense?  It doesn't tell you what action will be taken on the answers.

---

### Post by smcrossman on 2011-06-20
Well, it hasn't been the best time....I've now tried to install 3 times...LOL

First time grub rescue....I couldn't get a thing done to fix it.  So I went round 2.  That time I went for just the basic minimal Ubuntu install. When it came time to boot up it would hang. Judging from the messages when I would shut it down....somewhere around the plymouth screen portion.

Round 3 finally tried the script  could not get it to run for anything. Opted for the xbuntu desktop install option. Because I was having issues with Grub (like who doesn't?) I opted over to LILO. I have NO graphical display.  I can not run any programs that have a graphical front-end.  So I am about to try again and just install Lubuntu and see what happens.

I've learned a lot about partitioning and LVM.  I'm leaning a lot of package and command names that I didn't know before.  Becoming very comfortable with the apt-get serious of commands.  In fact I'm now using synaptic or software center to look up packages & names but installing using apt-get. LOL

It's been interesting....and I'm not done yet!

Maybe I'll try the script again before I ditch this install....hmmm......

---

### Post by Derek Karpinski on 2011-06-20
From psychocats blog:
 
> I have not yet tested this fully on Ubuntu 11.04 (Natty Narwhal), but for almost all of the installation process, it looks as if it's exactly the same, except with a purple background. The one tiny difference (thanks to Dan for the comment) is that you have to press Alt-F1 to get the command prompt after you reboot. 
 
So maybe it wasn't hanging.  I infact noticed this, and pressed Alt-F1, and volia! a command prompt.
 
Then you run the scripts, or your own 'apt-get' stuff.

---

### Post by smcrossman on 2011-06-20
Well, when I went back earlier I tried the script which took off and ran beautifully.....until my router somehow unplugged itself from the electrical outlet.  (My life has some really strange happenings!) Then it failed to get a lot of downloads but went ahead and finished the process iwth what it had gotten.  So living dangerously I re-ran the script, changing a few little answers and it went right back to work.  Where my second answer conflicted with what it had already done...it just ignored it.  So I didn't load 2 multimedia managers, just the first one AND the one that unity loaded.

I am having serious issues iwth hd space, it isn't liking the partiioning or using the lvm properly.  So I deleted a few things and installed VLM to see if I can fix the problem.  If not, well I guess it will be a fresh formatting and trying Xubuntu.  Maybe Lubuntu....I don't need the fancy graphical on this machine becaus of how I am using it, but darn it, I still want to be able to fix it up pretty and choose mouse over keyboard when I feel like it! LOL

I did finally figure out that with the monitor I'm using I absolutely cannot use anything more than Ubuntu Classic withOUT effects or I have periods of the screen just disappearing and clicking causing flashing invisibility.  So really why install the unity graphical if I can't use it?

---

### Post by Derek Karpinski on 2011-06-20
This is why trying all this stuff in a VM would let you experiment.
 
What I would do is:
 
1. install virtualbox on your main computer (plenty of space, right?)
2. install ubuntu minimal install in that VM.
3. take a snapshot of that minimal install before you do anything else.
4. start that vm and start installing stuff.
5. if it takes up too much space, or you don't like the way it looks, revert your snapshot to the minimal install.
6. make sure you take notes on the packages you did install.
 
> sudo apt-get install xorg lightdm gnome-core menu firefox gksu synaptic
 
Should get you a decent looking gnome desktop with everything you need but minimal space.

---

### Post by JC Cheloven on 2011-06-21
I guess you'll feel soon like finishing your experiments and installing a balanced, usable OS for your low-end machine. At that point, you may have realized that Lubuntu can be likely your choice (even xubuntu is a bit too much imo).  

You should have no problem at installing it in the usual way, but if you need to start from a command line system, you can follow [this]("http://ubuntuforums.org/showthread.php?p=10966102#post10966102").

---

### Post by smcrossman on 2011-06-21
Actually, I opted for the Lubuntu iso when I did my insall late last night/early tihs morning.  It was going along fine...except I was having an issue with being able to access or update the repositories in synaptic, and/or download in software center.  Figured that out...if you don't open as root it doesn't allow you to later become root to access those things?  

Anyway....I then shut down for a nap (been a LONG week or two) and figured I'd save some carbon by shutting down all 3 computers. Well I now get a gnome-2d not found and Lubuntu kicks me back out to command line. It's a nice little system...I think I actually like the desktop better than the unity, but I'm still a little lost as to what exactly I'm using.  Gnome, GTK, X, ???

Regardless tonight I'm doing a full clean install of Ubuntu on a previously dual boot  doing away with windows on that one.  So the little Lubuntu will have to wait another day to get into the network.

---

### Post by JC Cheloven on 2011-06-22
> **smcrossman said:**
> I was having an issue with being able to access or update the repositories in synaptic, and/or download in software center.

No software center in Lubuntu... unless you install it. Was it a clean Lubuntu install?

Oh, I remember I had a little problem at starting synapcit (at 11.04) from the menu, and I had to do a minor&absurd edit to /usr/share/applications/synaptic.desktop. 

Anyway, gksudo synaptic (at terminal) will do as well.

If you clean install Lubuntu, you'll not be using gnome, but openbox & lxde. You can run plenty of gtk applications though, as well as qt-based ones. Don't worry, you'll find the way among the jungle of options. Just explore... and ask ;)

---

