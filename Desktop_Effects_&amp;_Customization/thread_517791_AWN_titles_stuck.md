---
title: "AWN titles stuck"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by Vanish00 on 2007-08-05
I installed AWN through the synaptic package manager and I enable the docked.  Now whenever an application opens up it's icon is on the dock and once I put my mouse over it, the title of the application appears above it.  Now everytime my mouse goes for any icon the title will always appear but never disappear.  I tried to access the preference for AWN but nothing happens.  What can I do to have those titles to disappear? and if possible how can I access the preferences too?

---

### Post by hyperair on 2007-08-05
Which package did you install? avant-window-navigator or avant-window-navigator-svn? And which repository does it come from? Trevino's eyecandy repository?

---

### Post by Vanish00 on 2007-08-05
The packaged I installed is avant-window-navigator (version: 0.1.2+svn20070731~3v1ubuntu0) , which also called for me to install libawn0.  The repository I think i got it from is Trevino's eyecandy.  I am also using Compiz-fusion too.

---

### Post by hyperair on 2007-08-05
Weird. I don't have that problem. Anyway you could try upgrading some more. Use this repository:
```

deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator

```

You can add that to your third party repositories in System->Administration->Software Sources, or add that to your /etc/apt/sources.list manually. Then install the avant-window-navigator-bzr package.

---

### Post by Vanish00 on 2007-08-05
I followed what you said but I found out that I'm getting my packages from the same repository.  I uninstall avant-window-navigator package and installed avant-window-navigator-bzr package.  I have the still titles just appearing when i put my mouse over it.  Also I still can't access the preferences.

---

### Post by Vanish00 on 2007-08-05
Here's a picture of my here's my 1st part of my problem.  
[ATTACH]Titles stuck[/ATTACH]

My other problem is I can't launch preferences.
When I try to launch avant preferences from the terminal I get a runtime Error.
[PHP]chris@chris-desktop:~$ sudo avant-preferences
/usr/local/share/avant-window-navigator/window.glade

(avant-preferences:23652): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 331, in <module>
    app = main()
  File "/usr/local/bin/avant-preferences", line 136, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=I18N_DOMAIN) 
RuntimeError: could not create GladeXML object
[/PHP]

---

### Post by walkerk on 2007-08-05
> **Vanish00 said:**
> Here's a picture of my here's my 1st part of my problem.  
[ATTACH]Titles stuck[/ATTACH]

My other problem is I can't launch preferences.
When I try to launch avant preferences from the terminal I get a runtime Error.
[PHP]chris@chris-desktop:~$ sudo avant-preferences
/usr/local/share/avant-window-navigator/window.glade

(avant-preferences:23652): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 331, in <module>
    app = main()
  File "/usr/local/bin/avant-preferences", line 136, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=I18N_DOMAIN) 
RuntimeError: could not create GladeXML object
[/PHP]

What kind of video card do you have? I read a post today about this exact problem. Either way check out reacocard's [thread]("http://ubuntuforums.org/showthread.php?t=385981"). make sure you do this [FIRST. post #494]("http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard+avant&page=50")

---

### Post by andrewsomething on 2007-08-05
Unfortunatly the stuck titles issue is a known bug that effects certain video cards. You should follow the link bellow and let the developers know what video card and version of AWN you are using so that it will hopefully be fixed soon:

[https://bugs.launchpad.net/awn/+bug/128818](https://bugs.launchpad.net/awn/+bug/128818)

---

### Post by Vanish00 on 2007-08-05
My video card is a GeForce 8800 GTS.

I installed avant-window-navigator-bzr now.  Problems remain titles stuck & no avant preferences.

---

### Post by aidanr on 2007-08-05
same here, 8800 gts also, trevinos repo
i'll try the other repo when i get home

---

### Post by Vanish00 on 2007-08-05
Here's the official AWN forum discussing this bug, but no fix yet.
[http://http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=301&page=1&sl=1182705353&isLive=true#last]("http://http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=301&page=1&sl=1182705353&isLive=true#last")

The cheap fix is "use the preferences to set the tet and background of the text to totally transparent (for now)."by post #2269

---

