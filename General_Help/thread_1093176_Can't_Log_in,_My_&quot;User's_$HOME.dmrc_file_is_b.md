---
title: "Can't Log in, My &quot;User's $HOME/.dmrc file is being ignored&quot;"
date: 2009-03-11
forum: General Help
---

### Post by srpayo on 2009-03-11
Hi guys,

I am aware that this error has already been reported before but I´ve tried all suggestions in all posts I could find and none worked for me.

Basically I made a stupid mistake by going to my top right corner and clicked on the properties of my username. Then I changed the default directory from /home/vegan to the same as the root one, thinking this would make my user root as well....

Anyways after a restart I now get the error:

User's $HOME/.dmrc file is being ignored. This 
prevents the default session and language from 
being saved. Files should be owned by user and have 
644 permissions. User's $HOME directory must be 
owned by user and not writable by other users.


If I continue with OK then other errors appear such as 

The GNOME session manager was unable to lock the
 file '/home/vegan/.ICEauthority'. 

After OK all errors I get to a default desktop (not my custom one) and nothing appears there, just the desktop wallpaper.

I´ve tried Ctrl+Alt-F1 to go to a terminal, then login with my username and pwd and typed the following:

sudo chmod 644 /home/vegan/.dmrc
sudo chmod 755 /home/vegan

sudo shutdown -r now

I still get the same errors and I´ve also tried other suggestions in other posts but still cannot fix the problem! I am desperate for a solution!

Any help would be much appreciated! 
Thanks!

---

### Post by philinux on 2009-03-11
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Hope that helps.
You must do things in the right order or the fix wont work.

---

### Post by srpayo on 2009-03-11
Thanks philinux,

I already tried that fix following the guide but still, after a reboot, I get the same error.

The following are the exact errors Im getting:

User´s $HOME/.dmrc file is being ignore. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User´s $HOME directory must be owned by user and not writable by other users.

Then I click on OK and get:

Could not update ICEauthority file /root/.ICEauthority

click on Close and get:

There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Click on Close and get a couple more errors that dont seem too relevant for this issue. In the end I get the default intrepid wallpaper but nothing else loads, not even the upper or lower panels...nothing at all!

I go to the Terminal and enter with my user and pwd, then type:

ls -l .dmrc

-rw-r--r-- 1 root root 0 2009-03-11 12:07 .dmrc

I dont know what else to do from here....help!

---

### Post by philinux on 2009-03-11
So when you followed the guide you logged out then logged in with no errors but on reboot the error comes back?

---

### Post by yeats on 2009-03-11
Looks like the problem is that you can't have root as your home directory.  Please see this thread:

[http://ubuntuforums.org/showthread.php?t=1092782]("http://ubuntuforums.org/showthread.php?t=1092782")

---

### Post by srpayo on 2009-03-11
Exactly, I pressed Ctrl+Alt+F1 to get to the shell and there I entered with my user ´vegan´and the pwd I gave it. then I am logged in.

vegan@TOFUTI:/$ 

I then entered the commands as shown in the how to:

sudo chown vegan:vegan /home/vegan/.dmrc
chmod 644 /home/vegan/.dmrc
sudo chown vegan:vegan /home/vegan     
chmod 755 /home/vegan

No errors at all, all fine. Then typed:

sudo shutdown -r now
(or sudo reboot) 

Same error still appears...any ideas why?

---

### Post by srpayo on 2009-03-11
Hi chrissharp123,

I followed the steps from that post and Tada! It worked! Great! Thanks a lot guys for the assistance! I am learning step by step that I shouldn´t mess around in ubuntu, specially if everything is working fine! Hehehe.

Really thanks a lot, much appreciated!

---

### Post by yeats on 2009-03-11
> **srpayo said:**
> Hi chrissharp123,

I followed the steps from that post and Tada! It worked! Great! Thanks a lot guys for the assistance! I am learning step by step that I shouldn´t mess around in ubuntu, specially if everything is working fine! Hehehe.

Really thanks a lot, much appreciated!

Yeah, a lot of people who are new at this think they want/need to be root all the time, but it's really not worth the trouble. Ubuntu is built on the sudo model, and once you're used to it, you can do anything you really need to do.  There are other Linux distros around that allow root login, but you really don't need it as a regular user.

Glad I could help :-).

---

