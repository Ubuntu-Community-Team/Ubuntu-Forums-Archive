---
title: "Ubuntu out of commision...."
date: 2006-01-11
forum: Gaming &amp; Leisure
---

### Post by trawler on 2006-01-11
I'm not sure if my problem belongs under this forum... but my ubuntu is officially out of commision due to Nvidia drivers installation... :( 
I could use ANY help you have to offer, if you could take a peek at this  [ post]("http://ubuntuforums.org/showthread.php?t=115875").

---

### Post by yaye on 2006-01-11
[QUOTE=trawler]I'm not sure if my problem belongs under this forum... but my ubuntu is officially out of commision due to Nvidia drivers installation... :( 
I could use ANY help you have to offer, if you could take a peek at this  [ post]("http://ubuntuforums.org/showthread.php?t=115875").[/QUOTE]

Hello,

See my second post ( post #14) on this page:

[http://ubuntuforums.org/showthread.php?t=54930&page=2](http://ubuntuforums.org/showthread.php?t=54930&page=2)

Ian

---

### Post by trawler on 2006-01-11
Thanx :)
I could give it a try.

But how do i get around the lockups long enough to edit the file?
So far I could barely get around the login stage....

---

### Post by trawler on 2006-01-11
[QUOTE=trawler]But how do i get around the lockups long enough to edit the file?
So far I could barely get around the login stage....[/QUOTE]

Never mind, i figured it out.
And since i'm writing this post on my ubuntu, I'm hoping your solution did help :D (crosses fingers)

Thanx for the help :)

---

### Post by yaye on 2006-01-11
[QUOTE=trawler]Thanx :)
I could give it a try.

But how do i get around the lockups long enough to edit the file?
So far I could barely get around the login stage....[/QUOTE]

I usually use the nano text editor to edit the xorg.conf file.  If you press Ctrl-Alt-F2 combo, you should be at a text mode login screen.  Type your user name and password to login.  I think you should then be able to use sudo apt-get install nano (I don't know the apt commands well, I usually use Synaptic ).

After you install nano, you can run nano with root privileges by typing sudo nano .
You can use the arrow keys to navigate around in nano and there is a list of the key combos to write the edited file and exit nano at the bottom of the nano screen.  Write down the location of the xorg.conf file so you can tell nano what file you want to edit.  Good Luck.

Ian

---

### Post by yaye on 2006-01-11
[QUOTE=trawler]Never mind, i figured it out.
And since i'm writing this post on my ubuntu, I'm hoping your solution did help :D (crosses fingers)

Thanx for the help :)[/QUOTE]

You type faster than me.  You're welcome.

Ian

---

### Post by leech on 2006-01-11
nano should be installed by default.  I know because I ALWAYS use nano, simply because it actually makes sense, unlike vi.  (Ooh, that's going to start a flamewar... :D  But then I used to prefer emacs over vi...  )

Some people just love their text editors too much.

Best of luck.  I have only had some problems recently with my nVidia drivers, but they're all due to using xcompmgr (which supposedly is more stable with the newest nvidia drivers that are installed in Dapper.)  

Leech

---

### Post by yaye on 2006-01-11
[QUOTE=leech]**nano should be installed by default.**  I know because I ALWAYS use nano, simply because it actually makes sense, unlike vi.  (Ooh, that's going to start a flamewar... :D  But then I used to prefer emacs over vi...  )

Some people just love their text editors too much...................... 

Leech[/QUOTE]

Thanks for the info.  I'm not at my home system right now, so I wasn't sure.  Even if I were at my home system, it's been so long since I installed Ubuntu, I wouldn't remember if it came installed or whether I added it after the initial install.  For the small simple editing I do, nano is the easiest text mode editor to use.

Ian

---

