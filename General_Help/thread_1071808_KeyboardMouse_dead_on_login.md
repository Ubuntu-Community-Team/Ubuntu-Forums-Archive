---
title: "Keyboard/Mouse dead on login"
date: 2009-02-16
forum: General Help
---

### Post by yothere on 2009-02-16
Got home today and I could see the mouse on a black background and move it around but that was it. Nothing else on screen. I tried clicking around, Ctrl+Alt+Del and nothing. The computer was left on and I'd locked the screen before I'd left it last.

I reset the computer using the button the front and it restarted, performed it's disk checking, I had to perform a checking of the disk manually because the default disk checker thing kept exiting and told me to perform it manually.

After that finished when Ubuntu came up to the login thing the mouse and keyboard won't work. I pressed Ctrl+Alt+F1 and I got the terminal screen. I was able to type there.

I typed 'startx' and it told me there was already an instance of it running on display 0. Don't know what to do now. I can't use my computer. Please help me.

Thank you.

-h

---

### Post by Dr Small on 2009-02-16
Have you tried pressing ALT + F7 ?

---

### Post by yothere on 2009-02-16
Hello. Thank you for your reply. 

I just tried it with no luck. It just sat there.

---

### Post by Dr Small on 2009-02-16
What about trying to login, then running this commands:
```
sudo /etc/init.d/gdm restart
```

---

### Post by theozzlives on 2009-02-16
> **yothere said:**
> Got home today and I could see the mouse on a black background and move it around but that was it. Nothing else on screen. I tried clicking around, Ctrl+Alt+Del and nothing. The computer was left on and I'd locked the screen before I'd left it last.

I reset the computer using the button the front and it restarted, performed it's disk checking, I had to perform a checking of the disk manually because the default disk checker thing kept exiting and told me to perform it manually.

After that finished when Ubuntu came up to the login thing the mouse and keyboard won't work. I pressed Ctrl+Alt+F1 and I got the terminal screen. I was able to type there.

I typed 'startx' and it told me there was already an instance of it running on display 0. Don't know what to do now. I can't use my computer. Please help me.

Thank you.

-h

It should tell  you which file to delete  in  the /tmp folder. Delete that then  do startx.

---

### Post by glotz on 2009-02-16
Also, hitting the power switch or reset are the absolute last thing there is. First, you should try killing the hung process, from a virtual terminal (login and pkill process name) and then the X server (Ctrl+Alt+Backspace) and then doing the sysrq thing ([http://en.wikipedia.org/wiki/Reisub#.22Raising_Elephants.22_mnemonic_device](http://en.wikipedia.org/wiki/Reisub#.22Raising_Elephants.22_mnemonic_device)) This helps prevent damage to your hardware and data.

---

### Post by yothere on 2009-02-17
I deleted the file it told me to and tried startx again, no such luck. It tells me the server is already running.

---

### Post by yothere on 2009-02-17
> **Dr Small said:**
> What about trying to login, then running this commands:
```
sudo /etc/init.d/gdm restart
```

This one didn't work either.

---

### Post by yothere on 2009-02-26
I've tried the magic SysRq key thingi and it still didn't work. The computer is just an expensive paperweight at this point.

Does anyone know how to reinitialize my keyboard and mouse? I'm annoyed.

Primarily, I hate that I don't really know how it works. I'm not sure what's handling my keyboard and mouse. Is this an IRQ thing? I have no idea. I hate being ignorant. I believe that's why GNU/linux hasn't taken off. It's not explicit enough maybe?

---

