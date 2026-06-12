---
title: "Compiz, Wine: No title bars"
date: 2006-06-10
forum: Desktop Environments
---

### Post by porchcth on 2006-06-10
Dear Community,

I've recently installed Xgl and Compiz.
Everything works perfectly, except the Wine applications. I don't get any title bar on the Wine applications (e.g. Picasa).
I guess it has something to do with the gnome-window-decorator. Are there any options that I missed to set?

Thanks!

porch.

---

### Post by matt221984 on 2006-06-11
I am also having this problem. I'm using ubuntu 6.06 AMD64, Xgl and Compiz. Wine applications have no borders or title bars. If I run metacity --replace & in the terminal it switches back to the non-compiz window decoration and everything is ok, but I would like to get compiz working on wine.

any tips?

---

### Post by simianstyle on 2007-08-17
this is happening to me as well, are there any suggestions as to how to solve this? I'm running compiz-fusion and using emerald as my window manager.

---

### Post by staib on 2007-08-19
Ditto here - compiz fusion is great but picasa won't play - naughty picasa!

---

### Post by z0phi3l on 2007-08-19
Have you enabled Workarounds?

---

### Post by soaro77 on 2007-09-26
I am having this same problem. I do have Workarounds enabled and still no title bars on my wine applications.

Actually it appears it isn't all wine applications, only some. I got this primarily when running WoW. But I just tried Quicken and it is working fine. So I'm not sure what the difference is.

---

### Post by TRDownShift on 2007-09-29
same deal for me, runing ubuntu 7.04 with compiz-fusion and emerald, and i got no boreders on wine, well some, it runs fine with say IE6 (only started it to test >.>) but if i try stepmania i dont get any borders T.T someone help us!

i think looking the way of the games may help, soaro, you sed you get it wen you run WoW, but it works fine with Quicken, so then normal app's seem to run but anything that, oh boy, dont know how to put this... T.T ahh, it's games and game like things, i think you guys see where im going lol

---

### Post by TRDownShift on 2007-10-02
alright, i found a "workaround" a bad one at that but you get title bars so be happy lol

go to the Terminal and type in "winecfg" then go to graphics, and check the box for Emulate a virtual desktop. i set mine to 1280x960 becus i run my desktop at 1600x1200, that way the wine desktop holds anything i want to run, say wen you start your game set it to full screen and the wine desktop title bar becomes the games title bar. 

now to move your mouse away from the game you have to use the Alt+Esc command.

i know, it's not the best fix but this way we atlest get working title bars.... although they only have the close button.... -.- sorry... still new to linux, this was the best i could come up with T.T

---

### Post by idkwot on 2007-10-02
picasa stopped working for me also

---

### Post by Motorhead Kaze on 2007-10-04
I hope this is related:  I installed Compiz yesterday and Emerald and after starting Compiz up, I lost ALL title bars, and an error message talking about Wine.  I wasn't using any Wine related anything.  I tried to open a Terminal, and it was pure white, no words at all!

I just restarted Metacity and got the hell out.

---

### Post by juamez. on 2007-11-06
Also have the single problem of having no title bars for wine applications when using compiz (by checking Desktop Effects) which can be resolved by emulating a desktop. But I don't want to use this emulated desktop for things like steam or DVDFab HD Decrypter or whatever has it's own built-in titlebar. The windows without titlebar are also not seen as windows in the window manager, so I cant handle them like regular windows, i.e. resizing or moving them does not work, also they stay on top of everything, which is quite annoying.

Maybe I'm to fiddle around with compiz manager a little more. 

But in the meantime, if somebody finds a fix for this: please post, kthx.

---

