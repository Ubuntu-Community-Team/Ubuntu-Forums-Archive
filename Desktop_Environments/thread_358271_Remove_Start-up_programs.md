---
title: "Remove Start-up programs"
date: 2007-02-10
forum: Desktop Environments
---

### Post by sinister99 on 2007-02-10
Every time i log into my computer (Edgy), about 5-10 programs automatically start.  These programs are usually the last few programs I had open (they are closed before I shut down), and I really would like to stop this from happening.

Something related: programs that I have previously removed from my startup list still run.

I am using Gnome

Any suggestions?

---

### Post by paparucino on 2007-02-10
> **sinister99 said:**
> Every time i log into my computer (Edgy), about 5-10 programs automatically start.  These programs are usually the last few programs I had open (they are closed before I shut down), and I really would like to stop this from happening.

Something related: programs that I have previously removed from my startup list still run.

Close all your applications then
```

 Control Center -> Sessions -> Session options -> Save current session

```

if this doesn't work 
```

sudo gedit /home/your user/.gnome2/sessions

```
Here you'll all the apps which auomatically starts. Remove them deleting the line and updating the number at the begin of the line.

Use this options **[COLOR="Red"]ONLY[/COLOR]** if you know what you are doing and **[COLOR="Red"]ONLY[/COLOR]** if the prevous code doesn't work.

---

### Post by ComplexNumber on 2007-02-10
> sudo gedit /home/your user/.gnome2/sessions
sudo(for graphical applications, gksudo should be used instead) is not necessary to edit ones home directory.

---

### Post by paparucino on 2007-02-11
> **ComplexNumber said:**
> sudo(for graphical applications, gksudo should be used instead) is not necessary to edit ones home directory.
You're right. I was watching TV while writing :-)

---

### Post by sinister99 on 2007-02-11
> **paparucino said:**
> Close all your applications then
```

 Control Center -> Sessions -> Session options -> Save current session

```

if this doesn't work 
```

sudo gedit /home/your user/.gnome2/sessions

```
Here you'll all the apps which auomatically starts. Remove them deleting the line and updating the number at the begin of the line.

Use this options **[COLOR="Red"]ONLY[/COLOR]** if you know what you are doing and **[COLOR="Red"]ONLY[/COLOR]** if the prevous code doesn't work.

I tried both of these, and it still does the same thing.  If I edit the session file and save it, it somehow gets changed back to its original state when I end my session.

---

### Post by paparucino on 2007-02-11
> **sinister99 said:**
> I tried both of these, and it still does the same thing.  If I edit the session file and save it, it somehow gets changed back to its original state when I end my session.
Last try, for me. :-) :-)
In Control Center -> Sessions -> Startup Programs is there something which resemble one of your annoying programs?

---

### Post by sinister99 on 2007-02-11
> **paparucino said:**
> Last try, for me. :-) :-)
In Control Center -> Sessions -> Startup Programs is there something which resemble one of your annoying programs?

That was the first thing I tried ;-)

---

### Post by sinister99 on 2007-02-13
I have temporarily fixed the problem by editing my /home/username/.gnome2/session to remove the programs I didn't want to run, and then making the file read-only.

---

### Post by sabrewolf2006 on 2007-05-02
In Edgy
There is a checkbutton in amongst the session preferences called 'automatically save changes to session'.. not sure where atm, if you uncheck that it will stop altering your session.. if this doesn't work you can try and change the option using gconf-editor
its under the key /apps/gnome-session/options 
In Feisty
There should be a tab in the sessions preferences called Session options.. There is a checkbox called 'Automatically save changes to session', If you uncheck that, that should have the same effect.. It also has a button that allows you to save your current session options immediately.

Hope this helps

---

### Post by beow on 2007-07-16
Have a similar problem. But whatever I do I get the same start up behaviour, with same programs running. Is there any way to completely "reset" gnome-session, to start from scratch?  Removing the session file or something?

---

### Post by the yawner on 2007-07-29
I had this problem about a minute ago before I stumbled on this thread. Taking clues from your posts, I checked Sessions under Preferences, and found on the Current Session tab all applications which are saved on the */home/your user/.gnome2/sessions* file. I removed the unwanted programs, stopped other unwanted applications, and saved the session. And that worked. :)

> **sinister99 said:**
> I have temporarily fixed the problem by editing my /home/username/.gnome2/session to remove the programs I didn't want to run, and then making the file read-only.
My guess is that the file is always overwritten by that listed on the Current Session tab I mentioned above. So as long as the unwanted programs listed on that tab, it will always reflect on the file.

---

### Post by lexmiller on 2007-08-10
I had this problem too. I think I know the answer.

I think that the session file is only present if you save a session. It then overrides what would happen otherwise. If you have never saved a session then it appears to use ~/.config/autostart

You can find out more about the problem (and problems like these) by running the program from the command line. That way you can see any error messages that the program throws up.

lex@latitude-x1:~$ gnome-session-properties

** (gnome-session-properties:7676): WARNING **: Could not save /home/lex/.config/autostart/beagled-autostart.desktop file

lex@latitude-x1:~$ ls -ld .config
drwx------ 5 lex lex 1024 2007-08-09 17:43 .config
lex@latitude-x1:~$ ls -ld .config/autostart/
drwxr-xr-x 2 root root 1024 2007-08-10 15:12 .config/autostart/

So it is trying to write to the ~/.config/autostart directory by can't because it doesn't have permission.

I don't know how the permissions came to be this way, but I suspect that ~/.config/autostart is supposed to be owned by the user (not by root). Here's my fix:

lex@latitude-x1:~$ sudo chown lex:lex .config/autostart

You'll want to replace my user name by yours of course.

After this I was able to run System -> Preferences -> Sessions and it would happily save my changes.

I hope it works for you too.

---

### Post by beow on 2007-08-11
Found a solution to the session problem in [https://answers.launchpad.net/ubuntu/+question/11154](https://answers.launchpad.net/ubuntu/+question/11154)
Essentially you start gnome-session-properties in a shell and watches the error messages.

---

