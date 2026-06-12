---
title: "HSDPA Modem"
date: 2009-05-07
forum: General Help
---

### Post by mark.giblin on 2009-05-07
I have been looking and can not find the interface that monitors incoming SMS and allow outgoing SMS.

I plugged the modem in to my WindowsXP machine to find that people had been SMS'ing me for about a month but under Ubuntu, I got no incoming notifcation that the modem had recieved any SMS messages.

This is seriously bad, mainly because "3" in the UK send out important messages, passwords and other important information to their customers as well as that I use the SMS function and have been scratching my head on exactly where this part of the modem features are.

They appear to be missing or are they?

If anyone with experience can tell me where I look or what package I need in addition to access these important features I would appreciate it.

---

### Post by mark.giblin on 2009-05-09
I have tried "WINE" and running a copy of the modems software like I do on windows.

It is not at all happy. It does not acknowledge anything is plugged in to the USB, the software crashes and then I have to reboot because the system almost grinds to a halt.

So anyone in develpment, care to add the "Bubdled" functionalit that comes with a HSDPA modem like the reciept and sending of SMS, alerts, etc..?

The alternative is if someone here knows what application if any exists will allow access to these features.

---

### Post by Rhubarb on 2009-05-09
Wine won't work, as it can't interface to hardware at all.

You should try using a nice app called **Wammu** - It's in the Ubuntu repositories.
You'll need to set it up initially (it's not too hard, it's a nice easy app to use)

You can only use Wammu when you're not connected to the mobile network.

Wammu works for me with my "3" 3g usb modem quite nicely - I can send and receive SMSes with it fine.

---

### Post by mark.giblin on 2009-05-10
Thanks for that, it appears to connect but I have no indication of any SMS and it tends to crash which I have been finding an issue.

I seriously do not see why this important part of the modems features are neglected in the connection software that allow the HSDPA modem to function.

Under windows you can SMS while on-line... Seem that Myopia runs rife in Linux.

I resorted to WINE to see if I can get the functionality that is present in windows programs but is lacking in the linux programs.

It is a major pain in the *** having to disconect, because the "Device" is being used...

IMHO linux developers need to be looking long and hard at what programs they already have and how they can include the same functaionality.

I know that this is proving to me that the reason why windows wins the operating system install stakes is because the windows programs are designed better. This is based on my 3 months of trying to get various elements functioning in linux that are readily available under M$.

Me thinks if Linux wants to whoop microsofts ***, its a case of having to come up to scratch and having alternate programs that provide the same level of service.

TBH I am not impressed and I am being more than fair in giving Linux every chance but its becoming aparent that I will have to invest in a WinXP operating system as Linux currently is not cutting it.

Anyway, thanks for your help, it is IMHO a part of the HSDPA modem that should be accessed via the Network connections. I just hope that a developer of the Ubuntu team comprehends my whinge and understands that if Linux wants to win over windows users, the transition should be seemless and offer same as... Of the 5 people I have suggested to try Ubuntu, they all have gone back to windows, asking them why, they don't like it because it does not offer what they need unlike windows.

I don't suppose you know anything about sendmail or MTA as I can not get outgoing smtp connections but can get incoming pop, found here: [http://ubuntuforums.org/showthread.php?t=1130729](http://ubuntuforums.org/showthread.php?t=1130729) seems that help on this matter is nonexistent.

---

### Post by Rhubarb on 2009-05-11
> **mark.giblin said:**
> I seriously do not see why this important part of the modems features are neglected in the connection software that allow the HSDPA modem to function.
That's because HSDPA modems appear to the Operating System as a simple (usb attached) serial dial-up modem.
Dial up modems don't support SMS, which is why SMS features aren't currently supported in the gnome networking area.
Building in SMS support would require quite a bit of code.
Every different branded HSDPA modem would have a different interface to send / receive SMSs, which would add to the complexity if adding SMS support.


> **mark.giblin said:**
> Under windows you can SMS while on-line... Seem that Myopia runs rife in Linux.
That's because the manufacturers have made the program to enable that.
Windows does not support HSDPA modems by default without this customized software.

> **mark.giblin said:**
> It is a major pain in the *** having to disconect, because the "Device" is being used...
Be thankful that you can connect to the net with your HSDPA modem from the networking area, just last year you couldn't actually do that (you had to do it a much more un-user-friendly way).
If you're willing to spend some time / money, you could discuss this issue with some relevant people to start to get this integrated into gnome - it sounds like it could be a good nice feature to have.

> **mark.giblin said:**
> IMHO linux developers need to be looking long and hard at what programs they already have and how they can include the same functaionality.
Maybe that's because a very large majority of Linux developers either aren't interested / don't have any incentive / don't use HSDPA modems to send / receive SMSs.

> **mark.giblin said:**
> TBH I am not impressed and I am being more than fair in giving Linux every chance but its becoming aparent that I will have to invest in a WinXP operating system as Linux currently is not cutting it.
True, you have spent 3 months trying.
If you don't try to help out the Linux community, then perhaps your other alternative is to get that XP box (not that you can buy these anymore) and wait until it's supported in Linux.

> **mark.giblin said:**
> Anyway, thanks for your help, it is IMHO a part of the HSDPA modem that should be accessed via the Network connections. I just hope that a developer of the Ubuntu team comprehends my whinge and understands that if Linux wants to win over windows users, the transition should be seemless and offer same as... Of the 5 people I have suggested to try Ubuntu, they all have gone back to windows, asking them why, they don't like it because it does not offer what they need unlike windows.
Indeed I agree with you that it should be accessed via network connections, or some other easy way (perhaps evolution?).
An Ubuntu developer may not be the kind that would pick up development work for this.  More likely a Gammu developer that's wanting to collaborate with Gnome.
It's best to ask what people use their computer for before offering them a Ubuntu.  As some people have very specific needs, other people are unaware of what capable-but-alternative programs there are for Ubuntu.
Then if someone does want to try out Ubuntu, I install it and pre-configure it for them to suit their needs - atleast 90% of the people I do this for are very happy and haven't gone back to windows at all.

> **mark.giblin said:**
> I don't suppose you know anything about sendmail or MTA as I can not get outgoing smtp connections but can get incoming pop, found here: [http://ubuntuforums.org/showthread.php?t=1130729](http://ubuntuforums.org/showthread.php?t=1130729) seems that help on this matter is nonexistent.
Have a look, I replied, I'm not sure it'll be of much help though - as I haven't experienced many email problems before in Ubuntu - only when trying to send email from an outside different Internet Service Provider.

Gammu's website:
[http://www.gammu.org/wiki/index.php?title=Main_Page](http://www.gammu.org/wiki/index.php?title=Main_Page)

Wammu's website:
[http://wammu.eu/](http://wammu.eu/)

---

### Post by mark.giblin on 2009-05-11
I shall have a look.

On the issue of the HSDPA modem, I have contacted the manufacturer and suggested that they produce a suitble program support for Linux users. At first they replied with a message that they do not support Linux. I pointed them to the web forum article on setting up the modems under Linux.

Although I am not expecting anything to come of it, I have atleast planted the seed and hope to see future hardware with Linux support from the website of the manufacturer of the HSDPA modem will be available. I pointed out to them that if they want to reach a wider audiabce, they should consider supporting Linux systems.

We will have to see...

---

### Post by dj-toonz on 2009-05-11
Bravo Mark, I myself own & use a three Branded hsdpa modem under jaunty & I can't receive the text messages that three send when your broadband access is running low, that sort of stuff. yes there is the vodafone connection software for Ubuntu, that lets you receive/send text messages & check your data allowance as well. but I can't seem to get it to work as it comes up with unknown provider and no signal strength (as I don't know if it is just for vodafone or any network as it doesn't say on the website but I can still access the Internet using it tho, the website is [https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/) and you need the usb-modeswitch_0.9.7_i386.deb and  vodafone-mobile-connect_2.00.00-1_all.deb from the files section, to install that install the usb-switch.deb first then the vodafone-mobile-connect.deb second & it shows up in the Internet section under Applications, u might get better luck out of it then I do & it doesn't break the network connection's already set up in Ubuntu for the hsdpa modem (if that's what your thinking) as I used it before for a test to see what my millage would be but I used the svn version of it) so i used terminal after to do a sudo apt-get remove usb-modeswitch & sudo apt-get remove vodafone-mobile-connect to remove the installed files then sudo apt-get autoremove to clean up the left over python files that it installed (as the software uses python) then sudo apt-get clean & autoclean & the network connection under network manager still worked

---

