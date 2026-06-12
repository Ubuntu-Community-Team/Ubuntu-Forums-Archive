---
title: "YouTube broken in Konqueror 4.3.2?"
date: 2009-10-08
forum: Desktop Environments
---

### Post by jtappin on 2009-10-08
Since updating my KDE installation from KDE 4.3.1 to 4.3.2 from the PPA repositories (Jaunty) on two machines, YouTube videos no longer play, though other flash videos (e.g. BBC news) do work.

Has anyone else seen this? Are there any known fixes?

[I've not yet had a chance to check the state on my Karmic machine]

---

### Post by Lars Noodén on 2009-10-09
A short term solution will just have to be repeated every few months.  A long term solution means that sites should use open standards for video as they have for other web components.  

That can be done by patronizing sites that support open standards and getting those that don't to start / resume using open video standards. 

Here are some places to look
[list]
[*] [http://thevideobay.org/](http://thevideobay.org/)
[*] [http://dailymotion.com/](http://dailymotion.com/)
[*] [http://commons.wikimedia.org/](http://commons.wikimedia.org/)
[*] [http://www.archive.org/create/](http://www.archive.org/create/)
[/list]

---

### Post by jtappin on 2009-10-09
> **jtappin said:**
> [I've not yet had a chance to check the state on my Karmic machine]

I have now done that check and I find that the problem is present there as well. 

Since the videos play OK on arora, it has to be somewhere in the interaction between konqueror and the flash plugin (which is listed in the plugins). I know the flash plugin in konqueror is a pain[*], but why is it only YouTube that won't work?

[*] I recall an issue a while back where V10 would work fine on an old system, but not on a new one -- and the fix was to install V9 first.

---

### Post by tpapastylianou on 2009-11-09
I'm getting a similar problem, but in firefox under ubuntu (not kubuntu). Sometimes it just doesn't play and there's just a grey or white screen where the video should be; if I restart firefox it plays sometimes after a small delay at the grey screen, but you don't have any control over the video window itself (i.e. you can't pause, close the advertisement popup, move the slider, select a next video from the video window etc)

I don't know if anyone's submitted a bug for this yet, but I haven't seen anything relevant from a simple google search (other than this post :p).

---

