---
title: "Remove krunner"
date: 2011-02-10
forum: Desktop Environments
---

### Post by Gaba_p on 2011-02-10
Hi everybody,

I hope somebody will help me because this is driving me mad. I just recently switched from Windows 7 to Ubuntu + KDE and I can't for the life of me find a suitable 'msconfig' replacement.
My issue in particular is with the 'krunner' process which I want to replace with 'synapse', but I just can't seem to find where to disable 'krunner' from starting up with the system.
The 'Autostart' module in 'System settings' shows nothing. Also 'Pidgin' and 'Cairo-dock' start with the system and I can't find where this information is located.  I'd like two things: a way to easily manage applications and services running when the system starts up, and a way to prevent the 'krunner' process from starting up again.

Thanks!

Gabriel

---

### Post by thefasterblueone on 2011-02-10
Try looking here:

Menu / Personnel Settings / Advanced Tab / AutoStart

---

### Post by inobe on 2011-02-10
i don't mean to push you off somewhere else, but if you cannot find the answers here, you can certainly inquire about them here [http://forum.kde.org/](http://forum.kde.org/)

or join a kde irc channel.

---

### Post by Gaba_p on 2011-02-10
@thefasterblueone
In KDE 4.5.3 there is no 'Advanced' tab in 'System settings' (which is what I assume you mean by 'Personnel settings') Furthermore, I already said I checked the 'Autostart' module and it shows nothing (and it's pretty much useless compared with 'msconfig' and this is just an honest opinion, I am NOT trolling and I'm NOT switching back to Windows)

@inobe Well, if nobody can/will help me here I guess I'll have to.

Cheers.

---

### Post by lykwydchykyn on 2011-02-10
- Krunner is an integral part of KDE.  And it in no way shares any functionality with synaptic.  Synaptic is a package manager, krunner is how you launch commands / search / do all kinds of wacky stuff in KDE.

 - If they aren't in the Autoruns page, pidgin and cairodock are probably being started as part of your saved session.  Try going to the session manager tool in system settings and select "start with an empty session" under "On Login".  Then logout and log back in and see if they don't start.

If you want your sessions saved you can re-enable that after pidgin &co are gone.

---

### Post by ankspo71 on 2011-02-10
Hi,
Boot Up Manger (BUM) makes a pretty good alternative to msconfig as far as services and startup scripts go, but krunner is not shown to run as a startup script or service in there either. I see some people mentioning disabling the Nepomuk plugin inside Krunner to avoid poor performance with Krunner, that is if it is enabled (because mine is already disabled). To do this, press Alt+F2, then when krunner opens, click on the little wrench icon to enable and disable plugins. You can also disable Nepomuk all-together if you like. It can be found in System Settings > Desktop Search > Basic Settings.
Hope this helps.

---

### Post by Gaba_p on 2011-02-11
@lykwydchykyn The saved session advise worked for Pidgin (I ended up removing Cairo and installing Docky)

@ankspo71 Thanks for pointing me to 'BUM'. Still, this service combined with the 'Autostart' module don't match the power and usability of the old 'msconfig'. This is very frustrating.

I changed my mind and will not be replacing 'krunner' with 'synapse' since the first is far more powerful. That aside it still bugs me that I don't have complete control over which services/apps run at start-up. It doesn't matter if 'krunner' is an integral part of KDE, it's a service and we should be able to choose whether we want it running or not.

Thanks to all.

---

### Post by lykwydchykyn on 2011-02-11
> **Gaba_p said:**
> 
I changed my mind and will not be replacing 'krunner' with 'Synaptic' since the first is far more powerful. That aside it still bugs me that I don't have complete control over which services/apps run at start-up. It doesn't matter if 'krunner' is an integral part of KDE, it's a service and we should be able to choose whether we want it running or not.

Thanks to all.

I don't understand why you think Synaptic would be a replacement for krunner.  They are not even remotely the same type of software.  Are you wanting to replace the package manager in Kubuntu (kpackagekit) with Synaptic, or are you looking for something to use in place of krunner (e.g. gnome-do)?

Surely you can understand that there are parts of a desktop environment that simply cannot be shut off, because the system depends on them.

---

### Post by Gaba_p on 2011-02-11
Sorry, my bad. I just realized I've been saying 'synaptic' instead of 'synapse' #-o

I'm going to edit all my previous comments, so I don't confuse anyone else.

The way I see it 'krunner' is simply a launcher, just like 'synapse'. Maybe I'm missing something here, but if that's all it is, why can't I shut it off??

---

### Post by lykwydchykyn on 2011-02-12
> **Gaba_p said:**
> Sorry, my bad. I just realized I've been saying 'synaptic' instead of 'synapse' #-o

I'm going to edit all my previous comments, so I don't confuse anyone else.

The way I see it 'krunner' is simply a launcher, just like 'synapse'. Maybe I'm missing something here, but if that's all it is, why can't I shut it off??

I supposed you could always do "pkill krunner" and see what breaks.  If nothing breaks, add that command to your startup.
If stuff breaks, then you know it's more than just a launcher.

---

### Post by Gaba_p on 2011-02-14
> **lykwydchykyn said:**
> I supposed you could always do "pkill krunner" and see what breaks.  If nothing breaks, add that command to your startup.
If stuff breaks, then you know it's more than just a launcher.

??? I'm sorry, but that is just not an acceptable answer/solution.

I'm looking for a simple thing: a decent start-up manager a la 'msconfig' so I can decide which apps/services run at start-up.

I have killed 'krunner' and the system seem to remain stable, but that is merely a trivial fact.

---

### Post by lykwydchykyn on 2011-02-15
> **Gaba_p said:**
> ??? I'm sorry, but that is just not an acceptable answer/solution.

I'm looking for a simple thing: a decent start-up manager a la 'msconfig' so I can decide which apps/services run at start-up.

I have killed 'krunner' and the system seem to remain stable, but that is merely a trivial fact.

Ok then, good luck.

---

### Post by inobe on 2011-02-15
> **Gaba_p said:**
> a way to prevent the 'krunner' process from starting up again.

Thanks!

Gabriel

krunner is in auto start, look here

[IMG]http://img249.imageshack.us/img249/7721/krunner.jpg[/IMG]

---

### Post by Gaba_p on 2011-02-15
@lykwydchykyn Thanks for trying to help.

@inobe Not in mine (see attachment)


PD: By the way, although 'Gnote' appears in my 'Autostart', there's no way I can make it run at start-up. I've tried all the methods I could think of...

---

### Post by inobe on 2011-02-15
> **Gaba_p said:**
> 
@inobe Not in mine (see attachment)


PD: By the way, although 'Gnote' appears in my 'Autostart', there's no way I can make it run at start-up. I've tried all the methods I could think of...

[http://techbase.kde.org/KDE_System_Administration/Startup](http://techbase.kde.org/KDE_System_Administration/Startup)

i know very little about scripting, assuming.

---

### Post by Gaba_p on 2011-02-15
@inobe Thank you very much! I read the guide you posted and I finally found where the option to autostart  'krunner' is ($KDEDIR/share/autostart/krunner.desktop), amongst various other apps like 'kmix'.

What is really a shame is the dispersion of options to store/manage apps and services to autostart. Off the top of my head I can think of three different 'autostart' folders (three!) and apparently the apps/services in this folders appear randomly in the 'Autostart' module and in 'BUM'...

I think this is a serious lack of functionality in KDE. Even the almost deprecated Windows XP had 'msconfig' which is much more powerful than anything KDE has right now (at least anything I could find)

Anyway, thanks a lot again!

Cheers,
Gabriel

---

### Post by lykwydchykyn on 2011-02-16
> **Gaba_p said:**
> @inobe Thank you very much! I read the guide you posted and I finally found where the option to autostart  'krunner' is ($KDEDIR/share/autostart/krunner.desktop), amongst various other apps like 'kmix'.

What is really a shame is the dispersion of options to store/manage apps and services to autostart. Off the top of my head I can think of three different 'autostart' folders (three!) and apparently the apps/services in this folders appear randomly in the 'Autostart' module and in 'BUM'...

I think this is a serious lack of functionality in KDE. Even the almost deprecated Windows XP had 'msconfig' which is much more powerful than anything KDE has right now (at least anything I could find)

Anyway, thanks a lot again!

Cheers,
Gabriel

Windows XP is a monolithic operating system -- every component is built specifically for Windows XP, and it can readily assume things about its environment from kernel to desktop.

KDE is only a desktop environment; it runs on hundreds of different Linux distros, BSD, and Windows (there's even a project to bring it to OS X).  Having a full-on boot-services manager would be somewhat impractical, seeing as it would have to support all the supported OSes (just supporting the Linux distros would be challenging enough, with all their varied init systems and service names).  Maybe someone will undertake to making such a tool for KDE some day, but frankly I think most of the users who want to get that low-level are content (if not happier) to use the terminal.

In general, you'll find things on Linux a bit more "siloed" than they are in OSX or Windows, because it's assembled from interchangeable parts, so to speak.   It's just the nature of the system.

---

### Post by Gaba_p on 2011-02-17
@lykwydchykyn You say: '*...I think most of the users who want to get that low-level are content (if not happier) to use the terminal...*'

Is there a way to check all processes set to auto start from the terminal? Could you tell me how this is done?

---

### Post by lykwydchykyn on 2011-02-18
> **Gaba_p said:**
> @lykwydchykyn You say: '*...I think most of the users who want to get that low-level are content (if not happier) to use the terminal...*'

Is there a way to check all processes set to auto start from the terminal? Could you tell me how this is done?

Probably not the kind of thing you're looking for, at least as far as I know.  System-wide services are going to be started under upstart and have scripts in /etc/init.  Desktop-specific stuff is dependent on what desktop you're running.

I guess I shouldn't say "terminal", it's more a question of hitting up config files and understanding the init system.  Sorry for being vague.

---

