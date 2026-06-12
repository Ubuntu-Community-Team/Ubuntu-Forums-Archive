---
title: "Patching wine."
date: 2007-06-14
forum: Gaming &amp; Leisure
---

### Post by domat00 on 2007-06-14
I've got the version of Wine I need to patch, and the patch itself:  now, what the crap am I supposed to do with them?  :p

Overview:  I've been working my tail off trying to get Call of Duty 2 installed, Googling for wiki's about patching wine, and I've come up with squat.  So, I'm hoping that the entire Ubuntu community can come up with an answer that eludes me.

---

### Post by mocqueanh on 2007-06-14
Search Google for Winetools, Sidenet.

(I dont remember exactly) because i dont use Wine.

This is Gaming section, Wine is often used for install Windows apps on Linux, Windows games is Windows apps, of course. But game is "particular app", usually take all your Windows screen to play, this is a reason why use Wine to play Windows game in Linux is not best method.

**** Comment removed, reason : NO PIRACY PLEASE ****

---

### Post by hikaricore on 2007-06-14
> **mocqueanh said:**
> Search Google for Winetools, Sidenet.

(I dont remember exactly) because i dont use Wine.

This is Gaming section, Wine is often used for install Windows apps on Linux, Windows games is Windows apps, of course. But game is "particular app", usually take all your Windows screen to play, this is a reason why use Wine to play Windows game in Linux is not best method.

Cedega is a program for playing Windows game in Linux, i have it, do you want a copy of it ?

Hi I'm not sure if you even bothered reading the OPs issue judging from your response.  Seriously what?

------------------------------------------------------------------------------------

@domat00:  You might find some info here: [http://appdb.winehq.org/appview.php?iVersionId=3794](http://appdb.winehq.org/appview.php?iVersionId=3794)

Though you may be able to skip this whole process based on a quote from that very page:
[QUOTE=Warren Dumortier@Wine Application DB]Hi!

Today I tried the latest version of Wine ( 0.9.38 ) and I see that you don't have to patch anymore and that the game is very smooth like Windows except when there are a lot of animations in a combat...

But there's still a sound problem[/QUOTE]

So there you have it, it may work except for sound unpatched.  My original reply follows:

----------------------------------------------------------------------------------------------

Make sure you have the source to the version of wine you're using and not a debian/ubuntu package.

You will have to extract this source, then patch it, and finally compile / install it.

patching info: [http://www.linuxforums.org/applications/using_diff_and_patch.html](http://www.linuxforums.org/applications/using_diff_and_patch.html)
this might be better compile info than the first one I posted which is below this line: [http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)
compile info: [http://www.aboutdebian.com/compile.htm](http://www.aboutdebian.com/compile.htm)

Sorry for the random non-Ubuntu info links, it's late and I'm tired. >.<

Just trying to find you the best info I can in the time I have.

---

### Post by domat00 on 2007-06-14
That's probably the best response I've ever gotten in a forum (true...).  Thanks!  But I've tried 0.9.38...  That's why I've turned to the forums, because I can't make heads or tales of the AppDB section at WineHQ.  Thanks, I'll try and go through the patching.  Well, I guess I oughta just ask this:  How can I change my permissions to allow me to access a second disk?  If I could somehow access the other 5 discs in the package, I could just copy them all into a single folder and install from there and I wouldn't have this problem.  Thanks again.

---

### Post by hikaricore on 2007-06-14
Sorry for the delay, long day here.  >.<

Probably your best bet would be to copy all of the discs to a folder on your desktop or something and run the install from there.

WINE and Linux in general are really picky about ejecting/unmounting a CD which is currently in use. :(

---

### Post by domat00 on 2007-06-14
I tried to copy from the discs to a folder on my desktop, but I get an insufficient privileges error and I have absolutely no idea how to alter the permissions...  Got a command I can type?  :p

---

### Post by hikaricore on 2007-06-14
Hmm... that's really strange.

You can try it from command line if needed.
This assumes your cd is located at /media/cdrom

```
cd /media/cdrom

cp * -R ~/Desktop/Foldername
```

Where Foldername is the name of the directory you're copying to.

If this gives you an error I'm not sure.
There are a few possibilities such as copy protection on the cds (which I doubt) or for some reason your user doesn't have CD read privileges (which I doubt).

Failing this you could also try it with **sudo**:

```
cd /media/cdrom

sudo cp * -R ~/Desktop/Foldername
```

---

