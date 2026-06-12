---
title: "Behind the basics--How does Linux work?"
date: 2005-12-29
forum: Desktop Environments
---

### Post by moroz on 2005-12-29
Hi, this is my first post, so please excuse any oversights in the appropriateness of this thread.

I've been messing around with Ubuntu for a few days, having wiped XP from my hard drive in an attempt to force myself into leaving Windows for good.  One of my main problems right now is just being unfamiliar with how Linux works as opposed to Windows.  Specific tips are one thing, but I want to understand how this stuff works so I can slowly make better guesses on my own as to how to accomplish something. 

For example (and the first thing I really want help with):  "apt-get install" almost seems too easy.  What I mean is that I've been able to install programs I want without understanding what is happening.  Now I want to get rid of some of them, but I'm not sure how.  Do I use apt-get remove--will that completely remove all traces of an install?  

Basically, in Windows I knew how to install programs where I wanted to, and how to search out any remnants of them after I uninstalled.  But how do I do this in Linux?  When I use "apt-get install" how can I see and decide for myself what files will be put where?  How do I know what if any dependancies will also be downloaded and installed?  And then when I want to get rid of them, how do I uninstall cleanly so that my system is left the same as before I installed--how do I find, identify, and remove all the files that are associated with a program?

That's what's frustrating me most right now.  I like to keep my system uncluttered and organized, and right now I feel rather clueless in that regard.  Any help would be greatly appreciated, as all the tutorials I've found thus far mostly deal with getting things done.  I'd like to find something that explains to me what the different components/files/directories of this OS are, and what happens in the file-system when you follow those other tutorials.

Again, thanks for reading this, and for any advice you can offer.

Sil

---

### Post by darth_vector on 2005-12-29
hi,

to remove programs completely

sudo apt-get remove --purge progname

aptitude is much better than the windows uninstaller. it will let you know if there was any file it didnt - or couldnt - remove so that you can do it yourself. if it doesnt give you any such warnings then it has sucessfully removed the program in its entirety.

---

### Post by darth_vector on 2005-12-29
as for the directories:

/bin and /sbin contain operating system executables. you shouldnt have to go here.
/home contains all of the users files except those belonging to root
/root contains the root users files
/etc contains a lot of the configuration files for services like networking, X, etc...
/usr contains a lot of shared stuff. programs that you install should live mostly in /usr/bin or /usr/local/bin. there may be config files for these programs in other places.
/boot contains your bootloader
/proc is a pseudofilesystem that contains information about the system. have a look around, its quite helpfull.
....

have a read of this if you are interested in more details:

[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

### Post by DaMasta on 2005-12-29
Here's an informative link too. [http://en.wikipedia.org/wiki//bin](http://en.wikipedia.org/wiki//bin)
And kudos for taking the initiative of learning the guts.

---

### Post by az on 2005-12-29
Ubuntu strives to abstract a lot of the nitty-gritty things and make life easier.  I say abstract, because that in no way hides things.  You get the choice of using the easy way and then dropping down to the hard way for more advanced things.

For example, you can use synaptic instead of apt-get.  For one, it is easier to search, change or add repositories and so forth.  As well, recommended packages are installed while you have to do this by hand though the command-line.

You will tend to get into a lot less trouble.  Speaking of which, getting in trouble is actually the best way to get to know the internals of the system.

Other than that, it should work just fine without you having to know the internals.

Ask as many questions as you like here.  That is what this forum is for.

---

### Post by slux on 2005-12-30
Well, GNU/Linux is certainly for you if you like to keep things nice and organized. apt-get & dpkg exist for the very reason to keep track of things very closely and a Linux install will seldom degenerate into the mess that is Windows app install/uninstall. (and the Debian philosophy seems to be to keep a strict control on every single thing going on in the machine, sometimes overdone :P) 

If you really want to get down into the gritty details, take a look at how dpkg packages (debs) work but understanding the filesystem hierarchy others have pointed at is a good start.

---

### Post by steve.horsley on 2005-12-30
For a quick start, if you use Synaptic, right-click a package that is installed and select Properties, you can see a list of the files it installs. There are also lists of dependencies.

---

### Post by psusi on 2005-12-30
Aye, use synaptic.  You can do everything from the command line with apt-get and friends, but it's a lot easier from the gui.  

In synaptic you can right click on a package and choose properties and it will show you every file that the package installed, and what other packages it depends on.  

You can remove or completely remove packages from synaptic, the difference being that the normal remove leaves behind the config files and settings in case you decide to reinstall it some day and don't want to loose the settings.  

If you completely remove the package, all traces of it are destroyed.

---

### Post by MystaMax on 2005-12-30
I was wondering the same thing as the threadstarter.  I'm always reading the wiki and other online resources, that explain how to get things done, but don't explain to you what you are actually doing. So you spend tons of extra time trying to understand what you're doing and why a problem went wrong.

---

### Post by Zwack on 2005-12-30
Any good books on How Unix works will teach you general information about Linux...

O'Reilly Running Linux will teach you some of the How to do... stuff. It's a bit dated, but it covers the basics.  I think it may be available from the Linux Documentation Project as well.

If you're interested in how the OS actually works Modern Operating Systems by Andrew S Tanenbaum is a good introduction.  It does deal with writing an OS so it's heavy on technical detail.

What level of information are you really interested in?

Packages usually install files to a specific location (Using synaptic you can remove the package and examine what it puts where) unlike Windows you can't really decide where they should go.  But even in Windows you don't have that much control.  When you install a program in d:/program/example/ it installs stuff in c:/windows and c:/windows/system as well as the registry entries and...  

Z.

---

### Post by moroz on 2005-12-30
Thank you all for the replys and helpful commentary.  I wasn't expecting as much of a response as I have gotten.  Between all the suggestions I think I have a lot to start with.  

It's interesting that there was such an easy sollution using the gui.  (Although I think I've made some progress with Darth Vector's suggestion to use the "purge" attribute with "apt-get".)  I hadn't even messed with Synaptic that much because I had read that it was important to learn to do things from the command line, and that doing so would ultimately make you a more knowledgeable and efficent user of the Linux OS.  As a result I was trying not to rely on graphical interface programs as much as possible because I thought they would shield me from learning what I was doing.  Any thoughts?  

It does seem pretty handy to have something like Synaptic tell you all the details of your install.  Maybe this can be done from the command line as well, I'm not sure.  But if so, I imagine it to be much less easy to decipher for the beginner.  I'll try to mess with both.

Again, thanks to everyone here.  Your willingness to take the time to share your experience is what makes this place so such a great resource.

--Now I've got to go make another post to help me solve a technical problem that just arose. (Sigh)

Sil

---

