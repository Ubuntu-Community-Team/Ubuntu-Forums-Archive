---
title: "Heeelp!"
date: 2011-04-19
forum: Desktop Environments
---

### Post by kaourinio on 2011-04-19
[]("http://ubuntuforums.org/member.php?u=1281317")Hello Everybody
I have already posted two unanswered post, as you see  . This mainly a desktop problem  as my panels have dissapeared and I can't restore them. Maybe is  something easy to be fixed but I've tried a lot as you can see in  previous posts.
Thnks in advance for helping me!

Post 1:

                                                                                  "[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]                 **Missing Panels&Terminal not working after upgrade**             
                                                                After  upgrading ubuntu 10.04 above problems have arisen. The only thing I can  see at start up is bg image desktop and my files but no panels. I tried restoring them through terminal(ctl+alt+f1 or f2) but nothing happened.Terminal commands are not executed! 
It's very strange that in the past I upgraded same system from 9.04 to 10.04 and everything went good.
(While upgrading both times, I was asked if I wanted to maintain  menu.lst, and both times I replied keep local menu.lst-second choice. )
What about know?What going on?
IS there any way to restore my system in a previous state?
I though to change menu.lst or rewrite it but I do not have at least a live cd!
Also, I am a new user o f ubuntu if you consider that I using them almost one year!
Thank you
                                                                                                   
              
                                                                                                        
             Post 2:

                                                                                                   **"Re: Missing Panels&Terminal not working after upgrade**             
                                                                It seems that my case is a really "rare incident", judging from the 0 replies.:sad: 
But.....I can tell that every time I had any problem with ubuntu the last year, always an answer was hidden somewhere.
I suppose, that my system during update manager schedule for updating also upgraded my system.
Did anybody experience same problems after upgrading from10.04 to 11.04?
Can anybody help me to solve this problem indirectly?Either by restoring  my system to a previous state or by advising me on how to use terminal  (I mean this type of full-screen terminal ctr+shift+f1-6) in order to  execute some commands?Cause I can't execute commands (always saying that  
Can anybody advice on how to initialize gnome-terminal from desktop  ?(Neither, I  have panels to do it so nor shortcuts like ctr+shift+T are  working?
What should i do?
Thanks"

---

### Post by 3Miro on 2011-04-19
Go to the terminal (With Ctr + Alt + F1), then add a new user to your machine:

```
sudo adduser newuser
```
(change newuser to whatever name you want).

Setup a password for the new user and then reboot and try to login as the newuser. Check to see if the panels are OK then. If the panels are working, fixing it will be a smile manner.

---

### Post by samacaster on 2011-04-19
Curious as to why you would upgrade from a LTS release to a regular 6 month release. 10.04 LTS will be supported well after Maverick and Natty are not. Natty is not officially released yet, and there are bugs.

My advice to anyone wanting to go to 11.04 Natty is to back up the home folder and do a fresh install after it is released on the 28th.

---

### Post by kaourinio on 2011-04-25
Thanks for your help! 
sudo adduser newuser worked as to make a new user but it didn't fixed the problem at all.
It seems that  command order to make new users is working but if I type commands like killall gnome-panel nothing is done.
Anyway, I suppose the only solution is to install a new copy of ubuntu 10.04 and everyhting will be ok.
Thanks alot!

---

