---
title: "how to record your desktop; the simplest way"
date: 2012-05-14
forum: Desktop Environments
---

### Post by hannysabbagh on 2012-05-14
Hello, Congratulations on the new Style :)

here we will explain how to record your desktop GUI in command line in the simplest way, first you need ffmpeg package:
```
sudo apt-get install ffmpeg
```
now you can record your desktop using this command:
```
ffmpeg -an -s[COLOR=Red] 1280x800 [/COLOR]-r 25 -f x11grab -i :0.0 -vcodec&#65279; mpeg4 -sameq -y [COLOR=Red]output[/COLOR].avi
```
replace the red color Code with your settings, then Enter,you can press Ctrl + c in the terminal when you End or just close the terminal :)
thanks:KS

---

### Post by FakeOutdoorsman on 2012-05-15
The *-sameq* option should not be used when recording your screen. It does not mean "same quality". Replace it with *-qscale* with a value of 2 to 5, such as *-qscale 2*, when using *-vcodec&#65279; mpeg4*. A lower value is a higher quality.

---

### Post by chief10 on 2012-10-25
what's the best GUI app for this?

---

### Post by Sean Dewlin on 2012-10-25
I use RecordMyDesktop - you can download it via Ubuntu Software Center.

---

### Post by danielglz on 2012-11-14
Hello:

I think ffmpeg is deprecated. You have to use avconv instead. In any case, have you tried Kazam?. It is very good.

Daniel.

---

### Post by Sarys on 2012-11-14
Can I replace fraps with this? I like to make let's play videos.

---

### Post by Abhinav Kumar on 2012-11-14
Hi
Another method could be to use online sites like
Go to
[http://www.screencast-o-matic.com/](http://www.screencast-o-matic.com/)
and do the screen recording by allowing the java applet to run

Regards,
Abhinav

---

