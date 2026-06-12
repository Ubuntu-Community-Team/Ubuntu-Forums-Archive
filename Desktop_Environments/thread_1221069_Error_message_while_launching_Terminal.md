---
title: "Error message while launching Terminal"
date: 2009-07-23
forum: Desktop Environments
---

### Post by nizdobs on 2009-07-23
I have a launcher item for Terminal under Applications, Accessories, Terminal on the Gnome menu. The command run for this launcher is: gnome-terminal

When I launch terminal I see the following message:
bash: 526874_0225.option_sorted: command not found

"526874_0225.option_sorted" is a data file that I saved to my machine long ago. Why is gnome-terminal doing when it launches to make it think it's supposed to use this file? Is there some kind of a properties file for gnome-terminal that I can set so this error goes away?

Thanks,

- Niz

---

### Post by wojox on 2009-07-23
Try to reset the gnome terminal

```
gconftool-2 --recursive-unset /apps/gnome-terminal
```

---

### Post by nizdobs on 2009-07-23
Thanks very much for the reply. Unfortunately, that command didn't do the trick. Do I need to do anything special after running that command?

Thanks,

- Niz

---

### Post by wojox on 2009-07-23
Have you been messing with any of you .bash files ?

---

### Post by drs305 on 2009-07-23
> **nizdobs said:**
> I have a launcher item for Terminal under Applications, Accessories, Terminal on the Gnome menu. The command run for this launcher is: gnome-terminal


Is this the default launcher or one you created/replaced?

If you run this (the launcher's config file) does it provide any insight?
```

cat $HOME/.local/share/applications/gnome-terminal.desktop

```

---

### Post by mcduck on 2009-07-23
Do you get same message with another terminals, or is it just with gnome-terminal? Try xterm (it's installed by default) or log into one of the TTYs.

If it's just with gnome-terminal, you either have that command in the terminal's profile, or the launcher. If the same happens with any terminal check your .bashrc and .profile -files.

---

### Post by Dullstar on 2009-07-23
What version of Gnome/Ubuntu are you running?

---

### Post by nizdobs on 2009-07-23
> **wojox said:**
> Have you been messing with any of you .bash files ?

Yes. I needed to set some environment variables in ~/.bashrc. Might this have introduced the problem?

Thanks,

- Niz

---

### Post by nizdobs on 2009-07-23
> **Dullstar said:**
> What version of Gnome/Ubuntu are you running?

Gnome: 2.26.1
Ubuntu: 9.04

Thanks for any help you can provide.

- Niz

---

### Post by nizdobs on 2009-07-23
> **drs305 said:**
> Is this the default launcher or one you created/replaced?

If you run this (the launcher's config file) does it provide any insight?
```

cat $HOME/.local/share/applications/gnome-terminal.desktop

```

It's the default launcher. Running the command you suggested yields the output below. Thanks for any help you can provide.

[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.26.0
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
NotShowIn=XFCE;
X-Ubuntu-Gettext-Domain=gnome-terminal

---

### Post by nizdobs on 2009-07-23
> **mcduck said:**
> Do you get same message with another terminals, or is it just with gnome-terminal? Try xterm (it's installed by default) or log into one of the TTYs.

If it's just with gnome-terminal, you either have that command in the terminal's profile, or the launcher. If the same happens with any terminal check your .bashrc and .profile -files.

I didn't see a launcher for xterm. So I installed the PuTTY Terminal Emulator. When it launched I got the same message.

Thanks for all the help.

- Niz

---

### Post by drs305 on 2009-07-23
There was nothing of interest in the results of the gnome terminal .desktop file, but I would expect that once you said it also did the same with other terminals. 

Do you get the same result when you open a terminal with sudo? That would help pin it down to global or user settings.

---

### Post by nizdobs on 2009-07-23
> **drs305 said:**
> There was nothing of interest in the results of the gnome terminal .desktop file, but I would expect that once you said it also did the same with other terminals. 

Do you get the same result when you open a terminal with sudo? That would help pin it down to global or user settings.

Sorry to be clueless, but can you please tell me which command to issue to open terminal with sudo? I tried sudo gnome-terminal but received the following error:
[COLOR="Sienna"]Failed to contact the GConf daemon; exiting.[/COLOR]

Thanks.

---

### Post by drs305 on 2009-07-23
> **nizdobs said:**
> Sorry to be clueless, but can you please tell me which command to issue to open terminal with sudo? I tried sudo gnome-terminal but received the following error:
[COLOR="Sienna"]Failed to contact the GConf daemon; exiting.[/COLOR]

Thanks.

You aren't being dense. :D  Although I never had the problem, research shows it was reported as a bug. Of course, I might not have taken you down this path if I'd known that.
[https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575]("https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575")  

I'm still reading through the extensive bug reports to see if the issues might be related. I'll come back and edit this post when I've finished checking.
Edit: Nothing related to the original problem, although there is a script for fixing the "sudo gnome-terminal" problem.

In the meantime, you might try a text search of "option_sorted" via the Places, Search for Files, Select More Options, Text Search. I would try searching your entire HOME folder to see if you can find that text string in a configuration file.  You could also open gconf-editor ("gconf-editor") and do a similar search there.

---

### Post by mcduck on 2009-07-23
> **nizdobs said:**
> I didn't see a launcher for xterm. So I installed the PuTTY Terminal Emulator. When it launched I got the same message.

Thanks for all the help.

- Niz

you could have launched xterm from gnome-terminal, or the run-dialog (opened by pressing Alt-F2).

Anyway, since the problem clearly isn't specific to Gnome-terminal did you check .bashrc and .profile like I suggested?

---

### Post by nizdobs on 2009-07-23
> **mcduck said:**
> you could have launched xterm from gnome-terminal, or the run-dialog (opened by pressing Alt-F2).

Anyway, since the problem clearly isn't specific to Gnome-terminal did you check .bashrc and .profile like I suggested?

Is there only one .bashrc and .profile files or do I need to check for these files in multiple places?

Thanks,

- Niz (the noob)

---

### Post by mcduck on 2009-07-23
> **nizdobs said:**
> Is there only one .bashrc and .profile files or do I need to check for these files in multiple places?

Thanks,

- Niz (the noob)

One file for each user, in that user's home directory.

You only need to check the files in your own home, they are personal setting files so nobody else's settings would have any effect on your terminals.

---

### Post by nizdobs on 2009-08-05
I wasn't able to get a resolution to this and it was driving me batty so I gave up on it considering that it wasn't actually causing me any real problems.

Then today I noticed that 526874_0225.option_sorted was a file in my Home folder. Alphabetically it is the first file in that directory. So I renamed the file to 526874_0225.option_sorted2 and brought up a terminal window. The prompt on the terminal window reflected the changed file name. Next I created a file aa.txt and renamed the original file to Z526874_0225.option_sorted2. Now when I brought up a terminal window I was prompted with: bash: aa.txt: command not found

So somehow terminal is trying to reference the first file in my Home Folder. But why? One other potenitally interesting note: When I rename the file a.txt the terminal window does not include a.txt in the prompt but, rather, the next file alphabetically. So a one character filename doesn't get picked up.

Does any of this help with figuring out what's going on?

Thanks,

- Niz

---

