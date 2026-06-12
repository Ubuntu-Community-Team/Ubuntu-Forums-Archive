---
title: "Kopete problems"
date: 2005-04-11
forum: Desktop Environments
---

### Post by jakroo99 on 2005-04-11
HI guys,

I was recently using gaim as my main aim client...and my girlfriend uses mac and iChat.  I tried to send her a file thorugh gaim and for some reason it would just abort automatically.  So i switched over to kopete but i can never get a response from people...even though i can type stuff in...like their responses nvr come through :?  WTF is going on....file transfers doint work with gaim...and kopete is just plain acting weird.  Any solutions?

---

### Post by Narg on 2005-04-12
The no response is also happening to me. I have no clue whats up either. I've just been using irc via konversation as a IM for the time being as aim is unusable.

---

### Post by dermotti on 2005-04-12
On AIM kopete i can send messages but i never recive them, This is another Kubuntu issue as i do not have the issue on my Mepis Box.

---

### Post by Seth on 2005-04-12
[QUOTE=dermotti]On AIM kopete i can send messages but i never recive them, This is another Kubuntu issue as i do not have the issue on my Mepis Box.[/QUOTE]
 This happens to me on SuSE but not Kubuntu. It's a Kopete bug. I think it has to do with aliased buddy names on the server but I can't produce a reliable testcase. I suggest not using Kopete.

---

### Post by jpowers on 2005-04-26
> On AIM kopete i can send messages but i never recive them, This is another Kubuntu issue as i do not have the issue on my Mepis Box.


I've added this as a bug in the [kopete bugzilla](http://bugs.kde.org/show_bug.cgi?id=104561) 

I've also posted something I've found to resolve the issue for individual contacts, as it doesn't affect all of my contacts

---

### Post by srss on 2005-04-26
[QUOTE=dermotti]On AIM kopete i can send messages but i never recive them, This is another Kubuntu issue as i do not have the issue on my Mepis Box.[/QUOTE]
 Sorry, but I use it normally in hier. I´ve never faced an problem like this. Some times my Kopete insists that I´m typing a worng password (ICQ and MSN). Then it begins a Click OK loop. I have to kill its PID to continue. And when it happends, it starts to eat lots of RAM. Any ideas ? Anyone?

---

### Post by clparker on 2005-04-26
Same thing here, i dont want to use gaim, it's just too...too GNOME like...

---

### Post by nykobing on 2005-05-19
[QUOTE=srss]Sorry, but I use it normally in hier. I´ve never faced an problem like this. Some times my Kopete insists that I´m typing a worng password (ICQ and MSN). Then it begins a Click OK loop. I have to kill its PID to continue. And when it happends, it starts to eat lots of RAM. Any ideas ? Anyone?[/QUOTE]

Kopete is also giving me the wrong password message, even though it is correct. I really can't stand gaim at all, is there any other good instant messanger apps or a fix for this?

---

### Post by mattrkde on 2005-05-19
[QUOTE=srss]Sorry, but I use it normally in hier. I´ve never faced an problem like this. Some times my Kopete insists that I´m typing a worng password (ICQ and MSN). Then it begins a Click OK loop. I have to kill its PID to continue. And when it happends, it starts to eat lots of RAM. Any ideas ? Anyone?[/QUOTE]

The problem in the popups should be fixed in KDE 3.4.1, which also fixes the problem with the eating lots of RAM.

---

### Post by propagandhi on 2005-05-20
From what i understand, Kopete is being blocked by MSN Network now, hence the password prompting thingy, although I read on another forum that you can work-around this by installing the svn/cvs build at [http://kopete.kde.org/index.php?page=cvs](http://kopete.kde.org/index.php?page=cvs). Does anybody know of another workaround. I MUST use kopete, I hate all the other clients.

---

### Post by Michael Ambrus on 2006-08-01
Build from source and install over the currently installed one is what kopete project says should work (providing your current KDE disto is not too old).

From their page at [http://www.kde-apps.org/content/show.php?content=9891](http://www.kde-apps.org/content/show.php?content=9891) :

"Make sure you have at least KDE 3.3 and Qt 3.3 before compiling this
release. Please be sure to install this version over the version
you have installed currently."

The kopete project homepage contains more info ([http://kopete.kde.org/](http://kopete.kde.org/))

Sometimes the fancy-smancy update programs in nowadays Linux distributions are just too... errm... "crappy"?

Read about this guys opinion (hehe): [http://lists.suse.com/archive/suse-linux-e/2004-Nov/2284.html](http://lists.suse.com/archive/suse-linux-e/2004-Nov/2284.html)

In other words, nothing beats the source :)

/Mike

---

