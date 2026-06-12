---
title: "Cannot move files to the trash"
date: 2009-06-04
forum: Desktop Environments
---

### Post by bryanbankester on 2009-06-04
Whenever I try to move any file into the trash, an error message says "The trash has reached its maximum size! Cleanup the trash manually." 

There is less than 300 MB in the trash right now. Dolphin is my file manager under Kubuntu 9.04 AMD64.

---

### Post by bryanbankester on 2009-06-06
Nevermind, there was actually over 60 GB in the trash. Under Dolphin Preferences, you can set a maximum size. There is only 2 GB now and files can be moved to the trash.

But still, whenever I right click inside the Dolphin trash window and go to "Properties", Dolphin crashes and "The KDE Crash Handler" window appears. It doesn't do this for any other window. I guess I'll submit a bug report.

**A Fatal Error Occurred**
The application Dolphin (dolphin) crashed and caused the signal 6 (SIGABRT).

Application: Dolphin (dolphin), signal SIGABRT
0x00007f1bc24cacf0 in nanosleep () from /lib/libc.so.6

Thread 1 (Thread 0x7f1bc6e6a750 (LWP 14436)):
[KCrash Handler]
#5  0x00007f1bc2455fb5 in raise () from /lib/libc.so.6
#6  0x00007f1bc2457bc3 in abort () from /lib/libc.so.6
#7  0x00007f1bc244ef09 in __assert_fail () from /lib/libc.so.6
#8  0x00007f1bc1fb1012 in Strigi::AnalysisResult::Private::Private () from /usr/lib/libstreamanalyzer.so.0
#9  0x00007f1bc1fb1130 in Strigi::AnalysisResult::AnalysisResult () from /usr/lib/libstreamanalyzer.so.0
#10 0x00007f1bc6908709 in ?? () from /usr/lib/libkio.so.5
#11 0x00007f1bc6909d22 in KFileMetaInfo::KFileMetaInfo () from /usr/lib/libkio.so.5
#12 0x00007f1bc68f9c3c in KFileItem::metaInfo () from /usr/lib/libkio.so.5
#13 0x00007f1bc69b75f0 in KFileMetaPropsPlugin::KFileMetaPropsPlugin () from /usr/lib/libkio.so.5
#14 0x00007f1bc69db841 in KPropertiesDialog::KPropertiesDialogPrivate::insertPages () from /usr/lib/libkio.so.5
#15 0x00007f1bc69dba93 in KPropertiesDialog::KPropertiesDialogPrivate::init () from /usr/lib/libkio.so.5
#16 0x00007f1bc69dce28 in KPropertiesDialog::KPropertiesDialog () from /usr/lib/libkio.so.5
#17 0x00007f1bc5e8034a in DolphinViewActionHandler::slotProperties () from /usr/lib/libdolphinprivate.so.4
#18 0x00007f1bc5e68a9a in DolphinViewActionHandler::qt_metacall () from /usr/lib/libdolphinprivate.so.4
#19 0x00007f1bc30aa1f2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#20 0x00007f1bc355c7e7 in QAction::triggered () from /usr/lib/libQtGui.so.4
#21 0x00007f1bc355dc60 in QAction::activate () from /usr/lib/libQtGui.so.4
#22 0x00007f1bc398ba3c in ?? () from /usr/lib/libQtGui.so.4
#23 0x00007f1bc3991a0e in ?? () from /usr/lib/libQtGui.so.4
#24 0x00007f1bc4bd7b71 in KMenu::mouseReleaseEvent () from /usr/lib/libkdeui.so.5
#25 0x00007f1bc35b38cf in QWidget::event () from /usr/lib/libQtGui.so.4
#26 0x00007f1bc39941cb in QMenu::event () from /usr/lib/libQtGui.so.4
#27 0x00007f1bc356278d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#28 0x00007f1bc356b0da in QApplication::notify () from /usr/lib/libQtGui.so.4
#29 0x00007f1bc4b0626b in KApplication::notify () from /usr/lib/libkdeui.so.5
#30 0x00007f1bc309475c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#31 0x00007f1bc356a328 in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
#32 0x00007f1bc35d3fd4 in ?? () from /usr/lib/libQtGui.so.4
#33 0x00007f1bc35d2a88 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#34 0x00007f1bc35fb464 in ?? () from /usr/lib/libQtGui.so.4
#35 0x00007f1bbe91020a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#36 0x00007f1bbe9138e0 in ?? () from /usr/lib/libglib-2.0.so.0
#37 0x00007f1bbe913a7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#38 0x00007f1bc30bde6f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#39 0x00007f1bc35fabef in ?? () from /usr/lib/libQtGui.so.4
#40 0x00007f1bc3093002 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#41 0x00007f1bc30933cd in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#42 0x00007f1bc3994025 in QMenu::exec () from /usr/lib/libQtGui.so.4
#43 0x00000000004350a7 in _start ()

---

### Post by ShepHeard on 2009-07-27
I have the same problem - you ever get a solution?

---

### Post by bryanbankester on 2009-07-27
[https://bugs.kde.org/show_bug.cgi?id=185551](https://bugs.kde.org/show_bug.cgi?id=185551)
I still have this problem.

---

### Post by Zorael on 2009-07-27
[Comment 11](http://bugs.kde.org/show_bug.cgi?id=185551#c11), posted 2009-04-05:
> SVN commit 949697 by vandenoever:

Fix bug 185551

Strigi now allows path that start with protocol:/* like
 'file:///' or 'remote:/'

BUG:185551



 M  +9 -1      analysisresult.cpp  


WebSVN link: [http://websvn.kde.org/?view=rev&revision=949697](http://websvn.kde.org/?view=rev&revision=949697)

[Comment 41](http://bugs.kde.org/show_bug.cgi?id=185551#c41):
> [I]> I can confirm, in Kubuntu Jaunty with KDE 4.2.3 Dolphin stills crash.
[/I]
Note that this crash is a bug in Strigi which is released separately from KDE.
Therefore, an update of KDE alone cannot fix the problem for you.

People who cannot reproduce this crash either already have a fixed Strigi
version installed, or their Strigi is built with asserts disabled.

So the bug (*in Strigi*) was supposedly fixed in svn back in April, but the fix needs to be backported if you're to get it in Jaunty. You may want to contact MOTUs or #kubuntu-devel on irc.freenode.net, or just post a launchpad report to ask to have the fix be applied to current packages.

---

### Post by ShepHeard on 2009-07-27
Why is the bug marked as fixed?

---

### Post by ShepHeard on 2009-07-27
@Zorael: Sorry - our posts obviously crossed.. So, what should we do? Can we not update Strigi ourselves?

Excuse the ignorence, I'm on a learning curve... :)

---

### Post by Zorael on 2009-07-27
> **ShepHeard said:**
> @Zorael: Sorry - our posts obviously crossed.. So, what should we do? Can we not update Strigi ourselves?
Chances are that if you update Strigi to its most recent version, it'll depend on some other component also being a more recent version, which in turn depends on some other upgrade, and you end up having to upgrade a whole lot manually.

The *best* solution would be to get an Ubuntu packager to add the bugfix to the current Strigi code that's included in Jaunty, and have it be uploaded to the repositories as an upgrade. (Alternatively to the backports repo.)

I don't seem to get this issue on my netbook running Jaunty, but then I disabled Strigi early on to get rid of the cpu overhead on something I really don't use (the search feature Strigi provides).

It looks like a quick fix and really something one should be able to upload to a Launchpad PPA. [Replace the one line to the left with the nine to the right](http://websvn.kde.org/trunk/kdesupport/strigi/src/streamanalyzer/analysisresult.cpp?r1=949697&r2=949696&pathrev=949697), compile and install. But still, better to let Launchpad handle the compiling and just use the packages it provides. ;3

---

### Post by Zorael on 2009-07-27
I pulled the source, pasted the changes, added a few lines in the changelog and uploaded the bundle to Launchpad. It should be up in a few minutes over at [http://launchpad.net/~zorael/+archive/ppa](http://launchpad.net/~zorael/+archive/ppa) if you want to give the (supposedly) fixed packages a try. I'm not sure if you need to completely restart X to get the new Strigi loaded; you may need to. Click on "read about installing" if you don't know how to add repositories.

Fetch the key with the following.
```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 85AF6DDF
```

If you want to revert the upgrade, do this.
```
$ VER=0.6.4-0ubuntu2
$ sudo aptitude install strigi-daemon=VER strigi-client=VER libsearchclient0=VER libstreamanalyzer0=VER libstreams0=VER libstrigihtmlgui0=VER libstrigiqtdbusclient0=VER
```
See if you missed any packages (when reverting) with this. It shouldn't output anything if you managed to downgrade back successfully.
```
$ dpkg -l | grep 0.6.4-0ubuntu3~ppa2
```


And don't mind the changelog. I botched the first upload and it keeps rubbing it in.

---

### Post by ShepHeard on 2009-07-31
Cheers Zoreal - so basically, you fixed the buggy code, and uploaded it yourself - so we've just added your repo, and done an update. Kind of pre-empting the eventual fix released by the devs? 
We're so trusting... :)

And by revert the upgrade, you mean re-install the old (original) versions?

I'd waited to try this as the kernal's just been updated, but it's not fixed, so I've given your suggestion a try. 

I'll let you know how it goes.

Thanks again!

Shep :)

---

### Post by ShepHeard on 2009-08-01
OK - so this has fixed the problem of Dolphin crashing when I click properties on the Trash can, but I still can't delete the filder I want to, and still get the maximum size error...

Any ideas?

---

### Post by Zorael on 2009-08-01
> **ShepHeard said:**
> Cheers Zoreal - so basically, you fixed the buggy code, and uploaded it yourself - so we've just added your repo, and done an update. Kind of pre-empting the eventual fix released by the devs? 
We're so trusting... :)

And by revert the upgrade, you mean re-install the old (original) versions?
In a sense, the bug is already fixed, but a version in which the fix is included is not likely to ever hit Jaunty's main repos, since it isn't a security bug. From [the Ubuntu wiki entry on backports;](https://help.ubuntu.com/community/UbuntuBackports)
> Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages **stays constant** for the entire 6 months. For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time. **The Ubuntu team may apply important security fixes to 2.0.x, but any new features or non-security bugfixes will not be made available.**

This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.
So since this isn't a security bug, it's not slated to be backported into the **main** repositories. A more recent version of strigi may yet hit the **backports** repository, including new features along with this bugfix.

By reverting, I mean reinstalling the original version, yes. You would also need to remove my repository or **forbid** my version in Synaptic/aptitude. Else it will simply reupgrade to my version at the next upgrade run.

> **ShepHeard said:**
> OK - so this has fixed the problem of Dolphin crashing when I click properties on the Trash can, but I still can't delete the filder I want to, and still get the maximum size error...

Any ideas?
The OP said he had actually 60gb in his trash, and cleaning it up made the maximum size error go away.
> **bryanbankester said:**
> Nevermind, there was actually over 60 GB in the trash. Under Dolphin Preferences, you can set a maximum size. There is only 2 GB now and files can be moved to the trash.
Do you get the message even with an empty-ish trash? If so, that suggests it's another bug; I only added the fix for the crash one.

---

### Post by ShepHeard on 2009-08-01
Zoreal, thanks a lot - you've been a real help. Like I said, I'm still finding my way with Linux so thanks for pointing some of the fundamentals out to me. I'd never thought about backports.. 

As for the size error... I'm a muppet. It was, in fact, genuine. I was trying to delete a 10 gb folder - I hadn't realised it was that big, but it had a few more things in it than I remembered.. Like the apt cache from an old install (long story...)

Cheers,

Enjoy your weekend.

Shep

---

### Post by Jetro on 2011-01-11
Hi, I don't get an error while pressing Options etc., but I am unable to actually delete anything, however small it may be. I've emptied the trash and reloaded, and it's empty. Kubuntu 10.04

---

### Post by ebf.beltran on 2011-02-23
Check out this [link]("http://ubuntuforums.org/showthread.php?t=1675857&page=2"). I had the same problem and it solved it in no time.

---

### Post by Ludd1te on 2011-08-14
I get the same error--not always, but especially when deleting a lot of big files (regardless of how much is in my Trash).

For what it's worth, I can work around it by going to good ol' command line and using "rm -r foo/" where foo is the folder.

Remember, though, that "rm" is pretty much permanent: there's likely no getting the stuff back (but see <a href="http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html">this page</a> for a glimmer of hope).  So, use it carefully!

---

