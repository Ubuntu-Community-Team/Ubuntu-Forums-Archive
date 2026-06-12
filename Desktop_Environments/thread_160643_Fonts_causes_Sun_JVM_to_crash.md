---
title: "Fonts causes Sun JVM to crash"
date: 2006-04-15
forum: Desktop Environments
---

### Post by shadowfox on 2006-04-15
**Problem 1:**

Sun JVM: 1.5.0_06
Crashes when trying to display certain fonts.
I found out that the font it's crashing on is Saab, which is part of ttf-punjabi-fonts package.

**Problem 2:**

Then I realize that I cannot remove font packages without removing <gasp> **ubuntu-desktop**.

**Mega-huge-problem 3:**

What???? why can't I remove packages for fonts that I would never use like punjabi-fonts, gujarati, bengali, tamil, telugu, etc.   ](*,) 

**Very-annoying-and-unprofessional-problem 4:**

So I am now stuck with font(s) that cripples java programs that I use to work daily because I can't remove it without removing ubuntu-desktop itself.  This is a very odd way to spread the usage of Ubuntu among professional *humans*.  Indeed it is! :-k

Please tell me someone knows how to resolve this...

---

### Post by oscar on 2006-04-15
ubuntu-desktop is a meta package, it doesn't actually contain anything, it is just dependent on many other apps. You can remove it without uninstalling the desktop. However someone on these forums pointed out that it is good to have it when updating because it may depend on new packages that you would not receive unless you have ubuntu-desktop installed.

---

### Post by shadowfox on 2006-04-15
Thanks oscar for the explanation.

I went ahead and uninstall a bunch of indic ttf fonts, the one that messes up the JVM is font called Rekha from the ttf-gujarati-fonts package.

I am not the only one with this problem, of course, I found two programs that helped me figure out the offending font.

One from [here]("http://support.jetbrains.com/kb/entry!default.jspa?categoryID=4&externalID=172&fromSearchPage=true")
which will list the fonts that your JVM can see in order.

The other one from [here]("http://www.intellij.net/forums/thread.jspa?forumID=27&threadID=189420") (use the code in post: 62) which reproduce the JVM crash.  The offending font is the last one listed *before* the crash.

Hope this helps other poor souls who are scratching their head when their java programs suddenly crashes with this message:

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1c9aef6, pid=23772, tid=2980801456
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x31ef6]
#
# An error report file with more information is saved as hs_err_pid23772.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

And no, I won't submit this bug to Sun, they already know about it.

One thing still stands, though, why does Ubuntu install *by default* every known open source fonts out there regardless the locale settings?

I live in the US, if let's say I want to read a document written by my buddy from Punjab, I will then install the punjabi fonts, but don't clutter the *default* installation with gazillions of fonts from all corners of the world.

Aside from this, I am eagerly waiting for Dapper release.  Rock on guys!

---

### Post by miggy99 on 2007-01-30
ok, sorry i chimmed in so late, but i just figured i'd let you know what i did in my swing app. Anyhow, i'd rather have my apps display only the "safe" fonts, so to do that, i did the following:

```

Font font = new Font(f, Font.PLAIN, 20);
if(font.canDisplayUpTo(f.getFamily()) == -1)
   // if it's ok, then display it 
}

```

The "canDisplayUpTo() method return a "-1" if the font can display a string you pass in. In the example above, i pass in the family name of the font.

Hope this helps :)

~miggy

---

