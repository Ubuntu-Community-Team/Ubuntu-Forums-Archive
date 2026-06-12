---
title: "your session lasted less than 10 seconds"
date: 2005-12-01
forum: Desktop Environments
---

### Post by allbto on 2005-12-01
I have this problem when I start gnome: "Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem" in the error report appears that it wasn't possible to load the shared library /usr/lib/libgnome-2.so.0 because of a ELF header problem.
  What should I do? It's possible to solve the problem reinstalling gnome? How can I do it in the console with apt? 
  Thank you for any help,

al

---

### Post by az on 2005-12-01
boot into recovery mode and run

apt-get -f install

apt-get install ubuntu-desktop

If that does not work, reinstall libgnome2-0

apt-get install --reinstall libgnome2-0

If you do this from a normal login, use sudo.  From the recovery mode shell, you are root.


To get outof recovery mode and into desktop mode run

init 2

Unless someting went wrong with the install or youhave a bad cd, I would worry about your hard drive.  You may have some bad sectors.

---

### Post by ScreemingBlue on 2005-12-01
I had a similar problem, not sure of the exact error message but it was because I had re-installed ubuntu using the my original username and mounted my original HOME partition. So when I came to logon with the new username it was trying to access my original home directory and bombed out with a similar error message you are getting. 

FIX: sudo chown -R %username% /home/%username%

Hope this helps..

Cheers

---

### Post by ringding on 2005-12-01
Found the solution HERE   [http://www.ubuntuforums.org/showthre...session+lasted]("http://www.ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted")

You need to change the permissions of the .ICEauthority file.......for some reason it seams that k3b might be the culprit....

```
sudo chown (username) .ICEauthority
```

---

### Post by anil_robo on 2005-12-01
I had a similar problem soon after installing a window manager. Apparently I could not see anything on the screen. So I uninstalled that app by shifting to recovery mode and using sudo app-get remove command. But when I restarted my system, I got error message: your sesssion lasted less than 10 seconds.

I restarted system again, and while logging in, I clicked the SESSIONS button just below my username login, and chose GNOME failsafe. And everything has worked fine since then.

---

### Post by saz on 2006-07-30
i get about the same error, but instead of the ICE file, i get this:

"error while loading shared libraries: libasound.so.2: cannot open shared object file: no such file or directory"

anyone can help?? :confused: :confused: :confused: :confused:

(i'm running ubuntu dapper)

---

### Post by saz on 2006-08-01
problem solved :)

---

### Post by adotei on 2007-08-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/93613](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/93613) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I know its been a while since this thread was started. I had the same problem recently with the usual "Your session lasted less than 10 seconds .... ". However, I tried the solutions listed above and they didn't work for me. It might just be that it was a different issue causing the error. 

I think my problem was that my saved gnome-session file had been corrupted or was trying upon logging in to load a program or run a script that was corrupted. I had to delete the saved gnome-session file 

~/.gnome2/gnome-session

and restart the computer. Upon logging in again, the error was no more. But I also had to manual run my usual startup programs such as pidgin and skype. A small price to pay for this solution but no worries, the next time you logout a new saved session file is created and thus when you log back in your start up programs are run.

Hope this works for some of you.

---

### Post by ST.x on 2007-10-04
> **adotei said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/93613](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/93613) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I know its been a while since this thread was started. I had the same problem recently with the usual "Your session lasted less than 10 seconds .... ". However, I tried the solutions listed above and they didn't work for me. It might just be that it was a different issue causing the error. 

I think my problem was that my saved gnome-session file had been corrupted or was trying upon logging in to load a program or run a script that was corrupted. I had to delete the saved gnome-session file 

~/.gnome2/gnome-session

and restart the computer. Upon logging in again, the error was no more. But I also had to manual run my usual startup programs such as pidgin and skype. A small price to pay for this solution but no worries, the next time you logout a new saved session file is created and thus when you log back in your start up programs are run.

Hope this works for some of you.
okay I want to try this, but in  ~/.gnome2/ I only have a file called 'session' not 'gnome-session', would this do the same thing?

---

### Post by topjohn on 2007-10-15
> **ST.x said:**
> okay I want to try this, but in  ~/.gnome2/ I only have a file called 'session' not 'gnome-session', would this do the same thing?

i had the same problem i did everything up to the delete "gnome-session".  instead of 

~/.gnome2/gnome-session

i deleted

~/.gnome2/session

this worked for me.  no more message after login.  hope that helps.

---

