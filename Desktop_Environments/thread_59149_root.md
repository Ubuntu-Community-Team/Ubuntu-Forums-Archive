---
title: "root ??"
date: 2005-08-22
forum: Desktop Environments
---

### Post by Xalow1 on 2005-08-22
I cant get into root.  When I go in as 'Brendan' (my user) its all great but when I try to login to root from the main login screen on boot up, it says I didnt give myself permission to.  When I try to change the permissions in the control center, it wont let me change anything, because im not logged in as root.... and for network settings or anything, to change something you need to go in as 'Administrator Mode', once entering my password, I still cant change anything.

Help?  Some trick?

-Thanks,
Brendan

---

### Post by slada on 2005-08-22
The root account is disabled by default.

Try this:

[http://www.ubuntuguide.org/#setchangeenablerootpassword](http://www.ubuntuguide.org/#setchangeenablerootpassword)


The whole site [www.ubuntuguide.org](www.ubuntuguide.org) is very helpful for learning your way around ubuntu.

---

### Post by pixxelle on 2005-08-23
I have followed all the relevant instructions and I still can't change any settings (like Network, etc.) in Kubuntu.

I wanted to change my hostname (along with other things) and the admin button >login screen just keeps giving me a incorrect password message after entering my password ( I also tried a separate root password), and believe me I've checked it over and over. Kuser seems to be broken, too. Clicking the icon on the desktop will not bring up a window. The 'kdesu [whatever]' command just hangs in the console.

Last night I put Ubuntu 5.04 on an older machine at work and it installed almost flawlessly and worked fine. I like Gnome better than KDE anyway (less 'stuff'). I want to blow this Kubuntu install away and start over. How? I have a dual boot with XP and don't want to lose XP capability.

Thanks. Sorry for  being a bit testy, but this problem has been going on for way too long...

---

### Post by Lord Illidan on 2005-08-23
Ok, from a terminal, enter

```
sudo passwd
``` ,

and enter a new root password..

Then, reboot, go to fail-safe, and when it comes to the terminal login, type 
```
sudo startx
```,

and u have root access and u have a GUI...

---

### Post by pixxelle on 2005-08-23
This didn't work.

In Failsafe after entering 'sudo startx' and password, I got this:

X: Warning,  process set to priority -1 instead of requested priority 0
Fatal server error ........[a little stuff] ...remove /tmp/.x0-lock

I managed to figure out the reboot command.

I went looking for the file, but it didn't exist (which I wasn't surprised about)

Now what do I do?

---

### Post by h4rdc0d3 on 2005-08-23
You should prefer

 ```
sudo -s -H
```

or Applications > System Tools > Root Terminal

over

 ```
sudo passwd
su
```

Also, even if you set a root passwd, root is not allowed to log into gdm by default (because running an x-window (gnome) session as root is very insecure).

EDIT: You can substitute gdm/gnome with kdm/kde above and it doesn't change the meaning.

---

### Post by pixxelle on 2005-08-23
OK, I don't want to run a root account. I understand about the security issues. I just want to be able to change my settings!! I can't even change my background!

So I logged in again using the amended 'sudo' suggestion and then I got this when I tried to bring up the KDE Control center (where I want to change my hostname and it's all greyed out in the GUI).

root@[myhostname]:/home/lizt# kdesu kcontrol
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0

Look, I don't mind being a newbie and admitting it, but  I need to have some basic config going so I can figure out how things work.

Jeeez, Last night I put Ubuntu on the older machine at work, logged into Gnome, got to see the office 2k3Server domain like immediately, and logged into my notebook over that network. I couldn't hardly believe that was happening after what I'm going thru here at home. That's why I'd just like to wipe and begin over if I could, without losing my dual boot capability. Something seems very wrong here.
:mad:

---

### Post by tonysathre on 2005-08-23
you can reinstall without losing your dual-boot...just reinstall it over you existing ubuntu partition

---

### Post by pixxelle on 2005-08-23
'Kay, I stuck the Ubuntu install CDRom in and the machine  boots to the GRUB menu. ARRRGH!!!

I have to use the slave CDRom drive since my DVD Writer doesn't work in Linux. Booting from this Cd drive worked fine when all I had on the machine was a windows os.

The bios is set to boot off the CD Drive.

What to do now? I have to admit, I'm losing hair now by the handful... (big sigh)  ](*,)

---

### Post by tonysathre on 2005-08-23
you could try setting the one that works to master and try booting again

---

### Post by h4rdc0d3 on 2005-08-23
I can understand that you're frustrated... but you need to seriously calm down and breathe, okay?

I've been frustrated before too, but I made it through those times all right and I'm better off for it. Look, there's a whole community of **volunteers** that help others out on this forum, but if you keep acting like you're going to throw something if you don't get the help you so desperately need, we're just going to ignore you. But if you're courteous and generally show an attitude of wanting to learn instead of a "fix my broken computer now, dammit" attitude, then we'll help you.

The original complaint (and title) was "root ??". Upon further reading, I could tell that you meant that you were unable to give the root password in the KDE Control Panel and therefore unable to gain access to certain panels. I wish I could help you here but I use GNOME. I'm sure though that if you wait patiently (and I'd recommend silently unless it's an apology) someone knowledgeable in that area will probably come along and answer your question. That is if you didn't already convince them to ignore you.

While you're waiting I'd also recommend scouring these forums and the Internet for anybody else who might possibly have had the same or a similar problem. Also while you're waiting, you really ought to read [How To Ask Questions The Smart Way]("http://www.catb.org/%7Eesr/faqs/smart-questions.html").

As for your more recent booting problem, I have a question (if I may): Is the CD-ROM drive listed in your BIOS as a bootable drive and is it listed before your hard drive?

If that is not the case, it might explain why you arrive at GRUB.

**If you read all this and are aggravated more... stop using Ubuntu and stop posting here.**

---

### Post by pixxelle on 2005-08-23
[tonysathre]

Yeah...  looks like I'm headed towards opening the box again; I've had this one machine apart three times this week already....and I had considered that option of swapping master/slave... The DVD writer was already a big problem with the Kubuntu install (as in wouldn't install).

Thanks for your responses.

---

### Post by pixxelle on 2005-08-23
I posted in this thread because it seemed related to the problem I have had. I am not a newbie to forums and computers and I have been wanting to learn Linux for a few years. 

If you read one of my previous comments you would see that I had a very successful install last night on another machine. I do not expect anyone ' to fix my computer', I am just quite frustrated as I have been trying to get this one stable since Friday. And I am appreciative  that folks have responded to me.

And actually your suggestion was quite helpful.

Because I am a newbie I am having trouble even describing some of the problems so it would make sense to others. But I am trying anyway, and I'm not giving up.

I have printed out reams of material, visited two other forums and read two books before even attempting a Linux install. Please don't be patronizing.

> As for your more recent booting problem, I have a question (if I may): Is the CD-ROM drive listed in your BIOS as a bootable drive and is it listed before your hard drive?

Yes to both. The CDRom drive in question was used for my Kubuntu install.

> If that is not the case, it might explain why you arrive at GRUB.

If you read all this and are aggravated more... stop using Ubuntu and stop posting here.

I'm sorry if my frustration bothered you.  I am usually a very patient person.  You didn't have to reply, you know. Many thanks to all the others who did help.

---

### Post by tonysathre on 2005-08-23
so did what we mention fix the problem

---

### Post by Xalow1 on 2005-08-23
haha i see you all have had a little bitching going on by upset people? haha, i was the one that originally made this thread, and thank you for the quick replys.  I am trying to go into Control Center on Kubuntu, and let root be able to login from the main login screen when the comp starts up.  Currently I am only allowed to login to my personal account (brendan).  I can login to root through sudo -s -H then password, perfectly, in Konsole, but still need to allow root to login on the main login some how.  Also, when trying to edit things such as the login manager in control panel, Loging into Administrator Mode basically fails, it will tell me when I give it a wrong password, but everytime I tell it my correct password, it loads for a good 5 seconds, and then brings me back to the control center main page, just to repeat the process.

Any help would be greatly appreciated.  Thankyou.

-Brendan.

---

### Post by pixxelle on 2005-08-23
Brendan,

I'm sorry your problem is still there. It was this very type of login trouble that caused me to finally just reinstall (Ubuntu this time). I wasn't getting anywhere. I hope you are able to get help.

Tony,

I changed the order of my CD drives and and am happily in Ubuntu and Gnome right now. Thanks for your help and patience.

To every one else (even h4rdc0d3  ;-) ) Thanks for the suggestions. Maybe when I have some more experience under my belt, I'll be able to help folks, like you all helped me this time.

Now on to the big learning curve. It's good to know there are great volunteers out there! :)

---

### Post by alvonsius on 2005-08-24
[QUOTE=Xalow1]haha i see you all have had a little bitching going on by upset people? haha, i was the one that originally made this thread, and thank you for the quick replys.  I am trying to go into Control Center on Kubuntu, and let root be able to login from the main login screen when the comp starts up.  Currently I am only allowed to login to my personal account (brendan).  I can login to root through sudo -s -H then password, perfectly, in Konsole, but still need to allow root to login on the main login some how.  Also, when trying to edit things such as the login manager in control panel, Loging into Administrator Mode basically fails, it will tell me when I give it a wrong password, but everytime I tell it my correct password, it loads for a good 5 seconds, and then brings me back to the control center main page, just to repeat the process.

Any help would be greatly appreciated.  Thankyou.

-Brendan.[/QUOTE]

Hey there Brendan ... 

I must admit too that log into root account from "Administrator Mode" was somehow suck. But if you want to run KDE Control Centre with root account, you can use 

sudo kcontrol

or 

kdesu kcontrol

and FYI, you can use sudo for anything you want root to do ... anything ...  ;-)

---

### Post by Xalow1 on 2005-08-24
Thank you very much.  Now I know how to do that, however I still need to find out where I can let root login as a user, as a whole different session.  COmmand for that?  Setting to change somewhere that i cant find?

thanks

-brendan

---

