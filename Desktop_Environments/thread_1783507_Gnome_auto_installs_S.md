---
title: "Gnome auto installs :S"
date: 2011-06-15
forum: Desktop Environments
---

### Post by antrock101 on 2011-06-15
Hey there,

I'm creating a distribution for my work laptops, I'd rather do this myself than use another made distro.

I get it all running, i'm using server cd min with no packages selected.
I install 
Slim
E17
Gdebi
Synaptic
Firefox
Remastersys

It all works fine, slim selects e17 as windows manager.

However I make my iso using

remastersys dist

and then when i boot up the live cd it loads gnome not e17, I never installed gnome so i'm rather confused why it's loading gnome?

This also changes the default wm on my test pc it was built on.

Can someone help it's driving me mad, i've tried setting e17 up in slim to no avail.

---

### Post by antrock101 on 2011-06-16
just tried to remove gnome nothing changes

---

### Post by antrock101 on 2011-06-17
I was wondering if any of the packages added gnome, any idea?

---

### Post by 23dornot23d on 2011-06-17
You probably want to be looking at the way E17 starts up in its own window manager
using **[Entrance]("http://trac.enlightenment.org/e/wiki/Entrance")** .....

gdm is usually started and dictates what happens at login not sure if slim is similar
or if its due to remastersys ( but the _*[remastersys forum]("http://www.geekconnection.org/remastersys/forums/")*_ is quite good too for these type
of questions ). 



Also other things that might affect it - what system are you running from when you build it and what system is your main administrator using .... only when I build a distro and autologin using remastersys it will login to the last users session I was using when I create the ISO for it ....

---

### Post by antrock101 on 2011-06-17
I start from scratch, I only install xorg and e17 this is all on a seperate laptop, and the iso is made and burned in e17

---

### Post by antrock101 on 2011-06-19
ok this makes no sense, I asked on the remastersys forum and they suggested my e17 wasnt set up properly so when i make a new user it uses gnome, i thought you had to only install it. However I changed to fluxbox (much better) added exec startfluxbox in the xintec file and nothing still boots in gnome. this is driving me made and there no real documentation can someone help me before i throw this out the window.

---

### Post by 23dornot23d on 2011-06-20
You have probably already searched for [COLOR=Red]***[E17 and Remastersys]("http://www.google.com/search?client=ubuntu&channel=fs&q=e17+remastersys&ie=utf-8&oe=utf-8")***[/COLOR] ... but this is the link - as there were some success stories ....

I have not got it to boot directly into E17 before ....

But I do have E17 in the list to choose from with LXDE UNITY and GNOME-SHELL ....

Autologin as a User has been a problem just lately ...... maybe that is what is causing
most of the issues here ...... 

Some Dvd's that I have seen created just stop at the login ....... but by killing the greeter
it will let you in using htop on past Dvd's ......

I could not see where you posted on the Remastersys Forum ...... do you have a direct link to the thread ...... would like to know in more detail what is happening ....... maybe screenshots or output from the log that remastersys creates when it runs ......

---

### Post by antrock101 on 2011-06-20
I am at work presently, discussing the deadline with my boss. I've just moved to fluxbox so I have a whole host of new searches to do. It also seems I need to copy all the hidden files from my home folder to ect/skel aswell. 
 
[http://www.remastersys.com/forums/index.php?topic=1477.msg8210#msg8210](http://www.remastersys.com/forums/index.php?topic=1477.msg8210#msg8210)
 
here is the post on remastersys. I hope you can see the confusion

---

### Post by 23dornot23d on 2011-06-20
Ok I can understand his position .... we all are short of time ..... but sometimes it works out better for everyone if we make it .......

He mentions other Users .....

This is what I do ......

I create a new USER for a specific system ..... such that each one has a the system set up on it to run for either UNITY .... GNOME-SHELL or E17 ......

USER

Gnomeshell ...... runs only Gnomeshell ( and defaults to it )
E17 ................. runs only E17 ( and defaults to it )
UNITY ............. runs only UNITY (and Defaults to it )
etc .....

( Always do it in a clean partition with minimal personal information ....... on it if you use backup )
( you will probably find you need to use Firefox etc to get on the web for searches etc .... )
( Bleachbit should clean the majority of things out when you finish always run it before burning the ISO  )

First of all create a Remastersys Backup of your system ........ but try to keep it under 10 Gig ......
(doing it this way may give you what you want to install it quickly to other computers too)
You will be able to set it such that you have all administration rights over all the computers that you put
it onto .... and the root password can be yours alone .....

The Dvd then created will be around 3 to 4 Gig ..... depending on what you have .....

Things to do ........ use Bleachbit ..... both as root and use to get rid of as much as you can also Computer Janitor ...... but be careful as this may want to remove E17 ..... you have to look through the list carefully .... as it sometime just keeps the Ubuntu related things.

Once you successfully build a backup and it works properly ...... then you can go back and ask more questions ......

I do not know fully how it all works but am enjoying using it now as everyone is a success once its set up ok .......

Also ensure you have the files needed like squashfs etc ........ but I assume you have already done this as per the Remastersys instructions .....

If you create a ISO ....... load it up to [COLOR=Red]***[Linuxtracker]("http://linuxtracker.org/")***[/COLOR] and I will download it to see if I can
spot any obvious problems ....... best I can do at the moment .....

Maybe others have tried too .... maybe other people have more comments to help sort this
out ......

Hope this helps in some small way ......

---

### Post by antrock101 on 2011-06-20
thanks for the reply! I'm just going to spend a few days building it up again before I host it

---

### Post by antrock101 on 2011-06-28
ok, i got it working and booting into fluxbox, by removing metacity from the remastersys file. I've copyed all the files in home to ect/skel and when the live cd boots its seems to just revert to default

---

