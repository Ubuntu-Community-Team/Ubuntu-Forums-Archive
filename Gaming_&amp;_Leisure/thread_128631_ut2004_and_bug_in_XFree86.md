---
title: "ut2004 and bug in XFree86"
date: 2006-02-11
forum: Gaming &amp; Leisure
---

### Post by Horndog on 2006-02-11
I did a google seach and found that there is a bug with XFree86.

[Here]("http://groups.google.com/group/linux.debian.maint.x/browse_thread/thread/2daa712e4b41fd7c/56c68b1ac807e562?lnk=st&q=Major+opcode+of+failed+request%3A++135+(XFree86-VidModeExtension)&rnum=9&hl=en#56c68b1ac807e562") is one of many  links. I wonder if and when this will be fixed?
I can't start the game through a desktop link because with "gksudo" it errors out, *below*
But I can start the game in the terminal using "sudo". Anybody know of a fix?

Thanks



```


horndog@HornDogsHouse:/usr/local/games/ut2004$ gksudo ut2004
Exporting AS-BP2-SubRosa.....Successful!
Exporting AS-BP2-Outback.....Successful!
Exporting ONS-Adara.....Successful!
Exporting ONS-IslandHop.....Successful!
Exporting ONS-Tricky.....Successful!
Exporting ONS-Urban.....Successful!
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x75
  Serial number of failed request:  151
  Current serial number in output stream:  152
horndog@HornDogsHouse:/usr/local/games/ut2004$



```

---

### Post by handy on 2006-02-12
I just make a call from the menu:

**/home/handy/ut2004/ut2004**

You weren't offered a menu option when you installed ut2k4?

---

### Post by Horndog on 2006-02-12
[QUOTE=handy]I just make a call from the menu:

**/home/handy/ut2004/ut2004**[/Quote]

First thanks for your reply.

yes, there was a menu option and it did not work until I added "gksudo".
then it worked. I can't remember when it stopped but not to long ago with many
games played.

I also have ut2003 and I added a menu link, that does still work.

my path is: /usr/local/games/ut2004 with a System folder at /root/.ut2004/System

---

### Post by handy on 2006-02-12
Did you install something new, that caused the change?

Something has obviously changed.

Any other system symptoms?

Could ut2k4 have become corrupt somewhere?

These are the questions I would be asking myself in your situation... looking for clues.

---

### Post by Horndog on 2006-02-12
[QUOTE=handy]Did you install something new, that caused the change?

Something has obviously changed.

Any other system symptoms?

Could ut2k4 have become corrupt somewhere?

These are the questions I would be asking myself in your situation... looking for clues.[/QUOTE]

I still play the game only from the command line. According to the google search it seams to be a bug. You bring up valid questions that I don't have any answers for.

Why don't you start your game with "gksudo" and see if it works for you.


Thanks

---

### Post by handy on 2006-02-12
Yes, it runs when started with **gksudo**.?

---

### Post by Harleen on 2006-02-12
Why do you want to run that game as root? It should run perfectly as normal user, which would solve your problem with gksudo/sudo.

When running with sudo, you run the program with root priviledges, but with your user's environment variables. So you are _not_ using the configuration from /root/.ut2004 but from /home/<user>/.ut2004. Because some files get the ownership of root after running with sudo, you cannot play as normal user after running once with sudo.
Changing the ownership of that directory to your normal user should enable you to play as normal user.

Try this:
sudo chown <user> ~/.ut2004 -R
ut2004

---

### Post by Horndog on 2006-02-12
>  	
Why do you want to run that game as root?


That was not my intention. That was the only way It would run. After I installed the game with the installer provided It would error out until I used "sudo" and as a link "gksudo"

> 
It should run perfectly as normal user, which would solve your problem with gksudo/sudo.


Yes thanks for the tip it will start fine now with out gksudo/sudo.

> 

Because some files get the ownership of root after running with sudo



That is what happened and now, thanks to you, I am educated on this fact.

This is a fine work around and my thanks goes out to you and Handy for helping.  But there is still a Bug in XFree or one of its libs as documented on my google search.

---

