---
title: "know nothing about emerald"
date: 2009-01-22
forum: Desktop Environments
---

### Post by crimlaw on 2009-01-22
I am running 8.10, but I have not idea if I am running Emerald, Metacity, or neither.  How do I figure this out.  If I am not running either, how do I install emerald?

Thanks!!!

---

### Post by gettinoriginal on 2009-01-22
Emerald can be installed from Synaptic.  Also install Compiz Fusion Icon, with this you can select which window manager and which window decorator to use.

---

### Post by crimlaw on 2009-01-22
Ok, I got emerald, not sure about Compiz Fusion Icon.  I put it in the search, and something called "compiz fusion icon" did not come up specifically, so I am not sure what to install.  

However, now that I have Emerald, where can I find themes to use with 8.10.  I know there are a bunch of sites out there, but which one will give me the most options? 

Thanks.

---

### Post by gettinoriginal on 2009-01-22
There are alot of tutorials out there, but I am sending this one so that being new, you can set up more than Emerald.  But to start on this, scroll down until you see "Setting up Emerald".

[http://ubuntuforums.org/showthread.php?t=856190&highlight=emerald+themes](http://ubuntuforums.org/showthread.php?t=856190&highlight=emerald+themes)

P.S. Make sure that anything you do ie: installing medibuntu repositories that you edit them for your distribution (edit out Hardy and put in Intrepid).

---

### Post by crimlaw on 2009-01-23
Thanks for that post.  I skimmed it right now before heading to a late meeting.  I am going to spend my friday night reading the entire post and taking from it what I need.  

I am newer to Ubuntu (been using for about three months), and I am a very basic user.  I usually ask you guys for help when I have a problem, get the answer, and just apply the answer without really understanding what I am doing (no idea about command line or its full potential, don't know what repositories are/do).  Do you know of any guides like the one you suggested that can explain some of these things to me in really beginner terms.  

I have thought of buying a "Ubuntu for Dummies" book, but since I just upgraded to 8.10, I need to wait for the new version to come out.

Thanks again.  I will put "solved" up there when I get through the post.

---

### Post by gettinoriginal on 2009-01-23
I am 61 and have only been using Ubuntu exclusively for about 1 year.  Let me pass on some things I bookmarked that helped me understand things better.
[https://help.ubuntu.com/community/Glossary](https://help.ubuntu.com/community/Glossary)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=73885&highlight=linux+commands](http://ubuntuforums.org/showthread.php?t=73885&highlight=linux+commands)
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Well, that should give you the basics, any more questions, just ask.  :p

---

### Post by crimlaw on 2009-01-23
glancing at these sites . . . awesome.  Thanks so much.

65 eh?  Now, don't take this the wrong way, but that is impressive.  

I am 40 years younger, in my 3rd year of law school, and I am trying to learn this stuff for a hobby to keep me distracted from reading about divorce all day.  

Plus it is impressive to tell friends, although my fiance just thinks I am a dork.  ;)

Again, thanks for all of the advice, I am going to digest it as I go along.

---

### Post by crimlaw on 2009-01-23
ok, I followed the directions in your first post.  I went ahead and installed a lot of those programs from the first part, even though you suggested I skip to the "emerald" section.  Should have obeyed your advice.

Here is the problem now:  Firefox is all weird.  It changed my fonts, I can't change them, and it got rid of my bookmarks, and I can't save new ones.  What happened?  How do I undue whatever I did?

Thanks!!!

---

### Post by gettinoriginal on 2009-01-23
hmmmmmmmmm, went back through the site, and cannot find anything that specifically addresses firefox. Do you remember what of that stuff you did ??

---

### Post by crimlaw on 2009-01-23
holy crap, this is awful.  Firefox crashes when I try to open certain items form the menu bar, and it will restore my last sessions.  

Okay, here is what I did:

I followed the first part with Software Sources.  I checked what he recommended

then I ran the command line to install some of the programs:  multimedia codecs, Media Player, Catfish, Music player, wine, start up, localpurge (think that is the problem), and xchat.

Got any ideas?  I posted this question elsewhere, but no help so far.

---

### Post by crimlaw on 2009-01-23
oh, and then I followed the directions for ciaro dock - which is not working anyway and creating another issue.

I received an error when I first installed it that said Cairo dock could not be installed or updated.  Now, it appears in Accessories -> System Tools. But, when I click on it, it opens a preference box and gets stuck in a loop when I try to close it by reopening every time I close it.

---

### Post by crimlaw on 2009-01-23
I think I might have to go back into windows, uninstall my wubi and start over

---

### Post by gettinoriginal on 2009-01-23
Ok, here is what we are going to do, that is to try to reverse what has been done:  Run this in terminal:
```
sudo apt-get remove vlc catfish audacious wine firestarter thunderbird rar unrar-free virtualbox-ose gparted xchat cairo-dock
```
I have removed all those that would not effect Firefox

Cairo Dock is another animal, and takes special care to set up, so I added it to be removed.

---

### Post by crimlaw on 2009-01-23
thanks - giving it a try

---

### Post by gettinoriginal on 2009-01-23
hehehe, thats why I only wanted you to do the emerald part to start with, some of the other stuff needs to be edited for ease and non conflict.  But just between you and I and about 10,000 other readers of this forum, I have managed to break my system 5 or 6 times and had to start over, thats part of the learning experience with Linux.

---

### Post by crimlaw on 2009-01-23
I don' think it worked, kept saying there was not sufficient space

I am just going to start from scratch.  Thanks for all of your help in this.  I am going to use those other links you suggested

---

### Post by crimlaw on 2009-01-23
I see your reason now.  Next time I will take your advice more seriously

---

### Post by gettinoriginal on 2009-01-23
Ok, good luck, and remember, it's a learning experience  ](*,):-\"

---

### Post by crimlaw on 2009-01-23
right . . . learning experience . . . never do something until you understand what you are doing.  :-k

---

### Post by gettinoriginal on 2009-01-23
Well, if we waited till we knew what we were doing, it would work, so no learning involved ;),  after all, that's why they call it the "**practice** of law" \\:D/

---

