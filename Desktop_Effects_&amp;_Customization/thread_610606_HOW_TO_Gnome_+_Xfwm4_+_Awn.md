---
title: "HOW TO: Gnome + Xfwm4 + Awn"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by alvinistic on 2007-11-12
Hello, folks.

Today I am thinking of giving back to the Ubuntu community which has been really helpful to me. :guitar:
This how to is written for Ubuntu 7.10 Gutsy Gibbon. It may apply for others with slight adaption. 

**Why Xfwm4, not Metacity?**
In short, to gain a stable compositor which is not so resource hungry as compiz fusion. This is suitable for those who have hardware limitation to run compiz fusion without problems (e.g. choppy video, slow frame rate, etc). Mind though that xfwm provides only simple eye candies such as transparency and drop shadow. But hey, it's still better than nothing, isn't it?

**Why Gnome, not Xfce?**
Well, I have to say it is about preferences. Personally, I am used to Gnome and my computer runs it just fine hence I do not see the need of a lighter desktop environment. Besides, IMHO Ubuntu is more polished than its sibling Xubuntu.

**Why are we using Xfwm4 svn? I thought there is a package for Xfwm4 in repo, no?**
Xfwm4 in repo have some bugs working with Awn; the most well-known ones include: Awn only appears in one workspace and can't focus on window. However, those issues have been fixed in Xfwm4 svn.

Credits:
*This how to is adapted from this 2-year-old [[COLOR="RoyalBlue"]_thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=88393"). Many thanks to theine for providing it!
*Special thanks also to tehkain for telling me about the incorrect inline spacing in checkinstall spec file which caused it to fail.

Before begin, this guide requires subversion and checkinstall. Please install it beforehand before you continue.

```
sudo apt-get install subversion checkinstall
```

Alright then let's get it started!

1. Install necessary headers to compile Xfwm4 svn

```
sudo apt-get build-dep xfwm4
```

2. Grab Xfwm4 from svn and install it
```
svn co http://svn.xfce.org/svn/xfce/xfwm4/trunk xfwm4
```

```
cd xfwm4
./autogen.sh --enable-compositor --prefix=/usr
make
```

**Recommended**: Create a deb package using checkinstall using the spec file in the attachment below (rename xfwm4.txt to xfwm4.spec) 

```
sudo checkinstall --spec /path/to/xfwm4.spec
```

Note 1: the deb package created will not have any dependencies! So make sure you follow this guide closely to make sure everything works.

**Alternatively**, you can also do:

```
sudo make install
```

Note 2: it is recommended that you do not delete this folder yet, so that in case it does not work, you can always uninstall it with sudo make uninstall.

3. Install the Xfce settings manager:

```
sudo apt-get install xfce4-mcs-manager
```

4. Next, edit /usr/bin/gnome-wm and add xfwm4 to the entry line that already contains openbox, i.e.
```
sudo gedit /usr/bin/gnome-wm
```

Find this line:

```
openbox|enlightenment|e16)
      OPT1=--sm-client-id
      OPT2=$SMID
      ;;
```

Add “|xfwm4” (without quote) after “e16”, so it will look like this:

```
openbox|enlightenment|e16|xfwm4)
      OPT1=--sm-client-id
      OPT2=$SMID
      ;;
```

Don't forget to save it ;)

5. Set the WINDOW_MANAGER environment variable so that Gnome is aware of it. This can be accomplished by
```

echo export WINDOW_MANAGER=/usr/bin/xfwm4 >> ~/.gnomerc
```

6. Log off and then log back into Gnome, xfwm4 should now manage your windows instead of metacity. To activate compositor, type this in terminal:

```
xfce-setting-show
```

Choose Window Manager Tweaks and the last tab is the one you are looking for. Turn on the compositor and adjust according to your preference.

7. Install awn using this [[COLOR="RoyalBlue"]_guide_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=385981")
It is very well written so I don't think I should rewrite it here ;)

**Known Issue:**

Xfwm4 does not integrate into Gnome flawlessly. But it's only a small issue IMHO. It always hangs when there is a prompt with darkened background. This includes the password input prompt and the logout. So here is the workaround:

```
gconf-editor
```

/apps/panel/global -> tick upstream session then restart panel (killall gnome-panel)
/apps/gksu -> tick disable_grab

Now the password input prompt will not darken the background and you can restart/shutdown computer through System->Shut Down...
 
Now, I guess a screenshot would be nice:

[[IMG]http://img266.imageshack.us/img266/1965/screenshotgs0.th.png[/IMG]](http://img266.imageshack.us/my.php?image=screenshotgs0.png)

That's all. Enjoy!

-Alvin

---

### Post by DocHoliday52090 on 2007-11-12
Sexy, thanks. 

Running well on my old PIII :o

---

### Post by urukrama on 2007-11-12
> **alvinistic said:**
> Note: it is recommended that you do not delete this folder yet, so that in case it does not work, you can always uninstall it with sudo make uninstall.

Nice guide. You could use checkinstall to install the package (and change the last command from 'sudo make install' to 'sudo checkinstall). It creates a .deb package from the source and then installs it; if you ever want to uninstall it, you can do so easily with apt-get, aptitude or Synaptic. Checkinstall is in the repos, so all you need to do is:

```
sudo apt-get install checkinstall
```

---

### Post by Chang An on 2007-11-12
So if I have a fresh install of xubuntu gutsy I will need to install Xfwm4 svn as to not have bugs running awn?  Thanks

---

### Post by alvinistic on 2007-11-13
> **DocHoliday52090 said:**
> Sexy, thanks. 

Running well on my old PIII :o

Great! Glad it works for you :D

> **urukrama said:**
> Nice guide. You could use checkinstall to install the package (and change the last command from 'sudo make install' to 'sudo checkinstall). It creates a .deb package from the source and then installs it; if you ever want to uninstall it, you can do so easily with apt-get, aptitude or Synaptic. Checkinstall is in the repos, so all you need to do is:

```
sudo apt-get install checkinstall
```

Hi urukrama, I've tried that. But it did not work for me. Checkinstall refused to make a deb out of it. Maybe you can try it out and report back to us? Thanks!

> **Chang An said:**
> So if I have a fresh install of xubuntu gutsy I will need to install Xfwm4 svn as to not have bugs running awn?  Thanks

I haven't tried it with Xubuntu but I bet you will need the svn version. The one in the repo (and hence the one in Xubuntu) still has the bugs unfixed.

---

### Post by tehkain on 2007-11-13
If you want to check install
change the spec file to something like this because checkinstall screws up because of the inline spacing in the values

```

Summary:Next generation window manager for xfce
Name:xfwm4
Version:4.5.0
Release:1
License:GPL
URL:http://www.xfce.org/
Source0:%{name}-%{version}.tar.gz
Group:User Interface/Desktops
BuildRoot:%{_tmppath}/%{name}-root

%description
xfwm4 is a window manager compatable with GNOME, GNOME2, KDE2, KDE3 and Xfce.

%prep
%setup -q

%build
%configure --enable-compositor 
make

%install
rm -rf $RPM_BUILD_ROOT
make install DESTDIR=$RPM_BUILD_ROOT mandir=%{_mandir}

%clean
rm -rf $RPM_BUILD_ROOT

%files
%defattr(-,root,root)
%doc example.gtkrc-2.0 README INSTALL TODO COPYING AUTHORS COMPOSITOR
%{_bindir}
%{_libdir}/xfce4
%{_datadir}/applications
%{_datadir}/icons
%{_datadir}/locale
%{_datadir}/xfce4
%{_datadir}/xfwm4
%{_datadir}/themes

```

---

### Post by alvinistic on 2007-11-14
> **tehkain said:**
> If you want to check install
change the spec file to something like this because checkinstall screws up because of the inline spacing in the values

You're right. Thank you so much for pointing it out to me. I have updated the guide with checkinstall and put you in the credits ;)

How I love Ubuntu and her community. I hope this guide can be useful for others.

---

### Post by MJako on 2007-11-14
Hello.
You made a very good work with this HOWTO.
I am an Italian Ubuntu user, so forgive me for my poor english.
I follow this guide to install xfwm4 from svn: with sudo checkinstall I receive an error (a specified the file you attached in your post), but with sudo make install everythings work.
The error was related to a xfce directory who wasn't present in /usr/lib/.
I resolved with sudo make install, but i preferred checkinstall to eventually remove the package with apt-get.
I have one question for you. Can I translate this guide and put in italian Ubuntu forum, specifying the source, of course.

Bye

Edit: I have Ubuntu 7.04 Feisty Fawn

---

### Post by alvinistic on 2007-11-14
> **MJako said:**
> 
I follow this guide to install xfwm4 from svn: with sudo checkinstall I receive an error (a specified the file you attached in your post), but with sudo make install everythings work.
The error was related to a xfce directory who wasn't present in /usr/lib/.
I resolved with sudo make install, but i preferred checkinstall to eventually remove the package with apt-get.

Hi, Mjako. I am not really sure. But maybe you can try install the xfce4-mcs-manager first before doing the checkinstall? Perhaps it will create /usr/lib/xfce because I have it installed when I build the package using checkinstall.

Or other possibility, as mentioned, I built it in ubuntu gutsy. Perhaps the spec file will be a bit different under feisty. So, you may want to run checkinstall without specifying the spec file

```
sudo checkinstall
```

Then when the checkinstall prompt you for any changes to make, see whether there is an improper spacing. If there is, here is what I did:
- press Ctrl+C to terminate the checkinstall process
- edit the spec file generated by checkinstall. It should be in the source code directory named xfwm4.spec

```
gedit xfwm4.spec
```

- remove all the spacing there. For example change

```
Name:         xfwm4
```

to 

```
Name:xfwm4
```

- I also removed the several few lines about dependencies because it gives me an error. Just compare your spec file with the one I attached.

After that, just re-run checkinstall with the edited spec file:

```
sudo checkinstall --spec xfwm4_edited.spec
```

And voila! Your package is ready and is already installed to your system.

> I have one question for you. Can I translate this guide and put in italian Ubuntu forum, specifying the source, of course.

Sure, you can do that. Just send my best regards for the Italians there :D

---

### Post by MJako on 2007-11-14
Thanks for the tips, but I already resolved with sudo make install.
Maybe I can run sudo make uninstall to remove xfwm and retry with checkinstall, but I have already installed awn and I am satisfied with the work.
OK, in the few next days I put your solution in the italian Ubuntu forum, with a link to this thread, of course.:popcorn:

You have done a very good job. I like awn, but compiz always give me some problem.
Now I can have awn without the heaviness (and problem) of compiz.
Also I must admit that xfwm is very nice (I was tired of metacity).

Bye

---

### Post by SammyBoy247 on 2007-11-24
Help!...
I followed your guide - Excelent guide, everything went great - just the known issue with the "fade on password".  How ever I am now in failsafe mode scratching my head.

Anyway have been happily using Xfwm4 and AWN for a few weeks but logged on yesterday and i was met by a grey screen with a shadow where my main pannel was supposed to be and a shadow for every right click - the desktop context menu I think.

I think when I last updated the compiz-fusion packages were updated and I now have two compositors and window managers argueing for controll of my gui.

This is all beyond my skills - I whould like some help reversing the XFWM4 install and I will start from scratch.

Any help greatfully received. Cheers.

---

### Post by Zip247 on 2007-12-16
Thanks for the guide.  The Xfwm4 adds some flavor to the desktop.

---

### Post by cheemosabe on 2008-01-13
I recently switched to Xubuntu.
Although compiz was pretty fast in GNOME, compositing in xfwm was really slow, then i found out that it uses EXA acceleration. For those of you experiencing the same problem try adding this to your Device section in xorg.conf:

        Option "AccelMethod" "EXA"

---

### Post by JordanII on 2008-02-18
Is there a way I can do this, but only use the XFCE compositor and not the window borders? Thanks!

---

### Post by jonathanpiper on 2008-03-06
How do I go about switching back to Metacity as my window manager?

---

### Post by alvinistic on 2008-03-06
@JordanII: 
I don't think it is possible. The compositor itself is part of Xfwm's feature. If you wanna keep metacity without compiz, your best bet would be xcompmgr. 

@jonathanpiper:
$ gedit ~/.gnomerc
change the contents to:
WINDOW_MANAGER=/usr/bin/metacity

---

