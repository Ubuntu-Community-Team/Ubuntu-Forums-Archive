---
title: "Urban Terror 4.1 Install Script"
date: 2008-01-01
forum: Gaming &amp; Leisure
---

### Post by tshirtz1013 on 2008-01-01
I updated and modified a script to install Urban Terror 4.1.
a great FPS  thats absolutely free and very linux friendly.   

- Automatically Downloads the 4.1 Full Zip from the internet
- Checks md5 hash to verify download integrity
- Extracts the Game into a directory
- Provides options for 32-bit version Desktop Shortcut and Menu Entry
- Provides options for 64-bit version Desktop Shortcut and Menu Entry
- Automatically makes .i386/x86_64 files executable

To run this script :

- Open a terminal and $ cd <Directory where you put the script>
- $ chmod +x URT41.sh
- $ ./URT41.sh

Let me Know if you have any problems or any ideas.

-- The original Script was from Urban Terror 4.0 and was written by Nexu --
-- I rewrote the file wget address and wrote the chmod lines for the .i386/x86_64 files
-- Also fixed the Menu Entry and Desktop Shortcut features  and added an option for the 64-bit version
-- updated the md5sum for new file version
-- fixed invalid icon name

---

### Post by cherva on 2008-01-01
```
cherva@mitosoft:~/Desktop/Urban Terror$ ./URT41.sh 
 ______                      _______                  __               
|   __ \.-----..-----..----.|     __|.---.-..----..--|  |.-----..-----.
|   __ <|  -__||  -__||   _||    |  ||  _  ||   _||  _  ||  -__||     |
|______/|_____||_____||__|  |_______||___._||__|  |_____||_____||__|__|  

                        Urban Terror 4.1 Installer

        This program will help install UrbanTerror 4.1 on your system.
        Provided by :   Beer-Garden.org and The Paranoid Penguin

 Press enter key to continue or control-c now to abort


./URT41.sh: line 82: [: too many arguments
==> List of UrbanTerror 4.1 gamedata downloads host:
-------------------------------------------------
[1] BeerGarden

Enter a number for download location: 1
Downloading UrbanTerror 4.1 gamedata  ...
--18:27:42--  http://maps.game-host.org/UrbanTerror_41_FULL.zip
           => `UrbanTerror_41_FULL.zip'
Resolving maps.game-host.org... 70.84.61.155
Connecting to maps.game-host.org|70.84.61.155|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 754,307,397 (719M), 750,061,984 (715M) remaining [application/zip]

100%[====================================>] 754,307,397  300.37K/s    ETA 00:00

19:08:52 (296.64 KB/s) - `UrbanTerror_41_FULL.zip' saved [754307397/754307397]

Verifying UrbanTerror_41_FULL.zip integrity ...OK
Extracting game files ...And Making Executable
checkdir:  cannot create extraction directory: /home/cherva/Games/UrbanTerror41
ERROR: Archive extraction failure.
cherva@mitosoft:~/Desktop/Urban Terror$ 


```

---

### Post by tshirtz1013 on 2008-01-01
Think I fixed it.... I updated the Script in my previous post. Let me know if that works. I had it set to install into the /Games/Folder but that was a folder I made. Not one that exist by default.  Sorry about that.

---

### Post by cherva on 2008-01-01
Do you even test this script on your pc before posting it ?

---

### Post by tshirtz1013 on 2008-01-01
> **cherva said:**
> Do you even test this script on your pc before posting it ?


Yes, I did. It worked fine, but not everyones computer is like mine. so I had to fix a few things. I am sorry its not perfect. I have tweaked it pretty well now. 

I am sorry that it didnt work at first for you. I did re-upload a new version. I appreciate you letting me know it had issues though. I can't fix what i dont know is wrong.

---

### Post by cherva on 2008-01-01
Good job but there are some errors if the folder you are trying to run the script has a name with two words and a space between them (ex untitled folder)
```
Please choose your Game Type Shortcuts
(R)egular-32bit |(S)pecial-64bit | (N)one R
Making a desktop icon ...OK
Making a menu item ...OK
rm: cannot remove `/home/cherva/Desktop/untitled': No such file or directory
rm: cannot remove `folder/.urtinstaller': No such file or directory

Installation is done. Time to Lock And Load


|_  _  _  _   _  _  _ _| _  _   _  _ _ 
|_)(/_(/_| - (_|(_|| (_|(/_| |.(_)| (_| 
              _|                     _| 
If A Free Beer and a Free Game Had a baby....That's Us.


Be sure to check out the BeerGarden TeamSpeak Server @ TS.BEER-GARDEN.ORG:8900



cherva@mitosoft:~/Desktop/untitled folder$ 


```

---

### Post by tshirtz1013 on 2008-01-02
Did that effect the install or execution of the game or did it just screw up when trying to clean up. I mean I see the error so its apparent it didnt clean up properly after the script was done, But does everything else work ? like you got urban Terror now ?

---

### Post by cherva on 2008-01-02
Everything is working the problem is for the cleaning  part of your script

---

### Post by dante76 on 2008-05-25
good work.:guitar:


Thanks

Dante

---

### Post by xrobwx on 2008-07-01
What if you already have it downloaded? I have only been using ubuntu for about a week so go easy on me.

---

### Post by Vadi on 2008-08-11
Here's an easier way to get it: [http://www.getdeb.net/search.php?keywords=urban+terror](http://www.getdeb.net/search.php?keywords=urban+terror)

---

### Post by cristo-father on 2008-08-11
or [http://www.linuxmint.com/forum/viewtopic.php?f=32&t=14524](http://www.linuxmint.com/forum/viewtopic.php?f=32&t=14524)

---

### Post by zedoctor on 2009-02-11
yeh, works fine if you already have the zip. just put zip in the same folder

it will say this if it has detected the downloaded file

HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

Verifying UrbanTerror_41_FULL.zip integrity ...OK


and run commands 

chmod +x URT41.sh

and

./URT41.sh

-Thanx

the other install .sh i found didn't work 

another note. don't change your resolution too 1440x900 i got some serious bugs (no mouse, Crashed etc had to re install it)

Thanks for this one 
:thumbsup:
\\:D/

---

### Post by taurus0405 on 2009-03-15
fdgdfg legal kara shwwwwwwww

---

### Post by Sealbhach on 2009-03-15
> **taurus0405 said:**
> fdgdfg legal kara shwwwwwwww

OK thganhks.


.

---

### Post by 71CH on 2009-04-23
How can I uninstall this including the menu entry?  Thanks.

---

### Post by aonegodman on 2009-09-07
BUMP! Ditto. How to remove Urban Terror and all it's children off my computer????

---

### Post by knxville on 2009-12-04
Ive now installed Urban Terror through the script you've posted, but when I try to open it, nothing happens at all?

---

### Post by SNOOPY817 on 2009-12-06
Just download it right here [ftp://ftp.snt.utwente.nl/pub/games/urbanterror/UrbanTerror_41_FULL.zip](ftp://ftp.snt.utwente.nl/pub/games/urbanterror/UrbanTerror_41_FULL.zip)[]("ftp://ftp.snt.utwente.nl/pub/games/urbanterror/UrbanTerror_41_FULL.exe") and once its done downloading, extract it and what not then open up the urban terror folder then look for a file called "ioUrbanTerror.i386" right click it go to properties go to permission then check the little box next to "Execute" then close then double click "ioUrbanTerror.i386" and your ready to play.[URL="http://ftp//ftp.snt.utwente.nl/pub/games/urbanterror/UrbanTerror_41_FULL.zip"]
[/URL]

---

### Post by darren1996 on 2009-12-20
thanks:)

---

### Post by Sand &amp; Mercury on 2009-12-21
^ If you've already got it downloaded, just unzip and play. All good!

---

### Post by eerjay on 2011-10-14
I keep getting a 404 error after I enter a number for location.

---

### Post by uRock on 2011-10-15
Closed for Necromancy.

Please start a new thread for your problem.

---

