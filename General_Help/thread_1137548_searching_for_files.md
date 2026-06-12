---
title: "searching for files"
date: 2009-04-25
forum: General Help
---

### Post by Integral Void on 2009-04-25
so everything was so easy with ubuntu 8.10 and then i had to go and clean install kubuntu 9.04. and there are alot of things i don't know.

how do i associate dolphin with firefox so when i hit open folder for a download it doesn't take me to an application select screen?

where does wine install itself in the file system?

for the love of god how do i search my file system?

and many more coming soon lol =D

---

### Post by DracoJesi on 2009-04-25
> **Integral Void said:**
> so everything was so easy with ubuntu 8.10 and then i had to go and clean install kubuntu 9.04. and there are alot of things i don't know.

how do i associate dolphin with firefox so when i hit open folder for a download it doesn't take me to an application select screen?

where does wine install itself in the file system?

for the love of god how do i search my file system?

and many more coming soon lol =D


I'm not sure as I don't use KDE, but, is there any particular reason you switched from Gnome?

If you grabbed the wrong version, or just need to have Gnome as well, all you have to do is install Gnome and it's corresponding an select Gone via session manager on log in...

---

### Post by SuperSonic4 on 2009-04-25
> **Integral Void said:**
> so everything was so easy with ubuntu 8.10 and then i had to go and clean install kubuntu 9.04. and there are alot of things i don't know.

how do i associate dolphin with firefox so when i hit open folder for a download it doesn't take me to an application select screen?

I don't get what you mean here? Firefox can save to a given folder or wget can always be used?

> where does wine install itself in the file system?

I'm not sure, I think it's ~/.wine but that could be programs and settings

> for the love of god how do i search my file system?

My favourite is using locate from a terminal. You may have to do ```
sudo updatedb
``` first to update the locate database.

Alternatively there is the good old fashioned ctrl+f in dolphin

---

### Post by geirha on 2009-04-25
First time you run wine, it will create a hidden folder in your homefolder. ~/.wine. In there it puts its config, and a basic file hierarchy (~/.wine/drive_c). If you install a windows application using wine, it will be installed under ~/.wine/drive_c by default. Was that what you were wondering about?

Copying the .wine folder from your old homefolder to the new one should work just fine. The menu entries are located under ~/.local/share/applications/, but I don't know how compatible they are with kde ...

---

### Post by Integral Void on 2009-04-26
SOB, the wine file was hidden in my /home/HOSTNAME/ folder
can't figure out why, took awhile to figure it out since the link in the app launcher for browsing c:\ didn't work, trying to use ctrl+f in dolphin was a neat little trick but it couldn't find the files because it was hidden i guess

and no i didn't grab the wrong version, i wanted Kubuntu because it seemed to give me configurablity and to have a higher learning curve than ubuntu. Ubuntu w/ gnome was just too simple to use, go figure, i wanna do everything the hard way right lol

what i was talking about with firefox, if i download something than then when i right click from the Download Manager to "show in folder", it opens up a list similar to windows and asks me what program i should use to accomplish that function.


EDIT: figured it out, used ctrl+F to search for dolphin and linked the file in the usr/bin/ directory and viola it works wonderfully....now how to reformat a PnP device

---

### Post by andrew.46 on 2009-04-27
Hi Integral Void,

> **Integral Void said:**
> ... for the love of god how do i search my file system?

I see you have had a few great suggestions already for this one but I will seize this opportunity to pimp a new guide I have written:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

First in a series of about a dozen I hope but this particular one might put you off on the right foot.

All the best,

Andrew

---

