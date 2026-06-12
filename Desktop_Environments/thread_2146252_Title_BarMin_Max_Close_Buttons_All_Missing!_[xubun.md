---
title: "Title Bar/Min Max Close Buttons All Missing! [xubuntu]"
date: 2013-05-17
forum: Desktop Environments
---

### Post by flipjarg on 2013-05-17
A bunch of keys on my keyboard were recently pressed by a cat jumping onto my keyboard in Xubuntu/XFCE4. Now every app I open has no Title bar or Minimize, Maximize & Close buttons. Also, the windows ingore the the panels on the top and bottom of the desktop. They just go right on top of them.

[LIST]
[*]Alt + Tab does not work
[*]I should have 4 virtual desktops but only one shows up.
[*]Some settings menus don't have any options in them.. they are just blank.
[*]I tried to take a screenshot but when I hit "Print Screen" nothing happened. (my clipboard is empty when I attempt to paste into gimp)
[/LIST]


 How can I fix this?

---

### Post by Toz on 2013-05-17
Open a terminal window and execute the command:
```
xfwm4 --replace &
```

Your window manager has crashed/stopped working.

---

### Post by flipjarg on 2013-05-17
That works but when I restart I have the problem again.

One thing I forgot to mention: I did uninstall Xubuntu-desktop and `xfce4-*` and purged both. Then I installed them again. The problem still persists.

---

### Post by Toz on 2013-05-17
Ok. Try deleting your saved sessions cache - this will reset the components that should be restarting.

1. Log out.
2. Go to your first tty console (Ctrl+Alt+F1)
3. Log in to the text console.
4. Enter the following commands (be careful with the "rm -rf" command):
```
cd $HOME/.cache
rm -rf sessions
```
5. Go back to the gui (Ctrl+Alt+F7)
6. Log back in.

---

### Post by flipjarg on 2013-05-17
> **Toz said:**
> Ok. Try deleting your saved sessions cache - this will reset the components that should be restarting.

1. Log out.
2. Go to your first tty console (Ctrl+Alt+F1)
3. Log in to the text console.
4. Enter the following commands (be careful with the "rm -rf" command):
```
cd $HOME/.cache
rm -rf sessions
```
5. Go back to the gui (Ctrl+Alt+F7)
6. Log back in.


Solved! Thank you for your help! After restarting everything is still fine! I had a feeling it would be a file in my `$HOME` directory.

---

### Post by cmcanulty on 2014-01-20
Oh boy I just installed xubuntu to get away from constant ubuntu troubles and now I have this and the above fixes didn't work last time I had to reinstall. This is really  dumb bug. Please someone help I don't have time for a clean reinstall

---

### Post by Toz on 2014-01-20
Open a terminal window and type in the following command:
```
xfwm4 --replace
```
...and post back any messages that show up. Do the buttons come back?

If not, did you install or are you running something like compiz?

---

### Post by cmcanulty on 2014-01-21
I have reinstalled 3 times in the last 24 hours. ubuntu used to be so good I recommended it to eveyone not it is almost unusable and I am afraid to recommend it to anyone.

---

### Post by Toz on 2014-01-21
> **cmcanulty said:**
> I have reinstalled 3 times in the last 24 hours. ubuntu used to be so good I recommended it to eveyone not it is almost unusable and I am afraid to recommend it to anyone.

Are you talking about **U**buntu or **X**ubuntu?

If Xubuntu (Xfce), is the problem with the missing buttons still there? Did the command from my previous post fix it?

Is it happening with a vanilla install? If not, what other packages do you install on the base install? Maybe one of them is leading to the corruption.

---

### Post by cmcanulty on 2014-01-21
I reinstalled again and now it is OK but what a crazy reason to have to waste a day reinstalling nothing else worked.

---

### Post by Pete_White on 2014-07-10
Thanks Toz, that worked for me. ):P
Why do these buttons cause so much trouble, had the issue for years?
I really do not understand this windows manager thing, all the variations is very confusing for us non techie types.;)
Pete

---

