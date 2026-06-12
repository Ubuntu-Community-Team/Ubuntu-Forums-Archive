---
title: "HELP with dial up connection, please."
date: 2005-11-26
forum: Desktop Environments
---

### Post by L Campbell on 2005-11-26
I have loaded my Ubuntu 5.10 on my Win98 machine, on a 2nd hard drive.

My modem is an internal Smart Link, which works perfectly with both Windows and some other Linux systems but my Ubuntu cannot seem to find it.

Is there any way I can 'search' for the modem?

I can find my way around on Windows reasonably well but I am a total dunce on Linux, so I would appreciate it if you could make your suggestion as if I know nothing.   (which is close to the truth)       :-)

Thanks.

Lewis.

**********

---

### Post by towsonu2003 on 2005-11-26
linmodems.org -> read the page, download scanModem, read the readme (and maybe print it?) and follow instructions as carefully as possible after transferring the tool to ubuntu (bc you have to run the tool in ubuntu :) )...

---

### Post by L Campbell on 2005-11-27
WOW!!!

Thats a great resource.  Thanks.

Lewis.

********

---

### Post by eeried on 2005-11-27
Smartlink should work fine -- after installing all the necessary packages -- if you can read French I wrote an article on the subject -- [http://libre-fan.apinc.org/article38.html](http://libre-fan.apinc.org/article38.html)

---

### Post by L Campbell on 2005-11-27
Merci, Monsieur, mais je ne parle pas beaucoup de Francais.

I would love to read an English translation of it, though.

Kind regards.

Lewis.

**********

---

### Post by eeried on 2005-12-02
I'm sorry, L Campbell, I didn't see your message until now. Do you still need a translation? Please let me know.

Cheers,:cool:

---

### Post by L Campbell on 2005-12-03
[QUOTE=eeried]I'm sorry, L Campbell, I didn't see your message until now. Do you still need a translation? Please let me know.

Cheers,:cool:[/QUOTE]

WOW!!

YES, please.

I am still struggling here with both Ubuntu and Kubuntu 5.10 and, after about 6 weeks I am still not online.

In the meantime I have begun to pick up a little bit of the code, to enter in 'Terminal', so I AM making progress.   :-)

Kind regards.

---

### Post by eeried on 2005-12-04
Okay, L Campbell, I'll do the translation as soon as I'm through with another urgent article! -- I only need a few hours.

Let's hope this will solve your connection problem!

---

### Post by towsonu2003 on 2005-12-04
did you manage to run scanModem (./scanModem) ? If you are gettin stuck somewhere bf. actually running it, we may be able to help (after running it, the linmodems.org mailing list people are more like experts on this issue :) )?

PS. I notice I gave little or no instructions... So:

after downloading scanModem to your linux system (preferably to ~/Desktop, which is your desktop, for easy access), ```
gunzip scanModem.gz
chmod u+x scanModem
./scanModem

```
Scanmodem will scan modems and tell you how to configure them. You will need to read 'read1st.txt' and 'modemdata.txt' under (I think) the folder 'Modem'. If you cannot understand what these are saying, modemdata.txt should have some important instructions (at the top) on how to email linmodems.org people...

---

### Post by Gray. on 2005-12-04
This may sound silly but have you checked in System > Administration > Networking to see if it's activated/configured?

---

### Post by L Campbell on 2005-12-04
[QUOTE=towsonu2003]did you manage to run scanModem (./scanModem) ? If you are gettin stuck somewhere bf. actually running it, we may be able to help (after running it, the linmodems.org mailing list people are more like experts on this issue :) )?

PS. I notice I gave little or no instructions... So:

after downloading scanModem to your linux system (preferably to ~/Desktop, which is your desktop, for easy access), ```
gunzip scanModem.gz
chmod u+x scanModem
./scanModem

```
Scanmodem will scan modems and tell you how to configure them. You will need to read 'read1st.txt' and 'modemdata.txt' under (I think) the folder 'Modem'. If you cannot understand what these are saying, modemdata.txt should have some important instructions (at the top) on how to email linmodems.org people...[/QUOTE]


Hello and thanks again.

Yes, I did get ScanModem.gz and can see the files you refer to ( 'read1st.txt' and 'modemdata.txt') but I will need to read them several more times in order to get some more idea of what they mean.

Kind regards.

---

### Post by eeried on 2005-12-04
hello there,

I took a long time making my how-to easier to read on this forum only to realize I was deconnected from the forum, and lost all my work...


I'll post it again after a good night's sleep.
In the meantime, I found a very swift how-to. you v=can try it and see if it works. if it doesn't you'll have to unistall and do the smartlink installation the long way -- very boring, I know.
===========
[http://www.marzocca.net/linux/ubuntux31.html](http://www.marzocca.net/linux/ubuntux31.html)

The internal modem in Thinkpad X31 is an AC97 Modem type:
fabio@ubuntuPad:~ $ lspci | grep Modem
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
AC'97 Modem Controller (rev 03)

 
In order to get it working, you need to install the package l-modem-daemon which is in ubuntu multiverse.

sudo apt-get install sl-modem-daemon

 Once installed the package, your modem will be available on port /dev/ttySL0 ( or /dev/modem).


Now move to /etc/default and edit (with root privilegies) the file sl-modem-daemon. Browse to line SLMODEMD_COUNTRY= and type your country name (ITALY in my case...). Note: This last point is very important. I have been struggling for days before realizing that!

Now your modem is working. Just setup a dial script (with pppconfig or gkdial) and go online. 

============= 

PS: if you don't have a connection download the deb file from the Ubuntu package Web site and install with the command (as sudo) :
dpkg -i name_of_package.deb

I would think the package sl-modules would be required too. Let us know how it goes!

Good luck!

---

### Post by L Campbell on 2005-12-04
[QUOTE=eeried]hello there,

I took a long time making my how-to easier to read on this forum only to realize I was deconnected from the forum, and lost all my work...


I'll post it again after a good night's sleep.
In the meantime, I found a very swift how-to. you v=can try it and see if it works. if it doesn't you'll have to unistall and do the smartlink installation the long way -- very boring, I know.
===========
[http://www.marzocca.net/linux/ubuntux31.html](http://www.marzocca.net/linux/ubuntux31.html)

The internal modem in Thinkpad X31 is an AC97 Modem type:
fabio@ubuntuPad:~ $ lspci | grep Modem
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
AC'97 Modem Controller (rev 03)

 
In order to get it working, you need to install the package l-modem-daemon which is in ubuntu multiverse.

sudo apt-get install sl-modem-daemon

 Once installed the package, your modem will be available on port /dev/ttySL0 ( or /dev/modem).


Now move to /etc/default and edit (with root privilegies) the file sl-modem-daemon. Browse to line SLMODEMD_COUNTRY= and type your country name (ITALY in my case...). Note: This last point is very important. I have been struggling for days before realizing that!

Now your modem is working. Just setup a dial script (with pppconfig or gkdial) and go online. 

============= 

PS: if you don't have a connection download the deb file from the Ubuntu package Web site and install with the command (as sudo) :
dpkg -i name_of_package.deb

I would think the package sl-modules would be required too. Let us know how it goes!

Good luck![/QUOTE]


Yikes!!   :-)

This will be a challenge for me and I'm excited.  It'll be a couple of days before I can try it, because of work but I'm looking forward to it.

Many thanks for all your efforts.

---

### Post by eeried on 2005-12-05
Good thing you're too busy to try this how-to  L Campbell.

This delay gives time to refurbish my longer how-to.

But don't forget -- the most important thing is to make sure what type your modem is.  I wonder how this guy on marzocca.net guessed his modem was a smartlink type: [http://www.marzocca.net/linux/ubuntux31.html](http://www.marzocca.net/linux/ubuntux31.html)

Perhaps Breezy works miracles -- I 'll try and find out. :cool:

BTW It may not be necessary to quote a whole message, it may be inconvenient for people who read  the thread.

---

### Post by L Campbell on 2005-12-05
>>>
But don't forget -- the most important thing is to make sure what type your modem is. I wonder how this guy on marzocca.net guessed his modem was a smartlink type: [http://www.marzocca.net/linux/ubuntux31.html](http://www.marzocca.net/linux/ubuntux31.html)
<<<

Good morning.  (Its morning in Texas)    :-)

My modem is an internal SmartLink with an SL 1900 chipset.

When I first became interested in Linux, about a year ago, it appeared to me that the 'modem issue' was Linux's 'dirty little secret'.

I tried several versions of Linux (mainly LIVE CD's) but, after trying about 9 modems, still had not got online.

By chance one day, I bought a SmartLink modem from E-bay for 1 (yup, thats ONE) dollar and rode my bicycle into the next town to pick it up, so I didn't even pay a shipping charge.   :-)

This modem has consistantly connected at a higher baud rate than other modems that I have used in the past and works with both Win and Linux.  Using Mepis (KDE KPPP) and this modem was the first time I was able to get online with Linux.

I assumed that all my troubles were over but, since Oct., I have been trying with Ubuntu and Kubuntu but have yet to get online.   :-(

However, I feel that I am having a GREAT learning experience and realize that I WILL get online eventually and when I do I will be able to enjoy the 'Linux experience' much more than if I had got on at my first try.

Kind regards.

---

### Post by eeried on 2005-12-05
> it appeared to me that the 'modem issue' was Linux's 'dirty little secret'.

Well not exactly -- it's rather that winmodem manufacturers don't giive a dman for Linux and aren"t always keen on providing drivers.

Connexant for instance wants you to pay for its linux and you must buy a new driver one each time your Linux kernel version changes. oitherwise you'll have to makedo with their free version of the driver that gives you a very slow connection

So you're lucky to have a true Smartlink modem and I'm pretty confident it will work.

On the Smartlink website you can even download a driver for Linux but I guess you'll have to compile the sources and install them, which is sometimes very easy though.

As I said i'm getting this how-to ready and updated for Breezy so you can test it and I can correct it...

Best wishes,

---

### Post by eeried on 2005-12-09
Hello again,
 Sorry for responding so late -- I have been busy writing a couple of articles on my Web site about a French bill of law which is similar to DMCA, and even worse! There'll be no debate and the vote is to take place on 22 december  night -- this bill poses a serious threat to free software in particular.

And then I copied and pasted  this long message only to find the forum was down!  

 Now onto Smartlink:
Perhaps you can try this way: theSmartlink How-to on the Ubuntu Wiki:

[URL="https://wiki.ubuntu.com/BinaryDriverHowto/SmartLinkModem?highlight=%28modem%29"[/URL]

This is what I put together (no warrantee!), with the addition of the Ubuntu Wiki page

- A winmodem isn't a piece of hardware but software. As it is less expensive than hardware, computers are often shipped with a cheap internal modem. Of course those cheap modem work very well with M$Windows. Some of them work with Linux but none of them work with FreeDSD for instance.
Some external modem aren't true modem either, so beware.

It's often a better choice to run and buy yourself a real external modem than waste a lot of good time trying to install dirvers for a winmodem. BTW, a winmodem when used with Linux becomes a Linmodem.

===============
First you need to know which kind of modem you have.  if you're sure what your modem skip this part. To do this you need a connection to the internet, and copy the files to your Linux box. you have to download a programme called 'ScanModem'. That progamme is available inside a compressed filed called 'scanModem.gz' which contains a few useful text files.

Here's the direct link: scanModem.gz: [http://frankandjacq.com/ubuntuguide/scanModem.gz](http://frankandjacq.com/ubuntuguide/scanModem.gz)

In the rest of this article, the bash sign (#) preceding a command means you must type sudo before typing your command. Of course the # sign mustn't be typed.

On the contrary, the $ sign means you can type a command without being root (or sudo in Ubuntu)

- Uncompress the file which can remain in your /home directory. 
$ gunzip Modem.gz

- This has created a dir called Modem in your /home dir and you can move there: $ cd ./Modem

-* Execute scanModem by typing: 
# scanModem

A few basic information is displayed on the terminal but you'd well-advised to have a closer look at what the file 'ModemData.txt' says about your modem.

- To display the content of this file, type 
# cat ModemData.txt

If you find the word  «Smartlink» associated to words like 'drivers' ou 'codec' ou 'subsystem', go on reading. if you're uncertain, post the content to the Ubuntu forum and someone will be able to tell you what type of modem you have. 

============
Follow the Ubuntu Wiki for installing all the necessary packages and sources
 (download them from the Ubuntu package site) and  follow the instructions to try and make your modem dial up.

Note: In my experience in Hoary it was possible to download, and install with the dpkg -i command 
sl-modem_modules*.deb
sl-modem-daemon*.deb

Make sure you get the files with the right kernel version number (Breezy is 2.6.12) and mind you choose the appropriate  processor reference.

Here's the terminal ouput at the end of the sl-modem-daemon* installation:

Setting up sl-modem-daemon...
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0

The 'slamr' module must have replaced the'snd-intel8x0m' one – the final 'm' is important). Check it's there with the command: # lsmod
if it isn't there I think it exist in the ubuntu repository

In the Wiki they say you need to compile some source, and maybe this specific to Breey. they also install fakeroot but I don't if it's necessary.

=======
**Setting up the dial-up connection**:

Now I would begin by setting the dial-up connection with the command pppconfig – the program is very easy to understand since every step is explained. Choose dynamic DNS unless you're certain your ISP uses static ones (you need to enter the numbers).

To connect you simply type pon in the terminal and poff to disconnect. It's fun.
If you've find out how to put yourself in the ppp group in pppconfig, you can type pon and poff as user, otherwise you have to type the command as sudo.

Then download the package called:
-* 'gnome-ppp'. This is a very convenient applet to 'activate' a connection – and easy to set up (if you like pon & poff don't bother with gnome-ppp)
# dpkg -i gnome-ppp_0.3.21-1_i386.deb 
The latest version number on 12/05/2005) 
  
Set up Gnome-ppp (phone number etc) – once installed it's in the Applications menu > Internet. Check if the modem is detected in Gnome-ppp (explore the few tabs).Or type or select the right modem (= the symlink created as seen above).

Now try to connect using the command-line app called wvdial which enables you to check what goes on and what's not working as it spurts out messages on the terminal.

 # wvdial

you might get something like that:

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

Whether the connection works or not (here it doesn't) type:
# wvdialconf /etc/wvdial.conf

The command creates a config file: if the connection works the config will be saved. If it doesn't at least you'll have a config file to edit to make the connection work!

As the connection doesn't work in this instance, you can edit the config file with the text editor gedit:
# gedit /etc/wvdial.conf

Fill in the config file with what's missing there, and delete the semi-colons (;) before Phone and the < and > in the original file:.

You should now be able to connect to the internet. Type the command : # wvdial And be patient it sometimes takes a while to connect.

If you can see two IP addresses like 111.222.33.444, on the terminal, you've won the day! even if the modem doesn't make a sound. If the connection fails you'll get a number of error messages like: No Dial tone, No Answer, Unknown response, etc.

In case of failure, add  the following lines to /etc/wvdial.conf: Carrier Check = no or if there's the line Carrier Check = yes, add a ; at the beginning of the line to comment it or replace 'yes' par 'no'.

To disconnect press Ctrl+C – and check your phone line to make sure it is now free.

From now on you can use Gnome-ppp. In my experience it takes a few seconds before the modem is actually disconnected.

If sl-modem still doesn't work maybe the modem isn't rightly identified – some modems may require smartlink drivers but smartlink may have madee it impossible for modem not produced by Smartlink itself to use the smartlink drivers.. But in your case there's no doubt it's Smartliink.

- Read the page on wvdial on the Linmodem.technion.ac.il: [http://linmodems.technion.ac.il/wvdial.html](http://linmodems.technion.ac.il/wvdial.html).

- you can still edit /etc/wvdial.conf, par exemple:

- Check carrier = no 

- Stupid Mode = no

- Jacques Goldberg provides many other tips on Linmodem.org: "Linmodem Post Install Problems: A compilation of problems and solutions".
=====
- You can try the following sources – have to be compiled.
slmodem*.tar.gz
But before installing them you'll have to uninstall the sl-modem packages you first installed...  The TAR.GZ file contains all the instructions for installation.

- Download, untar, and compile the the following source file (very easy): slmodemd*-pre1-alsa.tar.gz and copy the file slmodemd to /usr/bin/  and follow the instructions byMarv Stodolsky in slmodemd.txt wich is included in the .tar.gz file). 

- To untar a .tgz ou tar.gz file: tar xzvf name_of_the_file.tar.gz (or .tgz)
=====
If nothing works you can post the ouput of the following commands: 

# tail -f /var/log/messages

- Then launch another terminal or open a new tab and type: # wvdial

- Look at the ouput in the first terminal or on the first tab and post it on the forum.

=======
 Goo luck and let us know how it goes!

---

### Post by L Campbell on 2005-12-09
THANK YOU, THANK YOU, THANK YOU.

This looks SUPER.

I'm going to get suitably rested, appropriately caffeinated and tackle it.

My prediction is that I'll be online this weekend.   :-)

BTW, I _really_ had to chuckle when I read this:-

>>>>>
n the rest of this article, the bash sign (#) preceding a command means you must type sudo before typing your command. Of course the # sign mustn't be typed.
<<<<

Guess what I have been doing wrong?    :-)

Kind regards.

---

### Post by GeneralZod on 2005-12-09
[QUOTE=L Campbell]
My prediction is that I'll be online this weekend.   :-)
[/QUOTE]

Just wanted to chime in and say how much I admire your patience throughout your ... (ahem) ...  ordeal (and that of those who have helped you by putting together guides, etc).  Many people would have tried for 2 hours and then posted an "UBUNUT SUX" post in Community Chat! ;)

Anyway, best of luck with things and I hope to see you posting from within Ubuntu at the weekend :)

---

### Post by L Campbell on 2005-12-09
[QUOTE=GeneralZod]Just wanted to chime in and say how much I admire your patience throughout your ... (ahem) ...  ordeal (and that of those who have helped you by putting together guides, etc).  Many people would have tried for 2 hours and then posted an "UBUNUT SUX" post in Community Chat! ;)

Anyway, best of luck with things and I hope to see you posting from within Ubuntu at the weekend :)[/QUOTE]


Thanks for the encouragement.

Its the British Bulldog in me.    :-)

---

### Post by L Campbell on 2005-12-11
[QUOTE=eeried] SNIP
 
===============

Here's the direct link: scanModem.gz: [http://frankandjacq.com/ubuntuguide/scanModem.gz](http://frankandjacq.com/ubuntuguide/scanModem.gz)

In the rest of this article, the bash sign (#) preceding a command means you must type sudo before typing your command. Of course the # sign mustn't be typed.

On the contrary, the $ sign means you can type a command without being root (or sudo in Ubuntu)

- Uncompress the file which can remain in your /home directory. 
$ gunzip Modem.gz

- This has created a dir called Modem in your /home dir and you can move there: $ cd ./Modem
----------------------
----------------------

Well, I got all ready to go to day but didn't get too far.

I downloaded a fresh copy of ' scanModem.gz ', using my Win computer, moved the file to a floppy, booted up Ubuntu and copied the file from the floppy to my Home folder.

The instructions for unzipping the file worked perfectly, so I then tried:-
......................
- This has created a dir called Modem in your /home dir and you can move there: $ cd ./Modem
......................

Although I tried a couple of times, I was not successful.

I copied the text from ' Terminal ', documenting what I had done and hoped to be able to post it here but I was unable to copy the information to my floppy.

Anyway, I have started.

The day was not a total loss, as I had a nice, 30 mile, bike ride in mid-twenties temperatures, managing to avoid most of the ice on the road and did not fall.       :-)

Kind regards.

---

### Post by eeried on 2005-12-12
I must apologize for all the typing mistakes in my messages which make my attempt at a how-to rather ridiculous, and unreadable. Today I'm enjoying a DSL connection and can take my time -- though this forum tends to disconnect you if you linger too long when writing a message.

L Campbell: You didn't manage to cd to ./Modem
- Make sure the directory exists (you know Modem and modem are two different files or dir in Linux)
- Make sure the dir doesn't belong to root: if it belongs to root, and has very restricted permissions -- this happens when you copy files to a floppy, etc. -- you'll see an icon: either a lock or a red icon. You'll have to type your command as sudo: sudo cp ./Modem

==========

Then download and install all the files as described in the Ubuntu Wiki: Here's the link again:
[https://wiki.ubuntu.com/BinaryDriverHowto/SmartLinkModem?highlight=%28smartlink%29]("https://wiki.ubuntu.com/BinaryDriverHowto/SmartLinkModem?highlight=%28smartlink%29")

The sl-modem* packages, in particular are available for Breezy on the Ubuntu package Website: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sl-modem&searchon=names&subword=1&version=breezy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sl-modem&searchon=names&subword=1&version=breezy&release=all")

Package sl-modem-daemon

    * breezy (misc): SmartLink software modem daemon [multiverse]
      2.9.10+2.9.9d-6ubuntu1: i386

Package sl-modem-source

    * breezy (misc): SmartLink software modem driver - module building source [multiverse]
      2.9.10+2.9.9d-6ubuntu1: i386
=============

I wrote a complete how-to for Hoary, and a few things seem to be different for breezy. However, the part dealing with wvdial and setting up the connection, checking it, editing it, should be all right.

==========
Finally, if things don't work,  you can always buy yourself a real external modem -- not a USB one, a plain one with an old-fashioned plug. Note not all external modems are genuine hardware, some are just external winmodems :rolleyes: -- so beware! (for instance, external Olitec modems are fine, but some US robotics aren't, apparently!).

 As you spent a dollar for your smartlink, you might sell it again for the same price  and buy yourself a dear old modem for a couple of bucks (well, a little more, I'd expect).  ;) An external modem is considered better quality too.
If you do that,  better remove your smarlink card -- the two modems may disagree, someone told me -- and adapt your M$windows connection to this new modem, if you still use Windows -- BTW , surfing on M$Windows is a hazard: M$ spies on you as sso as you're connected to the internet.
==============
Good luck,

---

### Post by L Campbell on 2005-12-16
In my continuing quest to get online, I received some feedback from linmodems.org and subsequently downloaded an ' slmodemd ' file, which I moved to the 'Modem' folder in my Home directory.

I opened the ReadMe file and tried to do this:-

******************
Installation
============

1. Unpack tar.gz package file:

	$ gzip -dc slmodem-2.9.X.tar.gz | tar xf -

***********************

lcampbell@ubuntulewis:~$ gzip -dc slmodem-2.9.X.tar.gz | tar xf-
gzip: slmodem-2.9.X.tar.gz: No such file or directory
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
lcampbell@ubuntulewis:~$ 


Unfortunately it didn't work and I wonder if you might have a suggestion here?

Kind regards.

---

### Post by GeneralZod on 2005-12-16
[QUOTE=L Campbell]In my continuing quest to get online, I received some feedback from linmodems.org and subsequently downloaded an ' slmodemd ' file, which I moved to the 'Modem' folder in my Home directory.
[/QUOTE]

Open a terminal, and navigate to the directory containing the downloaded file; if what you have said in your post is accurate (right down to the capitalisation of the letter "M"!), you can do this via

```

cd ~/Modem

```

Then do

```

tar -xzf <filename>

```

where <filename> should be replaced with the full name of the file you downloaded; hopefully, just pressing "tab" a couple of times after you enter

```

tar -xzf slm

```

will auto-fill it in for you.  Then try and follow the instructions in the README following the "Unpack tar.gz package file" part, and let us know how you get on :)

---

### Post by L Campbell on 2005-12-16
[QUOTE=GeneralZod]Open a terminal, and navigate to the directory containing the downloaded file; if what you have said in your post is accurate (right down to the capitalisation of the letter "M"!), you can do this via

```

cd ~/Modem

```

Then do

```

tar -xzf <filename>

```

where <filename> should be replaced with the full name of the file you downloaded; hopefully, just pressing "tab" a couple of times after you enter
[/QUOTE]

***********

I don't think I made much progress.    :-(

Your instruction seemed to work well, so I tried again to to follow these instruction from the 'Read me':-

......................
Note: Most Linux Distributions have 'ready to use' kernel source package -
      be sure that this is installed.


Installation
============

1. Unpack tar.gz package file:

	$ gzip -dc slmodem-2.9.X.tar.gz | tar xf -

2. 'cd' to package directory:

	$ cd slmodem-2.9.X

3. Review and edit 'Makefile' (if need):

   In many cases you will need to correct path to your local kernel
   source tree:

        KERNEL_DIR=/path/to/linux


Here is my action:-

lcampbell@ubuntulewis:~$ cd ~/Modem
lcampbell@ubuntulewis:~/Modem$ tar -xzf SLMODEMD.gcc4.tar.gz
lcampbell@ubuntulewis:~/Modem$ cd --/
bash: cd: --: invalid option
cd: usage: cd [-L|-P] [dir]
lcampbell@ubuntulewis:~/Modem$ cd --
lcampbell@ubuntulewis:~$ gzip -dc slmodem-2.9.X.tar.gz | tar xf -
gzip: slmodem-2.9.X.tar.gz: No such file or directory
lcampbell@ubuntulewis:~$ sudo mount /media/floppy
Password:
lcampbell@ubuntulewis:~$

******

Kind regards.

Lewis.

---

### Post by GeneralZod on 2005-12-16
There should be a new directory included within the Modem directory; go back there and then go into that directory.  This will bring us up to step 3 of the instructions you were provided with.
Try

```

./configure

```

and 

```

make

```

and let us know which errors (if any) you receive, along with the output of 

```

ls -l

```

---

### Post by L Campbell on 2005-12-16
>>>>>
There should be a new directory included within the Modem directory; (looks like a file 'folder' ?) (that would be SLMONDEMD.gcc4) go back there and then go into that directory.  This will bring us up to step 3 of the instruction you were provided with.

Step 3 of instructions:-
Then try and follow the instructions in the README following the &#8220;Unpack tar.gz package file&#8221; part 
<<<<<

OK, I think this is what you are asking me to do.  I tried some of them but didn't seem to get anywhere.

The only real result I got was from your command, Code:   ls -l

Obviously I'm doing something wrong but I'm not sure what.   :-(

Installation
============

1. Unpack tar.gz package file:

	$ gzip -dc slmodem-2.9.X.tar.gz | tar xf -

2. 'cd' to package directory:

	$ cd slmodem-2.9.X

3. Review and edit 'Makefile' (if need):

   In many cases you will need to correct path to your local kernel
   source tree:

        KERNEL_DIR=/path/to/linux

   Default KERNEL_DIR is '/lib/modules/<kerne-version>/build'. Many Linux
   Distributions use directory '/usr/src/linux-<version>' also.

   Note: If you are using Linux kernel 2.4, only header files should be
         available for build in $(KERNEL_DIR)/include

   Another way to pass right value KERNEL_DIR is to use command line
   parameter while running 'make':

        $ make KERNEL_DIR=/path/to/linux ...

4. Run 'make' command to compile package:

	$ make

5. Install. As 'root' user run:
***************************************


Results of $ ls -l

lcampbell@ubuntulewis:~$ cd slmodem-2.9.X
bash: cd: slmodem-2.9.X: No such file or directory
lcampbell@ubuntulewis:~$ KERNEL_DIR=/path/to/linux
lcampbell@ubuntulewis:~$ gzip -dc slmodem-2.9.X.tar.gz | tar xf -
gzip: slmodem-2.9.X.tar.gz: No such file or directory
lcampbell@ubuntulewis:~$ cd slmodem-2.9.X
bash: cd: slmodem-2.9.X: No such file or directory
lcampbell@ubuntulewis:~$ ./configure
bash: ./configure: No such file or directory
lcampbell@ubuntulewis:~$ make
bash: make: command not found
lcampbell@ubuntulewis:~$ 1s -1
bash: 1s: command not found
lcampbell@ubuntulewis:~$ ls -l
total 500
-rw-r--r--  1 lcampbell lcampbell   8704 2005-11-29 06:45 10 lines.doc
-rw-r--r--  1 lcampbell lcampbell   8164 2005-11-30 06:23 10 lines.odt
-rw-r--r--  1 lcampbell lcampbell   7757 2005-12-01 09:09 12-01-05 2nd code.odt
-rw-r--r--  1 lcampbell lcampbell   6729 2005-12-01 11:37 12-01-05 3rd code.odt
-rw-r--r--  1 lcampbell lcampbell   7375 2005-12-01 11:40 12-01-05 4th code.odt
-rw-r--r--  1 lcampbell lcampbell   8023 2005-12-01 14:00 12-01-05 5th code.odt
-rw-r--r--  1 lcampbell lcampbell   7299 2005-12-01 08:44 12-01-05 code.odt
-rw-r--r--  1 lcampbell lcampbell   9699 2005-12-13 08:49 1 Terminal 12-13-05.odt
-rw-r--r--  1 lcampbell lcampbell   7028 2005-12-11 13:37 Code from 12-11-05.odt-rw-r--r--  1 lcampbell lcampbell  15537 2005-12-01 20:28 Code info 12-01-05.odtdrwxr-xr-x  2 lcampbell lcampbell   4096 2005-12-15 06:22 Desktop
-rwxr-xr-x  1 lcampbell lcampbell   9118 2005-12-13 20:02 forumo.odt
-rwxr-xr-x  1 lcampbell lcampbell    766 2005-12-13 19:58 forumt.odt
-rw-r--r--  1 lcampbell lcampbell  23827 2005-12-15 19:57 FWD 'bent.odt
-rw-r--r--  1 lcampbell lcampbell   7784 2005-11-28 14:53 lew.odt
drwxr-xr-x  3 lcampbell lcampbell   4096 2005-12-16 11:12 Modem
-rw-r--r--  1 lcampbell lcampbell   9249 2005-12-15 06:33 MyCodes.odt
-rw-r--r--  1 lcampbell lcampbell   1095 2005-11-30 12:12 new file 11-30-05
-rw-r--r--  1 lcampbell lcampbell   6822 2005-12-15 15:48 post.odt
-rw-r--r--  1 lcampbell lcampbell  19456 2005-12-14 06:18 print me.doc
-rw-r--r--  1 lcampbell lcampbell  15180 2005-12-14 06:18 print me.odt
-rw-r--r--  1 lcampbell lcampbell   7910 2005-12-03 05:23 Problem with Nautilus.odt
-rwxr-xr-x  1 lcampbell lcampbell 212760 2005-12-11 18:38 scanModem
-rw-r--r--  1 lcampbell lcampbell   9845 2005-12-16 11:32 Snip.odt
-rw-r--r--  1 lcampbell lcampbell   7403 2005-12-16 11:28 snipp.odt
-rw-r--r--  1 lcampbell lcampbell   9612 2005-12-03 05:38 Successfuly seach and file transfer.odt
-rw-r--r--  1 lcampbell lcampbell   8463 2005-12-16 08:16 tar.odt
-rw-r--r--  1 lcampbell lcampbell  16870 2005-12-13 11:54 terminus.odt
drwxr-xr-x  2 lcampbell lcampbell   4096 2005-12-14 05:08 Tips for Newbie
lcampbell@ubuntulewis:~$

Kind regards.

---

### Post by GeneralZod on 2005-12-16
Looks like you were still in your home directory when you did the "ls -l" :) You need to be in the new sub-directory of ~/Modem, I guess from what you said that this is SLMONDEMD.gcc4 (make sure this is 100% correct - "MONDEM" sounds a bit odd, to me!), so do

```

cd ~/Modem/SLMONDEMD.gcc4

```

Then try ./configure and make and post the output of "ls -l".  Ignore steps 1 & 2 of the README file for the time being; the stuff I've written above is intended to replace them, as  it looks like the README is out of date :)

---

### Post by L Campbell on 2005-12-16
[QUOTE=GeneralZod]Looks like you were still in your home directory when you did the "ls -l" :) You need to be in the new sub-directory of ~/Modem, I guess from what you said that this is SLMONDEMD.gcc4 (make sure this is 100% correct - "MONDEM" sounds a bit odd, to me!), so do

```

cd ~/Modem/SLMONDEMD.gcc4

```

Then try ./configure and make and post the output of "ls -l".  Ignore steps 1 & 2 of the README file for the time being; the stuff I've written above is intended to replace them, as  it looks like the README is out of date :)[/QUOTE]

The strange looking file name is definitely the way it is shown in the folder.

Unfortunately, I didn't get very far and I do appreciate your continued patience. 

lcampbell@ubuntulewis:~$ cd ~/Modem/SLMODEMD.gcc4
[email]lcampbell@ubuntulewis:~/Modem/SLMODEMD.gcc[/email]4$ ./configure
bash: ./configure: No such file or directory
[email]lcampbell@ubuntulewis:~/Modem/SLMODEMD.gcc[/email]4$

Kind regards.

---

### Post by GeneralZod on 2005-12-16
Cool; you're in the right directory.  The output of 

```

ls

```

should be helpful.

---

### Post by L Campbell on 2005-12-16
[QUOTE=GeneralZod]Cool; you're in the right directory.  The output of 

```

ls

```

should be helpful.[/QUOTE]
>>>>>>>>>>>>>>>>>>>>                
                                                    
You're correct, its MODEMD not MONDEMD, sorry about that.
<>>>>>>>>>>>>>>>>>>>

I had a little success this time.

lcampbell@ubuntulewis:~$ cd ~/Modem/SLMODEMD.gcc4
[email]lcampbell@ubuntulewis:~/Modem/SLMODEMD.gcc[/email]4$ ls
1st_Read.txt  CountryList.txt  scripts           slmodem.txt
Changes       Files.txt        Slmodem-ALSA.txt  Testing.txt
COPYING       README           slmodemd          wvdial.conf


[email]lcampbell@ubuntulewis:~/Modem/SLMODEMD.gcc[/email]4$ ls -1
1st_Read.txt
Changes
COPYING
CountryList.txt
Files.txt
README
scripts
Slmodem-ALSA.txt
slmodemd
slmodem.txt
Testing.txt
wvdial.conf
[email]lcampbell@ubuntulewis:~/Modem/SLMODEMD.gcc[/email]4$ cd --
lcampbell@ubuntulewis:~$ sudo mount /media/floppy
Password:
lcampbell@u buntulewis:~$

Kind regards.

---

### Post by GeneralZod on 2005-12-17
Can you send me the URL you downloaded this slmodem thing from? I'd like to take a look for myself.  Thanks! :)

---

### Post by L Campbell on 2005-12-17
[QUOTE=GeneralZod]Can you send me the URL you downloaded this slmodem thing from? I'd like to take a look for myself.  Thanks! :)[/QUOTE]

I have included 2 messages that I received from the gentlemen at linmodems.org
The first one contains the link to linmodems.technion, where the SLMODEMD came from and it explains their reasoning for suggesting it.
In the second message their is an explanation about a second file, which they sent me a few hours ago and which is still on my Win desktop.

Thanks again.
 ____________________________________________
Yes, as you an see in this quote from the ModemData.txt below:
BEGIN QUOTE
   A series maintaining a much broader license for other
  chipset support, can be downloaded from

  [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

   Though not always needed, download the files:
     
slmodem-CurrentVersion.tar.gz - provides the most general code package.
     
slmodemd-CurrentVersion.tar.gz - provides a compiled slmodemd
     
ungrab-winmodem.tar.gz  -  may be needed for usage with slamr.
  
Details on their usage are in Slmodem.txt,
  Slmodem-ALSA.txt and
  [http://linmodems.technion.ac.il/slmodem-serial.html](http://linmodems.technion.ac.il/slmodem-serial.html)
END QUOTE

And minimal headache is with using the slmodemd precompiled driver 
rather than having to compile the slmodem (no trailing d) file.
Usage details are in the file to be downloaded.

Jacques
****************************************************

Lewis

> Class 0703: 163c:3052   Modem: Smart Link Ltd.
> SmartLink SmartPCI562
on
>  ./scanModem test 163c:3052 163c:3052 debian
> 2.6.12-9-386  3.4.5  i686
>
shows a well supported SmartLink modem.  Install the two Ubuntu
packages sl-modem-daemon and sl-modem-source.  You may have to get
them through the online repository [http://packages.ubuntu.com/](http://packages.ubuntu.com/) if not
on your install CD.  Move into the Linux folder they have been copied
into and Install with:
# sudo dpkg -i *.deb
Main components are start up scripts,  /usr/sbin/slmodemd and a
/usr/src/modules/slmodem-SomeVersion for compiling a slamr.ko driver.

To setup for the compiling,
OPPs, never mind the compiling. Breezy LACKS the gcc-3.4 compiler you
need and its dependent package.  A BUG which I've reported, but fixed
on my System.  This evening I'll compile the slamr.ko driver for
you/everyone
____________________________________________
( the file he sent is:-   slmodem_2.6.12_9_386.tar.gz  )
___________ ___________________________________

Meanwhile read the Slmodem.txt  to better understand the modem usage.

MarvS
scanModem maintainer

---

### Post by eeried on 2005-12-18
They're great at Linmodem, aren't they?

L Campbell, could you give us a link to the tarball they've sent you?

Cheers,

---

### Post by L Campbell on 2005-12-18
[QUOTE=eeried]They're great at Linmodem, aren't they?

L Campbell, could you give us a link to the tarball they've sent you?

Cheers,[/QUOTE]

Hello again, thanks for your continued interest.

[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
 
slmodem-2.6.12-9-386..> 17-Dec-2005 19:29   815k 

Here is the link and the file is about halfway down the page. There are a LOT of files on the page so I did a "Find on this page..", with the criteria ' Dec-2005 ' and it was the second hit.

I'm making the assumption that this is the same file (or has the same contents) as the one shown here, that the gentleman at Linmodems included with his E-mail to me. 

slmodem_2.6.12_9_386.tar.gz (815k)

Hoping my explanation makes sense..........     :-)

Kind regards.

---

### Post by towsonu2003 on 2006-02-02
too long a thread this is, out of my ability to follow what's going on. so I wanted to post (and hopefully update) the links in my signature, which may be helpful for others reading this.

PS. I am using the slmodem precompiled as well, and it is SOOOO nice \\:D/ 
ubuntu has this thing in the repos (and installation cd?) as well (slmodem-deamon??) but I have no idea how to use and configure to my needs. you might be interested if you're not as lazy as me. a search in synaptic for modem should show you the deamon. 

I have an open thread about how to configure this deamon (which, after getting some responses will go to the wiki page) but I got no responses so far :cry:

---

### Post by L Campbell on 2006-02-03
[QUOTE=towsonu2003]too long a thread this is, out of my ability to follow what's going on. so I wanted to post (and hopefully update) the links in my signature, which may be helpful for others reading this.

PS. I am using the slmodem precompiled as well, and it is SOOOO nice \\:D/ 
ubuntu has this thing in the repos (and installation cd?) as well (slmodem-deamon??) but I have no idea how to use and configure to my needs. you might be interested if you're not as lazy as me. a search in synaptic for modem should show you the deamon. 

I have an open thread about how to configure this deamon (which, after getting some responses will go to the wiki page) but I got no responses so far :cry:[/QUOTE]


Hi, I'm glad to see you are still interested in this subject.

After 3 months of trying to get online with my Ubuntu, I have decided to give Fedora a try and see if the guys over there have got this dial-up thing figured out.

I am convinced that, for Linux to have 'mass' appeal, it HAS to have user friendly access via dial-up.  This is based on my theory that there are more people at the 'bottom of the pile' and, consequently, more people who might be interested in using a computer if they didn't have to shell out the big bucks for cable, DSL, etc.

Kind regards.

---

### Post by Rhino1 on 2006-02-03
I too had a lot of trouble attempting to find a dial-up modem to work, but only on Xandros. On Ubuntu, I'm using a Conexant HCF with the free 14.4kbps drivers from Linuxant.  I also have to initialize the driver on Windows before loading my Linux system....this consists of loading windows, connecting with a different modem, and disconnecting, then a reboot to linux.  My HCF modem runs in/out of the first modem to get to phone line.  Don't know why this works.. just does.  I also use Dillo web browser, due to slow speed connection, works OK for me.  If I need to download something big, I reboot to windows and drag it over later.  Am asking for hardware modem for B-day. Good luck.

---

### Post by towsonu2003 on 2006-02-03
[QUOTE=L Campbell]
After 3 months of trying to get online with my Ubuntu, I have decided to give Fedora a try and see if the guys over there have got this dial-up thing figured out.
[/quote]did fedora worked?
[QUOTE=L Campbell]
I am convinced that, for Linux to have 'mass' appeal, it HAS to have user friendly access via dial-up.  This is based on my theory that there are more people at the 'bottom of the pile' and, consequently, more people who might be interested in using a computer if they didn't have to shell out the big bucks for cable, DSL, etc.[/quote]I totally agree, hence the first link in my signature. Unfortunately, that thread did not get any attention from the developers, who appearantly are using broadband-like networks (hence our dependence on online repositories but no additional CDs) and thay're not really concerned with winmodems (and hence, the fourth link I recently put in my signature).
[quote=Rhino1]I also have to initialize the driver on Windows before loading my Linux system....this consists of loading windows, connecting with a different modem, and disconnecting, then a reboot to linux. My HCF modem runs in/out of the first modem to get to phone line. Don't know why this works.. just does. I also use Dillo web browser, due to slow speed connection, works OK for me. If I need to download something big, I reboot to windows and drag it over later. Am asking for hardware modem for B-day.[/quote]wow that's some hassle... I wouldn't be as patient as you are with that...

---

### Post by L Campbell on 2006-02-05
[QUOTE=towsonu2003]did fedora worked?
I totally agree, hence the first link in my signature. Unfortunately, that thread did not get any attention from the developers, who appearantly are using broadband-like networks (hence our dependence on online repositories but no additional CDs) and thay're not really concerned with winmodems (and hence, the fourth link I recently put in my signature).
wow that's some hassle... I wouldn't be as patient as you are with that...[/QUOTE]


Hello again.

No, I'm not online with Fedora yet but its only been about a week.  At first it was one step forward and 2 steps back but now it seems to be 2 steps forward and only one step back.   :-)

I am still very optimistic and am planning to visit a Linux club when they have their monthly meeting next week.

Kind regards.

---

### Post by L Campbell on 2006-02-05
[QUOTE=Rhino1]I too had a lot of trouble attempting to find a dial-up modem to work, but only on Xandros. On Ubuntu, I'm using a Conexant HCF with the free 14.4kbps drivers from Linuxant.  I also have to initialize the driver on Windows before loading my Linux system....this consists of loading windows, connecting with a different modem, and disconnecting, then a reboot to linux.  My HCF modem runs in/out of the first modem to get to phone line.  Don't know why this works.. just does.  I also use Dillo web browser, due to slow speed connection, works OK for me.  If I need to download something big, I reboot to windows and drag it over later.  Am asking for hardware modem for B-day. Good luck.[/QUOTE]


You're a hero, Rhino1 but, realistically, that is really too much trouble for an average person.

With my SmartLink modem and Mepis, getting online was something a 6 year old could have done so, to my mind, if Mepis has this capability, why doesn't Ubuntu, Kubuntu, Fedora, Knoppix, etc.?

Well, when I, finally, do get online, I hope to be able to share the knowledge I aquired with others.

Kind regards.

---

### Post by mayankgarg1 on 2006-02-08
Hi 
please help me in connecting with serial modem.

---

### Post by towsonu2003 on 2006-02-08
[QUOTE=mayankgarg1]Hi 
please help me in connecting with serial modem.[/QUOTE]
Serial modems should be supported out of the box. Please refer to the second section of [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)
Here is the direct link to that section: [https://wiki.ubuntu.com/DialupModemHowto#head-c2e5e02fc299ef02bf3484aa89654a40e8ba2d2a](https://wiki.ubuntu.com/DialupModemHowto#head-c2e5e02fc299ef02bf3484aa89654a40e8ba2d2a)
Choose whichever works for you in configuring the modem.

---

### Post by hasala on 2008-02-06
(if you use this method you can forget about the rpms no rpm will be needed to be installed for you to get the modem running.)
RATHER THAN EXTERNAL MODEMS internal modems offloads a lot of funtionality to the software driver.it has always been a big problem to configure those internal modems or(WINMODEMS/LINMODEMS) to work with linux because of manufacturers not supporting linux (and also the driver being pretty much more complex than ) But due to a great person Linux maintainer Sasha Khapyorsky writing the neccassary drivers needed to work the winmodem , now using a internal modem in linux has become as easy as ABC.


Linux maintainer: Sasha Khapyorsky. Get his updated software from:
[http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)


what to do.

1. download a software called scanmodem from the foresaid site.

2. Browse [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) and  download scanModem.gz .
 Within a Linux partition open up a console and type in the following commands
    gunzip scanModem.gz
 To make it executable:
    chmod +x scanModem
 Run diagnositics with:
    ./scanModem 
3.scanmodem will check your hardware and software and then write its diagnostics to a subdir called modem.

4.open the ModemData.txt file.and go to   -----------end Softmodem section----------- part .

5.it will give the softwares you need to download and install.

6.if u have not installed the source at the installation of the distro. please install it.(source of the kernel) from the installation cd/dvd.

7.then install the downloaded software.

8.go to scanmodem/modem and open the diagnostic file chipsetname.txt eg:Smartlink.txt/conexant.txt .

9.In the start of the doc it gives the commands you have to run at the console to load the drivers that u downloaded and installed.

10.make sure that the smpppd, pppd services are installed and running.else install both and remember to enable them.

11.dial up using kinternet(i prefer it) or kppp. put to stupid mode option..now configure kinternet and the modem properly.to do that 
 goto yast->network devices ->modem.
           1.choose your modem device and press edit.
              enter modem device as /dev/ttySL0 and enter the details of the isp. if you are not sure call customer support for internet of your isp (internet provider) and get the required details such as number to dial and prefix.username
and password.

           2.remember to definitely check the box for stupid mode.

now every thing is set up

enjoy the internet with a great browser like firefox/opera.!!!!!!!
(with this you do not need any rpm for you to download,what you compile is enough)
if u have any comments or questions please mail to:dharmawardena_06@elect.mrt.ac.lk

						or [email]hasaladharmawardena@yahoo.com[/email]
or //(hasalaid@gmail.com).

hasala dharmawardena
faculty of engineering
department of electrical engineering([www.elect.mrt.ac.lk](www.elect.mrt.ac.lk))
University Of Moratuwa
SRILANKA

regards from srilanka , hasala.         ([www.hasala.bravehost.com](www.hasala.bravehost.com))

---

### Post by eeried on 2008-02-08
If you are lucky enough to have a smartlink modem, then things are straightforward. On the contrary HSf modems are hell simply because there's no free driver. The free edition is useless and if you buy the driver, don't forget you need to buy one again every time the kernel version is updated.

I think Linuxant drivers deserve to be pirated though I wouldn' know how. There's no excuse for making Linux users paying when windows users don't even have to install a driver for that piece of cr*p at all.
:mad:

Unfortunately many laptops are sold with that Conexant rubbish, and it is difficult to have an external modem on a laptop since there's no serial port. The alternative is an expensive PCI card which has to be installed inside the laptop, which can be a rather daunting task.

---

