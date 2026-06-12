---
title: "How to disable the KDE Screen Saver?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by HippoMan on 2006-06-19
I have been wanting to get **xscreensaver** hacks to work under **Dapper/Kubuntu**, but even with all the correct packages installed, it still doesn't work.  See this thread for more details on what I have done so far: [http://ubuntuforums.org/showthread.php?t=199463]("http://ubuntuforums.org/showthread.php?t=199463%29")

Because of my lack of success with this, and based on the following text in the **Screen Saver** section of the **KDE Help Center**, I have decided to totally disable the **KDE Screen Saver **and just use **xscreensaver** in its place:
> **Using a non-KDE screen saver**

KDE does not prevent another screen saver from working. To use a different screen saver, such as xscreensaver, simply disable the KDE Screen Saver, and set up your other screen saver program normally. My question is this: what is the recommended way to disable the **KDE Screen Saver**?  If I try to remove it via **apt-get**, the package manager wants to remove all of the principal KDE packages, including the **kde** package itself.  Therefore, I know that this is not the way to accomplish what I want to do.

Do I simply unset the **Start Automatically** checkbox in the **Screen Saver** section of the **KDE Control Center**, or is there more that I have to do in order to disable the **KDE Screen Saver** in the way that the help text is suggesting?

In other words, if all I do is to unset **Start Automatically** and then set up **xscreensaver** to run, will I still encounter conflicts between **kscreensaver** and **xscreensaver**?  If so, how can I avoid this.

Thanks in advance.

---

### Post by lowey23 on 2006-06-19
Hi, HippoMan

Quote:
Do I simply unset the Start Automatically checkbox in the Screen Saver section of the KDE Control Center

That's what I did and it works fine. I like the KDE Slideshow screensaver but because of a bug it doesn't work. I just did as above and added xscreensaver. Don't have the one I want but it is working fine until a fix becomes available.

Hope this helps

Cheers

Lowey

---

### Post by HippoMan on 2006-06-20
Yes, this does indeed help.  Thank you very much!

---

### Post by lowey23 on 2006-06-20
Pleasure, my friend, glad my 2c helped.

Took your advice and took a hippo to lunch. Can't they eat? I think I'll just stick with taking kangaroos out. 

Lowey

---

