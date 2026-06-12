---
title: "Run program with GUI with cron"
date: 2009-01-19
forum: Desktop Environments
---

### Post by martin_legion on 2009-01-19
Hello. I have a script that checks if a file exists in a folder, and if it finds the file, it calls zenity to display a message to the user.
I'd like to run this script periodically in cron, say, every 5 minutes. I know all the cron part. What I don't know is how can I run the script so that the messages created by zenity are shown to the user in the desktop enviroment.
I hope I made myself clear...

Thanks in advance!

---

### Post by ayoli on 2009-01-19
You need to set the DISPLAY variable before running your command :

```
*/5 * * * * export DISPLAY=:0 && /path/to/your/script
```

---

### Post by martin_legion on 2009-01-19
> **ayoli said:**
> You need to set the DISPLAY variable before running your command :

```
*/5 * * * * export DISPLAY=:0 && /path/to/your/script
```

Great, I'll try that!
By the way... is there a way to export ALL the displays, so that the message is shown in all X sessions?

Thanks for the light-speed reply!

---

### Post by ayoli on 2009-01-19
> **martin_legion said:**
> Great, I'll try that!
By the way... is there a way to export ALL the displays, so that the message is shown in all X sessions?

Thanks for the light-speed reply!

Hm, my guess is that you should have a cron line for each display.

---

### Post by martin_legion on 2009-01-19
> **ayoli said:**
> Hm, my guess is that you should have a cron line for each display.

This is the most efficient forum on earth
Thanks a lot.

---

### Post by ayoli on 2009-01-19
> **martin_legion said:**
> This is the most efficient forum on earth
Thanks a lot.
You're welcome.
If this works for you, please remember to mark the thread as solved.

---

### Post by martin_legion on 2009-01-19
Actually, I still have a little problem:
If I export the display and run the script manually from a TTY, everything goes smoothly. The problem comes when I try to run it from cron, that is, as root:
I log in as root, then type:

export DISPLAY=:0

and then I got this error:

Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified

So I tried adding "sudo -u myuser" to the export command, but it adds a new error to the two previous:
sudo: export: command not found.

This is why it doesn't run from cron...
Any suggestions?

Thanks

---

### Post by ayoli on 2009-01-19
> **martin_legion said:**
> Actually, I still have a little problem:
If I export the display and run the script manually from a TTY, everything goes smoothly. The problem comes when I try to run it from cron, that is, as root:
I log in as root, then type:

export DISPLAY=:0

and then I got this error:

Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified

So I tried adding "sudo -u myuser" to the export command, but it adds a new error to the two previous:
sudo: export: command not found.

This is why it doesn't run from cron...
Any suggestions?

Thanks

Why not running that cron frmo the user crontab ?

---

### Post by martin_legion on 2009-01-20
> **ayoli said:**
> Why not running that cron frmo the user crontab ?

I tried that too.
Logged in as my user I type "crontab -e" and add the line:
* * * * * export DISPLAY=:0 && /path/to/myscript
and nothing happens.

I see in /var/log/syslog that the command is executed every minute as my user, not root, which is correct, but still nothing happens... whyyyyyy?!

---

### Post by ayoli on 2009-01-20
> **martin_legion said:**
> I tried that too.
Logged in as my user I type "crontab -e" and add the line:
* * * * * export DISPLAY=:0 && /path/to/myscript
and nothing happens.

I see in /var/log/syslog that the command is executed every minute as my user, not root, which is correct, but still nothing happens... whyyyyyy?!

maybe your display isn't :0
also make sure your script is executable and maybe use exec inn you cron line :
```
* * * * * export DISPLAY=:0 && exec /path/to/myscript
```

---

### Post by martin_legion on 2009-01-20
> **ayoli said:**
> maybe your display isn't :0
also make sure your script is executable and maybe use exec inn you cron line :
```
* * * * * export DISPLAY=:0 && exec /path/to/myscript
```

The script belongs to my user and group, it has all permitions, and it's located in /usr/local/bin, so it's accesible system-wide (I include the full path in crontab anyway)
I also added exec but nothing changed... what am I doing wrong??
About display 0 or 1:
```
(zenity:18409): Gtk-WARNING **: cannot open display: :1
```

---

### Post by ayoli on 2009-01-20
> **martin_legion said:**
> The script belongs to my user and group, it has all permitions, and it's located in /usr/local/bin, so it's accesible system-wide (I include the full path in crontab anyway)
I also added exec but nothing changed... what am I doing wrong??
About display 0 or 1:
```
(zenity:18409): Gtk-WARNING **: cannot open display: :1
```
give a try with display=:1 :
```
* * * * * export DISPLAY=:1 && exec /path/to/myscript
```

---

### Post by martin_legion on 2009-01-21
> **ayoli said:**
> give a try with display=:1 :
```
* * * * * export DISPLAY=:1 && exec /path/to/myscript
```

I did. The result is that error message from zenity:
```
(zenity:18409): Gtk-WARNING **: cannot open display: :1
```

---

### Post by ayoli on 2009-01-21
> **martin_legion said:**
> I did. The result is that error message from zenity:
```
(zenity:18409): Gtk-WARNING **: cannot open display: :1
```
This one works here
```
* * * * * export DISPLAY=:0 && midori
```
So maybe the problem isn't here.

---

### Post by martin_legion on 2009-01-21
> **ayoli said:**
> This one works here
```
* * * * * export DISPLAY=:0 && midori
```
So maybe the problem isn't here.

This is very odd. I'm trying the same in my Ubuntu and in another computer running Mandriva without success. My head is a bit burned. I'll try again in a few hours and see if I find what's going on.
Thanks everybody.

---

### Post by ayoli on 2009-01-21
> **martin_legion said:**
> This is very odd. I'm trying the same in my Ubuntu and in another computer running Mandriva without success. My head is a bit burned. I'll try again in a few hours and see if I find what's going on.
Thanks everybody.

did you try to launch something else (eg: firefox) with the cron ?

---

