---
title: "Trouble with installing gnome-extension-user-theme...."
date: 2012-05-24
forum: Desktop Environments
---

### Post by squiglybob13 on 2012-05-24
First off I'm fairly new to ubuntu. I installed it a couple years ago but was to busy to mess with it so removed it. However I started using it again since a few days ago and started loving it again. So far everything has gone smoothly. A few errors here and there but nothing that couldn't be solved with help from google. However I haven't been able to find a working answer anywhere I've looked. Now my problem.

What I want:
To be able to install shell themes. I figured out to go into the shell extensions in Advanced Settings. However mine's blank so I read that you have to install "gnome-shell-extensions-user-theme", so I tried it...

My problem:

Trying to install the shell extension(s) from repo webupd8team.com/gnome3 gives me and error:
[COLOR="Red"]1st Attachment[/COLOR]

So I figured just install "gnome-shell-extensions-common" too right? Another error:
[COLOR="Red"]2st Attachment[/COLOR]

And this is where I'm lost. I just don't know what to do from here. I looked for broken packages in Synaptic Package Manager but nothing came up.

So basically what I'm asking is what's going wrong and how can I get this to work? Any help at all is appreciated! :)

---

### Post by traditionalist on 2012-05-24
> **squiglybob13 said:**
> First off I'm fairly new to ubuntu. I installed it a couple years ago but was to busy to mess with it so removed it. However I started using it again since a few days ago and started loving it again. So far everything has gone smoothly. A few errors here and there but nothing that couldn't be solved with help from google. However I haven't been able to find a working answer anywhere I've looked. Now my problem.

What I want:
To be able to install shell themes. I figured out to go into the shell extensions in Advanced Settings. However mine's blank so I read that you have to install "gnome-shell-extensions-user-theme", so I tried it...

My problem:

Trying to install the shell extension(s) from repo webupd8team.com/gnome3 gives me and error:
[COLOR=Red]1st Attachment[/COLOR]

So I figured just install "gnome-shell-extensions-common" too right? Another error:
[COLOR=Red]2st Attachment[/COLOR]

And this is where I'm lost. I just don't know what to do from here. I looked for broken packages in Synaptic Package Manager but nothing came up.

So basically what I'm asking is what's going wrong and how can I get this to work? Any help at all is appreciated! :)

The extensions don't work right now.  See here;

[http://ubuntuforums.org/showthread.php?t=1982885](http://ubuntuforums.org/showthread.php?t=1982885)

[http://ubuntuforums.org/showthread.php?t=1912749](http://ubuntuforums.org/showthread.php?t=1912749)

[http://ubuntuforums.org/showthread.php?t=1985378](http://ubuntuforums.org/showthread.php?t=1985378)

---

### Post by Frogs Hair on 2012-05-24
The only thing that comes to mind is to make sure you are using the 3.4 extensions PPA and not 3.2 .

---

### Post by squiglybob13 on 2012-05-24
@traditionalist: aw well that would explain it lol thanks :)

> **Frogs Hair said:**
> The only thing that comes to mind is to make sure you are using the 3.4 extensions PPA and not 3.2 .

How do I check?

---

### Post by squiglybob13 on 2012-05-24
Well I figured it out. I had to set my "style" or whatever to Gnome...I had it on Gnome Classic. Now the shell extensions tab is populated and everything's working :)

However I am curious why it doesn't work in Gnome Classic?

---

### Post by traditionalist on 2012-05-24
> **squiglybob13 said:**
> @traditionalist: aw well that would explain it lol thanks :)



How do I check?

There are a number of ways to check, ( one reason finding things out is often so difficult)

You can look in your update manager; 

[[IMG]http://img819.imageshack.us/img819/5880/workspace1014h.th.png[/IMG]](http://img819.imageshack.us/i/workspace1014h.png/)
[[IMG]http://img832.imageshack.us/img832/8046/updatemanager015.th.png[/IMG]](http://img832.imageshack.us/i/updatemanager015.png/)
[[IMG]http://img411.imageshack.us/img411/3775/softwaresources016fajm.th.png[/IMG]](http://img411.imageshack.us/i/softwaresources016fajm.png/)

Be careful what you do here!

---

### Post by traditionalist on 2012-05-24
> **squiglybob13 said:**
> Well I figured it out. I had to set my "style" or whatever to Gnome...I had it on Gnome Classic. Now the shell extensions tab is populated and everything's working :)

However I am curious why it doesn't work in Gnome Classic?

Gnome is a different shell to Gnome classic. Things that work in one shell wont necessarily work in another.

---

### Post by squiglybob13 on 2012-05-24
Hmmm I kinda understand but I'm still a little confused @_@ lol If I'm gonna continue seriously using ubuntu then maybe I should read up on it a little :P

Anyways thanks for all the help! And the very quick responses! :D

---

