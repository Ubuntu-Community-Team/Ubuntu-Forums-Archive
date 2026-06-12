---
title: "Desktop Launcher query"
date: 2005-11-03
forum: Desktop Environments
---

### Post by GrumpyBob on 2005-11-03
I've installed the mindmap application Freemind - this uses Java.  I can run this from the command line simply by typing "freemind".  However, when I try making a desktop or takbar launcher for it using this command, the launcher doesn't work.

I don't really understand why this would be the case - where would I look to find error messages?

Robert

---

### Post by manicka on 2005-11-03
run the command in a terminal and see what error messages appear there

---

### Post by GrumpyBob on 2005-11-03
Except the app launches fine in a terminal (there are a variety of Java related things that appear as it launches)!  Just doesn't work from a launcher.  If I tell the launcher to run in terminal, a terminal window opens, then closes.

Robert

---

### Post by manicka on 2005-11-03
Ok, you 've aroused my curiosity. I installed freemind and am able to make a  launcher successfully. 

What steps are you using to make the launcher?

---

### Post by manicka on 2005-11-03
I right clicked on the panel. Chose 'Add to Panel'-->custom application launcher and added as per the screenshot.

[IMG]http://img301.imageshack.us/img301/2572/screenshotlauncherproperties7y.png[/IMG]

---

### Post by GrumpyBob on 2005-11-03
I just made a launcher in exactly that way - it doesn't work!  There must be a log to look at somewhere to find out why.

Note added in edit:  There's nothing intrinsically wrong with my deaktop launchers - for example, I can make one for Evolution that works just fine!

Robert

---

### Post by niko_ on 2005-11-03
GrumpyBob try using the full path in the command (eg.: /usr/bin/freemind)

---

### Post by GrumpyBob on 2005-11-03
[QUOTE=niko_]GrumpyBob try using the full path in the command (eg.: /usr/bin/freemind)[/QUOTE]

No different.

Is there a way I can make it write a log of error messages to a file?

Robert

---

### Post by GrumpyBob on 2005-12-28
This week I've had to rebuild my Ubuntu installation after the Ubuntu partition took an un-fsck-able nose-dive.  Now I find that my freemind shortcuts work.  This I do not pretend to understand!

Robert

---

### Post by anil_robo on 2005-12-28
You could report this as a bug at bugzilla.

---

### Post by sup on 2006-01-17
I have got the same problem with Movietheque ([http://movietheque.sourceforge.net/]("http://movietheque.sourceforge.net/") and oslo with Google Earth (I read this thread [http://www.ubuntuforums.org/showthread.php?t=103618&highlight=launcher]("http://www.ubuntuforums.org/showthread.php?t=103618&highlight=launcher")), i have no idea what is going on for launcher for Qemu (also made up by me) works allright. I might try bugzilla then.
I also messed with my partitions, but it was some time ago and everything has been working fine since.

---

### Post by sup on 2006-01-27
I solved it - I created a bash script (something like ```
#!/bin/bash
cd /home/tom/Movietheque/
/home/tom/Movietheque/Movietheque.run

``` which I call and everything is working now. The program needs to be called from inside the directory it is in (I do not know if it is something that all java applications have) and this does just that. Hope that helps.

---

### Post by GrumpyBob on 2006-01-28
This is pretty much what I did for my freemind launcher.

Robert

---

