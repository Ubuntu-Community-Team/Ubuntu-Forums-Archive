---
title: "'Conversation with su failed?'"
date: 2006-01-12
forum: General Help
---

### Post by Glass Casket on 2006-01-12
I get that error after I put my password for Adept.

And yes, I am sure I'm putting in the right password.

---

### Post by amohanty on 2006-01-13
Drop into the recovery console, and post the output of:
> cat /etc/sudoers

If you dont see your username in there:
add the following at its end:
> your_username ALL=(ALL) ALL

You can do so in the console using 
> visudo /etc/sudoers
then get to the end of line and press the following keys in succession (I am assuming you dont know how to use vi):
> 
<esc>
a
<enter>
your_username ALL=(ALL) ALL
<esc>
:wq<enter>


stuff between < and > means key.

HTH
AM

---

### Post by DaveQB on 2006-08-25
I have this same problem on a brand new install of Dapper 6.06 64-bit (Kubuntu)

in sudoers there is the %admin group in there and I am part of that.  sudo works fine, just not kdesu.

Perhaps this is fixed in 6.06.1

---

### Post by Hoary on 2006-08-31
It happened with me, too, with Kubuntu version um, er, I forget but anyway downloaded from kubuntu.org the day before yesterday.

The procedure to fix it turns out to be slightly simpler than explained above. It's not

> visudo /etc/sudoers

but instead simply

> visudo

and for me this invoked not vi but instead nano. I'd never used nano either, but the instructions are at the foot of the screen: basically you edit the file (sudoers.tmp) as if you were using any mass-market text editor (even M$ Notepad) and then hit Ctrl-X.

That worked.

This is my first day with Kubuntu and I've never used Ubuntu, Debian, or indeed anything closer to Kubuntu than SuSE (and I never really got the hang of that), so I may understand even less than I realize. However, I'm puzzled by the security angle: as far as I remember, when I booted into the recovery console I wasn't asked to identify myself, and having got in I certainly didn't have to give any password in order to be able to futz around with the sudoers file. As it happened, this was most convenient for me, but I worry about who might walk into my office and play with the computer while I'm out.

---

### Post by DaveQB on 2006-08-31
The reason it used nano was becuse your env variable $EDITOR was set to nano or it was unset and the system fallback default was/is nano.

Odd that you could execute visudo without supplying a password, unless you recently authenticated with sudo.

Doesn't work for me 

```

david@jlh ~ $ visudo                                                            
visudo: /etc/sudoers: Permission denied


```

And I had recently executed 'sudo ls'

:-?

---

### Post by Bill-Turnbull on 2007-01-13
I was geting the same message when trying to get into admin mode to change display settings (probably other areas too)...

The way I fixed mine, came from reversing the last change I made that I thought would get me into trouble...

I had added a user on the end of the admin line in the /etc/group file


So, after reading a few other posts I booted into recovery mode
(Press ESC when Grub is loading and pick <version? Recovery mode)

```
pico /etc/group
```
and removed the new user from the admin line...

It was originally something like:  

```
admin:x:106:bill
```

I made it: 

```
admin:x:106:bill:mythtv
```
and thats where my prob started so after recovery mode, edit /etc/group and removing :mythtv it's all good again...

Yipppeee

HOPE THIS HELPS OTHER NEWBIES! :)

Bill

---

### Post by DaveQB on 2007-01-14
commas sperated values for the /etc/group file.

Like so

```

plugdev:x:46:david,mythtv

```

---

### Post by Pontiac on 2007-03-15
The question I have is what CAUSES this all to happen?

Theoretically, the problem I see is if someone gets a hold of my account because I walk away from the machine, they basically have control of the machine to do whatever they want pertaining to service, applications, cron jobs, etc, etc, and anything that can be done through the KDE UI system config stuff.

This is a decent patch, but where does this whole issue stem from?

---

### Post by actanner on 2007-04-21
Here's a possible reason, and a possible solution:
   I recently tried to upgrade from Kubuntu 6.10 to 7.04, but that failed.  I have three partitions: /, /usr, and /home.  I wound up reformatting / and /usr, and left /home alone.  When I tried to boot up after installation, the system didn't recognize my user name.  I went into "recovery" mode and added my old user name as a user, and then I could log in.  But then I began to get the "conversation with su failed" message when I tried to use sudo.  After much experimentation and web searching, I decided that maybe some of my old configuration information in /home was not compatible with the new installation.  I deleted the .kde directory and the .kderc file under my home directory, and rebooted.  The problem was solved.  :)

---

### Post by Pontiac on 2007-04-23
So that'd tell me that theres some sort of corruption going on within KDE... But the problem persists outside of KDE as well.  Even in the consoles (CTRL-ALT-F1) it messes up and says it can't do its thing.

But I'm thinking we're on the right track with corruption anyways.  Question stands as to what specifically is causing this corruption?

Being that I'm a tech a at a computer shop, when I get a machine in, I have to know what the alement is, and whats caused it.  *MOST* of the time its apps like Kazaa, bear share, lime wire and other crapware like that.  To be fair, its usually the third party apps that these P2P apps give that give such grief.  I gotta know how to repair and prevent that software from doing its damage again.  In my case, I want to know what the root of the problem is, and figure a way to prevent it.  Right now, my linux box (Although no one here other than myself knows how to run it) runs as the patch above says, but, that doesn't mean I feel better about not having to put in my password when I make a system change.

---

