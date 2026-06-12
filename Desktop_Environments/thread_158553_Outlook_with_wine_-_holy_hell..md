---
title: "Outlook with wine - holy hell."
date: 2006-04-11
forum: Desktop Environments
---

### Post by hotani on 2006-04-11
I'm running 6.06 here at work, and only need one windows app to avoid dual booting: Outlook. I need Outlook because we're using .pst files (pronounced "psssst!") and microsoft post office (don't laugh! we're upgrading to Exchange soon).

First, the documentation for Wine is, well, 'lacking' to put it nicely. What's worse than that? The documentation for actually installing an application to run on Wine. Fortunately, the wine package was in Synaptic so I got that going pretty easy. Then I looked around for how one would actually get Outlook running... and looked.... and looked... still looking......... somewhere it said "just install it!" So I tried that, and now it barks back "this feature requires MS IE 4.0 or later... etc..." and shuts down. 

So I try to install IE6, no go. I get the installer screen which shortly crashes out.

So I try the [package install](http://www.tatanka.com.br/ies4linux/en/instructions/) script which gave me a working IE6 (wow.), but (surprise!) Outlook doesn't know it's there and still comes back with the same error. 

I don't even need the whole office suite, just Outlook. I don't even like outlook, but as many of you know, it is a necessary evil right now. Maybe in a couple months when we get exchange going I can use evolution (fingers crossed).

---

### Post by art on 2006-04-12
I don't know for wine, but maybe you could get it working with crossover office. It is a commercial application, but if you absolutelu need it... You can try free for 30 days. Look here:
[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by Zerocool10482 on 2006-04-12
I hope you can us evolution but good luck?

---

### Post by Sef on 2006-04-12
Actually Kmail would be better.  It can read  Outlook Express files without an interpreter, and I would suspect it would do the same for Outlook.

---

### Post by anthro398 on 2006-04-12
I can, but don't, use Outlook via [Crossover Office]("http://www.codeweavers.com/").

---

### Post by KingBahamut on 2006-04-12
Memory serving correctly, ol2mbox and possibly readpst can move pst files from pst to mbox with relative ease. 

[http://alioth.debian.org/projects/libpst/](http://alioth.debian.org/projects/libpst/)

---

### Post by hotani on 2006-04-12
Thanks for the responses, I'll try some of those and post back how it goes.

Again, I'm not using Outlook by choice - Evolution would suit me fine but our mail setup here at work pretty much requires it. :(

---

### Post by kisiyel on 2007-03-28
I tried that "readpst" converter but it can not read outlook 2003 or newer pst files, then I installed crossover office with Office 2003. With crossover 6.0.1.1.deb, Office 2003 can not connect to internet, but you can open .pst files in your NTFS partition. Lastly I found outlook 2000 from a friend and tried, this time I could not able import .pst  files.

Consequently, Evolution works great. Thanks God for its simplicity...

---

### Post by Hendrixski on 2007-03-28
:-) dont worry, you won't be using .pst files for long.  One person will upgrade to office 2007, and none of those file formats are backwards compatible.  Everyone will have to scour the Microsoft.com website for hours to find the readers to update their office XP... yeah.  Their starting to go through that hell at my office now... so I'm actively telling everyone to just switch to platform independent tools, because the desktop is becoing a thing of the past and everything is online and interoperable.  :)

---

### Post by hotani on 2007-03-29
Wow - zombie thread!

I ended up with an oddball solution to this issue: we started our migration to exchange (I had nothing to do with it!) which [some versions of](http://www.ubuntuforums.org/showthread.php?t=356658) Evolution can connect to. I had a drone win2k machine checking my MS post office mail and dumping it to the exchange server which i could access from my ubuntu box. Not ideal, but it worked.

Now we have switched to exchange completely and I don't need the 'outlook server' anymore which is nice. Now if only I could get evolution in Feisty to connect to exchange (see link above). :(

---

### Post by chocbar31 on 2007-03-29
Follow the Novell link and it shows the method for connecting to Exchange.

Hope this helps.

[http://ubuntuforums.org/showthread.php?t=389369]("http://ubuntuforums.org/showthread.php?t=389369")

---

### Post by Snowmayne on 2007-03-29
What I ended up doing was opening up Outlook Express in windows, migrating my mailboxes there (over 4 gigs of mail i never read anymore) and then used Kmail to migrate OE mailboxes. Fastest and easiest way to move the .pst files over. The address book was just exported to .csv from outlook and imported into Kmail. 
Longest part was having to define all the headers (some of which didn't have equivalents, like assistant's phone number), but overall including reboot took less than 15 minutes, was relatively painless and didn't require 3rd party apps to be installed

---

