---
title: "I can't even do the basics"
date: 2005-04-27
forum: Desktop Environments
---

### Post by SuperKev on 2005-04-27
Hello,

Well like so many, Kubuntu is my first experience with Linux other than the Knoppix Live CD- which I really liked and is what got me into Linux- but I feel like a toddler lost in the woods on a moon-less night. 

I mean I can't seem to figure out how to even do the most basic of things like download and install a app for instance. I tried with Firefox and Xchat but no joy, I read all the posts, googled until my eyes bled but just can't seem to get my mind around how this is done. tried apt-gets, Knayptic, but nothing seems to work. I am surprised I was able to get this online but somehow I managed, although I still have to configure dhclient each time I boot back up, 

Now this is not a complaint about this distro, it's an admission of my own incompetence with Linux. I know once I learn this stuff I will rarely need to use Windows again and that's a good thing. Problem is the learning curve is steep and I feel like I'm sliding back down the slope.  :mad: 

Here's the things I would like to get running on my box:

Fluxbox- I just like it what can I say?

Firefox

Xchat

Get screensaver to work properly

Get my sound working

Understand how to DL and install apps.

And even more basic, how do I make a folder and then put documents or pictures in it? 

I know these are some almost assinine questions from a super-ultra n00b (I'm too old to be using that word!) But any help or direction you might give will be appreciated greatly. Funny thing is, when it comes to windows I'm the computer geek in my circle of friends and the one they all call to fix their computers. Not that I know all that much, I just know more than them I guess. 

Thanks!

---

### Post by claydoh on 2005-04-27
To begin, you can use kynaptic, found in the System menu to install applications. I would suggest starting out by installing synaptic, which is a better program as it has more info about what you are doing :)

you can install all the things you mentioned, and more :grin:

---

### Post by SuperKev on 2005-04-27
[QUOTE=claydoh]To begin, you can use kynaptic, found in the System menu to install applications. I would suggest starting out by installing synaptic, which is a better program as it has more info about what you are doing :)

you can install all the things you mentioned, and more :grin:[/QUOTE]

That's my point, I tried those and they are not working for me. For example I tried to install Firefox- seems fairly straightforward right?- Clicked all the right buttons in Kynaptic, it seemed to do_something_ but I don't see FF in any menu or an icon on my desktop. 

I'm sure things are not as complicated as I am making them but right now I'm as lost as I can be. I'm sure as soon as I see it done a couple of times I will be buzzing right along as  happy Linux user, I just hope that day is soon.  
 ;-)

---

### Post by MetalMusicAddict on 2005-04-27
I sent you a PM. Bring up the "Terminal" and type: **firefox**

---

### Post by skimitar on 2005-04-27
Hi,

To get synaptic open a command shell (there should be an icon for this on the KDE bar at the bottom of the screen).  I'll assume that you are connected to the internet.

In this type (without the quotes): "apt-get install synaptic" You will be prompted to enter your log on password.

This will install synaptic. There will be a menu item for Synaptic in the KDE menu (I <think> it is in the system sub-menu but I am at work and they don't run KDE) so have a look. If you can't find it, just type (again without quotes) "sudo synaptic" in the same command shell that you used to install synaptic.

This will open synaptic. There is a button marked search, if you click it you will be able to enter a search term (e.g. firefox).

When it returns a list of matches, you can just right click one and select "mark for installation". You can keep searching for the applications you want and mark each one.

When you are ready, click the apply button and synaptic will download and install all the software you have selected. Most of them will have menu items installed to run them (fluxbox will be a different story, you should be able to select it as the window manager from the KDE log on screen).

I find that sometimes KDE doesn't create the menu item straight away, but you can just log out and back in of KDE to fix this (no need to reboot).

To create a folder, open up your home directory (I think that there is a desktop icon by default for this in KDE) and right click anywhere. From memory a menu pops up with a "create new..." sub menu and one of these options is "Folder" which will let you create a folder. You can just drag and drop files into the folder.

As with most things in linux you can do this from the command line - if you wanted to create a folder you would type "mkdir FOLDERNAME" at the command shell.

Search the forums for advice on sound - there's a fair bit there, I think there is a Hoary specific thread on sound not working somewhere.

Cheers
Jon

---

### Post by maruchan on 2005-04-27
> Understand how to DL and install apps.

Well, you're halfway there. It sounds like you have installed Firefox already. The catch is, you probably need to add it to the menu you want it on. Right click the K-menu and choose "Menu Editor" for starters. Then click the "new item" icon and it should be pretty self-explanatory from there. The "command" field, for example, should have the word Firefox in it :)

> And even more basic, how do I make a folder and then put documents or pictures in it?

Well, if you open Konqueror and click the "home" button, there's your home directory. Then you can right-click inside that window and choose New -> Folder. Then you can drag files in there, or do Ctrl+C/V for copy/paste, etc. That's the visual way, anyhow.

You might read up in the KDE help section, too (in the K Menu). Lots of good stuff in there.

Keep asking questions, you'll find all the help you need.

---

### Post by SuperKev on 2005-04-27
:-| 

apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate


And when I right click on the K icon I get a Menu Editor line but when I click on that nothing happens.  ](*,) 

I have Firefox 'unpacked' in my home folder, just can't get it to install

---

### Post by audscott on 2005-04-28
In Kynaptic (in the find screen, if memory serves - control+f) check you haven't elected to "only download" the packages.  This will prevent the packages from installing with the download.  Kubuntu has seemed to nice for me, I hate to see someone be alianated - keep at it, I'm sure you'll find your way around.  Good luck, one way of the other.

EDIT:  Damn!  I'm thinking of Ubunto Synaptic.....sorry.  Check in Kynaptic for firefox plugins and dependencies.  

I'll agree Linux does not present the ease of Windows, but it's a blast to play with!   \\:D/

---

### Post by SuperKev on 2005-04-28
Like I said I know it will be worth it in the long run, and the knowledge I gain just from messing with it will be invaluable, However I would like to get it set up to where I can use it for my daily computing needs and then just use windose for gaming when neccessary. 

So the immediate need is to be able to write, email and print documents (sharing the printer with the windows box is another challenge I have yet to tackle) The ultmate goal is to have it so a vast majority of my computing needs will be taken care of by Linux.

I'm sure it will get there but I need to get things moving a bit faster than they are now. Learning how to DL and install apps (packages?) will be a big help. 

I'm still wondering why I have to reconfigure the dhclient in Konsole everytime I boot the machine up, at the end it says something about needing  'renewal in 41332 seconds' or some other such number, Is this normal behavior? Can I make it so I don't have to reconfigure this everytime I boot up?

Thanks

---

### Post by J. S. Jackson on 2005-04-28
I'm not sure why you chose Kubutu as your first distro.  You have your reasons.  However, I would strongly recommend you start with normal Ubuntu until you get the hang of how things work in gnu/linux.  Firefox and Xchat both are installed by default in Ubuntu.

A default install of Ubuntu, and [this guide](http://ubuntuguide.org/) and you will have **everything** you need for starters.  In addition you will have a much larger user base to help with any problems that arise.

From there, once you get your feet wet, you can try out Kubuntu or some other distros as you like.

---

### Post by dave9191 on 2005-04-29
> I'm still wondering why I have to reconfigure the dhclient in Konsole everytime I boot the machine up, at the end it says something about needing 'renewal in 41332 seconds' or some other such number, Is this normal behavior? Can I make it so I don't have to reconfigure this everytime I boot up?


If you open a terminal and type

sudo kcontrol

this will ask you for your password and bring up the control center in admin mode (An alternative way to do this is to open the control center from the menu and click on the admin button, that will ask for your password but doesnt work for me). 

There go to Internet & Network > Network settings. Click on the interface you want (Probably eth0) and configure it as automotic with dhcp. 

As for Renewal in xxxx sec it is normal. Its how dhcp works. You get given an IP address for 3 days. Then it has to be renewed with the dhcp server. In windows you can also find out how long till renewal if you look at the advanced status of the net adaptor. 

Dave

---

### Post by muzza on 2005-04-29
[QUOTE=J. S. Jackson]I'm not sure why you chose Kubutu as your first distro.  You have your reasons.  However, I would strongly recommend you start with normal Ubuntu until you get the hang of how things work in gnu/linux.  Firefox and Xchat both are installed by default in Ubuntu.[/QUOTE]

From an one old noob to another, I couldn't agree more with Monsieur Jaquson.

My first distro was Mandrake and it nearly sent me back to the virus ridden comfort zone that is Windoze.  Just before I packed my bags, I tried what everyone was raving about - Ubuntu - and I'm still here.

I've hit the wall a few times, but help is always here.  And I've just installed Kubuntu, and found that KDE isn't that hard after all.

I still have unresolved issues, but like you, I'm sticking with it.

And... you may find you prefer the Gnome desktop.

---

### Post by okTober on 2005-04-29
I installed Kubuntu on my Dell Inspiron 9100 with no problems. I even got the wireless working with a great post from jonny and others [here](http://ubuntuforums.org/showthread.php?p=125537#post125537). Like you, I also wanted some of the Unbuntu default apps on my machine. I just installed the ubuntu-desktop over my Kubuntu installation and everything works great. I still use KDE but have access to all Unbuntu and Gnome apps that are missing from Kubuntu. Of course not everybody wants to waste this kind of space on their harddrives. But I'm still a novice and want to play around with everything before I start weeding stuff out. 

[Here is another great post](http://www.ubuntuforums.org/showthread.php?t=26709&highlight=ubuntu-desktop+internet+connection) about how to install the ubuntu-desktop onto Kubuntu without and internet connection.

---

### Post by SuperKev on 2005-04-29
[QUOTE=okTober]I installed Kubuntu on my Dell Inspiron 9100 with no problems. I even got the wireless working with a great post from jonny and others [here](http://ubuntuforums.org/showthread.php?p=125537#post125537). Like you, I also wanted some of the Unbuntu default apps on my machine. I just installed the ubuntu-desktop over my Kubuntu installation and everything works great. I still use KDE but have access to all Unbuntu and Gnome apps that are missing from Kubuntu. Of course not everybody wants to waste this kind of space on their harddrives. But I'm still a novice and want to play around with everything before I start weeding stuff out. 

[Here is another great post](http://www.ubuntuforums.org/showthread.php?t=26709&highlight=ubuntu-desktop+internet+connection) about how to install the ubuntu-desktop onto Kubuntu without and internet connection.[/QUOTE]

I'm willing to give that a go since I have the Ubuntu distro burned to CD as well...I think. If not it's easily done. How do I go about putting Ubuntu on top of my current install? Keep in mind I am a super-ultra deluxe model n00b. 

I picked Kubuntu simply because Iike the KDE desktop, not that I have any aversion to GNOME, not in the least. I actually think fluxbox and enlightenment would be rather cool too, just for the geek factor when friends are over if nothing else
 ;-)

---

### Post by muzza on 2005-04-29
[QUOTE=SuperKev]I'm willing to give that a go since I have the Ubuntu distro burned to CD as well...I think. If not it's easily done. How do I go about putting Ubuntu on top of my current install? Keep in mind I am a super-ultra deluxe model n00b. ;-)[/QUOTE]

Here's one way; [Try this thread](http://www.ubuntuforums.org/showthread.php?t=26709&highlight=kde+gnome) 

Last night, I installed KDE desktop (from Kubuntu CD) over my seemingly perfect Ubuntu install, but in KDE I have no sound and none of the multimedia apps recognise the audio CD, even though it's right there on the desktop.

So I tried installing just Kubuntu on a different partition, and blow me away, everything worked?

Seeing I'm still in explore mode, I'm going to try installing Gnome desktop into Kubuntu and see if I can get the same positive result as oKtober.  Let us know how you get on, and so will I.

Noobs United!

---

### Post by muzza on 2005-04-30
OK, I did it tonight.

I tried the way the above link described, but Kubuntu-desktop just wouldn't install from the CD only.  I had to connect to the internet to get Kubuntu desktop installed, but it went without a hitch.

Prognosis:  Good.  Everything works as it should, except some KDE stuff only works in KDE (AmaroK)  I've got system sounds and I'm posting this message from Firefox in KDE.

I may discover some glitches down the road, but nothing obvious so far.  When I installed KDE over Ubuntu, I had immediately apparent problems.

---

### Post by SuperKev on 2005-05-01
Well I'v got good news and bad news;

Bad news is I unistalled Kubuntu, good news is I installed Ubuntu  :) 

It seemed like nothing in Kubuntu wanted to work right, I couldn't do apt-get, kynaptic wouldn't work, I had to re-initialize dhclient everytime I rebooted my machine. I almost did a HD install of gnoppix but at the last minute thought I would stick with Ubuntu since when I began thats what everyone was recommending but I had to be dofferent and try Kubuntu first.

But everything seems to be working ok and now I can start setting up my system to my liking rather than wrestling with it just to keep it running marginally.

So, how can I install fluxbox??

---

### Post by dave9191 on 2005-05-01
Enable the extra repositories and do an 


apt-get install fluxbox

---

### Post by SuperKev on 2005-05-01
[QUOTE=dave9191]Enable the extra repositories and do an 


apt-get install fluxbox[/QUOTE]

How do I enable them? Remember I'm a super-ultra deluxe model n00b, so for most things I will need to led by the hand until I do them once to see how it's done. 

And why does the screensaver not work? It didn't in Kubuntu either.


Thanks

---

### Post by Leif on 2005-05-01
[QUOTE=SuperKev]How do I enable them? Remember I'm a super-ultra deluxe model n00b, so for most things I will need to led by the hand until I do them once to see how it's done. 
[/QUOTE]

follow ubuntuguide.org for this, and many more answers.

---

### Post by dave9191 on 2005-05-01
Ubunutguide.org and these forums are a wealth of info, not to mention the wiki on the ubuntu site. Always search those 3 for answers and more often then not the answers will be found. Good luck ;)

---

### Post by SuperKev on 2005-05-01
Well I went the site that Lief pointed me to but couldn't make heads nor tails of it. The problem for me is because all the terminology is so different from windows I don't understand 99% of the instructions.

For instance he says take the below two line and 'uncomment' them (huh?) and then I guess put them in the terminal console. I tried them in there but just got error messages, so I'm as lost as I was before. My fault though, I just don't know all the terms and what they mean for me to do. 

SK

---

### Post by neilius on 2005-05-02
When you have a text file that is used to store program settings or some other configuration for your system it'll contain sections called 'comments'. These are ignored by any software reading the text file and are there just for you to read and make sense of things. You'll see commented lines with a # in front to signify this. For example:

```
# this is a comment - the following line is not
  this is not a comment, whatever program reads this file will only see me!
```

Sometimes a line of code can also be commented so all you have to do to change a setting or enable a feature is 'uncomment' the line, by simply editing the file and removing any #s that precede the juicy stuff. It comes from the world of programming on all platforms, even Windows, where programmers would put a comment before a section of their code to remind themselves what the code did or if there were any bugs there that might need fixing. When the program is compiled the comments are ignored by the compiler and not processed.

Regards,

Neil.   :)

---

### Post by verden01 on 2005-05-02
before you can do anything go to a Konsole and type in sudo apt-get update
after that you can then use kynaptic

---

### Post by ampiee on 2005-05-02
Hi I am trying to install ubuntu but it goes to command mode (Cannot start X windows due to Graphics driver) As i am NEW to linux I dont even know how to load driver. Somebody told me I must log in as root. but when i try it says it is disabled.
If i am using the wrong place for information I am sorry but i could not figure out how to start a new question (Thread) Can somebody help?? Please

---

### Post by muzza on 2005-05-02
go back to the index page (where you found this thread) and click on the 'new thread' icon - top left.

---

### Post by ampiee on 2005-05-03
Thanks -I managed to get it right ! 

How do I un-Subscribe to this thread ?

---

### Post by dave9191 on 2005-05-03
Go to the user CP, link near the top of the page under the thread location section. Then look at all your subscribed threads and click unsubscribe.

---

### Post by Nu-Buntu on 2005-05-03
SuperKev, you will learn this. You are adventurous enough to start, and you can become very productive with Linux in a short time. Soon you will look back on your opening post and say, "How could I have been so frustrated with this?"

I am an old DOS jockey, Windows user, and now an advocate of GNU/Linux and other freeware. If this old dog can learn some new tricks, you can too! Good luck as you begin to explore the joys of Open Source Software!!

Ubuntu ROCKS!

---

