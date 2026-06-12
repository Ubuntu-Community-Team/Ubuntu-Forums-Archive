---
title: "How do I install programs"
date: 2005-01-30
forum: Desktop Environments
---

### Post by Chrisb319 on 2005-01-30
It's just so confusing.

---

### Post by Quest-Master on 2005-01-30
apt-get.

;)

---

### Post by mendicant on 2005-01-30
Well you use a package manager.  Aptitude or synaptic are good choices for front ends to use.  Then, if you know the package name, you can search for and install that package.  The packages are also categorized, so you can use that to search within the package manager front end.

Are you having trouble installing or trouble finding programs?  Any specifics?

---

### Post by Chrisb319 on 2005-01-30
Well I can't play MP3's so I look around the forums and find this plugin, I download it and have no clue how to istall it. I want to install a P2P software and I have no clue what they are telling me to do.

---

### Post by mendicant on 2005-01-30
What plugin are you trying to use?  You can install a lot of different programs for mp3s, including xmms and rhythmbox and mpg321.  Use aptitude install xmms, for instance.

For the p2p software, what is its name?  It will always be easier to install from the package manager than from source code, or an RPM, or anything that you can typically download from a website.

---

### Post by Chrisb319 on 2005-01-30
gstreamer-mad

I'm not gettting anything  :-(

---

### Post by DirtDawg on 2005-01-30
I think you may be looking for the command line command? Let's say you have a package called toastandjam.deb in your /usr/home directory (these are both ficticious examples!). You open your command console window, then you change directories to that directoy like this: 'cd /usr/home' (without the quotes, of course) (cd= 'change directory'). 
  If you enter: 'ls', (short for 'list') you'll get a list of all the crud in that folder. You'll see "toastandjam.deb" in there along with whatever else you have floating around in that folder. 
  Then you enter: 'dpkg -i toastandjam.deb'. (Stands for "debianPackage -install toastandjam.deb")
  You'll see the command console spew some BS for a second or a minute or a few minutes or whatever. Everything should install fine. If it doesn't, you're probably missing libraries, which is another matter entirely, but not a big deal. 
  Hope this helps!

---

### Post by Chrisb319 on 2005-01-30
How do I get to the command console. :cry:

---

### Post by mendicant on 2005-01-30
You should probably be doing something like:

% aptitude install gstreamer-mad

which will install all its dependencies.  You may want to do something like:

% aptitude install gstreamer-player gstreamer-plugins

instead, to get the player and all the plugins.

---

### Post by Chrisb319 on 2005-01-30
I have no clue what you guys are telling me to do

---

### Post by JoWilly on 2005-01-30
[QUOTE=Chrisb319]How do I get to the command console. :cry:[/QUOTE]

Menu -> Applications -> System Tools -> Terminal (or root terminal)

Starting Terminal is better than root terminal.

If you start terminal, add the command "sudo" in front of your commands to execute something system whide.

---

### Post by carlc on 2005-01-31
You are probably better off learning to use synaptic at first.
Next, give apt-get a try.

Here are two great links.....

[http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)

[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

---

### Post by carlc on 2005-01-31
Go to synaptic by clicking "computer" on the top panel.
Then click "system configuration"
And then click on "synaptic package manager"

---

### Post by Chrisb319 on 2005-01-31
[QUOTE=carlc]Go to synaptic by clicking "computer" on the top panel.
Then click "system configuration"
And then click on "synaptic package manager"[/QUOTE]

is this what I use to install things

when it came to windows there would be a .exe file that would just install things to a specified directory.

How does Linux install things there seems to be many directories boot, bin, lib, home are these even directories?

---

### Post by Chrisb319 on 2005-01-31
When I try to listen to a cd I can't get any sound.

---

### Post by carlc on 2005-01-31
The synaptic package manager should be the easiest way to install a package (or program). 

What do you want to install?

---

### Post by DirtDawg on 2005-01-31
My my my. You are very new. I have been in your exact position before: very new and confused about what everyone's telling me. What's happening right now is you're getting two different ideas about how to accomplish the same thing. 
Ubuntu has something that works *kind of*  like "exe" files, and they are called  a "deb". The thing is, they don't work the same as "exe"s do (you don't just double-click them to install).
   What carlc is trying to tell you about is a program (called synaptic) which gets these "debs" and installs them for you on your computer. My linux box is not connected to the internet so I have never used this. Once you get it up and running, it is supposed to work very well and be very easy. 
   One thing I should note: Linux is different in windows in that there is not a universal "exe" type file. Different Linux operating systems use different types of "exe"'s. The two most popular are "deb" and "rpm". Ubuntu, as I stated before, uses "deb". 
  In addition, many Linux disributers tailor programs specifically for their operating system, Ubuntu is no exception. To see what I mean, go here and take a look: [http://higgs.djpig.de/ubuntu/www/warty/](http://higgs.djpig.de/ubuntu/www/warty/)  . You are free to install ANY of these programs. There may be many which don't make "sense" at first glance (that is, you may ask yourself "what is THAT!?"), don't worry about those, just check out the one's you understand. "Games" is a good place to start.
  Now, you aren't restricted to using only these programs, but they will most likely install without any trouble as they are, like I said, specifically designed to run on Ubuntu.
   Okay, I would recommend searching around the forums a bit and seeing about the synaptic system carlc referred to. If it's still too confusing for you, let us know and I will write a step by step for how I install things without synaptic. It involves downloading programs from the website I mentioned above, and installing them manually. It's not hard, but I think the synaptic is probablly easier in the long run.

  Good Luck!

---

### Post by Chrisb319 on 2005-01-31
ahh thanks DirtDawg,

but lets say I download the package how do I get synaptic to install it for me. 

the file I have to install is

"qtella-0.6.5.tar.gz"

also I do not get any sound when trying to play my cd and I cannot play my mp3 files.

---

### Post by DirtDawg on 2005-01-31
[QUOTE=Chrisb319]ahh thanks DirtDawg,

but lets say I download the package how do I get synaptic to install it for me.[/QUOTE] 

You're welcome. 
 Like, I said, I've never used synaptic before so I can't help you here. Someone can. I belive Synaptic works like this: it lists programs you can download for Ubuntu, but they all come from the website I posted earlier. I believe the website is what's known as a "repository". Essentially, it downloads the program you chose from the repository along with any dependencies you may need. 
   Ubuntu is written entirely in "C" code, dependincies are libraries "C" uses to make itself work. Sometimes (not very often, but sometimes nonetheless), when you try to install something, you'll be missing a library or two. The advantage of Synaptic over manually downloading and installing things is that it gets these libraries and installs them for you (though links to the required libraries are always listed on a programs main download page, so they're easy to find). 



> the file I have to install is

"qtella-0.6.5.tar.gz"



The file you're trying to install is called a "binary". What that is, it's the raw binary (0 and 1s) code used to run the program. The advantage of this is it can be installed on any Linux operating system. The disadvantage is you have to "compile" it yourself and those missing libraries I mentioned before can often be a problem. Compiling is a slightly advanced topic, and one I'm not too familiar with. Correct me if I'm wrong, but qtella is a filesharing program? If you go to the repository website, and scroll aaaaalllll the way to the bottom, there's a "packages search" link. I went in there and entered "filesharing", and found about 9 packages (by the way, a 'package' is a set of binaries pre-compiled specifically, in this case, for Ubuntu. Much easier to work with). The only one I am familiar with is amule ([http://www.amule.org/](http://www.amule.org/)). I haven't tried it though. Only it's cousin emule. My suggestion would be, unless you're hell-bent on qtella, to use Synaptic to find a filesharing package. Again, if that proves frustrating, go to the repository, and use the same search (by the way, i checked the "descriptions" button, not the "name" button). Use the search to find the packages you want to install, then maybe use Synaptic to download and install them(?). I'm not sure if Synaptic lists things by name or catagory or what. If worse comes to worse, you can download from the repository manually and install them manually (if you decide to go this route, like I said, I'll write you a step-by-step). 
   If you are hell-bent on qtella, well, you'll have to do some research into compiling. Not my strong suit.

> also I do not get any sound when trying to play my cd and I cannot play my mp3 files.

This is what's known in the Linux world as a "pain in the ass". The amazing thing about Windows, is their product works on just about any computer you slap it in. They do this very well (Ubuntu, in my experience is better at this than any other distrobution I've ever tried. Close to perfect, but not quite). The sound from my CD player on my Linux Box doesn't work either, but I haven't bothered messing with it because I have a radio right next to the computer. The best thing to do is search this, and maybe other forums for sound related problems. It may be something simple, so don't worry too much. You may also need to start getting aquanted with that Terminal you read about earlier.
  Mainly: be patient (Things pay off in the long run, after the learning curve), and don't be afraid to ask questions.
   Sorry I can't be more help with the Synaptic. Good Luck(again)!

---

### Post by rudi on 2005-01-31
[QUOTE=Chrisb319]How do I get to the command console. :cry:[/QUOTE]
 "Applications --> System Tools --> Root terminal
 Then you have to give your password. 
 
 Now take a look at the unofficial Ubuntu Starter Guide
 [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
 
 Happy apt-getting :D

---

### Post by regebro on 2005-01-31
[QUOTE=Chrisb319]also I do not get any sound when trying to play my cd and I cannot play my mp3 files.[/QUOTE]I don't know about the CD's, but for the mp3 files there are information in the FAQs.

Basically:

1. Open the synaptic package manager. 
2. Select "Settings" and then "Repositories".
3. There are two repositories not checked. Check them. (These are known as the Universe repositories). Click OK.
4. Click Reload, to download the list of the new packages from these two repositories.
5. If you use the default music player, search for "gstreamer-mad", and install that package.

TADA! You should now have mp3 support.

---

### Post by Buffalo Soldier on 2005-01-31
an introduction to apt-get [http://www.newsforge.com/article.pl?sid=04/12/02/1710208](http://www.newsforge.com/article.pl?sid=04/12/02/1710208)

---

### Post by Chrisb319 on 2005-01-31
[QUOTE=regebro]I don't know about the CD's, but for the mp3 files there are information in the FAQs.

Basically:

1. Open the synaptic package manager. 
2. Select "Settings" and then "Repositories".
3. There are two repositories not checked. Check them. (These are known as the Universe repositories). Click OK.
4. Click Reload, to download the list of the new packages from these two repositories.
5. If you use the default music player, search for "gstreamer-mad", and install that package.

TADA! You should now have mp3 support.[/QUOTE]

I installed it and it still does not play any sound.

I installed several things where do they go? Where can I open the aplications?

---

### Post by Chrisb319 on 2005-01-31
OKay so I have a .deb file that will install a emule client how do I install it?

---

### Post by carlc on 2005-01-31
Hey, Read the [Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/index.html) 

This is a great guide and if you follow it step by step, you should be ok.

From it, first follow the section: 

"How to add extra repositories?"

Then follow these two sections: 

"How to install Multimedia Codecs?"

And

"How to install Multimedia Player (XMMS)?"

If that goes well, then go for:

"How to install P2P Gnutella Client (LimeWire)"

---

### Post by DirtDawg on 2005-01-31
[QUOTE=Chrisb319]I installed it and it still does not play any sound.

I installed several things where do they go? Where can I open the aplications?[/QUOTE]

Hey, I am strpped for time at the moment, so I'll have to make this quick. For now, I'll just tell you how to run programs. Most of the time, programs are installed in a folder (aka directory) called "/usr/bin". When you open your home folder(computer>home), you'll notice a pop-up menu down in the left hand corner with your login name. It will give you the option to go to a directory called "/". Go there. Then look for directory "usr", then directory "bin". In this folder is a ton of stuff. Most of these are programs. If you did install things, you'll find them here. 
  I'll use an example I know you have. In /usr/bin, you'll find a program called "gaim", this is an instant messanger program. So, go to Applications>Run. A dialogue box will pop up. In the box, type in "/usr/bin/gaim" (without the quotes, of course). Make sure the "run in terminal" box is NOT checked. You'll notice that even as you enter these words, the GAIM logo (a little yellow man) will appear because Ubuntu recognizes the program you're running. 
    In a nutshell, that's it. You can add shortcuts in your pull-down menus. In addition, there is another folder called "/usr/games" with some other goodies in there. As a rule of thumb, you may not want to just start running things willy-nilly if you don't know what they are. Run things only if you know what they are, or if you installed them yourself (which would, I suppose, mean you know what they are).
   That's my understanding of the situation. If someone else knows an easier way to do this, I would also love to know what it is  :D .
    Alright, I need to go. 
   Good luck.

---

### Post by knappen on 2005-01-31
carlc is right. Have a look at the starter guide, heaps of info there.

But Chrisb319, please do not give up on Ubuntu (or Linux) yet.

---

### Post by crane on 2005-01-31
Click
Applications>System Tools> Terminal

That will open a the "command" window they are talking about. It's also referred to as a terminal window.
 From there you could enter your commands

---

### Post by Chrisb319 on 2005-01-31
I just manualy installed the Java VM so I can run LimeWire but I think I did not finish the instalation of Limewire as it did not appear where it was suppost to. I even rebooted my machine for good measure. How would I uninstall it I noticed while it was uninstalling it unpacked a uninstaller file. My hoopes is that I can unistall it then start over. 8-[ 

At the moment I am kinda stuck with Ubuntu but over the last 24 hours I have manualy installed something, ran a program I installed, started to play MP3 files on it (still can't get my totem to play them) I did manage to make it play video but not audio when playing .mpeg files. I would say I have made some improvement. =D>

---

### Post by carlc on 2005-02-01
It sounds like you are learning quick!

Limewire should apppear under "Internet" on the Gnome menu. 

Didn't it start when you installed it?

When I first installed it, I thought that I had messed something up because a start up screen that said something about starting a html reader (or something like that) would not go away. However, behind it was a menu to setup Limwire. I clicked on it and setup Limewire and it is working fine.

To run Limewire, try typing this from the terminal:

/opt/LimeWire/LimeWire

---

### Post by Chrisb319 on 2005-02-01
How do I know when I close a program like Limewire that it is infact closed? I would also like to know if there are any application to scan for viruses and remove spyware thanks in advanced.

---

