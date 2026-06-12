---
title: "Problem with Places Menu"
date: 2008-05-19
forum: Desktop Environments
---

### Post by jag67 on 2008-05-19
Hello,

I'm using Ubuntu 7.10. I upgraded to Firefox 3 today  and in order to use mplayer. I had to enter a few commands:

sudo cp /usr/lib/firefox/plugins/* /usr/lib/firefox-addons/plugins
ln -s /usr/lib/firefox/plugins/* .
sudo cp -r /usr/lib/firefox/plugins /usr/lib/firefox-addons/

but I probably did something wrong and since then I can't use the Places Menu properly. 

If I choose Home folders, desktop or documents from the places menu , the file manager just shows briefly and disappears. Music, images & videos shortcuts are the only ones that work. I tried to add another user and log on with it but got the same problem. When I restart I sometimes see the file manager trying to pull up documents a few times but it finally disappears.

Any idea what I should do to fix this? I'm new to Linux, so I'm still learning!

Thanks a lot in advance!

---

### Post by gnivler on 2008-05-19
> **jag67 said:**
> Hello,

I'm using Ubuntu 7.10. I upgraded to Firefox 3 today  and in order to use mplayer. I had to enter a few commands:

sudo cp /usr/lib/firefox/plugins/* /usr/lib/firefox-addons/plugins
ln -s /usr/lib/firefox/plugins/* .
sudo cp -r /usr/lib/firefox/plugins /usr/lib/firefox-addons/


The 2nd command there (ln -s) says link everything in /usr/lib/firefox/plugins into my current directory, so the question becomes, what directory where you in when you ran it?  It doesn't honestly look like something which would screw up the Places menu offhand.

> **jag67 said:**
> but I probably did something wrong and since then I can't use the Places Menu properly. 

If I choose Home folders, desktop or documents from the places menu , the file manager just shows briefly and disappears. Music, images & videos shortcuts are the only ones that work. I tried to add another user and log on with it but got the same problem. When I restart I sometimes see the file manager trying to pull up documents a few times but it finally disappears.

Any idea what I should do to fix this? I'm new to Linux, so I'm still learning!

Thanks a lot in advance!

You might want to give some thought to other things you may have changed or installed on the system which could be causal.  Also, you can refer to your system logs to see if entries are being generated when you try to click these problem Places.  Also under Places when you launch your drives/computer, does that come up?  The ones you quoted are all residing in your home directory, which is curious at least.

---

### Post by jag67 on 2008-05-20
Thanks for your reply!

> The 2nd command there (ln -s) says link everything in /usr/lib/firefox/plugins into my current directory, so the question becomes, what directory where you in when you ran it? It doesn't honestly look like something which would screw up the Places menu offhand.

I was initially in the Home folder when I ran the command, then I reread the instructions and rerun the command from /usr/lib/firefox-addons/plugins/.

> You might want to give some thought to other things you may have changed or installed on the system which could be causal. Also, you can refer to your system logs to see if entries are being generated when you try to click these problem Places. Also under Places when you launch your drives/computer, does that come up? The ones you quoted are all residing in your home directory, which is curious at least.

No entries in the system log when I try to click these Places. My drives/computer don't come up. One thing I tried was to install the Konqueror file system to check if I could still access them, and they work fine from Konqueror.

---

### Post by gnivler on 2008-05-20
> **jag67 said:**
> Thanks for your reply!



I was initially in the Home folder when I ran the command, then I reread the instructions and rerun the command from /usr/lib/firefox-addons/plugins/.



No entries in the system log when I try to click these Places. My drives/computer don't come up. One thing I tried was to install the Konqueror file system to check if I could still access them, and they work fine from Konqueror.


You are welcome :)  I'm still learning and don't have a canned answer ready for you, but I'm game for some troubleshooting until someone else chimes in.  I just did an hour of reading and research on the subject and came up with bubkiss, it doesn't seem like there exists a userland functionality to alter the Places menu directly.  Seems like the only answers available are changing bookmarks in nautilus (menu) or changing .gtk-bookmarks in your home directory.  Not much at all addresses the menu items which ARE there not working, but I'm still looking into it.

One easy thing you might want to try is going into Synaptic and doing a search in the Name column for gnome- (hyphen) and right clicking each entry which is already installed and marking it for reinstallation.  There are a bunch.  Apply those and log out/in.  You could also try reinstalling the ubuntu-desktop package but that is massively depended upon and I'm not sure the repercussions of doing that.  Yesterday I severely jacked my gnome packages and was able to recover them without an issue so I think that part is pretty safe.  Definitely back up your important data before doing these things in case your system gets screwed up to the point of reinstalling.

You could also try creating a new user account and seeing if the problem exists over there also, it kind of points to a local configuration versus system issue.

---

### Post by jag67 on 2008-05-20
Thanks again, I'm amazed you spent so much time on this!
> You could also try creating a new user account and seeing if the problem exists over there also,
Yes, I already tried that and got the same problem. I also switched the system from French to English, but not much better.

I'll have a look at your other suggestions this weekend and will let you know what I found. I'm using this PC for work and since it's working ok now (besides this Places issue), I'll wait until the weekend to test it more extensively and break it (if necessary) to then recover!

Cheers!

---

### Post by gnivler on 2008-05-20
> **jag67 said:**
> Thanks again, I'm amazed you spent so much time on this!

Yes, I already tried that and got the same problem. I also switched the system from French to English, but not much better.

I'll have a look at your other suggestions this weekend and will let you know what I found. I'm using this PC for work and since it's working ok now (besides this Places issue), I'll wait until the weekend to test it more extensively and break it (if necessary) to then recover!

Cheers!

Ah cool :)  Good luck.  I like spending time learning about how the system works, and it seems that Places is actually coded statically, I looked at the source code finally.  Gnome has some weird things going on!  Don't get me started on setting a default icon for a certain file type lol...

---

### Post by jag67 on 2008-05-25
It worked! I first tried to reinstall (after I marked the gnome- entries), but it didn't change anything. I saw that I could also update a bunch of other entries, so I tried that  and I got all my Places back in place!

Thanks again for your amazing help!!! :)

---

### Post by gnivler on 2008-05-25
Awesome, congrats and thanks for letting me know it helped :)

---

