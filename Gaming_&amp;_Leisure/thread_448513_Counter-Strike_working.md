---
title: "Counter-Strike working?"
date: 2007-05-19
forum: Gaming &amp; Leisure
---

### Post by wiseguy8575 on 2007-05-19
FINALLY AFTER ALL MY SEARCH FOR THE PERFECT DISTRO, I GET COUNTER STRIKE WORKING ON Kubuntu.

Unfortunately, I have no idea what I did to mess it up.  It was working the night before and the next day, when I launched Counter-Strike from Steam, I started getting a vgui.dll error.  Then I did some research and some people said that you could avoid that error if you launched Steam from winefile.

I did that and sure enough I could avoid the error however the problem now is that when I launch Counter-Strike, the game window comes up but there is no font.  I have installed the Tahoma font and as I said, before everything was working perfectly.

Any ideas as to what could have happened?

Thanks guys.

P.S. I'm talking about Counter-Strike 1.6 (if that makes a difference).

---

### Post by wiseguy8575 on 2007-05-19
Here is the output from running Steam and then launching Counter-Strike 1.6.

(The output is an attachment)

---

### Post by rolando2424 on 2007-05-19
Try this.

Go to .wine ( cd ~/.wine )
Edit the system.reg file ( gedit system.reg )

Do a search for FontSubstitutes .

Now at the end of the block of text add the following:

"Tahoma"="Times New Roman"

See if it works.

---

### Post by wiseguy8575 on 2007-05-19
Thanks for the help but that didn't work.

From my understanding, you wanted me to put

"Tahoma"="Times New Roman"

at the end of all of the text in the system.reg file right?

Any other suggestions?

---

### Post by rolando2424 on 2007-05-19
> **wiseguy8575 said:**
> Thanks for the help but that didn't work.

From my understanding, you wanted me to put

"Tahoma"="Times New Roman"

at the end of all of the text in the system.reg file right?

Any other suggestions?

Not at the end of the file.

At the end of the part where there was a FontSubstitutes .

(Search the file for it and in the end of  that section add the "Tahoma"="Times New Roman" .

---

### Post by CM Xtasy on 2007-05-19
My counter-strike 1.6 freezes with wine when im playing a game.  is there a fix?

---

### Post by wiseguy8575 on 2007-05-19
Just to let everyone know, I fixed the problem.

I ran:

```
sudo dpkg --force-all --purge wine
```

Then I reinstalled everything, installed the Tahoma fonts, and now it works!

Oh and also, don't forget to remove the .wine folder in your home directory.

---

