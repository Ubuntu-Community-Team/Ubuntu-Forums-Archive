---
title: "Desktop inverse mode colours"
date: 2010-07-20
forum: Desktop Environments
---

### Post by a_petrov303 on 2010-07-20
On 9.04/.10 Win+M would reverse the colours of the desktop, but on 10.04 the same shortcut opens the mail applet....

Any1 knows of a quick way of inversing desktop colours please?

Many thanks in advance

---

### Post by hictio on 2010-07-20
Ok, are you currently able to run the "Desktop Effects" and they are enabled, right?
Then check:

System > Preferences > Keyboard Shortcuts 

for the shortcut called "Launch Email Client" (it is under the 'Desktop' category) and try disabling that particular shortcut.

---

### Post by mcduck on 2010-07-20
> **a_petrov303 said:**
> On 9.04/.10 Win+M would reverse the colours of the desktop, but on 10.04 the same shortcut opens the mail applet....

Any1 knows of a quick way of inversing desktop colours please?

Many thanks in advance

Just install CompizConfig Settings Manager and change the keyboard shortcut for inverse colors to something else.

---

### Post by a_petrov303 on 2011-06-03
> **mcduck said:**
> Just install CompizConfig Settings Manager and change the keyboard shortcut for inverse colors to something else.
Thank you for your answer...

I have upgraded to 11.04 now and face the same problem...cannot find the "inverse colors" link anywhere - is it still in compiz config settings?

---

### Post by stinkeye on 2011-06-03
> **a_petrov303 said:**
> Thank you for your answer...

I have upgraded to 11.04 now and face the same problem...cannot find the "inverse colors" link anywhere - is it still in compiz config settings?
ccsm > Accessibilty > Negative

---

### Post by Spaarkplug on 2011-08-22
hey stinkeye...

It's still not working for me. I have done everything that is mentioned in this thread. I just installed Natty. A complete format of my Meerkat and full fresh install of Natty 11.04. I really need this feature. I even went to keyboard shortcuts and set the Win + M key as inverse screen and still not wokring. Any ideas why and what to do?

Thanks!

---

### Post by stinkeye on 2011-08-23
In the negative plugin the default setting for
**Exclude Windows** is
```
type=Desktop
```
If I delete that entry super+m works on the wallpaper as well.
Could also try changing the keyboard shortcut in ccsm.


Also check your running compiz with wmctrl.
```
sudo apt-get install wmctrl
```

Then run in terminal
```
wmctrl -m
```

and you should get similar output
```
glen@Natty:~$ wmctrl -m
Name: [COLOR="Red"]Compiz[/COLOR]
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

---

### Post by Spaarkplug on 2011-08-23
You know after I did wmctrl -m, I got this.

mo@sciencemachine:/$ wmctrl -m
Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A
mo@sciencemachine:/$ 

After I installed Natty, I googled what to do, and came across a link '[Top Things to do after installing Ubuntu 11.04 Natty Narwhal]("http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal")', and over there it said, OMG, if you haven't installed Nautilus and all these other things, you are sooo uncool, so I did install most of the good ones from there which I thought I needed like a derp.

So, yeah,.. now that I tinkered a few options with CCSM, I am almost certainly convinced none of the settings changes I make seem to take effect. I dont know why. Hmm.

---

### Post by stinkeye on 2011-08-23
The settings in ccsm don't work because your running
Metacity as your window manager and not Compiz.

---

### Post by Spaarkplug on 2011-08-24
Ok. Don't just stop there. Atleast tell me how can I change it from Metacity to Compiz. :)

---

### Post by Spaarkplug on 2011-08-24
Got it. I found your answer to somebody else. [http://ubuntuforums.org/showthread.php?t=1709792](http://ubuntuforums.org/showthread.php?t=1709792).

Thanks!

---

### Post by Spaarkplug on 2011-08-24
I found your reply to someone else solve this problem. [http://ubuntuforums.org/showthread.php?t=1709792](http://ubuntuforums.org/showthread.php?t=1709792)  THanks.

---

### Post by Spaarkplug on 2011-08-24
F-word!! Now, I don't have title bars, maximize, minimize and close window buttons for all of my windows. Argh! I can't even drag my windows around. Aaaah. What happened :(  ?? How do I fix this stinkeye :( ?

---

### Post by Spaarkplug on 2011-08-24
Ha. I see that compiz has problems with 11.04. Got the fix here. [http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/](http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/)

Its all good now.

---

