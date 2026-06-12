---
title: "nepomuk medadata store getting a bit large"
date: 2011-06-07
forum: Desktop Environments
---

### Post by TheSqueak on 2011-06-07
[IMG]http://oi55.tinypic.com/t7y6gm.jpg[/IMG]

Seriously, wtf?

Further investigation shows that it's a single log file that's grown to 137Gb in size, because of several hundred thousand occurences of

"Reference to page with free remap dp = 3840, remap = 3840"


For now i've just disabled nepomuk and deleted the file, but it'd be nice to know what the hell was going on ...

---

### Post by Zorael on 2011-06-07
Could it be related to [this bug](https://bugs.kde.org/show_bug.cgi?id=231989)?

I hesitate to encourage bugtracker spam, but you may want to add a comment there to say the bug is still prevalent in KDE 4.6.x, and perhaps vote for it to (hopefully) attract developer attention.

---

### Post by FormatSeize on 2011-06-07
> **TheSqueak said:**
> For now i've just disabled nepomuk and deleted the file, but it'd be nice to know what the hell was going on ...
Not that I am one to revel in another's misfortune, but I will have to say that the title of this thread in combination with the first line of your post made me chuckle. 
 
As for Nepomuk, and the things that it does in tandem with Strigi and Akonadi, it's just part of KDE, though it seems that it's application is yet to be fully utilized. But being that they are inherently integrated (quite deeply) into KDE, they can't be stopped, but merely tamed if the right steps are taken. 
 
More on this, here's an excerpt from [http://humanreadable.nfshost.com/journal/2011/2011-012.htm](http://humanreadable.nfshost.com/journal/2011/2011-012.htm) about KDE4 as it relates to the service that you are asking about:
 
> There is the malevolent triplet combination of Nepomuk, Strigi, and Akonadi. Yes, malevolent. Home desktop users do not need or want that overhead.
Nobody seems sure yet exactly what a social or semantic desktop should be. Not to mention that after five major point releases the Nepomuk engine still does not do anything useful and consumes CPU cycles and storage space.
Strigi seems like a good idea gone wrong. Creating a searchable desktop seems like a gallant idea, but at what cost?
Yes, disabling Nepomuk and Strigi is straightforward, but for many people requires at least one session of KDE. Disabled yes, removed no. Remove the Strigi package and KDE refuses to start. That is, the Strigi engine can be stopped, but other apps expect to find the associated libraries installed.
Akonadi cannot be removed. For all the promises made about Akonadi, the PIM apps do not yet fully use that backend service.
 
[...]
 
Why is there no option not to install these backend services? With previous KDE4 releases the PIM apps have been running without that backend. From the beginning days of KDE4 users have complained about these three services and the KDE developers continue to plod along without regard for what users want. Although an argument can be made that the KDE developers listen to users, these three services provide fodder that they do not.
 
It's a really good review of KDE4, but it could sound a little biased due to the writer being used to KDE3. I came across this since Slackware 13.1 has KDE4, and I was looking for ways to "tame" it, so to speak.

---

