---
title: "[SOLVED] PekWM + KDE Applications"
date: 2008-06-13
forum: Desktop Environments
---

### Post by jviscosi on 2008-06-13
So I've been playing with PekWM lately and like it a lot (I'm a longtime Fluxbox user), but I've noticed that it doesn't seem to play nicely with KDE applications.  For instance, KDE apps that are supposed to go in the system tray (I use peksystray), like Klipper and Amarok, don't.  Worse, Amarok often hangs when I open it, and when it does start normally, it's quasi-unusable -- for instance, it refuses to download podcasts.  I don't have any of these issues in OpenBox or Fluxbox.  (The startup scripts for all three WMs on my machine are more or less identical.)

I've tried the PekWM that comes with Ubuntu, 0.1.6, and the git version and they all behave the same way.

Anyway, I was wondering if anybody else had similar problems with KDE apps in PekWM?  I don't use a lot of KDE apps, but I want them to work if I decide to fire one up.

---

### Post by urukrama on 2008-06-14
The only KDE app I use in Pekwm is Krusader, and that doesn't give me any difficulties. 

Is there anything of interest in your .xsession-errors file, or do you get any error messages when you launch these applications from a terminal.

---

### Post by jviscosi on 2008-06-14
Mmm, not much that means anything to me.  Klipper reports nothing.  Amarok reports this stuff before it forks:

> 
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8096108 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8096108 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
    StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
I'll have to jump over to Fluxbox and see if it reports the same thing when started from there.

**strace -f** on them shows that they both end up constantly looping through this:

> 
gettimeofday({1213452730, 935433}, NULL) = 0
select(8, [3 4 5 7], [], [], {0, 996685}) = 0 (Timeout)
gettimeofday({1213452731, 935178}, NULL) = 0
gettimeofday({1213452731, 935283}, NULL) = 0
read(4, 0x805595c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
However, other KDE apps that work properly (like kflickr) also do this so I don't think that's actually a problem.

.xsession-errors has some stuff in it like this:

> 
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x500001c
  Serial number of failed request:  22
  Current serial number in output stream:  23
DCOPServer: DCOPReply for unknown connection.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4c00007
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x4c00007
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x4c00007
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x4c00007
  Serial number of failed request:  22
  Current serial number in output stream:  23
DCOP aborting while waiting for answer from 'kded'
DCOP aborting while waiting for answer from 'kded'
DCOP aborting while waiting for answer from 'kded'
kdeinit, kded, and dcopserver are all running but maybe for some reason PekWM is getting in the way?  I will test it in Fluxbox and see if it does the same thing.

It's not a HUGE deal; I only use klipper to help persist my clipboard after I close applications, and I only use Amarok about once a week to grab new podcasts (it handles them better than Rhythmbox does).  The KDE apps I actually use regularly, like KPhotoAlbum and Kflickr, work fine.  I might just keep using PekWM anyway as I quite like it.  Thank you for your excellent and useful guide to configuring it, by the way!

I'm also open to suggestions for a program other than Amarok to use for managing podcasts.  What I like about Amarok is that it properly does whatever witchcraft is required to make a podcast support bookmarking -- i.e., you listen to it partway through, then listen to something else, then go back to the podcast and it picks up where it left off.

---

### Post by jviscosi on 2008-06-14
I can report that those BadWindow and DCOP .xsession_errors don't occur when launching Amarok and Klipper in Fluxbox.  Does this indicate that Amarok and Klipper are trying to do something that PekWM doesn't understand?

---

### Post by jviscosi on 2008-07-23
The latest git version of PekWM as of 7/23/2008 fixes both of these issues.  Me == Happy!

---

