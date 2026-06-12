---
title: "Cannot input Chinese, even when iBus or fcitx is on"
date: 2015-11-03
forum: Desktop Environments
---

### Post by MMarauder on 2015-11-03
Hi all, 

I just installed Xubuntu 15.10. Sadly I found that I cannot use any input method. Neither iBus nor fcitx will start automatically. Even if manually started, neither would show me a Chinese Pinyin input interface--I can only input Latin letters when switching to Pinyin method. Plus, neither iBus and fcitx would start automatically.

---

### Post by bing_bai on 2016-06-05
I have the same problem. My is update to ubuntu 16.04. Non of the chinese input method is working including pinyin, sunpinyin, sogopinyin, libpinyin. IBUS is properly installed. something is wrong and looks like a bug or something. someone could help.

---

### Post by ping-wu on 2016-06-05
> **bing_bai said:**
> I have the same problem. My is update to ubuntu 16.04. Non of the chinese input method is working including pinyin, sunpinyin, sogopinyin, libpinyin. IBUS is properly installed. something is wrong and looks like a bug or something. someone could help.

I am running Ubuntu 1604 and ibus-pinyin works great.  &#25105;&#30446;&#21069;&#27491;&#22312;&#20351;&#29992;Ubuntu 16.04, ibus-&#25340;&#38899;&#19968;&#28857;&#38382;&#39064;&#20063;&#27809;&#26377;&#12290;

Kind of busy right now.  Will get back to you soon.  This is a very important issue for wanna-be Ubuntu users who have a need to input Chinese characters.

---

### Post by ping-wu on 2016-06-05
> **ping-wu said:**
> I am running Ubuntu 1604 and ibus-pinyin works great.  &#25105;&#30446;&#21069;&#27491;&#22312;&#20351;&#29992;Ubuntu 16.04, ibus-&#25340;&#38899;&#19968;&#28857;&#38382;&#39064;&#20063;&#27809;&#26377;&#12290;

Kind of busy right now.  Will get back to you soon.  This is a very important issue for wanna-be Ubuntu users who have a need to input Chinese characters.

As a quick fix, to input Chinese characters a Ubuntu user needs to apt-get the following three packages from Ubuntu repository:

[COLOR=#000000][FONT=&quot]sudo apt-get install ibus-pinyin ibus-libpinyin pinyin-database

For those who can read Chinese and are interested in additional info, please read my comments at the Ubuntu Chinese forum:

[/FONT][/COLOR]http://forum.ubuntu.org.cn/viewtopic.php?f=8&t=473743&start=16

and

[http://forum.ubuntu.org.cn/viewtopic.php?f=48&t=476647](http://forum.ubuntu.org.cn/viewtopic.php?f=48&t=476647)

Basically, Ubuntu Kylin has taken over control of the development of the Chinese locale of Ubuntu.  Because its main goal is to promote proprietary software, including the Sogou-pinyin method, the WPS office suite, and the now-defunct Kylin cloud storage, the whole thing really sucks.  I didn't realize this until after two years of active participation in the Ubuntu Kylin development.  This was totally unbelievable.

As I mentioned in a separate thread:

[http://ubuntuforums.org/showthread.php?t=2326509](http://ubuntuforums.org/showthread.php?t=2326509)

We are actively pursuing the development of a live Ubuntu USB so that those of us who have a need to use Chinese in Ubuntu can hope to have an alternative which more closely follows the Ubuntu main stream (especially with regard to the ibus input method and LibreOffice).

---

