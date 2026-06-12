---
title: "Preventing dual use of top bar in desktop and windows"
date: 2014-08-20
forum: Desktop Environments
---

### Post by ufarmer on 2014-08-20
I might be searching for the answer to this question using the wrong keywords as none of the solutions I have found have the desired effect.

I believe the top bar in the <insert curse word> Unity desktop is called the panel and that the top of every window is called the title bar.

1) I want to stop the title bar of maximized windows from merging with the panel so that one has to mouse over the now-shared area to see menu options.

2) Even in non-maximized windows, the title bar seems to serve a dual purpose and one has to mouse over it to reveal some menu options.  I want to change that behaviour too.

At best, I seem to have stopped the title bar of maximized windows from over-writing the window controls on the top left but I still have to mouse over the top of every window to reveal the menu options.  The settings I have been directed to by various "solutions" -- like System Settings and the gconf editor -- all seem to be already set to disable this behaviour.

---

### Post by bonzo2 on 2015-03-17
ufarmer,

Greetings. It's been several months since you posted. Did you ever get this issue resolved?  I am also trying to make this change and cannot figure out how to have both the title and menu always (rather than alternatively) displayed.

Bonzo

---

### Post by egeezer on 2015-03-17
I never found an answer to that question myself, so I simply installed the Xfce desktop on top of the Ubuntu to run as a separate session.  After a while I liked it so much I installed xfce4-goodies as well and now run it like Xubuntu, but with many more features accessible.  Ubuntu+Xfce is now my distro of choice (heavy, but any relatively recent desktop/laptop can easily handle the load).

---

### Post by bonzo2 on 2015-03-17
Hey egeezer!

Thanks for responding. So, I borrowed your approach and loaded xfce4 via Synaptic. Now I'd like to remove it for awhile.  I removed xfce4 via Synaptic yet there are still about 28 installed items that include xfce in Synaptic.  Are these remnants from my experimental installation of xfce4?  Would I need any of those in the absence of xfce4?  should I uninstall them?

Bonzo :-)

---

### Post by egeezer on 2015-03-18
It wouldn't be surprising if you had some bits and pieces left over from your original install of xfce4, since you used Synaptic rather than a
```
sudo apt-get remove --purge xfce4
```
process. In fact, you might run that command if you want to clear it all out.

If you intend to go back to it (you said you'd like to remove it for a while), it would be best to reinstall using
```
sudo apt-get install xfce4 xfce4-goodies
sudo apt-get update
```
which will give you all the Xfce configuration options that let you shape it to your liking.
.

---

