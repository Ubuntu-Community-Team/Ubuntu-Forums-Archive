---
title: "Want only 1 Nautilus window! How?"
date: 2005-03-05
forum: Desktop Environments
---

### Post by thestarman on 2005-03-05
I have tried and just can't find a way to force Nautilus from opening a new window for every item I click on!  It's the folder items that cause the biggest pain here:

I can't stand having to close 10 windows during or after trying to get to some file deep down inside.  When you click on the "Help ---> About", it has this to say about itself: "Nautilus is a graphical shell for GNOME that makes it easy to manage your files and the rest of your system."  Well, wasting my time with extra windows is most definitely not what I'd call 'easy' when it can be done so much neater and quicker using the CLI shell instead; where you can perform commands on, or just check for the existence of, files down inside a folder without ever having to 'cd' to that location!

Daniel.

---

### Post by doitashimashite on 2005-03-05
Applications -> System Tools -> Configuration Editor
Browse through the tree:
apps -> nautilus -> preferences
Check 'always_use_browser'

---

### Post by landotter on 2005-03-05
You can always just middle click on an item with the middle mouse button (wheel, or if you have only two buttons, click both), that's what I do--it helps to have nautilus set to single click when doing this. this will close the parent window and open the new window.

Right clicking a folder and choosing "browse" will open up a browser and I've got a launcher on my panel that starts a browser version of nautilus, the command is "nautilus --browser"

For quick and simple file management, I like spatial, but having the traditional browser option close at hand is nice.

(I also highly recommend that everybody apt-gets emelfm, a traditional two pane manager for powerful file management.)

---

### Post by bored2k on 2005-03-05
[QUOTE=landotter]You can always just middle click on an item with the middle mouse button (wheel, or if you have only two buttons, click both), that's what I do--it helps to have nautilus set to single click when doing this. this will close the parent window and open the new window.

Right clicking a folder and choosing "browse" will open up a browser and I've got a launcher on my panel that starts a browser version of nautilus, the command is "nautilus --browser"

For quick and simple file management, I like spatial, but having the traditional browser option close at hand is nice.

(I also highly recommend that everybody apt-gets emelfm, a traditional two pane manager for powerful file management.)[/QUOTE]
 hey that emelfm is quite nice thnx landotter

---

### Post by thestarman on 2005-03-06
Thanks for all your answers... It's much easier now following what you advised. I used Synaptic to get emelfm, but probably won't use it as often as Nautilius. Had to update 3 other files, so it was about a 4MB D/L to get it.  I used "Applications" --> "Run Application" (insert program name: "elelfm") to try it.

Daniel.

---

### Post by kassetra on 2005-03-06
[QUOTE=thestarman]but probably won't use it as often as Nautilius.[/QUOTE]

There's also [rox-filer]("http://www.gnomefiles.org/app.php?soft_id=725") (which is in synaptic)

If you don't like Nautilus, or it doesn't do everything you need, when you need it to, rox-filer is a nice alternative.

It does some really spiffy stuff and it's very snappy.
Here are some [screenshots]("http://rox.sourceforge.net/phpwiki/index.php/ROX-Filer").

:)

---

### Post by landotter on 2005-03-07
[QUOTE=thestarman]. I used Synaptic to get emelfm, but probably won't use it as often as Nautilius. 

Daniel.[/QUOTE]

You probably won't use it that often, but it's really small and handy. Especially when you need to make a bunch of symlinks or change the permissions on a bunch of folder recursively--something that can be annoying with nautilus. Remember, running "sudo emelfm" gives you some major power, use it carefully. ;)

I do like that nautilus is simple and elegant--it's what I use day to day to access my personal files. :)

---

### Post by cliff58 on 2005-03-09
[QUOTE=doitashimashite]Applications -> System Tools -> Configuration Editor
Browse through the tree:
apps -> nautilus -> preferences
Check 'always_use_browser'[/QUOTE]
 Thanks, doitashimashite! That's exactly what I've been missing. Probably the best way to go for those who have to go back and forth between Linux and Windows a lot too!   :grin:

---

### Post by AndyGates on 2005-03-12
Oh yes.  That and "tree" view and you've got one fast window that's really useful.  Great tip, thank you very much  :smile:

---

### Post by bryan986 on 2005-03-17
when I run "nautilus" it comes up in tree mode, but when I try to do "gksudo nautilus" I cant get the tree mode to display, how can I get this to work?

---

### Post by landotter on 2005-03-17
[QUOTE=bryan986]when I run "nautilus" it comes up in tree mode, but when I try to do "gksudo nautilus" I cant get the tree mode to display, how can I get this to work?[/QUOTE]
 "sudo nautilus --browser" then use f9 to get a sidepanel with the tree.

---

### Post by wernst on 2005-03-19
I am a huge fan of Midnight Commander (mc), and I find myself going to a shell to run it all the time for file management.

There are a few Gnome clones of this, but the best I've found by far is Tux Commander, located at:

[http://tuxcmd.sourceforge.net/news.php](http://tuxcmd.sourceforge.net/news.php)

It works fast and looks good. You don't even need to compile it. Just download the Binary package, uncompress it, and copy the files to someplace like /usr/local/bin, and then it just works.

Briliantly.

-Warr

---

### Post by landotter on 2005-03-19
[QUOTE=wernst]I am a huge fan of Midnight Commander (mc), and I find myself going to a shell to run it all the time for file management.

There are a few Gnome clones of this, but the best I've found by far is Tux Commander, located at:

[http://tuxcmd.sourceforge.net/news.php](http://tuxcmd.sourceforge.net/news.php)

It works fast and looks good. You don't even need to compile it. Just download the Binary package, uncompress it, and copy the files to someplace like /usr/local/bin, and then it just works.

Briliantly.

-Warr[/QUOTE]
 I've fooled with TC and it's quite nice looking and all (I'm an Emelfm user) but how in the heck can you choose multiple files?! ctrl+click does not work to select individual files.

---

### Post by TravisNewman on 2005-03-19
[QUOTE=doitashimashite]Applications -> System Tools -> Configuration Editor
Browse through the tree:
apps -> nautilus -> preferences
Check 'always_use_browser'[/QUOTE]
 To quote Blade: "Some motha)*&$*&% always tryin' to iceskate uphill"

There's a much easier way to do this:
System Menu->Preferences->File Management->Behavior->Always Open In Browser Windows

I just don't understand why this much more simplified method isn't common knowledge like the configuration editor method is. You'd think the easy way would be more common, right? I guess one person found the conf ed way and spread it around and it stuck.

---

### Post by Davepet on 2005-03-19
>>I just don't understand why this much more simplified method isn't common knowledge

Possibly because it isn't being reported properly?

Once Nautilus is open, you need to go to "edit">"preferences">File Management->Behavior->Always Open In Browser Windows


I don't see a "System Menu-" on my system anywhere.but I *can* find:"Applications -> System Tools -> Configuration Editor"

In any event, I fail to see how either method is any easier than the other. 

AFAIC, single window should be the defalt setup, 

Dave

---

### Post by TravisNewman on 2005-03-19
Sorry, I was using Hoary-Speak. I don't have a Warty box around.
your way works, but so does mine. In fact I did it last night as I was posting. How about some benefit of the doubt?
In Warty:
Computer->Desktop Preferences->File Management->etc

"AFAIC single window should be the default"
There are many many reasons why it's not:
[http://osnews.com/story.php?news_id=7344](http://osnews.com/story.php?news_id=7344)
[http://arstechnica.com/reviews/os/gnome-2-6.ars/2](http://arstechnica.com/reviews/os/gnome-2-6.ars/2)

I can't find the many many links that someone posted here before about it. I think everyone should reat about spatial nautilus though, and why it was chosen. And once you use it for a day or two, you'll never want to go back.

---

### Post by Julius on 2005-03-19
[QUOTE=panickedthumb]To quote Blade: "Some motha)*&$*&% always tryin' to iceskate uphill"

There's a much easier way to do this:
System Menu->Preferences->File Management->Behavior->Always Open In Browser Windows

I just don't understand why this much more simplified method isn't common knowledge like the configuration editor method is. You'd think the easy way would be more common, right? I guess one person found the conf ed way and spread it around and it stuck.[/QUOTE]

I've always done it that way... I mean, if I want the behaviour of an app. to change, what's the FIRST place I'd look after? The preferences. 
Open nautilus..
Edit > Preferences > Behaviour...

Easy :p

---

### Post by Davepet on 2005-03-19
OK, I won't get to see hoary until the cd's come out, so I guess they've made some changes.

As to why that method is so popular: It's the only method shown in the unofficial Ubuntu stater guide. Since "always open in browser window" is not what  most folks would  look for in prefs when what they want is "always open in same window" , it's unlikely for people to stumble on alternate ways to set this this pref. 

When I first installed Ubuntu It was frustrating trying to find a way to change that behavior, I was glad to see it actually *was* there where Iit should be (edit>preferences) if I had only known what it was called.

As to that spatial thing I used it for several days until I finally found the way to turn it off (in the user guide). Good ridence. I see no reason not to "browse" my HD as I do web pages.It is counter-intuitive as well as productivity crippling to have to do two things (that are so similar) differently.
I set my system to single click everywhere for the same reason.

Dave

---

### Post by maubp on 2008-05-09
I know this is an old thread, but I've just had to hunt down this setting on a gnome 2.16 machine.  I knew it was possible because my old machine was setup this way, but I couldn't remember how to do it.  Google to the rescue!
> **Davepet said:**
> ... It was frustrating trying to find a way to change that behavior, I was glad to see it actually *was* there where Iit should be (edit>preferences) if I had only known what it was called.
I agree with this; I even found this preference but didn't think it was what I was looking for because "Always open in browser windows" meant nothing to me!  I think this check box in the GUI need to be renamed...

---

