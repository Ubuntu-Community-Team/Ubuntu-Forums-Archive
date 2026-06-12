---
title: "Closing terminal ERROR message!"
date: 2009-04-23
forum: General Help
---

### Post by pro003 on 2009-04-23
Well it's been weird during test of release candidate but I now I just have finished installation of final 9.04 and this annoying message appears when closing terminal:

```
"There is still process running in this terminal. Closing the terminal will kill it!" 
```

any thoughts what might cause this?

---

### Post by abcuser on 2009-04-23
xxxxxxxxxxx

---

### Post by abcuser on 2009-04-23
Hi,
are you sure you didn't put some program in background? Like:
some_command &

Please post more info. Try to open terminal and close it. Does it happen again? What commands have you entered before you closed down terminal and this message appeared?
Regards

---

### Post by pro003 on 2009-04-23
no man, like i said, i have just finished installation and when i logged in i have opened terminal and did only update (sudo apt-get update) and then when I wanted to close it - this error msg popped up. And it happened before but i thought it will be resolved in final edition. Obviously not.

---

### Post by abcuser on 2009-04-23
It sounds like a bug. Maybe there is some process running and response back was too early.

Try to reboot Ubuntu, open Terminal do update again and after finished try to close Terminal if the problem persists it is very likely some kind of bug. If so reporting a bug to bugtracker is probably the only option.

---

### Post by pro003 on 2009-04-23
yeah it's a bug, definitely. I have tried everything but this little annoyance persist. Also am now having problems with graphic driver, I installed first Ati's latest driver in non-gui environment lie I always did before, and then screen resolution went down to some 1024x768 and the biggest was 1280x1024 and my screen is 22" viewsonic 1680x1050 native resolution, I even didn't have this problem with RC and not even with 8.04 or 8.10. 

I'm a bit disappointed with this release, and as far for now I give up. 

Jaunty - too buggy for me!

---

### Post by nanobahr on 2010-07-16
```
You can disable the confirmation window by launching gconf-editor, and then go to apps->gnome-terminal->global and disable confirm_window_close.
```

---

### Post by pro003 on 2010-07-16
> **nanobahr said:**
> ```
You can disable the confirmation window by launching gconf-editor, and then go to apps->gnome-terminal->global and disable confirm_window_close.
```

this is very old post, and am using lucid as a matter of fact but anyway i thank you for posting the solution....

This Thread should be marked Solved now.

---

### Post by willdeans on 2010-09-14
How do I get rid of the Windows-mentality message "There is still process running in this terminal. Closing the terminal will kill it!" from the command line?

---

### Post by CharlesA on 2010-09-14
> **willdeans said:**
> How do I get rid of the Windows-mentality message "There is still process running in this terminal. Closing the terminal will kill it!" from the command line?

I do not believe there is any way to do it without using gconf-editor, which requires a GUI.

Otherwise you can just launch it from there.

---

