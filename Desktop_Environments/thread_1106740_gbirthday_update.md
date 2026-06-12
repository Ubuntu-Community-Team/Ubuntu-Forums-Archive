---
title: "gbirthday update"
date: 2009-03-26
forum: Desktop Environments
---

### Post by slickvguy on 2009-03-26
In my recent migration from xp to ubuntu, about the only thing I miss is Outlook. Sure, I could use crossover (which I use for quicken) for Outlook, but I don't want to. So I'm using Evolution even though in many ways it's, um, shall we say "lacking". 

Problem: The version of Evolution that comes with Ubuntu 8.10 does not support alarms for birthdays that are linked from the contacts file. I think the latest version of Evolution added this feature, but I'm not sure if it's Ubuntu-safe. 

While searching on this topic, I found a post about GBirthday. Sweet. It's a python script that sits in the taskbar and shows you / alerts you to past and upcoming birthdays. A pretty good effort, but it didn't support anniversaries and had a few bugs in it. I had never used python before, but I decided to take a few hours to teach myself just enough about gtk and python to understand how the gbirthday script worked and then hopefully do the mods. The attached is the result of those efforts.

IMPORTANT: Even though I had used linux years ago, and have infrequently programmed in different languages over the decades, it's only been a short while since I got back into the linux game. I tell you this because I am unsure of what the protocols are for changing other people's code, distributing the changed code, credits, etc. I do not know what the GPL entitles me to (aside from "free software" lol), so forgive me if I am doing this incorrectly. The last thing I would ever do is try to take credit for someone else's work! I hope I'm not stepping on anyone's toes. I think I'll try to contact the author and send him the updates to see what he wants to do. (Change the version number? Put it in a package?) Anyways...with further ado...

My GBirthday Updates:

1) I added support for anniversaries. 
2) The anniversary icons have 2 candles on the cake instead of just 1 for birthdays. This is how you tell one from the other in the main window.
3) I changed the taskbar icon's behavior. No matter how many days back or ahead you set your preferences, the icon will only 'illuminate' if you have UPCOMING birthdays or anniversaries. It'll still blink if there is either event occurring today. 
4) Changed a few labels in en.lang to reflect the script mods. I only changed the labels in the en.lang (English) language file. If someone wants to update the other language files, I'm sure that would be appreciated by our non-anglo friends.
5) Fixed a few small bugs.

I left most of my comments in (which can easily be stripped out since I prefixed each comment with "#svg:")

To "install" simply overwrite the gbirthday script with the new one and replace (or merge) the pics and languages directories with included ones. If you dont' already have gbirthday, just google it and install the .deb package first. Then overwrite with my files. (You might need to use 'sudo' due to permissions).

Enjoy!

---

### Post by tez1982 on 2009-05-31
I'm struggling with GBirthday. It's the perfect little app for me and seems really simple. However whatever I do it always says there are no birthdays due - which is not true???

Anyone got any ideas or had a similar problem? I'm using Ubuntu 9.04 and everything is up to date?

---

### Post by stinger30au on 2009-10-30
heres the homepage if anyone is interested

---

