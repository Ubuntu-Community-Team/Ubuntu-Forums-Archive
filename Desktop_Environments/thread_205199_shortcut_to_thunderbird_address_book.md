---
title: "shortcut to thunderbird address book"
date: 2006-06-28
forum: Desktop Environments
---

### Post by oliwally on 2006-06-28
I know it's possible to create a shortcut to the thunderbird address book - I did it in breezy. But I can't quite remember how I did it. I found this:

> SHORTCUT TO THUNDERBIRD ADDRESS BOOK

Many thanks for the excellent site, long may it continue. When I used Outlook Express I had a short cut on my Desktop to my Address Book, since changing to Thunderbird I can't find a way to create a Desktop short cut to the Thunderbird Address Book. Is it in fact possible to do this?

A. Thanks for the support and those kind words Kenny, and you’ll be pleased to know that it is indeed possible. But first, for those of you still using Outlook Express, to save you writing in to ask how it’s done, all you have to do is go to Start > Programs > Accessories, right click on the Address Book icon and select Send To > Desktop as shortcut and it’s done.

Now back to Kenny’s request, and it’s almost as simple. Right-click into an empty area of your desktop, select New > Shortcut and in the ‘Type the location…’ box copy and paste the following command

"C:\Program Files\Mozilla Thunderbird\thunderbird.exe" -addressbook

Don’t miss the quote mark in front of c:\, and change the path as necessary if your copy of Thunderbird is on another drive. Click Next and keep or change the shortcut name and your new Address Book shortcut will appear on the desktop

Found at [http://www.rickmaybury.com/fffpages/fff05/nov05.html](http://www.rickmaybury.com/fffpages/fff05/nov05.html)

But somehow I can't make it happen in dapper. I'm not sure what I'm doing different. I think in Breezy I simply made a copy of the launch button and added the '-addressbook' to the end of the command and it worked. This isn't working this time. Would it have something to do with 'kicker' linking to thunderbird? I've tried several other ways (through /usr/bin and so forth) but to no avail.

How is it done?

---

### Post by aysiu on 2006-06-28
You're trying to link to a Windows Thunderbird address book or a Ubuntu Thunderbird addressbook?

---

### Post by oliwally on 2006-06-28
> You're trying to link to a Windows Thunderbird address book or a Ubuntu Thunderbird addressbook?

The Ubuntu Thunderbird address book. I was just using this as an example of how the "-addressbook" can be added to the end of the executable command. I didn't actually use the whole windows path - I tried to find the path to the thunderbird executable in my Kubuntu file structure. 

When I look at the properties of my current thunderbird launch button I see that it's path is /home/oliver/.kde/share/apps/kicker/mozilla-thunderbird. Adding the '-addressbook' to the end of this does not work, although I'm quite sure that's what I did in breezy.

---

### Post by oliwally on 2006-06-28
I did it !!!!!!

I forgot to add the space between 'mozilla-thunderbird' and '-addressbook'.

So, in the end all I needed to do is 'Create a New Link to Application' (KDE) and in the 'command' space stick in 'mozilla-thunderbird -addressbook', not forgetting the space. 

Thanks for your help though.

---

