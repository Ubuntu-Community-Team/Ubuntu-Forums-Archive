---
title: "Questions on playing games in Ubuntu on dual boot system"
date: 2007-03-23
forum: Gaming &amp; Leisure
---

### Post by Usually Lurking on 2007-03-23
I'm fairly new to Linux in general and after numerous forum searches feel more confused than when I started.  

My problem is that my home PC is a dual boot system, because I already had XP and I've kept it for gaming.  However I find that I spend more time in XP than Ubuntu  because it's such a pain to reboot each time I want to go from gaming to web surfing and other stuff or vice versa.

So, I have a Windows install on one HDD with a partition where all my programs are installed.  Then I have a second HDD that contains a FAT32 Partition for my non-program files and documents with the rest of the HDD partitioned for Ubuntu.  I've looked into WINE, Virtualbox and VMware but they all seem to be recreating the Windows operating system, which I already have installed.  Then there's the whole configuration, driver and other issues which may present themselves just getting games to work.

My question is this: 
Is there a way to "use" my Windows install without exiting Ubuntu?  What seems to make sense to me would be setting up my first HDD as the "virtual PC", and actually booting into Windows only to install games or mods.  Is this possible or do I just have no grasp yet of what these programs do/are for?

Thank you.

---

### Post by milton1 on 2007-03-23
wine is an emulation layer that does not require a copy of windows, but does require some tweaking, depending on the windows program you are trying to run.

programs like vmware create virtual machines on which you could run windows within ubuntu. In these cases, you must have a copy of windows to install on the virtual machine.

Other than these, there really is no way to have more than one OS active at a time.

If gaming is really your thing, I recommend either sticking with Windows, or finding some new favorite games that have native linux ports. They are out there, you just have to look a bit.

---

### Post by cisforcojo on 2007-03-26
Agreed. If you constantly go from surfing to games, I hate to say it but you're better off in Windows. Ubuntu just isn't there yet for game development.

I personally had trouble moving from Windows to Ubuntu for this reason but now that I live in China and can't get any games (I can understand) I've fully made the move to Ubuntu.

These options are available to you:

WINE (as previously mentioned)    
Cedega (you have to pay for it and it's based on WINE)
CrossOver Office   (not REALLY for games, works well with MS Office)

Check out these websites to see if the game(s) you want to play are supported.
[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/)

Getting games to work in Ubuntu as of RIGHT NOW usually require a lot of tweaking and have slower performance. 

On the other hand, I've gotten Warcraft III and Half-Life 2 to work perfectly.

---

### Post by lakersforce on 2007-03-26
You can also easely acces your files on your windows partition while running Ubuntu. So you dont have to boot back to windows just because you have to use some of its files, or files you have installed on that partition.

EDIT: You can also write files and install programs on your windows partition while running ubuntu. This is highly dangerous and not recommended though.

---

