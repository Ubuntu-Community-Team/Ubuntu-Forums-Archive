---
title: "suddenly, I can't log in (screenshot within)"
date: 2005-12-02
forum: Desktop Environments
---

### Post by HarryMangurian on 2005-12-02
I get the error log below.
I also tried failsafe and recovery modes - no difference.
I was able to get on with terminal only.
I recently did an install of about 19 Ubuntu upgrades that automatically popped up as available.
(I am not sure if this is the 1st boot since then I do not think so).

Very disturbing, because I recently decided I did not need Windows anymore.
Now I can't even log in. Even Windoze never did that to me.  HELP !
(I am a newbie to Linux and I need plain English help, not jargon - thanks)

[IMG]http://www.pbase.com/image/53064958.jpg[/IMG]

---

### Post by invalid on 2005-12-02
Use a failsafe terminal session, and do the following:
```
sudo chown youruser ~/.ICEauthority
```

Cb

---

### Post by teaker1s on 2005-12-02
if nobody can suggest a better way boot to recovery mode and use either synaptic or apt-get to install kubuntu-desktop then log in completely remove gnome and any config files in your home folder.
then reinstall gnome-worked for me

---

### Post by HarryMangurian on 2005-12-02
thanks for the rapid response.

> sudo chown youruser ~/.ICEauthority

by "youruser" do you mean **youruser** or my user name.

sorry for what is probably a dumb question.

---

### Post by invalid on 2005-12-02
No worries,

It should be replaced with whatever your username is.

Cheers,
Cb

---

### Post by HarryMangurian on 2005-12-02
I did the chown command and it worked !    Many thanks.
I love support Linux folks give to newbies.

I could guess, but are you willing to take the time to:

- explain what the command did,

and

- give me an idea of how you learned that was the thing to do to fix my problem.

---

### Post by silvagroup on 2005-12-02
I logged in under root and changed the priorities on ICEauthority. Ended session logged backin to user account just fine. Could not get sudo to work at terminal level, kept getting commmand not found for chown.

---

### Post by invalid on 2005-12-02
[QUOTE=HarryMangurian]- explain what the command did[/QUOTE]
Somewhere when you were updating packages, your file ~/.ICEauthority had its owner changed to the root user. You can see who owns a file by: ```
stat filename
```
Since gnome wants to start under your user account, and not root, it needs permission to read the file (which is essential to starting the desktop). Since you changed the owner, using "chown", it now can read with no problems.

[QUOTE=HarryMangurian]- give me an idea of how you learned that was the thing to do to fix my problem.[/QUOTE]
This has been a problem with many people recently, and has been the soultion for nearly all the cases.

Cheers,
Cb

---

