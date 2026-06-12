---
title: "[SOLVED] Text invisible in terminal."
date: 2008-11-07
forum: Desktop Environments
---

### Post by lenswipe on 2008-11-07
When im typing a command in terminal only the first character before the cursor is visible. The rest cannot be seen until i have executed the command. Some other text like the result of commands is invisible too. Im wondering if anyone is able to help


Cheers

-Lenswipe

---

### Post by NilsE on 2008-11-07
> **lenswipe said:**
> When im typing a command in terminal only the first character before the cursor is visible. The rest cannot be seen until i have executed the command. Some other text like the result of commands is invisible too. Im wondering if anyone is able to help


Cheers

-Lenswipe

Have you tried changing the colors in edit > profile preferences?  The default is to use theme colors but you can change it.

---

### Post by lenswipe on 2008-11-07
> **NilsE said:**
> Have you tried changing the colors in edit > profile preferences?  The default is to use theme colors but you can change it.

its nothing to do with the colors. What happens is im typing a command

lets say sudo apt-get install whatever

while im typing whatever the "sudo apt-get install" is invisible. the only thing i can see is the first character behind the cursor.

Its after i tried to install xfce. Things went kinda crazy but mostly i got it back to normal apart from this.

-L

---

### Post by NilsE on 2008-11-07
> **lenswipe said:**
> its nothing to do with the colors. What happens is im typing a command

lets say sudo apt-get install whatever

while im typing whatever the "sudo apt-get install" is invisible. the only thing i can see is the first character behind the cursor.

Its after i tried to install xfce. Things went kinda crazy but mostly i got it back to normal apart from this.

-L
xfce changes the themes so it may have your background and font colors the same if your are set to default which is to use system theme.  Just for the heck of it try changing the text color in the terminal.

---

### Post by hictio on 2008-11-07
> **NilsE said:**
> xfce changes the themes so it may have your background and font colors the same if your are set to default which is to use system theme.  Just for the heck of it try changing the text color in the terminal.

Have you rebooted after the install?
The next time you see this problem at the terminal, try typing: 'reset', w/o quotes, followed by an ENTER.

It will not reboot, nor anything radical your box, type:

```

man reset (ENTER)

```

to see what it does.

---

### Post by mali2297 on 2008-11-07
Which terminal emulator do you use? (gnome-terminal, xfce4-terminal or something else)

---

### Post by lenswipe on 2008-11-10
meh, works now. Idk wtf was wrong with it. Few reboots later after the xfce install and now it works...

-.-

thanks nyway guys :D

---

### Post by Rack1600 on 2012-12-13
> **hictio said:**
> Have you rebooted after the install?
The next time you see this problem at the terminal, try typing: 'reset', w/o quotes, followed by an ENTER.

It will not reboot, nor anything radical your box, type:

```

man reset (ENTER)

```

to see what it does.

Ah, thanks.  this resolved my issue which was much like the above issue.  Must remember "reset". :) 

Rock on! :guitar:

---

