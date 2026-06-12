---
title: "Window Manager Problem"
date: 2013-04-10
forum: Desktop Environments
---

### Post by rocketeer141263 on 2013-04-10
Hello everyone

I recently got a problem. Whenever I now log on, Firefox and Thunderbird no longer have  a border round them, they do not have the maximise, minimise and close icons. I cannot pop one window from beneath another. It also appears that the shut down box now appears at the top left hand corner(0,0)?

These problems all appear to have started when I was in a hurry to shut down and did not close all my applications. There was a brief error message about the window manager being idle. I did not make a note of it any further as it only appeared the once.

There are no messages at boot up. It has always been a blank screen until the logon box appears.

Can someone please offer a suggestion to rectify this problem, hopefully not involving reinstalling the operating system.

Regards

---

### Post by Toz on 2013-04-10
Hello and welcome to the forums.

It sounds like the window manager may have crashed. Try restarting it with:
```
xfwm4 --replace
```
...from a terminal window or Alt+F2.

---

### Post by rocketeer141263 on 2013-04-10
Toz

thank you for the speedy reply. The answer is yes and no!

Yes - it works for the current session
No - when I log out or reboot the PC then I am back to the original problem.

If I type
xfwm4 --replace in a terminal it refreshess everything but the window is tied up so to speak, as if it is expecting further input.

Is this more than the window manager crashing? Has a file become corrupted?

Regards

---

### Post by Toz on 2013-04-10
> Is this more than the window manager crashing? Has a file become corrupted?
No, its just the window manager is crashing or not starting. You can try this command instead to release the window:
```
xfwm4 --replace &
```
...it will fork the command to the background.

> No - when I log out or reboot the PC then I am back to the original problem.
There might be an issue with your saved sessions cache if the fix doesn't persist. Try deleting the sessions cache. Go to Settings Manager -> Session and Startup -> Session tab and click on the "Clear Saved Sessions" button. If this button doesn't exist, you'll have to do it manually like this:

```

cd $HOME/.cache
rm -rf sessions
```
...then log out and back in again.

If the problem still persists, you'll need to run the above commands while not logged in (Ctrl+Alt+F1 to get to text console)

---

### Post by rocketeer141263 on 2013-04-10
Thanks

clearing the files from .CACHE finally cured the problem

Thanks again

---

