---
title: "There was an error loading the theme... HELP"
date: 2006-01-01
forum: Desktop Environments
---

### Post by Ellias on 2006-01-01
Hello,

I thought it might be nice to install a new login theme on my ubuntu box. So I grabbed one (particularly this one... [http://art.gnome.org/themes/gdm_greeter/1036](http://art.gnome.org/themes/gdm_greeter/1036) )

I extracted the theme to /usr/share/gdm/themes/ where all the other themes are and installed it. Everything went fine, so then I logged off and was presented with this message...

Cannot open file /usr/share/gdm/themes/cleanlinux/cleanlinux.xml

I click 'ok'

Then it presents me with a prompt saying 'There was an error loading the theme, and the default theme could not be loaded. Attemplting to start the standard greeter.'

I click 'ok' again

Then it loads the standard greeter and low and behold I can't even type my username in the field. For some reason it just wont let you. 

"What have I gotten myself into" I think to myself.

So I hit CRL + ALT + F5 and drop into terminal view then 'su' and then vi /etc/gdm/gdm.conf.

I go all the way down to line 386 and change the GraphicalTheme variable from 'cleanlinux' (theme installed) to 'happygnome' (the one I last used).

I save and reboot and now I get the *same* message for happygnome! and happygnome used to work (before I tried another theme)!

I found a temporary fix for this by going into the gdm.conf file and enabled automatic login to true (line 23) and setting my username (line 24).

By doing this I was able to bypass the login screen and then I tried some of the other login themes that used to work. No dice, I get the same message with every single one stating...

Cannot open file /usr/share/gdm/themes/'themename'/'themename'.xml

Does anyone know how I can get my logon screens to work again? All I did this morning is install that theme and now, not only does that one not work, but now none of them do!?

Any help is greatly appreciated.

---

### Post by kaamos on 2006-01-01
Drop to the terminal, log in and start gnome with the commands
```
sudo /etc/init.d/gdm stop
startx
```
Now you can then open a terminal and use the command
```
sudo gdmsetup
```
to choose themes. Hope this helps!

---

### Post by Ellias on 2006-01-01
Hey kaamos, thanks for the reply. Unfortunately I can only get as far as typing gdmsetup.

Once I do I get...
(gdmsetup:8012): Gtk-WARNING **: cannot open display

However, I don't think this is causeing the main issue here mainly because I tried this exact same thing on my laptop that has Ubuntu 5.10 installed (where the logon screen works) and I get the same error message.

I'm still at a loss as to what the problem is here. All I did literally was install a new theme and then they all stopped working :( 

*sigh

---

### Post by kaamos on 2006-01-01
Did "startx" get you a graphical desktop? The "gdmsetup" is meant to be run inside gnome. And it is the same thing as choosing syste-administration-login setup or something like that (translated from finnish) in the panel.

If changing the theme does not work, you could remove (with config) gdm with synaptic, then reinstall it and hope that everything works again.

---

### Post by Ellias on 2006-01-01
I've been able to get a graphical desktop by simply going into the gdm.conf file and enabling automatic login to true (line 23) and setting my username (line 24).

That bypasses the login screen, the trouble is, I want my login screen to work like it used to, before I tried this new theme.

EDIT: Just tried reinstalling gdm as you said and still no dice. I even installed some other themes in the package manger but I get the same error. :(

---

### Post by Ellias on 2006-01-01
Hehe,

Good news: I figured it out

Bad news: I'm a moron.. :p 

The problem was in my installation of this new theme I was messing around with the permissions of the theme folder (dont ask)... Needless to say those permissions prevented the gdm from accessing the theme folder and anythinh in it. Once I set the permissions back to thier defaults, everything now works swimmingly. 

Oh well, at least I can say I learned a few things about X and gdm. Heh, thanks for the help tho kaamos!

---

