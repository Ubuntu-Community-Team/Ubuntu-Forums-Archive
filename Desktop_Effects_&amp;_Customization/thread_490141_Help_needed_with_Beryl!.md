---
title: "Help needed with Beryl!"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by ETS_5005 on 2007-07-02
So I finally did it. Installed Ubuntu Ubuntu Festy Fawn. And managed to mess it up at once too. Installed Beryl and then accidentally set Force GXT...or something. But since I have an ATI card that does not fit it. So the question is How could I set it back To Automatic. Total beginner so I do not know how to use the terminal to do it. Help would be good. 
+Do not mind if I post this at the wrong place or so...my first post.

---

### Post by Malibu Illusion on 2007-07-02
Everyone needs help here; I suggest using more descriptive topic names in future.

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

---

### Post by ndefontenay on 2007-07-02
Do you mean you don't have any graphical interface at all?

If you don't, then you can maybe try to restore your config file in /etc/X11/

---

### Post by pardesi on 2007-07-02
try to log  in via failsafe mode and start beryl manager and change

---

### Post by ETS_5005 on 2007-07-02
I already logged in Fail safe and in failsafe-Terminal. The screen went nuts and the graphics corrupted once I started beryl manager.:( just need away to reset all changes done to Beryl manager in Terminal session.

Already missing my Ubuntu desktop.

---

### Post by ETS_5005 on 2007-07-02
Found something Will try it out

[http://ubuntuforums.org/archive/index.php/t-384846.html](http://ubuntuforums.org/archive/index.php/t-384846.html)

[http://ubuntuforums.org/showthread.php?t=486544](http://ubuntuforums.org/showthread.php?t=486544)

If this works I will not hang myself. Thank you all for trying to save me.

---

### Post by ETS_5005 on 2007-07-02
OK everything running fine once again. Back on my Ubuntu desktop. Thank you all.

---

### Post by fongs on 2007-07-02
> **ETS_5005 said:**
> OK everything running fine once again. Back on my Ubuntu desktop. Thank you all.

Good to to know you fixed it can you tell us how you did it

---

### Post by nowald on 2007-07-02
> **fongs said:**
> Good to to know you fixed it can you tell us how you did it

I'm a begginer too, but I think, its possible to restore xorg configuration as default with:
```
sudo dpkg-reconfigure xserver-xorg
```

Un saludo

---

### Post by ndefontenay on 2007-07-02
When toying around with my dsktop and Compiz/Beryl, I like to backup the file /etc/X11/xorg.conf

If there's anything wrong, I will just put the original one back in place.

Compiz/Beryl and pretty much any kind of drivers you might install won't do more than just modify that configuration file.

If something goes wrong, you don't have to think about anything else than that.

---

### Post by ETS_5005 on 2007-07-03
backup the file /etc/X11/xorg.conf is a nice way to do it but the problem I had corrupted the entire desktop so I could not do anything. The only way was to use the Failsafe-Terminal session and to delete the beryl configuration files. The links above described that and so I did. After that the normal graphic mode was applied (the right option for ATI) and all I had to do was to type Exit to terminal. Sign in once again and re configure Beryl. 

Apparently I set Force XGL from Rendering platform and that does not work with ATI.;)

---

