---
title: "cant decide whether to wipe my HDD or dual boot"
date: 2006-07-20
forum: Desktop Environments
---

### Post by josh_g on 2006-07-20
I'm having problems installing the latest version of Ubuntu linux. Whenever I attempt to make a partition it doesn't work. I am trying to decide whether or not to just switch completely over to Ubuntu from WinXP. All I use the computer for is talking on IM, going on the internet (myspace and watching .WMV, .MOV, and .MPG files), listening to music/updating my iPod, editing videos, and HTML editing (by hand). Should I convert completely? Does Ubuntu have a decent video editing program and a decent text editing program, and does it have plug-ins to be able to view the types of movie files I previously stated?

---

### Post by ColinG on 2006-07-20
Ubuntu has Kino which is a pretty good video editor. It takes a bit of getting used to but it works well enough - and it gets better and better each release.

---

### Post by Lord Illidan on 2006-07-20
As for text editing..

Websites - BlueFish is an excellent tool.

General programming and stuff : Kate is one of the best out there...syntax highlighting, line numbering and all that.

Emacs is almost like an os of its own... and VI is in the same rank.

What is the problem with partitioning? I'd say back up your data first, though...then decide.

---

### Post by Thund3rstruck on 2006-07-21
If you want to switch entirely to Ubuntu them be sure to load XP into a VM session via the [howto]("http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server") this way, in cases of extreme emergency you have a fully functional, native WinXP at your disposal. It's the reason I have been able to stay Win-free for 3 months now (must have my newsleecher)

---

### Post by userundefine on 2006-07-21
You don't do anything I don't do on Linux and didn't do on Windows, sans video editing (I did low-level work with various dvd ripping tools -- haven't had the occasion to try it on Ubuntu yet), and I've fully switched.  There are a host of good source editors out there.  I used Notepad++ on Windows and there's Bluefish, Kate, gPHPedit, Screem, Scite, and more for you to try out.

---

### Post by avtolle on 2006-07-21
One small issue; the OP indicated using comp to visit myspace; since I understand that site upgraded to Flash 9, he'll need to keep access to XP to run Flash 9, for that purpose. Suggestion of Thund3rstruck is appropriate, too.

---

### Post by ColinG on 2006-07-22
> **Thund3rstruck said:**
> If you want to switch entirely to Ubuntu them be sure to load XP into a VM session via the [howto]("http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server") this way, in cases of extreme emergency you have a fully functional, native WinXP at your disposal. It's the reason I have been able to stay Win-free for 3 months now (must have my newsleecher)

What is the difference between vmware server and vmware player which is in the repositories for dapper?

This approach seems ideal to me so thanks for raising it :) 

Colin

---

### Post by Thund3rstruck on 2006-07-22
VMWare server allows you to create VMs, where as I understand VMWare player only allows for using already created VM images. 

I have only personally used server and I'm a huge advocate of it... it's that one thing that was missing from all my other attempts to go total linux and it's already saved me several times.

---

### Post by doobit on 2006-07-22
I've got one computer that runs only Windows XP, one that runs only Ubuntu, and a laptop that dual boots. Partitioning isn't that hard if you follow the advice of using Gparted to do the job before installing Ubuntu, because the installation setup on the live CD doesn't work very well. The computer that's running only Ubuntu was built from the parts of a couple of computers that people gave me. You'd be surprised how many people have older, but perfectly useable computers stuck away in a closet.

---

### Post by ColinG on 2006-07-26
Great howto!. I've now ditched windows and installed Vmware. I will put windows on later. Just played with Mepis in Vmware; I just ran the live cd on the VM. Couple of things:
1) No sound
2) No internet connection (broadband). I have the vm set up as NAT shared with host.

Am I missing something? Is it anything to do with the fact that I'm only running the live cd and should really install?

Help appreciated and thanks.

Colin

---

### Post by SeanHodges on 2006-07-26
> **josh_g said:**
> I'm having problems installing the latest version of Ubuntu linux. Whenever I attempt to make a partition it doesn't work.

What problem are you having with the partitioning? Someone might be able to explain the steps you need to do, if you haven't asked already.

> **josh_g said:**
>  All I use the computer for is talking on IM

Kopete and Gaim are both excellent at this. I use Kopete because it fits well on my desktop, but Gaim is just as good - and is available for Windows as well.

> **josh_g said:**
>  going on the internet (myspace and watching .WMV, .MOV, and .MPG files)

Firefox can handle all this as well as any other browser. You'll find the "mozplugger" package (sudo apt-get install mozplugger) useful for any embedded movies/music.

> **josh_g said:**
>  listening to music/updating my iPod, editing videos

amaroK is the best music player out there! The latest version has good support for iPods,

You can find more about iPod support here: [http://www.ubuntuforums.org/showthread.php?t=103071]("http://www.ubuntuforums.org/showthread.php?t=103071")

> **josh_g said:**
>  and HTML editing (by hand). 

I love using Quanta, it doesnt try to do things for you (if you dont ask it to) but has loads of tools ready for when you care to try them. Kate is a good text editor for this as well (turn on line numbers, and turn off word wrapping).

> **josh_g said:**
>  Should I convert completely? 

If you have the disk space, dual-boot first (with Linux as default boot), then move over completely when you're comfortable with everything in Linux. I don't use Windows at all at home now, and don't miss a thing! I used to have Windows 2000 on standby for converting videos, but I havent done that in a long time. 

> **josh_g said:**
>  Does Ubuntu have a decent video editing program 

Not sure, but I'm sure others will give you some good ones to try... Install all of them, and remove the others once you've found one you like.

> **josh_g said:**
>  and a decent text editing program

Kate is a good simple one. Emacs is great, very fast to use and featureful, but you need to spend some time with it - getting used to the controls. Try them both.

> **josh_g said:**
>  and does it have plug-ins to be able to view the types of movie files I previously stated?

You'll need to install the propietory codecs, this is really easy these days. The easiest is to use this:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

It will ask you a few simple questions, and install everything you should need to play DVD's, movies, etc.

If you want to do things yourself, go to:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

and read through the document.

Good luck!

Sean

---

