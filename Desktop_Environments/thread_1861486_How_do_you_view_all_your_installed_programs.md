---
title: "How do you view all your installed programs?"
date: 2011-10-15
forum: Desktop Environments
---

### Post by KeithLM on 2011-10-15
I'm trying to get a handle on this horrible UI in 11.10.  How do you find all your programs?  I know there's a search, but I don't know the name of everything that's installed.  When I click on the button that brings up some apps, it has 10 or so random huge icons, I'd like to find something that shows me more categories and more programs at once on my display, not just a few, like every other OS.  Is there some way to do this in Ubuntu?  Is there a way to configure the main menus to show many small icons instead of a few giant icons?

---

### Post by Larkspur on 2011-10-15
After you've clicked "More Apps" and gone to the lens with three rows of large icons, look at the second one.  It should be titled "Installed".  Click the phrase "show more results" and all your programs will be revealed.  You can then filter them if you want.  If I were you, I'd also take the opportunity to move some of your often-used programs to the launcher bar, so you can open them later without opening the Dash.

---

### Post by KeithLM on 2011-10-15
Is there no way to change it so that I can always see all my apps without clicking on multiple things each time?  It's very frustrating while setting up a new system to have to jump through so many hoops to get to all the various programs so I can try and figure out what I can and can't do with this. Like I believe there are programs that will help configure graphics and network settings, but I have to keep hunting for those and every time I open one app, I have to go through all the clicking again to get to another app.

---

### Post by apollothethird on 2011-10-15
> **KeithLM said:**
> Is there no way to change it so that I can always see all my apps without clicking on multiple things each time?  It's very frustrating while setting up a new system to have to jump through so many hoops to get to all the various programs so I can try and figure out what I can and can't do with this. Like I believe there are programs that will help configure graphics and network settings, but I have to keep hunting for those and every time I open one app, I have to go through all the clicking again to get to another app.

Hi, KeithLM.  From your description of having problems finding the apps, you might be missing these couple of clicks:[INDENT] [I]**[COLOR=Blue]Dash home -> More Apps -> Filter Results -> [Category you want] -> [App by name][/COLOR]**
[/I][/INDENT]The next time you won't even have to click on Filter Results, just click:[INDENT] [I]**[COLOR=Blue]Dash home -> More Apps -> [Category you want] -> [App by name][/COLOR]**
[/I][/INDENT]Also the OS will remember your frequent Apps.  The next time you'll just have to click:[INDENT] [I]**[COLOR=Blue]Dash home -> More Apps -> [App by name][/COLOR]**
[/I][/INDENT]You'll not only see your installed applications, but you'll also see suggestions from the repository.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by KeithLM on 2011-10-15
I'm finding those, it's just four clicks to do what should be one or two.  I should have an option to go to that easily, every time.  And why waste space with four 200 pixel icons, or whatever they are, they're just huge and the icons don't scale well so they look ugly, I want more options and I can't help but believe that in a modern OS those options would be available to me.   

With 11.04 I switched back to the older gui, and easily figured out everything in there even though I hadn't used an Ubuntu gui before.  It was so much cleaner and simpler and straight-forward and informative and provided access to everything in a simple, understandable manner.

---

### Post by apollothethird on 2011-10-15
> **KeithLM said:**
> I'm finding those, it's just four clicks to do what should be one or two.  I should have an option to go to that easily, every time.  And why waste space with four 200 pixel icons, or whatever they are, they're just huge and the icons don't scale well so they look ugly, I want more options and I can't help but believe that in a modern OS those options would be available to me.   

With 11.04 I switched back to the older gui, and easily figured out everything in there even though I hadn't used an Ubuntu gui before.  It was so much cleaner and simpler and straight-forward and informative and provided access to everything in a simple, understandable manner.

I can find my apps faster with the Unity interface than I can with the older gnome-panel (of version 10.10).  You mentioned it takes 4 clicks.  I hope those for clicks can calm some of the aggravation of the initial rant of (" It's very frustrating while setting up a new system to have to jump through so many hoops to get to all the various programs").

By the way, I count the clicks.  It might take as many as four clicks the first time.  But subsequent calls can almost always be done in three.  I'll try to see if I can find a way to get it down to two.  I don't think we can go lower than that.

By the way you can also setup a short cut to "/usr/share/applications".  Check out:

```

nautilus /usr/share/applications

```There you have all your applications a single click away after bringing up the nautilus short cut.  You can actually add the shortcut to the Launch bar.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by KeithLM on 2011-10-15
There's so little categorizing going on, that's one thing that's bad compared to the old one.  The other one is that it's using up the vast majority of the screen, yet displaying so little.  I think I'd find it far less annoying to use if it just popped up a small list of icons rather than huge, badly rendered icons with huge amounts of space between them.  Is that some sort of accessibility option for people with poor vision?

---

### Post by apollothethird on 2011-10-15
> **KeithLM said:**
> There's so little categorizing going on, that's one thing that's bad compared to the old one.  The other one is that it's using up the vast majority of the screen, yet displaying so little.  I think I'd find it far less annoying to use if it just popped up a small list of icons rather than huge, badly rendered icons with huge amounts of space between them.  Is that some sort of accessibility option for people with poor vision?

I don't know why they are so big.  Maybe after people get used to them and put in feature request after having actually used them rather than just generally complaining, the appearance will become different and possibly user configurable.

But I'm sure, at present, they probably are trying to make sure that people can find the applications in the new interface.  Lot's of people (for some reason) are saying they can't find them.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by KeithLM on 2011-10-15
I don't know what to think.  Choice is a good thing, and now we don't have it.  But if we don't upgrade to 11.10 then when 12.04 comes along we'll have issues. 

My hope is that I can get things configured then never have to touch it again.  I run this as a file server, and generally don't use it day-to-day, and I certainly would not stick with this OS if I actually had to interact with it on a regular basis.  But right now I've somehow mangled my X config or nvidia drivers or something and I have to fix that.  Joy.

---

### Post by garvinrick4 on 2011-10-15
> **KeithLM said:**
> I'm finding those, it's just four clicks to do what should be one or two.  I should have an option to go to that easily, every time.  And why waste space with four 200 pixel icons, or whatever they are, they're just huge and the icons don't scale well so they look ugly, I want more options and I can't help but believe that in a modern OS those options would be available to me.   

With 11.04 I switched back to the older gui, and easily figured out everything in there even though I hadn't used an Ubuntu gui before.  It was so much cleaner and simpler and straight-forward and informative and provided access to everything in a simple, understandable manner.
You might find that after a bit of a learning curve you can navigate through Unity pretty
smoothly. I have anyway, Ubuntu has made a decision to go with the Unity interface and
Classic Gnome is a thing of the past ending with 11.04 Natty. Give it a go for a while and then make a decision, I did and is very nice for me now. I never even look at the icons
I just tap windows key and type in first couple letters of app and when first in line in Dash hit enter and app opens. Can navigate with alt/tab between open windows. Other
windows key and letter commands with left hand opens a lot of avenues. If you want
install something like docky until used to it. Can put your favs on dock and in launcher for easy choice of most used apps. Below is oneiric ppa for docky. I had docky at first
and now do need it at all but convenient for some, Gnome-shell and Unity.
[http://www.ubuntuupdates.org/ppa/docky?dist=oneiric](http://www.ubuntuupdates.org/ppa/docky?dist=oneiric)

---

### Post by dhysk on 2011-10-15
KeithLM I feel your pain.  I've been using ubuntu as a mains system on my desktops and laptops for over 4 yrs now.  I didn't really even use the old UI really since I had configured it just how I liked it and how I liked to work.  I kept it with 11.04 but this time I'm trying to use it for 30 days to see if I find it handy.

I think this would be great on a device with a small screen or limited input options like a touch screen or a netbook.  But for my 2x24 inch monitor setup this UI just doesn't make sense.  It takes up WAY to much room and gives me 0 information.  Switching between windows is a pain, switching between desktops is even worse.  I often run 4-5 windows a desktop over 2-3 desktops.  I have to do 4x5 times the movements like clicks and traversing the screen with the mouse to do the same tasks as before.  

It is frustrating at best and my wife, who cares little to nothing about UI's and rarely uses a computer anyway, doesn't even like it.

So anyway I'm giving it a go but 'Unity' is nothing more than a joke and a hippy catch phrase.  Formula 1 cars can not go rally racing and netbook displays do not belong on the desktop......  There is no 1 fits all...

---

### Post by garvinrick4 on 2011-10-15
> I kept it with 11.04 but this time I'm trying to use it for 30 days to see if I find it handy.
That is good you are giving it the proper grace period for a learning curve, some do not.
I remember the first time I was looking at a mac and thought what is all these things
on the screen and how do they work, where is the command line. What is going on, and
now look Windows got in the game with icon driven machines. Well the rest is history, but
I sure thought they were ridiculous at first. Maybe one day Linus Torvalds and Mark Shuttleworth and Unity will be the household names instead of Bill Gates and Windows,
never know that is for sure. If we could predict the future we would still own Apple shares from 5 years ago and sitting on the Nest Egg all fat and happy.

---

### Post by KeithLM on 2011-10-15
> **dhysk said:**
> 
I think this would be great on a device with a small screen or limited input options like a touch screen or a netbook.  But for my 2x24 inch monitor setup this UI just doesn't make sense.  It takes up WAY to much room and gives me 0 information.  Switching between windows is a pain, switching between desktops is even worse.  I often run 4-5 windows a desktop over 2-3 desktops.  I have to do 4x5 times the movements like clicks and traversing the screen with the mouse to do the same tasks as before.  
...
So anyway I'm giving it a go but 'Unity' is nothing more than a joke and a hippy catch phrase.  Formula 1 cars can not go rally racing and netbook displays do not belong on the desktop......  There is no 1 fits all...

I'm using a widescreen 20" display, and if they are really aiming this for the lowest common denominator, well that's just stupid.  Even when you get to the point of seeing all the apps you have to scroll and scroll because they are all spaced so far apart.  

Like I said, I'll tolerate it, but there's no chance that I'd ever consider moving my laptop or primary desktop to this.  Why would I?  It's painful at best.  It's a very shortsighted move, and when I started with 11.04 a few months ago and ran into it I immediately looked into why the UI was so broken and found the classic desktop and switched.  When I read Ubuntu was going to be forcing this on everyone, and I couldn't see anyone making positive comments about it, I was quite confused.

Oh well, what can you do?  For the moment I can't get X up and running as it is, and I can't find any info on how to redo the setup since I messed it up trying to get proper nVidia drivers on it.  This may require me to reinstall the OS.  If I'm going to lose all my configuration of the few apps I run on it, I may just switch back to Fedora.  Hell, my upgrade left me with a 2.6 kernel, so that process is just broken as it is.

---

### Post by stinkeye on 2011-10-15
I don't think unity is designed to launch apps in the way you want to use it.
Can't you just put your commonly used apps on the launcher and then use the dash to search for apps you seldom use.
Using the filter will give you categories.
There is also a classic main menu indicator if that's what you want.
[**_[COLOR="DarkRed"]https://launchpad.net/~diesch/+archive/testing/+packages[/COLOR]_**]("https://launchpad.net/~diesch/+archive/testing/+packages")

I find using the launcher in combination with kupfer (lightweight desktop launcher) a good solution.

---

### Post by dhysk on 2011-10-15
> **stinkeye said:**
> I don't think unity is designed to launch apps in the way you want to use it.


That's the issue with me.  Personally I didn't really like Gnome 2.3 either.  But I could tweak it and configure it so it would launch apps the way "I" wanted to.  It looked the way "I" wanted to.  Sure the underlying interface was good enough and it was easy for visitors to use as well.  But when I sat down everything I needed was right there, right now, right as expected.  

Now I'm thinking visitors, IE windows users, are not going to find it so easy to get ware they want.  Especially if I start modifying things.

Right now little things are irritating me though.  For instance....  with compiz and gnome 2 I could use my tilt wheel to change desktops all they way threw the cycle and back.  I use 4 destops so no desktop was more than 2 taps of the tilt wheel away.  Now even if I turn on the cube only the top 2 desktop will switch.  I than have to go down to the bottom 2 desktops in the wall switcher, than i can switch between those two.  Without the cube using the tilt wheel you cant go from desktop 1-4 because left one goes to desk top #2 left one more goes back to #1.  As far as I can tell there is no 'next desktop' button so one of the most productive features is now all together lost.

This 'little' thing was actually why I started using Linux more than windows.  It wasn't because of security or even customization really.  It was the ability to sort my work out into different spaces and flip between them seamlessly without clutter.

I do like the new login screen alot more though ;)

---

### Post by stinkeye on 2011-10-16
> **dhysk said:**
> Right now little things are irritating me though. For instance.... with compiz and gnome 2 I could use my tilt wheel to change desktops all they way threw the cycle and back. I use 4 destops so no desktop was more than 2 taps of the tilt wheel away. Now even if I turn on the cube only the top 2 desktop will switch. I than have to go down to the bottom 2 desktops in the wall switcher, than i can switch between those two. Without the cube using the tilt wheel you cant go from desktop 1-4 because left one goes to desk top #2 left one more goes back to #1. As far as I can tell there is no 'next desktop' button so one of the most productive features is now all together lost.
Have you tried in
ccsm > General Options > Desktop size 
changing your **horizontal virtual size** to 4 and **vertical virtual size** to 1.

---

### Post by oboedad55 on 2011-10-16
sudo apt-get install xubuntu-desktop

---

### Post by dhysk on 2011-10-16
> **stinkeye said:**
> Have you tried in
ccsm > General Options > Desktop size 
changing your **horizontal virtual size** to 4 and **vertical virtual size** to 1.

lol I didn't even know that was in there.  Always did it threw right clicking the desktop switcher on the panel ;).. I was wondering how to change the # of desktops.  Unfortunately the desktops in that layout make the work space switcher, that I kinda like, completely pointless now ;(.. 

problem #1 solved.  Now you know how to auto hid the top panel?

---

### Post by stinkeye on 2011-10-16
> **dhysk said:**
> lol I didn't even know that was in there.  Always did it threw right clicking the desktop switcher on the panel ;).. I was wondering how to change the # of desktops.  Unfortunately the desktops in that layout make the work space switcher, that I kinda like, completely pointless now ;(.. 

problem #1 solved.  Now you know how to auto hid the top panel?

Get a strip of masking tape roughly 5cm longer than the width of your screen.
Attach to the left of your screen so as it will cover the top 20 pixels of your screen.
To hide the top panel run the masking across your screen and attach it to the right side.
To reveal the panel just detach the masking tape from the righthand side.
Problem solved. :idea: :rolleyes:

---

### Post by dFlyer on 2011-10-16
Just remember the names of the programs you usually run and under dash search start typing the name and it will pop up. No menus to navigate. When you don't know the name you can type something like disk or graphic and it will show all the programs that have graphic or disk in there search data. Give unity a chance and you will find in the long run it's very easy to navigate. When I first used it I had a lot of problems but stuck with it and now wouldn't use anything else.

---

### Post by dhysk on 2011-10-16
> **stinkeye said:**
> Get a strip of masking tape roughly 5cm longer than the width of your screen.
Attach to the left of your screen so as it will cover the top 20 pixels of your screen.
To hide the top panel run the masking across your screen and attach it to the right side.
To reveal the panel just detach the masking tape from the righthand side.
Problem solved. :idea: :rolleyes:

crap... i tried it but didn't have masking tape and used duct tape.... uhh you have any screen safe goo gone? ;)

---

### Post by KeithLM on 2011-10-16
> **dFlyer said:**
> Just remember the names of the programs you usually run and under dash search start typing the name and it will pop up. No menus to navigate. When you don't know the name you can type something like disk or graphic and it will show all the programs that have graphic or disk in there search data. Give unity a chance and you will find in the long run it's very easy to navigate. When I first used it I had a lot of problems but stuck with it and now wouldn't use anything else.

Well that would work if all the names made sense, which they don't always do, especially in the linux world.  Plus, I'm just trying to find places where I can configure desktop settings, change icon spacing, size, etc.  I don't know if those exist, doesn't appear to, but I expect them somewhere in any OS.  I'd also like to find something that tells me system info, mounted drives, other devices, graphics info, etc.  Still don't know if that exists.  I have to click through to all programs and scroll, scroll, scroll, to view them.  

It just doesn't make any sense to me to have a full screen display that shows so little info.  If they insist on showing four installed apps and four uninstalled apps, make it a small menu, don't take up the full screen.  That's just stupid, frustrating, annoying, and doesn't make one bit of sense.

---

### Post by apollothethird on 2011-10-23
> **KeithLM said:**
> I'm finding those, it's just four clicks to do what should be one or two.  I should have an option to go to that easily, every time.  And why waste space with four 200 pixel icons, or whatever they are, they're just huge and the icons don't scale well so they look ugly, I want more options and I can't help but believe that in a modern OS those options would be available to me.   


Hi, KeithLM.  Sorry for taking so long in getting back to you.  It has taken me this long (about a week) to get this worked out.  First the problem doesn't exist in Ubuntu 11.04, only 11.10.

Your applications are  two clicks away in Ubuntu 11.04, after having used a maximum of four to initially find what you want.  In Ubuntu 11.10 it's three clicks away until you add the “More Apps” feature back to the Launcher.

I don't know why it was removed and made almost impossible to put it back, but after many hours I've figured out how to get the functionality back.  I understand that having to perform an extra mouse search and click is a lot of work at the end of the day when you might have looked for a hundred applications and run a number of them multiple times.

With the method I'll present to you, two clicks and you have your application running.

First, you have to put the “More Apps” feature on the Laucher.  It takes a number of steps at present, but I'm going to work on a method to simply it.

The steps are:

1) Create a text file (mymoreapps.sh)
```

#!/bin/bash 
xterm -e sleep 2
xdotool keydown super sleep 0.1 key a keyup super 

```2) Create a launcher (mymoreapps.Desktop):
```

[Desktop Entry]
Type=Application
Terminal=false
Exec=/usr/local/bin/moreapps.sh
Name=My More Apps
Comment=Customized More Apps
Icon=/usr/share/app-install/icons/find_more_apps.png

```
You can use a program such as gedit to create the two files.

3) Drag the new launcher to the Unity Launcher side bar.

This should save some clicks and mouse movements in the future.  I hope to clean up this procedure and make it more functional.  If anyone discovers the script or routine that is called (by name) when you hit the (super-A) short cut to bring up the More Apps screen, I'd really appreciate it.

At present it's rather crude, could be cleaned up nicely with support from the developers.

By the way, the call to xterm (which doesn't do anything) appears to be necessary to take the focus away from the Launch bar when running the super-A keyboard short cut.  If someone can figure something different I'd really appreciate the input.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by KeithLM on 2011-10-23
Thanks for that, I've found some other info on apps that will fix up the gui a bit and I'm going to try those.  I'll give this a look and see if it helps.  I haven't actually touched that GUI in a week, and once I fix a few more things on that system hopefully I won't have to use the GUI much, if at all.

---

### Post by KeithLM on 2011-10-23
Well I installed compizconfig-settings-manager and gnome-tweak-tool and made a few minor tweaks and now Unity no longer works.  When I log in all I see is the default background, and absolutely nothing else on the screen.  I can log into gnome or Unity 2D just fine.  Wonderful.  If I can figure out auto-login and get xbmc running all might be well, or else I may have to reinstall again.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
/home/(username)/.cache/sessions

I did something similar in Xubuntu and deleted my session cache to return it to normal...

You also might have to edit your gnome-session....  I think there is a login manager you can use... but I don't use gnome/unity....

---

### Post by KeithLM on 2011-10-23
I hunted down everything related to compiz and deleted it and then I could finally log back into Unity.  What a pain.

---

