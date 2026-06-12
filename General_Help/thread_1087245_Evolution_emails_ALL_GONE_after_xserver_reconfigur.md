---
title: "Evolution emails ALL GONE after xserver reconfigure"
date: 2009-03-04
forum: General Help
---

### Post by dodd_alex on 2009-03-04
I chose to completely switch over to Ubuntu from Windows 2000 when I got a new desktop about a month ago and have been using it exclusively ever since. Just when my faith was stabilizing, this happened:

After some recent tinkering due to problems I've been having with Intrepid's Suspend Mode, I was unable to load the graphical interface and was forced to enter the following commands:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity (to reset my desktop appearance to it's defaults)

sudo dpkg-reconfigure xserver-xorg (to reset the xserver to it's defaults, i guess)

While resetting up my desktop I opened evolution and it now opens with the new user setup screen and has none of my emails or settings. I had been importing from my hotmail and gmail accounts since I felt secure in Ubuntu and had downloaded years of emails onto my computer. I hadn't had a chance to back them up yet, and now they appear to be gone. I found the file .evolution in my home folder, and it has files in it but they seem to be inaccessible and I can't even tell what if anything is in them.

Can somebody please explain to me what happened and if my files might be recovered still?

Thanks!

---

### Post by hexanol on 2009-03-04
Someone else might confirm this, but since Evolution is one official stuff used by GNOME, it may be storing user configurations files and email in the .gnome folder. So you erased your messages. I suspect (but I can't confirm, it just seems plausible).

EDIT: ok sorry, I didn't read correctly your post, my post is useless. :D

---

### Post by Therion on 2009-03-04
> **dodd_alex said:**
> Can somebody please explain to me what happened and if my files might be recovered still?

I'm no expert on the Command Line, so I'll bow to any CLI Ninja that jumps into the conversation, but here's my take on what you did, and really this ain't rocket science so I know I'm not too far off when I tell you this...

See that **rm -rf** command you typed in?  That didn't reset your desktop *appearance* my friend; that command did a file-remove (rm) without confirmation (-rf).

Those files that follow, all the .gnome, .gconf etc?  Those were your configuration files.  In short, those commands didn't just reset the *appearance* of your desktop, they reset your entire *desktop environment* by deleting your configuration files. Starting to get the picture?

And you have no backups you say...

Well, I'm not sure what to tell you then.  I very seriously doubt your lost files can be recovered.  I'd sit tight though, do as little on your PC as possible to avoid ruining any still existing possibility of recovery, and hope that someone who knows a whoooole lot more than I do comes along with some magic bullet for you.

Good luck.


***** EDIT:**

It just occured to me that it's possible... Just POSSIBLE mind you, that the missing config files are hanging around in one of the.trash folders.  I'd have a look in two places for them:

1.  /home/<user_name>/.Trash

and

2.  /root/.Trash 

You'll need to enable "Show Hidden Files" in the View menu or use Ctrl+H to check if the files remain.

---

### Post by dodd_alex on 2009-03-05
no luck in the trash files. is it possible that the files haven't actually been erased and have just been reassigned to be written over? if so, where could i find such programs. is there a program i can install that would help/allow me to access such files?

---

### Post by dcstar on 2009-03-05
> **Therion said:**
> 
.......
It just occured to me that it's possible... Just POSSIBLE mind you, that the missing config files are hanging around in one of the.trash folders.  I'd have a look in two places for them:

1.  /home/<user_name>/.Trash

and

2.  /root/.Trash 

You'll need to enable "Show Hidden Files" in the View menu or use Ctrl+H to check if the files remain.

There is no point whatsoever in looking at a GUI Trash system for files deleted using the command line.

When you use the command line you bypass all the things that a GUI provides, which is why people who do not know what they are doing should not be doing these things.

If there is anything this going to hold back Linux from being useful for the majority of "ordinary" computer users, it is the unhealthy obsession of people (continually) being advised to use the command line to do potentially dangerous things.

---

### Post by dcstar on 2009-03-05
> **dodd_alex said:**
> 
.........
After some recent tinkering due to problems I've been having with Intrepid's Suspend Mode, I was unable to load the graphical interface and was forced to enter the following commands:

**rm -rf .gnome .gnome2 .gconf .gconfd .metacity** (to reset my desktop appearance to it's defaults)
........
Can somebody please explain to me what happened and if my files might be recovered still?

Thanks!
First the explanation of what happened:
[LIST=1]
[*]You "tinkered"
[*]You deleted folders that contained vital configuration settings - like all the Evolution account credentials.
[/LIST]
All the e-mails should still be in .evolution/mail/local, go to that folder and post the output of:
```
ls -al
```

---

### Post by dodd_alex on 2009-03-05
> **dcstar said:**
> First the explanation of what happened:
[LIST=1]
[*]You "tinkered"
[*]You deleted folders that contained vital configuration settings - like all the Evolution account credentials.
[/LIST]
All the e-mails should still be in .evolution/mail/local, go to that folder and post the output of:
```
ls -al
```

Thanks for your help. As I originally wrote, I have found the .evolution folder and since discovered that the files in it are empty. It seems they've been reset.

I said I tinkered and what I meant is that I followed these instructions:

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

where the article and the comments say nothing about losing all of your mail, just losing your settings.

And while I agree that the encouragement of command line use in GNU/Linux based OS' is overwhelming and gives too much control to a beginner user, I think that negativity in a forum as open as cooperative as this is just as inhibiting to anybody trying to prevail in a world without microsoft.

If anyone can suggest another way please post. Thanks again.

---

### Post by dcstar on 2009-03-05
> **dodd_alex said:**
> Thanks for your help. As I originally wrote, I have found the .evolution folder and since discovered that the files in it are empty. It seems they've been reset.

I said I tinkered and what I meant is that I followed these instructions:

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

where the article and the comments say nothing about losing all of your mail, just losing your settings.

And while I agree that the encouragement of command line use in GNU/Linux based OS' is overwhelming and gives too much control to a beginner user, I think that negativity in a forum as open as cooperative as this is just as inhibiting to anybody trying to prevail in a world without microsoft.

If anyone can suggest another way please post. Thanks again.

The article that has now caused you to LOSE all of your mail is a perfect example of what I am saying. It is basically irresponsible because it has had this side effect and you have been left with lost data because of the general inadequacy of things like this. Yes it is "convenient" to tell people just to use this/that command, but "convenient" is not always the proper solution (as you have found).

No "HOWTO" that deletes system folders should exist without specific instructions (or scripts) for people to back up anything that they are going to delete so they have some sort of "roll back" recovery.

IMHO these things can do more harm than good, and while some may appreciate the "learning experience" those that lose data don't really come away with a good feeling about Linux.

---

### Post by dodd_alex on 2009-03-06
Three cheers to that, David

/slash/

bump.


anybody?

---

### Post by Therion on 2009-03-06
[quote="The Article" (Linked to Above)]

You keep thinking, “I wish I could just reset it back to its defaults, like a clean install, without losing all my applications and data.”

Well, you’re in luck. ...[/quote]
:shock:  Wow.

---

