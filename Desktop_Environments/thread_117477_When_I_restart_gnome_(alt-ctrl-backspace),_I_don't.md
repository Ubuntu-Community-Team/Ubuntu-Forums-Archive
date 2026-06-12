---
title: "When I restart gnome (alt-ctrl-backspace), I don't have graphical login screen - why?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by Turin Turambar on 2006-01-15
Sometimes, only sometimes I go into the graphical login screen! :confused:  Usually it's just a plain text (terminal mode) and I have to manually enter "startx" after login.
What did I miss?

---

### Post by Mr_Grieves on 2006-01-15
Alt+Ctrl+Backspace KILLS you're X Windows enviorment :) It's not the restart sequence as I know.

---

### Post by art on 2006-01-15
What you need to do is, after Ctrl-Alt-Bksp do
sudo killall gdm
 and then 
sudo /etc/init.d/gdm start
to start gnome login manager. I don't know why it doesn't work sometimes.

---

### Post by Turin Turambar on 2006-01-15
[QUOTE=Mr_Grieves]Alt+Ctrl+Backspace KILLS you're X Windows enviorment :) It's not the restart sequence as I know.[/QUOTE]

Actually, it restarts Gnome without rebooting. :) At least that's what I read in Unofficial Ubuntu guides.

So...... is that (not showing a gnome login manager) a bug?

---

### Post by twigboy on 2006-01-15
Sometimes when i ctrl+alt+ backspace my gdm doesnt even come up.  No gui no text.  But I can hear the sound the ubuntu makes when it loads the gdm gui. After that I have to restart.

---

### Post by MaX on 2006-01-15
[QUOTE=Turin Turambar]Actually, it restarts Gnome without rebooting. :) At least that's what I read in Unofficial Ubuntu guides.

So...... is that (not showing a gnome login manager) a bug?[/QUOTE]

Well that's just wrong. CTRL+ALT+Backspace DOES KILL X.
When I want to restart gnome without rebooting I usually log out and in again. That's enough to get it restarted. It also saves you the trouble of GDM crashing and you having to do startx manually.

---

### Post by Turin Turambar on 2006-01-15
Well, something isn't right here... Even if I type "sudo /etc/init.d/gdm restart", it just kills GDM and does NOT restart! The command "force-reload" doesn't work either.

And as I said, *sometimes* it works flawlessly (alt-ctrl-back)... :confused:

---

### Post by art on 2006-01-15
As I said, do an sudo killall gdm, and then start gdm, because there might be 2 gdms running, as I noticed doing ps aux|grep gdm. 
HTH

---

### Post by Turin Turambar on 2006-01-15
[QUOTE=art]As I said, do an sudo killall gdm, and then start gdm, because there might be 2 gdms running, as I noticed doing ps aux|grep gdm. 
HTH[/QUOTE]

You were right, I already did. I just wanted to point out that it didn't reload as Ubuntu guides claimed.

Here's what I got:

```
ivan@ubuntu-Ivan:~$ ps aux|grep gdm
root      7840  0.0  0.5  10608  2584 ?        Ss   15:06   0:00 /usr/sbin/gdm
root      7845  0.0  0.5  10944  3008 ?        S    15:06   0:00 /usr/sbin/gdm
root      7885  2.6  6.6  38448 34296 ?        SL   15:06   8:56 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
ivan     18803  0.0  0.1   3068   768 pts/0    S+   20:38   0:00 grep gdm
ivan@ubuntu-Ivan:~$

```

Is that ok?

---

### Post by rado_london on 2006-01-16
Hi
I have this issue when I change something in the Xorg.conf file.
Once I do CTRL+ALT+BACKSPACE it takes me to the terminal. Then I do 
```
sudo pkill gdm
sudo gdm
```

This works everytime for me.

---

