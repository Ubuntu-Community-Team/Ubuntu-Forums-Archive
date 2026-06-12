---
title: "Help with Conky"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by Fraser from Scotland on 2008-01-19
1. Where is the .conkyrc file? I have lost it, lol.
2. How do I change the colour of the grey writing to black?
3. How do I get conky to start at boot?

Feel free to add me on msn if it will be easier, [email]drum_man101@hotmail.com[/email]

---

### Post by Fraser from Scotland on 2008-01-19
Bump :)

---

### Post by FuturePilot on 2008-01-19
It's probably in your home folder but hidden. Press Ctrl+H in your Home folder and you will see all your hidden files.
As for getting it to start at login, I make a script to do that.
```
gksudo gedit /usr/local/bin/start_conky.sh
```
Add this
```
#!/bin/bash
sleep 15;
exec conky -d
exit

```
You can change the number after sleep to adjust the delay in seconds. It's good to have it start after a delay because if Conky starts before your wallpaper shows up, Conky will disappear. So you can adjust that to your liking.
Now make it executable
```
sudo chmod +x /usr/local/bin/start_conky.sh
```
Now go System>Preferences>Session and add a new entry. Give it a name and add this for the command
```
start_conky.sh
```
You can also give it a description if you like.

---

### Post by p_quarles on 2008-01-19
Conky comes with a sample config, but it's not initially in your home folder. This command will get it there:
```
$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

---

### Post by ilLorenz on 2008-01-20
hi everyone, I just installed conky and I have the same problem about making it start at boot: I tried following the instructions from FuturePilot, using a bash script and making it executable, then adding it to the Sessions panel, but it didn't work: here is the .sh script I'm currently trying:

#!/bin/sh
sleep 40s
exec conky 
exit 

I removed the -d option as if I used it running conky from the command line it didn't show up at all... I also tried adding a line to the session panel like this: sleep40 ; conky & exit but it didn' t work as well... I have the same problem setting the embedded terminal to show at startup... about that I tried with a script and with a direct command, but it didn't work as well.... any ideas why this happens?

Thanks in advance, and please forgive my bad english ;-)

PS: I just noticed that when I start conky from command line, if i press Control+C it disappears together with the terminal, but if I run it like this: conky & exit, the terminal disappears and conky remains active... is this normal? Thanks...

---

### Post by torgrot on 2008-01-20
I now have conky starting up after login, but it ignores my alignment sent spacing settings.  How do I get it to follow the```

alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 20

```

torgrot

---

