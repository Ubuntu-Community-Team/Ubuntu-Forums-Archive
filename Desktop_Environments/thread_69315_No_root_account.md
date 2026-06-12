---
title: "No root account?"
date: 2005-09-26
forum: Desktop Environments
---

### Post by Buffbannana049 on 2005-09-26
I have a little experiance in Fedora Core 4, but I would still call myself a extream newbie to Linux...

I recently figured out enough in Fedore Core that I could use it and was for everything except gaming which I kept a dual boot with XP for... So I decided it was time agian to get something new and try and get it to work how I liked :rolleyes:.

I choose Ubuntu because I heard VERY little bad about it and it got my attention form the mailing the cd's thing, I ended up downloading it since it was only one CD, but anywaise I picked Ubuntu.

I am figuring it out all right, I miss my RPM's and Yum since I finally got to a point where I could use it and had some good repositories but I'm getting along... I'm stumbling through things and trying diffrient ways till something works like all good people lost in the dark with no idea what they are doing or where they are going... However appearently I don't have a root account... I don't remember setting it up and I tried user name: root password: (the only one I used in case I got the user names mixed up...) except it doesn't work... Now I'm having a hard time installing programs and there are all kinds of things there I need but can't get super user access to change...

So the question is: Is there a way to add a Root account after the install? And if not where in the install do I pick one? Since I have not done much yet it I need to reinstall it's not to big a deal, I just want to know where to look for it...

---

### Post by heimo on 2005-09-26
This should explain:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Zelut on 2005-09-26
First, welcome to Ubuntu.  I hope you get comfortable with it.  I love it vs the other distros that I've used.

Concerning the root account question.  ubuntu doesn't use a root account by default.  If you want to run root commands or have root permission use the 'sudo' prefix (ie; sudo reboot).  sudo kinda means 'superuser-do', so you can run single commands with root priveledges.  I prefer this method actually as I've stayed logged in as root without realizing it & screwed things up.  

When you run sudo it'll ask for your password (the password you used to login) and will only work for you.  If another user is logged in and has your password they will not have access unless they are added to the SUPERUSER list... but thats another story.

As far as replacing your RPMs.. I believe that is our equivalent to apt-get.  This downloads updates & packages from repositories.  You'll want to check out [www.ubuntuguide.org](www.ubuntuguide.org) for some tips on that.  try: sudo apt-get update to check for updates & sudo apt-get upgrade to upgrade those packages.

I hope this helped a little bit.  We're always here to answer questions :)

---

### Post by Buffbannana049 on 2005-09-26
Thank you both...

The first thing I have to say is this is a excellent community... VERY fast answers and so far people who don't mind helping and really know their stuff...

Thanks for the help and I got it working... I got myself full root access so I could move some folders involved with setting up java that somehow got the idea root owned them... 

Also I was able to follow the directions on the unofficial starter guide thing (here [http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)) and I now have EVERYTHING working... I just went down and took what I wanted and I know have things on Fedora that I never even thoght of... I have the nvidia drivers installed (something I never bothered with all the odd sounding things I would have had to have done), I have all my multimedia working, I have all the programs I could want... I have media in firefox working, I have thuderbird set up to get the mail from my Gmail account (I couldn't get thunderbird to install right the time or two I tried and Evolution wouln't work with Gmail so I used the web based interface... I have DVD playback (something I never got in Fedora either)...

I so far as just blown away... Also all the little stuff like a lot of stuff saved to my desktop not showing up till I logged back in and stuff are fixed.. So far I am blown away.. Very happy I made the switch... Thanks again.

---

### Post by orb_nsc on 2005-09-26
Good to see that it's working out for you. I consider myself more or less a newbie as well but I've found that it's easier to fix mistakes in Ubuntu than other distros...there were times with Redhat/Fedora or SuSE that I screwed up my system and couldn't figure out how to correct it, and ended up reinstalling.  I have always been able to fix problems with Ubuntu, and have never reinstalled.  I think the .deb system with apt-get makes a BIG difference.

---

### Post by Buffbannana049 on 2005-09-26
Edit: Thanks for the welcome, the more I use this and interact the more I realize I made the right choice...

Ok, I'm off to bed soon and I'm sure I'll be thinking about this all night...

I got it all installed but I am having some problems with some stuff and I though this thread would be fine...

Mplayer stops buffering at 25% (no matter what video or format) on one site and on another it just says playing (filename) in text and there is no video... I tryed playing some videos all ready on my computer and it freezes and gives an error code. I googled the code and it seems to have something to do with bio2jack or something... On their site they say they are having some problems with the newest version and that they are used by both mplayer and XMMS (which is just freezing when I hit play after making a playlist). So putting two and two (and two and two and two...) together I think it's that bio2jack... 

This brings me to the problems I don't know do to get rid of debian packages... Anyone want to tell me how to go from version .7 to .6? :confused: After that stay posted, I'll try and figure out everything thats wrong at once :razz:.

---

### Post by Zwack on 2005-09-27
Greetings,

Strictly speaking, it's not true that there is no root account in Ubuntu.  But using Sudo you don't need to know the root password.  

If you are Unix literate you might have come across the command su (switch User) which without any arguments switches you to being root.  So su - ha would switch you to the account of user ha (provided you knew the password for that user) and su - would switch you to root (again, with the password).  sudo does something similar but it uses a configuration file (/etc/sudoers) to see who has permission to do what.  It also asks for your own password, so if you have permission then you don't need the root password.  Normally sudo is used as sudo <command)> but another common option is sudo -s which will give you a root shell.  sudo does remember that you provided a password for about 5 minutes, so you can usually run sudo <command> several times wiithout having to provide the password every time.

The easiest way to remove packages from Ubuntu is using Synaptic (System -> Administration -> Synaptic Package Manager).  Find the package you want to remove, Right click on it and select "Mark for complete removal"  To force a different version use Package -> Force Version, but think carefully about it as there is usually a very good reason that a version has been upgraded.

I hope that this helps.

Z.

---

### Post by Buffbannana049 on 2005-09-27
I like the package managment... I know fedora had stuff like Kyum but that one seems to work better... Also thats for the info for the root stuff, sometimes I just want to be able to do stuff, also sometimes the locked directories and stuff I like using the GUI to move stuff...

I updated it because it said there was a newer version but still no go...

[IMG]http://img.photobucket.com/albums/v47/Buffbannana049/Unsdfsdfsdf.jpg[/IMG]

There is the error, it happens after I open Mplayer, play a file in it, it freezes and then I go into the resource moniter and kill it... Anyone know what's causing it?

---

### Post by Dolphin on 2005-09-27
I don't mean to be rude, but I see the root question pop up on this forum once or twice a week.  Do people not use the search function?

---

### Post by Zwack on 2005-09-28
Dolphin, of course not...

Well... sometimes...

I do, but some people don't realise it's there, or just can't be bothered.

Z.

---

