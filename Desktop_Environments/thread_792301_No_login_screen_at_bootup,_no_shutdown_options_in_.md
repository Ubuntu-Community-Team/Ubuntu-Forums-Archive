---
title: "No login screen at bootup, no shutdown options in KDE"
date: 2008-05-12
forum: Desktop Environments
---

### Post by nihilion on 2008-05-12
Greetings,

I'm hoping someone can help me. I recently did a clean install of feisty (64bit) with the KDE4 desktop. 

I really didn't like KDE4, so I installed kde3 next to it and did my best to delete KDE4 off my system. 

However, after I got rid of KDE4, I no longer got a login screen when I booted my machine. I would only boot to a prompt (like DOS.. i know its not DOS, but I don't know what to call it). I would then login at the prompt and type "startx" in order to get into KDE. 

Also, I think because I start KDE this way, I no longer get all of my shutdown options from the shutdown menu./ The only thing i can do is "logout". 

Can anyone help? I just want to have a login screen so i can login properly, change users, or change sessions if I wish.

Thanks.

Nicholas

---

### Post by inportb on 2008-05-12
Did you install kde, or did you install kubuntu-desktop? Because you're missing kdm and most likely a bunch of other packages. If you installed kubuntu-desktop, try installing kdm or reconfiguring kdm. Otherwise, install kubuntu-desktop.

---

### Post by nihilion on 2008-05-12
I don't really know. I installed KDE4 originally from a Kubuntu (feisty 64) disk. 

When I installed KDE3.5.9, I think I just did it from a command line using apt-get. But I don't remember if I typed apt-get install KDE or if I did apt-get install kubuntu-desktop. 

Should I try that? 

Nick

---

### Post by Xiong Chiamiov on 2008-05-13
> **nihilion said:**
> I don't really know. I installed KDE4 originally from a Kubuntu (feisty 64) disk. 

When I installed KDE3.5.9, I think I just did it from a command line using apt-get. But I don't remember if I typed apt-get install KDE or if I did apt-get install kubuntu-desktop. 

Should I try that? 

Nick
Yes.

If you ever need to shutdown (and yes, starting X that way is why it doesn't appear in your options), you can run
```

sudo shutdown -pH now

```
or
```

sudo shutdown -r now

```
to reboot.

---

### Post by nihilion on 2008-05-13
Thanks guys. That did the trick. Just needed to install kubuntu-desktop.

---

