---
title: "Nautilus `replace file' dialog - can it show more information?"
date: 2009-03-19
forum: General Help
---

### Post by TobyReynolds on 2009-03-19
When copying files from one folder to another, I am wondering if there is an add-on, or even a current setting that I haven't found, to make the replace file dialog in Nautilus show more information about files that already exist in the destination directory, e.g. time and date last modified, size? This is so I can make a more informed decision about whether to overwrite or leave them in place.

Any suggestions?

Toby

---

### Post by Brucevdk on 2009-04-18
At the moment the current dialog is all there really is. See: nautilus-file-operations.c:4004.

Though I think the general idea of having more information (such as the affected directories/files) would be nice I'm not yet tempted to actually go out and implement it (i.e. scratch an itch). However, what you could do is create an interesting GUI mockup that shows how merge information would be depicted and use that as a starting point to discuss it on the [Nautilus mailing list](http://mail.gnome.org/archives/nautilus-list/). If you want you can use the [Nautilus wiki](http://live.gnome.org/Nautilus/Ideas) over at GNOME Live! as a brainstorm area.

For ideas you could take a look at [Kompare](http://www.caffeinated.me.uk/kompare/) or [Meld](http://meld.sourceforge.net/) which both have functionality to compare directories. Or perhaps see how other file managers do this.

I'm subscribed to this thread and also to the Nautilus mailing list so if anything comes up I'll be sure to notice it.

---

### Post by StuartN on 2009-04-18
Meld is a wonderful tool, especially when comparing entire trees, but even Meld doesn't show file properties like timestamp. It shows which is most recent, but not the actual dates.

---

### Post by Brucevdk on 2009-04-18
Thought I'd work on a mockup for the merge dialog so I started by doing some research looking in the area of diff viewers (Meld, Kompare, KDiff) and synchronization utilities.. I eventually came across a proprietary diff viewer named [DiffDog](http://www.altova.com/features_directory_diffdog.html) which has an interesting method of displaying directory diffs and took a lot of inspiration from that.

Before:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=110237&stc=1&d=1240088038[/IMG]

After:

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=110239&stc=1&d=1240088897[/IMG]](http://ubuntuforums.org/attachment.php?attachmentid=110234&stc=1&d=1240087754)

*Click on the thumbnail for a larger version (it's a little larger).*

It's not done yet and I'm not sure if I'm going to implement it but I thought I'd take a look and see what would be possible. I might look into seeing if it's possible to also have a single column view next to dual columns. I also have to take a look into seeing if it could be made a little bit more simplistic for just replaces.

---

### Post by TobyReynolds on 2009-04-21
Hi, Thanks for the replies. Interesting mock-up Brucevdk -- I like the idea, although it's perhaps a little more complicated than the everyday user would probably want. If you do start anything on the Nautilus mailing list or wiki, please post the URL here as I'd be interested to follow it.

Searching Google, there have been many discussion about this in the past, for example [this bug report]("https://bugs.launchpad.net/nautilus/+bug/136702"). And [this discussion]("http://www.archivum.info/usability@gnome.org/2008-04/msg00035.html") which features some nice ideas and more simplified mock-ups for the Replace dialogue, but I don't think any of them have been taken to completion.

---

### Post by Brucevdk on 2009-04-25
> **TobyReynolds said:**
> And [this discussion]("http://www.archivum.info/usability@gnome.org/2008-04/msg00035.html") which features some nice ideas and more simplified mock-ups for the Replace dialogue, but I don't think any of them have been taken to completion.

I discussed it with Cosimo and it turns out that that isn't a mock-up, it's actual working code. He hasn't implemented any of the changes mentioned in that thread yet though. He said it's on his todo-list for 2.28, but obviously also has some other things he'd like to work on. He hasn't published the relevant code yet (it's in a private branch) but he told me that if I wanted to work on it he'd be fine with it.

I'll keep you posted.

For lurkers, here's the screenshot of the dialog from the thread linked above:

[[img]http://ubuntuforums.org/attachment.php?attachmentid=111042&stc=1&d=1240699002[/img]](http://mail.gnome.org/archives/usability/2008-April/msg00034.html)

---

### Post by tonywhelan on 2009-05-22
> **Brucevdk said:**
> I discussed it with Cosimo and it turns out that that isn't a mock-up, it's actual working code. He hasn't implemented any of the changes mentioned in that thread yet though. He said it's on his todo-list for 2.28, but obviously also has some other things he'd like to work on. He hasn't published the relevant code yet (it's in a private branch) but he told me that if I wanted to work on it he'd be fine with it.

I'll keep you posted.

For lurkers, here's the screenshot of the dialog from the thread linked above:
\


Nautilus could certainly use this sort of improvement. I think it would be useful to have the full path of both files shown in the dialog, so the user is clear what is going where. Might look a bit untidy though.

---

### Post by markntaylor on 2009-06-13
It's probably heresy to say this; but this is an area where Windows still does it better!
I'm probably feeling a bit sore having just lost an entire afternoon's work by overwriting a new file with its older version; I would have been much less likely to have done this with information on dates and times in the dialogue box.

---

### Post by manolomanolo on 2009-12-07
Have you ever used **[SuperCopier]("http://supercopier.sfxteam.org/?q=node/35")** for windows?
Nautilus should integrate functionalities of that kind, at least:
[LIST]
[*]queuing different file transfers, instead that running in parallel
[*]non blocking copy: queue at the end of the file copy list all of those dirs and archives that requiere user actions (overwrite, skip, merge)
[/LIST]

---

### Post by sheck on 2010-01-16
Is there any news on this ?

Every time I need to merge directories, I have to load Windows XP to do it. It's way too dangerous to do it with Nautilus for important files.

---

### Post by jamesisin on 2010-01-16
A tool like rsync might be useful here.  Probably be easier than starting up Windows.

---

### Post by JohnnyC35 on 2010-03-01
I started using Thunar because of Nautilus' short coming with moving movie files. With either canceling or running out of space I have a small collection of partial movie files. Now that I can finally merge them onto a 1Tb dive I was getting the ambiguous replace message in Nautilus, Thunar at least gives file size. Another plus with Thunar is the red line across the top that says your using a root account, when you are, incase you have root and non root directories open.

---

### Post by agestrada on 2011-06-14
Showing dates when replacing files is one of many simple productivity issues where other OSes are far better than Ubuntu.   The idea of having to use other file managers besides the default one (i.e. Nautilus) is out the question. Hope to see this corrected in the future.

---

