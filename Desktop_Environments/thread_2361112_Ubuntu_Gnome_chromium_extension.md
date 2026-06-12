---
title: "Ubuntu Gnome chromium extension"
date: 2017-05-12
forum: Desktop Environments
---

### Post by rdb3 on 2017-05-12
Running Ubuntu 17.04 w Gnome.

In my installed chromium-browser, the extension GNOME Shell Integration is permanently enabled.  I can not disable it.  Is that normal?  
Is there a way to disable it?

---

### Post by howefield on 2017-05-12
Try ...

```
sudo apt purge chrome-gnome-shell
```

Watch for anything else that it wants to remove.

---

### Post by rdb3 on 2017-05-12
I did that, then restarted the pc and gone.

Thank you.

I thought I tried that before when I was searching the web for solutions, but........   ;)

---

### Post by howefield on 2017-05-12
Cool, glad you got it and thanks for marking the thread as solved.

---

### Post by jbicha on 2017-05-13
That extension allows you to install, enable or disable GNOME Shell extensions in your web browser which is probably a good thing!

---

### Post by howefield on 2017-05-13
> **jbicha said:**
> That extension allows you to install, enable or disable GNOME Shell extensions in your web browser which is probably a good thing!

Yep, in addition to that the extension also checks for updates as far as I can see, I kept chrome-gnome-shell in place but set the time interval between checking for updates to a more reasonable (for me) weekly instance.

---

### Post by rdb3 on 2017-05-13
Thanks for the replies. Here's my current situation:

On chromium, I removed 'Gnome Shell Integration' extension yesterday.

I had another extension, which is still running and has not been impacted.

I just installed another extension to see if it would install, and it did..... no problem.

It installed fine without 'Gnome Shell Integration.'

I am confused at this point. Why do I need GSI?
  
p.s. I just went to the Chrome Web Store to read the reviews on this extension. It seems like if I have x extensions on my chromium browser, it will make them available to any other browser on my computer.... if extension is set up correctly.

I don't see where it is needed to install or remove an extension though..... which I was able to do without it.

---

### Post by howefield on 2017-05-13
> **rdb3 said:**
> I am confused at this point. Why do I need GSI?.

Just in case there is confusion, chrome-gnome-shell doesn't impact on your web browser extensions.. only the gnome-shell extensions that you install in order to make the desktop environment more to your taste, eg Dash to Dock.

---

### Post by rdb3 on 2017-05-13
That explains it........ thanks again!

---

### Post by howefield on 2017-05-13
Cool, you're very welcome.

---

