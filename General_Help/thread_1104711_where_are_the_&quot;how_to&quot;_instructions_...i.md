---
title: "where are the &quot;how to&quot; instructions ...if any"
date: 2009-03-23
forum: General Help
---

### Post by attilab on 2009-03-23
instead newcommers asking same questions again and again
new to ubuntu, fine, having many questions, fine
same as thousands others comming from other OS looking for some answers,
but
and this is a bigger issue for me at least, learning ubuntu can not be a full time job, point.
I have asked questions, ppl answered me with language and dictionary as I would allready know something...and many of my posts left there nobody visiting anymore...
free source, as a name says its free, but its not! me personally spent abnormal time to get out from the door and started making my first baby steps. Windows programs you buy and have support, I call up the guy and after minutes I am up and running...
OK, here we are in different game,
my simple question is and assume many others might ask the same:
- is there a collection of "how to" directions for (not even mentioning the steps before these): 
1. dictinarry of similar functions (ubuntu-windows)
2. dictionary of similar programs
3. how to's like
how to access my NAS drive (username and passwords conflict)
how to move my contacts or full email from Outlook 2007
how to move my favorites
how to read my acrobat pdf
how to pack or unpack zips, arj, 
how to install downloaded third party applications (have some sitting on my desktop)
how to ...
and so on, these categories shall be fairly easy to place somewhere here..
my son (MAC user)just left me laughing, he sad "good luck"
well, I won't give up, but feel kind a frustrated with things like >>getting answers from ppl who don't really having time for me,

---

### Post by bodhi.zazen on 2009-03-23
There are tons of sites that can help.

I advise you start with the wiki :

[https://help.ubuntu.com/](https://help.ubuntu.com/)

There is an unofficial wiki which is like a FAQ :

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)

From there google is your friend.

---

### Post by williane on 2009-03-23
I use the same site for Windows and Linux support:

[http://www.google.com](http://www.google.com)

:p

---

### Post by Therion on 2009-03-23
> **attilab said:**
> 2. dictionary of similar programs
Several.  Here is just one, but Google will find you several more:  [http://www.linuxalt.com/](http://www.linuxalt.com/)
> **attilab said:**
> how to move my contacts or full email from Outlook 2007
That can be done using the Export function but it's tricky and I haven't done it in some time...

> **attilab said:**
> how to move my favorites
If you use Firefox, export the Bookmarks using the Export function: Bookmarks, Organize Bookmarks, Import and Backup, Export function.  That or install the "Foxmarks" extension.  You can also Export your "Favorites" in Internet Explorer and Import them into Firefox; just use "Import" instead of Export function.

> **attilab said:**
> how to read my acrobat pdf
Install the xpdf suite.

> **attilab said:**
> how to pack or unpack zips, arj, 
Install the P7zip-full package.

> **attilab said:**
> how to install downloaded third party applications (have some sitting on my desktop)
Depends on the specific package.

---

### Post by 123456789123456789123456 on 2009-03-23
As far as I know, Ubuntu has not come out with a step by step guide.  There is help, in the help section there is a guide on ubuntu.  it covers alot of things you mentioned.  not all of them

I can help with others
adobe or an adobe reader should have come with ubuntu.
double clicking on the pdf file should open it in the correct program
if you have a zip file, or any other compressed file, simply double clicking it loads up a program, I don't remember the name of it off hand, that decompresses, and can create compressed files.

Installing third party applications.
Under synaptic packet program.
You go to the repository section, and choose all the repositories listed.
after you tell it to reaload the information, under add/remove programs program, choose from the drop down box, all third party applications.

If you know what program you want by name, you can either find the program from the person/group that created it, and download, compile that way.  Or through the terminal
type 
sudo apt-get install "", where "" is the name of the program you want.

the apt program, will find, download, configure, and install the program.
I can help more with this if you like.

I don't know how to transfer from outlook express, but evolution mail, being a clone of outlook, should have an option in it.
Transfering favorites, is done through firefox.  it may be under file, inport.

Functions that are simular to windows.
Double clicking is the same in both OS's
If you click the close box on a ubuntu window, that is a program, it closes the program, same as in windows.
I'm not entirely shure how much you want.
let me know.

---

### Post by attilab on 2009-03-23
thanks all for google, I missed that one........life is just not long enough.......sometimes
I didn't checked the apt, but me downloaded from Real their player, have tons of movies.avi on my NAS drive, my FTA satellite is down, need to put something on the TV. so have a RealPlayer on my desktop, how to install it?
BTW, my NAS drive (HDD for 4 PCs attached to workgroup), I can see it on the network but can't open it because have a username=Guest and password="blank". I don't want to put a password there because of my kids and wife would eat me having allways to type it. any other way ubuntu could access it?
allready testing the exports to firebird, need more time,
thanks

---

### Post by mocoloco on 2009-03-24
> **attilab said:**
> so have a RealPlayer on my desktop, how to install it?

Go to realplayer.com, DON'T just click on the "download realplayer" button, instead underneath you have the option to download a DEB package.  That's what you want.  Double-click it, click "Install", provide your password.  You're done.
.deb is the extension for Ubuntu packages (and Debian, which Ubuntu is based on).  You'll learn these things as you go.

---

### Post by attilab on 2009-03-24
in case I allready download certain (any) program, its here on my desktop, 
might happen its not directly supported from ubuntu (??)but the website sad its for linux as well ?! (this for using programs I got used to untill I learn the new interface)
what is a command for something like that, step by step
what I did I let ubuntu do the updates, also I installed some other  supported programs (I guess I ended up having some duplicates, need to investigate), but what if it is not supported? it will still install?

thanks all

---

### Post by bodhi.zazen on 2009-03-24
> **attilab said:**
> in case I allready download certain (any) program, its here on my desktop, 
might happen its not directly supported from ubuntu (??)but the website sad its for linux as well ?! (this for using programs I got used to untill I learn the new interface)
what is a command for something like that, step by step
what I did I let ubuntu do the updates, also I installed some other  supported programs (I guess I ended up having some duplicates, need to investigate), but what if it is not supported? it will still install?

thanks all

Depends on the application, how it was packaged, and your skill at managing Linux. 

Obviously your are new and installing applications from outside the repositories is a very broad question.

You should start by learning to use the repositories first. The repositories are quite large.

Again, did you check the wiki ? The wiki is, IMO the place to start as it is the "offical" acn community supported documentation.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by mocoloco on 2009-03-24
I'm guessing you're still talking about realplayer, when you click on the download that just says for linux, it's a .bin file, which should work on any Linux distribution.  I would still recommend the .deb, because then you can manage it with synaptic to update or remove it later, but if you want to install the .bin file it should still work fine.
Click Applications -> Accessories -> Terminal
Type in these commands:
```
cd Desktop
sudo ./RealPlayer11GOLD.bin
```

Commands are case-sensitive (lower or upper case matters).  You'll be asked to enter your password.

---

### Post by attilab on 2009-03-25
```
cd Desktop
sudo ./RealPlayer11GOLD.deb
```

attilab@attilab-laptop:~$ cd Desktop
attilab@attilab-laptop:~/Desktop$ sudo ./RealPlayer11GOLD.deb
sudo: ./RealPlayer11GOLD.deb: command not found

```
sudo apt-get install "", where "" is the name of the program you want.
```

attilab@attilab-laptop:~/Desktop$ sudo apt-get install RealPlayer11GOLD.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package RealPlayer11GOLD.deb

attilab@attilab-laptop:~$ sudo apt-get install RealPlayer11GOLD.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package RealPlayer11GOLD.deb

what I am doing wrong?
it is my good educational project
[COLOR="Red"]what is the command to read from desktop and install?[/COLOR]
the file=package is here, but if I doubleclick, start the installation but hang, I left it overnite and nothing.
[COLOR="Red"]how to check the package integrity? not just this one but overall?[/COLOR]

---

### Post by jmore9 on 2009-03-25
Almost all documentation for linux is here

[http://mirror.facebook.com/ldp/](http://mirror.facebook.com/ldp/)

And as said before just google what you want info for

---

### Post by bodhi.zazen on 2009-03-25
```
sudo dpkg -i[FONT=monospace] [/FONT]./RealPlayer11GOLD.deb
```

---

### Post by lisati on 2009-03-26
> **bodhi.zazen said:**
> ```
sudo dpkg -i[FONT=monospace] [/FONT]./RealPlayer11GOLD.deb
```
Alternatively, double-click on the .deb file's icon......

---

### Post by attilab on 2009-03-26
double clicking worked, was a bit weird way but OK.
finally ended up having a limited RP, in XP gives you a choise to download the online movie, not here
BTW
I am writing down/printing to pdf all my notes from online, depend from which OS I am currently in. Noticing, the pdf's are not compatible?!
In XP I am using Acrobat 9 reader and CutePDF printer, in ubuntu I can not read those files on my shared D drive, and vise reversa...?

---

### Post by absolutezero1287 on 2009-03-26
It seems to me that the OP has failed to read any documentation. This forum is where you post after you have done research. We are not here to help you not spoon feed you. Just be glad you're not on the Gentoo or archlinux forums.

You say that learning Ubuntu can't be a full time job and I agree but you can't just wander in here and ask for a full blown Ubuntu guide. Help yourself so we can help you. Either way, when you were using Windows didn't you have to learn how to use it? I really don't see the issue.


> I have asked questions, ppl answered me with language and dictionary as I would already know something...and many of my posts left there nobody visiting anymore...
Again, people assume that you've already done your research about whatever your problem is. 

> free source, as a name says its free, but its not! me personally spent abnormal time to get out from the door and started making my first baby steps. Windows programs you buy and have support, I call up the guy and after minutes I am up and running...
GNU/Linux distributions are free and open source. There is extensive documentation online to help you. The forums should be a last resort. Of course, if you would have done your research this would have been revealed to you by now.

> OK, here we are in different game,
my simple question is and assume many others might ask the same:
- is there a collection of "how to" directions for (not even mentioning the steps before these):
1. dictinary of similar functions (ubuntu-windows)
2. dictionary of similar programs
3. how to's like
how to access my NAS drive (username and passwords conflict)
how to move my contacts or full email from Outlook 2007
how to move my favorites
how to read my acrobat pdf
how to pack or unpack zips, arj,
how to install downloaded third party applications (have some sitting on my desktop)
how to ...
and so on, these categories shall be fairly easy to place somewhere here

Move contacts from Outlook. That's a fairly common question. Again...google.

How to read a .pdf and unpack archives. Even when I was on my first day of using Ubuntu I did my research and learned all this on my own.

Everything you're asking is in the wiki or can be found via a search engine. This is sheer laziness.

---

### Post by attilab on 2009-03-26
> **absolutezero1287 said:**
> ... We are not here to help you not spoon feed you. Just be glad you're not on the Gentoo or archlinux forums...[QUOTE=absolutezero1287;6963793]

how did you found my post, on google? thanks for comming in...

[QUOTE=absolutezero1287;6963793]Move contacts from Outlook. That's a fairly common question. Again...google.[QUOTE=absolutezero1287;6963793]

.......and again, nobody wrote down/have a solutions (2007 Outlook <-> TB) what actually works...or I am wrong?

[QUOTE=absolutezero1287;6963793]How to read a .pdf and unpack archives. [QUOTE=absolutezero1287;6963793]
..... again, the two systems using pdf creators what are not compatible (my Acrobat in XP and whatever you offer me on the other side)... what me to do w/tons of my docs and instructions in L? running in and out thru the dual boot, whatever create on one side doesn't work on the other side and reverse....

[QUOTE=absolutezero1287;6963793]This is sheer laziness.
... very interesting coment, you must be some PC guru :guitar: , well, let me ask you:
can you believe me I am with PC since early 80's but I can't type not looking my fingers! Because these 10K's hours I've spent with spaceball and mouse creating guizmos for YOU, but, also have to put a sticker "operating this device needs some common sense" and than the guy after "me" writes a user manual with some pictures, but he just forgets to put a paragraph...don't worry just call the number I will lead you thru in a minute. I have learned 5 languages from friends, I speak now 6, english is my latest and worst, forgive me for these typo's
...thanks for loking, you are my greatest help...pls you are more than welcome to stay here as much you like...

---

### Post by Hatfield604 on 2009-03-26
Not to get off topic, but yes, not all of us out here are as computer savy as the gurus.  

Yes, I know I can look through a search ... but if I'm new to this and am in the process of learning, how am I going to know *what* to look for in the first place if I don't know what I'm doing?

I stumbled into this thread looking for some simple directions to help set up a gateway box in a small family LAN (all of 2 of us), which by the time I'm finished will be 100% Ubuntu with no M$.  But don't worry Ab-zero, I won't bother you to ask.

---

### Post by attilab on 2009-03-26
I've got a lesson, administrators if any close buy, can close this thread, and the rest with all those useless questions

---

### Post by absolutezero1287 on 2009-03-26
All I'm saying is the OP is asking how to unpack an archive and read a PDF file. I have the solutions:

[PDF]("http://lmgtfy.com/?q=%22pdf%22+Ubuntu")

[Unpack an archive]("http://lmgtfy.com/?q=%22zip%22+Ubuntu")

---

### Post by mb_webguy on 2009-03-26
> **Hatfield604 said:**
> Yes, I know I can look through a search ... but if I'm new to this and am in the process of learning, how am I going to know *what* to look for in the first place if I don't know what I'm doing?

Hatfield604 has an excellent point here that should be repeated for those of us who might have forgotten:  you have to at least know the terminology in order to look up answers for yourself, and Linux has a slightly different than Windows.  Grub?  Gnome panel?  Shell prompt?  Repositories?  Launcher?  We can't expect new users to be able to look up things for themselves when they don't yet have the vocabulary to be able to do so.

---

### Post by absolutezero1287 on 2009-03-26
> **mb_webguy said:**
> Hatfield604 has an excellent point here that should be repeated for those of us who might have forgotten:  you have to at least know the terminology in order to look up answers for yourself, and Linux has a slightly different than Windows.  Grub?  Gnome panel?  Shell prompt?  Repositories?  Launcher?  We can't expect new users to be able to look up things for themselves when they don't yet have the vocabulary to be able to do so.

How are pdf and archive Linux terminology? All I'm saying is that the wiki and other resources where not put up for <beep> and giggles. They should be used.

---

### Post by attilab on 2009-03-27
hey guys, no fight
I was wrong, trying hard to make 4 steps at once.
I am just realising what the free means, its not a free beer or free ride.
here's the answer to my question that I asked my (our) old friend Billy G:
>>Hi Atila, 
I have not received any response from you on this issue. Generally, this is an indication that the problem may no longer exist. If this is not the case, please contact me at your earliest convenient time and I will be happy to help you resolve the issue.<<
This is a support for me, for my money what I've spent for MSW, MSO, AA and so on....
BTW
I just saved/or/print/or/made some pdf (with Acrobat) as a reminder if I stuck next time with something. logged over to ubuntu, pickup the file and can't open it with that pdf thingy, tested again, made a pdf save as, log over again arround a corner and can't open that file with Acrobat. Any idea? somebody sad pdf is pdf? next thing me to learn how to upload a file, and you can entertain with it, the linux pdf doesn't haqve extension in XP (just noticed), now going back to see the other side.
this is you call "the learning curve" ?

---

### Post by sanjeevpunj on 2009-03-27
Ubuntu, or any other open system are evolving platforms, unlike the static microsoft platforms.You cannot really expect a "step by step guide" that applies generally to all systems. You can visit specific forums for specific answers. Depending on your OS(Ubuntu or whichever other distro) you will find the exact required support (if available on the internet). Remember you are open to the world, and in all probability you will get an answer that suits you, but there are no guarantees (does Windows offer any gurantee anyway? I have lost at least 2 HDDs since Y2K, due to Windows Installations going awry). I dont want to keep buying HDDs.

Windows designers maybe graphically good, but their understanding of how a HDD functions is terrible. 

When I installed Ubuntu, it took me one simple reboot to get going with my system. With Windows, (I am sure you have experienced this) you might need to pass through at least 4-5 boot cycles before you are up and going.

So again, if you want specific answers, it is all out there in the forums, but if you are looking for a Manual for "MY OS CRASHED TODAY" well, it is upto you to think how to find one.

Welcome to the open skies. By the way it is nice and cloudy today!

---

### Post by absolutezero1287 on 2009-03-27
> **sanjeevpunj said:**
> Ubuntu, or any other open system are evolving platforms, unlike the static microsoft platforms.You cannot really expect a "step by step guide" that applies generally to all systems. You can visit specific forums for specific answers. Depending on your OS(Ubuntu or whichever other distro) you will find the exact required support (if available on the internet). Remember you are open to the world, and in all probability you will get an answer that suits you, but there are no guarantees (does Windows offer any gurantee anyway? I have lost at least 2 HDDs since Y2K, due to Windows Installations going awry). I dont want to keep buying HDDs.

Windows designers maybe graphically good, but their understanding of how a HDD functions is terrible. 

When I installed Ubuntu, it took me one simple reboot to get going with my system. With Windows, (I am sure you have experienced this) you might need to pass through at least 4-5 boot cycles before you are up and going.

So again, if you want specific answers, it is all out there in the forums, but if you are looking for a Manual for "MY OS CRASHED TODAY" well, it is upto you to think how to find one.

Welcome to the open skies. By the way it is nice and cloudy today!

Well said. Much better than my posts. In retrospect I probably sounded like a(n) RTFM troll.

---

### Post by attilab on 2009-03-27
thanks, well said, 
at my place we still have a long way to go, sunny outside, but frost on the roofs, my kids were bycicling 2 weeks ago in T-shirts but we can still expect a snowfall mid april.
If I would be employed at this moment probably would be more difficult to justify the idea moving out from XP comfort. Same thing, I was learning the platform during years, crashing it with purpose (scraping HDD's, swapping boards and so on) to learn the tricks, some cost $$ (to buy a comfort) but there is also a "free source" software as well, maybe a bit different meaning but works.
Anyway, get back to the topic, preparing the next questions. I am digging in to programs now, to find my comfort level I've got used to.
I am a CAD designer (not many CAD running on ubuntu), just a short list of my hobby is photography (didn't got to Canon RAW processing yet); and online photo albums (not sure to expect any post processor written for ubuntu); GPS geotagging - or - datalogging; archery (I am not expecting to find calculators here), saltwater reef aquarium (fully digitized, drivers probably completely unknown to community); not to go further to make this synchronized to my existing (kids and wife&#8217;s) lifestyle.
And I am still struggling with pdf, archives, googlesearch and a warm welcome to the "fresh air".
go now, need to make a progress today, see ya later.

---

### Post by nothingspecial on 2009-03-27
> **absolutezero1287 said:**
> Well said. Much better than my posts. In retrospect I probably sounded like a(n) RTFM troll.

Yep you did. This is the absolute beginners forum for Ubuntu, not Gentoo or Arch. Correct me if I`m wrong but I didn`t think rtfm was acceptable here. I come here to help people who haven`t a clue what they`re doing as I didn`t, and still don`t in many respects. I`m sure you were the same.

attilab, keep going mate, it`s only a learning curve. It was easier for me coz I never had windows in the first place (must try it one day).

I can`t imagine what your problem with pdfs are coz I just click them and they open.

What I`m trying to say (and I am not a gamer) is in my measly computer experience I have only ever found one thing that I have not been able to get to work with Ubuntu - a stupid digital photo keyring from a pound shop.

It`s like anything new, its a mystery at first but once you *get it*, it`s pretty easy. Keep going.

---

### Post by attilab on 2009-03-27
regards to pdf, just managed that, but this is a very _basic_ looking application, I need more advanced pdf editor:
I have installed the **PDFedit**, how to put it as a default to the "Open With", when I 2xMB1 (doubleclick) to open it right away? I managed to place it to the dropdown list.
-also, I want to create pdf from this page here, save as pdf, won't list me the shared DATA (it is the second Fat32 partition) because its not a folder, can put it only in to my Documents. 
- also, I want to move these files from Documents to that DATA, can't copy-paste
any workaround?
- how to: add this print/save pdf function to my MB3 (third mouse button) menu?
this just for excercise, looking for better editor
thanks

---

### Post by attilab on 2009-03-27
anybody?
just one sample pls,

---

### Post by attilab on 2009-03-27
> **absolutezero1287 said:**
> Well said. Much better than my posts. In retrospect I probably sounded like a(n) RTFM troll.

scusi for my question, but 
what that doesn mean "like a(n) RTFM troll" again
google doesn't translates,

---

### Post by pbpersson on 2009-03-27
> **attilab said:**
> scusi for my question, but 
what that doesn mean "like a(n) RTFM troll" again
google doesn't translates,

If you type RTFM into Google by itself, read that article, then type TROLL into Google by itself you will understand

A "RTFM troll" would therefore be a troll who goes around telling everyone to RTFM to cause trouble.

---

### Post by pbpersson on 2009-03-27
> **attilab said:**
> regards to pdf, just managed that, but this is a very _basic_ looking application, I need more advanced pdf editor:
I have installed the **PDFedit**, how to put it as a default to the "Open With", when I 2xMB1 (doubleclick) to open it right away? I managed to place it to the dropdown list.
-also, I want to create pdf from this page here, save as pdf, won't list me the shared DATA (it is the second Fat32 partition) because its not a folder, can put it only in to my Documents. 
- also, I want to move these files from Documents to that DATA, can't copy-paste
any workaround?
- how to: add this print/save pdf function to my MB3 (third mouse button) menu?
this just for excercise, looking for better editor
thanks

If you have twenty questions about twenty topics, you might want to create twenty new threads so you don't overwhelm people.  

Also, as the thread progresses it will be easier for people to keep track of what they are talking about in trying to help you.

For instance, it SOUNDS like one of your questions relates to having a FAT32 partition on your hard drive and wanting to mount that as a folder on your Ubuntu system.

However, with all the other questions you are asking it is difficult to know if that is really in there or if I just imagined it.

---

### Post by pbpersson on 2009-03-28
> **mb_webguy said:**
> Hatfield604 has an excellent point here that should be repeated for those of us who might have forgotten:  you have to at least know the terminology in order to look up answers for yourself, and Linux has a slightly different than Windows. 

Yes, I have fond memories of when I was first learning Linux on Mandrake.  It took me hours of research to discover that in order to scan documents I had to install something called KOOKA.  

I did not think that was intuitively obvious, any more than knowing in Windows I have to use something called NERO to burn CDs.  ;)

---

### Post by attilab on 2009-03-28
> **pbpersson said:**
> If you type RTFM into Google by itself...

RTFM=
nice, I have to write down this one
I had once a norvegian girlfriend and I've learned norvegian? so I am in the hunt again..

---

### Post by attilab on 2009-03-28
> **pbpersson said:**
> I did not think that was intuitively obvious, any more than knowing in Windows I have to use something called NERO to burn CDs.  ;)
here I could help you out with something more flixible like PowerISO or MagicISO or WinBin or CloneCD or AnyDVD and so on, depend what you want to do?

---

