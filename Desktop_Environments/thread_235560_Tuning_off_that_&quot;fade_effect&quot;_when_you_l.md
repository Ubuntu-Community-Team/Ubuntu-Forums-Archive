---
title: "Tuning off that &quot;fade effect&quot; when you log out of Ubuntu"
date: 2006-08-13
forum: Desktop Environments
---

### Post by mwob on 2006-08-13
Hi,

Can anyone tell me if it is possible at all to disable that fade effect whenever Ubuntu asks you for the root password and when you log out of the system. Its perfectly nice, but it causes havoc with XGL/Compiz effects...

Thanks!

Matt

---

### Post by xenon2000 on 2006-08-15
I too would love to figure out how to disable the fade effect. I don't need it, seems pointless.... doesn't excite me at all. But right now it's just annoying.

---

### Post by aysiu on 2006-08-15
Add a *-g* to the command.

For example, if the command is ```
gksudo synaptic
``` change it to ```
gksudo -g synaptic
``` instead.

---

### Post by xenon2000 on 2006-08-15
hmmm, when I am in X windows, I don't use command lines for things that need the password. Are you saying that I need to edit the menu file manually to make all those commands include -g ? What a pain.. and what if I install something new and it needs the password, do I have to go manually add -g to the menu file again for that new addition? Seems this kind of thing should be globally controlled somewhere.

Personally, I don't understand why this was even added in the first place. As if I can't see the new window without having the rest of the screen darkened?

---

### Post by orb9220 on 2006-08-15
Ok I right clicked icon for home on my panel and selected properties.

Changed the command from  gksudo nautilus to gksudo -g nautilus and it worked. 

But how do I do that for like the exit button ?

---

### Post by aysiu on 2006-08-15
The command is ```
gnome-session-save --kill
``` but the *-g* parameter has no effect on it.

---

### Post by xenon2000 on 2006-08-15
> **aysiu said:**
> The command is ```
gnome-session-save --kill
``` but the *-g* parameter has no effect on it.

man, sure would be nice to be able to control the fade globally.

---

### Post by trent dillman on 2006-08-15
...

---

### Post by ardchoille on 2006-08-15
> **trent dillman said:**
> try adding an alias to /etc/profile:

```
alias gksudo='gksudo -g'
```

```
sudo -s -H
echo "alias gksudo='gksudo -g'" >> /etc/profile
exit
```

If you figure out the gnome-session-save fade, post it here!

Thank you for the idea of adding the alias :)

---

### Post by trent dillman on 2006-08-15
...

---

### Post by trent dillman on 2006-08-15
...

---

### Post by ardchoille on 2006-08-15
> **trent dillman said:**
> Hey, you may need to set that locally for your user name. It didn't work on my box in /etc/profile :-/

/etc/bash.bashrc is the correct file

Well, I put all aliases in ~/.bash_aliases . it works for me :)

---

### Post by ardchoille on 2006-08-15
> **trent dillman said:**
> Well, the alias approach works when you type 'gksudo yourapphere' from a terminal, but not from the menu...

EDIT: also add an alias for gksu
```
alias gksu='gksu -g'
```

Hmm.. good idea :)

---

### Post by trent dillman on 2006-08-15
...

---

### Post by ardchoille on 2006-08-15
> **trent dillman said:**
> Turns out this works, sort of...

...if I type it in a terminal, it works. Menu doesn't. I'm guessing it's gnome's menu not running things through a shell (at least, not bash)?

Well, I don't use the gnome menus.. I replaced Metacity with openbox as the window manager in gnome (metacity sucks out loud) and I use the desktop menus in openbox. I'll have to edit my openbox menus to add the "-g", but well worth it.

---

### Post by orb9220 on 2006-08-15
Well it appears to only work if you pull the app off the menu and place on the panel.

Which I have firefox,term and a gksudo nautilus which I fixed with the -g option. So if I want synaptic to not do that I guess I need to drag icon to panel and modify from there.

The only other possible way I see right not is to add a drawer to the  panel and drag all my shortcuts to there then modify with the -g option.

---

### Post by aysiu on 2006-08-15
You can edit the menu command--it doesn't have to be on the panel. Just right-click the **Applications** button and select **Edit Menus**.

---

### Post by mannheim on 2006-08-15
Using the "-g" option with gksudo also turns off the feature by which gksudo "grabs" and locks the keyboard and mouse. This feature is there to prevent you accidentally typing in your password into the terminal (or any other program) when you thought you were typing into the password box.

Probably not a big deal for most, but just be aware that if you do something like "gksudo -g synaptic" in a terminal, and if you then type your password, you may type it in the terminal before you know it; and then you may want to expunge it from the bash-history file.

I too would like a simple gconf setting somewhere that turns off just the "dim-and-fade" effect globally.

---

### Post by xenon2000 on 2006-08-15
well, I tried my bash.bashrc file for the alias and it works for terminal gksudo commands... but even after reboot, (alias still works) it doesn't work in my X session. It still dims the surrounding area when the password gui window pops up.

And of course the grid fade effect is still in place when I go to logout and I get the shutdown, logout, suspend, etc window.

Again, the method given so far works for typed commands from an xterm window. But still doesn't work for the regular Xwindow "buttons".

---

### Post by Ramses de Norre on 2006-08-15
There is a far more simple way: ```
gconf-editor /apps/gksu
```
and check "disable-grab".

---

### Post by xenon2000 on 2006-08-15
I am running Xubunbu XFce desktop. there is no gconf-editor  any other ideas?

---

### Post by aysiu on 2006-08-16
> **xenon2000 said:**
> I am running Xubunbu XFce desktop. there is no gconf-editor  any other ideas?
Well, you'll have to do it manually, then.

Paste in these terminal commands: ```
mkdir ~/.gconf/apps/gksu
mousepad ~/.gconf/apps/gksu/%gconf.xml
``` In the new mousepad file, paste this in: ```
<?xml version="1.0"?>
<gconf>
        <entry name="disable-grab" mtime="1155708286" type="bool" value="true">
        </entry>
</gconf>
``` Then save and exit. Should work.

---

### Post by xenon2000 on 2006-08-16
Sorry again, this is the 3rd thread I forgot to cross post to cover all my bases. Here is the link on my comments about -g

[http://ubuntuforums.org/showthread.php?p=1384583#post1384583](http://ubuntuforums.org/showthread.php?p=1384583#post1384583)

my quote:

comment on -g

[http://ubuntuforums.org/showthread.p...74#post1383774](http://ubuntuforums.org/showthread.p...74#post1383774)

Here is one of my posts from the thread above.

-g is --disable-grab

And I thought --disable-grab defeats the security of pausing all applications to prevent possibly grabbing the password as you type or capturing the screen.

If this is so, then -g in unacceptable and the fade effect needs to be controllable by itself as an effect and not just simply disable the event that is tied to the effect.

---

### Post by stvmty on 2006-08-20
Ok, so there is posible to disable the fade effect when prompted for a password. Now, how do we disable the fade effect at logout? That's what I want to know.

---

### Post by xenon2000 on 2006-08-20
> **stvmty said:**
> Ok, so there is posible to disable the fade effect when prompted for a password. Now, how do we disable the fade effect at logout? That's what I want to know.

No, it is not possible to disable the fade effect... only to disable the security function of "grab" which prevents background apps from monitoring the keyboard or display.

I think it is a bad habit to state it as disabling the fade effect as long as it's hard coded. People should understand that -g is disabling a security feature and is not an option flag for removing the fade effect. It only happens that the fade effect is part of the security feature that -g disables.

If disabling this security feature is ok with the user, fine. But people needs to understand what is really going on with -g

I personally will have to wait until the fade effect is separated from the grab function so that the fade can independently be disabled. Thanks.

---

### Post by ChrisNiemy on 2007-02-27
Probably the solution could be quiet easy:

start **gconf-editor**

goto:
> apps > panel > global >
there:
check that the entry "upstream_session" is set true

At nex login and then logout it should work, and the fade effect is gone and a simply message box will appear while logging out.

Hope it works.

---

### Post by xenon2000 on 2007-02-27
> **ChrisNiemy said:**
> Probably the solution could be quiet easy:

start **gconf-editor**

goto:
> apps > panel > global >
there:
check that the entry "upstream_session" is set true

At nex login and then logout it should work, and the fade effect is gone and a simply message box will appear while logging out.

Hope it works.

In Xubuntu there is no gconf-editor, is there a way to do this setting manually?

---

### Post by Jeremy23 on 2007-02-27
mwob, a while ago, [Paul Betts]("http://blog.paulbetts.org/") hacked on [getting gksu working with compositing]("http://blog.paulbetts.org/index.php/2006/12/05/gksu-compositing-bling/").

I have been hacking on that code a bit myself, and am planning to later port it to the GNOME logout dialog. If I ever get around to releasing that, I'll be sure to announce it on my [blog]("http://narnia.bounceme.net/jeremy/") (or [RSS feed]("http://feeds.feedburner.com/JeremyVisser")).

---

### Post by xenon2000 on 2007-02-27
> **Jeremy23 said:**
> mwob, a while ago, [Paul Betts]("http://blog.paulbetts.org/") hacked on [getting gksu working with compositing]("http://blog.paulbetts.org/index.php/2006/12/05/gksu-compositing-bling/").

I have been hacking on that code a bit myself, and am planning to later port it to the GNOME logout dialog. If I ever get around to releasing that, I'll be sure to announce it on my [blog]("http://narnia.bounceme.net/jeremy/") (or [RSS feed]("http://feeds.feedburner.com/JeremyVisser")).

Does your "hack" keep the security of preventing any focus other than the dialog, while still disabling the fade effect? Because that is the real issue here, the fact that even with editing the "upstream" option as just suggested, that it disables the security function that is hard coded with the fade effect.

Does your "hack" offer the same security without the fade effect?

---

### Post by Zelut on 2007-02-27
I used these steps and while it did remove the fade effect I could still access the other programs and menus.  I guess this doesn't include the security of "grabbing" the focus.  I think the thread topic might be a bit misleading, or perhaps not quite specific enough.  From what I understand we're trying to remove the fade, but keep the "grabbing" of input fields at critical points?

---

### Post by xenon2000 on 2007-02-27
> **kuyaedz said:**
> I used these steps and while it did remove the fade effect I could still access the other programs and menus.  I guess this doesn't include the security of "grabbing" the focus.  I think the thread topic might be a bit misleading, or perhaps not quite specific enough.  From what I understand we're trying to remove the fade, but keep the "grabbing" of input fields at critical points?

The subject line is not misleading. Yes, the subject is indeed in diabling the Fade effect. The assumption is that the solution would no including making the OS less secure. Being this is a linux based community, I would think that security would be on the forefront of everyone's mind when thinking of a solution.

Given that so many people keep giving the same solution for disabling the fade effect by disabling the grab function, it is obvious that many people do not understand the security risks involved by doing so. I keep pointing this out so that people who are security aware will not implement these suggestions and instead wait for a real solution for disabling the fade effect that does NOT affect the security of grabbing focus and locking out background input grabbing. 

Sure the subject line could read "Want to disable Fade effect when logging out, but not affect security." But I think that the security aspect is a no brainer for everyone's questions here.

So again, there currently is NO way to disable the fade effect without negatively affecting security with the current versions of Ubuntu and Xubuntu. Hopefully this lame graphical feature will be optional without losing the security function that it's hard coded to.

---

### Post by Jeremy23 on 2007-02-27
> **xenon2000 said:**
> Does your "hack" keep the security of preventing any focus other than the dialog, while still disabling the fade effect? Because that is the real issue here, the fact that even with editing the "upstream" option as just suggested, that it disables the security function that is hard coded with the fade effect.

Does your "hack" offer the same security without the fade effect?
The compositing hack doesn't actually disable the fading. What it does is simply utilise the compositing manager for the transparency, instead of manually manipulating a pixbuf of the screen contents, to make it slicker on a system running Beryl/Compiz (which is what the OP was interested in).

The original version by Paul Betts still had gksu doing the fade itself, but that wasn't as smooth as just setting the opacity and letting Beryl do the fade for it. That's what I modified it to do.

As far as I'm aware, the compositing hack doesn't affect the grabbing of anything (I just tested it by pressing Alt-Tab 'n stuff in a gksu dialog), but I'm not all that sure.

In Breezy or maybe Hoary, I think they didn't have any fading at all, but they still grabbed the keyboard and mouse.

---

### Post by xenon2000 on 2007-02-27
> **Jeremy23 said:**
> The compositing hack doesn't actually disable the fading. What it does is simply utilise the compositing manager for the transparency, instead of manually manipulating a pixbuf of the screen contents, to make it slicker on a system running Beryl/Compiz (which is what the OP was interested in).
....


I hope you can see how the point of disabling the fade is to reduce the eye candy of the desktop and how really the people interested in disabling the fade effect are mostly going to be those that are not using Compiz, etc.

My example is a server... not everyone with a server wants no desktop. I like Gnome and for my 500mhz server, I like Xfce of Xubuntu. Unfortunately the fade effect is directly tied into the security function to prevent other apps from grabbing focus and inadvertantly grabbing passwords, etc.

And the fade effect is really slow on my server and very annoying. Luckily I mostly SSH, but still... it should be optional, while still keeping the security feature in tact.

I am guessing that most of the people searching out a solution are those who's computers are slow during the fade effect. And would assume that if it's fast for others, that those people would not search out a way to disable it because it doesn't bother them.

The point being that such a security function should not have any graphical effects tied to it... or that if they do, they should be optionally without disabling the security part of the feature.

---

### Post by 23meg on 2007-02-27
[QUOTE=xenon2000]man, sure would be nice to be able to control the fade globally.[/QUOTE]

Here's a workaround to turn the effect (as well as the security measure) off globally for all dialogs, including the Quit one:

[http://www.ubuntuforums.org/showthread.php?t=326017](http://www.ubuntuforums.org/showthread.php?t=326017)

---

### Post by ChrisNiemy on 2007-02-28
> **xenon2000 said:**
> In Xubuntu there is no gconf-editor, is there a way to do this setting manually?
Hi, I'm afraid I don't know, because I'm not that familiar with Xubuntu. 

For me I can't reproduce the grab error anymore, because everything (incl Beryl) seems to be working fine with Xorg7.2 and the newest Nvidia-Drivers. I guess that is only an issue when using an extra Xgl Server. Don't know exactly.

Mhm, try to install gconf-editor or start it in Xubuntu. Perhaps it will work, while XFCE is based on GTK like Gnome does.

The easiest workaround seems to be pressing Alt+F2 and entering **gnome-session-save --kill** But another disadvantage is, that when you log in again you will get an open terminal. If you click on gnome-panel and Add..., there is the logout button and a shutdown button. Maybe the grab error doesn't occur when using the shutdown button (but there you will only have the choice between restart and shutdown, no logout or user switching)

---

### Post by ihavenoname on 2007-03-03
is there anyway to do this for kde? (sorry if this has been mentioned before, I haven't got the change to read this whole thread).

---

