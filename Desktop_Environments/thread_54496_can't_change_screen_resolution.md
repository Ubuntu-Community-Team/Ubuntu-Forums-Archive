---
title: "can't change screen resolution"
date: 2005-08-04
forum: Desktop Environments
---

### Post by thermopylae0480 on 2005-08-04
I am a total newbie when it comes to linux, and ubuntu is my first real installation of it. When I try to change my monitor resolution, it will only let me select 640x480. Do I need to install my monitor or something? Thanks.

---

### Post by bored2k on 2005-08-04
1. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
2. ```
sudo dpkg-reconfigure xserver-xorg
``` 
3. Restart.

?

---

### Post by ^NoX on 2005-08-04
[QUOTE=bored2k]1. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
2. ```
sudo dpkg-reconfigure xserver-xorg
``` 
3. Restart.

?[/QUOTE]
he realy needs a restart? i think that restarting the x-server will be as much as affective.
to restart the x-server, CTRL+ALT+BACKSPACE

---

### Post by bored2k on 2005-08-04
[QUOTE=^NoX]he realy needs a restart? i think that restarting the x-server will be as much as affective.
to restart the x-server, CTRL+ALT+BACKSPACE[/QUOTE]
 That also works..

---

### Post by sooqing on 2005-08-05
anyone knows how to quit the GUI? i tried ctrl-alt-backspace and it kept going GUI! think i have to kill something?

---

### Post by bored2k on 2005-08-05
[QUOTE=sooqing]anyone knows how to quit the GUI? i tried ctrl-alt-backspace and it kept going GUI! think i have to kill something?[/QUOTE]
 1. Ctrl+Alt+F1
2. Login
3. killall X

---

### Post by heimo on 2005-08-05
I've collected information about this topic to this post:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://ubuntuforums.org/showpost.php?p=129379&postcount=21")

And here's wiki about the same subject:
[https://wiki.ubuntu.com/FixVideoResolutionHowto]("https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29")

---

