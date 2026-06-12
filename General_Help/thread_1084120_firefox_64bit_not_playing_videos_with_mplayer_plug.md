---
title: "firefox 64bit not playing videos with mplayer plugin"
date: 2009-03-01
forum: General Help
---

### Post by arch0njw on 2009-03-01
For example, this site:
[http://www.goyk.com/video.asp?path=1502](http://www.goyk.com/video.asp?path=1502)

The video does not play for me.  But if I use the URL to the wmv I can make it play in mplayer:
mplayer [http://www2.goyk.com/aw333sas0903/videos/bud_light_commercial_5.wmv](http://www2.goyk.com/aw333sas0903/videos/bud_light_commercial_5.wmv)

Help?  This used to work for me.  I've been lazy and not followed-up on this for a long time.  Recently it has started annoying me.  Help would be appreciated.  I have tried many things including removing everything I can think of related to firefox and reinstalling -- including removing firefox2 and installing firefox3.

---

### Post by miegiel on 2009-03-01
It plays for me, but i don't get any audio (probably because mplayer is trying to use alsa instead of pulse). Do you have the mozilla-mplayer package installed?

edit: The sound was working, mplayer just couldn't hijack it from gmusicbrowser :D

---

### Post by arch0njw on 2009-03-02
Indeed I do have that package installed.

---

### Post by miegiel on 2009-03-02
Maybe you're missing codecs. Check [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) on how to ad them (unless you already have those too).

I skimmed the site's source, as far as I could tell it's just java and some microsoft media formats.

---

### Post by arch0njw on 2009-03-05
miegiel:  alas, that did not work.  :-(

Thanks for the suggestion!

---

### Post by arch0njw on 2009-08-10
> **arch0njw said:**
> miegiel:  alas, that did not work.  :-(

Thanks for the suggestion!

My solution to this was to install totem-mozilla and supporting packages.  I actually like the way totem works better in this case because it scales the video to the window size.  Pretty neat!!!

---

### Post by Arup on 2009-08-10
I use Greasemonkey script for playing via mplayer plugin with FF, it works out very well and plays back movies in HQ with minimal CPU usage compared to Flashplayer.

---

