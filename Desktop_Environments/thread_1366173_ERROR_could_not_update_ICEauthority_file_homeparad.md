---
title: "ERROR: could not update ICEauthority file /home/paradox/.ICEauthority?"
date: 2009-12-28
forum: Desktop Environments
---

### Post by cgb223 on 2009-12-28
hi, after unsuccessfully trying to give klamav root privilages (i tried gksu, sudo, gksudo, and Exec=gksu, Exec=gksudo, the last two from the advice on a different form on the root topic) and now when ever my computer boots into the desktop it states, "ERROR: could not update ICEauthority file /home/paradox/.ICEauthority" what does that mean? how do i fix it?  I tried completely removing klamav and reinstalling it, no luck.

I'm using Ubuntu 9.10.

thanks in advanced, quick response would be fantastic

Charlie B

---

### Post by K9. on 2010-01-11
I also have exactely the same error message problem everytime I startup as above.

Further info: 
- I have XP installed on another partition and can choose at beginning if I want to load that or Ubuntu 9.10
- I'm not sure if the "error" has something to do with my installing guarddog, which gives me these warning via terminal when running 'sudo guarddog'
kbuildsycoca running...
> Error: "/var/tmp/kdecache-u23" is owned by uid 1000 instead of uid 0.
Reusing existing ksycoca
Error: "/var/tmp/kdecache-u23" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-u23" is owned by uid 1000 instead of uid 0.


---

### Post by syncmasterpt on 2010-01-11
Hi!

The problem is that some KDE application or process was run as root, and so changed the permissions of the folder .ICEauthority to root:root when it should have permissions for your user.

In my case when logging in, at the KDE splash screen, it stopped at the Globe icon for ever.

To solve the issue, just let the system boot up, and
1) Press CTRL-ALT-F1 to go to a text console
2) logon with your user, let's suppose it is mike
3) run **sudo chown mike:mike .ICEauthority**
4) run **sudo /etc/init.d/kdm restart**

and you should have the problem solved.

---

### Post by K9. on 2010-01-12
Thanks,

But I get 
[B]
sudo: /etc/init.d/kdm: command not found[/B]

even though I entered 
[B]
sudo /etc/init.d/kdm restart[/B]

---

### Post by syncmasterpt on 2010-01-12
Sorry: 

 the correct command for setting permissions is:

 sudo -R chown paradox:paradox .ICEauthority

I suppose that paradox is your user name.

Also, are you using KDE or Gnome?

The last command is for KDE...

---

### Post by K9. on 2010-01-12
I'm using gnome (I think!) - ubuntu 9.10 - so that would explain the second command problem.  What would the correct one there be?

[The first posters username is paradox, but I adjusted for that.... and that command seemed to go ok.]

Thx

---

### Post by syncmasterpt on 2010-01-12
Well I use KDE (Kubuntu), so not sure if the command would be gdm, but anyway, with a reboot, it should work... If not, the problem is other.

---

### Post by K9. on 2010-01-12
I downloaded and installed KDE now , restarted an ICEauthority message no longer appears.  I think maybe changing the wallpaper / background without proper rights was the culprit.

Thx for help.

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
 sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
with thanks to all who helped me,
Phil

---

### Post by cgb223 on 2010-04-08
much thanks for all the replies. got it working now. need to change the prefix to solved, brb.

---

### Post by boredbutter on 2010-08-11
I am running Ubuntu 10.04 [gnome] as was getting the same error. I followed some of the aforementioned advice and fixed the issue.

I opened my terminal and typed:

sudo chown -R user:user .ICEauthority

problem solved

---

### Post by panchtatvam on 2010-08-15
> **syncmasterpt said:**
> Hi!

The problem is that some KDE application or process was run as root, and so changed the permissions of the folder .ICEauthority to root:root when it should have permissions for your user.

In my case when logging in, at the KDE splash screen, it stopped at the Globe icon for ever.

To solve the issue, just let the system boot up, and
1) Press CTRL-ALT-F1 to go to a text console
2) logon with your user, let's suppose it is mike
3) run **sudo chown mike:mike .ICEauthority**
4) run **sudo /etc/init.d/kdm restart**

and you should have the problem solved.
-----------------------------------------------------------------------------------------
great ..i got my problem solved . the only difference being that i use Netbook Ubuntu Remix, so had to change the "kdm" in second line with "gdm" as was told.
so , thanks.
:D

---

### Post by Sciezyna on 2010-09-19
I am running GNOME and got the same message after the login


All what I did was:

1. Open terminal
2. sudo chown user:user .ICEauthority (where user:user is your user name and group)
3. logout login and all was ok.

J

---

### Post by FlickLives on 2010-10-29
I did the same as Sciezyna in #13 above, and all went well.  The reason I'm writing is to say that I believe I caused the problem by running a graphical program, i.e. with a GUI, with sudo, which ended up changing the owner of /home/user/.ICEauthority to root.  I'll need to remember to run any GUI program owned by root with gksudo or gksu in order to prevent this from reoccurring.

---

### Post by maxcel-pc on 2010-12-04
> **syncmasterpt said:**
>  run **sudo /etc/init.d/kdm restart**
.

Thank you syncmasterpt, worked for me except if one is running gnome, the command required is:

[FONT=Arial Black]sudo /etc/init.d/gdm restart


[/FONT]

---

### Post by clappr on 2010-12-11
I have tried all solutions and still get the message "Could not update ICEauthority file" on startup.  I changed and confirmed ownership and chmod to 644.  Still get the message.  This only started happing last night on 12/10/2010 after an update to 10.04 

Help!

The output of ls -l ~/.ICEauthority is:

-rwxr--r-- 1 richard richard 231003 2010-12-10 12:21 /home/richard/.ICEauthority

I actually chmod to 744, hence the -rwx for the user.

---

### Post by 23494asd on 2011-02-01
Can someone explain to me why i get this error when i initially install Ubuntu for the first time?   I use a pretty standard system, hardware wise and not had issues prior to 10.10.  I have to say the Ubuntu experience is kinda lacking.

---

### Post by petruha on 2011-05-19
Tried all proposals regarding permissions etc to no avail (on a fresh 11.04 64bit install).
"sudo apt-get install gnome-panel" - FIXED it at once for me.

---

### Post by alfirin on 2011-05-29
I have tried all these the last days, but still nothing works for me. Any other suggestions?

I also have the 'waiting for sound system to respond' problem. I don't know if they are somehow linked together

---

### Post by khatta on 2011-06-05
> **petruha said:**
> Tried all proposals regarding permissions etc to no avail (on a fresh 11.04 64bit install).
"sudo apt-get install gnome-panel" - FIXED it at once for me.

Gr8. This worked for me as well. Nothing else worked.

---

### Post by Moozillaaa on 2011-06-22
> **Sciezyna said:**
> I am running GNOME and got the same message after the login


All what I did was:

1. Open terminal
2. [COLOR=Red]**sudo chown user:user .ICEauthority**[/COLOR] (where user:user is your user name and group)
3. logout login and all was ok.

J
What is the proper syntax for this command?


> 
With this, set your $HOME directory (/home/username) permissions to  something appropriate (I used 755) and make sure all directories can be  listed with the "ls" command.What's the command to change permissions? What is an 'appropriate' permission setting?

---

### Post by aparrales on 2011-07-16
Changing the group/user worked for me on Lucid.

Thanks for the solution.

---

### Post by HoLiC on 2011-08-17
I did an update on ubuntu 11.04 and got the problem

I try this but didn't work to me... (as example: username = "user")
```
sudo chown user:user ~/.ICEauthority
```

i cheked my /home/ folder with command ls
```
ls -la /home/
```

i was surprised because my home folder had another owner (1016, it wasn't my username) so i turned it back to my ownership ("user")
```
sudo chown user:user /home/user
```

and then of restarted the system everything is fine now

---

### Post by agillator on 2011-08-28
I just ran into the problem. None of the suggested remedies worked until I discovered something had changed the ownership of my home folder to, as it happens, 1016, the same as HoLiC and others. Something magic in that user number? At any rate, I corrected ownership of the home folder and everything is now ok. So, for those still having the problem, try checking the ownership of your home folder (and the .ICEauthority file, if necessary) and correcting that if in error. Assuming the user name and group name of 'me', as others have said, sudo chown me:me /home/me

---

### Post by lon3lyliv3r on 2011-10-08
changing permissions of the particular file .ICEauthority did not work for me.

changing permissions of my home folder /home/john did work.  

the steps suggested by HoLiC fixed it!

For people that may be confused, my username is john, i had to type:

sudo chown john:john /home/john

to fix the problem.

---

### Post by rahmanian on 2011-11-01
changing permissions of the particular file .ICEauthority did not work for me.

changing permissions of my home folder /home/mohsen did not work for me. 

sudo chown -R mohsen:mohsen /home/mohsen/.* did not work for me.

and some other thinks :(

How to fix this problem? 
I'm very sad. :(:(:(

---

### Post by starrtennis on 2012-07-07
> **Flos Headford said:**
> This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
 sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
with thanks to all who helped me,
Phil

Booting from a live cd does not allow me to access the hard drive, as far as I can tell. The home directory is /home/ubuntu so changing permissions would be moot?

I am running 10.04.3 btw.

I did uninstall nautilus, however. This removed the errors at graphical login. However, now NOTHING shows up (besides the gnome wallpaper in the background).

I changed the permission of the home directory (/home/mike) to mike, also.

I can't reinstall nautilus, I don't think, b/c internet is not hooked up. I'm not proficient in shell-based wireless, so to reinstall nautilus I'd have to funk around with that.

To rehash:
Errors previously mentioned. Uninstalled nautilus --> no errors, but no home screen.
No .ICEauthority file in home directory; only a README and another file with some info on the encrypted home directory.

See my other (perhaps misplaced) gripe at: [http://askubuntu.com/questions/129686/iceauthority-is-missing/160984#160984](http://askubuntu.com/questions/129686/iceauthority-is-missing/160984#160984).

Thanks.

---

### Post by oldos2er on 2012-07-08
Closed. Please don't bump old threads.

---

