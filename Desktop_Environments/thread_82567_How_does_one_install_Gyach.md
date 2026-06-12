---
title: "How does one install Gyach?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by BLTicklemonster on 2005-10-26
I've seen some pretty unbelievable technobabble since I've attempted to migrate to Ubuntu, but this site takes the cake so far: [http://www.phrozensmoke.com/projects/pyvoicechat/index_pyvoice.php](http://www.phrozensmoke.com/projects/pyvoicechat/index_pyvoice.php)

Is anyone familiar with how this is done? I did everything as well as I could make out, but this is way confusing. Does anyone like ... I mean is there an "Ease of use" monitor for linux programs who goes to sites and like grades them on "Dude's got book smarts, but don't expect him to find a place to sit in a one room out-house"? I mean come on; the Linux community calls people who want to migrate from Windows but don't all kinds of unkind things, but look at what we have to deal with? Synaptic, Easy Ubuntu, and Automatix go a long way towards fixing this, yes, but when you come across a mess like that site up there, it's just baffling.

I'm a leader of a gaming clan, and we have meetings on Wed nights. We use Yahoo voice chat (okay, they do, I used to, or I go to XP, which means unplugging drives and swapping because... guess what? No clear indication as of yet on how to hook two hard drives up as dual boot.), and I try to tell everyone how great this is, and they say, "why don't you tell us instead of typing about it?" Yay, score one for the geeks.

Honestly, has no one come out with the idea of monitoring the information available to the nermal public who desires to be nerds? An award to post on their site telling the world that they are certified freaking geniuses for remembering to mention stuff from start to finish, and (look at the site) put information in a logical place, like download these files, and have them all in one place, instead of a list of every freaking imaginable file (with php paint files listed with them, I was like huh, wrong page until I looked down. god all mighty what is going on here?) that you can possibly want to have mixed in with what you actually want.

Having a hard time following me? You should, as I'm trying to be as un-followable as possible, because I'm going to learn to make how tos and tutorials like the big guys!!! 

Argh.

Am I ranting? My ranting gets raves! 

Okay, I'm calm. Breathe... breathe... fine. Now would someone please like share some intelligible information on how to get that program to install and work, please?

Thank you so much, you're all too kind.

:rolleyes:

---

### Post by BLTicklemonster on 2005-10-26
If I bump this, will it stand a better chance of being seen?

---

### Post by endersshadow on 2005-10-26
I'm writing a script right now for this that will make a very easy install for you.  Just give me a minute :)

---

### Post by endersshadow on 2005-10-26
All right, installation instructions (simplified):

1. Download [http://www.politicalcrossfire.com/temp/enderavsig/gyach-install.tar.bz2]("http://www.politicalcrossfire.com/temp/enderavsig/gyach-install.tar.bz2"), and save it to your home directory (important!).

2. Run these commands in the terminal, in sequential order:
```
tar -xjf gyach-install.tar.bz2
cd gyach
sudo ./install
```

3. You're done with installation!  To put it on your main menu, go to Applications>System Tools>Applications Menu Editor, and add a new entry where you would like.  The location of the application will be at /usr/local/bin/gyach

---

### Post by BLTicklemonster on 2005-10-26
bill@ubuntumonster:~$ tar -xjf gyach-install.tar.bz2
tar: gyach-install.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



seen that one before...

---

### Post by endersshadow on 2005-10-26
Are you sure that you saved it in that directory?

Also, try doing it using sudo.  Sorry for not putting sudo on there before!

---

### Post by BLTicklemonster on 2005-10-26
[QUOTE=endersshadow]All right, installation instructions (simplified):

1. Download [http://www.politicalcrossfire.com/temp/enderavsig/gyach-install.tar.bz2]("http://www.politicalcrossfire.com/temp/enderavsig/gyach-install.tar.bz2"), and save it to your home directory (important!).

2. Run these commands in the terminal, in sequential order:
```
tar -xjf gyach-install.tar.bz2
cd gyach
sudo ./install
```

3. You're done with installation!  To put it on your main menu, go to Applications>System Tools>Applications Menu Editor, and add a new entry where you would like.  The location of the application will be at /usr/local/bin/gyach[/QUOTE]


maybe tar -xjf gyach-install.tar.bz2.tar ?

---

### Post by endersshadow on 2005-10-26
It's definitely tar.bz2.  Try what I stated in the above post:

```
sudo tar -xjf gyach-install.tar.bz2
```

---

### Post by BLTicklemonster on 2005-10-26
bingo.

now how do I log in just plain ole yahoo?

by the way, thanks a Brazillian@@@!!!!

---

### Post by BLTicklemonster on 2005-10-26
tar -xjf gyach-install.tar.bz2.tar 

worked fine. lol

---

### Post by endersshadow on 2005-10-26
[QUOTE=BLTicklemonster]bingo.

now how do I log in just plain ole yahoo?

by the way, thanks a Brazillian@@@!!!![/QUOTE]

You're quite welcome.  As for using the program, I've not a clue, as I just got it to install easily and open up.  I don't use yahoo :lol:

---

### Post by BLTicklemonster on 2005-10-26
That's cool about the sudo. I just had to stop and look at it for a minute and realize that the actual file name didn't match the command.

That's awesome how you can do that. Absolutely incredible. I guess I'll see if anyone else can get to yahoo on it.

Thanks again.

---

### Post by endersshadow on 2005-10-27
[QUOTE=BLTicklemonster]That's cool about the sudo. I just had to stop and look at it for a minute and realize that the actual file name didn't match the command.

That's awesome how you can do that. Absolutely incredible. I guess I'll see if anyone else can get to yahoo on it.

Thanks again.[/QUOTE]

You're welcome.  It really wasn't much, but I had the install script delete the tarballs during the install so that you wouldn't have unnecessary crap on your HDD after installation.  Unfortunately, I forgot to back them up, so I deleted them when I tested it...that's what took so bloody long :lol:

It's just a simple bash script that does the install.  Basically, all of the packages except the fonts went to /usr/local/whatever, whereas the fonts went to /ttf.  I simply unpacked it in a controlled folder and then repacked it.  I had the fonts load with their native packages.  Here's the bash script, if you're interested, because it isn't on your comp anymore...I created a script that deletes itself midscript, and I'm very proud of that fact :lol:

```
#!/bin/bash

mv gyach* /
cd /
tar -xjf /gyach.tar.bz2
tar -xjf /gyach_enhanced_fonts1.tar.bz2
tar -xjf /gyach_enhanced_fonts2.tar.bz2
rm -f /gyach*
rm -f ~/gyach/*
rmdir ~/gyach
```

It's nice to note that the install of this was simply an unpacking, so that you didn't have to do a configure, make, make install with each package.

At any rate, I hope you learned something from this, and good luck getting Yahoo! to work with it!

---

### Post by BLTicklemonster on 2005-10-27
Got it to work. It has a browser that comes up, and it basically tells you which lib* files were missing if you look, or in my case pay attention.

I got them in synaptic, and it logged right on after like 10 attempts, and it kept telling me that [email]blticklemonster@yahoo.com[/email] wasn't a valid id. So I dropped the @yahoo.com and it let me in. 

Anyway, yes, I learned that:


YOU ARE MY NEW BEST FRIEND.

lol

thanks a lot.
:cool: 


Oh, I'm going to link this everywhere I see anyone who has a problem. Probably at work tomorrow, I'll get bored and google gyach ubuntu, and see what other linux forums (people go to them, not here, can you imagine that?) have people with problems, and send them here.


Oh, and let me see if I get any of this yet:

#!/bin/bash

mv gyach* /
cd /
tar -xjf /gyach.tar.bz2
tar -xjf /gyach_enhanced_fonts1.tar.bz2
tar -xjf /gyach_enhanced_fonts2.tar.bz2
rm -f /gyach*
rm -f ~/gyach/*
rmdir ~/gyach

mv gyach* / means move any gyach files to / 

cd / brings the terminal to root
tar lines just unpack or whatever
rm -f /gyach* et al means remove files within the specified parameters
rmdir ~/gyach removes the ... no, remove? 

I don't know this stuff, but I do script some, so I'm trying to figure this stuff out as I see it happen. If I tried to learn it the way other people do, I'd get lost. ADD and all that garbage...

---

### Post by endersshadow on 2005-10-27
Quite welcome again.

Do you happen to know which lib files were missing?  If it requires some lib files, it wouldn't be too hard to get the .deb versions and just throw them into the install.

Edit
rm -f /gyach* removes the tarballs in the root directory
rm -f ~/gyach/* removes the install script (the script deletes itself...sorry, I just like that) in your home/gyach folder
rmdir ~/gyach just removes the directory gyach from your home folder

Otherwise, everything was correct in how it worked.  The most important line is #!/bin/bash which identifies it as a bash script.  Note that I had to do a sudo chmod +x install on the file when I created it to make it executable.

---

### Post by BLTicklemonster on 2005-10-27
No, I can't remember which lib files it was, sorry. And I missed the chmod. It seemed as if voice would work, but by the time I was done, everyone was gone. Hopefully it's pretty straight forward from this point on.

---

### Post by blueberrycheesecake on 2005-10-27
i have successfully installed gyach. however whenever i click on the 

action start webcam ... my PC hangs.

what's the solution for this?

---

### Post by BLTicklemonster on 2005-10-27
No idea on the web cam, if you have extra sensory perception, perhaps you can go to the website that is linked in the first post and decypher enough to perhaps come back and share (in humanspeak) what you learned? 

Good luck, I'm sure someone will drop by with an answer. (Question: if you try running a program from the terminal, does it stay up and show events so you could perhaps jot down what you see? I'm not familiar enough with all this yet.)

Oooh, and another thing!!!

This isn't the place, but I'm sure others feel the same way, but HOW DO I GET TO WHERE IF I COPY SOMETHING I WANT TO PASTE, I DON'T HAVE TO KEEP THE ORIGINAL TEXT IN THE ORIGINAL WINDOW SHOWING? If I copy something from a page, close it, then try to paste it somewhere else, it's lost. Is this a glitch, or something they never got around to, or is there a setting I can change to enable a clipboard somewhere? And if so, why is it not enabled by default? The ability to copy and paste into the terminal is absolutely ... cool, and it would be nice if a clipboard function were standard.

---

### Post by BLTicklemonster on 2005-10-27
So ah.... man, GYach is full of stuff I have never seen before. What's it all do? Is there a site that lays it all out in Earthling speak?

---

### Post by endangst on 2006-01-09
[QUOTE=endersshadow]All right, installation instructions (simplified):

1. Download [http://www.politicalcrossfire.com/temp/enderavsig/gyach-install.tar.bz2]("http://www.politicalcrossfire.com/temp/enderavsig/gyach-install.tar.bz2"), and save it to your home directory (important!).

2. Run these commands in the terminal, in sequential order:
```
tar -xjf gyach-install.tar.bz2
cd gyach
sudo ./install
```

3. You're done with installation!  To put it on your main menu, go to Applications>System Tools>Applications Menu Editor, and add a new entry where you would like.  The location of the application will be at /usr/local/bin/gyach[/QUOTE]


Sorry for the dumb question as I am a Linux newbie, but how do I move that file from my desktop to my home directory?

Please help...thanks! :smile: appreciate it.
Endang

---

### Post by endangst on 2006-01-09
Excellent.  Gyach installed just fine. ;)   Thanks for the how-to!

...but voice doesn't work, even when I click the green button and the pY! Voice chat button. ugh...

---

### Post by sabitha on 2006-01-09
try run the pyvoice with this :

$ /usr/local/share/gyach/pyvoice/pyvoiceui.py

if the program run you will see the voice window so u can tes your microprone to see if that works (you can hear your self on that test )

if you dont see the voice window try edit the line with gedit on vi 
 code :
$ sudo gedit /usr/local/share/gyach/pyvoice/pyvoiceui.py

find the line EXPAND+FILL and change with EXPAND&FILL
try open the voice window again to see if that works

---

### Post by leech on 2006-01-09
There is a much easier way to install gyach on Ubuntu....
[http://sourceforge.net/project/showfiles.php?group_id=57756](http://sourceforge.net/project/showfiles.php?group_id=57756) Download the 
Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm and then just run 'sudo alien Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm' from the command line.

This will create gyach-enhanced-pyvoicechat_1.0.7-2_i386.deb, then you just need to run 'sudo dpkg -i gyach-enhanced-pyvoicechat_1.0.7-2_i386.deb'

Simple, effective and goes into the Synaptic manager. :D  

I haven't played around with it much, since the last time I tried using Gyach was version 1.0.5 or 6 and it crashed more than Windows 95 did.  I did try 1.0.7 at one point, left it on for a day or two (not really using it, but waiting in the background) and it didn't crash, which was a huge improvement, but of course your experience may vary on that.  

One last thought on Gyach, you say that their website isn't made for humans, neither is the interface!  Looks like someone from KDE made the interface on it ;)  But it does try to create every little function of the Windows Yahoo messenger, so you can't really blame the creator of it's bloated interface.

Leech

---

### Post by Horndog on 2006-01-09
> **endangst]Excellent.  Gyach installed just fine.  said:**
> ...but voice doesn't work, even when I click the green button and the pY! Voice chat button. ugh...[/COLOR]

It doesn't work for me either.  ...now how do you uninstall it? (a non *.deb file)

---

### Post by Horndog on 2006-01-09
[QUOTE=leech]There is a much easier way to install gyach on Ubuntu....
[http://sourceforge.net/project/showfiles.php?group_id=57756](http://sourceforge.net/project/showfiles.php?group_id=57756) Download the 
Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm and then [color=red]just run 'sudo alien Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm' from the command line.[/color][/Quote]
```

horndog@HornDogsHouse:~$ sudo alien Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm
sudo: alien: command not found 
```:confused:

---

### Post by alberello2005 on 2006-01-14
hi! i use u guide for install gyach on my ubuntu breezy. well gyach work, i chat with other people and see theyr webcam…,but they cant seemy webcam,the see only a grey screen…
do u know why?? thx
sorry for my bad english im italian…
W spaghetti!

---

### Post by Ricky-9000 on 2006-02-19
[QUOTE=Horndog]```

horndog@HornDogsHouse:~$ sudo alien Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm
sudo: alien: command not found 
```:confused:[/QUOTE]

You need  to install alien before you can use it. 
Run this in shell then try it again.

sudo apt-get update
sudo apt-get install alien

now alien is installed and you can try installing gyach again:D

---

### Post by Ricky-9000 on 2006-02-19
[QUOTE=alberello2005]hi! i use u guide for install gyach on my ubuntu breezy. well gyach work, i chat with other people and see theyr webcam…,but they cant seemy webcam,the see only a grey screen…
do u know why?? thx
sorry for my bad english im italian…
W spaghetti![/QUOTE]
 Im just guessing here. But your web cam is probably not installed properly. Have you used it with any application other than Gyach? My guess is that it doesnt work there either. If that is the case see if you can find any posts reguarding your webcam. If your webcam works with other apps post back here and maybe someone will know the answer.

---

### Post by Ricky-9000 on 2006-02-19
Ok I have got Gyach installed now (it shows as installed in Adept). My question now how do I start gyaht? Hopw can I add it to my Kmenu? Sorry for the n00b questions this is my first attempt at linux on a PC.

---

### Post by krypto_wizard on 2006-02-19
This is a good post....i did't know about all the above mentioned things. 

Thanks OP and all others.

---

### Post by rory_fireshaper on 2006-02-20
Alright, I have GyachE installed, but when I try to connect I either get an Error in connect(): 111 error or the program freezes up. Any suggestions?

Edit: Nevermind, I got it. I installed it with the RPM and it works fine now. Thanks!

---

### Post by Ricky-9000 on 2006-02-21
Has anyone figured out a way to get gyach into  Kmenu on Kubuntu?

---

### Post by Ana Carolina on 2006-03-04
Hi...
I tried and it worked...
But how do I get the webcam to work?

Thanks
Ana

---

### Post by sabitha on 2006-03-04
first you have to install your driver for your webcam corectly
try spca5xx driver you can search on this forum or on wiki ;)

---

### Post by muzaki on 2006-03-04
[QUOTE=sabitha]try run the pyvoice with this :

$ /usr/local/share/gyach/pyvoice/pyvoiceui.py

if the program run you will see the voice window so u can tes your microprone to see if that works (you can hear your self on that test )

if you dont see the voice window try edit the line with gedit on vi 
 code :
$ sudo gedit /usr/local/share/gyach/pyvoice/pyvoiceui.py

find the line EXPAND+FILL and change with EXPAND&FILL
try open the voice window again to see if that works[/QUOTE]
I got these

dilli@kodo:~$  /usr/local/share/gyach/pyvoice/pyvoiceui.py
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIManager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.TreeView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints, longs, or tuples



What does it mean? I just chat with my friend, but not able to use voice or webcam......

---

### Post by muzaki on 2006-03-05
update: sorry ...my bad :D 
now works like charm

---

### Post by jose.eugene on 2006-03-06
I already installed gyach. its working but sometimes it disappears. also everytime load gyach this appears on the screen. where can i find these files? i used the synaptic but found none


** Plugin '/usr/local/share/gyach/plugins/gyach-gpgme.so' could not be loaded because of an error:
libgpgme.so.6: cannot open shared object file: No such file or directory
Location: /usr/local/share/gyach/plugins/gyach-gpgme.so
** Plugin Loaded:  'GyachE-XMMS' 
** Plugin '/usr/local/share/gyach/plugins/gyach-mcrypt.so' could not be loaded because of an error:
libmcrypt.so.4: cannot open shared object file: No such file or directory
Location: /usr/local/share/gyach/plugins/gyach-mcrypt.so
** Plugin Loaded:  'Blowfish-Internal' 
 Plugin Loaded:  'GyachE-Photos' 
 Loaded 3 plugins from '/usr/local/share/gyach/plugins'.

---

### Post by Black Moon on 2006-04-30
jose.eugene, you can find those files: gpgme.so, libmcrypt.so.4, and mcrypt.so in Synaptic Package Manager.

---

### Post by rykel on 2006-07-03
[QUOTE=endersshadow]I'm writing a script right now for this that will make a very easy install for you.  Just give me a minute :)[/QUOTE]

hey, thanks a lot for giving us the script... i was just having a headache (AS USUAL) abt how to install a non-deb on ubuntu dapper, but gyach looks attractive because it promises to voice chat with my contacts on yahoo messenger...

since you have the expertise, would you be able to spread some joy by making a gyach autopackage? the autopackage website is at [http://www.autopackage.org](http://www.autopackage.org)

thanks!!!   :rolleyes:

---

### Post by loell on 2006-07-05
for future readers, hope this might help :)

[GYachI]("http://ubuntuforums.org/showthread.php?t=190900&highlight=gyachi")

---

### Post by cosmint_1973 on 2007-01-05
Thanks Dude, can I please have this posted on my Romanian Ubuntu portal ? I will translate it but also mention the source of information here.

---

### Post by kcallis on 2007-01-11
Ok, I tried the tar package that was listed on page one, but when I tried to fire up gyach, I got the following error:

 gyach: error while loading shared libraries: libltdl.so.3: cannot open shared object file: No such file or directory

Of course, this is probably an issue with this being a AMD-64bit machine. So later on today, I am going to try and build this from source. I will get you posted!

K.

---

### Post by loell on 2007-01-11
try this instead .

[http://www.dpb.org.uk/ubuntu/edgy_6.10/gyachi_1.0.5-1_amd64.deb]("http://www.dpb.org.uk/ubuntu/edgy_6.10/gyachi_1.0.5-1_amd64.deb")

---

### Post by kcallis on 2007-01-12
> **loell said:**
> try this instead .

[http://www.dpb.org.uk/ubuntu/edgy_6.10/gyachi_1.0.5-1_amd64.deb]("http://www.dpb.org.uk/ubuntu/edgy_6.10/gyachi_1.0.5-1_amd64.deb")

Well, that was on the money... The only thing that is a slight problem is when I start it on the command line, I get a lot of packet information coming up on the screen... But that was easily solved when adding the application to the applications menu.

The only thing that I am missing is that there doesn't seem to be a way to create aliases like I could do with gaim. Oh well, a small price to pay... Now to test out the 2-way audio and web cam  viewing...

---

### Post by bennykenkireth on 2007-12-24
Try doing the following
1. Download Gyach-Enhanced-pYVoiceChat-1.X.X-X.i586.rpm
2. This is available on [http://sourceforge.net/project/showfiles.php?group_id=57756](http://sourceforge.net/project/showfiles.php?group_id=57756)
3. Doing alien Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm
4. That will generate a .deb file
5. Do dpkg -i on the deb file generated.

It worked like a charm for me. I have been able to use even the webcam. Haven't tested sound yet though

Regards
Benny Kenkireth

Homepage :[http://www.tcs.tifr.res.in/~benny](http://www.tcs.tifr.res.in/~benny)

---

### Post by bigbrovar on 2007-12-27
> 2 Days Ago 11:00 PM
bennykenkireth 	
Re: How does one install Gyach?
Try doing the following
1. Download Gyach-Enhanced-pYVoiceChat-1.X.X-X.i586.rpm
2. This is available on [http://sourceforge.net/project/showf...group_id=57756](http://sourceforge.net/project/showf...group_id=57756)
3. Doing alien Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm
4. That will generate a .deb file
5. Do dpkg -i on the deb file generated.

It worked like a charm for me. I have been able to use even the webcam. Haven't tested sound yet though

Regards
Benny Kenkireth

Homepage :[http://www.tcs.tifr.res.in/~benny](http://www.tcs.tifr.res.in/~benny)

mehn ur guide worked like a charm thanks :guitar:

---

