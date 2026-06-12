---
title: "xsession &amp; blackbox"
date: 2006-01-29
forum: Desktop Environments
---

### Post by william_nbg on 2006-01-29
I'm trying to get blackbox set up on a computer running Ubuntu. Blackbox is set up and running well, but I need several app to start up when logging in from the GDM:

such as Docker, and bbkeys

I've tried creating files in the $HOME directory:

.xsession   or .xinitrc  with permissions set at 755 to run scripts like:

if [ $DESKTOP_SESSION == 'blackbox' ]; then
docker&
fi

But nothing I've tried has born any fruit, any suggestions would be great.

---

### Post by bluevoodoo1 on 2006-02-02
I've had some trouble with this as well. But I have somewhat of a work around. 

If, when you get to the GDM you choose "gnome failsafe terminal" (I think that's the correct name) and type your .Xsession file you created it will load Blackbox with the startup programs you desire. Then, the next time you log out, be sure to sign in with "last." GDM will ask if you want to use your "failsafe gnome terminal" session as default, say yes. If you login to another window manager you will have to do the process again. here's my .Xsession file I use for the following to load upon startup..

```

#!/bin/sh

gnome-settings-daemon &
wmclock -12 -led white &
wmweather -w -s KROC &
wmcpuload &
wmbutton &
conky &
exec blackbox

```

you could always just make those items turn on, by putting a command for each of them in the menu... OR a script like above in your menu so that, yes you have to click it, but it will activate what you want with only a few clicks (I've seen a HOW-TO about that somewhere on the net). 

I like Blackbox because the startup is so fast, so I don't really do the startup script stuff, I'd rather just turn things on as I need them. 

it isn't the greatest, but it worked for me... hope that helped somewhat...

---

### Post by bluevoodoo1 on 2006-02-02
[http://ubuntuforums.org/showthread.php?t=18626&highlight=blackbox](http://ubuntuforums.org/showthread.php?t=18626&highlight=blackbox)

Talks about adding a startup script to the menu.

---

### Post by william_nbg on 2006-02-02
Ha ha!!

I already did that - put the apps in my menu.

I thought I was the only one was such cheap work-arounds.

Though, you are right - why start 'em if you might not need them everytime??

---

### Post by william_nbg on 2006-02-02
I know it's a noob question, but what wil the gnome-settings-daemon get me??

---

### Post by bluevoodoo1 on 2006-02-02
[QUOTE=william_nbg]I know it's a noob question, but what wil the gnome-settings-daemon get me??[/QUOTE]


You'll get your gnome theme (so if you open nautilus you get the theme and icons.... you'll get your firefox theme too [no metacity on either]) and it's good if you have a multimedia keyboard. For me, I can control volume from my keyboard rather than a slider on xmms or xine or another player, gnome-settings-daemon lets me do that. And your screensaver. Other than that, probably some other gnome-related things. The first two I mentioned are the reason why I use it.

---

### Post by william_nbg on 2006-02-03
Thanks.

I realized that, regarding the gnome themes last night after trying it. And now, thanks to you, I realize it regarding the multi-media keys.

Another question if you have a second:

How does conkey compare to gkrellm??

---

### Post by bluevoodoo1 on 2006-02-03
[QUOTE=william_nbg]How does conkey compare to gkrellm??[/QUOTE]

I haven't used gkrellm. I'm not fond of its looks. But it seems that it is more like some sort of 'dock' that can be added upon with other applications found in the repositories. (Search Synaptic for gkrellm and see how many matches it finds). It is similiar to the "wm" applications like wmcpuload, wmweather, wmxmms, wmbuttons etc. that are indvidual programs that sit in the slit. 

I like conky because of simplicity, looks, the fact that it seems to be part of the desktop, and the text output. You have to add the variables by hand. They can be found here...
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

Why not experiment with both??

Here's a screenshot with conky.

---

