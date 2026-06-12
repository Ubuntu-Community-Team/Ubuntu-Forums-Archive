---
title: "Root-tail (logs on desktop - problem)"
date: 2005-06-19
forum: Desktop Environments
---

### Post by dolny on 2005-06-19
Homepage: [http://www.goof.com/pcg/marc/root-tail.html](http://www.goof.com/pcg/marc/root-tail.html)

Root-tail displays the messages from /var/log on your desktop. I tried to use the command from the manual (example) but got this: 

```
dolny@milkshake:~$ sudo root-tail -g 800x250+100+50 -font 10x20 /var/log/messages
Password:
**Missing charsets in String to FontSet conversion (JISX0208.1983-0)**
```
...and nothing showed up on my KDE background.

It is supposed to look like here: [http://www.lynucs.org/index.php?screen_id=1029482457401e40ad34761&p=screen](http://www.lynucs.org/index.php?screen_id=1029482457401e40ad34761&p=screen) or here: 
[http://www.lynucs.org/index.php?screen_id=5235311274028194baaf11&p=screen](http://www.lynucs.org/index.php?screen_id=5235311274028194baaf11&p=screen)

Can anybody help?

**Edit: I found it - I had to enable 'allow programs on desktop': right click on KDE desktop>Behaviour>Allow programs on desktop>yes**

I have a polish version of KDE so I don't know the exact translation. Can anybody post their settings? I can't display it properly :) Fonts  too big etc.** How can I fix the size of the font? It's huge. Tried to change it but I got the error again - "Missing charsets..."**

---

### Post by dolny on 2005-06-19
Here's my desktop: [http://www.echostar.pl/~dolny/ubu/zrzut13.jpg](http://www.echostar.pl/~dolny/ubu/zrzut13.jpg)

I'm using these settings:

```
root-tail  -g  500x200+20+30  -font Tahoma -fn fixed /var/log/messages
```

How can I make the font a bit smaller/How can I make this messages to update when the file updates? Anyway I posted them because someone may find them useful :)

---

### Post by angkor on 2005-06-20
Are you using gnome? I've read root-tail and gnome don't like eachother, you could try root-portal.

---

