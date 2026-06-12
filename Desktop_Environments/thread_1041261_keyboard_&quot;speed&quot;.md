---
title: "keyboard &quot;speed&quot;"
date: 2009-01-16
forum: Desktop Environments
---

### Post by chejose on 2009-01-16
Since I spend a lot of time at the keyboard writing, I find myself frustrated by a function that should be simple, but does not seem to work.

If I set the keyboard delay to "longest" and the speed to "slowest" I just have to touch a key and it starts repeating. The repeat function is very useful, but when I type when it is "on" I always have the problem of multiple letters in words.

So... is that a bug? The Keyboard preferences should be able to control that, but in my case, they don't do anything.

So I send my worry out with the hope that someone can give a suggestion of just tell me to forget about it.

Thanks,

José

---

### Post by walshms on 2009-02-04
I can confirm this too. I'm constantly typing over things and inserting too many characters. You wouldn't by chance have a wireless keyboard also would you?

---

### Post by mfe on 2009-02-13
I have the same problem. As I type, the characters stop appearing on the screen for a while, then all come along in a rush.  Then, I have another problem in that suddenly, I'll get a line-and-a-half of the same letter.  Doesn't matter which letter.  It's been H and it's been i and n and lots of others.  Reading suggestions in this forum, I found the repeat delay and rate sliders, but they made little difference.  Eventually I switched off the "hold key to repeat" function and that appears to have stopped the repeating letters totally.  However, I'm still getting the delay in the characters appearing on the screen. 
I have replaced the keyboard with another and it's no different.
I have run both Windows and Mandriva One on this same PC - Windows from another partition and Mandriva One from a standalone CD - but neither of those two OS exhibit the same problem.
So that makes three of us in the same boat.  I wonder if there is a switch somewhere that we haven't found yet?

---

### Post by Tom55 on 2009-04-02
I now have the same problem after installing updates two days ago.  Interesting I have two pc running Ubuntu 8.10 and only the AMD machine is affected.  I've attempted the suggested additions to the rc-local file and the xorg.conf file mentioned in other posts.  Neither worked!

Both pc's are desktops, my keyboard is USB and connected to the PS2 socket with an adapter.

Another thing that happened after the update was that the auto login now no longer works - even though it is correctly configured to do so.

---

### Post by Tom55 on 2009-04-03
Well the problem has resolved itself. I don't know why but this is what I did

1.  Turned the pc off rather than just rebooting.
2.  Had a play with some of the bios settings (I can't recall anything specific).

When I rebooted I noticed that the keyboard repeat rate at the login screen seemed OK.  So I went to the login configuration screen and noticed that the option to auto-login was unticked (yesterday it was ticked but the pc wouldn't do an auto-login).

I then went to the keyboard option and ticked the "Repeat Keys" box.

I tested the configuration by successfully typing in the bottom box.  Then I did a reboot and Ubuntu rebooted doing the auto-login and the key repeat problem has disappeared.

---

