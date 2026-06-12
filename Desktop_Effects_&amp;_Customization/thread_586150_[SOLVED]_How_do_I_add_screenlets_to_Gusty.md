---
title: "[SOLVED] How do I add screenlets to Gusty?"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by sci-fi guy on 2007-10-22
I have not been able to get screenlets to work since Feisty and I am wondering what others have done to get it to work.

---

### Post by santiagoward2000 on 2007-10-22
> **sci-fi guy said:**
> I have not been able to get screenlets to work since Feisty and I am wondering what others have done to get it to work.

I just installed them with almost no problem in Gusty. Perhaps you're using the Feisty repository? If so, just update your list.
I used these instructions:
[http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users]("http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users")
If that's not the problem, maybe you should see if you've installed all the dependencies:
> First of all you need python (tested with 2.4 and 2.5). Further you need pygtk (at least version 2.10), pycairo, python-xdg and the package python-gnome2-desktop. The latter is unfortunately needed for the wnck/rsvg bindings (hopefully this will change sometime).
I hope this can help you.

---

### Post by sci-fi guy on 2007-10-22
I get an error when tying to compile pygtk (why ain't this in the repos?):
```
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

Also, I only found window exe's for pycairo.

---

### Post by santiagoward2000 on 2007-10-22
> **sci-fi guy said:**
> I get an error when tying to compile pygtk (why ain't this in the repos?):
```
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

Also, I only found window exe's for pycairo.

Hmmm, that's strange. I haven't even installed or compiled pycairo, but my screenlets work...

---

### Post by sci-fi guy on 2007-10-28
I just realized where my problem might be coming from: I am running the 64-bit version.

---

### Post by Hexxagon on 2007-10-28
Hey...

I just installed it like it says in the FAQ from screenlet.org.

Now, when I enter the screenlet settings I get the error message "unable to connect or launch daemon. Some Values may be displayed incorrectly".

I can't start any Screenlets... well, they just don't appear, no further error messages.

Any Ideas?

---

### Post by rundee_f on 2007-10-29
im having the same problems,, any idea??

---

### Post by ilowtf on 2007-10-29
> **Hexxagon said:**
> Hey...

I just installed it like it says in the FAQ from screenlet.org.

Now, when I enter the screenlet settings I get the error message "unable to connect or launch daemon. Some Values may be displayed incorrectly".

I can't start any Screenlets... well, they just don't appear, no further error messages.

Any Ideas?
I had the same problem, I went to proferences menu of compiz fusion and went to the widget layer meny, and in the behavior tab I put "name=Screenlet.py" (without the quotes) and now it seems that it can find daemon. But when I try to launch a screenlets this is what happens :

LISTED PATH NOT EXISTS: /usr/local/share/screenlets/screenlets-0.0.10
DAEMON FOUND!
Ruler
Launching Screenlet from: /usr/local/share/screenlets/Ruler/RulerScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/RulerScreenlet.log
REGISTER screenlet: RulerScreenlet


And the screenlet does not appear. Anyone knows why? and how to fix it?

---

### Post by rundee_f on 2007-10-29
bump

---

### Post by bllambert on 2007-10-30
Glad to see I am not alone.  Not only do I get the Daemon error at the start of each session, the screenlets forget their settings.  Also, the Calender comes up as a big fish after a restart.  As cool as these screenlets look when working, they don't seem to be worth this hassle.

---

### Post by Zorael on 2007-10-30
I can't get the manager to start. What do I need to install?

```
zorael@azrael:~$ screenlets-manager
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 23, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 33, in <module>
    import rsvg
ImportError: No module named rsvg
```


edit: nevermind, found it, python-gnome2-desktop.

---

### Post by mjamesd on 2007-10-31
I get the same error message ("Unable to connect or launch daemon. Some values may be displayed incorrectly.") when starting screenlets-manager.  When I first installed Screenlets, I could start the manager (I got this error) and it wouldn't add widgets to the widget layer (I use Compiz).  After a restart, I could add widgets but still got this message.  I read on another forum ([http://ubuntuforums.org/showthread.php?t=589403](http://ubuntuforums.org/showthread.php?t=589403)) that you have to enable the "Regex Matching" plugin for Compiz. I still get the "Unable to connect or launch daemon. Some values may be displayed incorrectly." error when launching the screenlets-manager, but it works.


Ubuntu 7.10 kernel v. 2.6.22-12-386

---

### Post by Superman88 on 2007-11-10
I** get the Same Error, But Most of the Screelets work, Not all. Does anyone know how to fix this ????**

---

### Post by sci-fi guy on 2007-11-10
Curiously enough, the screenlets compiled, installed, and ran for me now. Now to figure out adesklets...

---

### Post by fox_jones on 2007-11-13
just do the Screenlet.py thing described in post #8

then start a terminal and create 2 directories:

mkdir ~/.config/Screenlets
mkdir ~/.config/autostart

et voila =^.^=

---

### Post by Mttechserv on 2007-11-20
What I found when running into the error: 
"Unable to connect or launch daemon. Some values may be displayed incorrectly."
was that the screenlets-daemon wasn't starting with my gnome session for some reason. 

Went into System>Preferences>Sessions and added a new startup program
( pointed to /usr/local/share/screenlets-manager/screenlets-daemon.py )
Et voila... the whole issue was resolved. 
( In my case, everything was working, but it wasn't saving any of the settings to start automatically )

Prior to this, I also had to check the permissions on individual screenlets and make sure they were set to be executable. ( not quite sure if this had any real effect on anything, just thought I should mention it )

---

