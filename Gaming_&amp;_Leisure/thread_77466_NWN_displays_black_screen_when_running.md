---
title: "NWN displays black screen when running"
date: 2005-10-16
forum: Gaming &amp; Leisure
---

### Post by vahju on 2005-10-16
System spec:  AMD 1700
ATI Radeon 9700
My Linux experience:  Total linux knob but can work with detailed instructions.  Have run Ubuntu and Linspire only.

I read a bunch of forums here and at Bioware.  I was able to install all the files needed to run NWN then ran into graphics error (failed to initialize).  Did some investigation in these forums and updated ATI graphics drivers, which updated etc/X11/xorg.conf file.

Now when I run NWN from nwn directory the screen goes black, i see a cursor in upper left corner for a moment, then the screen returns to my desktop.  The terminal window shows the message "Fatal signal: Segmentation Fault (SDL Parachute Deployed)".  I copy the results of my terminal window.

I am currently running as non-root so not sure if that has any affect.  Is there a way to run NWN as root?  How do I login as root in intial login screen?

Any help would be apprecieated.

***TERMINAL WINDOWS RESULTS***
guest@hubuntu:~$ cd /home/guest/nwn
guest@hubuntu:~/nwn$ ./nwn
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
guest@hubuntu:~/nwn$ ./nwnmain
bash: ./nwnmain: No such file or directory
guest@hubuntu:~/nwn$ ./nwnmain
bash: ./nwnmain: No such file or directory
guest@hubuntu:~/nwn$ sudo ./nwn
Password:
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
guest@hubuntu:~/nwn$ ./fixinstall
Checking for required files

PASSED: ambient directory exists
PASSED: data directory exists
PASSED: music directory exists
PASSED: override directory exists
PASSED: miles directory exists
PASSED: nwm directory exists
PASSED: chitin.key exists
PASSED: dialog.tlk exists
PASSED: nwmain exists
PASSED: patch.key exists

Fixing case

ambient
..........................................................................................
data
.............................
dmvault
..
hak
.
localvault
.......................
music
..............................................................
override
....
portraits
.

Checking for problem files


Checking for permissions

PASSED: nwn.ini is writable
PASSED: nwnplayer.ini is writable
PASSED: saves is writable
PASSED: localvault is writable
PASSED: tempclient is writable
PASSED: dmvault is writable
PASSED: /home/guest/nwn is writable

You are ready to run Neverwinter Nights.

guest@hubuntu:~/nwn$ ./nwn
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

---

### Post by vahju on 2005-10-17
I'm not impatient just doing some research.  Also wanted to make sure that to add acronym for NWN in case some don't know that its Never Winter Nights.

I was lurking in this forum and found this post, [http://www.ubuntuforums.org/showthread.php?t=77486](http://www.ubuntuforums.org/showthread.php?t=77486).

Do I need to enable ATI drivers?  If so, how do I do that?

---

### Post by Perfect Storm on 2005-10-17
Yes, you need to enable it if you want to play games which are depended on 3D acc.

Take a look here: [http://ubuntuforums.org/showthread.php?t=76116](http://ubuntuforums.org/showthread.php?t=76116)

---

### Post by vahju on 2005-10-17
I am totally lost in that thread and not even sure if I have all the packages installed to perform those steps.  Is alien part of Ubuntu 5.10?  I hate asking for someone to hold my hand through this but I am a linux newbie.  If I need to start over I will and delete the nwn directory.

---

### Post by Perfect Storm on 2005-10-17
Okay, try this then: [http://ubuntuforums.org/showthread.php?t=76057](http://ubuntuforums.org/showthread.php?t=76057)
or 
[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)

I don't have ATI, so this is the only help I can give you.
I'll hope someone with ATI card can guide you.

---

### Post by vahju on 2005-10-17
I ran fglrxinfo and shows the following:
display:  :0.0 screen: 0
OpenGL vender string: ATI Technologies Inc.
OpenGL renderer sting:  RADEON 9700 PRO Generic
OpenGL version string:  1.3.5272 (X4.3.0-8.16.20)

I also ran glxgears and fgl_glxgears both displayed another window with gears turning and gears turning in a rotating box.  So it appears that 3d acceleration is turned on.

I have nwn directory in my Home folder running as non-root.  Could there be a problem with permissions on nwn folder and its contents.  I am not sure how to change permissions since I can't do this as current user and I don't know the terminal command to do this.

I feel I am getting closure but still NWN is out of my reach (on my linux box at least).

---

### Post by Perfect Storm on 2005-10-17
Did you install NWN this way, my work with this: [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)
and mine is in /home directory.

---

### Post by vahju on 2005-10-17
Checked out that link and thought it would be promissing.  Did chmod command first just in case.  When I run the installer I get the below message:

guest@hubuntu:~/nwn$ ./nwn_129_final.run
Verifying archive integrity... All good.
Uncompressing Neverwinter Nights 1.29 for Linux...............................................................................
/home/guest/.setup8774: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
guest@hubuntu:~/nwn$

Thinking that my current install could be causing issues I recreated the nwn directory and still get same error.

---

### Post by Perfect Storm on 2005-10-17
Have you the libgtk1.2 installed?
```

sudo apt-get install libgtk1.2
sudo apt-get install libgtk1.2-common

```

---

### Post by vahju on 2005-10-17
I went through synaptec to get lib files you pointed out.  Then tried to run installer got prompted for first CD, ejected, then kept getting prompted for second cd.

I checked [http://icculus.org/~ravage/nwn/faq.html](http://icculus.org/~ravage/nwn/faq.html) and one of FAQs stated you needed wine.  I went through synaptec for that too.  Seems like I am having nothing but issues.

so I cancelled out of install and checked terminal, saw the following message:

guest@hubuntu:~/nwn$ cd /home/guest/nwn
guest@hubuntu:~/nwn$ ./nwn_129_final.run
Verifying archive integrity... All good.
Uncompressing Neverwinter Nights 1.29 for Linux...............................................................................

SETUP_CDROM has not been set.
Attempting to use the following mount points to extract
the game data from your Neverwinter Nights CDs:

 /mnt
 /mnt/cdrecorder
 /mnt/cdrom
 /mnt/dvd
 /media/cdrecorder
 /media/cdrom
 /media/dvd
 /cdrom


Extracting Install Disc 1


An existing install of Wine/WineX has not been found.
Attempting to use the bundled binaries instead.

Extraction failed!


modules/Contest Of Champions 0492.mod -> modules/contest of champions 0492.mod
modules/DEMO - A Bucket of Gnolls.mod -> modules/demo - a bucket of gnolls.mod
modules/DEMO - Goblins vs Kobolds.mod -> modules/demo - goblins vs kobolds.mod
modules/DEMO - House of Doors.mod -> modules/demo - house of doors.mod
modules/DEMO - Thar be Rats! Yarrr!.mod -> modules/demo - thar be rats! yarrr!.mod
modules/DEMO - The Cat Lady.mod -> modules/demo - the cat lady.modmodules/The Dark Ranger's Treasure.mod -> modules/the dark ranger's treasure.mod
modules/The Winds of Eremor.mod -> modules/the winds of eremor.modmodules/To Heir is Human.mod -> modules/to heir is human.mod
Unable to find file 'chitin.key'
Unable to find file 'data'
Unable to find file 'dmvault'
Unable to find file 'localvault'
Unable to find file 'servervault'
Unable to find file 'texturepacks'
guest@hubuntu:~/nwn$

---

### Post by Perfect Storm on 2005-10-17
I had trouble also with it to find the wine, but then I uninstall wine and let it use the bundled binaries instead.


 Well first I tried without wine, no luck. Then I installed wine with no luck. But got lucky when I uninstalled wine.

---

### Post by vahju on 2005-10-17
I went through synaptic and wine is not installing correctly.  How can I install using apt-get if I can't update sources.list?  I tried to update sources.list but I think you have to do this via root.

---

### Post by Perfect Storm on 2005-10-17
sudo apt-get update
sudo apt-get install wine

---

### Post by Omnios on 2005-10-17
> Is there a way to run NWN as root?

 If you installed NWN with sudo .... 
 Then you will more than likely have to start it with "sudo ./nwn" from expereience I have had the black screen and I would get kicked out I also had to make a shell script to make an menu item. This is posted in 5.04 forums. I have also tryed changing owners and permitions but still had a few problems with it. Try sudo ./nwn in terminal in the game difectory you have nwn installed in.

---

### Post by vahju on 2005-10-17
I think I am at my wits end working on this today.  I tried using the installer from that external site and it didn't work so I decided to go back to Bioware and use there instructions, [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html).

Did everything to the letter using NWN directions:
1. unzipped nwresources129.tar.gz into nwn directory
2. unzipped nwclient129.tar.gz into nwn directory
3. unzipped linuxhotclientupdatexxto165eng.tar.gz to nwn directory
4. ran ./nwn from terminal within nwn directory and got following message:
guest@hubuntu:~/nwn$ sudo ./nwn
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

Still getting black screen and error in which I am at a loss.  I need to take a break from this and take out some frustration (play nwn on windows box).  If anyone has any suggestions to fix this I am all ears.  I should be able to work on this tomorrow after 5pm EST.

If one of you gurus think talknig me through it would be better then PM a time that is good for you.

Hoping to cut the Windows lease some day.

---

### Post by Omnios on 2005-10-17
Might be a config problem. I would recomend a long descriptive post on the Bioware  Linux section forum and mention you use Ubuntu. I have had a few problems solved by doing this as a lot of the people there are pretty Linux intense.  

 Umm stupid question but did you download and untar the proper nwn linux patches. I had the gold + hords and asked if it was ok only to do the last patch and they said should be ok but it was not and though my game ran it was unplayable. Also there is specific tar commands mentioned that replace old files. Anyways good luck.

---

### Post by vahju on 2005-10-17
[QUOTE=Omnios]
 Umm stupid question but did you download and untar the proper nwn linux patches. I had the gold + hords and asked if it was ok only to do the last patch and they said should be ok but it was not and though my game ran it was unplayable. Also there is specific tar commands mentioned that replace old files. Anyways good luck.[/QUOTE]

Not sure if I used the right commands.  I just mimicked the tar xvzf [filename] command found in this bioware thread, [http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72).

I then used Archive Manager to extract the other files with options to overwrite and replace files into nwn directory (hope that was correct).

I did originally post at bioware but thought it better to start here since 5.10 just came out.  Here is the link to bioware thread i created, [http://nwn.bioware.com/forums/viewtopic.html?topic=455232&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=455232&forum=72).

I did run ./fixinstall from nwn directory before raising the white flag this evening and when I ran it the first time it gave me a warning about several files not having write permissions.  Then I ran sudo ./fixinstall and everything was correct.  Still got black screen.

Thanks everyone for your help.  Hopefully this will get resolved and this post helps future ubuntu newbies.

---

### Post by Omnios on 2005-10-17
Id try untarring it with terminal that could be the problem, counting how you unzipped the file and where you unzipped it to expecialy with sudo which is root might affect the install. Fileroller dafault is to untar as user (your name) which would explain the file permition problem. As to fix install I thought that was to clean up the tar and allow it to be used again not shure about that.  Personaly I used terminal to move the tar to my nwn directory and used terminal to untar it.

 I think it will work if untared with the terminal.

---

### Post by leech on 2005-10-18
What particular version of nwn do you own?  I have the platinum version and when I installed it in Hoary, I used the linux installer script that someone in the forums made for it.  Works like a charm.  [http://www.paradoxinc.net/~icarus/files/install-nwn.sh](http://www.paradoxinc.net/~icarus/files/install-nwn.sh)

Good luck, I'm going to be installing this on my laptop right now.

Leech

---

### Post by vahju on 2005-10-19
Currently in work but I have the Plantinum 5 disc version that has SoU and HoU expansions.  Any tricks to using the install script that a Linux newbie should know?

---

### Post by Omnios on 2005-10-19
Think I read the Platinum Linux version is bugged I would do a platinum search on the bioware site and look into what Leech wrote.

---

### Post by leech on 2005-10-19
[QUOTE=vahju]Currently in work but I have the Plantinum 5 disc version that has SoU and HoU expansions.  Any tricks to using the install script that a Linux newbie should know?[/QUOTE]

Easy Howto.

1:  Enable the Universe repository;  Open up Synaptic Package Manager, System -> Administration -> Synaptic Package Manager.  Enter in your Password.  Click on Settings, and select Repositories.  Click Add.  Then put check marks in the box for Community maintained (Universe) and while you're at it, may as well put one in Non-free (Multiverse)

2: After clickng OK on both dialogs, click Search and type in unshield.  It will show three packages, just double click on unshield and it will ask you if you also want to mark libunshield, which is required.  Click mark, then cick Apply.  Unshield is required by the installer.

3: After downloading the script [http://www.paradoxinc.net/~icarus/files/install-nwn.sh](http://www.paradoxinc.net/~icarus/files/install-nwn.sh) right click on it and select properties.  Then select the Permissions tab.  On the Owner line, put a check in Execute.  Click close.

4: Double click on the install-nwn.sh and select Run in Terminal.

5: A terminal window will open, asking if you're installing the CD or DVD version.  Select the proper one, then enter.  Then it asks for the cdrom path.  On Ubuntu, this will be /media/cdrom for the first drive.  Next is the install directory.  By default this is /usr/local/games/nwn.  Change this if you'd like.  If you're going to install there, you will need to use sudo.  If you don't have multiple people using your computer, then just put it in /home/<username>/nwn.  Next it asks for the current patch version that is located in the users home directory (1.66 is the newest patch).  Note, if you haven't downloaded the patch (English_linuxclient166_xp2.tar.gz) then it will ask you if you wish to download it.  

Important:  When the script asks "Do you wish for the script to mount the CD (Y/n)" you'll want to choose NO.  This is because Ubuntu will automatically mount the CDs for you when you insert them.  For the group, it is safe enough to just hit enter (since you should already be in the users group.)  

Last but not least, start inserting the CDs.  It starts off with disk 2.  (Hint: You'll know when to hit enter on the script, because Nautilus will open up a window showing what is on the CD/DVD you just entered.  This shows that it is mounted and the script can do it's thing)  To eject a CD/DVD, right click on the icon on the desktop and select eject.

6: There is no step number 6

7: After installation, if you want an icon either on the desktop or on the menu you will need to edit the nwn start up script.  Just 'gedit ~/nwn/nwn' and add under the line 'cd /home/<username>/nwn' (without the 's) ```
# This script runs Neverwinter Nights from the current directory
```

7a: For a desktop Icon, simply right click on the desktop, and select Create Launcher.  Enter the Name (Neverwinter Nights), You don't really need Generic name or Comment.  For the command you can either Browse to /home/<username>/nwn and select the nwn file.  For the Icon, you can click on the button that says No Icon, and then browse to /home/<username>/nwn and select nwn.ico.

7b: For a menu entry.  Select Applications -> System Toos -> Applications Menu Editor.  Then in the left hand column, select Games.  Then press the New Entry button.  The rest is exactly like installing the desktop Launcher above.  Then quit the Menu Editor and you will have a Neverwinter Nights menu entry under Applications -> Games.  

8:  Now load the game up.  After the initial boot screen, you will be asked for the CD-Keys.  They are printed inside the front cover of your manual.  You will have to enter the key for the Original Neverwinter Nights twice.  I have no idea why, but it asks for it twice.  The others are only required once.

That concludes the Nwn how to for now.  I may (if I have time, which I seem to lately, since I have been laid off for two weeks now) I will clean this up, include screenshots and also add n how to get the Movies to play as well. 

Hope this is helpful.

Leech

---

### Post by leech on 2005-10-19
[QUOTE=Omnios]Think I read the Platinum Linux version is bugged I would do a platinum search on the bioware site and look into what Leech wrote.[/QUOTE]

Actually it's not bugged at all, follow my instructions (I tried to write them as newbie friendly as I could)  It took me long enough...  :D  I was in the middle of a few other things and you even did a post while I was writing.

Leech

---

### Post by vahju on 2005-10-20
I have to say your instructions are awesome and have gotten me alot closer.  When it prompted me for the update I tried to type in the name of the file and for some reason that didn't work, so I said yes to download update.

Now NWN loads but I can't see the text of any of the main menu items and only have access to main client and SoU.  There is no entry for HoU.  Does this installer account for SoU and HoU?

I only got prompted 3 times for my keys (could not see text in buttons).  First two times put in Main client key, then third time put in SoU.  Did not get prompted for HoU.  Is there some key related files in nwn directory that I should delete so I can retry or do I need to download other update files.

Since you helped me a great deal my turn to help you.  If your job seeking in IT world try [CompuCom]("http://www.compucom.com/") and [Oxford & Associates]("http://www.oxfordcorp.com/").  I currently work for CompuCom and its a good company.  Oxford & Associates is a IT placement firm mainly dealing with contract to permanent positions.  O&A (no references to Oppie & Anthony) has regional offices just in case your overseas.

---

### Post by vahju on 2005-10-20
I was able to figure out the last part by downloading update for HoU from bioware and extract into nwn directory.  I was then prompted for HoU key and badda bing I was able to login and play online.

Thanks for everyone's help and patience.  If you ever feel like playing nwn I habit Neversummer MidWest under PW Action.  I plan on make a character with _Ubuntu as part of the name to show my support.

The moderators can mark this one solved.

---

### Post by Perfect Storm on 2005-10-21
It's really nice to hear you got it Solved ^^

---

### Post by leech on 2005-10-22
[QUOTE=vahju]I have to say your instructions are awesome and have gotten me alot closer.  When it prompted me for the update I tried to type in the name of the file and for some reason that didn't work, so I said yes to download update.

Now NWN loads but I can't see the text of any of the main menu items and only have access to main client and SoU.  There is no entry for HoU.  Does this installer account for SoU and HoU?

I only got prompted 3 times for my keys (could not see text in buttons).  First two times put in Main client key, then third time put in SoU.  Did not get prompted for HoU.  Is there some key related files in nwn directory that I should delete so I can retry or do I need to download other update files.

Since you helped me a great deal my turn to help you.  If your job seeking in IT world try [CompuCom]("http://www.compucom.com/") and [Oxford & Associates]("http://www.oxfordcorp.com/").  I currently work for CompuCom and its a good company.  Oxford & Associates is a IT placement firm mainly dealing with contract to permanent positions.  O&A (no references to Oppie & Anthony) has regional offices just in case your overseas.[/QUOTE]


That's great you got it solved, and thanks for the job seeking advice, oddly enough I am looking for a job.  It always stinks when you get laid off.

I've found when you get no text, it is a permissions issue.  I find it easier just to wipe out and start over on the install if that happens, of course copy any save files you may have.  

Leech

---

### Post by raglinmason on 2006-10-29
> **leech said:**
> 
I've found when you get no text, it is a permissions issue.  I find it easier just to wipe out and start over on the install if that happens, of course copy any save files you may have.  

Leech

You could try doing a 'sudo chown -R user.user nwn' to take possessions of all the files in the NWN folder (including the folder), or run fixinstall again to see what it says. Always run fixinstall after anything changes...

---

### Post by the8thstar on 2007-04-24
Hello,

I can't see anything in there! All I have is a series of boxes to input the codes upon first startup and no indication of text whatsoever!!! CAN SOMEONE HELP ME PLEASE?

---

### Post by the8thstar on 2007-04-24
Alright, I figured it out... it was indeed an isue with the permissions.

---

### Post by iblis on 2007-11-24
> **the8thstar said:**
> Alright, I figured it out... it was indeed an isue with the permissions.
I had a similar issue, no text/black text/textures not loading, recently when updating to v1.68, even after the fixinstall script was run.

It is indeed a permissions issue, and 'chown -R user.group directory' fixes it.

(just noting this in case anyone else finds this thread in a google search :D )

---

### Post by AngelBreath on 2008-10-08
An old post , but a  good game..:) I followed the tutorial here and i installed the game very easy. My problem is that i m writing the cd-key and take "invalid cd key". I tried my original key : same 
                       I tried a pirate key    :same

Any idea? ( i have changed the nwn folder be "read-write".

---

