---
title: "Resetting KNetWalk high scores"
date: 2012-04-18
forum: Gaming &amp; Leisure
---

### Post by Andrew_P on 2012-04-18
This is a comment on [Thread #299058]("http://ubuntuforums.org/showthread.php?t=299058"), which was inexplicably locked before the question was answered.  The question by kitpierce on November 13, 2006 was "Just wondering how one would go about resetting the high scores for KDE games."

Here's the answer:
If you've installed KNetWalk on GNOME from Ubuntu Software Center, as I did, the file that contains the high scores is ~/.kde/share/config/knetwalkrc.  Open it with a text editor such as gedit and delete all entries in the highscore section of the selected difficulty level, for example everything below "[KHighscore_Medium]".

---

