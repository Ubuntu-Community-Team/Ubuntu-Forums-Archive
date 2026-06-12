---
title: "Blank Desktop Background After Login to Xubuntu or XFCE Session"
date: 2013-07-04
forum: Desktop Environments
---

### Post by livingegg on 2013-07-04
Hello All. I am hoping someone will be able to lend some advice that will spare me from needing to do a fresh install. I recently installed Xubuntu 12.04.2 on my Fujitsu Lifebook laptop, and everything was running smoothly until today when I logged in to a Xubuntu Session with my admin account and got only a blank desktop background. I then tried rebooting and logging into an XFCE Session for the same account (through the dropdown control in the login screen) and it loaded up fine. Believing I may have previously installed an update that caused the broken Xubuntu Session, I installed all the latest updates. I then rebooted and now the issue is occuring with both Xubuntu and XFCE sessions! I am still able to launch a guest session successfully. Any ideas on how I can start diagnosing this? All I have tried so far is ctrl+alt+F1 during the blank desktop session (which successfully gets a terminal) and ctrl+alt+del (which does nothing).

---

### Post by Toz on 2013-07-04
Hello and welcome to the forums.

It sounds like xfdesktop may have crashed. You could try cleaning out your sessions cache.
1. While _not_ logged in, go back to the first tty (Ctrl+Alt+F1).
2. Log in to the text console
3. Run the following commands:
```
cd $HOME/.cache
rm -rf sessions
```
4. Go back to the gui tty (Ctrl+Alt+F7) and log in normally again.

---

### Post by livingegg on 2013-07-04
You, sir, are a genius. Wiping out the sessions cache did indeed fix the issue. Many thanks!

---

### Post by Toz on 2013-07-04
Glad to help. If you don't mind, can you please mark this thread [SOLVED] as per the instructions in my signature?
Thanks

---

