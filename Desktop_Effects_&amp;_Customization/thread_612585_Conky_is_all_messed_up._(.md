---
title: "Conky is all messed up. :("
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by professor fate on 2007-11-14
I think the picture says it all.  This is what I get when I set up conky to start in the system > pref > sessions.  If I start it from the terminal though...all is good.  Suggestions?

PF

---

### Post by alphane on 2007-11-14
Looks like you're running compiz with those shadows.  I used to get it sometimes on boot up before I dropped all eye candy.

I think it's to do with the order that your startup programs are being launched.   I can't remember which way around it needs to be, so you'll need someone else here to help, I solved mine with the use of a script that made sure that compiz/conky were started in the correct order.

I'm sure a good ole' search will reveal the thread which helped me last time around.

---

### Post by Sqwishy on 2007-11-14
I'm guessing your problem is the "transparent" background on conky. K see when it runs it looks to see if the windows manager has compositing enabled, and when conky is starting, metacity is running and not compiz (which has compositing) hasn't started yet... anyway. Just make a delay for conky's start thingy, unfortunately the gnome startup thing is rather stupid and doesn't let you do complicated commands, so you'll wana make the startup thing run a script to start conky with a delay, rather than just starting conky.

In a terminal run ' gedit .start_conky.sh ' (without quotes)

In gedit put the following
```
#!/bin/bash
sleep 7
conky

```
The #!/bin/bash lets ubuntu know it's a shell script
sleep is a command and we told it to sleep for 7 (seconds is default if you don't specify what unit if time your using)
and conky will just run conky

Then still in your terminal make it an executable by running ' chmod +x .start_conky.sh '

Then in your start up session things replace the entry that runs conky with an entry that runs the conky script we made. To do this, edit the entry and click browse next to the command textbox, you should be at your home folder, and you should of saved your conky script in your home folder (that's like the default sorta), so either you can right click on the list of folders and click "show hidden files" (it's hidden because the filename starts with a . ), or you can just start tying the file name in the location bar at the top. Anyway, after you find it it should show something like "/home/<your_username>/.start_conky.sh" in the command place.

Then it should work next time you log in, if it doesn't then i'm sorry and you can reply here and attack me or something.

---

### Post by Jonne on 2007-11-14
Heh, you're the first person I've seen that actually voluntarely set his homepage to msn.com ...

As for your problem with conky: I think it would help if you posted your .conkyrc file (that should be a hidden file in your home directory).

---

