---
title: "Evolution upgrade issues (5.04-&gt;5.10, clean install, IMAP server)"
date: 2005-11-14
forum: Desktop Environments
---

### Post by rkinder on 2005-11-14
Hi all,
   Anyone know how to stop evolution querying/searching the IMAP server each time it starts up? I didn't have this problem on evo 2.2, but 2.4 insists on trawling through all 128000 files on my IMAP server home directory, then cranking away for 2hrs+ CPU time (100% usage to evo) before letting me read my emails and send/receive...
   I have the 'only display subscribed folders' checkbox marked, but it seems to do nothing at all in this case. Any debugging hints?
   On a related note, does anyone have a quick recipe for building evolution + related libraries with debugging symbols so I can attempt to look into this problem myself? Note: recipe should be quick - I don't have time to rebuild the world :)

Regards,
   Richard

---

### Post by dcstar on 2005-11-15
[QUOTE=rkinder]Hi all,
   Anyone know how to stop evolution querying/searching the IMAP server each time it starts up? I didn't have this problem on evo 2.2, but 2.4 insists on trawling through all 128000 files on my IMAP server home directory, then cranking away for 2hrs+ CPU time (100% usage to evo) before letting me read my emails and send/receive...
   I have the 'only display subscribed folders' checkbox marked, but it seems to do nothing at all in this case. Any debugging hints?
.......[/QUOTE]
Have you tried using the (from the help file):

[I]IMAP Subscriptions Manager

Because IMAP folders exist on the server, and opening them or checking them takes time, you need fine-grained control over the way that you use IMAP folders. You use the IMAP subscriptions manager to do this. If you prefer to have every mail folder displayed, you can select that option as well. However, if you want to choose specific items in your mailbox, and exclude others, you can use the subscription management tool to do that.

   1. Select Tools > Subscribe to Folders.
   2. If you have accounts on multiple IMAP servers, select the server where you want to manage your subscriptions. Evolution displays a list of available files and folders.
   3. Select a file or folder by clicking it. You should select at least the Inbox folder. Depending upon the way your IMAP server is configured, the list of available files might include non-mail folders. If it does, you can ignore them.
   4. Click Subscribe to add a folder to the subscribed list.
   5. When you have subscribed to the folders you want, close the window. [/I]

---

### Post by rkinder on 2005-11-15
Yeah, I tried the subscriptions manager, but sniffing the traffic between evolution and the imap server, evo is getting a massive filesystem listing (128000 files). Takes about 15-20 minutes just to do this. Once it has sucked the entire filesystem listing locally, it will sit spinning for hours trying to work out what's what.

Basically the subscibe to folders option sits spinning for many hours and I've never yet seen it complete and give me a listing. I suspect some horribly inefficient algorithm is being used when marking/sorting the IMAP folders. I also suspect the evo devs have never tested with an IMAP server with several tens of thousands of files on the filesystem...

---

### Post by rkinder on 2005-11-15
Update:

I sniffed the traffic from thunderbird connecting to the same problemattic IMAP server, and saw via a capabilities query that our IMAP server supports IMAP4r1. I changed my evolution account to use this, then restarted everything, waited ~1 hour, and I now have a working evolution again... funny thing was I wasn't using IMAP4r1 before, but have to do so now for some reason.

Anyway, maybe this will help someone else who is caught in evolution upgrade nightmare hell...

---

### Post by dcstar on 2005-11-16
[QUOTE=rkinder]Update:

I sniffed the traffic from thunderbird connecting to the same problemattic IMAP server, and saw via a capabilities query that our IMAP server supports IMAP4r1. I changed my evolution account to use this, then restarted everything, waited ~1 hour, and I now have a working evolution again... funny thing was I wasn't using IMAP4r1 before, but have to do so now for some reason.

Anyway, maybe this will help someone else who is caught in evolution upgrade nightmare hell...[/QUOTE]
Good work, maybe someone will put this in an Evolution/Breezy FAQ somewhere.

---

