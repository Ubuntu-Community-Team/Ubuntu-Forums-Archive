---
title: "Dell Inspiron 700m Not Booting Correctly"
date: 2011-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by blinovitch on 2011-08-04
So there's this beat up Inspiron 700m notebook. I've tinkered with it off and on for a couple years. Last I left it, it had Ubuntu 10.10 installed and everything seemed fine. After a period of inactivity I wanted to retrieve some files, only to find it's not booting up right at all.

At first it showed a black screen with a text login prompt. From there, I could log in with the admin account, but I wasn't able to do anything useful because I'm not that adept at the command line, but I did make attempts with commands like startx or trying to restart the Gnome environment.

Now that I have the opportunity to write this post, it's acting even odder: when booting, it hangs at this message: ```
[  21.9242471] ipw2200: Failed to send POWER_MODE: Command timed out.
```

I've tried a live CD with 10.04 on it. That hangs on a blank screen. I've tried a live USB drive made with Unetbootin. That garners a "Missing operating system" error.

I don't even know what terms I should be searching to diagnose the problem, let alone how to salvage the files I was trying to retrieve -- that error quoted above doesn't turn up any hits that seem related to this problem. Any thoughts?

---

### Post by mikewhatever on 2011-08-05
To try and diagnose this vague problem of nothing working, try booting from an Ubuntu CD with the splash screen disabled. To disable splash, hit any key as soon as you see the purple background, then, at the menu, hit f6, but don't select anything and hit Esc. The cursor should now be at the end of the boot line at the bottom of the screen. Delete the 'quiet' and 'splash' at the end of the line and hit enter. While booting this way, you should see lots of lines on the screen, hopefully, the lines just before it stops will prove helpful to get a clue about the problem.

To get to the files from the command line interface, you'll need the following commands and some practice:
cp - change directory
ls - list content of current directory
cp - copy files and dirs

I'd also be interested to know the specs of the computer.

---

### Post by blinovitch on 2011-08-05
Trying the "no quiet, no splash" technique, the last few lines before the screen goes to black are:[INDENT]init: ureadahead-other main process (1037) terminated with status 4
init: ureadahead-other main process (1038) terminated with status 4
 * Setting sensors limits
[/INDENT]Then the text disappears, scattered blocks of red and orange briefly appear and the screen goes black.

---

