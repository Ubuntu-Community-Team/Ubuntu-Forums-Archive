---
title: "mp3 and avi plugins for secondary account don't work"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Arael on 2005-06-28
Hi everybody,

I'm new in this forum, would like to great all users. Ubuntu is wonderful, I tried RedHat,  Slackware, FreeBSD, Gentoo, Arch and now I'm here. All of these are great distros but 
I never had quite all of my devices configured automatically. Ubuntu does...  \\:D/ 

I like so much GNU/Linux and usually maybe for my ignorance I saw that all distro has his own difficulties and problems that I had to solve by reading manuals, searching online and asking arround. That's why I'm here  ;-) 

When I first time tried to run an mp3 I realized that there aren't plugins for totem.
Searching a solution in the official wiki I found a Readme that advises to install totem-xine and needed codes. I did it and all worked fine for me. Before that I had aded an other account. In this account I can't use my plugins. I'm wondering why do I recieve warnings that says that there aren't plugins to play this file.
Why for the first account works and for the second don't?
The groups of the second account are the username group and audio group. Should I to add it to some other?
Should I to recreate my second account?

 :???:

---

### Post by felipe on 2005-06-28
where did you put your plugins? if they're inside your home then it's perfectly normal: the second account shouldn't see/use your personal files.

try to move the plugins in a "system wide" directory (such as /usr/lib/xine/plugins)

---

### Post by badboyz107 on 2005-06-28
Hey so I'm really really new at this linux stuff....

I did a new install and everything seems to be working as advertised except I cant get it to play mp3s or anything else....it says cant find the plugin

Where do I find this and HOW do I get them to work??

---

### Post by psychicdragon on 2005-06-28
Welcome to Ubuntu badboyz,

Mp3 support isn't enabled by default. Take a look at these two links and just follow the steps.

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

All the commands go in the terminal, which you can find by going to:
Applications > System Tools > Terminal

You should be able to play your mp3's in rhythmbox or whatever now.

The Ubuntuguide is a really great resource for a lot of other stuff as well. I would recommend starting at the beginning and making your way through it, you'll learn a lot of stuff.

---

