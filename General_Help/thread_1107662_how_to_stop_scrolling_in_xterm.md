---
title: "how to stop scrolling in xterm?"
date: 2009-03-27
forum: General Help
---

### Post by Daniel Song on 2009-03-27
I am using xterm with following options.
```
xterm -fs 9 -sb -s +si -sk -sl 5000 -u8 -rightbar
```

The problem I have is that when it updates data while I am scrolling, it scrolls up while I am seeing.

For example, in xterm, do like this
```

$ ls -R /

```
then, it starts to show the all directory from / directory. While it is doing that, you may scroll up to check the contents which is shown, but you can't do it since it keeps scrolling up.

How can I avoid the problem?

---

### Post by kerry_s on 2009-03-27
```
ls -R / | less
```

q to quit
you can use the spacebar, pageup, pagedown or arrow keys
you can also use more

but why would you do something like that when you can use locate, whereis, find ?

---

### Post by Daniel Song on 2009-03-27
Thank you for response, but the example is just showing for the scrolling problem.

Actually, I am using minicom to get message from serial in xterm, and the message keeps coming to xterm like "ls -R /"

So, I need actual resolution to avoid scrolling problem. "less" cannot be used in terms of like that.

---

### Post by lloyd_b on 2009-03-27
You can try the old fashioned method - <CTRL> + S to stop, and <CTRL> + Q to restart.  These are "flow control" characters (the classic XON/XOFF version), and may or may not be honored by whatever device it is that you're talking to in Minicom...

(They do work just fine in the "ls -R" example, though :))

Lloyd B.

---

### Post by lensman3 on 2009-03-27
You are connected using a serial port to a remote host. Try setting the "TERM" environment variable on the remote host.  Use "set TERM=vt100" or TERM=xterm.  The exact syntax depends on the remote shell.  Once the TERM variable is set correctly, the serial stream will correctly dump bytes a screen at a time.  And "vi" will work.  The TERM variable sets up termap so everything will work across a serial interface.

This is old ('80s) technology and before Ethernet and networks.  Should still work fine.

Hope this helps

---

### Post by Daniel Song on 2009-03-27
Thank you, lloyd_b and lensman3,

That is what I was looking for. Actually, when I do <CTRL>+S/<CTRL>+Q, it was not working. After setting up the correct TERM variable, it works! I didn't even know about <CTRL>+S/<CTRL>+Q. It is much helpful.

I appreciate you all.

Thanks,

---

