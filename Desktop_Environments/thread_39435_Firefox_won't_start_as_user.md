---
title: "Firefox won't start as user"
date: 2005-06-04
forum: Desktop Environments
---

### Post by akrapovic on 2005-06-04
Hi, Linux newbie here, been messing around for couple days and I like it :)

now, to the Firefox issue

1.  I installed the first Firefox using the file download from mozilla website.  I cannot start Firefox from either the start menu or by clicking on the script, have to type in "sudo /opt/firefox/firefox" in order for it to run.  Typing in "/opt/firefox/firefox" just give me nothing.  And I mean nothing, no feedback in the shell, no error, nothing!

2.  Since I thought that my previous installation is bad in some way, so I decided to download another firefox using "sudo apt-get install mozilla-firefox".  This one install nicely and even create an icon in my start bar for me, but Firefox won't start!  When I click on it, it just bouncing around and quit!  Typing "firefox" into the shell give nothing, no error, no feedback, nothing!  I however found away to start this baby by type in "kdesu firefox".

Here are the few things I tried:
```
akrapovic@ubuntu:/$ sudo firefox
You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:10067): Gtk-WARNING **: cannot open display:
akrapovic@ubuntu:/$ sudo -H firefox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:10079): Gtk-WARNING **: cannot open display:
akrapovic@ubuntu:/$ firefox
akrapovic@ubuntu:/$ /opt/firefox/firefox
akrapovic@ubuntu:/$ sudo /opt/firefox/firefox  (this one work)
akrapovic@ubuntu:/$ kdesu firefox  (this one work)

``` 


I like Firefox to run as user, so that I just either type in firefox and it pop up or by run it from the start menu, not by typing crazy in the shell konsole  ](*,) 

btw, I installed Opera, gedit, gimp, and xmms, everyone of those applications working properly for me, except for this Firefox thing which I already spend the last 2 days reading and messing around to no avail.

please help, thanks :)

---

### Post by jonrkc on 2005-06-05
One thing you might look for is a lock file (a file simply named "lock") in your ~/.mozilla/firefox directory.  If it's there, you can delete it with no harm, and it's possible that will allow you to run Firefox as your normal user.  

Firefox and Thunderbird both have unpleasant tendencies to be stubborn about running under various conditions.  The concept of "profiles" is often involved.  While profiles make sense if more than one person uses a computer, there are millions of people who are the sole users of their computers, and it would be nice if there were an option to do away with alternate profiles.  

But anyway...  I'd look for the "lock" file and see if that works.  It has for me several times.

P. S. Mozilla warns against installing Firefox "on top of" an existing Firefox installation.  They go so far as to say, "you WILL have problems."  When I update Firefox (all too frequently...), I make sure to rename my ~/firefox directory (your location will vary depending on where you said to install it) to something else before installing the new, sometimes somewhat improved version.

---

### Post by abandoned_hussam on 2005-06-05
I had the same exact problem when I installed firefox from mozilla.org
I had to delete ~/.mozilla
It recreated it the next time I reopened firefox.
I think it is a file permissions error.

---

### Post by jonrkc on 2005-06-05
[QUOTE=ht990332]I had the same exact problem when I installed firefox from mozilla.org
I had to delete ~/.mozilla
It recreated it the next time I reopened firefox.
I think it is a file permissions error.[/QUOTE]
 Yes, I feel sure it's a permissions error --the lock file business is a kind of permissions error, in that the user can't start the program again till the lock is cleared.  (And it's not only Firefox by any means that's afflicted by this problem; I've had probably four or five, maybe more, that mysteriously wouldn't run, and deleting the lock file--after I managed to find it--solved the problem every time.  Sometimes an abnormal shutdown, even slightly abnormal and not noticeable as such, causes this, by not allowing the lock to be cleared.)

It very possibly was not necessary to delete the ~/.mozilla directory, but rather just to poke around in it and find a lock file and delete that.  I think if I deleted my ~/.mozilla directory I'd be more inclined to want to shoot myself than to have to recreate it (cookies, etc.) afterward.  I have dozens and dozens of sites that I would have a hard time accessing without cookies....  Which is one reason I wish Firefox had its own "~/.firefox" directory, just as Thunderbird has its ~/.thunderbird directory.

---

### Post by akrapovic on 2005-06-05
thanks everyone for you help :)

fyi, the two installation of Firefox are in separate folder, one is is /opt/firefox and the other done by apt-get is in /usr/lib/mozilla-firefox, so I'm hoping that no conflict resulted from this.

I've searched both installation folders for the "lock" file, but I don't see it.  And yes, I'm sure this is a permission error of some sort, cause I was able to start both of them with sudo or kdesu.

> I had to delete ~/.mozilla
It recreated it the next time I reopened firefox.
Could you please tell me more about this ? which folder am I suppose to delete and it will recreate when I open again ? 
thanks

---

### Post by jonrkc on 2005-06-05
[QUOTE=akrapovic]thanks everyone for you help :)

fyi, the two installation of Firefox are in separate folder, one is is /opt/firefox and the other done by apt-get is in /usr/lib/mozilla-firefox, so I'm hoping that no conflict resulted from this.

I've searched both installation folders for the "lock" file, but I don't see it.  And yes, I'm sure this is a permission error of some sort, cause I was able to start both of them with sudo or kdesu.


Could you please tell me more about this ? which folder am I suppose to delete and it will recreate when I open again ? 
thanks[/QUOTE]
 The lock file won't be in an installation folder; it's in the ~/.mozilla folder.  In my setup, it's under 

```

~/.mozilla/firefox/default.skn

```

It's an empty file that serves as a flag to the firefox.bin program when it starts up; if it finds it there, it will ask the user to enter another profile, because it thinks the program's already in use by the default user.  

I personally would not delete the ~/.mozilla folder.  It contains much valuable stuff.  You could rename it temporarily as an experiment--but firefox won't open up right.  All its cookies and various other settings are in there.

---

### Post by akrapovic on 2005-06-05
[QUOTE=jonrkc]The lock file won't be in an installation folder; it's in the ~/.mozilla folder.  In my setup, it's under 

```

~/.mozilla/firefox/default.skn

```

It's an empty file that serves as a flag to the firefox.bin program when it starts up; if it finds it there, it will ask the user to enter another profile, because it thinks the program's already in use by the default user.  

I personally would not delete the ~/.mozilla folder.  It contains much valuable stuff.  You could rename it temporarily as an experiment--but firefox won't open up right.  All its cookies and various other settings are in there.[/QUOTE]
 sorry for asking a stupid question, but what is exact is **~/.mozilla** directory ? My first Firefox installation path is /opt/firefox, the second is /usr/lib/mozilla-firefox, so where exactly do I find this ~/.mozilla directory ?

I'm a newbie with all this Linux language regarding directory and stuff :)

thanks

---

### Post by philipacamaniac on 2005-06-05
[QUOTE=akrapovic]sorry for asking a stupid question, but what is exact is **~/.mozilla** directory ? My first Firefox installation path is /opt/firefox, the second is /usr/lib/mozilla-firefox, so where exactly do I find this ~/.mozilla directory ?

I'm a newbie with all this Linux language regarding directory and stuff :)

thanks[/QUOTE]
 ~/.mozilla = /home/username/.mozilla

Hidden directory within your home folder, stores all Firefox user settings, bookmarks, cache, etc.

EDIT: Having Firefox in a non-standard (to Debian, anyway) directory, /opt, may screw things up. I would remove the downloaded Firefox, remove the ubuntu package, and reinstall the ubuntu package. If you want the latest Firefox, use the Backports project.

---

### Post by akrapovic on 2005-06-05
yeah, I'll probably try to uninstall everything and start over to see what's going on, because I'm out of idea.

To tell you the truth, I don't exactly know where the "proper" installation path is, I read an instruction online and it tell me to install into /opt . The reason is I don't want to install a copy of Firefox into /home for each user, that's a lot of work! :D

btw, what is the Linux equivalent of "Program Files" in Windows?

-----------------------

Edit: good news, I got Firefox to work, both of them!
I read the instruction you guys give me about renaming the .mozilla folder again, I search around found that I must use ls -a for the hidden folders to show (didn't know that!).  After that I rename the folder, and both Firefox start up perfectly.  Another .mozilla folder created :)

thanks everyone for you help  \\:D/

---

### Post by berserker on 2005-07-14
I just installed 1.0.5 and in order to launch Firefox with my old settings I had to restore ~/.mozilla/firefox from backup.  I don't know what it was but it wasn't a permissions issue (I tried chown user.user -R .mozilla but that didn't work).

---

### Post by shooterae5 on 2005-08-05
after installing firefox 1.0.6 this app will not quit cleanly. the next time I try to start it spins and stops with no errors.

If I open a terminal and enter "ps -e | grep fire" 3 processes will be returned. sosmething like this:

 8682 ?        00:01:31 firefox-bin
 8693 ?        00:01:31 firefox
 8696 ?        00:01:31 firefox-bin

kill off the top one and firefox will finish launching. 

kill 8682

now I'm back surfing again.


I have no idea if this is a problem with firefox or one of the extenions I have installed.
If someone can help me with how to gather information that might help the firefox team please comment to this post.

---

