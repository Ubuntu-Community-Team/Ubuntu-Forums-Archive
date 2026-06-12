---
title: "&gt;&gt;&gt;    I'm lost !!"
date: 2005-10-26
forum: Desktop Environments
---

### Post by bilal3000 on 2005-10-26
Two days ago I decided to go ahead and making the big step : I removed win xp from my computer installing ubuntu. But now I'm totaly lost : I encounter problems such as:

- I'v got a "filesystem" hard disk name (where ubuntu in installed) where It's impossible to copy any folder, so installing software is not possible. But I can copy things into the "personal files" directory or on the desktop, what's wrong?:confused: 

- Ubuntu is installed in a partition where there's 13Go of free space but I have messages telling me that there's no available space. And when I check this with the monitor system tool, it tells me that the hard disk is used by only 12%...:confused: 

- What is the equivalent directory of program files where I can found all software that are installed?:confused: 

- How Can I install softwares with tar.gz extention? I read something about compiling (./configure, make su, make install), I tried it but it doesn't work at all:confused: 

- How can I install this : [http://gnome-look.org/content/show.php?content=19714](http://gnome-look.org/content/show.php?content=19714) ?:confused: 

My God, every simple thing i have to do is like climbing a mountain

Have I took the good decision?

Really, I'm lost! :???:

---

### Post by GeneralZod on 2005-10-26
[QUOTE=bilal3000]
Have I took the good decision?

Really, I'm lost! :???:[/QUOTE]

I'd never, ever advise someone to simply ditch XP in favour of Linux without at least spending a month or so dual-booting.  Thankfully, quite a lot of your complaints have solutions, I think, so you shouldn't worry too much :)

I'm at work at the moment so I can't reply at length, but I'm sure someone will beat me to it, anyway :)

Most of your problems occur because you are expecting Linux to behave in exactly the same way as Windows, when in fact they are worlds apart - installing software and the way installed appications are handled, in particular, is worlds apart.

---

### Post by Xian on 2005-10-26
Before you start trying to install themes I would advise you read a little on some of the topics that you've raised. There is a lot of documentation available and here are some places to start:

[What Goes Where in Linux](http://www.lesbell.com.au/Home.nsf/0/87cd60bdf18a2a75ca256caf001594b4?OpenDocument)
[Linux Documentation Project](http://www.tldp.org/)
[Linux How-To's](http://howtos.linux.com/howtos/HOWTO-INDEX/categories.shtml)
[Rute's Linux Tutorial](http://rute.2038bug.com/index.html.gz)
[Ubuntu User Documentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by Appolusionist on 2005-10-26
> - I'v got a "filesystem" hard disk name (where ubuntu in installed) where It's impossible to copy any folder, so installing software is not possible. But I can copy things into the "personal files" directory or on the desktop, what's wrong?:confused: 
 
When you are installing some programs, you have to either use Synaptic or by using the sudo command so it will give you root access via a terminal window. Take a look at the [Ubuntu Guide]("http://ubuntuguide.org"). But be mindful that the guide is based on Hoary 5.04, but most of it still applies to Breezy 5.10.
 
> - Ubuntu is installed in a partition where there's 13Go of free space but I have messages telling me that there's no available space. And when I check this with the monitor system tool, it tells me that the hard disk is used by only 12%...:confused: 
 
Can you give some more info about the messages you are getting?
 
> - What is the equivalent directory of program files where I can found all software that are installed?:confused: 
 
You can look under Applications for a basic picture of what apps you have installed. A more thorough way is by using Synaptic and sorting the list by what is installed.
 
> - How Can I install softwares with tar.gz extention? I read something about compiling (./configure, make su, make install), I tried it but it doesn't work at all:confused: 
 
What program are you trying to install? Have you checked to see if it was listed in Synaptic?
 
> - How can I install this : [http://gnome-look.org/content/show.php?content=19714]("http://gnome-look.org/content/show.php?content=19714") ?:confused: 
 
Download the theme to your pc. Then from the Gnome Panel Go to Syste->Preferences->Theme. You can then install the theme from here and then select the theme from the list.
 
>  
My God, every simple thing i have to do is like climbing a mountain
 
Have I took the good decision?

 
I agree with **GeneralZod **about taking an instant dive into Linux head first, unless you have the time and the patience. I had the time and it forced me to learn faster and more without having Windows readily available to use.

---

### Post by nolan43 on 2005-11-01
I'm almost like the guy at the geginning of this thread, I've dual booted with 3 other distro's before I wiped XP pro from my Vaio. An it's because of Ubuntu and this community; I worry less, read more, and keep my fingers moving. Much needed info.

Thanks.

---

### Post by Buffalo Soldier on 2005-11-01
[QUOTE=bilal3000]How Can I install softwares with tar.gz extention? I read something about compiling (./configure, make su, make install), I tried it but it doesn't work at all:confused:[/QUOTE]Have you installed all the neccesary files to compile a program? The command is:```
sudo apt-get install build-essential
```

---

