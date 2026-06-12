---
title: "Can't login anymore"
date: 2006-02-04
forum: Desktop Environments
---

### Post by m33s on 2006-02-04
so i finally decided the other day to completely kill my windows partition and switch to ubuntu for good. booting today i can't login anymore.
everything is normal up to the login-screen. i can enter my user-name, but as soon as i enter even the first letter of my password gdm crashes and restarts (repeat as often as you like ;) )
i do can log in in the console without any problems - i just don't know, where to look for the error.

help is greatly appreciated.

thanx, m33s

---

### Post by ipp3l1 on 2006-02-04
Does the error complain something about xserver-error or .ICEauthority file? Does it say something about your "session didn't last for longer than 10seconds" or something?

---

### Post by Luffield on 2006-02-04
I had the same problem. I never really solved it, but I found a workaround - I turned on automatic login for my user. I know it's not a good solution if you have more than one user on your computer, and I wish I could remember which configuration file exactly it was that I edited, but I'm sure you'll find it in the forums.
Still, I'll watch this thread in hope that a better solution is avialable.

---

### Post by Pudwud on 2006-02-04
I know that this is a silly unrelated problem but how do you post a new topic?

Thanks and good luck with your problem.

---

### Post by Luffield on 2006-02-04
In the forum where you want to post the topic, find "forum tools" at the top, and it's there.
Took me a while to find it too, after the recent change :)

---

### Post by m33s on 2006-02-04
@ipp3l1
no, it doesn't give me an error message whatsoever. it just restarts gdm back to the login-screen and everything is happening all over again...

---

### Post by ipp3l1 on 2006-02-04
[QUOTE=Pudwud]I know that this is a silly unrelated problem but how do you post a new topic?
[/QUOTE]
In the forums, there's this tiny blue button...
[img]http://img517.imageshack.us/img517/9103/ubuntupost6gf.png[/img]

\\:D/

---

### Post by abelethan on 2006-02-09
I just downloaded Automatrix the other night and I am getting the error for the logged in for less then 10secs. After the download was compleated I got booted. When I restarted and tried to log in all I would get is that error. I was able to install the Automatrix though terminal hoping that would help but no good. This is my first attempt at running a linux system and would appraciate any help you could give.

---

### Post by brianben1 on 2006-02-17
I had the same issue and it was driving me nuts. Type in the first character of the gdm password and it crashes and restarts. I knew it had to be a font issue. But I cannot take responsibility for the fix. I found it here...

[http://www.ubuntuforums.org/showthread.php?t=51859&highlight=gdm+password+crash](http://www.ubuntuforums.org/showthread.php?t=51859&highlight=gdm+password+crash)

I too had fonts only readable by root. chmod 755  the windows fonts I copied over and all was well. Hope this helps.

---

### Post by Luffield on 2006-02-17
Cool, thanks for digging it up for us Brian!

---

