---
title: "gnome sound server gives conflict whit some programs"
date: 2005-04-17
forum: Desktop Environments
---

### Post by walterBE on 2005-04-17
Hi,

This is my problem;
By default gnome makes sounds when there are system events. Warnings, clicking on buttons and so.

When this is on I can not use audacity, it gives a error that it has a i/o problem, host not found. Also Tuxracer, tuxkart, dosbox and so do not have sound.

I can switch it off and then it works.  But then i do not get a sound signal when there is a new e-mail or a jabber-contact from gaim.

Suggestions how i can resolve this conflict?

---

### Post by cwaldbieser on 2005-04-17
I do not use any of the specific programs you mentioned, but sometimes you can configure them to use specific sound systems.  I had similar problems with a couple of games I like to play.  When I ran esd, I could get system sounds, but no game sounds.  When I killed esd, I wasn't getting my system sounds.

I found that some of my games used common libraries like SDL or OpenAL, that could be configured via .rc files in my home directory.  I set them to use the same sound system as my system sounds, and everything worked great.

For programs like xmms or xine, you can actually tell the program what sound system / engine to use from the GUI, though I often had to restart the app.

Someone who knows more about the individual programs might be able to help you more.  I am guessing that you are using esound for system sounds, as that is what seems to come with Hoary by default, but if you are using something different for your system sounds, you might want to provide that information.

---

### Post by nix4me on 2005-04-17
Look in the Howto section.  There is a post in there about it.

Nix4me

---

