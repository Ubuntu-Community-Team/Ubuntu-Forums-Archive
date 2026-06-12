---
title: "Vmware the easy way"
date: 2010-12-16
forum: Desktop Environments
---

### Post by sp-1070 on 2010-12-16
***Installing into Vm ware The easy way***.

I have been using ubuntu a long time but i seem to always need windows  for some gaming witch is a pain in the *** now if you don't really have  the time,skills or simply motivation to create a dual boot here is  you're solution.

A save way to run ubuntu while running windows what more do you want.
The best way in my opinion is to follow this tutorial with dual screen's  on either laptop or desktop but certainly are not needed to do this.

Lets get to the actual works then

First you'll want to get Vm ware

go to:
> [http://www.vmware.com]("http://www.vmware.com/")
[LIST=1]
[*]Register
[*]Activate
[*]Download
[*]Install
[/LIST]
[I][B]
The installation process.[/B][/I]

You just go to the downloaded file en fire it up go trough the run/cancel pop ups you know what to do.
> 

[LIST=1]
[*]Just Next
[*]Choose installation folder
[*]Check for updates (recommend to leave it marked updates are important)
[*]Help improve (im selfish i never help ) but be glad some people do
[*]Choose if you want it on the desktop/start/quiklaunch
[*]Continue
[*]Restarting time
[/LIST]
[I][B]Some extra info and insight on Vmware
[/B][/I]
Vm  ware is quite something,Basically its an empty computer with no os on  it nothing you just download Anny live disc/ISO and set it to mount at  start up and it will start whatever it was you put there.

So to speak say you wanted to play old dos games but don't want to screw around with dos-box and stuff?

You  start vmware with win95 disc mounted it will start the setup and such  you walk trough that and you have a general PC with win 95 inside you're  vmware.
From that point on you wont have to mount Anny more seeing it save's whatever you do just like Anny ordinary desktop PC.

So yeah you have a computer in a computer pretty cool huh.

For this tutorial i have (of course) Downloaded the ubuntu 10.10 server edition.
In principle it should work with Anny other os's ISO you have,

> This  is where the second screen's porpoise jumps in you would have for an  instance win XP left and UNIX or mac OS for that matter on the right so 2  desktops 1 pcSo make sure you can find everything easily put the live ISO in a map with ISO'S thats what i recommend.
(with me its c:/isos)

Ok lets go system making then.

> 

[LIST=1]
[*]Start Vm Ware
[*]Accept the agreement (as if you ever read it)
[/LIST]
So there we are the vm ware GUI.
A lot of things to see and to try just not right now.

We will focus on the right side of the screen

> 

[LIST=1]
[*]Create a new virtual machine
[*]open a virtual machine
[*]Upgrade to vm ware workstation(cash and stuff)
[*]help
[/LIST]
Obviously we will start wit clicking on
```
Create a new virtual machine[/quote]

pops up

> 

[LIST=1]
[*]Installer disc
[*]installer disc image file(iso)
[*]I will install the operating system later (blank hdd)
[/LIST]
We will start by using the last one so we can set up some options before going all in.

pops up

> 
[I][B]Guest operating system

[/B][/I]
[LIST=1]
[*]Microsoft windows
[*]Linux
[*]Novell NetWare
[*]Sun Solaris
[*]Other
[/LIST]
[I][B]Version

[/B][/I]We choose linux wich brings us to a next screen 

> 
[B][I]Virtual Machine Name 
[/I][/B]
Here the version is usually stated but feel free to name it whatever you want

[I][B]Location
[/B][/I]
This is the location it will save the "machine" it will be a file witch you can later start see this as the hdd of the image.

Mine looks like this;

C:/Vmware/Machines/machine 1 (operating system's name)

Next comes up the size you want to give it,
i use generally 10 gig's for a UNIX distro.

Now comes a cool option.

Store as one file or as multiple,
id  say one file witch is clean and nice if you are so eager to make a  vmware box you can move around create on of 7 gig's and put it on a usb  stick or buy a bigger usb stick.
On to the next one.

> 

Also a very nice one.

This shows what your machine will be


[LIST=1]
[*]Name
[*]Location
[*]Version
[*]Operating system
[*]Hard disk
[*]Memory
[*]Network adapter
[*]Other devices 9cd-roms floppy's usb's printers and sound-cards etc etc)
[/LIST]
With the cooler button below

Customize hardware
Now i don't use to high a spec's its my net-book you know,but to those of you who have a monster muncher well have some fun.
finish

You're done you now have an absolutely empty computer.
Witch really is kinda cool.

So now you see at the left side of the GUI 

> 
Home
Ubuntu (or whatever name you choose)
In the home tab you can create new machines and all that,where interested in the second.
Lets install a OS

Start the player.
A black screen appears and of course it will output 

> No operating system foundOn the bottom of the screen a thingy pops up with some buttons.

> ***Restart VM  Change CD/DVD settings Never remind me***Well go to the 
[code]change CD/DVD settings
```Here you will choose what to start with an CD/DVD in the physical drive/ISO

I will use an ISO but the outcome should be the same using the CD/DVD
browse to you're ISO

Go OK

```
Restart vm
```(using the button below)

Here you go the setup starts,now sometimes you're setup wont start but give an output like.

This kernel requires an x86-64 CPU but only detected an ......CPU 

Shut it down
Edit virtual Machine's option's to what you need.
Then try again and install the operating system you want.

Now you have it you have managed to set up you're system witch is way cooler and twice as effective as an dual boot (if you're on windows emulating something else)

Have fun and i hope you all like this tutorial.

Also posted in absolute beginner talk dindt know if this belonged here

---

### Post by AlexanderDGreat on 2011-03-27
How do you autostart VMware with Guest OS Windows XP upon booting in Ubuntu, and move it to the 2nd workspace, do you have any ideas? Thanks.

---

### Post by pafufta503 on 2011-03-27
lol!!

---

