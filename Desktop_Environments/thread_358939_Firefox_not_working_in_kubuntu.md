---
title: "Firefox not working in kubuntu"
date: 2007-02-11
forum: Desktop Environments
---

### Post by drunkninja on 2007-02-11
I installed kubuntu, ran 'sudo apt-get install firefox' and everything appeared to be okay.  However, when I try to run firefox, the logo will bounce next to my cursor for a while, and the loading bar will appear at the bottom of my screen, but then both will disappear and nothing will happen!  I can run firefox if I download it from mozilla's website, extract it, and run the firefox executable with 'sudo' but otherwise, I get nothing.  Any thoughts?

---

### Post by aysiu on 2007-02-11
Can you run this command from the terminal and then post the output? ```
firefox
``` By the way, you shouldn't run Firefox with *sudo*.

---

### Post by drunkninja on 2007-02-11
I get nothing when I run 'firefox' from the terminal.  It just goes down another line to another prompt.

---

### Post by aysiu on 2007-02-11
So something like this? ```
drunkninja@ubuntu:~$ firefox
drunkninja@ubuntu:~$
``` Hm. I don't know what the problem is, then.

Can you try installing Firefox with this script and seeing if that makes a difference?
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by drunkninja on 2007-02-11
Yep, just like that....

---

### Post by drunkninja on 2007-02-11
[I]Okay, I tried removing and reinstalling firefox, and got the same thing.  However, when I tried 'sudo firefox', I got this:
[I]
You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:5531): Gtk-WARNING **: cannot open display:[/I]

---

### Post by aysiu on 2007-02-11
First of all, as both I and the terminal have said, you should not run Firefox using *sudo*.

Do not run Firefox using *sudo*.

Okay. Now that we've established that, I Googled your error and found [this thread](http://lists.debian.org/debian-user/2003/08/msg00818.html) that indicates restarting the X server may help.

Please, please, please do not **ever** run the command ```
sudo firefox
```

Okay. To restart the X server, make sure all your programs are closed. Then hit Control-Alt-Backspace. This will restart the X server and take you back to the login screen. Log in again and try launching Firefox.

---

### Post by Simon-au on 2007-11-07
-- xubuntu kubuntu Ubuntu firefox not working not starting up --
yes good advice, I had the same problem with not being able to start firefox in xubuntu 

I must have started firefox with  "sudo firefox" or something like that past.

This caused the .mozilla directory to be owned by root.

sudo chown -R **your_username**:**your_username** .mozilla

form the my home directory fixed it.

Or remove the directory and start firefox as the normal user.

Thanks very much for this thread.

---

### Post by MCMcButtah on 2007-11-08
I had the same problem with firefox after i upgraded to gutsy. I found out the problem was specific to only one user because as a test I created a new user and firefox worked no problem from that account. Based on that i deleted the .mozilla folder in the home directory of the user with the problem and then after that firefox worked again.

---

