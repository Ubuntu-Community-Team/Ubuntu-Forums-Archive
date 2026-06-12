---
title: "Warning: Color name &quot;black&quot; is not defined"
date: 2006-06-08
forum: Desktop Environments
---

### Post by RikBlankestijn on 2006-06-08
Hi.

I got the following message "Warning: Color name "black" is not defined" when opening vi for example. After I've quit the application I see the message.
There was already a thread about it for dapper but that one is closed and no solution provided ([http://www.ubuntuforums.org/showthread.php?t=154510](http://www.ubuntuforums.org/showthread.php?t=154510)) hopefully someone can help? 
Vim is working but the message should just not appear ;-)

kind regards,
Rik

---

### Post by DarthMandeep on 2006-06-08
You might need to make a copy of your /etc/X11/rgb.txt file and place it in the /usr/lib/X11/ directory and the /usr/share/X11 directory. This solved the issue for me.

---

### Post by RikBlankestijn on 2006-06-08
Thanks for the suggestion, unfortunatly, I do already have that file and black also is defined.

---

### Post by RikBlankestijn on 2006-06-19
just to let you know; it has been fixed with the latest updates.

---

### Post by bnortham on 2006-06-27
Latest "released" updates? or. . .because it still occurs for me, even after trying copying over the rgb.txt file to suggested locations.

---

### Post by marvinthesad on 2006-06-29
[QUOTE=bnortham]Latest "released" updates? or. . .because it still occurs for me, even after trying copying over the rgb.txt file to suggested locations.[/QUOTE]

Yep. Would like to know as well, what "updated" or "fixed" means. Which packages "were" guilty, xserver-xorg ? 

Now I'm running my session over NX with freenx server and nxclient.
Who knows why this happens to me?

I copied a version of rgb.txt to 
```
~$ find / -name rgb.txt 2> /dev/null
/etc/X11/rgb.txt
/etc/xplanet/rgb.txt
/usr/lib/X11/rgb.txt
/usr/share/X11/rgb.txt
/usr/share/emacs/21.4/etc/rgb.txt
/usr/share/xplanet/rgb.txt

```
actually in /etc/X11 and /usr/lib/X11 they were already there.
I had the line " RGBPath /etc/X11/rgb"  in xorg.conf, I 
"dpkg-reconfigure -phigh xserver-xorg"ed but still to no avail.

Symptoms: 
[LIST]
[/LIST][LIST]
[*]no TK app runs, 
```
~$ wish Application initialization failed: this isn't a Tk applicationunknown color name "Black"
```
[*]xclock, xterm, etc... show
```
Warning: Color name "black" is not defined
```
[/LIST]

Solutions:
Funny, just found it in a different forum:
I missed /usr/X11R6/lib/X11, because it is hardcoded in the freenx server/clients thus all I needed to do was copying rgb.txt to the directory.
I have no RGBPath line now in my config, btw.

Cheers, to anyone this is helpful for.

---

