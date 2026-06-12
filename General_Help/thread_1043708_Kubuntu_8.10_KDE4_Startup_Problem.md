---
title: "Kubuntu 8.10 KDE4 Startup Problem"
date: 2009-01-18
forum: General Help
---

### Post by marcodarco1 on 2009-01-18
After logging in to Kununtu for the first time, the splash screen gets in the middle of showing the fourth icon, then stops. The computer just sits there with the splash screen frozen like that. I have tried reinstalling it, but I still have the same problem.

The fourth icon (desktop ) only halfway appears and nothing happens afterwards. 

[IMG]http://www.blog.arun-prabha.com/wp-content/uploads/2008/01/kde4.JPG[/IMG]

I have tried these codes in the console to see if it would help, but it didn't fix the problem: 

```

sudo killall kdm
sudo mv ~/.kde ~/.kdebackup
sudo kdm
```

---

### Post by marcodarco1 on 2009-01-18
*bump*
I have updated info in the first post since creating the thread.

---

### Post by yeats on 2009-01-18
Anything useful in the /var/log/kdm file(s)?  Just a thought . . .

---

### Post by marcodarco1 on 2009-01-18
> **chrissharp123 said:**
> Anything useful in the /var/log/kdm file(s)?  Just a thought . . .

I haven't used Kubuntu in a while. So, unfortunately, I have no idea what you are talking about nor how to get to those files.

---

### Post by yeats on 2009-01-18
oh, I see.  When kdm fails, type Ctrl-Alt-F1, which will drop you to a regular login terminal, then log in from there.  Then you can do:

```
less /var/log/kdm
```

which will let you browse through the text of the kdm log.  It *should* have some useful information about what's not working.

If that doesn't work you can try: 

```
cd /var/log
grep kdm *
```

to search all the main logs for references to kdm.

You can type Alt-F7 to return to your X screen.

Hope that helps.

---

### Post by marcodarco1 on 2009-01-18
Someone from another forum has provided me with a fix for the problem. It was an Intel graphics driver bug.

This was the code that was typed into the console. I hit enter and restarted the computer.

```
kwriteconfig --file kwinrc --group Compositing --key Enabled false
```

My problem has been fixed. Thanks for your help anyways.

---

### Post by yeats on 2009-01-18
Excellent.  Happy to help anyway.

---

### Post by scythe944 on 2009-01-28
> **marcodarco1 said:**
> Someone from another forum has provided me with a fix for the problem. It was an Intel graphics driver bug.

This was the code that was typed into the console. I hit enter and restarted the computer.

```
kwriteconfig --file kwinrc --group Compositing --key Enabled false
```

My problem has been fixed. Thanks for your help anyways.

Woohoo! That fixed my problem too!
Thanks a bunch! :D

Oh, my hardware is different though, I have a Dell Dimension 2400 with an additional 512MB of RAM installed, as well as a second hard drive.  Just for anyone else that has this problem...

---

