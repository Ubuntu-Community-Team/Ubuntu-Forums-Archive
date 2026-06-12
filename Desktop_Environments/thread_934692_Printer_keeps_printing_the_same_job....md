---
title: "Printer keeps printing the same job..."
date: 2008-09-30
forum: Desktop Environments
---

### Post by SchneiderIS on 2008-09-30
I am experiencing a very odd problem.  When I go to print the printing performance is slow, which I can live with, and then after the print job is done it will keep on printing more copies.  These copies don't happen right away but rather after  restart my laptop.  At first I thought it was happening because I am printing through a USB printer connected to a Apple AirPort Extreme Base Station (I think this is what is causing the slow printing though) but then I set the print queue to abort the print job on an error (thinking it was trying to get past an error) but it still does the same thing.  I checked the number of copies and all is set to one copy.

Does anyone have any experience with this issue and does anyone have a resolution?

---

### Post by Arfdaddy on 2008-10-01
A few things I’ll ask for:
[LIST]
[*]your operating system, including version - Ubuntu something, or you'd be posting somewhere else,
[*]your printer model,
[*]how your printer is configured,
[/LIST]
[INDENT]I’m betting, since you’re using an Airport Extreme, that you’ve configured the printer as an HP JetDirect.  You’re getting prints, so you’ve got the IP address right, and the port number as well.[/INDENT]

[LIST]
[*]where you got the printer driver – did your operating system already know your printer, or did you have to go through some machinations to get it recognized?
[/LIST]

Now for the disclaimer:  In answer to your question, “No.”  I’ve never seen or heard of this problem before.  My response is based on intuition, on my experience with a similar problem - if you're not too particular about what "similar" means - and on how I’d start to troubleshoot this issue.

My opening theory is this:  
[LIST]
[*]I believe that the printer driver in your laptop expects to see a message from the printer that indicates that the job was completed.  I also believe that the Airport isn’t passing that message back to the computer, or at least it’s not doing so correctly.  As long as your session is active, the driver waits patiently for a response.  When you reboot, the driver looks for unfinished print jobs, and, finding one on which it never saw confirmation, sends it to the queue again.

[*]Note that Apple’s Airport/printer troubleshooting page says that the Airport is “  … not for printer utilities or other special features that may require a direct proprietary connection.”  ([http://support.apple.com/kb/TS1253](http://support.apple.com/kb/TS1253) )
[/LIST]


Knowing how the printer performed when it was directly connected to the laptop, and how the printer performed over the Airport from some other operating system – surely if you forked out the long green for an Airport, there’s a Mac around to test with – would go a long way toward refining the theory.  Just print and reboot, and see if you can duplicate the problem with a local interface or a different operating system.  If you haven’t already connected the printer directly to the laptop, I’d suggest that you create a second incarnation of the printer to perform that test, rather than trying it with the existing one – you’ll want different settings without the Airport.

Post your results, and we’ll see what to do next.

---

### Post by SchneiderIS on 2008-10-02
Thanks for the help.  

Here are the answers to your question:
- The operating system is 8.04 Ubuntu.
- The printer is a Canon MP830 multi-function.  The driver that I am using is a Guitenprint version for the Canon Pixima MP830
- You are correct that it is setup through a HP JetDirect and it is using port 9101.  The rest of the settings are defaults.
-  The printer driver, from what I recall, came with the install of Ubuntu.

Your theory is interesting in that yesterday I observed a means of printing that works better than past efforts.  After a print I have to clear the queue and then turn the printer off and then on again in order to send another print right away.  If you don't do this then it can take a long time, if ever, before the next print can go through.  I have also noticed that after printing from the Ubuntu box my Mac can have difficulty printing to the printer.  After the first print from Ubuntu the printer can also process subsequent prints extremely slow (15 minutes per page type of slow).

Hooking the printer up directly has worked perfectly fine in the past but I will try it again tomorrow and report back to you again.

---

### Post by Arfdaddy on 2008-10-04
Quoting you tersely:
> - ... 8.04 Ubuntu
- ... MP830 ... driver ... Gutenprint
- ... HP JetDirect ... port 9101
- ... driver ... came with ... Ubuntu.



Great!  I have the same setup:  Hardy, Canon iP4200, a cheap dinky "print server," if you're generous with that term, HP JetDirect protocol, port 9100, Gutenprint driver.

OK, it's not exactly the same.  Your hardware is much classier.

Here are some things that I'd like to know:
[LIST]
[*]When you say, "clear the queue," are you finding something in the queue after the print is complete?  If you are, does it clear by itself in a few minutes, or does/do the job/jobs just stay there?
[*]How are you clearing the queue?
[*]If you just clear the queue, without resetting the printer, does the performance change at all with either your Ubuntu box or your Mac?
[*]How's printing with the Mac?  Does it just work, as long as you don't try to print from Ubuntu?
[*]You're on  port 9101, while the canonical (no pun ... ) installation uses 9100.  I'm guessing that port 9100 wasn't available on the Airport.  What prompted you to use 9101?
[*]Do the fax and scanner functions work on the Mac?  Have you been able to set them up on the Ubuntu box?  Do they work on it?
[/LIST]

When you try directly connecting to the Ubuntu box again, I'd like to know:
[LIST]
[*]Whether the queue behaves differently than when the box is connected to the printer via the Airport - if it didn't clear itself through the Airport, does it clear itself when it's directly connected?
[*]Whether the printer works as expected when it's connected directly, particularly, whether it prints multiple jobs - where "multiple" means a number of jobs that would have given you trouble with the Airport - with reasonable performance.
[*]Whether the printer tries to print another copy after you reboot the Ubuntu box.
[/LIST]

Finally, some other stuff I'd like to know, that will take some experimenting:
[LIST]
[*]How does the system work with the Ubuntu box connected to one of the Airport's Ethernet connections?  I'd like to know if you get the same symptoms - queue doesn't clear, next print takes a long time, Mac has trouble printing after the Ubuntu box prints, performance improves if you clear the Ubuntu queue and reset the printer.
[*]If you print from Ubuntu, let the job finish, wait a few minutes, and then shut down the Ubuntu box, without clearing the queue or resetting the printer, how well does printing work from the Mac with the Ubuntu box off?
[*]If you have a Windows system, how does the system perform with the Windows box printing wirelessly?  Can you follow it with the Mac without problems?
[/LIST]

Now for the disclaimer:  I'm no expert in printing from Linux - I have a bit of experience setting up a couple of printers in Sarge, Etch, Edgy and Hardy with a puny server.  All this stuff that I'm suggesting you do is just the stuff that I would try, in order to get a feel for what the problem actually is.  I don't have a clear path to a solution in mind.  If you feel like doing all these tests, keep in mind that we may not get to an answer that has your printer on the Airport, playing nice with all the other gizmos that share the channel.  We may wind up doing this strictly in the interests of science, or, if we get lucky, our diligence may attract a Linux printing heavy hitter, who will tell us, "just apt-get somethingorother," and fix it.

Notice how I say, "we," when you have to do all the work.

Whew!  This is a long post.

---

### Post by SchneiderIS on 2008-10-05
I had written a longer post and left it overnight to wrap up some final tests.  Then just after hitting the "Post Quick Reply" remembered that I was going to copy the text in the event that something timed out.  To late, lost all the first round text so here I go again. This time I will try to keep it shorter.

- When I say clear the queue it is the printer queue that I access through the print job dialog.  The print stays in the queue and for some unknown time limit.  

- I clear the queue by right-clicking and selecting "Remove".  After removing the item from the queue I still need to restart the printer otherwise nothing else gets through from either the Mac or the Ubuntu.  

- The Mac has no problem printing through the AEBS unless the Ubuntu box has printed to it first.  Then it just doesn't get a print through.

- I am using port 9101 because 9100 didn't work.  I didn't do a port scan as the ability to work or not work seemed like a good enough scan.

- The Fax and Scanner only work when directly connected to the Mac.  With the AEBS would support this functionality as it would be much nicer that switching cables around when I need it, and only being able to do so with a machine in the same room.

- When the printer is connected directly to the Ubuntu box it works flawlessly in every regard.  There is no throwing it off in queue management, rebooting, anything.  

- The Ubuntu box is already connected to the AEBS through the wired Ethernet port and not wirelessly.  There have been other issues with the wireless card on the Toshiba laptop where Ubuntu is installed.  Given that it is only a 802.11.g adapter and I am wanting to get the best performance that I can from the network I opten to remove it from the party wirelessly.

- If I turn off the Ubuntu box after having printed from it, and after having tried to print from the Mac after having printed from it, it does not clear things up and enable the Mac to print right away.  This one is funny as when the Ubuntu box came back online, not logged in though, it then let my Mac job through and then started to print the last job from the Ubuntu box again.

- When I had Windows boxes they were able to print without issue.  Not surprising given that Apple provides the interface to go through the AEBS.

Something that may interest you is that after a print is complete from the Ubuntu box the printer shows the regular ready to print, or copy, status in the printers LCD.  As such the printer does think that it is done.  Odd then that the Mac and the Ubuntu box cannot print to it again then.  Makes me think, perhaps a twist to what you talked to earlier, that there must be some final status that needs to be sent to the AEBS to indicate that the job is complete.  Perhaps this isn't so much a printer and Ubuntu problem as a protocol of engagement from the AEBS side.

Thanks again for your help with this one.

---

### Post by Arfdaddy on 2008-10-06
> ... using port 9101 because 9100 didn't work.

I've seen more than one post about the difficulty of getting a printer to work with an Airport on port 9101.  Here's one: [[COLOR="Blue"]_http://ubuntuforums.org/showthread.php?t=156675_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=156675").  That guy even downgraded his airport firmware to get 9100 open, saying that 9101 "wouldn't work."  No word on whether, "wouldn't work," means, "wouldn't print," or, "acted weird."  That post is from a couple of years ago, and maybe a couple of OS iterations ago - I'm not seriously recommending that you downgrade your Airport firmware to something that was current that long ago.  

Here's some more info on JetDirect, Ubuntu and port 9100 - though none of it's recent - from CUPS' own site: [[COLOR="Blue"]_http://www.cups.org/newsgroups.php?s1+gcups.bugs+T0+Qjetdirect_[/COLOR]]("http://www.cups.org/newsgroups.php?s1+gcups.bugs+T0+Qjetdirect") 

Nevertheless, there's the possibility that CUPS isn't set up to manage network printing over port 9101.  Some say it works, no problem; some say it works, not; some say it works, crummily.

Here's some info on the JetDirect and AppSocket protocols at an MIT link: [[COLOR="Blue"]_http://web.mit.edu/source/third/lprng/doc/LPRng-HOWTO-3.html#ss3.1_[/COLOR]]("http://web.mit.edu/source/third/lprng/doc/LPRng-HOWTO-3.html#ss3.1"). There's a suggestion that the AppSocket protocol uses port 9101 for status and maybe control transactions - something that printing on port 9101 might interfere with.  There's also some text indicating that AppSocket will refuse a connection to a host if it already has a connection to another - suggesting that connections are closed by either the host or printer.  There's more text indicating that Socket API, a more recent protocol used by HP JetDirect printers, needs some transactrions to close the connection to a host, including a "half close" by the host when the data has all been sent, and a final closing by the printer.  It also indicates that JetDirect and AppSocket protocols diverged at some time in the past, which makes me wonder just what we're getting when we select "AppSocket/HP JetDirect" when we set the printer up. We have to take this info with a grain of salt, even though it's MIT, because the purpose of the page is about something else, and it only incidentally has any info about these protocols.  I'm not able to find a specification of either protocol on the web.

> When the printer is connected directly to the Ubuntu box it works flawlessly in every regard.

That argues heavily for the efficacy of the Gutenprint driver.  The driver works properly when it's connected the way that its maker intended.

> If I turn off the Ubuntu box after having printed from it, and after having tried to print from the Mac after having printed from it, it does not clear things up and enable the Mac to print right away.  This one is funny as when the Ubuntu box came back online, not logged in though, it then let my Mac job through and then started to print the last job from the Ubuntu box again.

That makes me suspect this - and I hate to suspect it, because I don't know what to do about it:  Either the Ubuntu or the Airport aren't getting the connection to the printer closed.  Ubuntu doesn't send it, or the Airport doesn't understand it, and the printer connection stays open to the Ubuntu box.  Shutting down the box doesn't get the connection closed, as the Airport apparently doesn't let the connection time out, or the Ubunutu box fails to close its connection as it gives out its last gasp.  I also suspect that, when the Ubuntu powers up, the Airport recognizes it and closes the previous connection, or Ubuntu does it, for some mysterious reason.

It looks like CUPS and the Airport aren't playing nice with each other, one way or the other - an odd development, since, as of about this time last year, Apple owns CUPS, and employs the guy that invented it.  I doubt that the printer has any idea who's talking to it, ever.

> ... Windows boxes ... were able to print without issue.

Not surprising, as you say.  Do you know how they performed with the Ubuntu box on the network?  Could the follow the Ubuntu, or did they have the same symptoms that the Ubuntu-then-Mac arrangement has?  Or did you even have Windows and Ubuntu at the same time?

> ... there must be some final status that needs to be sent to the AEBS to indicate that the job is complete.  

I can't tell which device is supposed to send what.  According to the MIT link, the printer may be in charge of closing the connection - but that would mean that the AEBS might handle that closing, since the printer doesn't expect to be available to multiple hosts and may not have any way to do such a thing, and besides, who know what its protocol is like?  I'm not sure how the AEBS, or any print server, for that matter, can know when the print job is complete over a USB interface, since it doesn't appear that it ever gets a clue as to what the printer really is, and what protocol it uses - unless Bonjour tells it something, and I've no idea what Bonjour does.

> Perhaps this isn't so much a printer and Ubuntu problem as a protocol of engagement from the AEBS side.

My instincts say that it's between the Ubuntu box and the AEBS. My instinct is to accuse the AEBS, since it makes sense to declare that it's the printer's responsibility to make the final closure on the connection - the host only knows when it finished sending, and printing has to finish some time after that, so the printer - or it's manager, the AEBS - has to declare the job complete. And I really don't know how to fix it.

And, since I'm baffled by my own theory, I'll suggest something to try that's inconsistent with it, for no other reason than that it's easy:  My Hardy setup has two Gutenprint drivers for the MP830 - a simplified one, which CUPS shows as "recommended," and another presumbaly complicated one.  You might try whichever one you're not using now, though I'm not optimistic, since it looks like the driver you use works perfectly.

Happy hunting.

---

### Post by SchneiderIS on 2008-10-08
Thanks ArfDaddy,

Resorting back to so much older of a firmware on my AEBS is not an option.  I had already read the same post but thanks for looking.  The CUPS post is definitely not a help as it actually seams like a step backwards.

I had actually already tried the Simplified driver and had no success but decided to retry it now.  In doing so I scratched my head because I noticed that I am using port 9100!  What a bonehead I am.  At any rate 9101 is not plugged up so it could communicate.

So I tried the Simplified driver again and it does absolutely nothing.  

Given that Apple owns CUPS and should know the print system for Linux and the development should be easy, it would be nice if they could simply knock out support for the AEBS or at least document configuration for it.  A real disappointment in my books. 

It looks like for now I will bear with it until I get my wife converted over to a Mac.

---

### Post by Arfdaddy on 2008-10-08
There's one alternative that you could try - you could buy a cheesy little printer server and connect it to one of the Airport's Ethernet ports, and connect the printer to that.  

My cheesy little server is an Airlink APSUSB201 "1-port USB Printer Server."  I paid about $19 for it.  It just works, generally, in that printing happens just like I expect.  It doesn't seem to work with any of the printer utilities, like examining the ink tank levels or anything that makes the printer talk back to the computer, from Windows, the printer's favorite OS.  I seriously doubt that you'd ever get the scanner working, and maybe not the fax, either - but I have doubts about whether you'll get those working over the Airport, too.  This one claims to work with a Mac, but you'll want to look at the manual to decide if it would work with yours.  [**[COLOR="Blue"]http://www.airlink101.com/download/apsusb201.php[/COLOR]**]("http://www.airlink101.com/download/apsusb201.php")

Setup could, as usual, be tricky.  I'd set it up with the Mac, and then use the info that I got from that process to set it up in Ubuntu.

Another thing you could try is posting at [www.cups.org](www.cups.org) - you'd think that those guys would know enough to help, and, being Apple employees now, would want to pretty badly.  I don't see that anyone has posted about an Airport unit since before the Apple takeover.

Printing from Linux appears to have long been a bugaboo.  I've heard that it's a spiritual act of mercy to help someone get their printer set up in Linux.  Network printing seems to be a bit of a bugaboo for everybody - my guess is that it's because the protocols of the network interface and the proprietary printer protocols don't match up very well.

Good luck in your quest.  Sorry we couldn't hammer out a happier solution.

---

