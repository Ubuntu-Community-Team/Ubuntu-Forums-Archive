---
title: "Switching to KDE from GNOME"
date: 2006-04-05
forum: Desktop Environments
---

### Post by jlhughes on 2006-04-05
I recently installed Ubuntu and I'm enjoying the experience. 

I would now like to try out the KDE desktop.  Do I need to reinstall using the Kubuntu package or is there a  less painful way to switch the desktop?

Thanks

---

### Post by aysiu on 2006-04-05
Go to Applications > Accessories > Terminal

Type ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Log out. Select "Session" and then "KDE." Log in again.

---

### Post by InExtremis on 2006-04-06
[QUOTE=aysiu]Go to Applications > Accessories > Terminal

Type ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Log out. Select "Session" and then "KDE." Log in again.[/QUOTE]

Sorry for this silly newbie-type question, but, I am in exactly the same situation as the original poster, and I would like to try KDE as well.

When you switch over using this method, will it keep the old GNOME desktop environment as well? Will all the packages I installed still be accessible as before?

Thanks!!

---

### Post by jlhughes on 2006-04-06
I asked the original question and the install went perfectly. 

The install will ask you which desktop to make default. I picked KDE.

Once you log out after installing KDE and reboot the machine (OK, maybe you don't have to reboot, but I did), you will get a new log in screen.

When I logged in, I was sent back to GNOME. It turns out that the desktop manager automatically uses your last desktop, which of course was GNOME.  

I logged out and returned to the log in screen. There is an icon for setting the desktop flavor you want. Once that was checked, the KDE desktop was used when I logged in.

So far, I prefer the bells and whistles of KDE, but I am a very new newbie.

---

### Post by InExtremis on 2006-04-06
[QUOTE=jlhughes]I asked the original question and the install went perfectly. 

The install will ask you which desktop to make default. I picked KDE.

Once you log out after installing KDE and reboot the machine (OK, maybe you don't have to reboot, but I did), you will get a new log in screen.

When I logged in, I was sent back to GNOME. It turns out that the desktop manager automatically uses your last desktop, which of course was GNOME.  

I logged out and returned to the log in screen. There is an icon for setting the desktop flavor you want. Once that was checked, the KDE desktop was used when I logged in.

So far, I prefer the bells and whistles of KDE, but I am a very new newbie.[/QUOTE]

Very cool!! I'm pretty new at this as well, although I'm not new with computers, for whatever reason, my only experience in 10+ years has been with Windows only, so this is very exciting for me to try!

I'm really looking forward to getting home after work so I can install a whole pile of new programs :)

Thanks for sharing your experience!

---

### Post by InExtremis on 2006-04-08
Now that I've successfully switched from GNOME to KDE ... how can I get rid of all the GNOME support files that I no longer need without jeopardizing the existing KDE files? Is it safe to remove packages using the Application Manager?

Thanks!

---

### Post by aysiu on 2006-04-08
[QUOTE=InExtremis]Now that I've successfully switched from GNOME to KDE ... how can I get rid of all the GNOME support files that I no longer need without jeopardizing the existing KDE files? Is it safe to remove packages using the Application Manager?[/QUOTE] [This](http://www.ubuntuforums.org/showthread.php?t=96046) might help.

---

### Post by wmgobuffs on 2006-04-08
Hello,
I've tried this sudo aptitude install kubuntu-desktop command a few times now, and I get the same error message every time: 

E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Suggestions?  I'd like to have gnome and kde on the same machine.

---

### Post by aysiu on 2006-04-08
Suggestion?
[Get a new sources.list](http://www.psychocats.net/ubuntu/sources)

Errors like that usually mean you have conflicting repositories.

---

### Post by wmgobuffs on 2006-04-10
[QUOTE=aysiu]Suggestion?
[Get a new sources.list](http://www.psychocats.net/ubuntu/sources)

Errors like that usually mean you have conflicting repositories.[/QUOTE]

Perfect, thanks!  I had copied over the wrong sources.list from the Unofficial Ubuntu Guide, which had Hoary items in it.  I like kubuntu much better!

---

### Post by chipwood10 on 2006-04-11
my problem is when i reboot (Just a hold over from windows thing I guess) it takes reboots and then takes me to a console screen. I then have to issue gdm and then i get the gui login screen. Once there I can select KDE. Does this sound right or am I missing something?

---

### Post by aysiu on 2006-04-11
[QUOTE=chipwood10]my problem is when i reboot (Just a hold over from windows thing I guess) it takes reboots and then takes me to a console screen. I then have to issue gdm and then i get the gui login screen. Once there I can select KDE. Does this sound right or am I missing something?[/QUOTE] You shouldn't have to "issue gdm" every time you restart.

Are you using this command? ```
sudo /etc/init.d/gdm restart
```

---

### Post by chipwood10 on 2006-04-11
no. once I log into the console screen i then log in as su. next i issue gdm and it fires right up to the login splash screen. I tried just issuing kdm from the console and it took it but just sat there. I still had to run gdm to get it to come up.

---

### Post by aysiu on 2006-04-11
[QUOTE=chipwood10]no. once I log into the console screen i then log in as su. next i issue gdm and it fires right up to the login splash screen. I tried just issuing kdm from the console and it took it but just sat there. I still had to run gdm to get it to come up.[/QUOTE] Next time it happens, don't log in as su. Log in as yourself. Then type ```
sudo /etc/init.d/gdm restart
``` See if that helps.

---

### Post by user1397 on 2006-04-12
[QUOTE=InExtremis]Sorry for this silly newbie-type question, but, I am in exactly the same situation as the original poster, and I would like to try KDE as well.

When you switch over using this method, will it keep the old GNOME desktop environment as well? Will all the packages I installed still be accessible as before?

Thanks!![/QUOTE]
Can someone answer this question please because I'm having the same problem!

---

### Post by tagg3rx on 2006-04-12
> 
Quote:
Originally Posted by InExtremis
Sorry for this silly newbie-type question, but, I am in exactly the same situation as the original poster, and I would like to try KDE as well.

When you switch over using this method, will it keep the old GNOME desktop environment as well? Will all the packages I installed still be accessible as before?

Thanks!!
Can someone answer this question please because I'm having the same problem!

Absoutly 
One cool thing is you can try every desktop manager on the market till you find one you like.  And each will retain the profile settings for each user per desktop environment.  At the login screen you get a drop down that lets you choose which DE you want to use.

I currently have Gnome, KDE, XFCE, and Enlightnment all installed and play with each occasionaly.  

But I must say KDE is IMO the best (espically for those of us coming from windows)

---

### Post by user1397 on 2006-04-12
[QUOTE=tagg3rx]Absoutly 
One cool thing is you can try every desktop manager on the market till you find one you like.  And each will retain the profile settings for each user per desktop environment.  At the login screen you get a drop down that lets you choose which DE you want to use.

I currently have Gnome, KDE, XFCE, and Enlightnment all installed and play with each occasionaly.  

But I must say KDE is IMO the best (espically for those of us coming from windows)[/QUOTE]
THanks for the reply.
Will having any programs that are gnome only, like automatix, affect the kde desktop?

---

### Post by GeneralZod on 2006-04-12
[QUOTE=erik1397]THanks for the reply.
Will having any programs that are gnome only, like automatix, affect the kde desktop?[/QUOTE]

They *should* be just fine but, as with all things in life, there are no guarantees :)

---

