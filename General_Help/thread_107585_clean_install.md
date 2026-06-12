---
title: "clean install"
date: 2005-12-23
forum: General Help
---

### Post by 504harry on 2005-12-23
Hi there, I've run Ubuntu504 for a while OK then 510 turned up (great News), so rather than risk getting confused, I started again formatting the HDD into three partitions: 61,G 61G plus another as swap (total presumably 130G although I thought it was a 120G drive...let's overlook this) The HDD contains only Ubuntu 510 - there is no Win partition.
/
I chose three partitions to make installation easier (I read somewhere)...
/
The installation and formatting was done with assistance by someone who understands far more than I....however, the pc was stand-alone - other than keyboard/mouse......so the internet and LPT1-printer were missing.
/
Now, When I log-on  It behaves much as 504, although the screen is darker so I cannot read the endless files - one is in red ( something like "synchronisation - - -"  =fail)  but I can't be certain and don't know what it means - it's about 2/3 the way through the boot sequence.
/
After it gets my details it says: Gnome is missing Ubuntu internet address...and suggests I add it to file/etc/hosts....then gives me the option of try again or log-in anyway. (only this option produces a result)...when logged-in I cannot use the internet, even though it's connected (that's how I'm writing this, using a different HDD/ OS, although it's the same pc hardware.....
Not nly that but I cannot find this file/etc/hosts although once I did and it was a "Read-only file" so I couldn't add "Ubuntu" to it, although cusriously the file already says "Ubuntu" - however, I wonder why if Gnome needs it for the web it isn't [www.Ubuntu.com](www.Ubuntu.com) (rather than plain Ubuntu)
/
As a secondary problem I need to set-up my printer under OpenOffice and this appears to be impossible also....but getting the thing to address the internet would help.
I'm not too concerned with emails as I can use Win/OE5 on another HDD set-up and also "Webmail" gives me the same access - if I can get onto the web......
So there we have it - - - just how do I get my settings into Ubuntu510 and why doesn't it detect them each session, even if I didn't have the connection when I installed?
/
Thanks etc......I have spent about 6 hours fiddling and looking but it really has me beat.......I'm tempted to reload the lot, -but don't relish the hour it takes - and the partitioning was somewhat difficult to understand.
Harry

---

### Post by 504harry on 2005-12-25
ADDITIONAL  Info.
I have been searching for info on this "/etc/hosts " (issue, & see earlier post) and I'm wondering if I need to be root to alter the file - curiously it doesn't ask - and I am at a loss as to know what form the "ubuntu" entry should take anyway.
My latest info source is a 2-yr old "Dummies"-series book on RedHat v8.(oops, sorry).....under "Gnome" it mentions the use of these "/etc/host" (series of ) files ....but annoyingly doesn't suggest how they are updated, or tested....again it is curious the entries they show do not contain "RedHat" (ie the "Ubuntu" equivalent, I would expect)....all very curious ...... 
/
However, I have tried to connect to the internet, altered settings, this and that, etc but still no result........I find my 510 system is very confusing, because it has installed so many options that won't apply to my requirements -
/
I hope to install Java in Firefox (to view certain web-pages I need), but it seems I can't log-in anywhere. Maybe get my printer to work...
/
Regards
Happy New Year (soon)

---

### Post by zoiks on 2005-12-25
It sounds like you have a couple of issues.

1) Looks like your network isn't set up.  When you boot up, go to the menu item System|Administration|Networking.  You should have an ethernet card listed.  Activate this card and in "Properties" make sure it's enabled and has "DHCP" for configuration.  I think you should be good to go once you've done this.  The blurb about synchronization is probably the ntp service starting up, complaining cuz it can't find the server.  It'll work fine when your network's set up properly.  I think you can also ignore the /etc/hosts messages.

2) You can add a printer within gnome by going to System|Administration|Printing.

---

### Post by Sef on 2005-12-26
What type of printer do you have? 

 Some can just be plugged in to work fine; some need some downloads to work fine; some only work partially; and some won't work at all.

---

### Post by 504harry on 2005-12-27
[QUOTE=Sef]What type of printer do you have? 

 Some can just be plugged in to work fine; some need some downloads to work fine; some only work partially; and some won't work at all.[/QUOTE]
Hi, thaks for the interest,  + Zoiks - I'll look for that network card - can't say I had found it, I believe it is a "Netgear10/100" will look into it.

Printer is Lexamrk z51 - and I have made it work with OpenOffice under Ubuntu 5.04 (but 5.10 is harder!). ie For printing text...
/
To print photos, under Gimp, I appear to need a driver 5700 (or a similar number, sorry I'm using another PC to do this - since my Linux/Ubuntu510 isn't connecting, yet).

I'm somewhat confused by this recommended driver (from Linuxprintingdotcom I think) - in 504 I downloaded it and it appears to be a text file of commands - not exactly what I expected, but what do I know?.......however, I think it needs to be "put somewhere" or needs another program to run it.....so any assistance would be great. I know Lexmarks aren't well supported and may not offer top-image quality.....but Gimp is a great program.
Any further info needed. thanks.

---

### Post by 504harry on 2005-12-28
[QUOTE=zoiks]It sounds like you have a couple of issues.

1) Looks like your network isn't set up.  When you boot up, go to the menu item System|Administration|Networking.  You should have an ethernet card listed.  Activate this card and in "Properties" make sure it's enabled and has "DHCP" for configuration.  I think you should be good to go once you've done this.  The blurb about synchronization is probably the ntp service starting up, complaining cuz it can't find the server.  It'll work fine when your network's set up properly.  I think you can also ignore the /etc/hosts messages.

2) You can add a printer within gnome by going to System|Administration|Printing.[/QUOTE]

Zoiks-
I've tried your suggestions: this is what happens and I suspect I've been there before, not being sure what to expect...
After Booting + normal log-in:  
[but Gnome still suggests Ubunt needs to be added to /etc/hosts....(.without saying why or how)..]
What follows is what you suggested:

System/Admin/..networking....I get the spinning "round wheel" for 30 sec then nothing, as mouse pointer returns normal
So I tried some others:
S/A/...Services ....*same thing*
S/A/...Time and date....same thing
S/A/...Users and Groups.....same thing
.......it's as though these features only go as far as the "menu".....*it's as though that feature is "missing"....!*
/
Your second suggestion:
System/Admin/..Printing.......error msg tells me "CUPS server could not be contacted" -(but then ethernet PCI-card/web connection is faulty anyway)
(I do recall this Msg before -)

Also, somehow I reached "Device Manager"
and there I find:- Macphyter (who?)...\Ethernet Controller....PCI(tab) lists lots of stuff... including... 
Vendor: Netgear (correct!)
Product:FA311/312 (also correct!)
- I conclude that some of the software is correctly **finding this card **but the necessary Ubuntu commands are missing to **get it going**. 
//
{Just to reiterate (and thanks for your patience)...this PC has now had the Ububtu510.HDD replaced with a WIN98SE HDD}, which is why I'm on-line right now - it "proves" the PC, cable and Modem etc  "works"...I don't believe it's a card issue, or faulty cable - also the processor, RAM, etc is common to both PC's _ I only just replaced the HDD. (=Operating System)
//
Ubuntu510 Boot Message - I wrote it down quickly today - it says 
"synchronising to ntp"..... failed 
- (or something like it...-it flys past so quickly....).
//
I'm considering a fresh install, as I have my genuine Ubuntu 510 CD somewhere. I have just Ububtu on the 120G - but partitioned into three - just under 1G for swap, 60G for programs and 60G for my files (since I normally store photos as CDR to avoid loss if the HDD croaks...yes I know CD's aren't perfect - that worries me too...).
- Is it possible to re-install onto the existing Partitions? - I'm quite happy with them at present.....or would that leave duplicate Ububtu files in place?.....I know Partitioning will erase everything.....There is no work/data worth keeping....
The reason for not re-installing is I don't **see why I can't **fix it. and I'm reluctant to re-partition the HDD- a most unfriendly process....and I'm not sufficiently convinced it will be any better next time.
I did manage Ununtu 5.04 on my own, but this episode shows how little I understand....quite humbling, really. 
.............. Any thoughts welcome.....

---

### Post by zoiks on 2005-12-28
The attachment shows what I get when I choose "System|Administration|Networking".  (I'm not suure if the attachment worked.)

It seems something fundamental is messed up with your gnome installation.  Try running networking from the command line using

```
gksudo network-admin
```

That way, you can see any error messages that come back, which should give you an indication of the problem.  You should post any such error messages here.  You can also try that with services-admin, or time-admin for Time & Date.

The etc/hosts thing gnome is complaining about, I don't know.  Hopefully someone who knows gnome and ubuntu better than I can help interpret that.

Admin/printing may work better when you have the other problem(s) fixed.  FWIW, if you type

```
ps afx | grep cupsd
```

at a command prompt, you should get a line like 

16033 ?        SNs    0:29 /usr/sbin/cupsd -F

if your printing services are running correctly.

---

### Post by 504harry on 2005-12-29
Zoiks,
Many thanks, I will try your suggestions tomorrow and report back; someone may be able to suggest a fix.......it's definately odd....
Regards H.

---

### Post by thingy on 2005-12-29
Hi Harry,

[QUOTE=504harry]The installation and formatting was done with assistance by someone who understands far more than I....however, the pc was stand-alone - other than keyboard/mouse......so the internet and LPT1-printer were missing.[/QUOTE]


Since you did not have a network connection while installing Ubuntu, I suspect the following to be happening:


[QUOTE=504harry]Now, When I log-on  It behaves much as 504, although the screen is darker so I cannot read the endless files - one is in red ( something like "synchronisation - - -"  =fail)  but I can't be certain and don't know what it means - it's about 2/3 the way through the boot sequence.[/QUOTE]

Yes, this sounds like the time synchronisation with the ubuntu NTP server is failing...Ofcourse this would happen since your network is not yet configured. You can ignore this message! It just means that ubuntu tried to update your systems clock with the correct time by polling the time from a accurate time server machine.


[QUOTE=504harry]After it gets my details it says: Gnome is missing Ubuntu internet address...and suggests I add it to file/etc/hosts....then gives me the option of try again or log-in anyway. (only this option produces a result)...when logged-in I cannot use the internet, even though it's connected (that's how I'm writing this, using a different HDD/ OS, although it's the same pc hardware.....
Not nly that but I cannot find this file/etc/hosts although once I did and it was a "Read-only file" so I couldn't add "Ubuntu" to it, although cusriously the file already says "Ubuntu" - however, I wonder why if Gnome needs it for the web it isn't [www.Ubuntu.com](www.Ubuntu.com) (rather than plain Ubuntu)[/QUOTE]

I'm not sure what this Gnome is missing ubuntu internet address thing is...It could be related to this thread...Harry have a read of this and see if it applies to you:

[http://www.ubuntuforums.org/showthread.php?t=109002&highlight=gnome+%2Fetc%2Fhosts](http://www.ubuntuforums.org/showthread.php?t=109002&highlight=gnome+%2Fetc%2Fhosts)

The instructions in the thread tell you how to fix the problem if it does apply to you!


JC

---

### Post by 504harry on 2005-12-31
Many thanks to Zoiks and recently, thingy - I looked up this "similar problem" thread and it looks like it has gone for the "new install" routine.....
/however, I'd really like to discover "why" so before I completely trash the HDD - the answer to Zoiks' routines are as follows:-
{what was suggested} 
*what happened*

{Code gksudo network-admin}
*sudo: unable to look up ubuntu via gethostbyname()*
Similar answer from the following = trying something else that doesn't appear to be working when I go into ADMIN -
{code gksudo time-admin}
*sudo: unable to look up ubuntu via gethostbyname()*

Further, I tried the printing problem:
{ps afx | grep cupsd}
[I]7667 pts/o s+  0:00 \_grepcupsd
7536?           SNs0:00/usr/sbincupsd -F[/I]

The hope is that someone will recognise these replies and suggest a fix........Thanks

---

### Post by zoiks on 2005-12-31
This may help.  The first line in your /etc/hosts is I think supposed to look like this.

127.0.0.1 localhost.localdomain localhost ubuntu

I have a feeling it doesn't.  The line may be either missing or the last entry doesn't say "ubuntu".  It might be related to some screw-up related to your hostname during installation, or an incomplete change of your hostname to something else after installation.

FWIW, I got similar behavior as you when I put the wrong host name as the last entry in the first line of /etc/hosts.  This will probably fix your printing problem as well.

---

