---
title: "Not sure what's going on..."
date: 2006-06-20
forum: Desktop Environments
---

### Post by gsail11 on 2006-06-20
Note: I think the forum is making me select a tag (thread prefix?) but none of them apply. I'm using breezy badger.

I'm not sure exactly what's wrong, or if this thread is in the right part of the forum, but I'm just going to toss it out there.

I think I have a number of missing files, or other errors going on with my ubuntu right now, and I'm not sure what to do. I am going to give a little cause and effect list of things I try to do that don't work.

I was trying to get videos to play in Mozilla which is something that has been very disappointing for me in my switch from Windows to ubuntu. Flash was difficult to install, and either isn't installed properly, or there is some other error, because flash movies are usually sort of freezy or jumpy. In addition to this, I have no windows media or realplayer support, so that is very limiting. I entered some lines into the terminal that I got from a website that were supposed to make mozilla work with any video type I could come across. Well that didn't work, and now Totem doesn't work either. When I try to run Totem I get: "Totem could not start up. The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector." I don't really know what this means or why it's not working. I would like to be able to use Totem to play music, but I also want to be able to watch videos via mozilla.

When I try to run synaptic, I get this: "The following problems were found on your system:

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)" 
But even though I get this error message, synaptic still opens and works.

When I try to upgrade to Dapper Drake from Breezy Badger via upgrade manager, I get this: 
"Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found"


Not sure what to do here...

---

### Post by GoogleNinja on 2006-06-20
ok, theres a few things going on here

> **gsail11]
I think I have a number of missing files, or other errors going on with my ubuntu right now, and I'm not sure what to do. I am going to give a little cause and effect list of things I try to do that don't work.[/QUOTE]

I don't think the problem(s) are related to missing files
[QUOTE=gsail11]
I was trying to get videos to play in Mozilla which is something that has been very disappointing for me in my switch from Windows to ubuntu. Flash was difficult to install, and either isn't installed properly, or there is some other error, because flash movies are usually sort of freezy or jumpy. In addition to this, I have no windows media or realplayer support, so that is very limiting. [/QUOTE]

Currently, flash on linux doesnt work, it "works" if you get my drift  said:**
> 
 I entered some lines into the terminal that I got from a website that were supposed to make mozilla work with any video type I could come across.

the lines you entered are kinda important to know, in order to diagnose your problem. chances are its one of the plugins i mentioned earlier, but how to fix it depends on how you installed it.

[QUOTE=gsail11]
Well that didn't work, and now Totem doesn't work either. When I try to run Totem I get: "Totem could not start up. The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector." I don't really know what this means or why it's not working. I would like to be able to use Totem to play music, but I also want to be able to watch videos via mozilla.
[/QUOTE]

Try doing this 
```
sudo apt-get install totem-xine
```
it may not help in the least, but it may also fix the problem. if you are willing to reformat, i would highly recommend trying automatix to set all this stuff for you.

[QUOTE=gsail11]
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)" 
But even though I get this error message, synaptic still opens and works.
[/QUOTE]

those are apt-caches that seem to have been corrupted. normally, you just need to "sudo apt-get update" to fix it. however....

> 
When I try to upgrade to Dapper Drake from Breezy Badger via upgrade manager, I get this: 
"Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found"


Not sure what to do here...

...that tells me that you have repositories in your /etc/apt/sources.list file that apt cant hit. that could mean that the repository is temporarily down (because the server crashed or something), the repository no longer exists (as in the fellows who ran it have stopped), or there is a type somewhere in the url in your sources.list. in any case, sticking a "#" in front of the "theli.free.fr/" and the "koti.mbnet.fi/" entries will get apt to ignore them. you can then run apt-get update, and figure out what was wrong at your convenience.

---

### Post by gsail11 on 2006-06-23
The good news is that Totem works fine now. Videos don't, but I guess they just aren't very compatible with linux, and I have a windows computer I can use.


I put "sudo apt-get update #[http://koti.mbnet.fi](http://koti.mbnet.fi) #[http://theli.free](http://theli.free). " into the terminal, and it ran, and I'm not sure what I was supposed to do. The "and figure out what was wrong at your convenience." It what threw me... When I ran it this was the result.
"W: Duplicate sources.list entry [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/v ar/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead."
Not sure why it tells me to run apt-get update to fix the problems it faced while I was running apt-get update...

When I tried to upgrade to dapper again, I had the same problem. I decided to go to theli.free.fr to see if I could find them and I found that "http://theli.free.fr/packages/breezy/./Packages.gz" is now at http://theli.free.fr/packages/_breezy_obsoltete/" How do I change it so ubuntu looks there intstead of the old place?

Another unrelated issue is that my mozilla came up with a message saying that my default user is occupied, so I need to make a new user. This means that I have no access to any of my favorites, or any of the settings on my original account. How do I remedy this?

---

### Post by ayoli on 2006-06-23
if you want to change path or desactivate a repository the aphical way: in synatptic, go menu to configuration > repositories then uncheck the repos you don't want (usefull for update, you'll need to desactivate some non-official repos) or edit it if the uri has changed.
the text-mode way is to edit your apt-get sources.list with
```
sudo nano /etc/apt/sources.list
```
and comment out lines of repos you want desactivate or change uri then CTRL X for save.

---

