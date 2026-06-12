---
title: "help please: odd differences between updated Hoary vs freshly installed Hoary"
date: 2005-04-28
forum: Desktop Environments
---

### Post by darkfox on 2005-04-28
I have 2 desktops:
[1] Home PC, was running Warty until I upgraded to Hoary pre-release
[2] Office PC, running Hoary installed from scratch post-release

I keep both up to date, but strangely I have differences between the 2 systems, such as:
> Synaptic looks and feels different. The upgraded version retains a similar look and feel (black process console etc) to Warty, but the fresh install is more whizzy and integrated into the dektop
> Wallpaper choices are different. Upgraded version has the old browns and calendars up to and including March, but no Blues. Fresh version has Blues but no Browns.
> Subjectively, the fresh install just feels different - more tightly integrated etc (I know this last comment is utterly useless but I can't think of a better way of putting it)

I did the upgrade by following the release notes.  My sources all point to Hoary and I did do a "sudo apt-get dist-upgrade".

I did the fresh install from a CD image downloaded after the official release date.

I would like to know if I have done something wrong, or if in fact there are clear differences between an upgrade to Hoary and a freshly installed Hoary. Can you help me?

---

### Post by accuser on 2005-04-28
Some of the differences will no doubt be based on your system configuration and your own preferences. If you want to compare the two systems, take a look at:
```
$ dpkg-query --list
```
on each system.

---

### Post by darkfox on 2005-04-28
I have compared the package listings already, and could find no differences relating to either Synaptic or wallpaper unfortunately. 

I agree that its far more likely that I've done something wrong than that there are differences betwen an upgraded Hoary and a fresh Hoary, but I just don't know enough stuff to be able to confirm this either way. Any ideas on where these differences could come from?

---

### Post by nocturn on 2005-04-28
Try creating a new user to test.
Does it still feel different?

If not, the cause may be that your old profile is overwriting some of the newer settings in Hoary.

---

### Post by darkfox on 2005-04-28
[QUOTE=nocturn]Try creating a new user to test.
Does it still feel different?

If not, the cause may be that your old profile is overwriting some of the newer settings in Hoary.[/QUOTE]
 Thanks Nocturn - I'll try this when I get home this evening.  Sounds sensible.

---

### Post by denzilla on 2005-04-28
How did you get blue ubuntu walls? I did a fresh install about 4 times now and only have to ugly brown walls to choose from.

---

### Post by darkfox on 2005-04-28
[QUOTE=denzilla]How did you get blue ubuntu walls? I did a fresh install about 4 times now and only have to ugly brown walls to choose from.[/QUOTE]

They come as part of the Ubuntu Calendar package - which offers a changing wallpaper each month (in Gnome). Just select it in Synaptic. Since April the calendar has changed concept from humans on a brown background to become a semi-abstract aquamarine coloured thing.

---

### Post by GTKpower on 2005-04-28
[QUOTE=darkfox]I have 2 desktops:
[1] Home PC, was running Warty until I upgraded to Hoary pre-release
[2] Office PC, running Hoary installed from scratch post-release

I keep both up to date, but strangely I have differences between the 2 systems, such as:
> Synaptic looks and feels different. The upgraded version retains a similar look and feel (black process console etc) to Warty, but the fresh install is more whizzy and integrated into the dektop
> Wallpaper choices are different. Upgraded version has the old browns and calendars up to and including March, but no Blues. Fresh version has Blues but no Browns.
> Subjectively, the fresh install just feels different - more tightly integrated etc (I know this last comment is utterly useless but I can't think of a better way of putting it)

I did the upgrade by following the release notes.  My sources all point to Hoary and I did do a "sudo apt-get dist-upgrade".

I did the fresh install from a CD image downloaded after the official release date.

I would like to know if I have done something wrong, or if in fact there are clear differences between an upgrade to Hoary and a freshly installed Hoary. Can you help me?[/QUOTE]

Sounds like the updated to Hoary gave you a better, faster, tighter desktop environment.  This is normal, and what we all hope for.  There have been newer updates to Hoary since the downloads hit the mirrors.  The point of updates is to improve the user experience.  Seems fine to me.

 . . . . unless I'm misunderstanding something.

---

### Post by darkfox on 2005-04-28
[QUOTE=GTKpower]. . . . unless I'm misunderstanding something.[/QUOTE]

Yers I'm afraid you are misunderstanding something. Both desktops are running Hoary. The difference is that one was a fresh install and the other was an upgrade from Warty. That's whay I started my post with:
[QUOTE=darkfox]I have 2 desktops:
 [1] Home PC, was running Warty until I upgraded to Hoary pre-release
 [2] Office PC, running Hoary installed from scratch post-release"[/QUOTE]
I thought that this was very clear and unambiguous. It obviously wasn't. I apopogise. I do not know how more clearly to state the fact that both machines are running Hoary in terms that you will be able to understand.

---

### Post by Joeb on 2005-04-28
I'm coming late to this discussion, but what did you do about your home directories?  If you created new home directories on the new install and copied back stuff you wanted, versus leaving the home directories intact on the upgrade, then you most likely have different configuration files in the upgraded version vs the clean install.

Some of the leftover items in the upgraded version might include fonts, themes and wallpapers, along with any manual tweaks you might have made.  Also, a lot of times, existing configuration and shell scripts are left untouched in an upgrade vs a new install.  So, even if it's not a home directory issue, your /etc and /usr/bin may have different contents.

I don't know if that is the cause of your problem or not, though.  Just some other places to look.

Joeb

---

### Post by darkfox on 2005-04-28
[QUOTE=nocturn]Try creating a new user to test.
Does it still feel different?

If not, the cause may be that your old profile is overwriting some of the newer settings in Hoary.[/QUOTE]

I've now been able to do this test.  Unfortunately the result is the same - only the old wallpapers (no sign of April at all, no blues), old feel to Synaptic etc.  Ho Hum.  I'm really perplexed now...

---

### Post by darkfox on 2005-04-28
[QUOTE=Joeb]I'm coming late to this discussion, but what did you do about your home directories? If you created new home directories on the new install and copied back stuff you wanted, versus leaving the home directories intact on the upgrade, then you most likely have different configuration files in the upgraded version vs the clean install.

Some of the leftover items in the upgraded version might include fonts, themes and wallpapers, along with any manual tweaks you might have made. Also, a lot of times, existing configuration and shell scripts are left untouched in an upgrade vs a new install. So, even if it's not a home directory issue, your /etc and /usr/bin may have different contents.

I don't know if that is the cause of your problem or not, though.  Just some other places to look.

Joeb[/QUOTE]

Well, I set up an entirely new user cleanly and the results were the same, so I guess its not that.  Thanks for the advice, it could well be something in /etc somewhere but I can't begin to think what it could be.  Most odd...

---

### Post by darkfox on 2005-04-28
OK I've found where I went wrong - I knew it must have been a problem with the chair-to-keyboard interface 

I forgot the update repositories:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted universe

All is now well :)

---

### Post by kiddo on 2005-04-28
Weeeeeeeeeell the "problem" is real, I tell you ;) (I'm late on this topic.) I have the same issue here, some stuff just doesn't "appear" in a dist-upgraded box. For instance, the update manager tray icon didn't show up automatically for me. But I just discovered something a few days ago. I created a new user and.. it behaves mostly -- I think -- like a fresh hoary. So I guess that's a false alert, or simply that the user config files do all the difference, and that's why a fresh install changes lots of things.

---

