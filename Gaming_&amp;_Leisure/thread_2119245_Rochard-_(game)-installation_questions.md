---
title: "Rochard- (game)-installation questions"
date: 2013-02-23
forum: Gaming &amp; Leisure
---

### Post by Hodevah on 2013-02-23
HI. I recently downloaded Rochard. And it seems like a neat game. my problem is on  installing this game. Specifically  how so?

Within the folder is an executable (application/x-executable), a README  file that informs next to nothing other than the required specifications (all of which I well exceed) and a directory named 'rochard_data' which basically contains TGA images  (image/x-tga), unknown files (application/octet-stream), Ogg Vorbis  audio files (audio/x-vorbis+ogg), a couple of other directories  containing application/x-msdownload types (application/x-msdownload). 

I moved the files and folders into usr/local/games/Rochard_x64 because I think that this is where the installation might need to be. 

Do I need to compile and build this game. How so, please? 
Or do I need to extract some additional files here via right-click?

I have used my friend google but he is not friendly atm. Hence giving me  no info or any leads to go to go where I can get some information. 

I have also done a bit of research here on the forum but there does not seem to be much information here. The game itself is from Indie Bundle.

Does anyone have any ideas?

---

### Post by GWBouge on 2013-02-23
Just extract the folder in the archive to your home directory, and double-click the 'Rochard.app' file (may have to set it as executable, I don't remember).  I got it from a Humble Bundle as well, and there wasn't any installation necessary, just extract and play.

Side-note:  Getting it with that bundle, you should also be able to get links/keys to install it through the Ubuntu Software Center or Steam if you'd rather do it that way.  It was recently added to Steam's Linux game list.

---

### Post by Hodevah on 2013-02-23
Alright. So when I click on the application/x-executable I get a *PyPar2* pop-up along with a number of Parchive archives (application/x-par2).  The pop-up has 2 tabs. One for 'check' and the second for 'create'. 

Screenshots below of what I mean


[IMG]http://i.imgur.com/bk9qDcj.png[/IMG]



[IMG]http://i.imgur.com/f7bpXU4.png[/IMG]


There is a 'directory-browse' selection option for me to find a *Par2* file supposedly allowing me to being locating it at /home/usr. There is a *.pypar2 *folder/directory; however, nothing located inside it. 


Also, along with those Parchives some of them are named Rochard.vol063+37.par2, Rochard.par2, Rochard.vol031+32.par2 just to list a few. It seems that if these Parchives are intended for the game, that some of them are missing. I dont know for sure. It just seems like it. 

Screenshot below of what I mean:


[IMG]http://i.imgur.com/Bvup0hM.png[/IMG]




I forgot to mention earlier that along with the Rochard_X64 folder is another folder.directory containing a number of [I]

(1) unknown (application/octet-stream)[/I], [I]
(2) TGA images (image/x-tga)[/I], 
(3) Ogg Vorbis audio (audio/x-vorbis+ogg),
(4) 3 other folders which are Mono, Managed, and Recources.

I think all of the above numbered files/folders/directories are just game related files for when playing.



.

---

### Post by GWBouge on 2013-02-25
Not really sure here ... is the Rochard file set as executable?  As in, not does it have an application/x-executable file type, but does it have execute permissions?  It seems like it's trying to extract the file, not run it.

---

### Post by myromance123 on 2013-02-25
In your  third picture, you have the Rochard executable (it's that purplish icon that's like a square turned to it's side slightly).

Right click it, go to Properties. Under the Permissions tab, at the bottom is a a line that says "Allow executing file as program". Tick that.

Click close. Now double click that Rochard executable. The game should start up no fuss. However, if it still doesn't run then we will use the Terminal to figure out why.

Open a Terminal (search for "Terminal" in Ubuntu's Dash).

Type "./" then drag the Rochard executable into the Terminal ( you may have to wait for a 1 second for the Terminal to recognize it). Now you should have a long command that will start Rochard through the Terminal. Just hit Enter, and we'll see what it says. Post any errors it may give here.

---

### Post by Hodevah on 2013-02-25
> **myromance123 said:**
> In your  third picture, you have the Rochard executable (it's that purplish icon that's like a square turned to it's side slightly).

Right click it, go to Properties. Under the Permissions tab, at the bottom is a a line that says "Allow executing file as program". Tick that.

Click close. Now double click that Rochard executable. The game should start up no fuss. However, if it still doesn't run then we will use the Terminal to figure out why.

Open a Terminal (search for "Terminal" in Ubuntu's Dash).

Type "./" then drag the Rochard executable into the Terminal ( you may have to wait for a 1 second for the Terminal to recognize it). Now you should have a long command that will start Rochard through the Terminal. Just hit Enter, and we'll see what it says. Post any errors it may give here.

This did it. I selected 'run as executable'. Game started. Thanks a bunch guys.  :popcorn:

Even dragging the executable into Terminal started the game.

One other thing, I dont think that I need those .par files do I? 

Those were extracted for some reason that I dont know why. I dont think that they were necessary. I do recall that for some reason after I initially extracted Rochard, the second folder that I mentioned earlier was extracted and then afterwards, I must have selected to extract the executable as I thought that is what was necessary to eventually play the game and for some reason had software manager ask me to download the pypar2 from its repositories. Hence I kept getting this search for and extract these par2 files.

I have navigated to the .pypar2 directory. There is an .xml file inside with the following content: 

> <prefs version="1"><pref name="spnRedundancyLvl" type="int" value="5"/><pref name="nbkAdvanced" type="int" value="0"/><pref name="spnFirstBlock" type="int" value="0"/><pref name="outputDlgWidth" type="int" value="550"/><pref name="grpBlocks" type="str" value="radBlockDynamic"/><pref name="spnMemoryUsage" type="int" value="16"/><pref name="grpAction" type="str" value="radActionRepair"/><pref name="chkUniformFileSize" type="bool" value="False"/><pref name="outputDlgHeight" type="int" value="400"/><pref name="spnBlockCount" type="int" value="1"/><pref name="nbkMain" type="int" value="1"/><pref name="grpRedundancy" type="str" value="radRedundancyLvl"/><pref name="chkUseAdvSettings" type="bool" value="True"/><pref name="spnBlockSize" type="int" value="1"/><pref name="spnRecoveryCount" type="int" value="7"/><pref name="spnRedundancyCount" type="int" value="100"/><pref name="grpParity" type="str" value="radParityCount"/></prefs>
I have no clue what this means. I dont even think it is n ecessary. By the way, I did remove the pypar executable being installed through the repositories and hence my belief this .xml file is not needed. But still would like some feedback though.

---

### Post by myromance123 on 2013-02-25
I'm glad you got the game working :)

I'm uncertain if you need the pypar files.

What you can do is make a copy of your Rochard folder, and place it somewhere else. Then, delete all the par files. Try running the game. If it doesn't work, then you need the par files. So, just copy the files from your backup folder you just made.

Hope that helps!

---

### Post by Hodevah on 2013-02-25
Done. Everything still works great after deleting them. Thanks a bunch for your help. ):P

---

