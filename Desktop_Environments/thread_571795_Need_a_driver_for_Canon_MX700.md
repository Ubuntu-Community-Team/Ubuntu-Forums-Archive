---
title: "Need a driver for Canon MX700"
date: 2007-10-09
forum: Desktop Environments
---

### Post by eg-maverick on 2007-10-09
I've searched all over for a driver for my Canon PIXMA MX700. Can't find anything. I also tried a few other Canon drivers but no luck. I would be satisfied (for now) with basic print capability. Any "generic" Canon drivers out there?
Thanks,
Craig

---

### Post by eg-maverick on 2007-10-14
bump.

---

### Post by jacekbuntu on 2007-10-24
> **eg-maverick said:**
> bump.

I've just bought the same printer MX700 and I did not find anything.

---

### Post by tealnet on 2007-11-23
I just picked one of these up as well.  Excellent multi-function device!  But I too would love even basic printing support for Ubuntu.  I don't even see any of the MX series in the driver list.

---

### Post by icecream17 on 2007-12-05
Hej,

I'm thinking about buying the MX700 as well, but only if there's a linux driver available.

Well, there's a problem with some Canon printers, but for the MP530 there is a solution
here: .[http://www.rosemaryroad.org/computer_log.html](http://www.rosemaryroad.org/computer_log.html)

Maybe this works for the MX700 as well? Would any of you guys here give it a try?

Note that I had a similar problem with S520, and the trick worked there as well (normal cups drivers would just give me black & white, but problems with color graphics, but everything works fine now with these drivers from Japan.

Icecream17

---

### Post by BlackTiger4u on 2007-12-20
Hi,

I just bought the Canon Pixma MX700 too :lolflag:

Didn't think about the possibility that there are no Linux drivers released baw Q_Q"

Does anyone have the MX700 working yet?

**Edit:** Yeah, I finally got the printer working using the TurboPrint PIXMA MP520 driver (MP510 works aswell) :) Not a final solution, but a good workaround!

**Edit2:** Update! It seems like I managed to get the MX700 print function fully working up to 4800dpi! Works with the TurboPrint AND the official Canon drivers! Modified the TurboPrint driver (Base MP510) and the official one (Base MP520 V2.80) :)

Thanks in Advance,
BlackTiger

---

### Post by gjarboni on 2007-12-26
Sorry if this is obvious, but how wouldI get the drivers that you modified. Thanks in advance,

Jason M.

---

### Post by Johnsont on 2008-01-01
I was able to at get basic printing working using the MP520 drivers. I haven't gotten anything working using Ethernet, only with USB.

I was able to get the drivers from here:

[http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp520_support.aspx]("http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp520_support.aspx")

Everything installed fine and then I just selected these drivers during configuration.

---

### Post by BlackTiger4u on 2008-01-01
> **Johnsont said:**
> I was able to at get basic printing working using the MP520 drivers. I haven't gotten anything working using Ethernet, only with USB.

I was able to get the drivers from here:

[http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp520_support.aspx]("http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp520_support.aspx")

Everything installed fine and then I just selected these drivers during configuration.

Yep that's the official one which works here too :)

I attached my modified *.ppd for the MX700 printer to support printer function up to 4800 dpi :D

Just remove the .txt part of the filename and move the canonmx700.ppd to /usr/share/cups/model

Best Regards
BlackTiger

---

### Post by Metaljaz on 2008-01-05
just got this printer for xmas and was wondering if anyone has had any luck with the wireless working in ubuntu.

---

### Post by Metaljaz on 2008-01-05
tried installing the deb file using:

sudo dpkg i- cnijfilter-mp520series_2.80-1_i386.deb

but was unsuccessful. What am I doing wrong?

---

### Post by RepoMonkey on 2008-02-09
Not an ideal solution by any stretch of the imagination - but I have the MX700 running on a mixed network of Windows/Linux PCs. I just shared the MX700 on one of the Windows machines and added the printer as a Samba share.

---

### Post by Metaljaz on 2008-02-09
never tried using samba but i can give it a try..

---

### Post by zubrug on 2008-02-14
> **Metaljaz said:**
> tried installing the deb file using:

sudo dpkg i- cnijfilter-mp520series_2.80-1_i386.deb

but was unsuccessful. What am I doing wrong?

Try 
sudo dpkg -i cnijfilter-mp520series_2.80-1_i386.deb

If you get a dependancy error then do a sudo apt-get -f install  and it should finish.

---

### Post by Metaljaz on 2008-02-14
tks zubrug for the reply.

---

### Post by peakay on 2008-02-18
OK, linux newbie here.  I was able to get my mx700 printing using blacktiger's ppd file and printing through our family windows machine using samba.

Is there a way to get this to print directly to the mx700 through our network? It's a network enabled printer plugged into our router via hard wire ethernet.

thanks!

---

### Post by Metaljaz on 2008-02-18
That is the same way that mine is plugged in and I wanted to use it without using samba. I had an HP that I had set up to a win vista box and could print with my ubuntu laptop wireless setup. If i can't get this one to do the same thing I guess I will have to go back to HP.

---

### Post by jesse c on 2008-02-25
im a linux/computer newby with new canon mx700 printer with dual boot ubuntu/vista box. driver works on vista not on ubuntn. I found BlackTigers file ,downloaded it copied and pasted into terminal but got a lot of "command not found" entries throughout.Was there something i was supposed  to add to file,like sudo or whatever? This is my first time using terminal so dont know how to deal with second party files i have only used synaptic successfully.Any education would be appreciated. thanks  JESSE C

---

### Post by Michael Schmidt on 2008-03-02
I'm a Linux/Ubuntu newbie, and so far I love it.  I bought a Pixma MX700 while I had Windows XP and it is a great printer.  I noticed on the Canon Europe site there is a Max OS X CUPS driver.  Can that be useful for Ubuntu?

---

### Post by bharadwaj on 2008-03-03
This printer worked for my pal in SuSe. Did you try updating your Ubutu??

---

### Post by highwaystar42 on 2008-03-18
How abaout the Scanner?
Does it work?

---

### Post by nicolos on 2008-03-19
Hi, 
Concerning network printing with MX700 and cups, try to install the printer using the following cups URIs: 
socket://printerIP@
or
lpd://printerIP@

For instance: 
socket://192.168.1.2 
or 
lpd://192.168.1.2

---

### Post by nicolos on 2008-03-19
FYI, PIXMA MX700 scanner is now supported by the Sane pixma backend, for both flatbed and ADF scanning. :)

You can get the libsane-pixma 0.14.4 driver on the MP610 blog site (see signature below), or get the latest Sane CVS and recompile/reinstall Sane-CVS.

Nicolas

---

### Post by terryh on 2008-03-27
Has anyone succeeded with printing to an *** ethernet-attached  ***   MX700?
If so, what are the details of your recipe?

After much thrashing about, I think I can say:

1. CUPS does not support the type of protocol this printer uses;

2. running wireshark (on WinXP) and tracing a successful print interaction,
   the XP client first interacts with UDP packets to port 8611 on the printer,
   then switches to interacting with TCP to port 8611 on the printer.    There
   are reserved ports listed (but not in Ubuntu's /etc/services file)  for:                        
          #    Atsushi Nakamura <nakamura.atsushi318&canon.co.jp> November 2003
         canon-bjnp1     8611/tcp    Canon BJNP Port 1
         canon-bjnp1     8611/udp    Canon BJNP Port 1

         canon-bjnp2     8612/tcp    Canon BJNP Port 2
         canon-bjnp2     8612/udp    Canon BJNP Port 2
 
         canon-bjnp3     8613/tcp    Canon BJNP Port 3
         canon-bjnp3     8613/udp    Canon BJNP Port 3

         canon-bjnp4     8614/tcp    Canon BJNP Port 4
         canon-bjnp4     8614/udp    Canon BJNP Port 4

3. the protocol seems to be something called BJNP, but it is not publicly    
    documented, AFAIK.

4. as pointed out in the posts above, Canon JP (and AU) seem to offer some support
    for Linux on some of its (far too many) printers (but NOT MX700 yet), but Canon USA 
    seems to never have heard of Linux...

5. it isn't clear that these Linux drivers support Ethernet-connected mode.  The
    source code provided has woeful documentation.

Is there any hope for Ethernet-connected mode for the MX700 ever working
on Ubuntu?     At this point, I'm regretting this purchase.

Thanks,
Terry

---

### Post by AlanB66 on 2008-03-27
I've been reading and diddling and I don't know if this is old news or helpful to help someone here get a little further, but ...

I used "other (CUPS URI)" and specified:
  ipp://IPaddress:8612

When I try a test page, it now sits at "Connected to 192.168.1.222 on port 8612 ..."

It's not printing, but it's not erroring, as usual, this time.

Now what?  :confused:

---

### Post by AlanB66 on 2008-03-27
When I look in my Windows registry at HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Print\Monitors\Canon BJNP Port\Ports\CNBJNP_############, I see a Target Port of 8611. 

When I look in my Windows registry at HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Print\Monitors\Canon BJNP Port\Ports\CNBJNPFAX_############, I see a Target Port of 8613.

Just more info, just in case it helps for us to solve this together.

---

### Post by nicolos on 2008-03-27
So did you try also the following URIs ?  

socket://IPaddress:8611
or
socket://IPaddress:8612
...
or
lpd://IPaddress:8611
or
lpd://IPaddress:8612
...

---

### Post by AlanB66 on 2008-03-27
Yep. No go, though.:mad:

---

### Post by ThyMaster on 2008-03-30
I have the problem as you.

And I think we must face it:
There is no way to access (new?) Canon printers with LAN interface via LAN by any other OS than MacOS and Windows as they use their proprietary network printing protocol (CNBJNP) only.

The only solution I can think of it to add a USB printer server to and access the printer that way.

- ThyMaster

---

### Post by AlanB66 on 2008-03-30
Unless and until someone comes up with instructions that really get the MX700 viable over the network directly from Ubuntu, I solved it for now by making this a shared printer from my Windows PC.

I then used TurboPrint to configure a Windows Network printer, filled in all the details, and the test print went thru flawlessly.

So, a solution is:
1. Set up a PC with a USB or Network connection to the MX700
2. Set that PC's printer connection to the MX700 as Shared
3. Install TurboPrint to Ubuntu   ([http://www.turboprint.info/download2.html](http://www.turboprint.info/download2.html))
4. Use the Pixma_MP520 drivers (IJ Printer Driver Ver. 2.80 for Linux(debian Common package) [http://support-au.canon.com.au/contents/AU/EN/0100083403.html](http://support-au.canon.com.au/contents/AU/EN/0100083403.html))
5. Get the replacement PPD file for a Canon ([http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424](http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424)) and put it in place of the 520 PPD file(s) you find on your system
    (look for PPD here ==> /usr/share/cups/model/turboprint/Canon_Pixma_MP520.ppd   /usr/share/turboprint/ppd/Canon_Pixma_MP520.ppd)
6. Set up TurboPrint to see #2 ...
     Shortname: <anything you'd like>
     Config Name: Canon_Pixma_MP520
     Connection: Remote Windows
     Printer Name: <the share you called out on the PC>
     Server Name: <PC's host name>
     User Name: <your PC login>
     Password: <your PC password>
     Workgroup: <your PC's workgroup>
     IP Address: <your PC's IP address>

It should work for you, too.

---

### Post by shur on 2008-04-03
its working, thanks a lot.
Now i dont have to use the usb stick everytime.
Im a noob, but isnt it possible to use the canon software with wine? dont know

---

### Post by Frank64 on 2008-04-14
[COLOR="Navy"]No wine will not help, we are talking about drivers, not applications. Wine supports applications, but not drivers (nor does it support audio/video codec and such things).

As stated in this thread already, Canon had the "great" idea to use some proprietary protocol. Of course, we all discovered that after we bought the machine, which BTW is awesome anyway. :) I have asked them why, cuz that's unacceptable for us opensource guys and other brands are using standard protocols. I will certainly never get an answer. :)

But there might be hope. The driver (IJ Network tools) exists for OS-X which is as we know UNIX-based. If we could find some awesome developer, maybe he could work out something out of the MAC drivers for Linux.

Anyone would know of a super-developer stupid enough to give it a try but wise enough to know he will be super famous if he succeeds?:lolflag:[/COLOR]

---

### Post by awilki01 on 2008-04-24
> **AlanB66 said:**
> Unless and until someone comes up with instructions that really get the MX700 viable over the network directly from Ubuntu, I solved it for now by making this a shared printer from my Windows PC.

I then used TurboPrint to configure a Windows Network printer, filled in all the details, and the test print went thru flawlessly.

So, a solution is:
1. Set up a PC with a USB or Network connection to the MX700
2. Set that PC's printer connection to the MX700 as Shared
3. Install TurboPrint to Ubuntu   ([http://www.turboprint.info/download2.html](http://www.turboprint.info/download2.html))
4. Use the Pixma_MP520 drivers (IJ Printer Driver Ver. 2.80 for Linux(debian Common package) [http://support-au.canon.com.au/contents/AU/EN/0100083403.html](http://support-au.canon.com.au/contents/AU/EN/0100083403.html))
5. Get the replacement PPD file for a Canon ([http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424](http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424)) and put it in place of the 520 PPD file(s) you find on your system
    (look for PPD here ==> /usr/share/cups/model/turboprint/Canon_Pixma_MP520.ppd   /usr/share/turboprint/ppd/Canon_Pixma_MP520.ppd)
6. Set up TurboPrint to see #2 ...
     Shortname: <anything you'd like>
     Config Name: Canon_Pixma_MP520
     Connection: Remote Windows
     Printer Name: <the share you called out on the PC>
     Server Name: <PC's host name>
     User Name: <your PC login>
     Password: <your PC password>
     Workgroup: <your PC's workgroup>
     IP Address: <your PC's IP address>

It should work for you, too.

Works awesome!  Thanks!!!!  I can live with this for now.

Edit: Um, I guess I will just use my Windows PC for now to print from.  I don't feel like purchasing a license for TurboPrint to get rid of their logo on every print page.  I understand everyone needs to make a buck, but its just not worth it to me personally.

---

### Post by Frank64 on 2008-04-28
The problem with that TurboPrint-Windows-share solution is that you need a Windows machine. I don't like Windows, I trashed it in favor of Linux, so I don't want to use my old machine back with Windows and power it on every time I need to print.

So I have to live with what Linux has and what I can tweak for. Hum, I wonder if that could work through Windows in VMware... I'll try and see. Still, I would need to power on Windows in VMware every time I need to print.

---

### Post by AlanB66 on 2008-04-28
That IS the part that sucks. I agree.

You might try to:
1. print to postscript and then,
2. ftp the .ps file to the Canon.

Just not sure how.

---

### Post by Frank64 on 2008-04-28
> **AlanB66 said:**
> That IS the part that sucks. I agree.

You might try to:
1. print to postscript and then,
2. ftp the .ps file to the Canon.

Just not sure how.

Yeah me neither, I am even unsure the printer can take the .ps like that. Such a great printer, sad the functionalities are still basic (or workarounds aren't 100% Linux-based).

I can't even print in grayscale using the mp520 pdd. MP610ppd does not work, when the print command is sent, nothing happens, the job does not exist (I renamed mp610pdd to mp520ppd when I tried that), I don't know where it got lost. I'll have to try out some other things, hopefully next versions of our distros will support full USB printing. In my case I will fill up an enhancement for opensuse.

---

### Post by llagendijk on 2008-05-06
> **terryh said:**
> Has anyone succeeded with printing to an *** ethernet-attached  ***   MX700?
If so, what are the details of your recipe?

After much thrashing about, I think I can say:

1. CUPS does not support the type of protocol this printer uses;

2. running wireshark (on WinXP) and tracing a successful print interaction,
   the XP client first interacts with UDP packets to port 8611 on the printer,
   then switches to interacting with TCP to port 8611 on the printer.    There
   are reserved ports listed (but not in Ubuntu's /etc/services file)  for:                        
          #    Atsushi Nakamura <nakamura.atsushi318&canon.co.jp> November 2003
         canon-bjnp1     8611/tcp    Canon BJNP Port 1
         canon-bjnp1     8611/udp    Canon BJNP Port 1

         canon-bjnp2     8612/tcp    Canon BJNP Port 2
         canon-bjnp2     8612/udp    Canon BJNP Port 2
 
         canon-bjnp3     8613/tcp    Canon BJNP Port 3
         canon-bjnp3     8613/udp    Canon BJNP Port 3

         canon-bjnp4     8614/tcp    Canon BJNP Port 4
         canon-bjnp4     8614/udp    Canon BJNP Port 4

3. the protocol seems to be something called BJNP, but it is not publicly    
    documented, AFAIK.

4. as pointed out in the posts above, Canon JP (and AU) seem to offer some support
    for Linux on some of its (far too many) printers (but NOT MX700 yet), but Canon USA 
    seems to never have heard of Linux...

5. it isn't clear that these Linux drivers support Ethernet-connected mode.  The
    source code provided has woeful documentation.

Is there any hope for Ethernet-connected mode for the MX700 ever working
on Ubuntu?     At this point, I'm regretting this purchase.

Thanks,
Terry

Yes, there is some hope... I have started development of a cups backend for the BJNP protocol. It definitely needs more work, but I have got it working on my Canon MP970. It does contain some ugly hacks. If you want to test it, you will need to be able to compile the C-code. Please let ne know if you can compile CUPS as (for the time being) it needs to be compiled in the cups source tree. I have been developing it under Fedora, but it should compile in Ubuntu as well. Which version of cups does Ubuntu use? Right now I am using Cups 1.3, downgrading to CUPS 1.2 might take some work (which I plan to do anyhow as my other machine runs Centos, which uses CUPS 1.2)

Please let me know if you want to give it a try

---

### Post by Frank64 on 2008-05-06
Wow, nice work! I though those proprietary codes were sort of unbreakable.

I am using CUPS 1.2.12 on openSUSE 10.3, but openSUSE 11.0 Beta, which I run as well, has 1.3.7.

If could try to compile cups, I need 64-bits though. I might also need a little guide of the steps though, but I am definately interested to be part of the testing. I can offer 3 different test cases, which are CUPS 1.3.7 under VMware, CUPS 1.3.7 real life and CUPS 1.2.12 real life. I've got images of my HDDs so I can easily switch from one to another and I don't mind at all screwing everything up. :lol:

But before making the networking work, do we need to use a special PPD file or the one we currently use through USB (and any other) would work?

tnx!

---

### Post by llagendijk on 2008-05-07
> **Frank64 said:**
> Wow, nice work! I though those proprietary codes were sort of unbreakable.

I am using CUPS 1.2.12 on openSUSE 10.3, but openSUSE 11.0 Beta, which I run as well, has 1.3.7.

If could try to compile cups, I need 64-bits though. I might also need a little guide of the steps though, but I am definately interested to be part of the testing. I can offer 3 different test cases, which are CUPS 1.3.7 under VMware, CUPS 1.3.7 real life and CUPS 1.2.12 real life. I've got images of my HDDs so I can easily switch from one to another and I don't mind at all screwing everything up. :lol:

But before making the networking work, do we need to use a special PPD file or the one we currently use through USB (and any other) would work?

tnx!

To start off with the last question: no you do not need any special PPD files, nor do you really need to change the CUPS setup. The BJNP backend will be compiled in the CUPS source tree, but the resulting binary can be manually copied to the CUPS backend directory (probably something like /usr/lib(64?)/cups/backend. No need to mess up the existing cups setup. Then setup the printer queue and you should be all set.
I am primarily interested in a test with CUPS 1.3 in a native Linux setup,as I do not yet have the time to spend on debugging other OS's and environments (I am starting to work with the SANE pixma guy on intergrating BJNP support in Sane as well).

Please try to configure and compile CUPS on your box. I will send you a link to the source code and some instructions as soon as I found the time

---

### Post by Frank64 on 2008-05-07
I've got both 32-bits and 64-bits support for many things, so I've got both /usr/lib64/cups/backend and /usr/lib/cups/backend.

When you mention CUPS 1.3, you mean 1.3.x or 1.3.0? Just checking, sometimes it could make a difference.

If CUPS 1.3.x, then I would test that under a fresh native install of openSUSE 11.0 64-bits, with 1.3.7. I could upgrade CUPS on my main machine, from 1.2.12 to 1.3.7 as well, I'll see later on that. I could also test on a native v11.0 32-bits version no problem.

I am not in a hurry much cuz most of the time I spend on the printer I spend it on looking for the right PPD to take advantage of most of the MX700 functionalities, the mp600 and mp610 are not working and mp520 is very minimal support.

Anyway, I'm in any time to add the network functionality on that printer! :)

I appreciate the time and effort you put on that. I was not expecting it could be possible to "hack" a proprietary protocol, thumbs up!

Anybody else want to test on a different distro, if possible?
tnx

---

### Post by AlanB66 on 2008-05-07
> **Frank64 said:**
> Anybody else want to test on a different distro, if possible?
tnx

I might be willing to test out my Ubuntu 8.04 (32-bit) if you give me some instructions on what to do.

I understand "sudo make all" and "sudo make install", but if there are other steps, I'll need them spelled out a bit.

I'll take an image of my partition before attempting this so that I can easily get back to where I am - everything working, so far - if this fails to satisfy.

Thanks,
Alan

UPDATE: I think I have Cups 1.2.0.

---

### Post by llagendijk on 2008-05-09
> **Frank64 said:**
> I've got both 32-bits and 64-bits support for many things, so I've got both /usr/lib64/cups/backend and /usr/lib/cups/backend.

When you mention CUPS 1.3, you mean 1.3.x or 1.3.0? Just checking, sometimes it could make a difference.

If CUPS 1.3.x, then I would test that under a fresh native install of openSUSE 11.0 64-bits, with 1.3.7. I could upgrade CUPS on my main machine, from 1.2.12 to 1.3.7 as well, I'll see later on that. I could also test on a native v11.0 32-bits version no problem.

I am not in a hurry much cuz most of the time I spend on the printer I spend it on looking for the right PPD to take advantage of most of the MX700 functionalities, the mp600 and mp610 are not working and mp520 is very minimal support.

Anyway, I'm in any time to add the network functionality on that printer! :)

I appreciate the time and effort you put on that. I was not expecting it could be possible to "hack" a proprietary protocol, thumbs up!

Anybody else want to test on a different distro, if possible?
tnx

As the dependencies on the rest of CUPS are limited, it would be safe to to that I have the changes for 1.3.x (where x is 6 in my case as that is what the Fedora on my workstation/development machine uses).

Simple instructions:
1) get the source code for the version of CUPS running on your machine
2) unpack it
3) cd into the cups directory (as your normal userid)
4) ./configure
5) make
6) patch the source tree (instructions to follow once the patch file are made, hopefully some time this weekend)
7) cd backend
8) make bjnp
9) ./bjnp should return the printers uri assuming that you are on the same subnet, the printer is on, and there is no firewall blocking tcp/udp port 8611
10) if this works, copy (as root) bjnp into your /usr/lib(64?)/cups/backend
11) configure cups through the web frontend ([https://localhost:631](https://localhost:631))
12) report results
13) enjoy....

I would appreciate testing under the native cups versions for different platforms. therefore it is important to start of from the cups version that is installed on that platform

As said above, I plan to make patches for both the 1.2 and 1.3 trees. The will be based on my current pre-alpha status code that "works for me".

kind regards, Louis

---

### Post by llagendijk on 2008-05-09
[QUOTE=llagendijk;4917316]As the dependencies on the rest of CUPS are limited, it would be safe to to that I have the changes for 1.3.x (where x is 6 in my case as that is what the Fedora on my workstation/development machine uses).
/QUOTE]

Ok, for Cups-1.3.x users there is a diff file available on [http://www.fazant.net/cups](http://www.fazant.net/cups)
In this directory there is also a README that describes the installation process. Please report any results!

In the meanwhile I will try to backport the sources to cups-1.2, so people can test there too

happy testing, Louis

---

### Post by Tobe84 on 2008-05-10
wow - works great!

I'm using a the Canon MX700 under Kubuntu 8.04 with CUPS 1.3.7.
The printer is quite slower than under windows - but who cares!

Thanks a lot llagendijk! Great work!
If there is any bug I notice the next time I'll email you!

Greetings

---

### Post by KocaineKady on 2008-05-10
I like you tried many many drivers for my MX700 & Ubuntu . I finally got the Pixma mp180 to work. I hope this helps ya. Good Luck Kady

---

### Post by turingstest on 2008-05-20
> **llagendijk said:**
> 

Ok, for Cups-1.3.x users there is a diff file available on [http://www.fazant.net/cups](http://www.fazant.net/cups)
In this directory there is also a README that describes the installation process. Please report any results!

In the meanwhile I will try to backport the sources to cups-1.2, so people can test there too

happy testing, Louis

I've just compiled your bjnp patch against CUPS 1.3.7 - running on x86_64 gentoo, 2.6.24 kernel, printing to canon MP970 via ethernet. 
I've only run a couple of tests, but network printing works flawlessly so far. Or at least as well as non-network printing does ;) Excellent work, you should submit these patches to the folks over at cups.org. I'll let you know if I find any bugs.

---

### Post by AlanB66 on 2008-05-20
Just an update, since I believe I asked for support of Cups 1.2 ... I believe I have Cups 1.3.7 on my Ubuntu 8.04 system.

How do I determine for certain so you don't backport it just for me for v1.2?

Disregard this:
[COLOR="Gray"]Meanwhile, where's the follow-up to step #6 "patch the source tree"??[/COLOR]

---

### Post by AlanB66 on 2008-05-20
It all seems to work right, but the test pages and any attempts to print fail.

Here is ./bjnp ...
[INDENT]alanb@JAZZnSAX-LX:~/tmp/CUPS/cups-1.3.7/backend$ ./bjnp
set_debug_level: open - Permission deniedBJNP debug level = 14
Discover:
 00000000:42 4a 4e 50 01 01 00 00  00 01 00 00 00 00 00 00   BJNP.... ........


Select returned, time left 0.980000....
Discover response:
 00000000:42 4a 4e 50 81 01 00 00  00 01 00 00 00 00 00 10   BJNP.... ........
 00000010:00 01 08 00 06 04 00 00  85 c3 5f 07 c0 a8 01 de   ........ .._.....


Found printer at ip address: 192.168.1.222
Get printer identity
 00000000:42 4a 4e 50 01 30 00 00  00 02 00 00 00 00 00 00   BJNP.0.. ........


Sending UDP command to 192.168.1.222:8611
Printer identity:
 00000000:42 4a 4e 50 81 30 00 00  00 02 00 00 00 00 00 95   BJNP.0.. ........
 00000010:00 95 4d 46 47 3a 43 61  6e 6f 6e 3b 43 4d 44 3a   ..MFG:Ca non;CMD:
 00000020:42 4a 4c 2c 42 4a 52 61  73 74 65 72 33 2c 42 53   BJL,BJRa ster3,BS
 00000030:43 43 65 2c 4e 43 43 65  2c 50 4c 49 3b 53 4f 4a   CCe,NCCe ,PLI;SOJ
 00000040:3a 54 58 54 30 31 2c 42  4a 4e 50 32 3b 4d 44 4c   :TXT01,B JNP2;MDL
 00000050:3a 4d 58 37 30 30 20 73  65 72 69 65 73 3b 43 4c   :MX700.s eries;CL
 00000060:53 3a 50 52 49 4e 54 45  52 3b 44 45 53 3a 43 61   S:PRINTE R;DES:Ca
 00000070:6e 6f 6e 20 4d 58 37 30  30 20 73 65 72 69 65 73   non.MX70 0.series
 00000080:3b 56 45 52 3a 31 2e 30  35 30 3b 53 54 41 3a 31   ;VER:1.0 50;STA:1
 00000090:30 3b 48 52 49 3a 4f 54  48 3b 4d 53 49 3a 44 41   0;HRI:OT H;MSI:DA
 000000a0:54 2c 45 33 3b                                     T,E3;


Identity = MFG:Canon;CMD:BJL,BJRaster3,BSCCe,NCCe,PLI;SOJ:TXT01,BJNP2;MDL:MX700 series;CLS:PRINTER;DES:Canon MX700 series;VER:1.050;STA:10;HRI:OTH;MSI:DAT,E3;
Description = Canon MX700 series
printer discovery finished...
network bjnp://canon_mx700:0 "Canon MX700 series" "bjnp canon_mx700" "MFG:Canon;CMD:BJL,BJRaster3,BSCCe,NCCe,PLI;SOJ:TXT01,BJNP2;MDL:MX700 series;CLS:PRINTER;DES:Canon MX700 series;VER:1.050;STA:10;HRI:OTH;MSI:DAT,E3;"[/INDENT]

Here is the WebPage

[INDENT][IMG]http://www.fatmailman.com/ubuntu/CUPS.jpg[/IMG][/INDENT]


Using Ubuntu 8.04 - Cups 1.3.7 - Canon MX700 - TurboPrint PPD MP520

---

### Post by llagendijk on 2008-05-22
> **turingstest said:**
> I've just compiled your bjnp patch against CUPS 1.3.7 - running on x86_64 gentoo, 2.6.24 kernel, printing to canon MP970 via ethernet. 
I've only run a couple of tests, but network printing works flawlessly so far. Or at least as well as non-network printing does ;) Excellent work, you should submit these patches to the folks over at cups.org. I'll let you know if I find any bugs.

I already checked with them, but they think it is too much code to include it in CUPS. I will make it a separate project. The have indicated that they are willing to link to  a separate project. That is fine by me
Louis

---

### Post by llagendijk on 2008-05-22
> **AlanB66 said:**
> Just an update, since I believe I asked for support of Cups 1.2 ... I believe I have Cups 1.3.7 on my Ubuntu 8.04 system.

How do I determine for certain so you don't backport it just for me for v1.2?

Disregard this:
[COLOR="Gray"]Meanwhile, where's the follow-up to step #6 "patch the source tree"??[/COLOR]

Don't worry. I needed a port to 1.2 for my other machine. It is done (together with some patches for multi-homed support). I have not yet got around to release that stuff due to a short holiday. I will try to release it soon, but I may need some time due to a business trip next week
Louis

---

### Post by Frank64 on 2008-05-24
Finally got some time to test that. I am working on bugs for the next release of opensuse.

Well compiling 1.3.7 went fine, though not as mentioned. For some reason ./configure does not work, I had to do sh configure, I guess some kind of basic configuration on the system.

Detecting the printer worked. To my surprised it worked on first try. :)

Once it is configured in CUPS using the new bjnp protocol in the drop down menu, I cannot print a test page, it says it fails to run pstocanonij filter.

At first the filter was not found, it was not on the machine. So I copied the one from CUPS 1.2 but it says "/usr.../pstocanonij failed".

Do I still need to install the cnijfilter-common-2.80-1.i386.rpm filters to make it work?

EDIT: Ok now the pstocanonij filter thing is fine, I did nothing it did not want to install the rpm package anyway, weird.

Still, the jobs are sent to the printer, CUPS says they completed fine, but nothing prints. I don't know how to backtrace.

tnx

---

### Post by llagendijk on 2008-05-24
> **Frank64 said:**
> Finally got some time to test that. I am working on bugs for the next release of opensuse.

Well compiling 1.3.7 went fine, though not as mentioned. For some reason ./configure does not work, I had to do sh configure, I guess some kind of basic configuration on the system.

Detecting the printer worked. To my surprised it worked on first try. :)

Once it is configured in CUPS using the new bjnp protocol in the drop down menu, I cannot print a test page, it says it fails to run pstocanonij filter.

At first the filter was not found, it was not on the machine. So I copied the one from CUPS 1.2 but it says "/usr.../pstocanonij failed".

Do I still need to install the cnijfilter-common-2.80-1.i386.rpm filters to make it work?

EDIT: Ok now the pstocanonij filter thing is fine, I did nothing it did not want to install the rpm package anyway, weird.

Still, the jobs are sent to the printer, CUPS says they completed fine, but nothing prints. I don't know how to backtrace.

tnx

Well you still need a working filter. You might want to ensure that it works using USB before trying bjnp. Once that works modify the cups printer setup to use the bjnp protocol. That makes sure that the rest of the setup works. If that works, but the bjnp backend still fails, please send me your /var/log/cups/bjnpdebug file and I will have a look at it. That may take a week, as I am off on a business trip on Monday.

I can not see an obvious reason why ./configure would fail, this is indeed most likely a OS version specific issue

---

### Post by llagendijk on 2008-05-24
> **llagendijk said:**
> Don't worry. I needed a port to 1.2 for my other machine. It is done (together with some patches for multi-homed support). I have not yet got around to release that stuff due to a short holiday. I will try to release it soon, but I may need some time due to a business trip next week
Louis

I have now a new version available. Changes are limited, but this version works with both cups-1.2 and cups-1.3, without changes.
The only other changes are:
- a more standards compliant output if started wih no arguments to better support the detect new printer option in  the cups administration tab
- added support for multihomed hosts with more than one ehternet interface
- please note that cups-bjnp is now a single tar file that must be unpacked in the cups root directory

Tar and readme can be found under:
[http://www.fazant.net/cups](http://www.fazant.net/cups)

happy testing
/Louis

---

### Post by Frank64 on 2008-05-24
Oh yes, it sure is an OS specific issue, I get those little things with opensuse, like normal exec files which are in the path, well some of them I have to type the complete path, like /sbin/file. fdisk is an example. Anyway that does not matter cuz it's the OS. And it was working, but in another way.

I guess my filter is either corrupted or something else is wrong. When you ask to install an rpm and it says failed dependencies and you install them and you rerun the rpm and it says already installed, that's weird! :)

I should start off a new OS install. No worries cuz I ran this under vmware. And your compilation of cups and bjnp worked like a charm. I am 99% positive the problem is MY filter, not the bjnp.

I will give a try in cups 1.2 as well, of course this time I will install the filters and make it work under USB first. :)

It still is amazing you could built the compatibility with a proprietary protocol. :)

tnx, I'll let you know probably after your trip, though.

---

### Post by Frank64 on 2008-05-24
> **llagendijk said:**
> 
Tar and readme can be found under:
[http://www.fazant.net/cups](http://www.fazant.net/cups)


Just to let you know, one small typo in your readme:

"i8 ) type: make " should read "8 ) type: make " I have added a space after the ), cuz otherwise you would this emoticon 8)

:)

Louis, could this installation work by just compiling the bjnp tar source file? I just don't see the link between compiling cups and then the bjnp.

---

### Post by llagendijk on 2008-05-24
> **Frank64 said:**
> Just to let you know, one small typo in your readme:

"i8 ) type: make " should read "8 ) type: make " I have added a space after the ), cuz otherwise you would this emoticon 8)

:)

Louis, could this installation work by just compiling the bjnp tar source file? I just don't see the link between compiling cups and then the bjnp.

Thanks for the correction, I have updated the readme (replaced all closingbrackets bt dots)
The dependency is on ../cups/$(LIBCUPS, from which I need some stuff. I want to have a look at removing that dependency, but that might be tricky due to differences between cups-1.2 and 1.3
Louis

---

### Post by Frank64 on 2008-05-24
Oh ok and the stuff that you need is not there in the installed CUPS folder, I assume? Only in the installation folder of the compiled version? I am not familiar with all that compilation stuff, I just know the basics of it but what files remain where and when I have no idea.

For openSUSE and possibly other distros, I wonder if you (or anybody with its own favorite distro) could send the info to the developers of those distros so they can package a rpm or deb, depending on the distro. For me, they told me they support integrating the PPDs. If I find one working or if I build one and it works, I can send it to them and they will put the glue around to integrate it with their release version. When I'll make it work, if you don't want to bother contacting openSUSE (in my case), I could ask them if they can integrate it with their next release.

Also do you think this will work with the next versions of CUPS, 1.4, 1.5, 2.0, 3.0 (one day! :)), or some tweaks need to be done for every .x version? Maybe the developers of the distro supporting your bjnp, if any will, would know what to do when 1.5, 1.6 and so on will be released. I ask that cuz I am trying all I can to make sure this does not get lost somewhere, it's damn too important for that! :)

You must have excellent knowledge of cups and *nix to do what you've done. :)

---

### Post by llagendijk on 2008-05-30
> **Frank64 said:**
> Oh ok and the stuff that you need is not there in the installed CUPS folder, I assume? Only in the installation folder of the compiled version? I am not familiar with all that compilation stuff, I just know the basics of it but what files remain where and when I have no idea.

I still need to investigate further into what I really need. But this is for now more a proof of concept than a complete product. I just need more time to work on the code. Removing any unnecessary dependencies is part of that. But I also need to work on bi-dorectional support so that reading ink status will work for example. It looks as if linking to the installed libcups is sufficient indeed. So I may be able to remove the dependency on the cups source tree.
> **Frank64 said:**
> 
For openSUSE and possibly other distros, I wonder if you (or anybody with its own favorite distro) could send the info to the developers of those distros so they can package a rpm or deb, depending on the distro. For me, they told me they support integrating the PPDs. If I find one working or if I build one and it works, I can send it to them and they will put the glue around to integrate it with their release version. When I'll make it work, if you don't want to bother contacting openSUSE (in my case), I could ask them if they can integrate it with their next release.

I am myself using Fedora and Centos (RHEL clone). I am planning to create RPM's for that once I have a more complete product. Compiling that same RPM for Suse should then not be too hard. My aim is indeed to make cups-bjnp a separate package
I have not yet thought about a deb package.
> **Frank64 said:**
> 
Also do you think this will work with the next versions of CUPS, 1.4, 1.5, 2.0, 3.0 (one day! :)), or some tweaks need to be done for every .x version? Maybe the developers of the distro supporting your bjnp, if any will, would know what to do when 1.5, 1.6 and so on will be released. I ask that cuz I am trying all I can to make sure this does not get lost somewhere, it's damn too important for that! :)

I already had a look at the CUPS 1.4 code. It will need some more tweaking, but I will add support for that later. I just need time.....CUPS 1.4 adds some more interaction between the cups filters and the backend. I will add support for CUPS 1.4 once the rest of the sources are cleaned up.
> **Frank64 said:**
> 
You must have excellent knowledge of cups and *nix to do what you've done. :)
Not really. I did not know much about CUPS except for the parts I used so far. CUPS is however well structured so it was not hard to find out what to do. It was actually some 5 years ago that I wrote any code. 
But looking at some tcp/ip traces made it pretty obvious what needed to be done. The BJNP protocol is pretty simple and straight forward.
The most complicated part was the actual network code, but there is plenty of information on the internet. Ok, I pretty well know the basics of TCP/IP, that helped a lot

---

### Post by Frank64 on 2008-05-30
Me too I need some time to complete the tests. Things have been harder than expected on my other projects.

I am happy to see that you plan on building RPMs later on and offering support for later CUPS versions, looks quite promising!

One day having a RPM, reading ink, printing and scanning all that through the network, perfect! :)

I should be able to test more this w-e. Will be back as soon as I have more results.

tnx again for your work

---

### Post by Frank64 on 2008-05-31
> **llagendijk said:**
> I have now a new version available. Changes are limited, but this version works with both cups-1.2 and cups-1.3, without changes.
The only other changes are:
- a more standards compliant output if started wih no arguments to better support the detect new printer option in  the cups administration tab
- added support for multihomed hosts with more than one ehternet interface
- please note that cups-bjnp is now a single tar file that must be unpacked in the cups root directory

Tar and readme can be found under:
[http://www.fazant.net/cups](http://www.fazant.net/cups)

happy testing
/Louis

Louis, I can't make the make of bjnp anymore.

I followed 1 to 5 no problem.

1) get the source code for the specifc version of CUPS running on your machine
2) unpack it (tar xvzf cups-version>.tar.gz or tar xvjf cups-<version>.tar.bz2
3) cd into the cups directory (as your normal userid): cd cups-<version>
4) configure your source tree: ./configure
5) make binaries: make

But 6 to 8 don't work.

6. tar xvzf cups-bjnp<x.y.z>
7. cd bjnp 
8. type: make 

Where ever I unpack the bnjp sources, when I type MAKE it returns the following:

```
Makefile:18: ../Makedefs: No such file or directory
make: *** No rule to make target `../Makedefs'.  Stop.
```
I have tried unpacking with different options, moving files in different folders, I always get the same error.

Looking for the error on the web does not seem to return precise results.

I am now under cups 1.2.12 using your new install source. This one does not have the PATCH command anymore.

tnx

---

### Post by llagendijk on 2008-05-31
> **Frank64 said:**
> Louis, I can't make the make of bjnp anymore.

I followed 1 to 5 no problem.

1) get the source code for the specifc version of CUPS running on your machine
2) unpack it (tar xvzf cups-version>.tar.gz or tar xvjf cups-<version>.tar.bz2
3) cd into the cups directory (as your normal userid): cd cups-<version>
4) configure your source tree: ./configure
5) make binaries: make

But 6 to 8 don't work.

6. tar xvzf cups-bjnp<x.y.z>
7. cd bjnp 
8. type: make 

Where ever I unpack the bnjp sources, when I type MAKE it returns the following:

```
Makefile:18: ../Makedefs: No such file or directory
make: *** No rule to make target `../Makedefs'.  Stop.
```
I have tried unpacking with different options, moving files in different folders, I always get the same error.

Looking for the error on the web does not seem to return precise results.

I am now under cups 1.2.12 using your new install source. This one does not have the PATCH command anymore.

tnx
Please remember to unpack cups-bjnp WITHIN the cups root directory. It then unpacks to a bjnp directory in the cups tree. The Makedefs is made in step 4 IN THE cups-1.2.12 directory. bjnp being a subdirectory there allows the Makefile to use the Makedefs from the ./configure step. If this does not work, can you please mail me the outut from
ls -al
in the cups directory? It should look like:
[root@nest cups-1.2.12]# ls -al
total 1264
drwxr-xr-x  29 louis users   4096 May 24 21:51 .
drwxr-xr-x 173 louis users   8192 May 31 17:31 ..
drwxr-xr-x   2 louis users   4096 May 24 22:02 backend
drwxr-xr-x   2 louis users   4096 Jul 11  2007 berkeley
drwxr-xr-x   2 louis users   4096 May 24 23:21 bjnp
drwxr-xr-x   2 louis users   4096 Jul 11  2007 cgi-bin
-rw-r--r--   1 louis users   9210 Dec 29  2001 CHANGES-1.0.txt
-rw-r--r--   1 louis users 151005 Jan  3  2005 CHANGES-1.1.txt
-rw-r--r--   1 louis users  54208 Jul  9  2007 CHANGES.txt
drwxr-xr-x   2 louis users   4096 May  9 23:41 conf
-rw-r--r--   1 louis users   7460 May  9 23:41 config.h
-rw-r--r--   1 louis users   7043 Feb  6  2007 config.h.in
-rw-r--r--   1 louis users  81524 May  9 23:41 config.log
drwxr-xr-x   2 louis users   4096 Jul 11  2007 config-scripts
-rwxr-xr-x   1 louis users  36260 May  9 23:41 config.status
-rwxr-xr-x   1 louis users 480655 Jul 11  2007 configure
-rw-r--r--   1 louis users   2810 Dec  6  2006 configure.in
-rw-r--r--   1 louis users   2428 Feb  5  2007 CREDITS.txt
drwxr-xr-x   2 louis users   4096 May  9 23:49 cups
-rwxr-xr-x   1 louis users   3338 May  9 23:41 cups-config
-rwxr-xr-x   1 louis users   3437 Aug  3  2006 cups-config.in
drwxr-xr-x   2 louis users   4096 Jul 11  2007 data
drwxr-xr-x   2 louis users   4096 Jul 11  2007 desktop
drwxr-xr-x  13 louis users   4096 May  9 23:41 doc
drwxr-xr-x   2 louis users   4096 Jul 11  2007 driver
drwxr-xr-x   2 louis users   4096 Jul 11  2007 filter
drwxr-xr-x   2 louis users   4096 Jul 11  2007 fonts
drwxr-xr-x   2 louis users   4096 May  9 23:41 init
-rwxr-xr-x   1 louis users   5561 Dec 26  2001 install-sh
-rw-r--r--   1 louis users   5375 May  8  2007 INSTALL.txt
-rw-r--r--   1 louis users  48602 Jan  3  2007 LICENSE.txt
drwxr-xr-x   2 louis users   4096 Jul 11  2007 locale
-rw-r--r--   1 louis users   6495 May  9 23:41 Makedefs
-rw-r--r--   1 louis users   6662 Mar 12  2007 Makedefs.in
-rw-r--r--   1 louis users   9576 May  7  2007 Makefile
drwxr-xr-x   2 louis users   4096 May  9 23:41 man
drwxr-xr-x   2 louis users   4096 Jul 11  2007 monitor
drwxr-xr-x   2 louis users   4096 Jul 11  2007 notifier
drwxr-xr-x   2 louis users   4096 May  9 23:41 packaging
drwxr-xr-x   2 louis users   4096 Jul 11  2007 pdftops
drwxr-xr-x   2 louis users   4096 Jul 11  2007 ppd
-rw-r--r--   1 louis users   6896 May  8  2007 README.txt
drwxr-xr-x   2 louis users   4096 Jul 11  2007 scheduler
drwxr-xr-x   5 louis users   4096 Jul 11  2007 scripting
drwxr-xr-x   2 louis users   4096 Jul 11  2007 systemv
drwxr-xr-x  11 louis users   4096 May  9 23:41 templates
drwxr-xr-x   2 louis users   4096 Jul 11  2007 test
drwxr-xr-x   2 louis users   4096 Jul 11  2007 vcnet


Please note the Makedefs file and the bjnp directory in the listing

---

### Post by Frank64 on 2008-05-31
> **llagendijk said:**
> Please remember to unpack cups-bjnp WITHIN the cups root directory. It then unpacks to a bjnp directory in the cups tree. The Makedefs is made in step 4 IN THE cups-1.2.12 directory. bjnp being a subdirectory there allows the Makefile to use the Makedefs from the ./configure step. If this does not work, can you please mail me the outut from
ls -al
in the cups directory? It should look like:
[root@nest cups-1.2.12]# ls -al

[...]

Please note the Makedefs file and the bjnp directory in the listing

Well, according to the readme I have to unpack bjnp after compiling CUPS. Which is what I did, in the cups root (the one I am compiling, not the one installed on the machine).

Unpack cups, /configure it, make it, unpack bjnp, make it. That's what I followed.

I have the bjnp folder. I then cd into it and typed make.

Should I unpack the bjnp before doing ./configure for cups?

---

### Post by llagendijk on 2008-05-31
> **Frank64 said:**
> Well, according to the readme I have to unpack bjnp after compiling CUPS. Which is what I did, in the cups root (the one I am compiling, not the one installed on the machine).

Unpack cups, /configure it, make it, unpack bjnp, make it. That's what I followed.

I have the bjnp folder. I then cd into it and typed make.

Should I unpack the bjnp before doing ./configure for cups?
Well, if you did the ./configure in the cups root, the Makedep file should have been generated, strange.... as I said, please compare your directory listing of the cups source root directory with the one I posted. Is the Makedep file there?

---

### Post by Frank64 on 2008-05-31
IT WORKS!!!!!!!!!!!!! :)

Under CUPS 1.2.12 I confirm it works for printing! :)

Your README file is wrong though. I will paste it below with corrections, but before I want to explain to other users what causes the printing to be slow. It's simple, to print out a 153k 1 page OpenOffice Calc document it uploads 50megs through the network!! 50!!! That is a lot for 153k.

I have no idea why it works this way, maybe it's just not optimized yet?

Now for the README file, the cups-bjnp MUST be extracted in the root of cups BEFORE you do ./configure and make.

Here's the corrected file:
```
This is the BJNP protocol backend for CUPS
It currently supports both CUPS 1.2 and 1.3 in a single tar file!

Simple instructions:

The description assumes that all development packages required for cups compilation have already been installed
on your machine. If initial cups compilation fails, please check the result of step 4, as that may report missing 
dependencies!!!


1. get the source code for the specifc version of CUPS running on your machine
2. unpack cups (tar xvzf cups-version>.tar.gz or tar xvjf cups-<version>.tar.bz2
3. unpack cups-bjnp anywhere (tar xvzf cups-bjnp<x.y.z>)
4. copy the bjnp folder into the cups root folder you are compiling
5. cd into the cups directory (as your normal userid): cd cups-<version>
6. configure your source tree: ./configure
7. make binaries: make

If you got this far, we know for sure that cups compiles on your machine.
The bjnp driver depends on parts of cups, these have now been built

Now we install the bjnp sources (still wihin the cups source tree):

8. cd bjnp 
9. type: make 

If this works ok, you got a bjnp binary in the current directory
10. type: ./bjnp 

This should return the printers uri assuming that you are on the same subnet, 
the printer is on, and there is no firewall blocking tcp/udp port 8611

For my MP970 it returns:

[louis@travel backend]$ ./bjnp 
network bjnp://printer-1.pheasant:0 "Canon MP970 series" "bjnp printer-1.pheasant" "MFG:Canon;CMD:BJL,BJRaster3,BSCCe,NCCe,PLI;SOJ:TXT01,BJNP2;MDL:MP970 series;CLS:PRINTER;DES:Canon MP970 series;VER:1.110;STA:10;FSI:03;HRI:OTH;MSI:DAT,E3;"

11. if this works, install the binary, as root type:  make install.
    if you want to do this manually: copy (as root) bjnp into your /usr/lib/cups/backend
	this could possibly be the lib64 directory, but in my 64bit Fedora, it is the directory above

12. configure cups through the web frontend (https://localhost:631), e.g. try tab <administration> <find new printers>
13. report results
14. enjoy....

Louis Lagendijk
louis.lagendijk@gmail.com
```

---

### Post by imnuts on 2008-06-07
I got it working under Gentoo with cups 1.3.7 and also cnijfilter-2.80. The only complaint I have ATM is that network printing is really, really slow. It took about a minute to print out the test page, which seems like it is far to long. I don't print much, and the fact that it works is great, but it would also be nice if it printed faster. Thanks for the work though and for my working printer

---

### Post by llagendijk on 2008-06-10
> **imnuts said:**
> I got it working under Gentoo with cups 1.3.7 and also cnijfilter-2.80. The only complaint I have ATM is that network printing is really, really slow. It took about a minute to print out the test page, which seems like it is far to long. I don't print much, and the fact that it works is great, but it would also be nice if it printed faster. Thanks for the work though and for my working printer

I realized that printing is slow. I however need a significant amount of re-design to solve that. I am trying to think of a good way to do it. Right now cups-bjnp is designed with a synchronous communication towards the printer, I assume that a a-synchronous interface will work better, but I need to find a good design pattern that allows for it, while making sure that I do not overrun the printer buffer.I am pretty busy with real work, so it may take some time before I can implement this. I will announce an improved version once it is done.

---

### Post by AlanB66 on 2008-06-10
OK, I've got it all compiled, again, and I chose the following "driver" for my Canon MX700:

Canon PIXMA MP500 - CUPS+Gutenprint v5.0.2


I now - finally - get a page to come out with the print/print-test-page action. But, the page is BLANK!

I've tried the PPD from Turboprint - a modified MP520.ppd file - and that doesn't yield any results.

What is the proper driver to set for my Canon MX700 to work with this fix you've put in place?

Thanks!

---

### Post by AlanB66 on 2008-06-11
For what it's worth, I recently contacted Canon USA:
[INDENT]*[COLOR="Purple"]HP has a Multi-Function printer - J6480 - that offers Linux drivers.  A lot of people on the Ubuntu Forums are looking for a solution for the MX700 for Linux - currently to no avail.  Can you escalate this issue to have drivers worked on for the MX700 and Linux? Please??[/COLOR]*[/INDENT]

The responded as such:
[INDENT]*[COLOR="Purple"]We have forwarded your comments to Canon USA through our Customer Feedback process. This process allows us to capture important feedback from our valued customers. As we constantly strive to improve our products and services, your comments are vital to our continued success.[/COLOR]*[/INDENT]

So maybe Canon will light a fire under this issue now that HP is offering a wireless network multifunction that DOES support Linux.

---

### Post by imnuts on 2008-06-12
> **llagendijk said:**
> I realized that printing is slow. I however need a significant amount of re-design to solve that. I am trying to think of a good way to do it. Right now cups-bjnp is designed with a synchronous communication towards the printer, I assume that a a-synchronous interface will work better, but I need to find a good design pattern that allows for it, while making sure that I do not overrun the printer buffer.I am pretty busy with real work, so it may take some time before I can implement this. I will announce an improved version once it is done.

Just the fact that it works is good for me ATM just because I don't really print stuff all that often, and the fact that this is better than what I had before, which was a printer sitting on my desk that I couldn't use. Anything that you get done when you have time would be great as I can totally understand being busy with other stuff.

---

### Post by AdlerAlgreen on 2008-06-17
Two questions:

1.  I just bought this printer and tried the CUPS BJNP solution and so far it doesn't work.  But I did download the new Turboprint 2.0 beta and there is an MX700 driver that works beautifully.  The beta has the ability to access the printer via the network but I haven't gotten it to work yet.  I suspect that the problem is the printer port.  Anyone try this yet?

2.  I can't get the scanner to work at all.  I recompiled sane with the MP610 driver and it doesn't work.  I also tried vuescan and that doesn't work either.  Has anyone gotten the scanner to work in ubuntu?

btw, I am using Hardy Heron 8.04.

---

### Post by llagendijk on 2008-06-17
> **AdlerAlgreen said:**
> Two questions:

1.  I just bought this printer and tried the CUPS BJNP solution and so far it doesn't work.  

CUPS-BJNP only implements the canon proprietary network protocol. I am under the impression that turboprint does not do that. It offer printer drivers (called filters).

> **AdlerAlgreen said:**
> 
But I did download the new Turboprint 2.0 beta and there is an MX700 driver that works beautifully.  The beta has the ability to access the printer via the network but I haven't gotten it to work yet.  I suspect that the problem is the printer port.  Anyone try this yet?

See above. Try to print from Turboprint via USB first and then continue from there.

---

### Post by AdlerAlgreen on 2008-06-17
Turboprint 2.0 is printing to the MX700 from USB extremely well.  I just can't get the Network print to work yet.  I had a PixmaiP4200 hooked up to a network print server and it was very easy to use.  I just set the IP address and port 9100.  I may go back to that solution if the direct Canon Network port is so hard to use.

Anyone get the scanner to work yet under Ubuntu, in either USB or Network?

---

### Post by llagendijk on 2008-06-18
> **AdlerAlgreen said:**
> Turboprint 2.0 is printing to the MX700 from USB extremely well.  I just can't get the Network print to work yet.  I had a PixmaiP4200 hooked up to a network print server and it was very easy to use.  I just set the IP address and port 9100.  I may go back to that solution if the direct Canon Network port is so hard to use.


But what did you try? If bjnp is installed in your backend directory (probably /usr/lib/cups/backend) and your firewall is switched off, your printer should show up under the adminitration tab of cups when do scan for new printers. Did you try to run the bjnp command after compilation as per the instructions? Did it show the printer?
bjnp is not really ready so it may have rough edges. I need a more detailed fault reports to help you

---

### Post by AlanB66 on 2008-06-18
> **llagendijk said:**
> But what did you try? If bjnp is installed in your backend directory (probably /usr/lib/cups/backend) and your firewall is switched off, your printer should show up under the adminitration tab of cups when do scan for new printers. Did you try to run the bjnp command after compilation as per the instructions? Did it show the printer?
bjnp is not really ready so it may have rough edges. I need a more detailed fault reports to help you

I tried the same to no avail. I set the printer up in the CUPS web interface and when I try to print a test page, nothing ever comes out of the printer.

---

### Post by AdlerAlgreen on 2008-06-18
I sent the following note to TurboPrint:

>I've been a Turboprint fan for a year and I'm really pleased with what
>you have done with the product in version 2.0.

>I just bought a Canon MX700 and Turboprint 2.0 support is terrific under
>USB.  I notice you have also included network support in the product.
>Canon uses a proprietary network interface on the MX700.  Will Turboprint
>support that too so that uses like me can use the network interface and
>print from any computer?
>Looking forward to hearing from you,

And this was their response: 

hank you for your inquiry!

There is currently no direct support for Canon's proprietary network interface within TurboPrint - we hope to have a solution soon.

There is an entry in our support forum that looks promising:

"As I have not been able to find a solution on the internet, I have started development of a backend for CUPS that talks bjnp. I have a working demo available. I will post source code in a while. On [http://fazant.net/cups](http://fazant.net/cups) you can find a very first version. It does require the cups source code, as it must be built within the cups source tree."

I guess in this case all roads lead to the same source...

---

### Post by pcarphanatik on 2008-07-02
Legendary work! The 1.3 version of the bjnp protocol works great for me as well. My MX700 is printing via network! Just to make it clear...you do need to download and install BOTH:

cnijfilter-common_2.80-1_i386.deb
cnijfilter-mp520series_2.80-1_i386.deb

If your platform is AMD64 (like me) just force architecture.

I had one odd issue...bjnp was communicating and I could print, however the same jobs would print over and over; this happened because I did not compile bjnp within the cups dirctory.  So just make sure you place the bjnp directory within the cups directory (the one you configured) and all will go smoothly.

---

### Post by llagendijk on 2008-07-02
> **pcarphanatik said:**
> Legendary work! The 1.3 version of the bjnp protocol works great for me as well. My MX700 is printing via network! Just to make it clear...you do need to download and install BOTH:

cnijfilter-common_2.80-1_i386.deb
cnijfilter-mp520series_2.80-1_i386.deb

If your platform is AMD64 (like me) just force architecture.

I had one odd issue...bjnp was communicating and I could print, however the same jobs would print over and over; this happened because I did not compile bjnp within the cups dirctory.  So just make sure you place the bjnp directory within the cups directory (the one you configured) and all will go smoothly.

Instead of using cnijfilter, you could also use turboprint (the commercial software). This is what I have to use with my MP970 (with the IP6700 drivers). Works well. Turboprint will possibly support ink level status in the short term as well

---

### Post by AndrewRodaway on 2008-07-02
A bit late, but I have just successfully printed via WLAN to my Canon Pixma iP5200r. I just installed it first as a USB printer using the CUPS+Gutenprint v 5.0.2 driver and did a test print OK. Then made a copy of the printer and changed the device URI in the settings dialog to socket://192.168.1.101 which I know to be the IP address of the wireless interface and it just worked... (yes, I did pull out the USB cable first...)

a.

---

### Post by AlanB66 on 2008-07-02
pcarphanatik,

Thank You! It was the MP520 pkg that I was missing and now I can print over the network.

Thank You, again.:guitar:
And Thank YOU llagendijk!!

> **pcarphanatik said:**
> Legendary work! The 1.3 version of the bjnp protocol works great for me as well. My MX700 is printing via network! Just to make it clear...you do need to download and install BOTH:

cnijfilter-common_2.80-1_i386.deb
cnijfilter-mp520series_2.80-1_i386.deb

If your platform is AMD64 (like me) just force architecture.

I had one odd issue...bjnp was communicating and I could print, however the same jobs would print over and over; this happened because I did not compile bjnp within the cups dirctory.  So just make sure you place the bjnp directory within the cups directory (the one you configured) and all will go smoothly.

---

### Post by ThyMaster on 2008-07-11
Kudos also from me!

All I have to "complain" about is that Cups stops the printer after every printout.
I'm using Turboprint 2.0 and Cups 1.2.7 (SusSE 10.2). The current workaround is to tell the driver/Turboprint not to stop the printer after failure but to abort/delete the to-be-printed document (which is no problem since it was printed fine already!).

Cups itself states a /usr/lib/cups/backen/bjnp failure

Seems Cups expects the printer to give a status on finishing the print job which seems not to be support by bjnp (yet).
Any chance this will be implemented/fixed?

Regards
ThyMaster

---

### Post by llagendijk on 2008-07-12
> **ThyMaster said:**
> Kudos also from me!

All I have to "complain" about is that Cups stops the printer after every printout.
I'm using Turboprint 2.0 and Cups 1.2.7 (SusSE 10.2). The current workaround is to tell the driver/Turboprint not to stop the printer after failure but to abort/delete the to-be-printed document (which is no problem since it was printed fine already!).

Cups itself states a /usr/lib/cups/backen/bjnp failure

Seems Cups expects the printer to give a status on finishing the print job which seems not to be support by bjnp (yet).
Any chance this will be implemented/fixed?

Regards
ThyMaster
This should work, but there must be something in your configuration that causes this. Can you please upload the /var/log/cups/bjnpdebug file, or even better the last 100 lines?

---

### Post by ThyMaster on 2008-07-13
Thanks for the quick answer.
Here's the result:
```
032.689 bjnp_write2: print response received after 0.004000 seconds
032.689 Print response:
032.689  00000000:42 4a 4e 50 81 21 00 00  24 5d 00 03 00 00 00 04   BJNP.!.. $]......
032.689  00000010:00 00 08 00                                        ....
032.689 

032.689 bjnp_write: Printed 2048 bytes
032.689 bjnp_write: starting printing of 1961 characters
032.689 bjnp_write: Print remaining 1961 bytes
032.689 bjnp_write2: printing 1961 bytes
032.689 Print data:
032.689  00000000:42 4a 4e 50 01 21 00 00  24 5e 00 03 00 00 07 a9   BJNP.!.. $^......
032.689  00000010:01 0e e0 f9 00 00 e8 f9  00 00 0e f9 00 01 02 e0   ........ ........
032.689  00000020:f9 00 00 6c f9 00 01 0e  80 f9 00 00 e0 f9 00 00   ...l.... ........
032.689  00000030:2e f9 00 01 0e e0 f9 00  00 e8 f9 00 00 0e f9 00   ........ ........
032.689  00000040:01 02 e0 f9 00 00 6c f9  00 01 0e 80 f9 00 00 e0   ......l. ........
032.689  00000050:f9 00 00 2e f9 00 01 0e  e0 f9 00 00 e8 f9 00 00   ........ ........
032.689  00000060:0e f9 00 01 02 e0 f9 00  00 6c f9 00 01 0e 80 f9   ........ .l......
032.689  00000070:00 00 e0 fd 00 04 0e ee  ee e8 2e f9 00 04 0e e0   ........ ........
032.689  00000080:00 00 02 fb ee 80 ff ff  00 80 fc 00 00 1f f9 00   ........ ........
032.689  00000090:01 03 e0 f9 00 00 7c f9  00 01 0f 80 fa 00 01 01   ......|. ........
032.689  000000a0:f0 f9 00 00 3e f9 00 01  1f f0 f9 00 00 f8 f9 00   ....>... ........
032.689  000000b0:00 1f f9 00 01 03 e0 f9  00 00 7c f9 00 01 0f 80   ........ ..|.....
032.689  000000c0:fa 00 01 01 f0 f9 00 00  3e f9 00 01 1f f0 f9 00   ........ >.......
032.689  000000d0:00 f8 f9 00 00 1f f9 00  01 03 e0 f9 00 00 7c f9   ........ ......|.
032.689  000000e0:00 01 0f 80 fa 00 01 01  f0 f9 00 00 3e f9 00 01   ........ ....>...
032.689  000000f0:1f f0 f9 00 00 f8 f9 00  00 1f f9 00 01 03 e0 f9   ........ ........
032.689  00000100:00 00 7c f9 00 01 0f 80  fa 00 01 01 f0 f9 00 00   ..|..... ........
032.689  00000110:3e f9 00 01 1f f0 f9 00  00 f8 f9 00 00 1f f9 00   >....... ........
032.689  00000120:01 03 e0 f9 00 00 7c f9  00 01 0f 80 fa 00 01 01   ......|. ........
032.689  00000130:f0 f9 00 00 3e f9 00 01  1f f0 f9 00 00 f8 f9 00   ....>... ........
032.689  00000140:00 1f f9 00 01 03 e0 f9  00 00 7c f9 00 01 0f 80   ........ ..|.....
032.689  00000150:fa 00 01 01 f0 f9 00 00  3e f9 00 01 1f f0 f9 00   ........ >.......
032.689  00000160:00 f8 f9 00 00 1f f9 00  01 03 e0 f9 00 00 7c f9   ........ ......|.
032.689  00000170:00 01 0f 80 fa 00 01 01  f0 f9 00 00 3e f9 00 01   ........ ....>...
032.689  00000180:1f f0 f9 00 00 f8 f9 00  00 1f f9 00 01 03 e0 f9   ........ ........
032.689  00000190:00 00 7c f9 00 01 0f 80  fa 00 01 01 f0 f9 00 00   ..|..... ........
032.689  000001a0:3e f9 00 04 1f f0 00 00  03 fb ff 80 ff bb 00 80   >....... ........
032.689  000001b0:fc 00 00 1b f9 00 01 03  a0 f9 00 00 38 f9 00 01   ........ ....8...
032.689  000001c0:0b 80 fa 00 01 01 b0 f9  00 00 3a f9 00 01 1b b0   ........ ..:.....
032.689  000001d0:f9 00 00 b8 f9 00 00 1b  f9 00 01 03 a0 f9 00 00   ........ ........
032.689  000001e0:38 f9 00 01 0b 80 fa 00  01 01 b0 f9 00 00 3a f9   8....... ......:.
032.689  000001f0:00 01 1b b0 f9 00 00 b8  f9 00 00 1b f9 00 01 03   ........ ........
032.689  00000200:a0 f9 00 00 38 f9 00 01  0b 80 fa 00 01 01 b0 f9   ....8... ........
032.689  00000210:00 00 3a f9 00 01 1b b0  f9 00 00 b8 f9 00 00 1b   ..:..... ........
032.689  00000220:f9 00 01 03 a0 f9 00 00  38 f9 00 01 0b 80 fa 00   ........ 8.......
032.689  00000230:01 01 b0 f9 00 00 3a f9  00 01 1b b0 f9 00 00 b8   ......:. ........
032.689  00000240:f9 00 00 1b f9 00 01 03  a0 f9 00 00 38 f9 00 01   ........ ....8...
032.689  00000250:0b 80 fa 00 01 01 b0 f9  00 00 3a f9 00 01 1b b0   ........ ..:.....
032.689  00000260:f9 00 00 b8 f9 00 00 1b  f9 00 01 03 a0 f9 00 00   ........ ........
032.689  00000270:38 f9 00 01 0b 80 fa 00  01 01 b0 f9 00 00 3a f9   8....... ......:.
032.689  00000280:00 01 1b b0 f9 00 00 b8  f9 00 00 1b f9 00 01 03   ........ ........
032.689  00000290:a0 f9 00 00 38 f9 00 01  0b 80 fa 00 01 01 b0 f9   ....8... ........
032.689  000002a0:00 00 3a f9 00 01 1b b0  f9 00 00 b8 f9 00 00 1b   ..:..... ........
032.689  000002b0:f9 00 01 03 a0 f9 00 00  38 f9 00 01 0b 80 fa 00   ........ 8.......
032.689  000002c0:01 01 b0 f9 00 00 3a f9  00 04 1b b0 00 00 03 fb   ......:. ........
032.689  000002d0:bb 80 ff ff 00 80 fc 00  00 1f f9 00 01 03 e0 f9   ........ ........
032.689  000002e0:00 00 7c f9 00 01 0f 80  fa 00 01 01 f0 f9 00 00   ..|..... ........
032.689  000002f0:3e f9 00 01 1f f0 f9 00  00 f8 f9 00 00 1f f9 00   >....... ........
032.689  00000300:01 03 e0 f9 00 00 7c f9  00 01 0f 80 fa 00 01 01   ......|. ........
032.689  00000310:f0 f9 00 00 3e f9 00 01  1f f0 f9 00 00 f8 f9 00   ....>... ........
032.689  00000320:00 1f f9 00 01 03 e0 f9  00 00 7c f9 00 01 0f 80   ........ ..|.....
032.689  00000330:fa 00 01 01 f0 f9 00 00  3e f9 00 01 1f f0 f9 00   ........ >.......
032.689  00000340:00 f8 f9 00 00 1f f9 00  01 03 e0 f9 00 00 7c f9   ........ ......|.
032.689  00000350:00 01 0f 80 fa 00 01 01  f0 f9 00 00 3e f9 00 01   ........ ....>...
032.689  00000360:1f f0 f9 00 00 f8 f9 00  00 1f f9 00 01 03 e0 f9   ........ ........
032.689  00000370:00 00 7c f9 00 01 0f 80  fa 00 01 01 f0 f9 00 00   ..|..... ........
032.689  00000380:3e f9 00 01 1f f0 f9 00  00 f8 f9 00 00 1f f9 00   >....... ........
032.689  00000390:01 03 e0 f9 00 00 7c f9  00 01 0f 80 fa 00 01 01   ......|. ........
032.689  000003a0:f0 f9 00 00 3e f9 00 01  1f f0 f9 00 00 f8 f9 00   ....>... ........
032.689  000003b0:00 1f f9 00 01 03 e0 f9  00 00 7c f9 00 01 0f 80   ........ ..|.....
032.689  000003c0:fa 00 01 01 f0 f9 00 00  3e f9 00 01 1f f0 f9 00   ........ >.......
032.689  000003d0:00 f8 f9 00 00 1f f9 00  01 03 e0 f9 00 00 7c f9   ........ ......|.
032.689  000003e0:00 01 0f 80 fa 00 01 01  f0 f9 00 00 3e f9 00 01   ........ ....>...
032.689  000003f0:1f f0 fb 00 02 01 ff ff  80 ff ee 00 80 fc 00 00   ........ ........
032.689  00000400:0e f9 00 01 02 e0 f9 00  00 6c f9 00 01 0e 80 f9   ........ .l......
032.689  00000410:00 00 e0 f9 00 00 2e f9  00 01 0e e0 f9 00 00 e8   ........ ........
032.689  00000420:f9 00 00 0e f9 00 01 02  e0 f9 00 00 6c f9 00 01   ........ ....l...
032.689  00000430:0e 80 f9 00 00 e0 f9 00  00 2e f9 00 01 0e e0 f9   ........ ........
032.689  00000440:00 00 e8 f9 00 00 0e f9  00 01 02 e0 f9 00 00 6c   ........ .......l
032.689  00000450:f9 00 01 0e 80 f9 00 00  e0 f9 00 00 2e f9 00 01   ........ ........
032.689  00000460:0e e0 f9 00 00 e8 f9 00  00 0e f9 00 01 02 e0 f9   ........ ........
032.689  00000470:00 00 6c f9 00 01 0e 80  f9 00 00 e0 f9 00 00 2e   ..l..... ........
032.689  00000480:f9 00 01 0e e0 f9 00 00  e8 f9 00 00 0e f9 00 01   ........ ........
032.689  00000490:02 e0 f9 00 00 6c f9 00  01 0e 80 f9 00 00 e0 f9   .....l.. ........
032.689  000004a0:00 00 2e f9 00 01 0e e0  f9 00 00 e8 f9 00 00 0e   ........ ........
032.689  000004b0:f9 00 01 02 e0 f9 00 00  6c f9 00 01 0e 80 f9 00   ........ l.......
032.689  000004c0:00 e0 f9 00 00 2e f9 00  01 0e e0 f9 00 00 e8 f9   ........ ........
032.689  000004d0:00 00 0e f9 00 01 02 e0  f9 00 00 6c f9 00 01 0e   ........ ...l....
032.689  000004e0:80 f9 00 00 e0 f9 00 00  2e f9 00 01 0e e0 f9 00   ........ ........
032.689  000004f0:00 e8 f9 00 00 0e f9 00  01 02 e0 f9 00 00 6c f9   ........ ......l.
032.689  00000500:00 01 0e 80 f9 00 00 e0  f9 00 00 2e f9 00 01 0e   ........ ........
032.689  00000510:e0 fa 00 ff ee 80 1b 28  46 08 00 80 80 80 80 80   .......( F.......
032.689  00000520:80 80 80 1b 28 46 08 00  80 80 80 80 80 80 80 80   ....(F.. ........
032.689  00000530:1b 28 46 08 00 80 80 80  80 80 80 80 80 1b 28 46   .(F..... ......(F
032.689  00000540:74 01 ff ff 00 80 fc 00  00 1f f9 00 01 03 e0 f9   t....... ........
032.689  00000550:00 00 7c f9 00 01 0f 80  fa 00 01 01 f0 f9 00 00   ..|..... ........
032.689  00000560:3e f9 00 01 1f f0 f9 00  00 f8 f9 00 00 1f f9 00   >....... ........
032.689  00000570:01 03 e0 f9 00 00 7c f9  00 01 0f 80 fa 00 01 01   ......|. ........
032.689  00000580:f0 f9 00 00 3e f9 00 01  1f f0 f9 00 00 f8 f9 00   ....>... ........
032.689  00000590:00 1f f9 00 01 03 e0 f9  00 00 7c f9 00 01 0f 80   ........ ..|.....
032.689  000005a0:fa 00 01 01 f0 f9 00 00  3e f9 00 01 1f f0 f9 00   ........ >.......
032.689  000005b0:00 f8 f9 00 00 1f f9 00  01 03 e0 f9 00 00 7c f9   ........ ......|.
032.689  000005c0:00 01 0f 80 fa 00 01 01  f0 f9 00 00 3e f9 00 01   ........ ....>...
032.689  000005d0:1f f0 f9 00 00 f8 f9 00  00 1f f9 00 01 03 e0 f9   ........ ........
032.689  000005e0:00 00 7c f9 00 01 0f 80  fa 00 01 01 f0 f9 00 00   ..|..... ........
032.689  000005f0:3e f9 00 01 1f f0 f9 00  00 f8 f9 00 00 1f f9 00   >....... ........
032.689  00000600:01 03 e0 f9 00 00 7c f9  00 01 0f 80 fa 00 01 01   ......|. ........
032.689  00000610:f0 f9 00 00 3e f9 00 01  1f f0 f9 00 00 f8 f9 00   ....>... ........
032.689  00000620:00 1f f9 00 01 03 e0 f9  00 00 7c f9 00 01 0f 80   ........ ..|.....
032.689  00000630:fa 00 01 01 f0 f9 00 00  3e f9 00 01 1f f0 f9 00   ........ >.......
032.689  00000640:00 f8 f9 00 00 1f f9 00  01 03 e0 f9 00 00 7c f9   ........ ......|.
032.689  00000650:00 01 0f 80 fa 00 01 01  f0 f9 00 00 3e f9 00 01   ........ ....>...
032.689  00000660:1f f0 fb 00 02 01 ff ff  80 81 bb 81 bb 81 bb 81   ........ ........
032.689  00000670:bb a9 bb 80 81 ff 81 ff  81 ff 81 ff a9 ff 80 81   ........ ........
032.689  00000680:ee 81 ee 81 ee 81 ee a9  ee 80 81 ff 81 ff 81 ff   ........ ........
032.689  00000690:81 ff a9 ff 80 81 bb 81  bb 81 bb 81 bb a9 bb 80   ........ ........
032.689  000006a0:81 ff 81 ff 81 ff 81 ff  a9 ff 80 81 ee 81 ee 81   ........ ........
032.689  000006b0:ee 81 ee a9 ee 80 1b 28  46 08 00 80 80 80 80 80   .......( F.......
032.689  000006c0:80 80 80 1b 28 46 08 00  80 80 80 80 80 80 80 80   ....(F.. ........
032.689  000006d0:1b 28 46 08 00 80 80 80  80 80 80 80 80 1b 28 46   .(F..... ......(F
032.689  000006e0:58 00 81 ff 81 ff 81 ff  81 ff a9 ff 80 81 bb 81   X....... ........
032.689  000006f0:bb 81 bb 81 bb a9 bb 80  81 ff 81 ff 81 ff 81 ff   ........ ........
032.689  00000700:a9 ff 80 81 ee 81 ee 81  ee 81 ee a9 ee 80 81 ff   ........ ........
032.689  00000710:81 ff 81 ff 81 ff a9 ff  80 81 bb 81 bb 81 bb 81   ........ ........
032.689  00000720:bb a9 bb 80 81 ff 81 ff  81 ff 81 ff a9 ff 80 81   ........ ........
032.689  00000730:ee 81 ee 81 ee 81 ee a9  ee 80 1b 28 46 08 00 80   ........ ...(F...
032.689  00000740:80 80 80 80 80 80 80 1b  28 46 08 00 80 80 80 80   ........ (F......
032.689  00000750:80 80 80 80 1b 28 46 08  00 80 80 80 80 80 80 80   .....(F. ........
032.689  00000760:80 1b 28 46 1c 00 81 ff  81 ff 81 ff 81 ff a9 ff   ..(F.... ........
032.689  00000770:80 81 bb 81 bb 81 bb 81  bb a9 bb 80 80 80 80 80   ........ ........
032.689  00000780:80 80 1b 28 46 08 00 80  80 80 80 80 80 80 80 1b   ...(F... ........
032.689  00000790:28 46 08 00 80 80 80 80  80 80 80 80 1b 28 46 08   (F...... .....(F.
032.689  000007a0:00 80 80 80 80 80 80 80  80 1b 28 65 02 00 00 01   ........ ..(e....
032.689  000007b0:0c 1b 28 62 01 00 00 1b  40                        ..(b.... @
032.689 

032.692 bjnp_write2: print response received after 0.004000 seconds
032.692 Print response:
032.692  00000000:42 4a 4e 50 81 21 00 00  24 5e 00 03 00 00 00 04   BJNP.!.. $^......
032.692  00000010:00 00 07 a9                                        ....
032.692 

032.692 bjnp_write: Printed 1961 bytes
035.709 Finish printjob
035.709  00000000:42 4a 4e 50 01 10 00 00  24 5f 00 03 00 00 00 10   BJNP.... $_......
035.709 

035.709 Sending UDP command to 192.168.1.10:53943
035.709 udp_command: connect - Address family not supported by protocol

```
Regards
ThyMaster

---

### Post by enieffak on 2008-07-13
Thank you - now my MX700 printer works via LAN with amd64-Ubuntu.
First I installed "cnijfilter-common_2.80-1_i386.deb" and "cnijfilter-mp520series_2.80-1_i386.deb" and ensured that the printer works via USB (with the help of canonmx700.ppd).
Then I followed the steps of your readme (the part with unpacking "cups-bjnp-0.0.1.tar.gz" was a bit confusing, because it unpacked the bjnp-directory to "cups-1.3.7/home/home1/louis/" instead of "cups-1.3.7/". Simply swifting the bjnp-directory to the right place was the solution.) The printer was recognized at the first go and works good with the canonmx700.ppd-File. The printing speed is slow, but the quality is good.
Thank you!

---

### Post by chrisolof on 2008-07-14
So I'm looking for a bit of clarification on simple USB-connected printing.  I've got the MX700 hooked up to my stepfather's laptop (running Hardy) via USB and printing successfully using TurboPrint.  Is there a way of doing this *without using TurboPrint*?

Ideally I'd love to have him printing via the LAN (and it looks like other posters are progressing towards that goal), but for now simple USB printing would suffice - just would really like to avoid paying TurboPrint after the 30-day trial.

---

### Post by llagendijk on 2008-07-15
> **ThyMaster said:**
> Thanks for the quick answer.
Here's the result:


035.709 Sending UDP command to 192.168.1.10:53943
035.709 udp_command: connect - Address family not supported by protocol
[/CODE]
Regards
ThyMaster
This part looks funny. Something is messing up the address (http_addr_t *addr) that the close command is sent to. 
I have made quite a few changes to the code base that I plan to release as soon as I have some time (probably after my holiday in two weeks time. So debugging this now is not very useful. To work around the bug you can add a return on line 728 of bjnp-io.c. This will skip the close command, but this should no hurt too much for now. It for now avoids the automatic stopping of the printer. Ugly, but it should work

---

### Post by enieffak on 2008-07-15
> **chrisolof said:**
> Is there a way of doing this *without using TurboPrint*?


Of course. Read the second sentence of my last posting :-D.

---

### Post by chrisolof on 2008-07-16
> First I installed "cnijfilter-common_2.80-1_i386.deb" and "cnijfilter-mp520series_2.80-1_i386.deb" and ensured that the printer works via USB (with the help of canonmx700.ppd).

Thanks enieffak - I'll see if I can get that working tomorrow.  Just as a note for future readers who want to try the above quoted method for getting the MX700 working *without* using the crutch of TurboPrint, here are the locations of the files mentioned above:

**cnijfilter-common_2.80-1_i386.deb**
[http://support-au.canon.com.au/contents/AU/EN/0100083403.html]("http://support-au.canon.com.au/contents/AU/EN/0100083403.html")

**cnijfilter-mp520series_2.80-1_i386.deb**
[http://support-au.canon.com.au/contents/AU/EN/0100083901.html]("http://support-au.canon.com.au/contents/AU/EN/0100083901.html")

**canonmx700.ppd** (remove the .txt ending when saving)
[http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424]("http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424")

---

### Post by ThyMaster on 2008-07-16
> **llagendijk said:**
> This part looks funny. Something is messing up the address (http_addr_t *addr) that the close command is sent to. 
I have made quite a few changes to the code base that I plan to release as soon as I have some time (probably after my holiday in two weeks time. So debugging this now is not very useful. To work around the bug you can add a return on line 728 of bjnp-io.c. This will skip the close command, but this should no hurt too much for now. It for now avoids the automatic stopping of the printer. Ugly, but it should work

Thanks for your answer, but how that should look like?
```
{
   strncpy(device_id, cur_printer_IEEE1284_id, device_id_size);
   device_id[device_id_size] = '\0';

   strncpy(make_model, cur_printer_model, make_model_size);
   make_model[make_model_size] = '\0';
   if ( (strlen(make_model) == 0) && (strlen(device_id) == 0))
        return -1;
   return 0;
}
[COLOR="Red"]return[/COLOR]
```The above won't work when trying to compile. Sorry, but I'm not a developer...

- ThyMaster

---

