---
title: "howto: minimize evolution to tray"
date: 2010-05-07
forum: Desktop Environments
---

### Post by nZain on 2010-05-07
With Lucid I gave evolution another try (actually the fourth time I installed a new Ubuntu version) and after some fiddling it worked (the first time, sadly). I like the idea to gather all "message" like things in one tray icon, so basically I like the indicator-applet. However, there is no way to customize it and many users complain about this. One particular issue is that evolution cannot be minimized to this tray icon. There are a lot of workarounds, all of them (to my knowledge) circumventing the indicator-applet and using an individual tray icon. But today, I found out how to do it. So...

You want to use the indicator-message icon, but minimize evolution without an entry in the window-list?

Devilspie has the "skip_tasklist" capability. So, install _[COLOR=Blue][devilspie]("http://wiki.ubuntuusers.de/devilspie")[/COLOR]_ and create a script for evolution mail, e.g.  $HOME/.devilspie/evolution.ds like this:
```
( if 
  ( and
    ( matches (application_name) "evolution" )
    ( matches (window_name) "^.*-.Evolution" )
  )
  ( begin 
    ( println "--[ Evolution ]--" )
    ( pin )
    ( skip_tasklist )
    ( minimize )
  )
)
```When evolution is started, the script pins evolution (so its available on all workspaces), enables skip_tasklist (so it is not shown in the window list), and minimizes it.

best
    Patrick

---

### Post by x-shaney-x on 2010-05-07
Hmm, it's doing nothing here.

I added the file as well as a "test" firefox rule to make sure it's working.
When run from a terminal devilspie is showing both the .ds files are being read but doesn't actually do anything.

Though I do get a message saying /etc/devilspie doesn't exist.

---

### Post by iamnotthemessiah on 2010-05-07
not working here either. devilspie running

---

### Post by aeltester on 2010-05-09
works right here.

```
( if 
  ( and
    ( is (application_name) "evolution" )
    ( matches (window_name) "^.*-.Evolution" )
  )
  ( begin
    ( pin )
    ( skip_tasklist )
    ( minimize )
  )
)
```

---

### Post by x-shaney-x on 2010-05-09
That's not working for me either :(

---

### Post by nZain on 2010-05-10
Hmm, too bad :-( When you run devilspie in a terminal with the debug option, i.e.
```
devilspie -d
```do you get the println output from my original code? Eventually, the regular expression may not work in your language setting? On my system, the output looks like this, when I have both firefox and evolution open:
```
patrick@patrick-laptop:~$ devilspie -d
Devil's Pie 0.22 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/patrick/.devilspie
Loading /home/patrick/.devilspie/evolution.ds
Loading /home/patrick/.devilspie/firefox.ds
5 s-expressions loaded.
--[ Firefox ]--
Setting geometry '1024x750+1280+0'
Setting pinned
--[ Evolution ]--
Setting pinned
Skipping tasklist
Minimising
```As you see, it also says that /etc/devilspie is missing on my system, probably some default settings that are loaded optionally. Furthermore, I'm not sure if that works with other panel implementations - I'm using the default in gnome, i.e. gnome-panel.

---

### Post by x-shaney-x on 2010-05-10
```
Devil's Pie 0.22 starting...
Loading /etc/devilspie
Loading /home/shane/.devilspie
Loading /home/shane/.devilspie/calc.ds
Loading /home/shane/.devilspie/evolution.ds
Loading /home/shane/.devilspie/firefox.ds
Loading /home/shane/.devilspie/openoffice.ds

4 s-expressions loaded.
```

That's it.  It isn't just evolution, none of them are doing anything.  The other files are just tests but I have tried all sorts of different expressions from different parts of the web and NOTHING is working for me.
I created the /etc/devilspie directory but made no difference.

---

### Post by Eggenheimer on 2010-05-10
It works for me if I make the match a bit more relaxed like this:

```

( if
  ( matches (window_name) ".+Evolution$" )
  ( begin
    ( println "--[ Evolution ]--" )
    ( pin )
    ( skip_tasklist )
    ( minimize )
  )
)


```

---

### Post by x-shaney-x on 2010-05-10
Thanks, NOW it's working.
None of my others are though.  Not that it matters since I only want it for Evo :)

---

### Post by mirajshah on 2010-08-25
i'm quite sure both nZain's and Eggenheimer's scripts work for me; devilspie runs for me, i have the script in /etc/devilspie (i use opensuse), and when i open evolution the window wireframe thingy appears to maximize then minimize to the tray.  The problem is, I can't seem to get a tray icon.... is this how the scripts are intended or is something wrong?

i'd really prefer to have a tray icon :)

---

### Post by mirajshah on 2010-08-25
TERMINAL OUTPUT
linux-bu4e:/etc/devilspie # devilspie -d
Devil's Pie 0.22 starting...
Loading /etc/devilspie
Loading /etc/devilspie/evolution.ds
Loading /root/.devilspie
/root/.devilspie doesn't exist
1 s-expressions loaded.
--[ Evolution ]--
Setting pinned
Skipping tasklist
Minimising

---

### Post by nZain on 2010-09-03
> **mirajshah said:**
> i'm quite sure both nZain's and Eggenheimer's scripts work for me; devilspie runs for me, i have the script in /etc/devilspie (i use opensuse), and when i open evolution the window wireframe thingy appears to maximize then minimize to the tray.  The problem is, I can't seem to get a tray icon.... is this how the scripts are intended or is something wrong?

i'd really prefer to have a tray icon :)

Devilspie does not create a tray icon for you. With the current Ubuntu version, there is a tray icon + you get a evolution entry in your window list. What devilspie does here, is to hide the window list entry - it does nothing with tray icons.

However, you're half way there: Install one of the tray icon thingys that support evolution and you got 1) a tray icon for evolution and 2) only the tray icon, but not the disturbing panel entry.

best
  nZain

edit: I'm not sure about Suse - you'll have to find a tray icon tool on your own.

---

### Post by User4519 on 2011-02-06
Is this just removing it from the task bar, or does it disappear also when Alt+Tab'ing, using Present Windows, etc.? I'd like for it to just get the f*** out of my general desktop and stay in that tray completely until clicked :)

I'm on the Netbook edition, btw. Not sure if that makes any difference. I don't mind it being in the dock as the square icon thing, I just hate that it's always there when I Alt+Tab or present windows or workspaces.

---

