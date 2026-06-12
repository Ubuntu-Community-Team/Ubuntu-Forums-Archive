---
title: "Enable root login from login manager."
date: 2005-07-13
forum: Desktop Environments
---

### Post by E-Buzz on 2005-07-13
As you all might know by now, Kubuntu comes with disabled root account and root login at the login screen forbidden. I've enabled the root account and now i would like to enable root login from the login screen. Cant find any way to do that, can someone be of help?

---

### Post by Xian on 2005-07-13
If this was enabled it would be a very bad system management idea.
You are also negating the clear advantage that Linux has -- security.

What are you needing to login as root for?
Is there something you can't accomplish as su within your user session?

---

### Post by E-Buzz on 2005-07-13
[QUOTE=Xian]If this was enabled it would be a very bad system management idea.
You are also negating the clear advantage that Linux has -- security.

What are you needing to login as root for?
Is there something you can't accomplish as su within your user session?[/QUOTE]

The security is not an issue here, the machine is in a closed environment and got no internet connection at the moment. And yes, i have, from time to time, the need to login from start as root. 

As far as i know its more common amongst the different linux dists ( i have tested at least six different ones the last month) that root account is enabled instead of the other way around. I can very well see the advantages with having it disabled by default, but for some users (like me) it is annoying not to have the option to use root account when i want it.

---

### Post by elsewhere on 2005-07-13
Rather than running as root, why not use su ?  More convenient than sudo, less risky than logging in as root.  Even in a closed environment, system files and settings can still be inadvertently deleted or modified...

However, if you really want to log in as root for your desktop, just change "AllowRootLogin=false" to true in /etc/kde3/kdm/kdmrc.

Hope this helps...

Cheers,
KV

---

### Post by Xian on 2005-07-13
[QUOTE=E-Buzz]The security is not an issue here, the machine is in a closed environment and got no internet connection at the moment. And yes, i have, from time to time, the need to login from start as root.[/QUOTE]
It is still very much a bad system management idea.
This would include security and a host of other potential ills.

What can you not do as su in a user session that would require a root login?

---

### Post by Terracotta on 2005-07-14
"It is still very much a bad system management idea.
This would include security and a host of other potential ills.

What can you not do as su in a user session that would require a root login?"

What's with the we-don't-think-it's-good-so-we-wont-tell-you attitude??? if you know the answer you can warn perhaps that you shouldn't do it, and name the reason's why, but why are SOME guys, MOST AREN'T, so eager to force someone on doing thing's the way they prefer it, and not giving other's the choice to choose if they want to do it otherwise, if you don't know the answer the least you can do when you give comment on someone's way of working is tell that you don't know the answer, before giving replies like "why would you do that"?? I myself prefer su, and I don't know the answer, otherwise I'd tell you, but I've been looking for a way to do this myself, since sometimes I really need to do a lot of work as root, and then it's really much easier to go to a root acount.
Sorry if I sound a bit harsh, and if it sounds like a flame, it isn't ment as one, it's just that this isn't the first time I've seen these kind of replies without any other valuable information on the matter. If someone knows what he's doing, or if someone wants to learn how to screw up his computer, let him do so, a great way to learn how linux  works.
Greetz,

---

### Post by skyboy on 2005-07-14
or a simple : sudo xterm  //is a good trick too

---

### Post by centremco on 2005-07-19
You can also end your current session, choose to do a console login. X is stopped and you get a console. with su you become logged in as root. then start x and you are logged in as root.
The funny thing then is, all the font settings are different...

---

### Post by Lord Illidan on 2005-07-19
Be careful..that is all we are saying...do something wrong, and you might have destroyed your distro..
sudo + su work perfectly..

---

### Post by rezonatix3 on 2005-07-19
The supposed benefits of disabling the *root* account are listed at the wikipage [RootSudo](https://wiki.ubuntu.com/RootSudo):

> [list][*]Initially the Ubuntu team wanted the easiest install possible. By not enabling root, a couple of steps requiring user interaction during install could be avoided. (Colin Watson) 
[*]Even more significantly, if root were enabled during install, the user would be required to forever remember the password they chose--even though they would rarely use it. Root passwords are often forgotten by users who are new to the Unix security model. (Matt Zimmerman) 
[*]It avoids the "I can do anything" interactive login by default--you will be prompted for a password before major changes can happen, which should make you think about the consequences of what you are doing. If you were logged in as root, you could just delete some of those "useless folders" and not realize you were in the wrong directory until it's too late. It's been good Unix practice for a long time to "su-command-^D" regularly instead of staying in a root shell--unless you're doing serious system maintenance (at which point you can still "sudo su"). (Jim Cheetham and Andrew Sobala) 
[*]Sudo adds a log entry of the command(s) run (In /var/log/auth.log). If you mess up, you can always go back and see what commands were run. (Andrew Zbikowski) 
[*]Every cracker trying to brute-force their way into your box will know it has an account named "root" and will try that first. What they don't know is what the usernames of your other users are. 
[*]Allows easy transfer for admin rights, in a short term or long term period, by added and removing users from groups, while not compromising the root account. (Stuart Bishop)[/list] The same page also states that you can enable *root* with the following command:

> [FONT=Courier New]sudo passwd root[/FONT] Eventually disabling it with

> [FONT=Courier New]sudo passwd -l root[/FONT] should you feel convinced that the [FONT=Courier New]sudo[/FONT] approach is safer.

**Edit:** Since you're a Kubuntu user, you also need to follow [elsewhere's instructions](http://ubuntuforums.org/showthread.php?p=253475#post253475) earlier in this thread:

[QUOTE=elsewhere]However, if you really want to log in as root for your desktop, just change "AllowRootLogin=false" to true in /etc/kde3/kdm/kdmrc.[/QUOTE] **Edit 2:** Okay, this post is somewhat superfluous since you say you've already activated the *root* account. But perhaps it can be of use to other users searching this forum for information about the same topic?

---

### Post by Altmenorg on 2005-07-19
I also disapprove this idea....
A standard usage doesn't require to be root.
Just imagin that beeing administrator by default is responsible of at least 90% of the security problems on MS Windows....

Well, root login is not allowed by default with KDE, but I assume that if you add your user to the root group, it may work (even though I never tried that, note this ;))

Just open prompt and type the following :
sudo vim /etc/passwd

You should find a line like this :
youruserlogin:x:1000:1000:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Just replace by this :
youruserlogin:x:1000:0:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

---

