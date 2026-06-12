---
title: "Krusader crashes"
date: 2005-10-20
forum: Desktop Environments
---

### Post by johanPO on 2005-10-20
On my breezy, I have installed Krusader. Don't ask me why but I quite simply like Krusader and it was working fine under Hoary so I got used to it. Now I have upgraded to Breezy, and if I understand correctly also Krusader has been upgraded. It is working fine until I try to sort the files after the size (by clicking on size), then Krusader crashes and gives me the KDE Crash handler, stating that Krusader has crashed and caused the signal 11 (SIGSEGV).

attached the relevant(?) parts of the backtrace 

Has anyone experianced something similar? Greatful for any hints!




(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1236060480 (LWP 19744)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#4  0x0811ed09 in QStrList::~QStrList ()
#5  0xb6e105f5 in QListViewPrivate::SortableItem::cmp ()
   from /usr/lib/libqt-mt.so.3
#6  0xb6e1069a in QListViewPrivate::SortableItem::operator< ()
   from /usr/lib/libqt-mt.so.3
#7  0xb6e1183b in qHeapSortHelper<QListViewPrivate::SortableItem*, QListViewPrivate::SortableItem> () from /usr/lib/libqt-mt.so.3
#8  0xb6e1198a in qHeapSort<QListViewPrivate::SortableItem*> ()
   from /usr/lib/libqt-mt.so.3
#9  0xb6e0daa9 in QListViewItem::sortChildItems () from /usr/lib/libqt-mt.so.3
#10 0xb6df9204 in QListViewItem::enforceSortOrder ()
   from /usr/lib/libqt-mt.so.3
#11 0xb6df843d in QListView::firstChild () from /usr/lib/libqt-mt.so.3
#12 0xb758adcd in KListView::setSorting () from /usr/lib/libkdeui.so.4
#13 0xb6dfac2e in QListView::changeSortColumn () from /usr/lib/libqt-mt.so.3
#14 0xb707f32d in QListView::qt_invoke () from /usr/lib/libqt-mt.so.3
#15 0xb760c4dd in KListView::qt_invoke () from /usr/lib/libkdeui.so.4
#16 0x08123430 in QStrList::~QStrList ()
#17 0xb6d08929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb6d09238 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#19 0xb7077d66 in QHeader::sectionClicked () from /usr/lib/libqt-mt.so.3
#20 0xb6dd0a0c in QHeader::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#21 0xb6d43356 in QWidget::event () from /usr/lib/libqt-mt.so.3
#22 0xb6c9ff80 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#23 0xb6ca0500 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#24 0xb73dae37 in KApplication::notify () from /usr/lib/libkdecore.so.4
#25 0xb6c30e25 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#26 0xb6c2c325 in QETWidget::translateMouseEvent () from /usr/lib/libqt-mt.so.3
#27 0xb6c2a66f in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#28 0xb6c43fff in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#29 0xb6cb7cfb in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#30 0xb6cb7c1e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#31 0xb6c9ec13 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#32 0x0808189e in QMapPrivate<QString, QString>::QMapPrivate ()
#33 0xb657dea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#34 0x0807b531 in ?? ()

---

### Post by flibble on 2005-10-28
Same for me. Krusader is basically unusable under breezy *if* I have it set to sort by name. If I set it to sort by 'Modified' (the date a file was modified) it works fine...

Hope this helps

---

### Post by johanPO on 2005-10-29
Odd, for me all other sort possobilities are working. Sort by name is working for me, only thing that does not is size.

There seems to be a few stability issues when using KDE apps under GNOME. Kaffeine seems to shut down improperly, causing it to belive that it is  the first time it is started every time....

---

### Post by krojc on 2005-11-18
I do remember these crashes. You're talking about 1.60.0, right. You should upgrade to 1.70.0-beta from their webpage until the 1.70.0 gets out. There is a unofficial deb built just for ubuntu. As I remember it had todo something with some libs, which was fixed.

I now run krusader under GNOME just fine. Maybe someone should put a bounty on the krusader port to gnome :)

---

### Post by johanPO on 2005-11-19
Thanks,

Works out nicely.  I had to install libkjsembed1, and then the kde package

---

### Post by ijanos on 2006-01-10
[Howto build stable krusader](http://ubuntuforums.org/showthread.php?p=644330#post644330)

---

### Post by Copter on 2006-02-10
hi!

had the same problem on kubuntu breezy. i folowed this link [http://krusader.sourceforge.net/down.php#development]("http://krusader.sourceforge.net/down.php#development") and downloaded beta2 ubuntu package. than istalled (like johnanPO said) libkjsembed1.```
sudo dpkg -i krusader_1.70.0-beta2-0ubuntu0_i386.deb
```new krusader is **really faster** than 1.60. it is worth checking out. as i can see it crasher less than stable 1.60 on my system :]

copter

---

