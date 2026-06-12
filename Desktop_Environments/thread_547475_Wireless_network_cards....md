---
title: "Wireless network cards..."
date: 2007-09-10
forum: Desktop Environments
---

### Post by richardterris on 2007-09-10
Jeez these forums move fast don't they..

Anyway, i have an Edimax EW-7108PCg card, and i am having problems with this in Feisty...

The system does seem to recognise the card is there, but does not want to connect to it..

I dug around online a bit and found an article that states their are two colours of card (apparantly this is a s techinical as they wanted to be), a light red and a dark red.. only the light red one works with ubuntu, according to this article anyway,...

And you can guess which colour of card i have

Does anyone know if this article is correct? 

Do i have to buy a new card? If so, can anyone recommend one to me?

Richy.

---

### Post by mojoman on 2007-09-10
> **richardterris said:**
> 
Does anyone know if this article is correct? 


Your chances of getting an answer on this one will increase significantly if you post a link to the article in question.

I've had good experience with the Ralink RT2500 Cards. It worked out of the box on breezy, dapper and feisty. (Never ran edgy but I assume it works there as well. Haven't gotten around to try gutsy yet either.) I also used this card on Debian Etch and I know other people on this forum who also used it succesfully.  A small caveat is that there have been people who had some problems with it but I think that all of them got the cards to work after some tweaking.

best regards
/mojoman

EDIT: Just adding that I've used Ralink RT2500 both for laptops and for desktop.

---

### Post by richardterris on 2007-09-11
> **mojoman said:**
> Your chances of getting an answer on this one will increase significantly if you post a link to the article in question.


Good thinking Batman....

[http://ubuntu-uk.groups.vox.com/library/post/6a00d4141b9517685e00cd971fed744cd5.html](http://ubuntu-uk.groups.vox.com/library/post/6a00d4141b9517685e00cd971fed744cd5.html)

---

### Post by richardterris on 2007-09-12
Ok 

last night i got the RT2500 code from debian etch

On the network connections on the system tray, it does appear to be recognising the card's presence as its getting as far as 94% signal strength; At this point however, i am not even able to get onto the page with my router configuration let alone the internet.

Tried with roaming both enabled and disabled.

Anyone who managed to get this card working, mojoman? Could you contact me to talk me through this? Im not so clued up yet on the technical aspects, and there may well be something i have missed....

---

### Post by mojoman on 2007-09-12
> **richardterris said:**
> Ok 

last night i got the RT2500 code from debian etch

On the network connections on the system tray, it does appear to be recognising the card's presence as its getting as far as 94% signal strength; At this point however, i am not even able to get onto the page with my router configuration let alone the internet.

Tried with roaming both enabled and disabled.

Anyone who managed to get this card working, mojoman? Could you contact me to talk me through this? Im not so clued up yet on the technical aspects, and there may well be something i have missed....

I don't know if anyone got that exact card to work google tells me it has the rt2500 chip so it shouldn't be too hard (hope I don't have to eat these words).

First I'd do is have a look at what iwconfig tells you. Open a terminal and punch in.
```

iwconfig
```

This should give you an output on the wireless. My server uses this chip and I get this output

```
ra0       RT2500 Wireless  ESSID:MYESSID  
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:0F:B5:14:DA:A6   
          Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:MYKEY   Security mode:open
          Link Quality=65/100  Signal level=-72 dBm  Noise level:-210 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

(I edited out MYESSID and MYKEY since I really don't want that on the net...) How does your output look. If the card is detected nicely it could be a simple thing such it not being brought up properly.

To bring up a card you use the ifconfig commando. Just punch in

```
sudo ifconfig ra0 up
```
(note that you might have to change ra0 for whatever your card is called but you should get this information from iwconfig)

Also, try pinging your router to see if there is any connection there. Do you know the router IP? A good guess would be 192.168.0.1but there might be other options. You ping it by punching in
```
ping -c 3 192.168.0.1
```
(the -c 3 tells ping to try three times. Otherwise, it'll keep going and going and going and, eh, you get the idea.)

Try these things for a starter. If we're really lucky it will work, if not we'll have some more info to work with.

/mojoman

---

### Post by richardterris on 2007-09-12
I wont be able to look at this until i go home from work.

I emailed Edimax earlier for them to confirm or deny this report of the two different colour of cards, and they emailed back saying there are 2 different cards...

The girl who emailed me, has asked me to open the card and tell her which adapter is inside... strange request i thought in all honesty, but it seems that perhaps my card will just not work because of the FCC ID?

---

### Post by mojoman on 2007-09-12
> **richardterris said:**
> I wont be able to look at this until i go home from work.

I emailed Edimax earlier for them to confirm or deny this report of the two different colour of cards, and they emailed back saying there are 2 different cards...

The girl who emailed me, has asked me to open the card and tell her which adapter is inside... strange request i thought in all honesty, but it seems that perhaps my card will just not work because of the FCC ID?

Isn't the FCC ID just a number that will help you information on the hardware and its manufacturer? Anyway, try the stuff I posted and it that doesn't help you can try compiling the driver from etch.I got a good step-by-step howto on it if you need it.  I know that it has worked for several people, and I myself used it on my Debian laptop but with a little luck it won't be needed at all. I'll check back later to see what you've come up with.

cheers
/mojoman

---

### Post by richardterris on 2007-09-12
Step by step might be a good help actually..

---

### Post by TimVB on 2007-09-12
The folks at [The Linux Emporium]("http://www.linuxemporium.co.uk/products/wireless/#pid88169") reckon the Edimax EW-7108pcg (yes, the dark red one) should work 'out of the box' with Feisty, and sell them as such.  

They write (on a README that comes with the card):
----------------
Users of Ubuntu Feisty with a [Edimax] PCI or PCMCIA card do not need to install the drivers from the CD [which comes with the card] as the new rt2x00 serialmonkey driver that is provided with Feisty works.  The interface is detected as ra0.

Unfortunately as of May 2007 it is not possible to set the WEP key for the serialmonkey driver, so the /etc/network/interfaces has to be edited.  From a console use nano:

$sudo nano /etc/network/interfaces

and then add the following lines, using the actual values in place of the bracketed items:

auto ra0
iface ra0 inet dhcp
     wireless-essid <your-essid>
     wireless-key <your-key>

use ctrl-O to write out the file and ctrl-X to exit.

The card can be brought up using 
$sudo ifup ra0

If the card is subsequently removed and then replaced then the commands:
$sudo ifdown ra0

then

$sudo ifup ra0

will re-activate the card.

---------------
They say it doesn't work with WPA though.  I can confirm that I got my WiFi card working this way.  However, I then had to re-install Feisty and now it's not working.  It's entirely possible that, in the process of trying to get various cards working, I installed the drivers that made the Edimax work and it is these - not the Linux Emporium notes - that got the card working!!

If the above fails, I think you need to install the RT61 driver.  The LinuxEmporium CD provides this and some scripting, which I'll try when I've finished my urgently pressing work (so why am I writing here??)

Or try [here]("http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61") to use the RaLink driver, or [here]("http://ubuntuforums.org/showthread.php?t=400236&highlight=rt61") to follow the HOWTO for the RT73 serialmonkey drivers, but making the necessary changes for RT61.  I hope that helps - sorry not to be more precise; I'll give several things a try and see what happens!  (I'm very much a newbie using google, ubuntuforums and following instructions blindly, so no promises!!)

Or try [here]("http://ubuntuforums.org/showthread.php?t=419709") for someone who reckons they have an RT61 chipset card working with Feisty *and* WPA.   Must stop googling and start writing my sermon for sunday!

**UPDATE!!** I tried 'ifconfig' and it showed that my card was ra1, not ra0 (my terminology is probably wrong).  So I changed the entries in /etc/network/interfaces from ra0 to ra1, did a "$sudo ifup ra1" and now it's working!   This is after a very fresh install of feisty, which means it should be very easy to get an Edimax EW-7108pcg working with feisty, at least with WEP rather than WPA.

---

### Post by mojoman on 2007-09-12
_[Here]("http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto")_ is a good step-by-step guide for rt2500. The guide is for Debian Etch and Sid but it has been used succesfully with Ubuntu as well.

Again, I'd try the other stuff before compiling the driver from source as it might not be needed but the how-to is pretty straightforward. You'll nedd to have build-essential installed in order to compile is and probably some kernel packages as well but if you have build-essential the terminal will yell and holler to tell you what it needs. To install build-essential, open a terminal and type

```
sudo apt-get install build-essential
```

/mojoman

---

### Post by richardterris on 2007-09-12
This is a nightmare...

Ive just tried all of the above, and also went through a HOWTO

Still not working.... perhaps i'll just go back to windows... dont wanna, but at least my **** works there.

Thanks for the help guys

---

### Post by mojoman on 2007-09-13
If anyone is going to be able to help out you need to provied them with more information on what is going on when you try the these thing.

Could you post the output of the following commands:

```
ifconfig
```
```
iwconfig
```
```
cat /etc/resolv.conf
```
```
cat /etc/network/interfaces
```

/mojoman

---

### Post by richardterris on 2007-09-13
Ok chaps,

Thanks for your help so far.... I fear i have probably messed things up too much with all my mucking about last night... Is there a way to wipe the slate clean? Will i just delete the directories that were created in the process?

I will try to go through this again after work, at about 5pm, and i will post the outputs i get from each step..

Im becoming very confused with all the different drivers and HOWTO's that are on offer.. Be careful what you wish for eh, lol..

I will try the RT61, since thats what Edimax themselves have recommended to me, and i'll get back to you, because i probably will, nay, will need more help no doubt,

Cheers,

Richy

---

### Post by mojoman on 2007-09-13
Just wiping the directories sound like an awful idea. If you screwed things up it's most likley config-files and those can be edited. Again, post the output I asked for and people will have a better idea of the nature of the problem.

---

### Post by richardterris on 2007-09-13
The plot thickens MojoMan...

Girl from Edimax emailed me this today 

"Hello,

 I have managed to find the way to identify.  It depends on the adapter, when you open up the casing, on the Ralink chip, you will either be able to see the chipset number which starts with RT, or you will be able to check the version.  Version 1 is RT-2560 chipset and version 2 is RT-2561 chipset.  If you can find the exact driver for your adapter according to the chipset then it should be fine".

Im not sure if i want to open the casing on the card, because there are no screws, so it will imvolve bending metal with a screwdriver... warranty etc etc

If it can only be one or the other driver, then i'll just try one and then the other...

Would any of you be available on messenger for some live help? around 4.30pm?

Richy

---

### Post by mojoman on 2007-09-13
But why would you want to go through all this trouble (i.e. opening the case to determine the exact chip number) before trying other options? Your about to pry open the hardware without doing some very basic stuff first. This just don't make any sense to me. Again, if you'd post the output of the commands I wrote people might actually be able to help out. Another command that might provide information is the following,
```
dmesg
```
Post the output of that as well and we'll take it from there.

---

### Post by richardterris on 2007-09-13
Yip agreed, thats why i said, i'll try the stuff you guys gave me before, with the 2 drivers that edimax mentioned..

hopefully i'll get a result with one of them,.

thanks again man, i appreciate your help and patience

---

### Post by richardterris on 2007-09-13
ok guys

i came on tonight (little later than expected) to look at the above..

Ububtu is playing up, and i had to restart the machine 4 times
1st - couldnt enter username or password system froze
2nd - entered these, and system froze
3rd - entered these and ubuntu started loading, then froze
4th - got booted, opened firefox and then system froze

this is all a lot more hassle than i anticipated, and the problem is, i dont have enough technical knowledge to deal with any of these problems, other than coming on here all the time...

thanks for all your help and patience, especially tim and mojoman, but im gonna have to sulk back off to windows.

richy

---

### Post by richardterris on 2007-09-13
> **TimVB said:**
> The folks at [The Linux Emporium]("http://www.linuxemporium.co.uk/products/wireless/#pid88169") reckon the Edimax EW-7108pcg (yes, the dark red one) should work 'out of the box' with Feisty, and sell them as such.  

They write (on a README that comes with the card):
----------------
Users of Ubuntu Feisty with a [Edimax] PCI or PCMCIA card do not need to install the drivers from the CD [which comes with the card] as the new rt2x00 serialmonkey driver that is provided with Feisty works.  The interface is detected as ra0.

Unfortunately as of May 2007 it is not possible to set the WEP key for the serialmonkey driver, so the /etc/network/interfaces has to be edited.  From a console use nano:

$sudo nano /etc/network/interfaces

and then add the following lines, using the actual values in place of the bracketed items:

auto ra0
iface ra0 inet dhcp
     wireless-essid <your-essid>
     wireless-key <your-key>

use ctrl-O to write out the file and ctrl-X to exit.

The card can be brought up using 
$sudo ifup ra0

If the card is subsequently removed and then replaced then the commands:
$sudo ifdown ra0

then

$sudo ifup ra0

will re-activate the card.

---------------
They say it doesn't work with WPA though.  I can confirm that I got my WiFi card working this way.  However, I then had to re-install Feisty and now it's not working.  It's entirely possible that, in the process of trying to get various cards working, I installed the drivers that made the Edimax work and it is these - not the Linux Emporium notes - that got the card working!!

If the above fails, I think you need to install the RT61 driver.  The LinuxEmporium CD provides this and some scripting, which I'll try when I've finished my urgently pressing work (so why am I writing here??)

Or try [here]("http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61") to use the RaLink driver, or [here]("http://ubuntuforums.org/showthread.php?t=400236&highlight=rt61") to follow the HOWTO for the RT73 serialmonkey drivers, but making the necessary changes for RT61.  I hope that helps - sorry not to be more precise; I'll give several things a try and see what happens!  (I'm very much a newbie using google, ubuntuforums and following instructions blindly, so no promises!!)

Or try [here]("http://ubuntuforums.org/showthread.php?t=419709") for someone who reckons they have an RT61 chipset card working with Feisty *and* WPA.   Must stop googling and start writing my sermon for sunday!

**UPDATE!!** I tried 'ifconfig' and it showed that my card was ra1, not ra0 (my terminology is probably wrong).  So I changed the entries in /etc/network/interfaces from ra0 to ra1, did a "$sudo ifup ra1" and now it's working!   This is after a very fresh install of feisty, which means it should be very easy to get an Edimax EW-7108pcg working with feisty, at least with WEP rather than WPA.

[here]("http://ubuntuforums.org/showthread.php?t=419709")

Tried this, and it all worked except when i came to PINGing

When trying to PING my router, i got the message "destination unreachable" each time

and when trying to PING google.com i got unknown host google.com

any ideas?

sorry, i know i said i was giving up but ubuntu seems to be working again, and i also seem to be taking this as a challenge...

thanks again guys.

---

### Post by mojoman on 2007-09-14
> **richardterris said:**
> any ideas?

Well, I might have mentioned posting the output of some relevent files and commandos as a first step.

---

### Post by richardterris on 2007-09-14
Finally!!!

Ok guys, with the RT61 driver installed, i removed the ecryption from my router, and in ubuntu chose manual configuration, and added the gateway and router IP addresses, and Hey Presto!!

In all honesty, im not too bothered if anyone in my building uses my connection, since i think they all have their own anyway.

Mojoman, Jim thank you very much for your help with all this.

---

