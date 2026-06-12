---
title: "dont want wubi , next ?"
date: 2009-06-05
forum: General Help
---

### Post by pantera10 on 2009-06-05
ok i installed ubuntu thru wubi...i started using ubuntu...LOVED IT...now i wanna make the switch...but the thing is wubi doesnt let me put more then 30gb :S ...so i was wondering if theres an alternative method or soemthing...i have a 150gb free and will be giving atleast 120-130 to ubuntu

:popcorn:

---

### Post by Tibuda on 2009-06-05
[Install]("http://www.psychocats.net/ubuntu/installing") from the [Live CD]("http://www.ubuntu.com/getubuntu/download") installer.

---

### Post by tenmilez on 2009-06-05
My preferred method is to nuke the whole drive and start over. There's less finagling, but you have to backup everything you want to keep to an external something (CD/USB/etc) or it'll get lost. 
Then what I usually do is create, in this order:
boot partition (1gb, but you could go way less)
root partition for ubuntu (I think I use 20gb)
home partition for ubuntu (this is your big one)
windows partition (whatever you want, but I'd keep at least 20gb)

If you want windows to think it's on a drive called C: (it bugs the crap out of me when it doesn't have a C:) then there is a *little* finagling.

To do this I would say to get the live CD and (after you've backed everything up) go into gparted (system>admin>partition editor?) and delete all the partitions and then make a new one, format it as ntfs (or leave it unformatted), give it the size you want to allocate to windows, and then specify that you want it at the end. It's all graphical so it should be fairly obvious. 

Then install windows normally.

Then install ubuntu (boot the live CD and click the install icon on the desktop). 
When it gets to the part where it asks about your hard drive setup it'll say guided - use free space; guided - use everything; manual. Pick manual. 

Then you put in your /boot partition, / partition, and /home partition. Don't worry about the other ones because they'll default to / if you don't give them somewhere else to live (everything descends from /, right?)

The reason you want a boot partition is because then you can multi boot multiple versions of linux more easily (that's my opinion anyway), but technically you could have it automatically included in / (just don't make the partition at all)

The reason you want a /home is because if you upgrade or reinstall (or even, sometimes, use another version of linux) then you don't have to setup everything again and you don't lose your files. I had to reinstall and because I had a seperate /home it automagically found everything, including my desktop wallpaper and custom keyboard/mouse shortcuts and knew what to do with it.

---

### Post by Therion on 2009-06-05
You could do a couple of things.

1.  **Dual boot**.  This would mean running the two operating systems side-by-side and choosing which one you boot into each time you restart your PC.  Very good if you want ease the transition from Windows to Ubuntu.  You don't mention if you're running XP, or Vista, or what, but there are guides for how to set up a dual boot with pretty much all the current Windows releases here (see the sidebar to the right if you're not running Windows XP):

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)


2.  **Full install**.  This means wiping your hard drive of Windows and running nothing but Ubuntu.  If you think you're ready for that you would simply need to boot using the LiveCD and then click on the Installer icon on the desktop.

---

### Post by Mirages on 2009-06-05
I think the only way to do that is to wipe your hard-drive and repartition it. to give it the amount of hard disk space you want to give it

installing just ubuntu as the only partition is cake, but having 2 partitions one for linux the other for windows is slightly more complicated. 

before you consider doing this have you maxed out the total amount of space on your wubi so that ubuntu can no longer install more apps? I run a wubi on one of my machines and I only gave it 20gigs and I have space to spare for more applications.

if you want to repartition the drive for dual boot here is a nice guide
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
i assume you are using windows and its a good idea to backup your  data.
[http://windowshelp.microsoft.com/Windows/en-US/Help/699ce30c-13f1-46ec-9684-e84bf4109dd81033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/699ce30c-13f1-46ec-9684-e84bf4109dd81033.mspx)
and this is how you would resotre the files to the freshly installed windows partition
[http://windowshelp.microsoft.com/Windows/en-US/Help/55e35b7f-58ab-409b-997c-bcc81d64c4271033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/55e35b7f-58ab-409b-997c-bcc81d64c4271033.mspx)

you dont have to use dual boot at all if you want. assumning your machine is powerful enough you could just install ubuntu as your ony partitiion and then install windows on a virtual machine (VirtualBox) or use WINE for windows apps

lots of choices. good luck

---

### Post by pantera10 on 2009-06-06
alright everyone thanks alot for your replies...

heres my plan...im on vista...and the only reason why i'll be keeping vista is for shockwave player plugin and online gaming like Red Alert 3 and stuff...thts it...which is why i think 20gb partition for vista should be sufficient...
so yes i will be dual booting and not doing the full installation..

>tenmilez : i did not understand a word u said :P ...i think u wanna if my data is backed up or not ? ans: yes it is

the virtual box thing sounds like a pretty good idea aswell...but do you think it'll be better then running a live version of vista ...as ive stated earlier i only need vista ofr SWF and GAMING !
also can u define " machine is powerful enough "

---

