---
title: "File Explorers"
date: 2005-12-20
forum: Desktop Environments
---

### Post by dk_pa on 2005-12-20
Well, I have just switched all my partitions and files over from Windows so I am officially 100% Linux.  =)  It has been a bit of a process tho, and I learned a lot and become pretty good at somethings...I have also found out a bit I like / dont like.

One thing I really don't care for is Nautilus.  I have to admit that I like Windows File Explorer A LOT better.  I don't know enough about Nautilus to know if you can put it in a similar view or not.  That would be helpful =)

I remember using Xandros they have a REALLY nice file explorer.  I think it was a hacked up version of Konquerer tho.  It would allow up to 4 Panes and was pretty easy to use.  Can I use Konquerer on Gnome? 

Anyway I install XNC but I need to get the Helvectica font I believe (that is what terminal seems to show).  

So what does everyone use for file explorers.  YES, I know there is the terminal and I use it quite a bit but I would like to have a nice File Explorer (at least one I like) too.  Not really knocking Nautilus it's just not my style =)

---

### Post by audax321 on 2005-12-20
Don't know if you tried this or not, but you can make Nautilus look like this:

[IMG]http://www.dieburnbot.com/file_browser.png[/IMG]

If you look in the sidebar, at the top is a drop-down box where you can select "Tree" and it will display the tree much like in Explorer.

Also, Nautilus in Breezy doesn't display a location bar by default, but if you want to see it really fast you can just hit CNTRL+L to view it.

---

### Post by dk_pa on 2005-12-20
Ahhh..I must have missed that (obviously).  I will try that out when I get home.  That looks like what I want or close to it.  Thanks for the tips.  Like the colors btw.

I believe I will help promote bunny now =P

---

### Post by dartakaum on 2005-12-26
have you tried xfe ?

i'm also searching for one good file explorer.

now i'm using xfe and konqueror to acess to my network.

i don't like nautilus cause always change my desktop and starts some process and stuff...

if someone got one better file explorer, say please. :)

---

### Post by Bou on 2005-12-26
I don't remember much of explorer, but I fail to see any remarkable differnces between it and nautilus.

[IMG]http://www.saunalahti.fi/wpoet/scr/scr-xp-explorer.jpg[/IMG]

[IMG]http://img203.imageshack.us/img203/6904/pantallazoestopalacalleestuyan1.png[/IMG]

---

### Post by dk_pa on 2006-01-19
That is just the default view above (at least I think it is).  I don't use it anywhere near like that.  WAYYY too clumsy and counter-productive for my tastes.  This is basically what I was talking about.  I have things just about right now on Ubuntu for that tho =)

[IMG]http://www.drdispatch.com/help/explorer.jpeg[/IMG]

---

### Post by ardchoille on 2006-01-19
There are other file browsers out there. I have used gnome commander (I believe it's in the repos), emelfm2 (also in the repos) and tux commander. These are nice file browsers, IMHO.

---

### Post by dk_pa on 2006-01-20
Thanks for the suggestions I'll check them out.

---

### Post by John Jason Jordan on 2006-01-20
[QUOTE=ardchoille]There are other file browsers out there. I have used gnome commander (I believe it's in the repos), emelfm2 (also in the repos) and tux commander. These are nice file browsers, IMHO.[/QUOTE]
I have Breezy-64. I found emelfm in Synaptic, but not emelfm2. Anyway, I installed it. But I can't figure out how to launch it. It did not install a menu item in Applications. From the command line "emelfm" returns "command not found."

Synaptic says it is installed, but how do I launch it?

---

### Post by reidar on 2006-03-25
I have the same problem in Breezy. Have installed emelfm, but I cannot find a way to launch it. 'which emelfm' doesn't display anything, although 'dkpg -l | grep emelfm' proves that it has been installed. Appears that no launcher has been made. Nothing of emelfm in /usr/bin. 

-r

---

### Post by John Jason Jordan on 2006-03-25
I have tried all the file managers listed in this thread and they all suck one way or another. Nautilus ate 14 GB of mp3 files one day, after which I banned it from my computer. Konqueror is OK except that it takes forever to launch and it thinks it is a web browser. (Thanks, but no thanks -- I have Firefox for that.) I tried Endeavour2, but its inteface is hideous -- gtk1.2, and I can't get the right libraries installed on my Breezy-64 computer so I can change the interface. Krusader isn't bad, ditto for gnome commander, but neither can have a tree in the left panel and the files listed in the right panel. All you can have is two identical panels. I also tried several others but either they wouldn't install or, like emelfm, I couldn't figure out how to launch them. There is a more or less complete list here:

[http://applications.linux.com/article.pl?sid=05/02/23/2226202]("http://applications.linux.com/article.pl?sid=05/02/23/2226202")

Right now I use Konqueror as my main file manager. I have tweaked it to get it to launch a little faster, but it's still slow, especially the first time it is launched. And this is on a laptop which is constantly being rebooted. I also use Krusader which I run as root so I can use its mountman feature (not available in Konqueror).

I don't understand why file managers have to be so sucky on Linux. Maybe it's because Linux-heads are so desperately trying to be "not-Windows" that they refuse to copy features from Windows Explorer. Never mind the fact that Microsoft spent gazillions on user research to find out what people wanted. Oh well. I love everything else about Linux!

---

### Post by outofnicks on 2006-03-25
Myy emelfm was installed in /usr/X11R6/bin/ , took me a while to find it until I learned to do"updatedb" before using the locate command. I had to open it with sudo at first, until I put it in the main menu.

Filerunner is another two-pane FM, almost identical to emelfm.

Anyone know if there's an icon for emelfm? I can't seem to find it.

---

### Post by John Jason Jordan on 2006-03-25
[QUOTE=outofnicks]My emelfm was installed in /usr/X11R6/bin/ , took me a while to find it until I learned to do"updatedb" before using the locate command. I had to open it with sudo at first, until I put it in the main menu.

Filerunner is another two-pane FM, almost identical to emelfm.[/QUOTE]
Thanks for pointing out where it was. I installed it again and this time was able to launch it. However, it is like gnome commander and most of the others -- two identical panels. I want a file manager with the tree in the left panel and the file list in the right panel. In other words, when I click on a folder in the left panel the files in that folder appear in the right panel. As far as I know, the only file managers that do that are Nautilus, Konqueror and Endeavour2. :(

---

### Post by simon_is_learning on 2006-03-25
as a Xubuntu User running a low-end machine I find Thunar file-manager nice.

[http://thunar.xfce.org/index.html](http://thunar.xfce.org/index.html)

version 0.2.2 =)

---

### Post by akshaysrinivasan on 2006-03-25
Try evidence and Xfe and rox-filer

---

### Post by John Jason Jordan on 2006-03-25
[QUOTE=akshaysrinivasan]Try evidence and Xfe and rox-filer[/QUOTE]
I already tried rox-filer and it can't show the tree on the left and the file list on the right. It has just two identical panels. Plus, it's hideous.

Xfe is very nice and almost does the job for me. It has two missing parts -- it doesn't have a mount facility, and it can't see my network. The latter is especially important. Without the ability to see the network I can't move files back and forth between my Windows desktop and my Linux laptop.

As for thunar, it is not listed in Synaptic on my 64-bit Breezy computer. :(

---

### Post by audax321 on 2006-03-26
.... nm wrong thread :)

---

