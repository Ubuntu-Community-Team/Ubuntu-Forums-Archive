---
title: "[error login]Will not save configuration."
date: 2006-01-05
forum: General Help
---

### Post by kubuntu32 on 2006-01-05
I have a major problem on my hands.  I was refered to install kubuntu instead of reinstalling redhat fedora core 4 (for the practical reasons) though as simple as the installation proces was I ended up screwing up somewhere because there is an error that is making my head spin.

So here is the problem.
I see the login screen I type in my information and then press enter or the login button... So everything is loading just fine and then BOoOm!  This message pops up:

[COLOR="Navy"]Will not save configuration.

Configuration file
"/home/myname/.kde/share/config/konsolerc"not
writable.

Configuration file
"/home/myname/.kde/share/config/kdeglobals" not
writable.

Please contact your system administrator.[/COLOR]

I press **OK** and then it brings me another error message.

[COLOR="Navy"]Unable to save bookmarks
in /home/myname/.kde/share/apps/konqueror/bookmarks.xml.
Reported error was: Permission denied.  This error mesage
will only be shown once.  The cause of the error needs to be
fixed as quickly as possible.  Which is most likely a full hard
drive.[/COLOR]

I press **OK**.  Then it brings up a terminal (since I just logged in into safemode)

I believe I have 3 hard drives in here. All of them around 8gb which should be more than enough.  My processor speed is 533 and ram is 192mb.  Hardware speaking there shouldn't be a problem.

My theory is that somehow my partitions were configured to be read only.  I don't know exactly how to make them writable.

What can I do?   Has anybody else had this problem before?  (Sorry i'm not a linux or kubuntu expert)


[COLOR="Red"]EDIT:  I forgot to mention that I have scoured both ubuntu and kubuntu forums for an answer and even google was no help.  I know, its amazing isn't it?[/COLOR]

---

### Post by One Quick Question on 2006-01-05
[QUOTE=kubuntu32]My theory is that somehow my partitions were configured to be read only.  I don't know exactly how to make them writable.[/QUOTE]
That sounds like a good theory.  If you have /home on a read-only partition then those error messages make sense.
Post your /etc/fstab file.
Also, this is just a guess, see if *sudo mount -o rw /home* works as a short-term fix.

---

### Post by kubuntu32 on 2006-01-05
Thanks for the swift reply!  I am on the final stage of re-installing everything.  I believe I installed it on the wrong partition rendering it pretty much useless at this point.  Though this might not be the case so I will edit this message if it works or not and if it doesn't then I will post my fstab file.

---

### Post by kubuntu32 on 2006-01-05
It works!!  I installed on the wrong partition I believe.  I see the beautiful desktop and I just want to cry! lol

If reinstalling it didn't work then i might of went crazy.  Hope for the best and lets see if it can eventually replace my other pc (windows xp pro).  See ya later!

---

### Post by bulldogzerofive on 2006-01-06
I have this problem on occaission as well.  It does not require a new install and i imagine you are going to run into it again.  I can't make it happen in a repeatable way though, so i can't really file a bug report (couldn't find one either)...

**I am pretty sure the problem is not that your drive is read only.**  If it were, you never would have gotten so far into the log-in process.  Rather, at times, for some reason, i have noticed that when KDE does not shut down cleanly, or at other times when i have too much open when i shut down KDE, some of the files are left as belonging to root.

**To fix this (short term):**
**1.**  Boot your computer
**2.**  When the login prompt comes up, log in as your "sudo" enabled user (the first one you created) but before you hit return, select "failsafe terminal" as the session type.
**3.**  When the session starts up, cd into the home directory of the user you are having issues with.
**4.**
_a.  Quicker solution:_
      i.  type " **sudo chown -R ***<user_name>***:***<user_name>* ***** ".
      ii.  type " **exit** "
      iii.  attempt to log in to KDE again.

_b.  More involved solution _(if you have files belonging to other users or groups that you want to preserve):
      i.  type " **ls -la | grep root**" or "**ls -la | grep -v ***<user_name>* "
      ii.  All the files in your home directory belonging to root (or in the second case any not belonging to the user) will be listed.
      iii.  Type " **sudo chown -R ***<user_name>***:***<user_name> <instert_name_of_file_in_question>* ".  Repeat this for each file listed in ii.
      iv.  Type "**exit**"
      v.  Attempt to log in to KDE again.

Hope this helps!

---

