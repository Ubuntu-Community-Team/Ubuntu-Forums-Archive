---
title: "cannot come back from tty with ctrl+alt+f7"
date: 2006-07-09
forum: Desktop Environments
---

### Post by sup on 2006-07-09
Hello, when I press ctrl+alt+F1, a console with login gets on the screen, so so far, so good. I am able to do my stuff there, but then I am struggling to get back to x. As far as I understand, ctrl+alt+F7 should switch to console where X are running, but that is not happening (nothing is happening after I pres ctrl+alt+F7 actually), so I usually have to use something like /etc/init.d/gdm/restart which is not very nice for I must restart every application that was running and so on.
Anybody got a clue what the problem might be in?
Also, I am using laptop with ATI graphic, proprietary drivers (8.26.18), if that matters.

I tried some more experimenting and it seems that either of alt+ctrl+f1-f6 sends me to corresponding tty, but after that, I cannot switch between them (nor can I get to X). when I press F1-F6 in console, ABCDE~ is printed (F1 - A, F6 - ~ etc).  Is that expected behaviour?

---

### Post by parkash on 2006-07-09
Do all your consoles work ok?

I mean, when you do Alt+F1, F2, F3,...,F6?  And then Alt+F7 is the only one wrong?

hmm... Because if so... That IS a bit strange...  You do not happen to have your x on other console right?

---

### Post by sup on 2006-07-09
As I wrote in my edit, they work when I want to swith into them from X (so obvioulsy after pressing alt+ctr+f7 in X nothing happens, but it does not mean the console does not work), but as soon as I get into them, none of them seems to work.

---

### Post by parkash on 2006-07-09
Oops, I didn't see that part of your post before :p...  Anyway, sorry, that's never happened to me before.  Though I've read similar problems with proprietary drivers... :s

---

### Post by sup on 2006-07-09
well, without proprietary drivers, I cannot even play videos smoothly, so it is something I just muset use.

---

### Post by macuser9214 on 2007-09-10
I'm having this problem too.. I can't go back into X, after doing some work in the consoles...

I'm on a HP 533W with no additional addons (except wireless)

---

