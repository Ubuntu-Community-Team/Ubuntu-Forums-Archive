---
title: "sudo applications don't use custom themes"
date: 2005-10-29
forum: Desktop Environments
---

### Post by jnoreiko on 2005-10-29
I'm started playing around with metacity and gtk themes, and I've put my versions in my personal themes folder.
then I noticed that apps such as synaptic aren't using them, but showing up with ugly buttons and menus.
I'm guessing this is because they are running as root, and my themes are in my personal folder.

But this is a bug, right?
When I change the desktop theme, I expect all windows to follow suit.

---

### Post by aysiu on 2005-10-29
It's not a bug. That's the way it's supposed to operate. If you want, you can copy your appropriate config files to the /root folder, but you could probably also run the theme manager as gksudo and change the themes that way.

---

### Post by jnoreiko on 2005-10-29
the theme manager shows a flat list of themes, both from /usr/share and my own themes. There's no mention there that some of the listed themes won't affect all windows.
I call that a bug :)
what's the reason for it working the way it does?

---

### Post by aysiu on 2005-10-29
[QUOTE=jnoreiko]the theme manager shows a flat list of themes, both from /usr/share and my own themes. There's no mention there that some of the listed themes won't affect all windows.
I call that a bug :)[/quote] A bug is something that's supposed to work one way but works another way. It's not the omission of explicit directions for people who need everything mapped out explicitly. For example, there's nothing that says email accounts you set up won't be set up for other users, but that is actually the case as well.

> what's the reason for it working the way it does? Linux, from its very inception, was always designed to be a multi-user environment. One of those users, though discouraged from actual regular use, is root (which Ubuntu accesses via the *sudo* command). Root, like other users, has its own preferences, including themes. If I change my theme from Human to Glossy-P, why should that change to Glossy-P for my wife? Maybe she wants a different them on her Ubuntu login? So Ubuntu (and Linux in general) is made to have different preferences for different users (you'll find this to be true for Mac and Windows as well), including root.

I'd say, actually, that if root just took the preferences of the first user created for the computer, *that* would be the bug. (Why not take the preferences of the second user? Or the third?)

---

### Post by eeGhoong0ais on 2005-10-29
[QUOTE=aysiu]It's not a bug. That's the way it's supposed to operate.[/QUOTE]

Of course it's a bug. If you're familiar with the way GNU/Linux works, it's obvious why it happens, but that doesn't alter the fact that when someone changes their desktop theme, they are going to expect consistency.

---

### Post by jnoreiko on 2005-10-29
Exactly.

At the very least, the Themes manager panel needs to warn the user that certain themes won't apply to root apps.

But beyond that, why should I have to muck with moving files to root-owned folders to customize my desktop?
If I copy files to /usr/share or the /root folder, then they won't be there next time I reinstall, and I lose some of the benefits of keeping /home on another partition.
And running the theme manager with gksudo is just silly.

---

### Post by psychicdragon on 2005-10-29
The only real solution would be to require root access to install a theme. Which is obviously a bad idea because not everybody is an administrator. If you want to install extra themes that aren't in the repositories, it's actually really easy to do:

```
sudo tar zxf theme.tar.gz -C /usr/share/themes
``` or
```
sudo tar jxf theme.tar.bz2 -C /usr/share/themes
```
Then select it with the theme manager.

---

### Post by gillion on 2005-10-29
I am sorry but this is not a bug. It is the same across all Linux distros, FreeBSD and OS X.

---

### Post by gillion on 2005-10-29
I am sorry but this is not a bug. It is the same across all Linux distros, FreeBSD and OS X.

---

### Post by jnoreiko on 2005-10-29
[QUOTE=psychicdragon]If you want to install extra themes that aren't in the repositories, it's actually really easy to do.[/QUOTE]

So basically, the existence of the user theme folder ~/.themes is pointless, since themes placed there don't work properly.

---

### Post by Wolki on 2005-10-29
> **jnoreiko]At the very least, the Themes manager panel needs to warn the user that certain themes won't apply to root apps.[/quote]

Difficult question. Should it also warn that other people's themes won't be affected?

On the other hand, there are more (and probably more important) things that get changed if start apps sudo'd. For example, my nautilus is spatial and single-click said:**
> 
But beyond that, why should I have to muck with moving files to root-owned folders to customize my desktop?

The idea is clear, and it's one that makes sense. But the implications are many :-/

Sudo is switching users, but it does not really feel like that to the user. (unless he's used to it, of course). I guess that's where the confusion comes from.

But wouldn't it be good to have applications with root powers visually different from the rest of the desktop? They are fundamentally different in what they can do, and this would maybe make that clearer to the user.

---

### Post by jnoreiko on 2005-10-29
[QUOTE=Wolki]Sudo is switching users, but it does not really feel like that to the user. (unless he's used to it, of course). I guess that's where the confusion comes from.[/QUOTE]

Sort of, but no.


My point is that when I pick a theme that's installed with the distro, Synaptic & other sudo apps are changed.
Open a regular terminal and a root terminal.
Now open the Themes preference app and pick 'Crux' or 'Clearlooks',
*BOTH* terminal windows change.
The intention is obviously that I have control over all windows, including those I'm running as root.
If the root terminal NEVER took the theme I chose, this would perhaps be ok. It's a bug because of the lack of consistency.




[QUOTE=Wolki]

But wouldn't it be good to have applications with root powers visually different from the rest of the desktop? They are fundamentally different in what they can do, and this would maybe make that clearer to the user.[/QUOTE]



That's true as well.

It's easy to confuse a root terminal with a regular one, for example.

---

### Post by eeGhoong0ais on 2005-10-29
[QUOTE=Wolki]But wouldn't it be good to have applications with root powers visually different from the rest of the desktop? They are fundamentally different in what they can do, and this would maybe make that clearer to the user.[/QUOTE]

Definitely, but changing the theme isn't the way to do it - it just feels wrong. A differently coloured titlebar [maybe with black & yellow warning stripes] is the first thing that comes to mind.

Gillion suggests that it isn't a bug because other distros do it. I don't think that argument holds water; if every distro came with a browser that had a serious memory leak, for example, that would still be a bug.

---

### Post by Wolki on 2005-10-29
> **jnoreiko]Sort of, but no.
My point is that when I pick a theme that's installed with the distro, Synaptic & other sudo apps are changed.[/quote]

Oh, interesting. Didn't know that. You learn something new every day... ^^ said:**
> Definitely, but changing the theme isn't the way to do it - it just feels wrong. A differently coloured titlebar [maybe with black & yellow warning stripes] is the first thing that comes to mind.

Hm, a different theme might be a good idea too, but it should be a more distinctive one. A different titlebar might be enough, would have to be tested.

---

### Post by jnoreiko on 2005-10-29
[QUOTE=Wolki]Hm... problem is probably that root might not be allowed to read user-installed themes, and that could break stuff? Not sure. Maybe i should look into that...[/QUOTE]

I'm happy to file a bug report with gnome, but I don't know which component this falls under.

(I thought root was allowed to do everything?)

EDIT: I have no idea of the internals of this, but I have a hunch of what the problem might be: with a user-owned theme, the preference is probably stored as an abstract path from {HOME}. And the theme doesn't exist in root's {HOME}, so it falls back to something else.

---

### Post by Wolki on 2005-10-29
[QUOTE=jnoreiko]I'm happy to file a bug report with gnome, but I don't know which component this falls under.

(I thought root was allowed to do everything?)[/QUOTE]

Hm, you're right... looks like root automatically grants itself the right if it doesn't have them.

Not sure which component this falls under, either.
I've played a bit with gconf.. while you can set a theme for root, it seems to always take the one the current user has, if it's a standard theme. This is only the case for some settings. Wonder how this exactly works... It might have something to do with the problem.

---

### Post by clearnitesky on 2005-10-29
> **Etiol]Gillion suggests that it isn't a bug because other distros do it. I don't think that argument holds water said:**
> 

Look mate, I'm really sorry, but **IT IS NOT A BUG** If a few programs like Synaptic don't use your themes get over it. If you want constant theming throughout then use KDE.

You've had a really good explanation of this in the reply you had from Aysiu. Now it seems to me that you didn't read it properly, so I've quoted it below for you to read again. 

[QUOTE=aysiu] Linux, from its very inception, was always designed to be a multi-user environment. One of those users, though discouraged from actual regular use, is root (which Ubuntu accesses via the *sudo* command). Root, like other users, has its own preferences, including themes. If I change my theme from Human to Glossy-P, why should that change to Glossy-P for my wife? Maybe she wants a different them on her Ubuntu login? So Ubuntu (and Linux in general) is made to have different preferences for different users (you'll find this to be true for Mac and Windows as well), including root.

I'd say, actually, that if root just took the preferences of the first user created for the computer, *that* would be the bug. (Why not take the preferences of the second user? Or the third?)

---

### Post by jnoreiko on 2005-10-29
clearnitesky, comment #12 explains why this is a bug.

---

### Post by clearnitesky on 2005-10-29
no, because by the sound of things you're confusing the window manager themes with the gtk themes.
There's nothing *inside* of a terminal to theme...

By editing the theme from Crux to Clearlooks then all the window decorations will change because it's the logged in user that controls these decorations. It is the user that ran the program however that controls what is inside the window.

---

### Post by jnoreiko on 2005-10-29
[QUOTE=clearnitesky]no, because by the sound of things you're confusing the window manager themes with the gtk themes.
There's nothing *inside* of a terminal to theme...[/QUOTE]

Terminal has a window border, and a menu. Its dialog boxes (eg preferences) have controls. These are all themed.
And anyway, my example applies to Synaptic too. 
Try it before you complain, please.

By "theme" I mean the thing you choose in Preferences -> Theme.

---

### Post by clearnitesky on 2005-10-29
mate, the window manager is being run by you, so therefore if you change your theme then the window borders will change. Synaptic is being run by root but it is being hosted by your window manager, hense the borders are yours but the content is not

---

### Post by clearnitesky on 2005-10-29
If you go to the program you have indicated to me and click on "Theme Details" you will see that you have multiple tabs for window boarders and controls. window borders is your metacity theme and controls is your gtk theme.

---

### Post by psychicdragon on 2005-10-29
This thread has gotten out of hand.

Please, file a bug report and be done with it. Then we'll see whether the devs see it as a bug or a feature.

---

### Post by clearnitesky on 2005-10-29
[QUOTE=psychicdragon]This thread has gotten out of hand.

Please, file a bug report and be done with it. Then we'll see whether the devs see it as a bug or a feature.[/QUOTE]

There's nothing to report, the problem is that this guy doesn't understand what theming actually does and he wont take any notice of people **trying to help**.

As long as you are using gnome as a normal user then gnome-terminal will use your theme. If you change your gtk theme then with will not have any effect on a program you run via sudo. 

I suggest to any moderators that this thread be closed. 
Needless to say I am not going to waste any more of my time on it.

---

### Post by jnoreiko on 2005-10-29
clearnitesky, I have Synaptic in front of me now.
It has a border, styled by metacity's theme, and a menu & toolbar, styled by gtk theme. (I think I understand the different parts to a theme)

I also have the Theme panel, run as myself.
I'm picking different themes in it (the ones installed by ubuntu).

ALL of synaptic changes to match. The border, AND the controls (the scroll bars, the buttons, the menu text)

Root apps are changing to reflect my personal user settings.

---

### Post by aysiu on 2005-10-29
I'm closing this thread. There's no point in arguing about it. If you really think it's a bug, file a bug report--let the developers decide whether they intended for this to happen or not. Otherwise, it doesn't really matter what theoretically we consider the "proper" behavior for themes here.

**Edit**: Temporarily reopening the thread in the hopes it'll be productive. If it ends up being a silly debate again, I'll shut it down again. The way I see it, there are two options:

1. Legitimate bug--file the bug report
2. Illegitimate "bug"--live with it

---

### Post by NewbieNik on 2005-10-29
[QUOTE=Etiol]Of course it's a bug. If you're familiar with the way GNU/Linux works, it's obvious why it happens, but that doesn't alter the fact that when someone changes their desktop theme, they are going to expect consistency.[/QUOTE]


Unless you're a root in corporate enviroment, in which case you'd be a bit narked at a user changing your settings!!!

Each to their own!

---

### Post by Wolki on 2005-10-29
[QUOTE=NewbieNik]Unless you're a root in corporate enviroment, in which case you'd be a bit narked at a user changing your settings!!!

Each to their own![/QUOTE]


Look, people.... lets start fresh.

This is not about users changing root settings. This is about ubuntu using user settings for root, and that it works in some cases, and not in others.

I thought like most of you, but then I actually looked at what happened. And I saw jnoreiko was right.

Just try it. Change your theme for root (with "sudo <name of the theme manager>", sorry i'm not at home right now), then start a sudoed application like nautilus. Then see what theme it has. Change the theme for your user. Look at the theme of the sudoed nautilus. Then change your user theme to one you downloaded. Look at that nautilus again. You'll see what jnoreiko means. If you want to, you can do it even with gconf-editor, it has the same effect.

The issue at hand is *not* that a user has to set a theme for root manually. The behavior has changed since Hoary, and the problem is a little more complicated.

---

### Post by manicka on 2005-10-29
The solution is fairly simple as has already been explained by aysiu. I usually copy all installed themes to /usr/share/themes and /usr/share/icons. Then when I play around with the different metacity/gtk2/font themes the changes are consistent in synaptic and any other program run as root.

To be honest I'm about to run the theme manager as root and change the theme slightly from my default (probably just the icons) so that I know when nautilus or whatever is running as root. The consistent appearance while visually pleasing, can be confusing when working with different apps and different user/root windows open.

---

### Post by Kevin on 2005-11-06
I agree that this behaviour is inconsistent and confusing for new users.

When I install a theme with Synaptic, it gets installed for all users, it does not get *applied* for all users though.  This however requires root access to install a theme, which should not be required.

The way I see it, the way most new users would install a theme, is to download a tar.gz, and install it using the theme manager, which places it in ~/.themes and ~/.icons.  When running a program as root, it does not look in these directories, since it obviously has a different home directory.  When it can't find these, it defaults to something horrible looking, which is unnacceptable in my opinion.

I see two solutions.  The first, which I do not like, would be to ask the user, when it installs a theme from theme-manager, if they would like to install the theme for root as well, and then ask for a root password.  This could either install the theme in /usr/share/themes, or both in the user directory and /root/.themes.  The solution that I feel would be cleaner, would be to somehow have the root account check the current user's ~/.themes and ~/.icons directory for the current theme.  This way, it does not affect the root account, and it is transparent to the user, as it should be.

Also, there has been some discussion about the fact that root applications should be distinguished from other apps.  I agree with this, however making them look like this (attachment at the bottom is after I changed my theme to clearlooks-quicksilver, and icons to Dropline-Nuovo) is not the right direction.

The fact is, when I change my theme, it also changes the theme for root.  This means that the root theme is supposed to change, and it does, but not to the right theme.  This behaviour, to me, constitutes a bug.

---

### Post by Wolki on 2005-11-06
[QUOTE=Kevin] The solution that I feel would be cleaner, would be to somehow have the root account check the current user's ~/.themes and ~/.icons directory for the current theme.  This way, it does not affect the root account, and it is transparent to the user, as it should be.[/quote]

Exactly. since we have some magic already taking the theme settings from the user's gconf, this shouldn't be that hard, I hope.

> Also, there has been some discussion about the fact that root applications should be distinguished from other apps.  I agree with this, however making them look like this (attachment at the bottom is after I changed my theme to clearlooks-quicksilver, and icons to Dropline-Nuovo) is not the right direction.


Of course, that's not what I meant. If such a thing is done, it should be a specific theme designed for applications that run as root, and apply even if the user has a standard theme. While trying out some things for this thread, i had to have a normal user and a root gconf-editor open, and it was terribly confusing after a short time.

jnoreiko, have you filed this?

---

### Post by openmind on 2005-11-06
[quote=manicka]............................................................................

To be honest I'm about to run the theme manager as root and change the theme slightly from my default (probably just the icons) so that I know when nautilus or whatever is running as root. The consistent appearance while visually pleasing, can be confusing when working with different apps and different user/root windows open.[/quote]

Exactly! The drastically different theme serves to remind me (Constantly) that I'm running as root, and to have my wits about me. (Double check all rm's!!).

---

### Post by jnoreiko on 2005-11-16
[QUOTE=Wolki]jnoreiko, have you filed this?[/QUOTE]

I wanted to be sure to file in the right place, so I did some asking around first...
turns out someone beat me to it :) 
[http://bugzilla.ubuntu.com/show_bug.cgi?id=18135](http://bugzilla.ubuntu.com/show_bug.cgi?id=18135)

(It's marked as an enhancement, but I think it should be a minor bug. Anyone here have the rights to change it?)

---

### Post by Xyhthyx on 2007-05-03
**I know this is an old thread, but a quick bump to post the answer to the OPs situation since I figured out a quick solution as I searched the forums.**

Applications run as root will not use your custom themes (~/.themes and ~/.icons) because they're not in /usr/share. Instead of installing them directly to /usr/share/themes or /usr/share/icons (and keep installing them by using the theme manager) you can do the following:

```
cd /root
sudo ln -s /home/<user_name>/.themes
sudo ln -s /home/<user_name>/.icons
```

* Replace <user_name> with your current user name. Note: These are symbolic links, therefor will only work when the user you put does sudo/gksudo. Other users besides the one you put will see an unthemed app if they use sudo/gksudo.

Now you can keep using the regular theme manager to install themes and icons and any applications run as root will use them too.

---

