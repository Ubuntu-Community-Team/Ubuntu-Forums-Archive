---
title: "Turn Beryl on at Startup"
date: 2007-07-13
forum: Desktop Effects &amp; Customization
---

### Post by boozker on 2007-07-13
I was wondering how I can configure Beryl to start up when I log in and start up my computer. Im using Ubuntu 7.04. I know you can go to sessions, but when I go to the .beryl directory there is only two files in there:

libberylsettings.ini and settings

Which one do I choose? Neither look like the one I would use. Where do I look? Also an even bigger question for me is what do I put in the command section? Wouldn't I simply put in "run"? 

I would like to know how I could do this all in terminal if that is possible also. I'm trying to learn the ropes of Linux.  I try to not go through any menus when I can do it in terminal.

---

### Post by Saxomophone on 2007-07-13
Got to System>Preferences>Sessions

Click the *Startup Programs* Tab

Click *Add*

type "/usr/bin/startberyl.sh" (No Quotes)

Click OK

Just did that this morning. Enjoy!

---

### Post by Motoxrdude on 2007-07-13
Or you can go
System>>Preference>>Sessions>>New>>Name=Bery>>Command=beryl-manager.
Enjoy.

---

### Post by diafanos on 2007-07-13
In case there is no startberyl.sh file (like in my case), type "beryl-manager"

EDIT: I didn't see the previous post...

---

### Post by avik on 2007-07-13
That's assume you've made a startberyl.sh script.

Do you use beryl-manager to start beryl?  Then you'd use /usr/bin/beryl-manager.  Basically, you want the absolute path to whatever program you use to start beryl.

EDIT: Too slow, I guess...

---

### Post by shavenlunatic on 2007-07-13
i've never had to do that.. all i've ever done is add beryl-manager to startup

---

