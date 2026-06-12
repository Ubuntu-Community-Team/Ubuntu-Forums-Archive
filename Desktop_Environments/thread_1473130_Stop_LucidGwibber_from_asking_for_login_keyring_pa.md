---
title: "Stop Lucid/Gwibber from asking for login keyring password"
date: 2010-05-04
forum: Desktop Environments
---

### Post by Cammy on 2010-05-04
Ok, I have Lucid working nicely now, and I've started using Gwibber, which seems to try to connect at login.  The only problem is that I'm immediately asked for the login keyring password (which happens to be the same exact password I just entered to log into the machine).  This happens every time I boot the machine.

Is there any way to make it stop asking me for this login keyring password?  I just don't get why I have to enter the same password twice.

The message is: 

```
The login keyring did not get unlocked when you logged into your computer.
```

---

### Post by pritamps on 2010-05-05
I had the same problem and this blogpost helped me:

[http://davestechsupport.com/blog/](http://davestechsupport.com/blog/)

---

### Post by germanix on 2010-05-05
> **pritamps said:**
> I had the same problem and this blogpost helped me:

[http://davestechsupport.com/blog/](http://davestechsupport.com/blog/)

This is no help at all. You link to a blog but not to a specific post within this block that deals with this problem. Do you now expect that whoever follows this link must now read all of the entries in this blog in order to find the solution to the problem in question? Are you really trying to help or are you just directing people to this blog for own interest? If you do want to help then link to the blog entry that discusses the problem at hand. Thank you.

---

### Post by Rasa1111 on 2010-05-05
whenever I sign into Empathy I have to do the same thing... 
to get rid of it *would* be a cool.

---

### Post by Cammy on 2010-05-05
It worked for me!  I used the search function on that blog to find this:

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by cristofaro on 2010-05-12
> **Cammy said:**
> It worked for me!  I used the search function on that blog to find this:

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

Thank you this is really helpful!

---

### Post by Cardale on 2010-06-09
> **germanix said:**
> This is no help at all. You link to a blog but not to a specific post within this block that deals with this problem. Do you now expect that whoever follows this link must now read all of the entries in this blog in order to find the solution to the problem in question? Are you really trying to help or are you just directing people to this blog for own interest? If you do want to help then link to the blog entry that discusses the problem at hand. Thank you.

Whats wrong with you dude?

Thanks for the link.  I was gonna use it, but I decided to just uninstall gwibber all together.  If I want my social media updates I can just visit the website haha...

---

### Post by dark.power on 2010-08-02
There's actually an easier way to do it. The post's method is a bit messy. An alternative(which doesn't involve deleting your passwords is to go to applications menu-->accessories-->passwords and encryption keys. In the window that comes up, go to the collapsible thing that says "passwords", right click, and click change password. It has the same effect as the post, only this way you keep your saved passwords. :D

---

### Post by JustinR on 2010-08-03
> **dark.power said:**
> There's actually an easier way to do it. The post's method is a bit messy. An alternative(which doesn't involve deleting your passwords is to go to applications menu-->accessories-->passwords and encryption keys. In the window that comes up, go to the collapsible thing that says "passwords", right click, and click change password. It has the same effect as the post, only this way you keep your saved passwords. :D

+1 thats the norm for removing the password to your Gnome Key ring.

---

### Post by Replicounts on 2010-08-15
It's amazing how fast Lucid Lynx (Ubuntu 10.04) can wake up from Suspend, if you get the settings right. Takes about 1 second on my Netbook (Eee), about the same as a Macintosh waking from Sleep. This is handy many times. But it could be better.

To get the fast response you need to get rid of the password box (the one this thread is complaining about). But to kill it for Suspend, I had to turn off screen lock entirely, in a **lockdown** menu. Here are the steps to do so:

(1) Alt-F2 to get to the "Run Application" box.

(2) Enter **gconf-editor** followed by the Enter key (or the Run button).

(3) Open **desktop** (not **apps**).

(4) Open **gnome**.

(5) Click **lockdown**.

(6) Then check the box **disable_lock_screen**.

You can reverse this any time by unchecking the same box.

The drawback is that you lose the security of locking the screen. You can still get similar security by logging out -- anyone who steals your computer would need your password to log in. Though neither security is all that good, unless you also have your files encrypted.

So now I set my netbook to Suspend when the lid is closed (System -> Preferences -> Power Management (both for AC Power, and for Battery Power). Then to turn on the computer and return to your work immediately, just open the lid and tap the space bar.

Then when you end your session, you have three main choices:

1. Just close the lid, and later you can get back to where you were within 2 seconds;

2. Logout to maximize security; or

3. Hibernate to use no battery power.

What I want is to **only** turn off the screen lock (and the password request) on Suspend, but not on Hibernate or Restart (which take long enough anyway that the extra time to type the password doesn't matter much). I've tried a number of settings without success. Does anyone know how to do this?

--
John S. James
RepliCounts.org

---

### Post by AstarothSquirrel on 2010-12-27
I appreciate that this may not be the right way to go about it but I have managed to get this to work for me.

I currently have Ubuntu running on an old computer which I use as a file-server, ftp -server, http intranet server and fuppes media server.  I was set to auto login and run fuppes on startup so that all I had to do was switch on and everything worked.  I would use VNC to control the server and did not need a keyboard or screen attached to the server.  

I recently upgraded to 10.04 Lucid and found I had the annoying problem that it would not connect to the network without putting in my password again to unlock the key-ring which meant that I could not use VNC to control the server.  I tried different methods including setting the keyring password to nul (blank) and playing with "sudo apt-get install libpam-keyring" but without any success.  So in desperation, I stopped the keyring apps from starting in the first place.

System|Preferences|Startup Applications:

unticked the following:
Bluetooth Manager - Don't need it, not running anything bluetooth.
Certificate and Key Storage.
Secret Storage Service..
Ubuntu One - Don't need it
Visual Assistance - Don't need it.

Now, it runs and connects without issue or password request.  Just tested ftp and that works fine too.  Http working fine.  Shared directories are fine.  Now I just need to get my fuppes to run on startup and I'll be happy.

If you need to use "Certificate and Key Storage" and "Secret Storage Service" then this probably won't help you but I think it would indicate that there is a problem either with these services or the way they communicate with other services.  I confess to being a complete Ubuntu noob but I hope this points people in the right direction.

---

