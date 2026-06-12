---
title: "disabling asking for a password..."
date: 2009-01-19
forum: General Help
---

### Post by cwortman on 2009-01-19
I am so sick of it asking for my password for everything I need to get done. It slows me down. I am not an idiot and I know what I am doing. This feature was really cool at first (back in 7.10 when I started using it) but now that I know what I am doing for the most part, it annoys the piss out of me. Every time I need to update, when I want to install a new application, when I want to change something more than an icon set, the list goes on. It feels worse than Windows UAC imho. I logged in this should be enough. Both me and my friend here really dislike this "feature". Time for me to remove the training wheels.:guitar: Please pass the wrench. I am a big boy now. I have read about security issues but if you can't make a system more secure without asking for my password, the system is not more secure than anything else. Just way more annoying. Say 6 months from now a virus comes about and Ubuntu is used by less technically inclined people. It keeps asking for the password. The user will simply type it and move on about his business. Not a very far fetched idea as netbooks are gaining popularity.

---

### Post by aesis05401 on 2009-01-19
After your machine is 'set-up' you should really only be seeing passwords at logins and updates.
The whole point of your user-space is that you are sand-boxed mostly from the rest of the box... and if you want out of the sandbox you need a password.


What are you doing that is giving you problems?

---

### Post by cwortman on 2009-01-19
> **aesis05401 said:**
> After your machine is 'set-up' you should really only be seeing passwords at logins and updates.
The whole point of your user-space is that you are sand-boxed mostly from the rest of the box... and if you want out of the sandbox you need a password.


What are you doing that is giving you problems?

This solves nothing... I understand the idea of it but I like to try new applications. It is bothersome because every-time I need to start Hamachi I need to type my system password as it needs elevated privileges. Please can someone help me out Googling has lead me to a cornucopia of "its too dangerous don't do it".

---

### Post by cariboo on 2009-01-19
Are you asking for help, or is this just a rant? If you are asking for help, how about checking out these links:

[Sudo  without a password]("http:///ubuntuforums.org/archive/index.php/t-20724.html")

[How to use sudo without prompt for password (not_secure)]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29")

[RootSudo]("http://help.ubuntu.com/community/RootSudo")

You should read the last page as it explains  why sudo is a good thing.

Personally I have been using Linux since 1998, and I would really rather use sudo, then running as root all the time. Life sometimes gets in the way and when you get back to the computer, mistakes can be made.

Jim

---

### Post by cwortman on 2009-01-19
> **cariboo907 said:**
> Are you asking for help, or is this just a rant? If you are asking for help, how about checking out these links:

[Sudo  without a password]("http:///ubuntuforums.org/archive/index.php/t-20724.html")

[How to use sudo without prompt for password (not_secure)]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29")

[RootSudo]("http://help.ubuntu.com/community/RootSudo")

You should read the last page as it explains  why sudo is a god thing.

Personally I have been using Linux since 1998, and I would really rather use sudo, then running as root all the time. Life sometimes gets in the way and when you get back to the computer, mistakes can be made.

Jim

Thank you so much thats exactly what I was looking for. No it wasn't a rant but the most annoying part of Ubuntu to me and my friend who owns an Ubuntu machine too. We are both complete geeks with nothing better to do than to ruin our installs for the sake of learning! :lolflag:

---

### Post by cwortman on 2009-01-19
Sure mistakes can be made and after reading through those when was the last time you typed rm -rf / or chroot 000 /? I think both commands should be disabled even as root. Yes I type both commands on a daily basis just to ruin my pc muahahaha. I think a system with more privileges to install things from trusted sources shouldn't require passwords. Doing elevated things past user 300 even 455 requires the root password. Totally insecure if you take in the life gets in the way. If I am going to make a mistake something as silly as a password will not stop me.

---

### Post by cariboo on 2009-01-19
I really would suggest that you not follow the instructions, as you are never good enough to take off the training wheels, I know I'm not. 

The whole philosophy of security is to make it hard for someone to take over your system and use it as part of a bot net. Nobody cares about the data you have on your hard drive.  

None of my system have ever been cracked, but there is always a first time and I intend on waiting a long, long, long time before that happens.

If you aren't being challenged enough running Linux on one system, it's time for more computers. I currently have 2 systems running XP,  1 I triple boot windows7/Intrepid/Jaunty, 2 Ubuntu servers, a Mac G3 running Xubuntu, and just recently an old (ca 1998 ) compaq running AntiX.

edit: I also just built a mini ITX system, that is running Intrepid, that I use for a media system.

Jim

---

### Post by eightmillion on 2009-01-19
I'm of the opinion that if you have to ask how to disable security, you probably should not be disabling security.

---

### Post by cwortman on 2009-01-19
Awesome I solved it. I don't have anything totally of security related articles on this machine. Like I said previously relying on the user to enter a password for security purposes is completely insecure. Most people use common words as passwords. If the system is insecure to an attack in which would require a password the system is insecure to begin with. I log in typing my password. When I walk away I have a hotkey set up to lock it and have made it a habit to hit the lock key when walking away for any length of time. I could make a simple brute force macro to get a persons password and have it in no time. Or like I said you download a new virus it installs invisible as say .virus in /home and runs whenever you attempt to do something asking for a password, an inadequate person will simply type the password and move on about his business. For example Hamachi a completely legit program asks for a password because it needs user 455 to run. User 300 is not enough as it uses network resources. I am sure more and more applications of the like will pop up... Honestly Sudo is great but it has it's faults... and could be a whole lot better. I might take it upon myself to make a fork project which generally disallows stupid obvious commands from running and allows the rest of life to exist as it should...

---

### Post by EvilRobotDrew on 2009-01-19
one alternative is to change the sudo timeout to something like 1 hour or whatever you feel is appropriate ([http://ubuntuforums.org/showthread.php?t=183418](http://ubuntuforums.org/showthread.php?t=183418)), you will still need to use your password the first time but if you are installing lot of different programs, or doing a lot of admin stuff it may save a little bit of hassle for you. You could also look into changing your password, i keep mine short, consecutive on the keyboard, and make sure it is typable (is this a word?) with one hand. Granted, this is a laptop and not a server so i feel that i can sacrifice a little bit of security on the altar of convenience. 

I don't like the idea of disabling the password entirely, i can understand your desire, but i like knowing that if i let a friend borrow my comp that they cannot unintentionally do something stupid, it is worth a little bit of hassle. i would rather take a half second to type my password when updating then try to fix a problem caused by an unintentional command or stupid person.

---

### Post by cariboo on 2009-01-19
Damn, I wish I was young and smarter then everyone else **again**. :)

Jim

---

### Post by mcduck on 2009-01-19
> **eightmillion said:**
> I'm of the opinion that if you have to ask how to disable security, you probably should not be disabling security.
+1 for this.

Disabling security pretty much always means not understanding it in the first place.

"But I'm the only user on this machine and I own it" seems to be a common reasoning. But it's wrong, at least as long as the machine in question is connected to Internet. Disable security features and sooner or later you most likely won't be the only user any more.. ;)

If the only reason to disable passwords completely is one single program, you should disable passwords for that program, not for everything.

---

### Post by aesis05401 on 2009-01-19
Just a note to the original poster.  I am with the posters who are suggesting that running as root is not a good thing, but I also want to support experimentation... 

So just a suggestion.  VirtualBox OSE is a quick download/setup.  If you are going to run as root you could do it in a VM that could be replaced with the click of a button.  

There is no 3d acceleration so far as I know, but that is one of the few issues.  

I have several VMs configured and stable at any given time and literally just put up an Ubuntu server VM to experiment with some apache stuff.  It took me all of a couple minutes and boom - there it was...  I can throw it out just as easily.

Just leave the host system alone security-wise, though.. It just makes better sense :)

---

### Post by cwortman on 2009-01-19
Thank you for your posts. I guess I am the only one who sees that passwords no matter length and matter can be broken. Once Linux catches on idiots will use it. Stupid lazy people make up 90% of the population who can afford luxuries such as computers. Most people I know would make the password a name or iloveyou or something inane. Viruses will start to thrive because not everyone in the world is pure. All it takes is for someone else to realize this with the ability. Try as a desktop system for the sake of argument disabling remote login. Using Sudo to keep an entire system secure instead of a different security model for everything is again insecure. Say have 100 different instances of smaller more portable security protocols for the 100 different uses of the desktop computer model. Again I use this as a desktop not a server. Why do you treat it like one. I will continue to use Windows simply as Windows 7 does just this. Not saying FOSS fails and it works for you. I guess Linux is not for me. I like my Mac because they have had this very basic security model for quite some time. Much love to all the work put into it. It fails to meet my needs, albeit very basic to me, seems way too complicated to implement. I suppose it is asking too much for the amount of work to be put into a free product. In time I suppose it will be. I love it I really do. Tux is schmexy and as my server it is phenomenal. As a toy to configure to my liking of how I see as a desktop should look like it is amazing. When it really comes to the grind I guess so but better exists for my needs. I have in the past had viruses and spyware but the instances I can count on one hand. I am neither lazy or stupid but for a desktop I don't see this going anywhere. I see way too many issues people will run into. The general population which makes up our families. The ones who don't care and call you to fix it. I guess I am spoiled by XP and Mac for my desktop usage. Linux sits where it is most useful to me. In my closet running quietly Debian where I can access movies music and pictures and anything else I put on there from my DVR and other computers. Thanks for all the free beer and for what it is, it is simply the most amazing in it's league and un-touchable. For a general desktop for me however it fails because it is not in it's design and the work to put into it would be a lot to ask.

---

### Post by Andy06 on 2009-01-19
System>preferences>Users and groups. Edit the u8ser privileges tab takes care of a lot of these prompts. I agree that Linux is very annoying with this, more so than windows. When people criticise UAC, they don't realise that MAC and Linux are even worse (or better depending on perspective) in that regard. I wish I had UAC style admin OK prompts rather than admin password prompts.

Do let me know if you resolve you issue completely and how you do it.

Thanks

---

### Post by 3rdalbum on 2009-01-19
I think with your last post, you just demonstrated that you don't understand the security system behind Linux.

Windows has moved *towards* the Linux security model, not away from it. Mac OS X has the same security model built-in, with lots of backdoors so Apple engineers don't have to think about how to best design their software. The seperation between root and user is the way today's desktop operating systems work, and for very good reason; and if you don't like it, you should stop using computers now.

The problem with the people who use Windows is not that they are "stupid", it's that Windows XP doesn't encourage good security practice and there's no culture of educating the user about keeping themselves safe and secure. When they come to Linux, they learn about why the security system is in place, how to work within it, and by the end they hopefully know enough to not be a threat to others.

I think you should move back to Windows XP and run as an administrator account full-time. Just don't upgrade to Vista or Windows 7, because by default they try to encourage a good security practice that involves seperation between privileged and unprivileged users.

---

### Post by adamlau on 2009-01-19
There are applications where disabling asking for a password can be beneficial. For example, I always ran XP as Administrator. Having tired in the past of setting up NT in accordance to NSA recommendations and moving to 2K and doing the same, I customized an XP disk (under 400 MB installed) for my kiosk boxes to run. Very convenient!

---

### Post by Peter09 on 2009-01-19
Just remember that the easy option of running with low security brings with it the somewhat harder option of running virus and worm checking software, which is always a pain in the performance butt, especially if it fails to stop something.

The reason you have to Virus check windows is because of the negligible security on the windows O/S - microsoft should be ashamed of putting the IT world into the current defensive state it is in, and enabling the criminal activity that has resulted.

---

