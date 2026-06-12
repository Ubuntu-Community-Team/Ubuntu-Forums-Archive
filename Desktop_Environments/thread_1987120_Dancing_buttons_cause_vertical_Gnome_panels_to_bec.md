---
title: "Dancing buttons cause vertical Gnome panels to become useless"
date: 2012-05-25
forum: Desktop Environments
---

### Post by rocksockdoc on 2012-05-25
I had this problem with Ubuntu and on another machine I have the SAME problem with CentOS so I figured I'd let others know that vertical Gnome panels are essentially useless.

The bug, which makes Gnome panels useless when used verticdally is going on its ten year anniversary come June 24th of this year - so most of you will have seen it by now if you try to efficiently use real estate on your monitor.

Note: If you don't care to be efficient with real estate, you might never even notice this bug because you're probably using Top or Bottom panels and not side panels.

Here's the bug if you're interested:
- [**Bug 86382**]("https://bugzilla.gnome.org/show_bug.cgi?id=86382") -        [Fix window list on vertical panels (with possible rotation)](https://bugzilla.gnome.org/show_bug.cgi?id=86382#c0)

[Here's my append to that bug report:](https://bugzilla.gnome.org/show_bug.cgi?id=86382#c178)
SUMMARY: This bug makes vertical button panels almost totally useless, if not wholly useless. The disadvantage of the workaround is that precious screen space is wasted.  DETAILS: Depending on the screen resolution & width of the vertical panel, you generally get about 7 or so running programs before WHAM! The buttons dance about 3 or 4 times a second such that you can't possibly open up another window without clicking again and again and again, like an idiot - which for the most part, does nothing.   The dancing buttons apparently happens, as explained in this bug, whenever a new column is started, which depends on the width setting of the panel and the number and name of the running programs.   This youtube video set shows how easily the bug is reproduced: [http://youtu.be/NczFOlvaR9A](http://youtu.be/NczFOlvaR9A) [http://youtu.be/wdwaVfu2HHk](http://youtu.be/wdwaVfu2HHk)  You might say "just put your panels on the top or bottom"; but that's a lousy workaround.   The REASON it matters greatly to have panels on the sides of your monitor is because the most precious real estate is the top:down direction (especially on HD monitors such as that on the Lenovo W510 laptop, 1920x1080).   So, from a logical standpoint, it wastes precious top:bottom real estate to put the panel on the top or bottom (which is the only practical location given this bug which makes the sides useless). Then you're forced to autohide, which in and of itself is an obnoxious setting due to the time-wasting lag - but at least with this sub optimal workaround, the panel can be utilized.

---

