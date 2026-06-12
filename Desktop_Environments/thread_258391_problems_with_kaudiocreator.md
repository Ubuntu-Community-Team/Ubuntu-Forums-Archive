---
title: "problems with kaudiocreator"
date: 2006-09-15
forum: Desktop Environments
---

### Post by charles.figura on 2006-09-15
I'm running dapper on a dell620, and I've been having problems with kaudiocreator.  When I try to rip tracks from a cd, the job list sits there, but no progress is made.  If I start kaudiocreator from terminal, I get an infinite number of the following error message:
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (373)

I found a page listing fixes to a
[http://websvn.kde.org/trunk/KDE/kdemultimedia/kioslave/audiocd/audiocd.cpp/](http://websvn.kde.org/trunk/KDE/kdemultimedia/kioslave/audiocd/audiocd.cpp/)
> Filename: trunk/kdemultimedia/kioslave/audiocd/audiocd.cpp
Revision 325598 - (view) (download) (as text) - [select for diffs]
Modified Sat Jul 3 19:36:10 2004 UTC (2 years, 2 months ago) by woebbe
File length: 31471 byte(s)
Diff to previous 325141

Keep the lists track_titles and templateTitles in sync.

This fixes initRequest(): sometimes the file name wasn't found because
the list templateTitles was empty. It was the reason for

ASSERT: "i <= nodes" in /src/kde/qt-copy/include/qvaluelist.h

seems vaguely relevant, but that fix was over two years ago.

Has anyone else had this problem?  kaudiocreator used to work for me - I'm not sure when it first failed, but it must be at least one update ago.  Current version of kaudiocreator is 1.13.

Thanks for any possible clues -
-C

---

