---
title: "Adept: QT-based package manager for Kubuntu?"
date: 2005-08-18
forum: Desktop Environments
---

### Post by oobuntoo on 2005-08-18
I stumbled upon Adept package manager while googling for something else. Has anyone ever heard of this before? It is still in alpha stage. You can see the screenshots at this [website](http://web.ekhis.org/adept.html).  

The website says "The work on Adept (and through it on libapt-front) is currently sponsored through a bounty  by Ubuntu/Canonical for Kubuntu." I think this would be great for Kubuntu users although Synaptic is very good for now.

---

### Post by drizek on 2005-08-18
[QUOTE=oobuntoo]I stumbled upon Adept package manager while googling for something else. Has anyone ever heard of this before? It is still in alpha stage. You can see the screenshots at this [website](http://web.ekhis.org/adept.html).  

The website says "The work on Adept (and through it on libapt-front) is currently sponsored through a bounty  by Ubuntu/Canonical for Kubuntu." I think this would be great for Kubuntu users although Synaptic is very good for now.[/QUOTE]
 Its going to be used in breezy AFAIK. its great, but i wish there was a deb for it so we can use it right now.

---

### Post by 8FootSativa on 2005-08-18
Looks great. I loathe Kynaptic with a firey passion.

---

### Post by Nubsauce on 2005-08-18
[QUOTE=oobuntoo]I stumbled upon Adept package manager while googling for something else. Has anyone ever heard of this before? It is still in alpha stage. You can see the screenshots at this [website](http://web.ekhis.org/adept.html).  

The website says "The work on Adept (and through it on libapt-front) is currently sponsored through a bounty  by Ubuntu/Canonical for Kubuntu." I think this would be great for Kubuntu users although Synaptic is very good for now.[/QUOTE]
 Wow, that looks amazing.  I am just now using Kubuntu, been using just the gnome version and that looks as nice as the version on normal Ubuntu..  Synaptic(?)..  or whatever.

---

### Post by Mishura on 2005-08-18
Looks nice.  If only Kynaptic showed package details and such.  As far as Kpackage,  last time I used it was with Mepis, and the thing with it was, if you minimize KPackage then it stops what its doing  :mad:  .  It *has* to be maximized on your current desktop to work.  (No switching desktops either.. that paused it as well..)

Too bad there couldn't be any kind of merging between Adept and Kynaptic.. Kynaptic was SOO close.  Oh well.  Adept looks nice and I look forward to it so I can kill Yet Another GTK app.

---

### Post by ltmon on 2005-08-18
[QUOTE=Mishura]Looks nice.  If only Kynaptic showed package details and such.  As far as Kpackage,  last time I used it was with Mepis, and the thing with it was, if you minimize KPackage then it stops what its doing  :mad:  .  It *has* to be maximized on your current desktop to work.  (No switching desktops either.. that paused it as well..)

Too bad there couldn't be any kind of merging between Adept and Kynaptic.. Kynaptic was SOO close.  Oh well.  Adept looks nice and I look forward to it so I can kill Yet Another GTK app.[/QUOTE]

I did have a look at the Kynaptic code once, and it was a bit of a beast.  Some of the issues I had with it (on a code level) were:

Firstly, it should rightly be called qsynaptic because there was no use of the KDE apis in it anyway.  That's why the toolbar looked so weird and the app never seemed to "fit in" quite like it should.

The source contained a directory called "shared" (?) which was code shared from an old version of Synaptic.  Synaptic had probably fixed a whole lot of bugs since that was made.  I compared the latest version of Synaptic against this Kynaptic directory and the difference was huge.  It wouldn't have been possible to simply drop the newer code in without a concerted porting effort.

Also, Synaptic is collaborating in the development of libapt-front, the library that Adept is now based on.  Future versions of Synaptic will likely use that library for the backend work also I guess.

When you fix these problems, there actually isn't much useable code left in Kynaptic.  I think the starting afresh was the right thing to do.

L.

---

### Post by Mishura on 2005-08-19
[QUOTE=ltmon]I did have a look at the Kynaptic code once, and it was a bit of a beast.  Some of the issues I had with it (on a code level) were:

Firstly, it should rightly be called qsynaptic because there was no use of the KDE apis in it anyway.  That's why the toolbar looked so weird and the app never seemed to "fit in" quite like it should.

The source contained a directory called "shared" (?) which was code shared from an old version of Synaptic.  Synaptic had probably fixed a whole lot of bugs since that was made.  I compared the latest version of Synaptic against this Kynaptic directory and the difference was huge.  It wouldn't have been possible to simply drop the newer code in without a concerted porting effort.

Also, Synaptic is collaborating in the development of libapt-front, the library that Adept is now based on.  Future versions of Synaptic will likely use that library for the backend work also I guess.

When you fix these problems, there actually isn't much useable code left in Kynaptic.  I think the starting afresh was the right thing to do.

L.[/QUOTE]

Sounds good, now that you mention it.  The shared libapt-front thing looks to be the best bet, as both Adept and Synaptic don't have to "reinvent the wheel" a lot with the backend stuff.  Thanks for clearing this up.

Plus, Kynaptic is a stupid name anyways (NOT A WORD!).

---

### Post by JuanC on 2005-08-19
i wish that Adept would be a good port of synaptic.

i try kynaptic and was terrible , i didn't like and i had to return to synaptic.

But synaptic works sometimes good and sometimes freeze my kubuntu  ](*,)

---

### Post by Terracotta on 2005-08-19
I actually got to like kynaptic, it does what it has to, nothing more, it's got package description as well. But then again, if it's really old :). I actually hoped that yast4debian would set of. Great tool if adding new repos actually works (never got that in suse working :s, don't know why). The rest of installing stuff is quite similar to synaptics and kynaptics, I think :).

---

### Post by mornfall on 2005-08-23
Hello folks, since yesterdays alpha release of adept, you can apt-get it if you are using hoary or breezy versions of kubuntu. See [homepage](http://web.ekhis.org/adept.html) for the sources.list lines. It would be cool if you could install it and test it for me, thanks a lot. Btw, read the Plans and Progress section on the web, i will be working on improving the user interface for the beta.

Note for hoary users: installing adept alpha will upgrade your apt (and aptitude). That shouldn't be a problem, but you better know.

Adept home: [http://web.ekhis.org/adept.html](http://web.ekhis.org/adept.html)

---

### Post by !nkubus on 2005-08-24
It actually cause some irreversible damage:

Synaptic and kynaptic are removed and not reinstalable, kubuntu-desktop as well ,It give me unmet dependencies :(

and the kde debconf isn't working :(


hope to see a beta soon that will resolve some issues.

It look promising but it's too early to say houray.

---

### Post by haaglin on 2005-08-25
just download and install these, and your synaptic will be working again:

[http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.6.35ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.6.35ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.55+cvs20050406-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.55+cvs20050406-1_i386.deb)

it worked for me.

---

### Post by !nkubus on 2005-08-25
Thanks a lot

---

### Post by mornfall on 2005-09-06
Beta is out now. Check [adept web]("http://web.ekhis.org/adept.html").

---

### Post by Maikun on 2005-09-06
and got some problems.
Apart from the ones mentioned at the adept web page, here are some bugs and suggestions:

_**Bugs**_
- When you click the rmb on the Active filters part of the UI, it sometimes takes ages till the context menu is loaded and till then the UI is frozen.
- When you want to install a package, it sorts the dependencies without telling you that it's going to install (or remove?) extra packages
- The Kmenu entries don't sudo
- You cannot see anywhere the package size (or couldn't find it)
- adept updater doesn't need State filter nor such a huge area dedicated to filters
- The Beta anouncement on the web page gives a false date, 22.8.2005, when it was obviously released on the 6th :-)
- Commit changes works even if there are no changes

_**Wishes**_
-LEFT Mouse click on package name could unfold package details (not just if you click on the arrow). Way easier (and needed if you don't show details on a separate area like Synaptic).
- adept updater could be nicer (more like the ubuntu one?).

**Conclusion**
Adept has a lot of potencial and it's development it's extremely important to Kubuntu.
I would suggest doing a second beta release as soon as the Outstanding issues are solved, and with new icons.
Only then will enough people be willing to use it every day and find all bugs before the breezy release.

Regards

---

### Post by mornfall on 2005-09-06
Thanks for the feedback :). I have included the bugs on adept homepage. Handling dependencies on install/etc: the statusbar gives some immediate feedback (package counts to be changed) and there is preview changes button you should use before commiting. Re left mouse click, i am not entirely sure that's a good idea, because it ruins selection. Right now it is easy to select a bunch of packages and mark them for install/remove through context menu. The updater is rough yeah. Yes there will be second beta sometime next week.

---

### Post by Maikun on 2005-09-06
[QUOTE=mornfall]Thanks for the feedback :). [/QUOTE]
You are welcome. I also want Adept to rock  :) 

[QUOTE=mornfall]I have included the bugs on adept homepage. [/QUOTE]
Well, that was quick!.

[QUOTE=mornfall]
Handling dependencies on install/etc: the statusbar gives some immediate feedback (package counts to be changed) and there is preview changes button you should use before commiting. [/QUOTE]
Yes but that's not enough and you may install or remove something you don't want. At least it should ask to confirm you want to do all that (install/remove) once you click "commit changes".

[QUOTE=mornfall]left mouse click, i am not entirely sure that's a good idea, because it ruins selection. Right now it is easy to select a bunch of packages and mark them for install/remove through context menu. [/QUOTE]
But how often do you select a bunch of packages (normally to install something, you check *one* programm package and dependencies are installed automatically) versus how often do you view details?

[QUOTE=mornfall]Yes there will be second beta sometime next week.[/QUOTE] 
That's great! (In time for Kubuntu breezy preview? -> [https://wiki.ubuntu.com/BreezyReleaseSchedule](https://wiki.ubuntu.com/BreezyReleaseSchedule)) :)

---

### Post by Maikun on 2005-09-06
I have a crash to report. But first, isn't Adept being taken into KDE Bug Tracking system? I mean, ich you are not to be found here or at #mornfall, where should we report bugs in the future?

Also, another  bug: The program name is "Adept Manager (beta)". Shouldn't it be "Package Manager"?

**The Crash**
While filtering, I clicked on the arrow to show details and the program crashed. It has happened twice so far (with different filter names).
The KCrash output:
```

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
[Thread debugging using libthread_db enabled]
[New Thread -1237642592 (LWP 9253)]
[KCrash handler]
#4  0xb65c03fb in __dynamic_cast () from /usr/lib/libstdc++.so.5
#5  0xb7cffea8 in ept::ListerItem::less (this=0x8cae360, b=0x8d71cd8)
    at /home/mornfall/dev/libapt-front/dist/ept/ept/libept/lister.cpp:520
#6  0xb7cdf9e6 in ept::ExtendableItem::s_less (a=0x8cae360, b=0x8d71cd8)
    at /home/mornfall/dev/libapt-front/dist/ept/ept/libept/extendablelist.cpp:76
#7  0xb7ce03ff in std::_Rb_tree<ept::ExtendableItem*, ept::ExtendableItem*, std::_Identity<ept::ExtendableItem*>, bool (*)(ept::ExtendableItem const*, ept::ExtendableItem const*), std::allocator<ept::ExtendableItem*> >::insert_unique (
    this=0x83370d0, __position=
        {<std::_Rb_tree_base_iterator> = {_M_node = 0x857fcf0}, <No data fields>}, __v=@0xbfffe664) at stl_tree.h:1066
#8  0xb7ce0339 in std::set<ept::ExtendableItem*, bool (*)(ept::ExtendableItem const*, ept::ExtendableItem const*), std::allocator<ept::ExtendableItem*> >::insert (this=0x83370d0, __position=
        {<std::_Rb_tree_base_iterator> = {_M_node = 0x857fcf0}, <No data fields>}, __x=@0xbfffe664) at stl_set.h:160
#9  0xb7cdf7ee in ept::ExtendableList::addExtender (this=0x8337030, 
    item=0x8cae360)
    at /home/mornfall/dev/libapt-front/dist/ept/ept/libept/extendablelist.cpp:45
#10 0xb7cdfba9 in ept::ExtendableItem::toggleExtender (this=0x8cae360)
    at /home/mornfall/dev/libapt-front/dist/ept/ept/libept/extendablelist.cpp:93
#11 0xb7cdf95b in ept::ExtendableList::processClick (this=0x8337030, 
    it=0x8cae360, pt=@0xbfffe8e0, c=0)
    at /home/mornfall/dev/libapt-front/dist/ept/ept/libept/extendablelist.cpp:65
#12 0xb7d3cd45 in ept::ExtendableList::qt_invoke (this=0x8337030, _id=110, 
    _o=0xbfffe800) at extendablelist.moc.cpp:114
#13 0xb7d0114d in ept::Lister::qt_invoke (this=0x8337030, _id=110, 
    _o=0xbfffe800) at lister.moc:159
#14 0xb6b9d067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#15 0xb6ec9655 in QListView::clicked () from /usr/lib/libqt-mt.so.3
#16 0xb6c78c17 in QListView::contentsMouseReleaseEventEx ()
   from /usr/lib/libqt-mt.so.3
#17 0xb6c78936 in QListView::contentsMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#18 0xb742c2e3 in KListView::contentsMouseReleaseEvent ()
   from /usr/lib/libkdeui.so.4
#19 0xb6ca70fc in QScrollView::viewportMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#20 0xb6ca6a10 in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#21 0xb6c77338 in QListView::eventFilter () from /usr/lib/libqt-mt.so.3
#22 0xb6b9ab01 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#23 0xb6b9aa5d in QObject::event () from /usr/lib/libqt-mt.so.3
#24 0xb6bd076f in QWidget::event () from /usr/lib/libqt-mt.so.3
#25 0xb6b45370 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#26 0xb6b44ac7 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#27 0xb714fab5 in KApplication::notify () from /usr/lib/libkdecore.so.4
#28 0xb6ade12f in QETWidget::translateMouseEvent () from /usr/lib/libqt-mt.so.3
#29 0xb6adbe1c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#30 0xb6af1ec2 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#31 0xb6b5674c in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#32 0xb6b5660e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#33 0xb6b4557b in QApplication::exec () from /usr/lib/libqt-mt.so.3
#34 0x08071115 in main (argc=1, argv=0xbffff7e4)
    at /home/mornfall/dev/libapt-front/dist/ept/ept/manager/main.cpp:49

```

---

### Post by mornfall on 2005-09-07
I have added a bugs.kde.org entry so you can report things there now. The crash is fixed in svn, the second beta should have the fix, consequently.

---

### Post by Maikun on 2005-09-07
Great!

I think the second beta will already be very usable. Looking foward to it.

Mike

---

### Post by mornfall on 2005-09-07
Just a small update, issues fixed in svn:
- The icons used are not very suitable when crystal icon theme is used. Should ship the nuvola icons, seen in screeshots below.
- Preview on/off messes up filters layout.
- No preview icon.
- Commit changes should be disabled if there are no changes marked
- The quick filter should be case-insensitive.
- The Kmenu entries don't sudo

About updater and state filter, i may remove it by default, but it is pretty useful with big upgrades (want to see which packages are going to disappear? what new stuff will be installed, etc... consider that eg i casually do updates of hundreds of packages in one go).

About showing details versus selecting, i think i will see how it works with open-on-click, it may as well end up being usable (given i manage to have it not open things when trying to select, like with drag or shift/ctrl).

---

### Post by Maikun on 2005-09-08
I think it's great that you'er open to discuss everything with us. I'll check the second beta as soon as you release it and will give again my feedback.

Happy coding! ;-)

---

### Post by Runico on 2005-10-07
Are the dependencies marked as automatically installed like aptitude does? I don't used kynaptic to install because when I uninstalled a program didn't remove automatically its dependencies if no program needs them.

---

### Post by edrex on 2005-10-07
Yay non-heirarchical UI!

KDE 3.5 is making real steps in this direction (with Kubuntu leading the way), and of course 4 should be a bombshell. 

I think Adept is a very well architected app, and I'm using it more and more. When I run back to Synaptic, it is because I want more information about a package. Things which adept should eventually expose (without breaking the elegance of the UI:
[LIST]
[*][Suggested,Recommended,Required] for a package could be implemented as an additional search field, also accessible via hyperlinks in the package description
[*]Reverse dependancies
[*]Installed files list would be nice, but it's not clear how it would fit into the current layout. Maybe a popup?
[/LIST]
Anyway, these are by no means critical features, and I'm very happy with the app as it stands.

Eric D

---

### Post by mlomker on 2005-10-07
> Note for hoary users: installing adept alpha will upgrade your apt (and aptitude). That shouldn't be a problem, but you better know.


I just installed it on a test box and poked around a bit.  There are already things that I like about it over Synaptic (and that's saying something when compared to Kynaptic).  The main interface seems a little 'busy' to me as far as the search filters are concerned...many KDE users are Windows converts and the less confusing the interface is the better.

I see that the update applet is separate.  Is the intention to eventually have a task-tray icon that'll notify users when there are updates (like gnome users have)?  That'll be fantastic.

---

### Post by gflores on 2005-10-07
Is Adept going to be ready for 5.10? Isn't it alpha software?

---

### Post by mlomker on 2005-10-07
> Is Adept going to be ready for 5.10? Isn't it alpha software?

No, but it is listed as beta 2 on the website.

---

### Post by Hobbsee on 2005-10-08
it's already in kubuntu 5.10 and seems to work just fine :)

An icon in the taskbar would be cool though, to know when to update our machines though - seconding an earlier request

---

### Post by mlomker on 2005-10-08
[QUOTE=Hobbsee]it's already in kubuntu 5.10 and seems to work just fine :)
[/QUOTE]

You're right...I just hadn't noticed it in my menu.

---

### Post by mlomker on 2005-10-09
I should warn anyone installing Adept on Hoary that it breaks a number of other packages related to apt.  

For example, I love to use apt-file but now it can't be installed or used.

---

### Post by stimpack on 2005-10-09
[QUOTE=mlomker]I see that the update applet is separate.  Is the intention to eventually have a task-tray icon that'll notify users when there are updates (like gnome users have)?  That'll be fantastic.[/QUOTE]

I hope so, but hopefully it wont have Gnomes annoying windowsesque giant popup reminders, simple taskbar icon changing colour would be great. And if you could set it only to notify security updates that would be amazing.

---

### Post by olwin on 2005-10-09
has it a *.po files (for translation) ? i can't find it in Rosetta ?

---

### Post by Hobbsee on 2005-10-10
hehe...

It was clearly hidden for you, until I mentioned it.

It's this whole idea of predictable menus you know :P

---

