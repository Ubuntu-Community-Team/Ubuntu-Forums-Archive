---
title: "Adding RealPlayer install dir to system path"
date: 2006-01-06
forum: Desktop Environments
---

### Post by Rishi on 2006-01-06
I've just installed RealPlayer for Linux. However, when I try to play embedded media using RealPlayer, I get an error informing me that no realplay or hxplay was found in my system path. As RealPlayer is installed to /home/rishi/RealPlayer, I have this line in my .bashrc file:

```
export PATH=$PATH:/home/rishi/RealPlayer
```

I'm using Ubuntu 5.10, Firefox 1.0.7 (Ubuntu package), and RealPlayer 10. What am I doing wrong?

---

### Post by dcstar on 2006-01-07
[QUOTE=Rishi]I've just installed RealPlayer for Linux. However, when I try to play embedded media using RealPlayer, I get an error informing me that no realplay or hxplay was found in my system path. As RealPlayer is installed to /home/rishi/RealPlayer, I have this line in my .bashrc file:

```
export PATH=$PATH:/home/rishi/RealPlayer
```

I'm using Ubuntu 5.10, Firefox 1.0.7 (Ubuntu package), and RealPlayer 10. What am I doing wrong?[/QUOTE]
How did you install it?, by default the install process puts the realplay binary in the standard paths (like /usr/bin).

---

### Post by Rishi on 2006-01-07
[QUOTE=dcstar]How did you install it?, by default the install process puts the realplay binary in the standard paths (like /usr/bin).[/QUOTE]
I used the .bin file and ran it. By default it wanted to install to ./RealPlayer (I downloaded it to the desktop so this was /home/rishi/Desktop/RealPlayer).

---

### Post by dcstar on 2006-01-07
[QUOTE=Rishi]I used the .bin file and ran it. By default it wanted to install to ./RealPlayer (I downloaded it to the desktop so this was /home/rishi/Desktop/RealPlayer).[/QUOTE]
Did it ask you to allow it to create all the links?

---

### Post by Rishi on 2006-01-07
[QUOTE=dcstar]Did it ask you to allow it to create all the links?[/QUOTE]
Nope. After I ran it (as root), it asked which directory I wanted to install to, and then to type 'F' for 'Finish' or 'B' to change the install directory (it may not have been 'B', I don't recall), then it outputted a whole set of stuff to the terminal (which, unfortunately, I didn't save) and said 'Finished' (or 'Done', don't recall).

---

### Post by dcstar on 2006-01-07
[QUOTE=Rishi]Nope. After I ran it (as root), it asked which directory I wanted to install to, and then to type 'F' for 'Finish' or 'B' to change the install directory (it may not have been 'B', I don't recall), then it outputted a whole set of stuff to the terminal (which, unfortunately, I didn't save) and said 'Finished' (or 'Done', don't recall).[/QUOTE]
What happens when you type (in a user terminal):

"whereis realplay"
or
"whereis realplayer"

Note that these are case sensitive.

---

### Post by Rishi on 2006-01-07
[QUOTE=dcstar]What happens when you type (in a user terminal):

"whereis realplay"
or
"whereis realplayer"

Note that these are case sensitive.[/QUOTE]
Here you go:

```
rishi@ubuntu:~$ whereis realplay
realplay:
rishi@ubuntu:~$ whereis realplayer
realplayer:
```

---

