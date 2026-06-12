---
title: "Need some good questions ansewered"
date: 2006-06-16
forum: Desktop Environments
---

### Post by kcallstar7 on 2006-06-16
well first off im very new to linux and am very much in love with it...

first... what is all this dapper talk vs brezzy talk... are the both unbuntu and is unbuntu standard 64bit...

on that note what is 64 bit really do...

can i get flash to work with firefox...

the kernel is my os right? should i upgrade it or does unbuntu do that automatically... if it does the does a new kernal leave me alone when it comes to installing the programs that were built for the prior kernal?

finally why cant i get my dv4000 wifi working... ive tried ndiswrapper with my default windows broadcom drivers and still dont manage to get it to work...

love unbuntu and really love all the support all guys give us (newbies) hope... i relize the airplanes were'nt built to swim in water... as so programs cant work on linux as well... i wish all people who get so frustrated with linux could understand this... and also understand the phenominal solutions giving here by some of the gueniess minds that go so unappreciated... sry had to get that last paragraph in... any help is good help... 

im converting so show the path i need to follow and eventually i shall lead...

---

### Post by BitTorrentBuddha on 2006-06-16
1) Dapper is the successor of Breezy, Dapper was officially released about two weeks ago, Breezy about 8 months ago. They are both available for 64-bit systems.

2) 64-bit processors are capable of handling larger numbers than 32-bit processors, it is undoubtedly going to replace 32-bit processors some day... But right now they're more of an inconvenience than anything else because very few things apply the power behind 64-bit processors. If you're really interested in going in depth, [this](http://www.softwaretipsandtricks.com/windowsxp/articles/581/1/The-difference-between-64-and-32-bit-processors) may prove a good read.

3) Yes. [The automatix script](http://ubuntuforums.org/showthread.php?t=190025&highlight=automatix+dapper) is a new users best friend, and will install several other essentials including flash.

4) Ubuntu handles all upgrades (assuming you are connected to the internet.) It is best to not meddle with anything involving the kernal unless you are absolutely sure you know what you're doing (or it's a test machine and you're looking for a learning process.)

5) Beats me, but 4 out of 5 ain't bad.

---

### Post by yager on 2006-06-16
[QUOTE=kcallstar7]well first off im very new to linux and am very much in love with it...

first... what is all this dapper talk vs brezzy talk... are the both unbuntu and is unbuntu standard 64bit...

on that note what is 64 bit really do...[/QUOTE]

Breezy and Dapper are the names of the most recent versions.  Like Windows 95 and 98.  The 64 bit is for people who have a 64 bit AMD processor.  It allows them to take advantage of that processors specific abilities vs. the standard 32 bit kernel.

[QUOTE=kcallstar7]can i get flash to work with firefox...[/QUOTE]

Download the Automatix tool and it will set everything up for you so you have all of the right codecs and other tools to use in your browser as well as a bunch of useful programs.  You will find the link on this forum under the 3rd party discussions.

[QUOTE=kcallstar7]the kernel is my os right? should i upgrade it or does unbuntu do that automatically... if it does the does a new kernal leave me alone when it comes to installing the programs that were built for the prior kernal?[/QUOTE]

This is a hard one.  The kernel is the core of the OS.  An operating system can be defined at multiple levels.  If you have seen DOS before Windows, this is what the kernel would look like without the X layer and GNOME or KDE which provide a graphical front end.  Some like to include this graphical layer in the definition of the OS since it controls how you interact with the computer and also has an impact on what programs that you can run on top of the kernel.  Technically, you only need the kernel and the drivers for the hardware to have a viable operating system.

[QUOTE=kcallstar7]
finally why cant i get my dv4000 wifi working... ive tried ndiswrapper with my default windows broadcom drivers and still dont manage to get it to work...
[/QUOTE]

I will have to go to the audience for this last one.  I have not had to resort to a wifi setup.

---

### Post by H.E. Pennypacker on 2006-06-16
> first... what is all this dapper talk vs brezzy talk... are the both unbuntu and is unbuntu standard 64bit...

Ubuntu gives its versions (releases) names.  Each official release is given a name. Breazy is an older version.  Dapper Drake is the current version.

> 
on that note what is 64 bit really do...

That's a completely different question, and its not a question that necessarily needs to be asked on a Linux messageboard, because anyone would be able to answer that question.

Whenever you have a question on the Internet, always check with useful resources such as Google and Wikipedia.  For example, if you had checked out Wikipedia, you would have found this:

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

> 
can i get flash to work with firefox...

If you checked out Ubuntu.com and used its search feature, you would have found the following page which answers your question:

[http://www.ubuntu.com/support/faq?highlight=%28flash%29](http://www.ubuntu.com/support/faq?highlight=%28flash%29)

You could also have found the answer by using Firefox's official website.

> the kernel is my os right?

The answer to that is also available on Wikipedia by finding out what a kernel is, and what an operating system.  You could also have done a search on Google, which would have, for example, shown this:

[http://www.daniweb.com/techtalkforums/thread19037.html](http://www.daniweb.com/techtalkforums/thread19037.html)

---

### Post by kcallstar7 on 2006-06-16
you guys really rock when it comes to this stuff... i have unbuntu on both my lappy and my dell desktop (which is my girlfriends ... so yeah i got me a test machine) but have unbuntu so do i have dapper or brezzy... or are they all 3 diff. then debain unbuntu... if they are should i upgrade to one or the other given my hardware prefrence that i will half to work around... my laptop supports 64bit flawlessly i fell i can stick with it as well as run 32bit on it, given the fact that my 32bit programs will be a mininmum limit...

---

### Post by johnc4510 on 2006-06-16
enter this command in your terminal:
cat /etc/issue
Your terminal is here: Applications>Accessories>Terminal
Type in exit to close

---

