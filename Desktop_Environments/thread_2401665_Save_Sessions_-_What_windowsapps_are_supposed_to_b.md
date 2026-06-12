---
title: "Save Sessions - What windows/apps are supposed to be saved ?"
date: 2018-09-20
forum: Desktop Environments
---

### Post by palipeaublasee on 2018-09-20
Hi,

I'm on Xubuntu 16.04 waiting to finish some clean up and my sys/config
backup before I switch to 18.04.  All my personal files are backed up.

I don't have the option to save session at logout screen, but in "Settings"
-> "Sesssion and Statup" -> General (tab) I have:

**Session Chooser**[INDENT]Display chooser on login  [  ]
[/INDENT]

**Logout Settings**[INDENT]Automatically save session on logout  [&#10004;]
[/INDENT]
[INDENT]Prompt on logout  [&#10004;]
[/INDENT]

I only ever use a single session.

I have done some tests and out of the dozen programs I have been using
only the following three show up on my destop:

    - thunar (file manager)
    - firefox
    - terminal (xfce4-terminal 0.6.3)

The Session tab in Sessions and Startup list:
- xfwm4
- Thunar
- Xfsettingsd
- xfce4-panel
- xfdesktop
- Power Manage
- firefox
- xfce4-terminal

Is there a way that I could at least make LibreOffice Writer and
my text editor (mousepad or leafpad) appear when I login, like
the three mentioned above?

Thanks.

---

### Post by ajgreeny on 2018-09-21
If you close those applications, eg LO Writer, before logging out they will not be included in your saved session, however, if you leave them running and logout or shutdown they should be included if you have "Save session" set as your default, though any unsaved data in those applications will be lost.

If you really want LO Writer, etc etc, to start automatically at login you can add them to the **Application Autostart** list in **Session and Startup** of the settings manager.

---

### Post by palipeaublasee on 2018-09-21
Hi,

Yes, I know they have to be opened.  They were, all of them, with every tests.  Also I 
 did not use the "save session" in Settings->Session and Startup, I simply logged out 
every time.  The "automatically save session on logout" should take care of it.

It's not that I need Writer opened in particular.  I would like to know how it is determined 
 that only the three programs I mentioned are saved (their state, not the programs 
 themselves).  Where is that documented?  Is it xfce4, xubuntu, the programs themselves 
 somehow, or in a configurtion file on my machine?   What quality do these three have in 
common, that other programs like Writer or Mousepad or Leafpad don't?

I was dreaming that since Firefox has its windows/web pages/tabs opened, and Thunar,
every instance of it, is opened at the same places as in the logout, a text editor could
have all its opened windows opened displaying the files that were there before.  So if I
had four text documents opened at logout, I would have the same four documents opened
at the subsequent login, in windows positioned at the same places.

It seemed odd to me so that for a long time I thought something was wrong with my
system, or that there was some kind of bug in xfce.  Since I didn't find any relevant info 
on Internet I figured it must be my system, but better ask then suppose.

Thanks for the reply.

---

