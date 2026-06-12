---
title: "Gnome desktop works perfectly well on one user but problematic on another user"
date: 2009-11-12
forum: Desktop Environments
---

### Post by Hobbsilla on 2009-11-12
So, I've had my share of minor problems with the Gnome desktop on my main user account but as of right now the Gnome Desktop is working perfectly well. However I have a second user which was added before I upgraded to 9.10. After upgrading to 9.10 the desktop for the other user was not working correctly. 
The first problem the top part of windows that contain your basic exit, minimize, maximize buttons seems to be missing and using Alt + Tab doesn't seem to work or Alt + F4 to get the windows to alternate or quit. Trying to do either of those two commands seems to make an error message pop up.
My second problem is when I have an application running it does not show up on the bottom task bar.
Third problem seems to be clicking on the Desktop icon apparently does not work and makes another error message pop up. 
And the final noticeable problem is either wifi is failing on that user or the nm-applet is missing. Its so frustrating to boot into and out of that user that I'm not really sure I want to find out.
Luckily I can bring up the terminal window using a keyboard shortcut I had set up before updating the OS but i haven't tested to see if I can run functions on it.
If I had to guess this is a metacity or desktop problem. Does anyone have an possible solutions for any of these problems?
Any help is appreciated.

---

### Post by Peter09 on 2009-11-12
In your non-working user try deleting the gnome config file. Next time you log in gnome will reset to default.

In the non-working users directory do in a terminal:

```
rm -r .gnome2
```

---

### Post by Hobbsilla on 2009-11-13
It didn't seem to do anything. I rebooted too.

---

