---
title: "window focus grabbing"
date: 2006-01-15
forum: General Help
---

### Post by borisattva on 2006-01-15
something just happened to me that used to be a source of immense haterid towards ms windows.

i was running a synaptics update installing new programs, and an IM popped up which i began running a response to. as i was hitting the space bar a window popped up, and took that space bar hit as destined for it and did something.

it was a confirmation of some sort and i think the 'Forward' button was preselected.

i hated this window focus stealing in windows with a passion because as usually fast paced multitasker it cost me alot of unintentional authorizations in windows that would messed things up.

i used to post in windows forums suggesting that if a window really needs my immediate attention, to let it pop up, but either 

a) for a brief delay not accept any inputs from keyboard or mouse clicks
or
b) shift the focus into nothing, so that key strikes and mouse click will be outside the filed of what i was doing before and out side of the window that needs my attention, resulting in nothing farmful. untill i explicitely chose a window thati want my next command to address.

there it went unanswered, but in linux i feel there has to be some kind of a way to get that accomplished. is there a feature exactly as i'm describing it?

---

### Post by bonzodog on 2006-01-15
try going to:
**System --> Preferences --> Windows**

There is a setting in there to move the focus away.

---

### Post by borisattva on 2006-01-15
that was the first place i checked,
but i'm wondering if something should be enabled as the only options i see are window selection with a mouse hover, title bar actions and movement keys. nothing on window focus shift

---

### Post by Pausanias on 2006-02-03
No, this cannot be changed in any of the preference menus. Not even in the default configuration editor. You have to install a patch to metacity for this to work.

[http://dpk.net/2005/11/29/metacity-and-focus-theft/](http://dpk.net/2005/11/29/metacity-and-focus-theft/)

I am **loving** my new non-focus-crazy ubuntu experience.

---

### Post by borisattva on 2006-02-04
[QUOTE=Pausanias]No, this cannot be changed in any of the preference menus. Not even in the default configuration editor. You have to install a patch to metacity for this to work.

[http://dpk.net/2005/11/29/metacity-and-focus-theft/](http://dpk.net/2005/11/29/metacity-and-focus-theft/)

I am **loving** my new non-focus-crazy ubuntu experience.[/QUOTE]
thank you very much for taking your time to respond with the solution.

---

### Post by Pausanias on 2006-02-05
Actually, it seems that the above package has a problem. When a new window opens, it is not raised. What I wanted was for a new window to be raised to the foreground but not focused. So I modified the source to do so.

So, to review:
[list]
[*] The default Ubuntu metacity raises **and** focuses new windows.
[*] dpk's hack neither raises nor focuses windows.
[*] I have made a patch that raises new windows, but does not focus them.
[/list]

If there is enough interest I can post it.

---

### Post by borisattva on 2006-02-05
[QUOTE=Pausanias]Actually, it seems that the above package has a problem. When a new window opens, it is not raised. What I wanted was for a new window to be raised to the foreground but not focused. So I modified the source to do so.[/QUOTE]

thats what i wanted (and believe the way it should have been to begin with, linux or windows).

unfortunately non of my ubuntu boxes are up and running right now due to the controller card bug, but i'll jot down your patch if you were to be so kind and release it?

thanks again

---

### Post by Pausanias on 2006-02-06
OK, I am attaching the patch to this message. To build it you would download the patch file to a brand new directory. From that same directory you (as yourself, not as root) would type the following commands. The first command gets the necessary tools for getting a .deb; the next command unzips the diff; the third command downloads the metacity source and compiles it;  the fourth command applies my patches; and the rest of the commands produce a .deb file from the source.

```

sudo apt-get install build-essential fakeroot
gunzip pausanias-metacity_breezy_notheft.diff.gz
fakeroot apt-get -b source metacity
patch -p0 < pausanias-metacity_breezy_notheft.diff
cd metacity-2.12.1
dpkg-buildpackage -uc -us -rfakeroot
cd ..

```

This will create a .deb file called metacity_2.12.1-0ubuntu1notheft_i386.deb.

To install it:

```

sudo dpkg -i metacity_2.12.1-0ubuntu1notheft_i386.deb

```

To revert to the old metacity, go to synaptic, select the metacity package, select Force version from the menu, and select the breezy version.

---

### Post by Pausanias on 2006-02-12
I forgot to add that once you install the deb, you should type metacity --replace to replace the currently running version of metacity with the new one.

---

### Post by Madpilot on 2006-02-12
Pausanias, have you submitted this patch in a bug report to anyone? Having it available somewhere in gconf or elsewhere as a metacity option would be very cool.

[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs) - I'd be interested to see what the devs have to say.

---

### Post by Pausanias on 2006-02-14
It's a good idea to add a gconf preference for this. dpk's patch already does that; perhaps I could just steal a bit of his code. If I get around to doing it, I'll post it on launchpad.

---

