---
title: "Login manager crashes"
date: 2006-01-07
forum: General Help
---

### Post by metafile on 2006-01-07
I`ve just installed and configured Ubuntu. Added and removed some software, installed new fonts (by copying them into /usr/share/fonts).
Then I restarted the computer and when I tried to log in, the login manager had crashed. Right after I`d typed first letter of the password in the "password" field.

Gnome`s default login screen came up, but the same thing happened to it, and Ubuntu`s login screen appeared again. I`ve tried to login once again, but the same thing had happened.

So, I restarted with console mode and after logging as myself (not root) launched X. First of all linux said to me that it "Failed to load HAL" and then I`ve noticed that all of the preferences were reset to defaults. But the most unpleasant -- all the data from my home directory dissapeared (luckily, the system was just set).

I`ve noticed the [same problem](http://www.ubuntuforums.org/showthread.php?t=77256) here, but there is still no responce to it. What the hell was wrong with the system?

---

### Post by professor_chaos on 2006-01-07
Unfortunately I don't know the "answer" as to why this happened. And, since your presumably back up and running, this probably does nothing for you. But I would probably first tried to reinstall gdm and all hal libraries. Or I might even be thinking of hardware issues.
The fact that you lost everything in your home directory is BS. I don't really mind a crash, but thats a real CRASH!!! Makes me mad just thinking about it. Hope your experience with Ubuntu in the future is better.

---

### Post by metafile on 2006-01-08
Unfortunately I couldn`t restore my Ubuntu, and now I`m still under W#ndows.
I`ve tried to reinstall HAL and gdm, but this didn`t work for me.
Same situation: I can not login.

Looks like now I`ve no other choice but trying to reinstall Ubuntu again.

---

### Post by nerval on 2006-01-08
One thing Ubuntu or any linux distribution can't do; is to fix Microsoft Windows' problems. 

hal.dll is a system file for windows, becomes a pain even if you wanna install another version of windows on your second harddrive.

To learn more about Hardware Abstraction Layer; here it is a link :
[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

A hand from microsoft support :
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;q237556](http://support.microsoft.com/default.aspx?scid=kb;EN-US;q237556)

If it is still not solved, and you have to talk to a microsoft support guy; tell him linux users hate them :)

Cheers;
Onur

---

### Post by metafile on 2006-01-08
Looks like you`ve missed the word "still" :).
I`ve already had windows on another hard drive before trying Ubuntu.
Anyway, thanks for those links, I`ll read them after Ubuntu reinstallation. :)

---

### Post by brianben1 on 2006-02-17
I had the same issue and it was driving me nuts. Type in the first character of the gdm password and it crashes and restarts. I knew it had to be a font issue. But I cannot take responsibility for the fix. I found it here...

[http://www.ubuntuforums.org/showthread.php?t=51859&highlight=gdm+password+crash](http://www.ubuntuforums.org/showthread.php?t=51859&highlight=gdm+password+crash)

I too had fonts only readable by root. chmod 755 the windows fonts I copied over and all was well. Hope this helps.

---

### Post by metafile on 2006-02-17
Thanks a lot, brianben :).
Although my solution was reinstallation (and then I copied fonts to ~/.fonts, not /usr/share/fonts, like the first time), it`s good to find out the matter of the problem. Now I shouldn`t add "although, once Ubuntu destroyed all my data, just once, but..." to "Ubuntu is great" statement :).

---

