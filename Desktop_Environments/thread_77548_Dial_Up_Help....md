---
title: "Dial Up Help..."
date: 2005-10-17
forum: Desktop Environments
---

### Post by sardopsycho on 2005-10-17
I am new to Linux and Ubuntu and I am loving it so far.  Problem is the beginners forum isn't helping me.  I need to know how to setup a dial-up internet connection for my system and I do not know how in Ubuntu 5.10....

Help?

Thanx in advance...

---

### Post by migueljacq on 2005-10-17
[QUOTE=sardopsycho]I am new to Linux and Ubuntu and I am loving it so far.  Problem is the beginners forum isn't helping me.  I need to know how to setup a dial-up internet connection for my system and I do not know how in Ubuntu 5.10....

Help?

Thanx in advance...[/QUOTE]

Hi,

Go to your terminal and type 'sudo pppconfig'. Follow the instructions to set up a 'provider' account. If you don't know your modem port, I think you can tell the computer to auto-detect it. If you need to specify your ISP's DNS, make sure you choose 'Static' at this option. Otherwise I think choosing 'Dynamic' will make the modem autodetect it during the handshake with the ISP.
Upon doing that, I personally had problems using the 'pon' 'poff' terminal commands. Instead, I went to System >> Networking. 
Open the properties under 'Modem', tick 'this device is configured', enter the phone number and your account details. 
Then you should be able to dial out. Let me know if it doesn't work.

Miguel

---

### Post by sardopsycho on 2005-10-17
nope..nothin..and the system has the right hardware to

---

### Post by migueljacq on 2005-10-17
[QUOTE=sardopsycho]nope..nothin..and the system has the right hardware to[/QUOTE]
Can you tell me where it actually went wrong? Does it dial out but you can't access the internet?

---

### Post by sardopsycho on 2005-10-17
I dont even know HOW to make it dial lol - noob here :)

---

### Post by migueljacq on 2005-10-17
[QUOTE=sardopsycho]I dont even know HOW to make it dial lol - noob here :)[/QUOTE]
That's alright. Just make sure your modem is switched on and plugged into one of (probably two) ports in the back of the machine.
If you run pppconfig and follow the steps it should be alright. It might depend on what type of protocol you use to dial (pap, chap, etc). I personally use PAP. Then all I have to do is put in my account name, and my password. I had my DNS (nameservers) so I put them in manuall using 'Static'. Modem speed 115200 or whatever it is. 
You can also try to change the port: from either ttyS0 or ttyS1 usually. 
If the configuration is right, you should be able to go to your Networking menu, fill in the details (number and account again) and press activate.
I'm writing this from memory by the way, since I am at work and under the Microsoft chains :(

---

### Post by migueljacq on 2005-10-17
[QUOTE=sardopsycho]I dont even know HOW to make it dial lol - noob here :)[/QUOTE]
When you go to the terminal and type sudo pppconfig and it starts the config program -- how far do you get? The trick sometimes with pppconfig is moving around the menus - if you simply press 'enter' after typing, sometimes it thinks you've finished. if you get to the end of the config and it presents you with a little summary, make sure you choose 'Finished write files and return to menu' and then exit the program.
According to the ubuntu guide you can then run in the terminal 'sudo pon (your provider name - probably just 'provider' if you left it as the default).
Chances are if you haven't got this far, it's probably just the configuration. Have you got your login, your ISP's phone number, the DNS if possible? All the basics?

---

### Post by sardopsycho on 2005-10-17
It is an internal HSF 56K PCI modem.  Breezy has picked up the device with no problem.  At your advice, I tried ALL the ports.  However when I go to activate the modem, I keep getting the error (again no matter what port I choose), "Could not enable the interface ppp0 - Check that the settings are correct for this network and that the computer is correctly connected to it".

The modem worked fine in Windows XP...

not sure what I am missing here

---

### Post by migueljacq on 2005-10-17
[QUOTE=sardopsycho]It is an internal HSF 56K PCI modem.  Breezy has picked up the device with no problem.  At your advice, I tried ALL the ports.  However when I go to activate the modem, I keep getting the error (again no matter what port I choose), "Could not enable the interface ppp0 - Check that the settings are correct for this network and that the computer is correctly connected to it".

The modem worked fine in Windows XP...

not sure what I am missing here[/QUOTE]

Ok - that definitely sounds like it's the configuration. So you need to make sure you covered all the steps in pppconfig. You have to run pppconfig and configure it all first, before you can try to activate it.
I'll be heading home soon so if you stick around, in 2 hours or so I can post the pppconfig steps one by one.
Don't give up! I had this dialup problem too and it took me a day to figure it out.

---

### Post by sardopsycho on 2005-10-17
I have to get to bed, so if you leave directions, I will grab them in the AM and try it....it's 2:30 AM over here heh.....thanx for all your help :)

PAul

---

### Post by migueljacq on 2005-10-17
Alright here is a guideline for pppconfig:
1. Open your terminal
2. type sudo pppconfig (then password if prompted)
3. Choose 'Create Create a Connection' - press TAB to OK and then Enter
4. Give it a name (may as well leave it as 'provider' press TAB to OK then Enter
5. Configure DNS: If you know your nameservers (you can call your ISP and ask), go to 'Static', press spacebar to * it, tab to OK then Enter. Otherwise go to Dynamic and press spacebar, TAB to OK then Enter.
6. (assuming you chose Dynamic) Choose the protocol (your ISP can tell you, I would take a guess at PAP) TAB to OK then Enter
7. enter your login name i.e 'john@doe.com.au' TAB to OK then Enter
8. enter your password, TAB to OK then Enter
9. enter modem speed (I would leave it at 115200),  TAB to OK then Enter
10. enter method of dialing (spacebar to * (i use tone)),  TAB to OK then Enter)
11.enter in the ISP's phone number to dial,  TAB to OK then Enter
12. you can choose to have your modem identified automatically, or TAB to No and choose the port yourself
13. go down to 'Finished Write files and return to main menu.'  TAB to OK then Enter
14. OK
15. Go down to 'Quit Exit this utility',  TAB to OK then Enter
16. Now you can either type into the terminal 'sudo pon provider' (sometimes for me it doesn't work first go (modem doesn't activate), try it a couple of times
Or if 'sudo pon provider' doesn't work, you can go to 'System >> Administration>> Networking>> choose the modem, go to Properties
'Enable This Connection', tick the box
Enter phone number, username and password (same as before). Click on the 'Modem' tab and identify the port.
After that, click OK and then 'Activate'. It ought to work, if not, let me know and I will try to think of something else I might've forgotten :-)

---

### Post by sardopsycho on 2005-10-17
Literally have done everything you just listed trying ALL modem ports listed.  Nothing...system does not dial out, nothing.

---

### Post by migueljacq on 2005-10-17
Truly weird. Especially as your computer detects your modem, doesn't sound like a hardware problem then. Are you sure your phone cord is plugged in? hehe
I have no more answers. Suggest following towsonu2003's advice (in the beginner talk where you also posted) using wvdial and cut and paste any error reports (delete your account and password details from any errors first). It would be interesting to see what the computer says in wvdial.

---

### Post by strate on 2005-10-19
Hi sardopsycho,

Have been watching this thread for two days, 'cause I've got the same problem.

[QUOTE=sardopsycho]It is an internal HSF 56K PCI modem.  Breezy has picked up the device with no problem.  At your advice, I tried ALL the ports.  However when I go to activate the modem, I keep getting the error (again no matter what port I choose), "Could not enable the interface ppp0 - Check that the settings are correct for this network and that the computer is correctly connected to it". The modem worked fine in Windows XP...[/QUOTE]

*Exactly* the same thing, except that I've got PCTel HSP56 modem. As far I understand it, it's a winmodem which has some serious issues under Linux.. since Connexant bought PCTel and stopped releasing drivers. I tried scanModem.gz to verify the chipset (789), and I found some interesting resources: [http://linmodems.technion.ac.il/pctel-linux/welcome.html](http://linmodems.technion.ac.il/pctel-linux/welcome.html) .

So, today, if these drivers don't work, I'm off to the nearest dealer to get myself a decent _hardware_ modem.. At least, it's an interesting experience for a Linux newbie :)

HTH,
Nikola

---

### Post by darius_underhill on 2005-10-19
[QUOTE=sardopsycho]It is an internal HSF 56K PCI modem.  Breezy has picked up the device with no problem.  At your advice, I tried ALL the ports.  However when I go to activate the modem, I keep getting the error (again no matter what port I choose), "Could not enable the interface ppp0 - Check that the settings are correct for this network and that the computer is correctly connected to it".

The modem worked fine in Windows XP...

not sure what I am missing here[/QUOTE]

Isnt this a winmodem?

---

### Post by sardopsycho on 2005-10-23
Welp....still having issues here.  I think it might be a driver issue.  Any suggestions would be welcome so I could get this darned thing working..

---

### Post by migueljacq on 2005-10-23
I've been doing some research and it appears any winmodem is going to have problems in linux.
Someone else had a USB modem and had the same problems. They ended up buying a serial modem and had no problems. Mine is a serial modem (on the COM port ttyS0)

---

### Post by johnfimo on 2005-12-19
I am experiencing problems with a USB modem with Ubuntu 5.10.
There seems to be a number of opinions on the Ubuntu Forum, but I think the issue is kernel related.
My modem is a Netcomm Roaster V.92 USB.
When the kernel boots, it probes the modem, initialises the USB power, communicates with the modem and continues to boot.
It seems that there are no usb drivers installed with the Ubuntu Gnome setup.
A similar problem occurs in the Fedora/Centos distros as well.
The Mephis distro kernel install a USB driver and will dial out and communicate with the net.
I do not known anything about kernel compiling but from my observations it seems different distro kernels suffer from compile problems.
In the case of Ubuntu 5.10, the USB drivers are missing.
Before starting a flame war, I have read through all the Linux documention available; Linux from Scratch, Debian, Gentoo, Red Hat etc, and I am just stating an observation.
Linux may be a good server system when compiled, built and sold into a commercial environment, but unfortunately for us mortals the free distros have thier faults.
My System:
Intel Battle Lake D915PBL Motherboard, 3Ghz Pentium 4 Prescott, 1gb ram,
Nvidia 6600GT PCI-E graphics, 200gb WD HDD.
The motherboard is certified by Intel for multimedia work and should work 100% in a Linux environment.
All the Linux motherboard drivers are on the Intel site, but for what ever reason different Linux distros refuse to work 100% on the motherboard.
I think the problem may be the magic ink that the disk manufacturer's place on the top side of the CDROM's. Maybe it is just that Microsoft perfected the ink and turned it into a billion dollar corporation.

---

### Post by L Campbell on 2005-12-19
[QUOTE=sardopsycho]I have to get to bed, so if you leave directions, I will grab them in the AM and try it....it's 2:30 AM over here heh.....thanx for all your help :)

PAul[/QUOTE]


I feel your pain, Paul, as I, too, have been struggling to get online with dial up.

Maybe this link will help you:- 
[http://ubuntuforums.org/showthread.php?t=95544](http://ubuntuforums.org/showthread.php?t=95544)

Several good people have been very helpful to me but maybe I'm a Linux Dunce, anway, I REALLY believe that I will be online soon.

Best of luck to you.

---

### Post by medya on 2005-12-19
hey peopel of the world listen :
 I HAVE THE SAME PROBLEM !!!


I have a HCF - MOTHER F///K// CONEXANT. 
it is zoltrix smart sprit .

i can see the modem in the Device Manager, but it never dials...
please help me , how to dial 


I really hope Conexant Head , Die Today.... he is torturing peopel of the world..
Jesus Christ , please send this man to hell .Amin .

---

### Post by medya on 2005-12-20
******* ping ***** somebody help please.

---

### Post by N8MAN1068 on 2005-12-20
I had an internal winmodem for the longest time.
I spent hours upon hours trying everything under the sun to work.
Finally, I orderd an opened box external modem from Techforless.com
[http://www.techforless.com/cgi-bin/tech4less/process?id=xI2Z5NUx&mv_pc=42](http://www.techforless.com/cgi-bin/tech4less/process?id=xI2Z5NUx&mv_pc=42)

$25 and a few days later, I plugged everything in, rebooted for kicks, and was smooth sailing.

Short moral is, before you try ANYTHING, get an external modem.

---

### Post by kevinmthor on 2006-01-31
hi forum,

been reading this thread and trying to get my dial up to work. i have a few problems. to start off with, this is an IBM thinkpad laptop with built in modem.

one is that under the Network Settings, the AutoDetect of the modem turns up nothing. i ran the sudo pppconfig and when asked about a modem, it says that i have to configure manually, it cannot find it.

if i go under Network Settings and choose modem connection > properties > modem and put in /dev/modem, i then click on Activate and get this error: "Cannot enable interface ppp0". if i put in /dev/ttyS1 i can then click Activate and it will say that the modem is now active. however, i close this dialog box and then re-open it and the modem is set back to inactive. i have tried this with all others to the same effect.

do i need an external modem? if so, how does this work from a laptop?

next, what do i do to make ubuntu dial out to the internet? so far i have not seen anything that says "Connect to Internet". i have seen the "connect to server" under the Places menu but, that only lists SSH, FTP, etc...

thanks in advance for any advice.

k

---

### Post by ddtmsa on 2006-02-01
[QUOTE=kevinmthor]
if i go under Network Settings and choose modem connection > properties > modem and put in /dev/modem, i then click on Activate and get this error: "Cannot enable interface ppp0". if i put in /dev/ttyS1 i can then click Activate and it will say that the modem is now active. however, i close this dialog box and then re-open it and the modem is set back to inactive. i have tried this with all others to the same effect.
[/QUOTE]

This is the correct way to set up your modem, the problem is you almost certainly have a winmodem and you will need to compile a /dev/modem file from scratch. 

You will need to find out what modem chipset you have in your Thinkpad.

> 
do i need an external modem? if so, how does this work from a laptop?


You don't need an external modem, but depending on your experience it may be the easiest option (either that or broadband).

> 
next, what do i do to make ubuntu dial out to the internet? so far i have not seen anything that says "Connect to Internet". i have seen the "connect to server" under the Places menu but, that only lists SSH, FTP, etc...


When you've got your modem set up, all you have to do is go through the Network Settings menu and select Active Modem! Dead easy ... after the first time :-(

---

### Post by kevinmthor on 2006-02-01
hi ddtmsa,

ok, i have from ibm a lucent modem driver for ibm 600X type computers but, my USB drive is not coming up so, i have no way to get this on the machine at the moment. i have posted to another thread about my USB and am working on it. 

once i get this driver installed, how do i compile a /dev/modem file?

thanks for the replies.

k

---

### Post by ddtmsa on 2006-02-01
[QUOTE=kevinmthor]
ok, i have from ibm a lucent modem driver for ibm 600X type computers but, my USB drive is not coming up so, i have no way to get this on the machine at the moment. i have posted to another thread about my USB and am working on it. 
[/QUOTE]
I've not had any problems with USB (so far, obviously this is my next ubuntu mini-project sometime soon :-) ) so I cannot help there. As for the modem, you will need to find out precisely which lucent chipset you have, I suggest looking at the site

[http://linmodems.org](http://linmodems.org)

as a starting point, especially for the scanmodem utility, which will give you the necessary information. It also contains links to faqs for lucent modems users. There is also the lucent website

[http://www.lucent.com](http://www.lucent.com)

from which you should get the manufacturer's support. I've got an intel modem, so haven't had to use the lucent site.


> 
once i get this driver installed, how do i compile a /dev/modem file?


Before you do anything you will need to install the build-essential and linux-headers files from the CD. In a terminal window, type the following commands

sudo apt-get install build-essential
sudo apt-get install linux-headers2.6.12-9-386

You may then also need to install some compliler files, but that is a couple of steps down the line, and something to worry about later!

Keep thinking, mini-project and learning curve, if getting ubuntu online is not urgent.

---

### Post by kevinmthor on 2006-02-01
hi ddtmsa,

ok, i burned a cd with the shell script from here:

[http://www-3.ibm.com/pc/support/site.wss/MIGR-4VFTT3.html](http://www-3.ibm.com/pc/support/site.wss/MIGR-4VFTT3.html)

this is supposed to be from my modem. i ran the shell script and get these errors from it:

ERROR: Module ltserial does not exits in /proc/modules
ERROR: Module ltmodem does not exits in /proc/modules

mv : cannot stat ' /etc/rc.d/rc.local': no such file or directory
etc, etc...

now what?

k

---

### Post by kevinmthor on 2006-02-01
hi,

i went to linmodems.org and clicked on the link for the Mwave modem driver for thinkpad 600e and was just thrown to the ibm home page. apparently the link for this is no longer valid.

then i did a search on ibm site for a linux modem driver and got to this page:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4BP6Q6](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4BP6Q6)

about half way down is a table about built-in devices supported by linux. it states this:

ACP Modem  	No  	No drivers available

should i even bother with scan modem or go straight to an external modem?

k

---

### Post by kevinmthor on 2006-02-01
ok, i downloaded scanmodem and ran it.

while reading ModemData.txt i see this:

A modem was not detected among the above PCI devices. 

i then read on that i can detect the modem in another way via SoftModem.txt so, i read that. a very confusing file but, i think i run lsmod to see my modem. after lsmod, i get a huge list of things but, nothing that looks like a modem.

any other suggestions?

k

---

### Post by kevinmthor on 2006-02-02
anyone on this? i still don't know where to go next. please read previous posts, thanks.

k

---

### Post by towsonu2003 on 2006-02-02
wow too many posts from too many people. wanted to post here for the links in my signature. I just couldn't follow whose problem with which modem is what... 

this is the only one I was able to follow a little bit:
[quote=kevinmthor]anyone on this? i still don't know where to go next. please read previous posts, thanks[/quote] english being a second language, it's hardddd following this thread...
kevinmthor-> can you attach (as a file, not copy-paste) softmodem.txt and modemdata.txt here? 
and for anyone who cannot understand what modemdata.txt is saying, you might wanna go to linmodems.org, read the page about how to send an email to their mailing list, and email them the modemdata.txt **after re-reading the first few sentences of the modemdata.txt**. they get mad when you don't follow their instructions :)

---

### Post by dgc on 2006-02-07
Yesterday, I just installed Ubuntu 5.10 on a box which had an HCF 56K modem and I had the same
problem,  that it showed up in the devices but could not get the thing working. 

SO, I then went to this site [www.linuxant.com/drivers/ ]("http://www.linuxant.com/drivers/")
and downloaded the automated driver installer... It worked flawlessly, and downloaded all the lib
dependencies that it needed directly. (I recommend doing it from the terminal, I could not get it to
work using the web browser) (AND of course you need a network connection to do it, too!)

The downside is that you only get limited functionality 14.4k for free and if you want to get FULL 
functionality you need to buy the Upgrade license ... 20 USD ... 

After reading their explanation for this, I can understand but decided to live with limited functionality 
since it will only be used for downloading email and some limited web browsing.

Hope this helps ...
dgc

---

### Post by towsonu2003 on 2006-02-07
> **dgc]Yesterday, I just installed Ubuntu 5.10 on a box which had an HCF 56K modem and I had the same
problem,  that it showed up in the devices but could not get the thing working. 
[/QUOTE]
I'd say file a bug on that issue  said:**
> After reading their explanation for this, I can understand Although their reasons seem logical from a distance, it is not that hard to let the community do the work (write drivers) for them, for free... The only thing they'd need to do would be to assist linmodems.org people in their efforts...

---

