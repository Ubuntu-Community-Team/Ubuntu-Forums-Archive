---
title: "Kill login/pword/premissions bullshit entirely"
date: 2005-05-22
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-22
One thing that frustrates me very much about Ubuntu is that it tries its best to alienate me from computer and hard drive. To do anything or modify any file I need to use the terminal screen just to get permission. In Windows I was able to just set a blank password and never have to deal with that garbage. I don't want to ever have to enter a password or have to go through permissions.

Is there a way to make Ubuntu stop questioning my authority?

---

### Post by angkor on 2005-05-22
:grin:  Yeah, go back to Windows

You could set up an automatic login....maybe even an automatic root login but I've never bothered cause it doesn't make sense.

---

### Post by Alexander Kirillov on 2005-05-22
[QUOTE=Curlydave]One thing that frustrates me very much about Ubuntu is that it tries its best to alienate me from computer and hard drive. To do anything or modify any file I need to use the terminal screen just to get permission. In Windows I was able to just set a blank password and never have to deal with that garbage. I don't want to ever have to enter a password or have to go through permissions.

Is there a way to make Ubuntu stop questioning my authority?[/QUOTE]
 Password is needed to change any system-wide settings (this includes installing apps). To change somethign for just one user, you do not need a root password. 

There is a way to disable this - but you would be  inviting trouble. Liek not licking your door because you do not weant to mess with keys. If your computer is not ever connected to Internet, you can do this.

---

### Post by Curlydave on 2005-05-22
Ohh, so the system is vulnerable to hackers if there's no password? I'll have to look into changing those settings though, as it seems more than a little overboard to have issues modifying local files.

Alright, let me explain the start of the rant. I'm trying to install UT2k4, but when I get to the install step where I select the directory, it pulls the no permission garbage on me again. I just want to avoid these scenarios. How do I let it install the game? What I"m frustrated is that this stuff doesn't contribute to teh OS at all; i'ts just a hinderance and obstruction that serves no use.

---

### Post by hondje on 2005-05-22
[QUOTE=Curlydave]Ohh, so the system is vulnerable to hackers if there's no password? I'll have to look into changing those settings though, as it seems more than a little overboard to have issues modifying local files.[/QUOTE]

I'm surprised, I was just talking a few minutes ago about how bad the default security settings were, especially w.r.t. sudo, and how a simple iptables managing app isn't installed in the base desktop either.  I guess it goes to show that you can't make everyone happy all the time :)

---

### Post by jamie on 2005-05-22
Having no passwords and permissions is a very bad idea. Mainly for two reasons. This first being that if you were to accidentally run any malicious code on your system, it would have full access to do as much damage as it could. Secondly, having permissions and passwords is a good safety measure to prevent user error. This means that it makes it harder to accidentally delete important files such as system files or make damaging modifications to important files.

---

### Post by neighborlee on 2005-05-22
[QUOTE=Curlydave]Ohh, so the system is vulnerable to hackers if there's no password? I'll have to look into changing those settings though, as it seems more than a little overboard to have issues modifying local files.

Alright, let me explain the start of the rant. I'm trying to install UT2k4, but when I get to the install step where I select the directory, it pulls the no permission garbage on me again. I just want to avoid these scenarios. How do I let it install the game? What I"m frustrated is that this stuff doesn't contribute to teh OS at all; i'ts just a hinderance and obstruction that serves no use.[/QUOTE]
-----------------
there is a easy way around that which I do immediately but you can take your pick:

a) sudo chown user.user /usr/local/games
b) install game to /home/user

good luck ( sorry for annoyances but ultimately they do help to protect you from outside threats albeit YES they truly are annoying even for us pros ;=-)

good luck ..if you want private help feel free to PM me anytime ( or if you want to rant Ill listen )

cheers
nl

---

### Post by Takis on 2005-05-23
[QUOTE=angkor]:grin:  Yeah, go back to Windows[/QUOTE]
Not for too much longer. Apparently Longhorn's going to have admin accounts where you still need to enter a password to do higher level tasks. (wow that sounds familiar).

On that note, other "major" improvements to Windows include:
- Previews of your files in their icons (funny, I could have sworn I'd seen this somewhere before too)
- Scalable icons (gasp - sounds like SVG!)
I really should stop here before I really get started.

ERRRUUUGH.
 ](*,)

---

### Post by angkor on 2005-05-23
[QUOTE=Takis]Not for too much longer. Apparently Longhorn's going to have admin accounts where you still need to enter a password to do higher level tasks. (wow that sounds familiar).
[/QUOTE]

woo....I know some people that aren't going to be happy with that... :-)

But I consider it a good thing. Unlike the TS said, permissions and passwords do serve a use. To me it's either buying, installing and updating anti-virus software and firewalls or using hard passwords on my system...I choose the latter. After a while I don't even notice using my password.

---

