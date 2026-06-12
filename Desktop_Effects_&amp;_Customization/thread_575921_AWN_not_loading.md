---
title: "AWN not loading"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by bethaviv on 2007-10-14
I followed the guide and restarted my computer, but whenever I click on the Awn Manager, nothing happens.

I've never used Awn before so I'm not too sure what I'm doing wrong.

I'm using Gutsy with all the updates. Compiz is enabled. I've checked a couple posts, but nothing seemed to be my issue.

When I try running Awn in the terminal I get:

```
bethaviv@bethaviv-desktop:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:182: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 162, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 182, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue

```

Thanks,
Beth

---

### Post by Faud on 2007-10-14
Hi and good morning/afternoon/evening.

What guide did you follow ?

---

### Post by bethaviv on 2007-10-14
The one that is posted here: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Everything went fine until I tried to load the program =\

(Thanks for your quick response =) )

Not sure if this helps, but I tried to gedit that last file

```

Key: /apps/avant-window-navigator/title/text_color isn't set.

```

And there's nothing in the file.

---

### Post by Faud on 2007-10-14
Do you have python installed ?

---

### Post by Faud on 2007-10-14
and just to make sure, you click on system->preferences and then awn and nothing at all happens right ?

---

### Post by bethaviv on 2007-10-14
Yeah, System > Preferences -> Awn Manager

For Python I have:

python2.5
python2.5-dev
python2.5-minimal

There's other ones too... Is there one I should be looking for specifically?

(I'm able to use my Gmail Notifier which is written in Python, so I'm assuming all is good there.)

---

### Post by Faud on 2007-10-14
I am going to do some more research for you. I know that Ive seen this before and that people have found the answer though, and that its something simple. Im just at work right now and cant remember what it is lol.
When I get a minute Im gonna go hit tha awn forums for you and post that first line of your error message and see if I can get a response

---

### Post by bethaviv on 2007-10-14
I'll go looking over there too. I looked through the forums here and found my error, but no one posted a fix... only that they had solved it.

---

### Post by bethaviv on 2007-10-15
Sorry.. just bumping the thread. I did check out the AWN forums for the error I'm getting, but got no hits. Even tried googling, but nothing.

I completely uninstalled and then reinstalled compiz-fusion w/ emerald and then AVN, still nothing.

Ideas?

---

### Post by Faud on 2007-10-15
Check out this page

[http://ubuntuforums.org/showthread.php?t=385981&page=87](http://ubuntuforums.org/showthread.php?t=385981&page=87)

How are you starting AWN ?

Im home from work now =D Finally so I can put some more time in this.  Is it like this guy where you start it and then it immediatly exits ? Or nothing happens at all ?

---

### Post by bethaviv on 2007-10-15
I tried from the command line and from System > Prefernces

But this worked:

```

avant-window-navigator

awn-manager

```

He had "avant-manager" which didn't exist at the command line for me, but awn-manager worked.

Only thing is, it seems I need "avant-window-navigator" always running.. otherwise it kills the launcher at the bottom and kills the manager if it's open.

I'm going to add it to my session and see if that works.

Yep.. adding "avant-window-navigator" to my session is working... I wonder if this is Gutsy's doing or AWN's doing...

---

### Post by Faud on 2007-10-15
If you go to applications,accessories, is avant window manager there ?

---

### Post by bethaviv on 2007-10-15
Avent Window Navigator is there, not the Manager.

---

### Post by Faud on 2007-10-15
If you click on that it should start AWN and then you go to the dock itself and right click and choose preferences...at least that is what I do My AWN manager is located in system->preferences

---

### Post by bethaviv on 2007-10-15
It does... I didn't think to look there... I figured the manager would be like the C-F and Emerald manager and have just one spot to load stuff from... didn't expect AVN to be hiding in my Apps.

Thanks, that link was what I needed =)

Learn something new everyday...

---

### Post by Faud on 2007-10-15
LOL, see knew it was simple. I am so happy that its working for you now. As for me, the wife is cooking dinner and it smells amazing. Enjoy your new AWN

---

### Post by bethaviv on 2007-10-15
Cool thanks =)

Have a good dinner. As for me... it's bed time *yawn*

---

