---
title: "wis to open .txt with gedit &amp; .doc with oo-writer"
date: 2009-10-10
forum: Desktop Environments
---

### Post by NorthernSuze on 2009-10-10
starting a week ago --- I have been having the problem that if I assign gedit to open .txt files it then tries to open the .doc files I want to open in oo-writer and vice versa. (using rt-click >open with other > always open with...)

Forum search seems to deal with the sys > preferences > preferred programs. I did look at [http://ubuntuforums.org/showthread.php?t=1253470&](http://ubuntuforums.org/showthread.php?t=1253470&)

and saw  /etc/gnome/defaults.list which seems to assign the correct applications.
>>application/msword=ooo-writer.desktop
>>text/plain=gedit.desktop

and 

.local/share/applications/defaults.list
      >text/plain=openoffice.org-writer.desktop;gedit.desktop
      >application/vnd.oasis.opendocument.text=openoffice.org-writer.desktop

If I remove the =openoffice.org-writer.desktop; from the first line in the .local/share file it still won't assign .txt to gedit and .doc to oo-writer

If one of you could point me in the right direction, I would be most appreciative.

Suzanne
Ubuntu 8.10 amd64 on Asus n50v

---

### Post by Tclarkie on 2009-10-10
or you could right click on both types of files as set the open with

---

### Post by NorthernSuze on 2009-10-10
> **Tclarkie said:**
> or you could right click on both types of files as set the open with

Thanks, Tclarkies for your quick response.  
When I set one type of file to open with the preferred application, something automatically sets it for the other file type at the same time .... it just wants to open .txt and .doc files with the same application not matter how I try set things.

I can rt-click and open with each time but that is a pain. It is like somebody is trying to make decisions for me >> one of the reasons I left Windows >> to take control of my own computer! lol

Suze

---

### Post by Tclarkie on 2009-10-11
upgrade to 9.04

---

### Post by mcduck on 2009-10-11
I don't really even remember there ever being option to right-click->Open With->Always Open With in Ubuntu.

The way to set the default applications is right-click->_Properties_->Open With.

---

### Post by NorthernSuze on 2009-10-11
> **mcduck said:**
> I don't really even remember there ever being option to right-click->Open With->Always Open With in Ubuntu.

The way to set the default applications is right-click->_Properties_->Open With.

Thank you, mcduck for jogging some brain cells loose.  You are right Nautilus doesn't have the "always open with" and the files open properly in their respective programs...

I have been using Thunar 0.9.3 file manager for the most part: opens a terminal session in the directory you want do some command line work in; and it handles thumbnails for graphics work much better than Nautilus. (just doesn't accept different applications for .txt & .doc files!) 

I will take this to the thunar people.  My apologies for not realizing where exactly my problem lay and looking for a solution here.

Suze
Again thanks I would be lost without all the terrific helpers here 
(do I mark this solved since it isn't basically Ubuntu problem?)

---

### Post by NorthernSuze on 2009-10-11
> **Tclarkie said:**
> upgrade to 9.04

It is on my list to do....somewhere...if I can find my list... <grin>

And here it is fall already :P

Thanks again for your help, Tclarkie, I love travelling out the other side of a forum post in a less confused state of mind.

Suze

---

### Post by mcduck on 2009-10-11
> **NorthernSuze said:**
> Thank you, mcduck for jogging some brain cells loose.  You are right Nautilus doesn't have the "always open with" and the files open properly in their respective programs...

I have been using Thunar 0.9.3 file manager for the most part: opens a terminal session in the directory you want do some command line work in; and it handles thumbnails for graphics work much better than Nautilus. (just doesn't accept different applications for .txt & .doc files!) 

I will take this to the thunar people.  My apologies for not realizing where exactly my problem lay and looking for a solution here.

Suze
Again thanks I would be lost without all the terrific helpers here 
(do I mark this solved since it isn't basically Ubuntu problem?)

So you are using Thunar, not Nautilus? If you still have Nautilus installed you could use it to set the default programs, the setting should be respected regardless of what file manager you use.

Also there's a package called "nautilus-open-terminal" which adds option to open a terminal in current directory into the right-click menu in Nautilus & Gnome desktop.. :)

---

### Post by NorthernSuze on 2009-10-11
> **mcduck said:**
>   So you are using Thunar, not Nautilus? If you still have Nautilus installed you could use it to set the default programs, the setting should be respected regardless of what file manager you use.

That is the strange part: the settings act correctly in Nautilus but are still confused in Thunar. I am searching for a thunar configuration file. Hopefully that will tell me something.

> **mcduck said:**
>  Also there's a package called "nautilus-open-terminal" which adds option to open a terminal in current directory into the right-click menu in Nautilus & Gnome desktop.. :)

Perfect! Thanks for pointing it out. There are so many good things out there, it is hard to keep up with it all. I love Linux :) 

Suze in chilly, but sunny northern BC Canada

---

