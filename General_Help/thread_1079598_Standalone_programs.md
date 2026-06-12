---
title: "Standalone programs?"
date: 2009-02-24
forum: General Help
---

### Post by Charles Douglas Wehner on 2009-02-24
Currently I have downloaded Ubuntu 7.1 and am very carefully examining it. I am eager to explore Linux as an alternative to the horrendous Microsoft "offerings".

I have 46 years experience of computers. 

On my website, which is non-commercial (an "org"), I offer tested programming advice for the outer shell and inner core of floating point. 

[http://wehner.org/fpoint/index.htm](http://wehner.org/fpoint/index.htm) 

The outer shell is the link at the bottom.

So I am not a novice.

When I bought a laptop with Vista, I simply ran the installation wizard and loaded software for two new cameras. After that nothing worked.

I took it back to the shop. There was a mixture of bickering from the cheap staff and co-operation from the more sensible staff. They followed part of my advice, and tried to install "Service Pack 1". It took ten hours of one day, and six hours the next. Nothing had changed.

So the sales manager agreed to exchange it for a more expensive one, against a small increase in price, but with a price concession.

I took this laptop home, and installed a Lexmark printer. It connected itself for COM1, although neither the computer nor the printer had a COM1 facility. It was obviously a bug.

I resolved never to install anything with the "Installation Wizard" again. 

As I gained experience of the Vista bugs - a file-size of MINUS 1,285,230,262 bytes reported by Function 66, subfunction 2, the "pale screen of death", the freezing up under various conditions, and more and more, I decided that the core of the system is corrupt.

The idiot at the shop who had tried to install "Service Pack 1" had experienced a crash on each of both days. I think he demanded overtime pay whilst waiting for the pack to install - unaware that it was a crash. That was the first computer.

Service Pack 1 took four minutes to download. I put it on an SD card, and virus-checked it. Then I tried to install it. It should take two hours (not sixteen). It reported on the second (new) machine that it was already installed.

I examined the "Updates". Microsoft have "Updates to enable Updates". They do not work. It is only on a machine that already accepts "Updates" that an "Update to enable Updates" will work.

As I examined more and more of these "Updates" (NONE of which works), I found they are described as "standalone programs". They have made 49 "Updates" to date.

By now I have become reasonably clear in my mind that Microsoft has NO IDEA of what a "standalone program" is.

To work the system in machine code, you put "Thing" into AH and perhaps "Whatever" into AL, and perhaps do more before you call interrupt 33.

This is the point where it is no longer standalone.

My software had put Hex 4202 into AX and done the INT 33 call. My own research program malfunctioned, as did commercial software which at that time delivered the -1,285,230,262 byte report.

Although I have serious work to do, I am tempted to use DEBUG to search the "Updates" for INT 33. If I find so much as a single one, it is not standalone.

My Vista will not burn in a CD. It's the bug.

I downloaded a ROM-burning program, but am reluctant to use it.

Here is the reason:

LINUX is a public-domain system. There must be files out there which create ROM-burner drivers.

Is there a ROM-burning program that calls ITS OWN drivers? That is, a STANDALONE ROM-burner?

I do not believe that this buggy Vista is capable of using the ISO file to make an image disk. I would not trust a program that calls the INT 33 of Vista. From the feel of the bugs, it seems that help in creating an image disk must come from outside.

I know that free disks are available, but if I can create my own image disk I will not have to inconvenience anybody.

Charles Douglas Wehner

---

### Post by Slim Odds on 2009-02-24
> **Charles Douglas Wehner said:**
> Currently I have downloaded Ubuntu 7.1 and am very carefully examining it. I am eager to explore Linux as an alternative to the horrendous Microsoft "offerings".

Why 7.10?  It's old.... try 8.04 or 8.10

> LINUX is a public-domain system.Linux is **NOT** public-domain. It is GPL, which is copyrighted software that is freely available under **the GPL license**.

There's a big difference.

Why don't you try ImgBurn? [http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by Charles Douglas Wehner on 2009-02-25
Thank you, "Slim Odds", for that.

Yes - I was going from memory, but have the SD card with me today. It is Ubuntu 8.1 on the chip, not 7.1.

I have downloaded md5 as an image-burner. However, I do not know which programs are STANDALONE.

The choice of tools is not a fashion statement.

I have notched up many hours struggling with the Vista bugs:

[IMG]http://www.geocities.com/charleswehner/bugs/clock2.gif[/IMG]

For example, the Lexmark printer was wongly installed at COM1 for Windows applications. The "Installation Wizard" however, went into the DOS registry and seems wrongly to have installed it for LPT1.

However, although "LPT1" is a Microsoft word, EDIT did not understand it:

[IMG]http://www.geocities.com/charleswehner/bugs/lpt.gif[/IMG]

It actually "thought" that LPT1 is a file.

By the way, it would not let me save that image as "lpt1.gif" because it said "lpt1.gif" is reserved by Microsoft. I had to save it as "lpt.gif".

With Qbasic, however, it "thinks" LPT1 is a device fault:

[IMG]http://www.geocities.com/charleswehner/bugs/fault.gif[/IMG]

My own programs, and commercial ones I put in (without the "Wizard") worked most of the time. When my own program suddenly malfunctioned, I found out why:

[IMG]http://www.geocities.com/charleswehner/bugs/size.gif[/IMG]

This mad file-size made me go back to my source files. I discovered that it was when one puts the file-pointer to the end of the file, and gets the file size in DX:AX that the trouble arises. Everybody does that. There is no other way of accessing the file size. So it is a deeply-imbedded fault that makes STANDALONE programs essential if one is using Vista to escape from Vista.

It is high time that Microsoft sorted out the mess:

[IMG]http://www.geocities.com/charleswehner/bugs/clock.gif[/IMG]

Vista will not burn in a CD - or at least on the versions I had on two laptops (one of which I returned).

I take your point about ImgBurn. I am trying to find a STANDALONE image burner, and thank "Slim Odds" for pointing me to the site.

As regards "Public Domain", there is a fine distinction between Ubuntu and Linux. For example, developments of Linux have the intellectual property of the developers added - just as Netscape Navigator had the intellectual property of Netscape added to the original Mozilla.

However, I was not talking about copyright. In my haste I used the term "Public Domain" where I should have said "Open Architecture".

My point is that if the source files can be accessed, one can evaluate them visually instead of hacking. Where INT 33 is used, the program calls for help from Vista. Vista cannot be trusted to give any help to a program, so that program must stand alone.

A final point is that although I am very busy on a project, I am seriously thinking of coming over to Ubuntu. I have to discover such things as whether Linux also uses MOV AX #4202 and INT 33 for file size, and whether other functions are similar to the Microsoft ones.

If there are major incompatibilities, the switch to Ubuntu may be a rather tedious one.

Microsoft have perhaps got myself and other serious programmers locked into their "system".

In passing - do not mention Windows 7. Do not even whisper it. The children will start screaming and you will frighten the horses.

Charles Douglas Wehner

---

### Post by Slim Odds on 2009-02-25
> **Charles Douglas Wehner said:**
> Thank you, "Slim Odds", for that.

You're welcome... just trying to help.

> I take your point about ImgBurn. I am trying to find a STANDALONE image burner, and thank "Slim Odds" for pointing me to the site.
I'm not quite sure why you are so hung up on the term "STANDALONE".

Practically **nothing** that runs on a OS like Windows or linux is "STANDALONE". Ther all rely on many system services that the OS provides to do their job.

By design, modern OS's don't want every application to be going directly to the hardware. That would be total chaos. They provide an interface which is able to arbitrate requests for access to the hardware.

About the only place that you will find "STANDALONE" applications is on a dedicated piece of embedded hardware that is so specialized that is doesn't even have an OS (which is pretty rare these days).

---

### Post by Charles Douglas Wehner on 2009-02-26
First, a little more Vista comedy (picture below).

You never know what to expect. 

Unix had STDIN, STDOUT and STDERR as ever-open files. These were numbered by a "file handle". I think they are 0, 1 and 2. So instead of using DOS file-control blocks, one would point to the file name and path, and call for a "handle".

On a server, the ever-open files were glorious. Data arrived via STDIN to a COMMON GATEWAY. Your program would run its script, and the reply went out via STDOUT.

Unix became the standard operating system of servers. Even the all-lower-case style of Unix became a standard on the Web.

I wonder what the special feature of Linux is?

There was even an "X Window System" developed for Unix. When changing from Microsoft to another system, one has to consider all the advantages and disadvantages.

Returning to the subject, Microsoft copied the "file handle" idea in later versions of DOS, in order to be more Internet compatible. However they did not implement a common gateway.

On Microsoft systems, one has to run a server to get a common gateway. That way, one uses a browser and sends messages to [http://www.localhost](http://www.localhost) . WWW means the world. LOCALHOST negates that, and says "NOT".

So a localhost URL lands in one of your own directories, and you can develop CGI scripts as if they were far away on a distant server.

I wonder if Linux has a built-in STDIN, STDOUT and STDERR?

Anyway, Vista would not maximise the DOS windows. They were always the size of the ones I showed earlier.

I decided to try to run an old Xitami server, to get a common gateway. As usual with Vista, it hung up.

[IMG]http://www.geocities.com/charleswehner/bugs/xitami.gif[/IMG]

You can see on that image the point where Xitami stopped working. However - a MIRACLE! The window could now be maximised, even though useless because frozen up.

Later attempts at maximising the window also worked under certain restricted circumstances. It has been a PARTIAL REPAIR. It was not a repair tool, but an application program than partly mended it.

Further examples of the "Vista Experience" include the times when I tried to access one of my own directories. Back came a reply that this "resource" is currently not available - like when a web page request times out, and the webpage is currently not available.

Yet again, when I request the data on a file (as described previously for the MINUS 1,285,230,262 byte file), it announced that "You do not have permission to access this facility. Access DENIED".

I intend to check the size of MY files on MY computer without the permission of Bill Gates.

> I'm not quite sure why you are so hung up on the term "STANDALONE".

I am not hung up. I know exactly what "STANDALONE" means. I simply do not trust anything that a Microsoft operating system delivers. I have spelled out so much of the zany behaviour of Vista. This is due to deeply-embedded flaws.

I started to be professionally involved with computers in 1962. That gives me 46 years of experience - more than that of Bill Gates, and even of Steve Jobs and Stephen Wozniak (although the latter two have surely learnt far more than me).

> They provide an interface which is able to arbitrate requests for access to the hardware.

WRONG. Vista does not. It PRETENDS to provide an interface.

> By design, modern OS's don't want every application to be going directly to the hardware.

WHOOPS. You were talking about MODERN OSs. Ok. Vista is not modern. I agree.

> About the only place that you will find "STANDALONE" applications is on a dedicated piece of embedded hardware that is so specialized that is doesn't even have an OS (which is pretty rare these days).

Sorry. Not quite right here. Firstly, every pocket calculator is standalone HARDWARE. That meets your specification. Pocket calculators are not rare, though.

I am talking about standalone SOFTWARE.

If the Linux community have the original source files of a CD driver, for example, they can make a driver. So if one wants to write a program to run on a buggy computer, one adds the CD driver to that program. It is not a system call, but does the same as a system call.

For example to get a file size one might write:

MOV AX,#4202
CALL local_cd_driver

instead of 

MOV AX,#4202
INT #21

That makes it standalone.

From my descriptions of the various Vista bugs it should be clear that only a standalone program can be SURE to run correctly under Vista. All my CD burning programs fail because they use that dratted system.

I could describe more Vista freak behaviour, but have written enough to reveal the problem.

Maybe I will simply order the free CD.

I would like to contribute to Ubuntu in a small way. They are doing a great job.

Charles Douglas Wehner

---

### Post by Slim Odds on 2009-02-26
> **Charles Douglas Wehner said:**
> Returning to the subject, Microsoft copied the "file handle" idea in later versions of DOS, in order to be more Internet compatible.

Charles, you are one confused dude. They copied the "file handle idea" to be more "Unix like". It had nothing to do with the Internet.

> I started to be professionally involved with computers in 1962. That gives me 46 years of experience - more than that of Bill Gates, and even of Steve Jobs and Stephen Wozniak (although the latter two have surely learnt far more than me).So.... do you call memory "core"?

I hope you find what you're looking for.... over and out.....

---

### Post by davec64 on 2009-02-26
> **Charles Douglas Wehner said:**
> If the Linux community have the original source files of a CD driver, for example, they can make a driver. So if one wants to write a program to run on a buggy computer, one adds the CD driver to that program. It is not a system call, but does the same as a system call.

Just a point I picked up from your post (above), as Linux is GPL and you have access to the CD Driver's source code, the CD Driver will have been incorporated into the the Kernel. So you would make the call to the driver within the kernel and not take the CD Driver source and incorporate it into your own program. The point I'm trying to make is if you found a bug in the CD Driver source you would report the bug and possibly provide the corrected source as a fix which would then be incorporated in future releases. With this approach problems and bugs are identified for the benefit of everyone and solutions provided.

As linux takes the above approach I think it would be unlikely to find a truly standalone application you require.

I guess if I'm off mark with my above statements somebody will correct me! :)

Thanks for posting your Vista problems! It's made a very entertaining read! :)

---

### Post by moster on 2009-02-26
> **Charles Douglas Wehner said:**
> Currently I have downloaded Ubuntu 7.1 and am very carefully examining it. I am eager to explore Linux as an alternative to the horrendous Microsoft "offerings".

I have 46 years experience of computers. 

...

Oh, so many years with computers and just trying linux. I would love to hear your experience in Ubuntu. Just do not go away without say why. Wish luck :)

---

### Post by Charles Douglas Wehner on 2009-02-28
> Charles, you are one confused dude. They copied the "file handle idea" to be more "Unix like". It had nothing to do with the Internet.

There is absolutely no need to start a "flame war" with personal abuse.

The story of Windows goes back to the Apple Lisa and the Apple Mac. Both were resounding failures, so Steve Jobs and Stephen Wozniak sold shares to try to stay afloat. "Mr. Pepsico" bought those shares and sacked them both.

However, the "Mac" was ahead of its time. Publishers discovered the benefit of "drag-and-drop", particularly when using the Mac with Postscript to make a newspaper page. It was labour-saving. It speeded things up.

Starting with the Xerox GUI idea, Jobs and Wozniak had invented DESKTOP PUBLISHING.

This surge in Mac sales caused Microsoft to copy the GUI, and Windows arrived. Mr. Pepsico knew nothing of technology, and the lawyers ran rings around him. His unique selling feature was gone.

Meanwhile, academics were using Unix. The files on Unix were free of charge, because the academics were paid with public money.

The LYNX program was text only. Out of public money, it turned into MOSAIC. Out of public money it turned into the GODZILLA of MOSAIC (MOZILLA) - a monster. The US government refused to pay for any further development.

Academics then took the public-domain files, left academia, set up Netscape, and developed NETSCAPE NAVIGATOR.

Bill Gates wanted the browser market also. He was falling behind in his developments. There was only one thing to do - get the public domain Mozilla files, and extend them as Internet Explorer.

However, there was a snag. They all referred to file handles. The quickest thing to do was to add file handles to DOS, and then compile Mozilla to run under that DOS.

Now Bill Gates was ready to raise the price of DOS, and pretend he was "giving away" the browser. He was trying to monopolise the Internet.

> The point I'm trying to make is if you found a bug in the CD Driver source you would report the bug and possibly provide the corrected source as a fix which would then be incorporated in future releases.

I have NOT found any bugs in the Ubuntu code. I have found plenty of malfunctions in Vista. Of course, in the future, if I have time, I might try to sort out some development problems with Linux.

My problem is that the CD drivers of VISTA are faulty. A CD-image program may just be surface gloss on top of something that uses Interrupt 33 on VISTA. If so, it will have inherited the problems of VISTA.

If a CD-image program is provided, to burn in a CD on VISTA, it must have its own CD drivers (perhaps from the Linux library). It must not call VISTA. That is "STANDALONE".

Perhaps I will give up trying to burn in my own CD on a dud system, and simply order the free Ubuntu CD.

There does not seem to be anybody who knows which CD-image programs are standalone.

> Thanks for posting your Vista problems! It's made a very entertaining read!

Thank you too, for your comments. Yes, when things go terribly wrong à la Vista, it does seem comical. It is frustrating, too. I have a job of work to do, and bought the machine as a tool.

> Oh, so many years with computers and just trying linux.

Yes, for years I was using Digital Research CP/M 3, when the rest of the world was struggling with Microsoft products. It was TOTALLY stable and reliable. Then I used Windows 95 after it had become stable. I briefly tried XP, but it was buggy then. I reverted to Windows 95.

Now I have leapfrogged into the "Vista revolution", because I need modern equipment. Nothing works.

So now I am investigating Ubuntu. If I can get it up and running without too much delay, and I do not suffer such penalties as having unfamiliar system calls or non-standard "file handles", I will desert Vista.

HASTA LA VISTA, Vista.

Charles Douglas Wehner

---

### Post by Charles Douglas Wehner on 2009-02-28
A small point. I stated I had downloaded MD5 as an image-burner. This is wrong. It is an integrity test (checksum).

Charles Douglas Wehner

---

### Post by fifth on 2009-02-28
> **Charles Douglas Wehner said:**
> ...
erm, CD Wenher?
Busted?

---

### Post by Slim Odds on 2009-02-28
I wasn't try to start a "flame war" or "abuse" you personally.

You posts have been all over the map and difficult to follow at best.

Your time-line for DOS and Windows development is also completely wrong.

MS-DOS 2.11 had file handles in 1984. This is over 10 years before Microsoft released the first version of Internet Explorer and about 9 years before the first release of NCSA Mosaic (LYNX was initially release in 1992).

My point was the file handles and the Internet have nothing to do with each other.

Regarding your initial problem; are you sure that you don't have something else wrong with your machine?

I have no love for Vista, but I don't hear a huge outcry of people all over the place that cannot burn CD's in Vista.

As I mentioned before, the  reason people use an OS is to get support for things like hardware access, file system, etc. So there is very little incentive for anyone to write a CD burner that needs to directly talk to the hardware. Especially since there are way too many devices to support.

You might want to try to get your hands on an external burner (like USB) and try that. I have a Sony that I like a lot because I can plug it into a Window machine or a Linux machine and it works fine for both.

---

### Post by mc4man on 2009-02-28
It actually seems the 'cause' of this thread was/is the inability to burn a Ubuntu live cd on a vista machine. If that's the case then simply following the orig. suggestion of using ImgBurn would resolve that.(if ImgBurn fails then you have bad hardware and or poor media.

I have vista on a small laptop and while I've seen no issues using vista's built-in burning prog, why bother when a vastly superior tool is available.

If you do install ubuntu and need to do some cd/dvd burning, while there are some decent linux apps, again Imgburn works perfectly thru wine (to save yourself some *possible* aggravation set the I/O to ASPI-WNASPI32.DLL

---

