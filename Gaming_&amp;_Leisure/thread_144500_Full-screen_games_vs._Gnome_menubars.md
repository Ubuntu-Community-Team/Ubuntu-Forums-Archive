---
title: "Full-screen games vs. Gnome menubars"
date: 2006-03-14
forum: Gaming &amp; Leisure
---

### Post by AskHL on 2006-03-14
Greetings.

I use wine to play Warcraft 3: Frozen Throne, and mostly it works perfectly. However there is one problem so serious that I am surprised I cannot find it in the forums already.

(note: it was out there somewhere, see the below post!)

If I multitask from WC3, the Gnome panels in the top and bottom of the screen will become visible. When I task back to WC3, they will sometimes disappear and the game will continue as it should. However at other occasions these panels will be visible over the WC3 window, making it impossible to scroll in certain directions, thus making the game unplayable. This appears to be irreversible - I have to restart the game completely to obtain a working interface.

Sometimes these things can happen by accident if I hit the wrong buttons, which is why it is particularly annoying. It could conveivably be triggered by background window events too (automatic updating, etc.).

One solution to this problem is to make the window manager unable to control the game window by checking a specific option from winecfg. However another problem arises: if I do the wrong thing (most likely something with multitasking, but I cannot reproduce it every time) the application will somehow lose focus and - even though it is displayed on top of everything else - not receive keyboard input. Also it is impossible to make the game receive keyboard input again once it enters this state, meaning the game is unplayable.

Now, one solution to both these problems is to install a non-Gnome window manager such as WindowMaker or similar which does not disturb the full-screen window. However it is not particularly elegant to have to log out and start another Window Manager just to play WC3. Since no one has as far as I can see asked this question before, I take it that either there exists an easy solution, or possibly that this is a very rare problem, in which case it may be relevant that I have a Radeon 9700 Mobility card in my laptop.

I have not yet detected any problem with WC3 in WindowMaker, but several of the small window managers available had some kind of way to mess up the game beyond repair which could be triggered by accident.

This problem is most likely relevant for any full-screen game. Does anyone have a solution? How do you guys run your full-screen games? Have you never seen anything like this?

---

### Post by AskHL on 2006-03-14
Why is it that I look for ages through the forum, create an account, write a long post, then immediately afterwards I find what I'm looking for?

From the World of Warcraft guide (so at least it wasn't mindnumbingly obvious):

"This is easily solved by setting a hotkey for fullscreen mode in gnome and using that hotkey when the problem arises."

Maybe this will help someone else with the same problem, who does not play World of Warcraft either.

---

### Post by kaamos on 2006-03-14
It also works to uncheck mouse grapping for directX in winecfg and use alt+tab. And you can also start games with their own xserver to save resources. So there is no need to run any WM. :)

[http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)

---

### Post by AskHL on 2006-03-15
I had considered completely avoiding a WM, but it was much too complicated. That link seems to explain things adequately though, so thank you!

---

### Post by Trullo on 2006-03-16
Did you try [devilspie]("http://www.ubuntuforums.org/showthread.php?t=75749")?

Have great! zZzzz..

---

