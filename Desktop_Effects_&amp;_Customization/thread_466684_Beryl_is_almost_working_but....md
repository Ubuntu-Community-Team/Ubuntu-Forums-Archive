---
title: "Beryl is almost working but..."
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by phollos on 2007-06-07
Brand new Linux user, excuse me if I name things incorrectly =)

background info, I'm running:
X800 ati radeon card with the fglrx drivers
XGL mode on startup

basically I can get beryl working flawlessly under two conditions:
1. opening up a terminal and typing "beryl". this starts beryl and as long as I have this window open everything is perfect. As soon as I kill it though I can no longer move windows and they lose the "_" "X" functionality.

2. opening theme preferences and keeping that window open. If I close it the window borders sometimes go white so I can't see anything.


I'm guessing to solve problem 1 is to write or edit something to start that command automatically on system startup so I don't have to leave a terminal window running all the time. Any help there?

For problem two I'm guessing there's some conflict behind what program is handling theme preferences. I have emerald installed but can't get themes working for some reason. As long as I have the theme preferences window open from normal ubuntu things stay great, as soon as I kill it, white borders start cropping up. I've seen some guides that tell me to right click on the red beryl icon and set things from a menu, but whenever I right click my beryl icon the screen goes black leaving only my mouse cursor. So I'm at a loss for what to do here...

Thanks for any help you can give on either!

---

### Post by RelativelyQuantum on 2007-06-07
I had a similar experience with Beryl. Though in my case nothing I did caused it to work properly, and I eventually wiped it from my system. In its place I use the desktop effects which come build into Feisty.

I'm not certain why Beryl has these glitches, but there are definitely ways to solve them. Many people are extremely satisfied by the program - I just wasn't one of them :)

---

### Post by phollos on 2007-06-07
I'm not thrilled with it by any means haha!

Basically I want three things:
1) An expose-like window browser
2) The cube (comes with fiesty)
3) Transparency effects

I'm mainly annoyed with the 3rd. I've set my top bar to a low opacity (20% or so) with a white color and it gives a really nice effect like it's made of glass. After seeing that the solid colored window bars just look clunky and ugly.

If I can get expose and make my windows "glassy" in some other way than beryl that is stable I'd be quite happy =)

---

### Post by RelativelyQuantum on 2007-06-07
I was able to achieve this using the built-in features:

[ATTACH]34584[/ATTACH]

Nothing glassy, but note the transparent (but colored) panels. This is also pretty cool:

[ATTACH]34583[/ATTACH]

Not certain weather that's what you mean by 'expose,' but it might be worth a try :)

---

### Post by phollos on 2007-06-07
Looks just like expose =)

In the mac OS you could press a button, think it was F12, and all your windows would scale down in size so you could see all your windows at the same time. Then you could just click the one you wanted and bring it to the front.

What did you end up using for it?

---

### Post by RelativelyQuantum on 2007-06-07
Yep - that's part of the magic of Feisty; Desktop Effects!

'System > Preferences > Desktop Effects' gives you some interesting options. Clicking the "Enable Desktop Effects" button activates the window selector. There are also options for desktop rotation and wobbly windows. Gutsy should include a slurry more, but these are pretty handy for now.

---

### Post by issueperson on 2007-06-08
> **phollos said:**
> 
basically I can get beryl working flawlessly under two conditions:
1. opening up a terminal and typing "beryl". this starts beryl and as long as I have this window open everything is perfect. As soon as I kill it though I can no longer move windows and they lose the "_" "X" functionality.


Go to System>Preferences>Sessions and on the startup programs tab click "New."  Call it whatever you want and under command enter "beryl" (no quotes and be sure it is lower case.  Linux is case sensitive).  Restart your windows manager (ctrl+alt+backspace) and it should be running, no terminal required.

---

### Post by mizzikee on 2007-06-24
Hello there, I'm a pretty new user as well but I believe I have an answer for your.  Try adding a " & " after you type beryl in the terminal.  This should cause it to continue running after you close the terminal.  Also, if you want it to run on login, go to Preferences > Sessions > Start-Up LIst.  You then simply add "beryl" to the list and you should be good to go. If you have anymore questions I'd be happy to try to help you out!

---

