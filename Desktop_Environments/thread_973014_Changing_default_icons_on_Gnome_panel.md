---
title: "Changing default icons on Gnome panel"
date: 2008-11-06
forum: Desktop Environments
---

### Post by geefy on 2008-11-06
Hello,

I am building an LTSP server with Ubuntu 8.04 with the Edubuntu add on. Things are going well except for a couple issues that i can't figure out.

1. When I log in to gnome as a local user on the actual server, not from a client, it will show the background and sit for about 2 minutes then the panel will load then about 20 seconds later the icons and menus will show up. The only relevant logs that I have found are ~/.xsession-errors. Listed below:

Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

** (nautilus:17165): WARNING **: Unable to add monitor: Not supported
I/O warning : failed to load external entity "/home/linux/.compiz/session/default0"
  PID TTY          TIME CMD
17143 ?        00:00:00 pulseaudio

** (gnome-panel:17164): WARNING **: panel-applet-frame.c:1310: failed to get Bonobo/Control interface on applet OAFIID:GNOME_MixerApplet:
Unknown CORBA exception id: 'IDL:omg.org/CORBA/COMM_FAILURE:1.0'


I have googled all of this and tried dozens of "fixes" none have worked. 


2. I need to remove the Evolution-email icon from the default Gnome panel. This is a school district and I need to remove anything from plain sight that the kids might want to fiddle with. By default, when someone logs in they get the:
Applicatoins  Places  System (firefox) (email) (help)

I simply want to remove the (email) icon from the panel for all NEW users. I have gone through all the configs i can find and modified everything i could think of and it still shows up, even after rm -rfing the home directories of my test accounts.

Any advice??? This is also my first post so feel free to tell me what I did wrong :)

--scott

---

### Post by mfox on 2008-11-06
Scott, I think that all you have to do is right-click on that icon on the panel and you should get an option to delete or remove it.

---

### Post by geefy on 2008-11-06
That is correct. However, if i were to delete my profile lets say "/home/linuxuser" and then log back in as linuxuser... i would get a brand new profile with the email icon back on the panel. So what i am looking to do is change the "Default" profile that all new users get. So the end result would be that if i created a new user lets say "linuxuser2" when they logged in for the first time and got a brand new homedir they would not have the email icon on the panel. 

Does this make sense?

--scott

---

### Post by mfox on 2008-11-07
Makes sense, Scott, but I haven't ever dealt with anything bigger than my own desktop.  Perhaps you would do better to post your question in the Server forum.

---

### Post by geefy on 2008-11-07
That is a very good idea, thank you. I also posted to LTSP-discuss mailing list and got a couple good responses, but still no "fix". I will try your suggestion.

--scott

---

### Post by ad_267 on 2008-11-07
Maybe try sabayon, which allows you to customize the default desktop. I haven't used it myself, but it should be able to do this.

---

### Post by fballem on 2008-11-09
I'm wrestling with similar issues in the following thread: [http://ubuntuforums.org/showthread.php?t=975914](http://ubuntuforums.org/showthread.php?t=975914)

During the course of this research, I have discovered that there is a file called /etc/gconf/schemas/panel-default-setup.entries that may hold the key to solving your problem (getting rid of the evolution icon on the top panel for new users).

In that file, there is a lengthy section that starts with ```
<!-- Email Launcher -->
``` and has a number of lines. The next section, in my file, starts with ```
<!-- Yelp Launcher -->
```

Make sure that you make a backup of this file first. You should then be able to edit this file ```
gksudo gedit /etc/gconf/schemas/panel-default-setup.entries
``` and delete the section from this file.

Once that is done, then restart your system and setup a new user using System > Administration > Users and Groups. Then login as the new user. If all is well, the Evolution icon will not appear on the top panel.

Three things before you try this:
[LIST=1]
[*]I would like to suggest that you wait until other users have looked at this post and provided their comments. I'm relatively new and my research is still in progress.
[*]Make certain you backup the file before you make any changes to it. If these changes don't work, then you can delete the changed file and rename the backup so that things are back to what they should be.
[*]If at all possible, do this on a separate machine from your production machine. That way, if it breaks, there won't be an impact on your other work.
[/LIST]

If this works, you may want to make detailed notes of this change for your future reference. I'm not sure if this file is updated by the Update Manager. It is certainly created when ubuntu is installed initially. You may want to look at remastersys as a way to create a custom installation disc once you have a system setup exactly the way that you want it.

Hope this helps,

---

### Post by geefy on 2008-11-13
Well... thank you all for your replies. I will try out the suggestions and when I have figured out the solution I will post.

Thanks,

--scott

---

