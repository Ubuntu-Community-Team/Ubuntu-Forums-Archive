---
title: "Two OS on one drive?"
date: 2009-04-03
forum: General Help
---

### Post by soomro on 2009-04-03
well as the title says can i have both (Ubuntu and Kubuntu) on one drive?

my other side question can't the "windows" drives (in which windows is installed) be mounted? i can't mount them? 
and plus when i put my username and password i get into ubuntu then it hangs and i get back to logon screen? this started happening after i installed custom effects for compiz? how to undo it?

---

### Post by James_Lochhead on 2009-04-03
The term "drive" means something physical. If you use this term to describe partitions then people will think you have multiple hard disks. A partition is (I think) what you mean it is part of (think part-ition a storage medium (i.e. hard disk in this case). 

1) You can have KDE and GNOME installed on a single partition. If you have Ubuntu (GNOME) display get the package kubuntu-desktop.

2) Yes you can mount your Windows partition. You should be able to do this in the file manager (left side).

Don't know how to fix Compiz.

---

### Post by soomro on 2009-04-03
> **James_Lochhead said:**
> The term "drive" means something physical. If you use this term to describe partitions then people will think you have multiple hard disks. A partition is (I think) what you mean it is part of (think part-ition a storage medium (i.e. hard disk in this case). 

1) You can have KDE and GNOME installed on a single partition. If you have Ubuntu (GNOME) display get the package kubuntu-desktop.

2) Yes you can mount your Windows partition. You should be able to do this in the file manager (left side).

Don't know how to fix Compiz.

yes probably i meant Partition.

can i have tutorial or you can tell me how to do that? i already have gnome installed?

so it asks me which desktop i want to load :lolflag:

---

### Post by James_Lochhead on 2009-04-03
> **soomro said:**
> yes probably i meant Partition.

can i have tutorial or you can tell me how to do that? i already have gnome installed?

so it asks me which desktop i want to load :lolflag:

[LIST]
[*]Go to System > Administration > Synaptic Package Manager.
[*]Search for kubuntu-desktop.
[*]In the list that appears find the entry for the package with the exact name kubuntu-desktop.
[*]Right click and check in for installation.
[*]Click apply.
[*]Log out.
[*]In the session link at the bottom of the login screen choose "KDE".
[*]Log back in.
[/LIST]

---

### Post by asuastrophysics on 2009-04-03
Quote: "*and plus when i put my username and password i get into ubuntu then it hangs and i get back to logon screen? this started happening after i installed custom effects for compiz? how to undo it?"*

This can be done pretty easily, but it will require loosing all those custom settings you picked in compiz. 

When the logon screen goes to black, hit CTRL + ALT + F1. If it says "logon", enter your username and password. 
Then type this in:
$ sudo apt-get remove compiz compiz-plugins compiz-wrapper compiz-core
hit ENTER
type in your password
ENTER again
it will prompt a "y" or "n" to uninstall the packages. choose yes
when it finishes, type in:
sudo apt-get install compiz compiz-plugins compiz-wrapper compiz-core
hit ENTER and choose "y" at the prompt

restart your computer

hope this helps, let me know
8-)

---

### Post by soomro on 2009-04-03
> **James_Lochhead said:**
> The term "drive" means something physical. If you use this term to describe partitions then people will think you have multiple hard disks. A partition is (I think) what you mean it is part of (think part-ition a storage medium (i.e. hard disk in this case). 

1) You can have KDE and GNOME installed on a single partition. If you have Ubuntu (GNOME) display get the package kubuntu-desktop.

2) Yes you can mount your Windows partition. You should be able to do this in the file manager (left side).

Don't know how to fix Compiz.

> **James_Lochhead said:**
> [LIST]
[*]Go to System > Administration > Synaptic Package Manager.
[*]Search for kubuntu-desktop.
[*]In the list that appears find the entry for the package with the exact name kubuntu-desktop.
[*]Right click and check in for installation.
[*]Click apply.
[*]Log out.
[*]In the session link at the bottom of the login screen choose "KDE".
[*]Log back in.
[/LIST]


will that actually download the whole OS from internet?
because i dun want it cause i already have the CD for that OS XD probably i am sorry if i am confusing you

isn't Kubuntu-desktop = Kubuntu OS? :-#

---

### Post by soomro on 2009-04-03
> **asuastrophysics said:**
> Quote: "*and plus when i put my username and password i get into ubuntu then it hangs and i get back to logon screen? this started happening after i installed custom effects for compiz? how to undo it?"*

This can be done pretty easily, but it will require loosing all those custom settings you picked in compiz. 

When the logon screen goes to black, hit CTRL + ALT + F1. If it says "logon", enter your username and password. 
Then type this in:
$ sudo apt-get remove compiz compiz-plugins compiz-wrapper compiz-core
hit ENTER
type in your password
ENTER again
it will prompt a "y" or "n" to uninstall the packages. choose yes
when it finishes, type in:
sudo apt-get install compiz compiz-plugins compiz-wrapper compiz-core
hit ENTER and choose "y" at the prompt

restart your computer

hope this helps, let me know
8-)

ok i am trying that XD
i need to save the commands before i restart :lolflag:

---

### Post by chinmaya_n on 2009-04-03
Yes, what happened to u is b'se of compiz conflicts ...... first remove compiz using following command.
 [U get dropped into shell by selecting the safe made during loading of the os(i.e in grub)]
```
$apt-get remove compiz compiz-core
```

Then restart ur system,u'll get logged into Ubuntu. But u loose compiz. To get back them type this command
```
$apt-get install compiz compiz-core
```
Then u'll get back ur compiz. The better way to use compiz is by *Simple CCSM i.e Simple Compiz Config Settings Manager* rather than using CCSM directly...:p

---

### Post by soomro on 2009-04-03
I did as you said removed them and installed them again restarted but still it doesn't work? it hangs and logs out!

EDIT: i installed this and then the problem started
"How can I get Custom to appear in the Visual Effects dialog?

    Custom only appears if the package simple-ccsm is installed. When you install simple-ccsm, a new selection will be available in Visual Effects, which allows you to customize what effects are active on your desktop. You can also customize the effects from System > Preferences > Simple CompizConfig Settings Manager."

[Source]("http://ubuntuforums.org/showthread.php?t=809695")

---

### Post by soomro on 2009-04-03
Ok i uninstalled it and i can now log in so thanks a lot so now i am trying to install it again.

---

### Post by soomro on 2009-04-03
when i remove it i can log in but when i install it i can't?????

---

### Post by soomro on 2009-04-03
is bumping allowed here? :lolflag:

---

### Post by Mason Whitaker on 2009-04-03
Problem with having both the KDE and Gnome environments on one Ubuntu partition is that on either one you still have your applications which can only run in the other environment.

Much less of a headache to just install Kubuntu and Ubuntu :D

---

### Post by soomro on 2009-04-03
> **Mason Whitaker said:**
> Problem with having both the KDE and Gnome environments on one Ubuntu partition is that on either one you still have your applications which can only run in the other environment.

Much less of a headache to just install Kubuntu and Ubuntu :D

I dun get you, are you trying to say i have to install the applications again for different environment?:mad:

---

### Post by soomro on 2009-04-03
Bump - tell me if bumping is not allowed here :popcorn:

---

### Post by soomro on 2009-04-04
BUMP :lolflag:

---

### Post by Elfy on 2009-04-04
Did you not get the 2 os's installed on the one partition yet? 

You do just have to install it and then choose when you login.

Bumping is allowed - need to leave it 24 hours though, you appear to have done so 3 times in 13 hours which is probably pushing it ;)

---

### Post by mb_webguy on 2009-04-04
There's seems to be quite a bit of confusion in this thread on all sides.  Hopefully I'll be able to clear things up a bit...

Ubuntu and Kubuntu are the same OS.  (Actually, Linux is the OS and K/Ubuntu is the distribution, but let's keep things simple.)  

Ubuntu == Kubuntu

They're the same thing.  The only difference between the two are the desktop used and the default applications.  *Because* they are the same OS, and only differ by the programs used, you don't have to have either/or.  You can have both at the same time, on the same partition, without having to reinstall *anything*, because they're the *same thing*.

The desktop environment is a program.  This program can be installed, uninstalled, and reinstalled just like any other program.  And there are several desktop environments available.  Ubuntu uses Gnome, and Kubuntu uses KDE.  Some applications are designed for use with one or the other desktop environment, but because it's all Linux, you can run programs designed for use on Gnome while using KDE, or programs designed for use on KDE while using Gnome.  It *doesn't matter*, because it's all the *same operating system*.

You can have two (or more) desktop environments installed at once.  If you do, you can choose which desktop enviroment you want to use when you login.  Today, you might want to use Gnome.  Tomorrow, you might want to use KDE.  The next day, you might want to use Gnome again.  As long as you have both installed, you just have to pick which one you want to use at the login screen by going to Options (in the bottom-right corner) and selecting Choose Session.

If you're using Ubuntu, you can install the KDE desktop environment by installing the kubuntu-desktop package.  If you're using Kubuntu, you can install the Gnome desktop environment by installing the ubuntu-desktop package.  This will *only* install the desktop environment.  If you're using Ubuntu and you install kubuntu-desktop, if you want Amarok (the KDE alternative to Rhythmbox) or any of the other applications that come with Kubuntu, you'll have to install them separately.  You can do this fairly easily in Synaptic by right-clicking on the kubuntu-desktop package and selecting "Mark Recommended for Installation", and selecting the packages for the applications you want to install in addition to kubuntu-desktop.

Keep in mind that no matter which desktop environment you use, it's still the same OS -- it just has a different interface depending on which desktop environment you choose to use.

You can *also* have a second, separate installation of K/Ubuntu or any other operating system on another partition on the same drive, but that's a completely different situation, and not, I don't think, what you were asking.

---

### Post by soomro on 2009-04-04
> **forestpixie said:**
> Did you not get the 2 os's installed on the one partition yet? 

You do just have to install it and then choose when you login.

Bumping is allowed - need to leave it 24 hours though, you appear to have done so 3 times in 13 hours which is probably pushing it ;)



no not yet...

be more specific what you trying to say is i have install it JUST IN THE SAME PARTITION and it will ask me at logon which session i want?

ok i won't do it then lol

---

### Post by soomro on 2009-04-04
> **mb_webguy said:**
> There's seems to be quite a bit of confusion in this thread on all sides.  Hopefully I'll be able to clear things up a bit...

Ubuntu and Kubuntu are the same OS.  (Actually, Linux is the OS and K/Ubuntu is the distribution, but let's keep things simple.)  

Ubuntu == Kubuntu

They're the same thing.  The only difference between the two are the desktop used and the default applications.  *Because* they are the same OS, and only differ by the programs used, you don't have to have either/or.  You can have both at the same time, on the same partition, without having to reinstall *anything*, because they're the *same thing*.

The desktop environment is a program.  This program can be installed, uninstalled, and reinstalled just like any other program.  And there are several desktop environments available.  Ubuntu uses Gnome, and Kubuntu uses KDE.  Some applications are designed for use with one or the other desktop environment, but because it's all Linux, you can run programs designed for use on Gnome while using KDE, or programs designed for use on KDE while using Gnome.  It *doesn't matter*, because it's all the *same operating system*.

You can have two (or more) desktop environments installed at once.  If you do, you can choose which desktop enviroment you want to use when you login.  Today, you might want to use Gnome.  Tomorrow, you might want to use KDE.  The next day, you might want to use Gnome again.  As long as you have both installed, you just have to pick which one you want to use at the login screen by going to Options (in the bottom-right corner) and selecting Choose Session.

If you're using Ubuntu, you can install the KDE desktop environment by installing the kubuntu-desktop package.  If you're using Kubuntu, you can install the Gnome desktop environment by installing the ubuntu-desktop package.  This will *only* install the desktop environment.  If you're using Ubuntu and you install kubuntu-desktop, if you want Amarok (the KDE alternative to Rhythmbox) or any of the other applications that come with Kubuntu, you'll have to install them separately.  You can do this fairly easily in Synaptic by right-clicking on the kubuntu-desktop package and selecting "Mark Recommended for Installation", and selecting the packages for the applications you want to install in addition to kubuntu-desktop.

Keep in mind that no matter which desktop environment you use, it's still the same OS -- it just has a different interface depending on which desktop environment you choose to use.

You can *also* have a second, separate installation of K/Ubuntu or any other operating system on another partition on the same drive, but that's a completely different situation, and not, I don't think, what you were asking.

i knew what ever you explained but did not know how to explain it myself so thanks a lot for giving me some words through which i can make people understand what i mean.

same qustion again. I have the CD for my Kubuntu-desktop so i do not want to use internet to download whole thing again (i know its 250mb approximately since i have the OS as Ubuntu already) but my internet is slow right now for that. So can i just select the SAME partition for that and it will repair/replace the files and also install new one's so i get the option of which desktop i want?

---

### Post by Elfy on 2009-04-04
No you can, if you want to install to the same partition use apt-get install buntuvariant-desktop, ie kubuntu-desktop, xubuntu-desktop, then you can choose them form login

Or  you can install to seperate partitions if you want to - I have jaunty ubuntu, jaunty kubuntu, xubuntu intrepid all on seperate partitions.

---

### Post by soomro on 2009-04-04
> **forestpixie said:**
> No you can, if you want to install to the same partition use apt-get install buntuvariant-desktop, ie kubuntu-desktop, xubuntu-desktop, then you can choose them form login

Or  you can install to seperate partitions if you want to - I have jaunty ubuntu, jaunty kubuntu, xubuntu intrepid all on seperate partitions.

Uh this is the same process explained by the first answerer. This will download it from INTERNET that i do not what?????

---

### Post by mb_webguy on 2009-04-04
Forget the darn disc.  Throw it away.  You don't need it.  *You already have Ubuntu installed*, and *Kubuntu IS Ubuntu*.

All you need to do is open System->Administration->Synaptic Package Manager, type "kubuntu-desktop" in the Quick Search box, mark the kubuntu-desktop package for installation, and click the Apply button.

That's it.  That's all.  You're *done*.  No disc required.  If you try to do anything with that disc, you're just going to screw up what you have.  Please don't do that, because it makes babies cry.  Ok?  ;)

---

### Post by Elfy on 2009-04-04
add the cdrom to your software source - System >admin > Software Sources

---

### Post by soomro on 2009-04-04
> **mb_webguy said:**
> Forget the darn disc.  Throw it away.  You don't need it.  *You already have Ubuntu installed*, and *Kubuntu IS Ubuntu*.

All you need to do is open System->Administration->Synaptic Package Manager, type "kubuntu-desktop" in the Quick Search box, mark the kubuntu-desktop package for installation, and click the Apply button.

That's it.  That's all.  You're *done*.  No disc required.  If you try to do anything with that disc, you're just going to screw up what you have.  Please don't do that, because it makes babies cry.  Ok?  ;)


Ok i am getting more stupid!!!

what i really mean is the default software is already in the Kubuntu disc right so why i need to install them from internet XD 

but thanks for help.

---

### Post by soomro on 2009-04-04
> **forestpixie said:**
> add the cdrom to your software source - System >admin > Software Sources

Now this is what i wanted like ****

THANKS A LOT!!!!!!!!!!!!

---------------------
[Another question here if you would like to help me more cause its natural with me too lol]("http://ubuntuforums.org/showthread.php?p=7010467#post7010467")

---

### Post by mb_webguy on 2009-04-04
*cringe*  Pix is right...  You can add the disc to your Software Sources, and save yourself from a lengthy (approximately 500MB) download during the kubuntu-desktop installation.

But do *exactly* as ForestPixie said.  You're not using the disc to install Kubuntu.  You're *just* using it like a local software repository.

---

### Post by Elfy on 2009-04-04
and what I forgot to add was that once you have done - remove the cdrom from the software sources otherwise it will complain each and everytim you try and use apt-get

---

### Post by soomro on 2009-04-04
> **forestpixie said:**
> and what I forgot to add was that once you have done - remove the cdrom from the software sources otherwise it will complain each and everytim you try and use apt-get


Its about commonsense :lolflag:

---

### Post by soomro on 2009-04-04
> **mb_webguy said:**
> *cringe*  Pix is right...  You can add the disc to your Software Sources, and save yourself from a lengthy (approximately 500MB) download during the kubuntu-desktop installation.

But do *exactly* as ForestPixie said.  You're not using the disc to install Kubuntu.  You're *just* using it like a local software repository.

that is what i was trying to tell lately

---

### Post by Ben Crisford on 2009-04-04
Of course you can.

Open  *accessories> terminal*
And enter:
```
sudo apt-get install kubuntu-desktop
```

That will install KDE, all your ubuntu files wil also be on Kubuntu.

To switch between them logout> options>session>KDE/Gnome

---

### Post by Elfy on 2009-04-04
> **Ben Crisford said:**
> Of course you can.

Open  *accessories> terminal*
And enter:
```
sudo apt-get install kubuntu-desktop
```

That will install KDE, all your ubuntu files wil also be on Kubuntu.

To switch between them logout> options>session>KDE/Gnome

We've been there - OP doesn't want to download the packages as there is already a cd with the packages on ;)

---

### Post by soomro on 2009-04-04
OP? orignal poster lol

but hey it says to insert CD where as i already have inserted?

---

### Post by soomro on 2009-04-04
just to bring it on top i need urgent help :lolflag:


hmm i can't type symbols

---

### Post by Ben Crisford on 2009-04-04
> **forestpixie said:**
> We've been there - OP doesn't want to download the packages as there is already a cd with the packages on ;)

Oops.

Sorry...  I was on my mobile and didn't get time to read all the posts.

---

### Post by soomro on 2009-04-04
man i can't resist

---

### Post by soomro on 2009-04-04
is there some body to answer me

---

### Post by soomro on 2009-04-04
damn i can't wait why any one is not posting please reply i am sorry i can't resist but post more without any reason :mad:

---

### Post by soomro on 2009-04-04
answer me or i am gonna die

---

### Post by pbpersson on 2009-04-04
Tell me exactly where you are in this process, exactly what you are doing, and exactly what error you are getting

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> Tell me exactly where you are in this process, exactly what you are doing, and exactly what error you are getting

Ok i go to System>administration>software source

i select add CD rom which says that the CD is not inserted but still adds the CD which states that there is Kubuntu in it. 

after that how do i make the synaptic package manager to install it form CD?

and also [answer this interlinked question.]("http://ubuntuforums.org/showthread.php?t=1115809&highlight=synaptic+package+manager")


thanks


P.S: if you also want to know what i exactly want is that i want the Kubuntu-environment to be put in my sessions so i  can log into that session along with my Ubuntu-environment.

---

### Post by pbpersson on 2009-04-04
<comment for everyone>

This entire concept,... 

(Ubuntu = Kubuntu) AND (Ubuntu = Gonme) AND (Kubuntu = KDE) 

That would tend to suggest that (KDE = Gnome) which is not true at all

People have to realize that Ubuntu and Kubuntu are the same OS with a different skin...sort of (I know it is more complicated)

Probably when you tell them you can run KDE applications under Gnome and Gnome applications under KDE is when their eyes get a glazed/dazed look.

</comment>

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> <comment for everyone>

This entire concept,... 

(Ubuntu = Kubuntu) AND (Ubuntu = Gonme) AND (Kubuntu = KDE) 

That would tend to suggest that (KDE = Gnome) which is not true at all

People have to realize that Ubuntu and Kubuntu are the same OS with a different skin...sort of (I know it is more complicated)

Probably when you tell them you can run KDE applications under Gnome and Gnome applications under KDE is when their eyes get a glazed/dazed look.

</comment>


eh! i already know that and this is what we have been talking here lately XD

---

### Post by pbpersson on 2009-04-04
> **soomro said:**
> Ok i go to System>administration>software source

i select add CD rom which says that the CD is not inserted but still adds the CD which states that there is Kubuntu in it. 

after that how do i make the synaptic package manager to install it form CD?


In theory I would think that:

1.  There must be a way to tell synaptic to ONLY install from CD or
2.  There must be a way to tell synaptic to use the CD as the first choice

You most likely assume that everyone here knows these things.....but why would anyone ever do this?  Everyone uses the Internet for download.

Did you PURCHASE the CD and have it shipped to you because your connection is so slow?

Let me play with this and see if I can get my machine to load a package from CD.  I will even use the command line just for you.  ;)

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> In theory I would think that:

1.  There must be a way to tell synaptic to ONLY install from CD or
2.  There must be a way to tell synaptic to use the CD as the first choice

You most likely assume that everyone here knows these things.....but why would anyone ever do this?  Everyone uses the Internet for download.

Did you PURCHASE the CD and have it shipped to you because your connection is so slow?

Let me play with this and see if I can get my machine to load a package from CD.  I will even use the command line just for you.  ;)

OMG thanks alot.

well my connection is 50/kbps so yes i dun want to waste time download it for hours.

again thanks i am waiting ^^

---

### Post by pbpersson on 2009-04-04
PHASE ONE

Okay, I am in Synaptic

I go to repositories

The first four check boxes are checked under "download from Internet"

At the bottom it says "to install from CD, insert your CD"

So I insert my CD and uncheck all the checkboxes that say "download from Internet"

---

### Post by soomro on 2009-04-04
Uh and i had downloaded it earlier and burnt the .iso to a cd did not PURCHASE it (isn't it free?)

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> PHASE ONE

Okay, I am in Synaptic

I go to repositories

The first four check boxes are checked under "download from Internet"

At the bottom it says "to install from CD, insert your CD"

So I insert my CD and uncheck all the checkboxes that say "download from Internet"

after that? how do i make it install the desktop?

---

### Post by pbpersson on 2009-04-04
OK.....well listen......everything that is on my CD is already installed on my machine.  However, I unplugged the power from my network switch here so I was NOT connected to the network for this session.  I would think this would work for you - what I suggested in my last post.

I am including my session of me attempting to install things that are already installed.

Let me know if you have troubles and it you do, what problems you are having

I think if my machine could read packages and dependencies without the net then it was using the CD

```
phil@Ubuntu-desktop:~$ sudo apt-get install myspell-en-us
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package myspell-en-us is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  hunspell-en-us
E: Package myspell-en-us has no installation candidate
phil@Ubuntu-desktop:~$ sudo apt-get install hunspell-en-us
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hunspell-en-us is already the newest version.
hunspell-en-us set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by soomro on 2009-04-04
i get this

> Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by pbpersson on 2009-04-04
> **soomro said:**
> after that? how do i make it install the desktop?

You were told that earlier in this session - look at the posts in the thread.

It was some command line stuff.

The general command is:
[B]
sudo apt-get install <your-package-name>[/B]

---

### Post by soomro on 2009-04-04
so is this what i am supposed to do? (ahh sorry i am one of the dummies)


```
tassaduq@Lost-in-dreams:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop
tassaduq@Lost-in-dreams:~$ 

```

does this mean that the cd is corrupted?
P.S: i can install from CD on different partition

---

### Post by pbpersson on 2009-04-04
try this at your command line and when it says "insert the CD and hit enter, if the CD is already in there just hit enter:

```
sudo apt-cdrom add
```

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> try this at your command line and when it says "insert the CD and hit enter, if the CD is already in there just hit enter:

```
sudo apt-cdrom add
```

did it it mounted it succesfully also gives info about it then i do the command again but it shows the same error
```

tassaduq@Lost-in-dreams:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop
```

---

### Post by pbpersson on 2009-04-04
> **soomro said:**
> 
P.S: i can install from CD on different partition

I just read this line in your post.

What exactly does this line mean?

---

### Post by soomro on 2009-04-04
This might be of some help

```
tassaduq@Lost-in-dreams:~$ sudo apt-cdrom add

Using CD-ROM mount point /cdrom/

Unmounting CD-ROM

Waiting for disc...

Please insert a Disc in the drive and press enter 

Mounting CD-ROM...

Identifying.. [3c618d02d13ac5e949a974f0b0a41e60-2]

Scanning disc for index files..

Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures

This disc is called: 

'Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)'

Copying package lists...gpgv: Signature made Thu 30 Oct 2008 04:28:55 AM PKST using DSA key ID FBB75451

gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"

Reading Package Indexes... Done

Writing new source list

Source list entries for this disc are:

deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted

Unmounting CD-ROM...

Repeat this process for the rest of the CDs in your set.

W: Skipping non-exisiting file /cdrom/dists/intrepid/main/binary-i386/Packages

W: Skipping non-exisiting file /cdrom/dists/intrepid/restricted/binary-i386/Packages

tassaduq@Lost-in-dreams:~$ 


```

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> I just read this line in your post.

What exactly does this line mean?


by that i am trying to prove that the CD is not corrupted because i can install in on different partition but i can't do it as you say to add it to my session using the SAME cd!

---

### Post by pbpersson on 2009-04-04
Well....hey.....I gotta be honest here - I hate the command line, I really do.

I can spend hours researching command line stuff or we can do it the easy way.

Go into Synaptic, make sure under repositories the "download from internet" stuff is unchecked.

Then reload, it is a button at the top

Can you see all the packages on the CD?

And.....this is a **Kubuntu** Live CD, correct?

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> Well....hey.....I gotta be honest here - I hate the command line, I really do.

I can spend hours researching command line stuff or we can do it the easy way.

Go into Synaptic, make sure under repositories the "download from internet" stuff is unchecked.

Then reload, it is a button at the top

Can you see all the packages on the CD?

And.....this is a **Kubuntu** Live CD, correct?


LiveCD? i mean i can install it i HAVE installed it earlier from that cd?

hey i can see packages now after mounting the derive but when i install them it says its uninstallable or it is not going to be installed?

---

### Post by pbpersson on 2009-04-04
One other question I had......

You installed from a 32-bit Intrepid Ibex Ubuntu disk and now......

you are trying to add Kubuntu from a 32-bit Intrepid Ibex Kubuntu disk....

correct?

I am downloading a Kubuntu CD now.....just so we can be on the same page here

I would not THINK this would be so difficult

---

### Post by pbpersson on 2009-04-04
> **soomro said:**
> LiveCD? i mean i can install it i HAVE installed it earlier from that cd?

hey i can see packages now after mounting the derive but when i install them it says its uninstallable or it is not going to be installed?

Give me the exact errors.....not that they will mean anything, but I will have something more to read ;)

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> One other question I had......

You installed from a 32-bit Intrepid Ibex Ubuntu disk and now......

you are trying to add Kubuntu from a 32-bit Intrepid Ibex Kubuntu disk....

correct?
yes correct

> **pbpersson said:**
> I am downloading a Kubuntu CD now.....just so we can be on the same page here

I would not THINK this would be so difficult

OMG thanks for being so nice

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> Give me the exact errors.....not that they will mean anything, but I will have something more to read ;)

i can get the Abrowser to download and replace firefox.
but when i install amarok

```

amarok:
 Depends: libmysqlclient15off (>=5.0.27-1) but it is not installable
 Depends: libnjb5  but it is not installable
 Depends: libtunepimp5  but it is not installable
```

---

### Post by pbpersson on 2009-04-04
> **soomro said:**
> 
well my connection is 50/kbps so yes i dun want to waste time download it for hours.


The new CD is 88% downloaded.

Are you on DIALUP?  :o

---

### Post by soomro on 2009-04-04
and also even after uncheking the things under "downloadable from INTERNET" its downloading from internet.

and at the place of CD/DVD rom it shows the name of Ubuntu intreped ibex?

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> The new CD is 88% downloaded.

Are you on DIALUP?  :o

lol no i am on LAN which has slow internet. and plus my internet speed is slow in Linux but in windows its more than 100/kbps

---

### Post by pbpersson on 2009-04-04
> **soomro said:**
> lol no i am on LAN which has slow internet. and plus my internet speed is slow in Linux but in windows its more than 100/kbps

New CD is half burned - I always do a slow speed to avoid errors.

You are not exactly burning up the Internet at 100/kbps ;)

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> 

You are not exactly burning up the Internet at 100/kbps ;)

what do you mean by that?

---

### Post by pbpersson on 2009-04-04
> **soomro said:**
> what do you mean by that?

In the 21st century, a typical speed on the Internet is 3000kbps so you are 30 times too slow.

---

### Post by soomro on 2009-04-04
> **pbpersson said:**
> In the 21st century, a typical speed on the Internet is 3000kbps so you are 30 times too slow.

i have 2mbps which is given out to so many people that i only receive 100kps lol.

umm back to the topic please.

---

### Post by pbpersson on 2009-04-04
OKAY, I have looked on the CD and cannot find anything called kubuntu-desktop.  I do not know what I am doing wrong but I need to have breakfast, get ready, and then drive across the city to meet some people who flew in from Detroit.  I am sorry this is so dammed difficult.  If I were you, I would research this using Google - hundreds of people have had this problem before and the solution is out there but I have run out of time.

Anyway, here is my terminal session for all to see:

```
phil@Ubuntu-desktop:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [b7b72fa41f5bbdff7ad057eaa687aaf7-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)'
Copying package lists...gpgv: Signature made Wed 29 Oct 2008 03:28:34 PM MST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)]/ intrepid main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
W: Skipping non-exisiting file /cdrom/dists/intrepid/main/binary-amd64/Packages
W: Skipping non-exisiting file /cdrom/dists/intrepid/restricted/binary-amd64/Packages
phil@Ubuntu-desktop:~$ sudo apt-get kubuntu-desktop
E: Invalid operation kubuntu-desktop
phil@Ubuntu-desktop:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop

```

---

### Post by soomro on 2009-04-04
its same as i was getting.
```

tassaduq@Lost-in-dreams:~$ sudo apt-get install ubuntu-desktop
[sudo] password for tassaduq: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  libdlmcontrol3 libarts1c2a kdelibs4c2a libartsc0 libopenipmi0
  amarok-engine-xine python-pexpect libxine1-x libnet-snmp-perl libopenais2
  corosync libxine1-misc-plugins kdelibs-data libxcb-xv0 libccs3 bridge-utils
  amarok-common liblualib50 mysql-common libcorosync2 libxine1-bin libdlm3
  python-openssl libnet-telnet-perl snmp libvirt0 ruby libxen3 libavahi-qt3-1
  openipmi libxcb-shape0 openais kvm libifp4 libxvmc1 libmodplug0c2 libcman3
  libqt3-mt liblua50 libaudio2 libxcb-shm0 libmpcdec3 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 263 not upgraded.

```

this is the terminal session i got when i inserted the ubuntu CD that means if i install Kubuntu and then Ubuntu would it work?

what i need now is some one who has Kubuntu already installed to see if this works on his PC before i could end up switching to Kubuntu uselessly.

---

### Post by pbpersson on 2009-04-04
my omelet is on the stove frying now

PART OF MY CONFUSION

when I put the kubuntu CD in I thought it said Ubuntu was on the CD but that could not be

Anyway, if we are both confused that means the instructions are just wrong

---

### Post by soomro on 2009-04-04
i googled possibly the factors i could but couldn't find any one talking about this

---

### Post by pbpersson on 2009-04-04
According to my research - Googling stuff.....

kubuntu-desktop is a meta package and it might only be in the repositories, it might not be on a CD

Take a look at this

[http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html]("http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html")

---

### Post by pbpersson on 2009-04-04
> **soomro said:**
> i googled possibly the factors i could but couldn't find any one talking about this

Oh?  I found a few people online with this problem.  They were told not to use the CD, to use the repositories.

However, the link I sent - maybe you can install the individual packages?

---

### Post by Laibcoms on 2009-04-04
You need to use an Alternate-CD of Kubuntu, not the Live-CD.  If your Kubuntu CD is a "Live" CD, you'll end up downloading either way to get the "Alternate" CD version of the installer.  Might as well just install via synaptic and get kubuntu-desktop.

Btw, here's my Google Search -> [http://www.google.com/search?hl=en&rlz=1B3GGGL_enPH321PH321&q=How+to+install+Kubuntu-desktop+on+top+of+Ubuntu+via+CD%3F&btnG=Search]("http://www.google.com/search?hl=en&rlz=1B3GGGL_enPH321PH321&q=How+to+install+Kubuntu-desktop+on+top+of+Ubuntu+via+CD%3F&btnG=Search")  I used this search string: "How to install Kubuntu-desktop on top of Ubuntu via CD?"  (sometimes you have to play with words or ask a question to Google)

First result leads to: [http://ubuntuforums.org/showthread.php?t=350227](http://ubuntuforums.org/showthread.php?t=350227) entitled: [B]Install kubuntu-desktop on Ubuntu from Kubuntu live-cd

[/B];)

Btw, you may also want to read this one (I just found this, thanks to you :p ) -> [http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/](http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/)

Quoting:
> 
So installing kubuntu-desktop will not give you *all* the KDE utilities, just like installing Ubuntu did not give you all the Gnome applications. There is another meta-package called &#8220;KDE&#8221; which, when installed will give you a different set of software. **So if, after installing kubuntu-desktop, you find some of your favorite KDE apps missing, install the entire KDE suite, by installing the kde metapackage.** I find this unneccassary, as kubuntu-desktop provides me with the minimal set of tools to get my work done. If I need something extra, like, kile, that very useful LaTeX editor, then I just install kile. Less baggage, better trip!

(my emphasis)

---

### Post by soomro on 2009-04-04
ok any how i have to wait millions of minutes to get it installed. thanks for helping me though. i guess i will select that option.

---

### Post by soomro on 2009-04-04
i probably would have downloaded it after installing ubuntu but who knew i will drag it to such a hell.

i know how i downloaded 699MB file with 100/kbps :mad:

---

