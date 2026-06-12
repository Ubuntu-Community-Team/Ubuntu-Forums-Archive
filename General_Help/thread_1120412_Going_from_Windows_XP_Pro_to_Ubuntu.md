---
title: "Going from Windows XP Pro to Ubuntu"
date: 2009-04-08
forum: General Help
---

### Post by carlitx on 2009-04-08
Hi all, as the title suggests I have gotten POed at Windows for the last time. So I have officially switched to Ubuntu :) I have used it before but not allot. For I am a PC Gamer and Windows is game friendly. I know you can run almost anything and everything on Linux. So if someone could please lend a hand or either lead me to a tutorial that is easy to understand (since  am still have new to Linux and have not used it since Feisty Fawn) on how to run this list of software on Ubuntu:

Sins of a Solar Empire (Very Important)

World of Warcraft (Very important)

Paint Shop (or just lead me to a better Linux version :P)

Easy Paint Tool Sai (Very Important for I use my graphics tablet to do my 
anime drawings)

Blackberry Desktop Manager(very Important)

Winamp (or a Linux equivalent)

Something for my iPod 5.5 gen

PS: I am pretty computer savy already and catch on very fast, and am willing to learn any and all things about Linux.

PSS: If this is in the wrong topic or what not please movie it and pm a link to where it has been moved to.

---

### Post by Stupendoussteve on 2009-04-08
You are welcome to try all of those in the application "wine", but they may not all work.

For some you may need to find alternatives (there are a ton of Winamp alternatives - look in the Add/Remove under sound and video, choosing "All Avilable" - You may like Audacious in the meantime), others may not work at all (Blackberry desktop may be too low level for wine - there may be an alternative, I'm unsure).

Games are hit and miss. World of Warcraft can work pretty well, according to the wine [appDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12495") Sins of a Solar Empire should also run well.

Good luck.

---

### Post by carlitx on 2009-04-09
Thank you, I'll hunt down wine and try to get world of warcraft working. Also one last question. I am trying to hunt down aMSN but can not seem to find it anywhere. it is also not in the add/ remove programs.... Apparently i can get it through automatix. Which I used way bak when but I can not even find that any more -_-.... could you possibly lead me in 
the right direction for the latest version of it?

EDIT: one more question, I backed up the videos and other stuff from when i had windows on a friends portable HD. But the password manager for it won't prompt me when i plug it into a usb port. It just gives me a folder with a coupel mroe folders within it and a .exe. will wine work with this as well? Plus I am planing on getting a portable HD the next time i am in the city. I am not looking for anything to expensive, would you happen to know any that work well with linux?

---

### Post by sekinto on 2009-04-09
You can find aMSN using Synaptic or apt-get. To use Synaptic you would open it by going to System > Administration > Synaptic Package Manager and the searching for amsn (use a name-only search, it goes much quicker) and installing it. To use apt-get you would open a terminal by going to Applications > Accessories > Terminal and typing in "sudo apt-get install amsn" and hitting enter, type in your password, and then hit enter again.

Edit:
There are also other IMing programs available for Linux to like Pidgin or Kopete.

Edit2:
To answer one of your other questions, all external hard drives should work with Linux.

---

### Post by carlitx on 2009-04-09
Thanks again :)

when i try to mark wine for installation it gives me this error:
wine:
  Depends: libasound2 (>1.0.18) but 1.0.17a-0ubuntu4 is to be installed

what do i do?:S

---

### Post by Stupendoussteve on 2009-04-09
How are you trying to install? Have you updated the system yet?

I suggest opening a terminal and typing:
> sudo aptitude install wine

It is usually pretty smart about updating what is needed.

Note: You can do the same thing through Synaptic in the System> Administration menu

---

### Post by sekinto on 2009-04-09
I looked at the Paint Shop information page. There are two programs that should allow you to do that same things that are already installed on Ubuntu. F-Spot (Applications > Graphics > F-Spot Photo Manager) will allow you to import photos from devices and folders and will manage your photos for you and allow you to make minor corrections, GIMP (Applications > Graphics > GIMP Image Editor) will allow you to make huge adjustments and corrections.

---

### Post by matrixblue on 2009-04-09
> **carlitx said:**
> Thanks again :)

when i try to mark wine for installation it gives me this error:
wine:
  Depends: libasound2 (>1.0.18) but 1.0.17a-0ubuntu4 is to be installed

what do i do?:S

Try copying and pasting "sudo apt-get update && sudo apt-get upgrade" (without the quotation marks) in terminal. If you're using Jaunty (9.04) that may be a bug that will soon be fixed.

Instead of aMSN I'd recommend emesene. It's runs much more smoothly in Ubuntu and is very similar to the official MSN client. Only thing missing is video (for now). Search for it in Synaptic

For a music player I like Banshee. It runs smooth and has iPod sync built (in Synaptic too).

---

### Post by carlitx on 2009-04-09
Ok thanks once again, you have all been very helpful :) But now I have wine installed and  am just about there, all i need now is to know how to load up the usb hard drive. When I was on windows when i first pluged it in it prompted me with a password screen, and as i said above now it only shows up as a mounted volume that has an exe and a couple other folders inside.... how do I get that password to prompt me again so I can access the actual HD? I have tried running the .exe in wine, but nothing happens :(.

---

### Post by matrixblue on 2009-04-09
Anytime, that's what the Ubuntu community is all about.

I'm assuming that the drive you're using is encrypted using some windows based encryption software.

Take the drive to a windows machine (or use a virtual machine) and decrypt the data. Then encrypt it again using TrueCrypt ([www.truecrypt.org](www.truecrypt.org)). It's an excellent FREE (as in beer and speech) program that is available for Windows, Linux and Mac.

---

### Post by sekinto on 2009-04-09
I'm guessing the hard drive uses some sort of encryption, and includes a program that knows how to decrypt the data assuming it is given the right key. My advice would be to plug the computer into a Windows machine and put the data on a different device, format the HD, move the data back... and then if you want to encrypt it use something like TrueCrypt.

---

### Post by asmotj on 2009-04-09
Just to let everyone know if you used efax just change the filename.efx to filename.tif and inageviewer and gimp will open it 9.04

Left smallimp Micro$oft on my 45th birthday...

---

### Post by asmotj on 2009-04-09
Paint Shop Pro 7 installs under wine and works well but Gimp also works and does all I need


> **sekinto said:**
> I looked at the Paint Shop information page. There are two programs that should allow you to do that same things that are already installed on Ubuntu. F-Spot (Applications > Graphics > F-Spot Photo Manager) will allow you to import photos from devices and folders and will manage your photos for you and allow you to make minor corrections, GIMP (Applications > Graphics > GIMP Image Editor) will allow you to make huge adjustments and corrections.

---

### Post by carlitx on 2009-04-09
K, I'll get VM ware on the go and try that :P. My main reason for wanting to do this is to get my backed up firefox bookmarks and wow again. 

Also, I got Sins fo a Solar Empire Installed but wehn i go into the wine menu and try to start it it says Starting Sins of a solar empire" down on the bottom taskbar and then it disappears :S

---

### Post by sekinto on 2009-04-09
Try starting the game from the terminal using "wine <file>" and see what the output is. And also read any extra setup configuration that you may need to do on the Wine AppDB page.

And VirtualBox is also another good virtualization program.

---

### Post by carlitx on 2009-04-09
> **sekinto said:**
> Try starting the game from the terminal using "wine <file>" and see what the output is. And also read any extra setup configuration that you may need to do on the Wine AppDB page.

And VirtualBox is also another good virtualization program.

im not quite sure as to what to type after wine in terminal..... could you give me an example of what your talking about?

mean time ill try virtualbox

---

### Post by sekinto on 2009-04-09
I mean like "wine /path/to/your/file"

---

### Post by carlitx on 2009-04-09
Still no go, tells me it can not find the file.

---

### Post by Karsa on 2009-04-09
He means thatyou should type "wine /path/to/executable" in the terminal. Assuming you installed Sins of a Solar Empire in c:\Program Files\Sins of a Solar Empire\ and the .exe-file is called soase.exe type this -
```
wine .wine/drive_c/Program\ Files/Sins\ of\ a\ Solar\ Empire/soase.exe
```

Please note that I'm not sure about escaping spaces with backslash, so if it doesn't work, try using auto complete on the path (type the first part of the path then press tab).

Regarding WoW under Ubuntu, check out the massive thread in the wine-forum. It should get you started in no time as there's not much tinkering needed to get WoW running under linux. In theory just running "wine /path/to/Wow.exe --opengl" from a terminal should do the trick. If it starts, you're good to go.

Hope that helps. =)

---

### Post by carlitx on 2009-04-09
> **Karsa said:**
> He means thatyou should type "wine /path/to/executable" in the terminal. Assuming you installed Sins of a Solar Empire in c:\Program Files\Sins of a Solar Empire\ and the .exe-file is called soase.exe type this -
```
wine .wine/drive_c/Program\ Files/Sins\ of\ a\ Solar\ Empire/soase.exe
```

Please note that I'm not sure about escaping spaces with backslash, so if it doesn't work, try using auto complete on the path (type the first part of the path then press tab).

Regarding WoW under Ubuntu, check out the massive thread in the wine-forum. It should get you started in no time as there's not much tinkering needed to get WoW running under linux. In theory just running "wine /path/to/Wow.exe --opengl" from a terminal should do the trick. If it starts, you're good to go.


Hope that helps. =)
still no go with the path you provided, and when i press tb it gives me :

shane@shane-desktop:~$ wine .wine/d
dosdevices/ drive_c/

cabnt gt my

cant get it to work with my wow installation dvd's so im using the installer provided to download it on the wow website as well. still a no go for sins though :(

---

### Post by Karsa on 2009-04-09
Hmm... Where did you install Sins of a Solar Empire?  Please provide the full path (I'm assuming you installed it through wine).

If you havent already, spend a few minutes browsing [http://linuxcommand.org](http://linuxcommand.org) - It's awesome!

---

### Post by carlitx on 2009-04-09
> **Karsa said:**
> Hmm... Where did you install Sins of a Solar Empire?  Please provide the full path (I'm assuming you installed it through wine).

If you havent already, spend a few minutes browsing [http://linuxcommand.org](http://linuxcommand.org) - It's awesome!

in the default directories provided. so C:\Program Files\Stardock Games\Sins of a Solar Empire

---

### Post by Mze on 2009-04-09
Hopefully you configured Wine first, if not type **wine** in your terminal and then configure it for use, selecting the Windows environment you want it to emulate.

Use the command **winefile** to locate your executable and try to install.

---

### Post by Karsa on 2009-04-09
```
wine .wine/dosdevices/drive_c/Program\ Files/Stardock\ Games/Sins\ of\ a\ Solar\ Empire\Sins\ of\ a\ Solar\ Empire.exe
```
should do the trick :)

---

### Post by carlitx on 2009-04-09
> **Karsa said:**
> ```
wine .wine/dosdevices/drive_c/Program\ Files/Stardock\ Games/Sins\ of\ a\ Solar\ Empire\Sins\ of\ a\ Solar\ Empire.exe
```
should do the trick :)

no, it never....

and for Mze i did. and it just refuses to work.... i believe this is what made e ditch linux the last time when i was all a go for replacing windows. everything just never worked. and it is infuriating at this point..... And I am absolutely sick of a bloated Microsoft OS....

---

### Post by Mze on 2009-04-09
Software for managing your Blackberry under Linux, check [Barry]("http://www.netdirect.ca/software/packages/barry/")

For a Winamp equivalent try [Audacious]("http://audacious-media-player.org/"). Install it from the terminal.

sudo apt-get install audacious

Also please edit your profile to indicate which version of Ubuntu you are using.

---

### Post by carlitx on 2009-04-09
thanks for those 2 apps :) and there, that better? lol im on 8.10 sorry about that.

---

### Post by Mze on 2009-04-09
> **carlitx said:**
> no, it never....

and for Mze i did. and it just refuses to work.... i believe this is what made e ditch linux the last time when i was all a go for replacing windows. everything just never worked. and it is infuriating at this point..... And I am absolutely sick of a bloated Microsoft OS....

The most important thing with Linux is doing your research first before you switch. It's not guaranteed that everything works off the bat. The game you're working on, has been successfully installed and run as per the Wine db, so you may want to retrace your steps.

---

### Post by Karsa on 2009-04-09
Instead of saying "No it doesn't work", tell us what error message you recieve. It's impossible for us to guess how your system is configured.

As Mze is saying, the game is working under wine so this is most likely a simple typo in the path, please provide the output after running the command I posted in my previous post.

And don't give up just yet, have patience and don't fear the terminal =)

---

### Post by carlitx on 2009-04-09
> **Karsa said:**
> Instead of saying "No it doesn't work", tell us what error message you recieve. It's impossible for us to guess how your system is configured.

As Mze is saying, the game is working under wine so this is most likely a simple typo in the path, please provide the output after running the command I posted in my previous post.

once again sorry. here it is:

shane@shane-desktop:~$ wine .wine/dosdevices/drive_c/Program\ Files/Stardock\ Games/Sins\ of\ a\ Solar\ Empire\Sins\ of\ a\ Solar\ Empire.exe
wine: cannot find '.wine/dosdevices/drive_c/Program Files/Stardock Games/Sins of a Solar EmpireSins of a Solar Empire.exe'

---

### Post by Mze on 2009-04-09
One the [Wine page]("http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=12495") for Sins of a Solar Empire I found this:

You need this file "d3dx9_36.dll". from Jan 31st 2009. There's a link to the file and where to copy it.

Hope it solves your problem.

You may also want to look at [winetricks]("http://wiki.winehq.org/winetricks") in the future.

---

### Post by Karsa on 2009-04-09
> **carlitx said:**
> once again sorry. here it is:

shane@shane-desktop:~$ wine .wine/dosdevices/drive_c/Program\ Files/Stardock\ Games/Sins\ of\ a\ Solar\ Empire\Sins\ of\ a\ Solar\ Empire.exe
wine: cannot find '.wine/dosdevices/drive_c/Program Files/Stardock Games/Sins of a Solar EmpireSins of a Solar Empire.exe'

You've forgotten a slash in the path to the executable file =)
try this instead:
wine .wine/dosdevices/drive_c/Program\ Files/Stardock\ Games/Sins\ of\ a\ Solar\ Empire/Sins\ of\ a\ Solar\ Empire.exe

Multiple backslashes in a path makes it pretty hard to spot errors on the fly, unless you autocomplete with tab.

---

### Post by Mze on 2009-04-09
From your Wine menu under Applications, can you browse C: Drive to find your executable?

You've indicated in a previous post that you have run the installation of your game under Wine, so I'm finding it very confusing that there's no folder for your game under Program Files (your default install directory for Windows)

---

### Post by carlitx on 2009-04-09
> **Mze said:**
> From your Wine menu under Applications, can you browse C: Drive to find your executable?

You've indicated in a previous post that you have run the installation of your game under Wine, so I'm finding it very confusing that there's no folder for your game under Program Files (your default install directory for Windows)

I exploered the program files folder the first time it refused to open. All that was in there were folders. but no exe :S i figured it had something to do with wine...... and the default is program files
\ stardock games\ sins of a solar empire\ soase.exe

and now i have another problem as well, when i try to eject my first cd/dvd re-writer drive says only root can do so -_-.....

---

### Post by Mze on 2009-04-09
Can you try a reinstall then?

Please use the browse C: Drive command to locate your setup.exe or install.exe on your CD and give it another go. Nothing else comes to mind.

---

### Post by mb_webguy on 2009-04-09
> **carlitx said:**
> and now i have another problem as well, when i try to eject my first cd/dvd re-writer drive says only root can do so -_-.....

Could you post the output of the command "cat /etc/fstab" in the terminal?

---

### Post by carlitx on 2009-04-09
> **Mze said:**
> Can you try a reinstall then?

Please use the browse C: Drive command to locate your setup.exe or install.exe on your CD and give it another go. Nothing else comes to mind.

I just re-installed and it shows me the same stuff..... any ways im going to try an get some sleep. its like 4:30 AM where I am so ill try some more stuff in the morning

---

### Post by Mze on 2009-04-09
> **carlitx said:**
>  and now i have another problem as well, when i try to eject my first cd/dvd re-writer drive says only root can do so -_-.....

Try a log out and log in or just restart your machine.

---

### Post by Mze on 2009-04-09
Which version of Wine do you have installed?

---

### Post by carlitx on 2009-04-09
The restart fixed it :P, and I have a friend who I never knew was an avid ubuntu user coming over to help me in person. Thanks for all the help and support it is much appreciated guys :)

---

### Post by mixmaster on 2009-04-09
> **carlitx said:**
> Also one last question. I am trying to hunt down aMSN but can not seem to find it anywhere. it is also not in the add/ remove programs.... Apparently i can get it through automatix. Which I used way bak when but I can not even find that any more -_-.... could you possibly lead me in 
the right direction for the latest version of it?
This question has been ignored but I think it is worth warning you that automatix is basically dead, mainly because it had a habit of making a mess of systems in such a way that later software installs/deletes did not work properly and eventually a clean reinstal was the only way to recover from the situation.

Background here :[http://en.wikipedia.org/wiki/Automatix_(software](http://en.wikipedia.org/wiki/Automatix_(software))

---

