---
title: "Connect to my *existing* session remotely"
date: 2007-08-05
forum: Desktop Environments
---

### Post by toon on 2007-08-05
Hello,

I've searched a bit around and my head is now about to explode because there are so many alternatives! vnc? vnc over nx? freenx? x11vnc? etc etc. It's crazy - in that other os all i do is connect after checking off "allow users to remotely log in..."

I've found a few guides, but all of them are mostly pretty old so I wondered what is the current, best, way of enabling me to connect to my homecomputer (kubuntu 7.04) from work (windows)? I set up vnc a year ago only to get hacked (i know, i need ssh, which is something I found out AFTEr setting it up, I couldn't get it to work when I tried).

So, what is the best way of doing it these days? Remeber, I want to be able to remotely log in to my current session at home, from any IP.

Thank you for your time.

---

### Post by MrFSL on 2007-08-05
1) Create an ssh server at the house.
2) Install x11vnc and vnc-common
```
sudo apt-get install vnc-common x11vnc
vncpasswd
```
3) From your work computer:```

ssh -l <USERNAME> -L 5900:localhost:5900 <IP_ADDRESS> -f 'x11vnc -localhost -forever -nowf -norc -notruecolor -usepw -scale 2/3 -scale_cursor 1 -display :0'
```
(<USERNAME> is the ssh user on your home/remote system, <IP_ADDRESS> in your remote IP)
4) On your local/work computer:
```
vncviewer -encodings 'copyrect tight hextile' -compresslevel 9 -quality 5 localhost
```

Explanation:
You create an ssh tunnel to your home computer forwarding local traffic on port 5900 through the tunnel. At the same time you start x11vnc on the remote computer only allowing connections from localhost. (The rest of the options you can edit to suit your needs.)

---

### Post by toon on 2007-08-05
Whoa, that didn't seem very intuitive. However if it works it works. Thank you for the quick reply, I'll have a go at it tomorrow from work. :)

---

### Post by toon on 2007-08-30
> **toon said:**
> Whoa, that didn't seem very intuitive. However if it works it works. Thank you for the quick reply, I'll have a go at it tomorrow from work. :)
Couldn't get this to work.

Remember, the work-computer is running Windows - "ssh -l" makes no sense to me there (I have to use putty, which I know can do port forwarding as well but it wouldn't be the same command), and the home computer is running Ubuntu.

---

### Post by krunge on 2007-08-30
> Couldn't get this to work.

Remember, the work-computer is running Windows - "ssh -l" makes no sense to me there (I have to use putty, which I know can do port forwarding as well but it wouldn't be the same command), and the home computer is running Ubuntu.

Try this contraption:  [http://www.karlrunge.com/x11vnc/ssvnc.html]("http://www.karlrunge.com/x11vnc/ssvnc.html")

For Windows it comes bundled with putty's plink.exe and it will run the SSH and redir for you automatically.

You can have it run the x11vnc cmd for you too if you want.  In 1.0.19 the 'Terminal Services' mode will do that automatically for you as well (and if you are already logged into your X session on the remote side it will attach to that rather than starting a virtual  X session for you).

---

### Post by OlympicSoftworks on 2007-08-31
What would one do if the goal were to login to a new graphical session remotely?

I am interested in this quite a bit, can someone please recommend a book or a couple good fairly comprehensive 'net guides on using Remote Desktops?

---

### Post by maybeway36 on 2007-08-31
I don't really like SSVNC because it doesn't connect to NON-secure VNC servers, which I am sometimes using (usually on Windows machines, but they get reinstalled practically every week anyway.) TightVNC, oddly, doesn't work with x11vnc; this left me with RealVNC.

---

### Post by krunge on 2007-09-01
> I don't really like SSVNC because it doesn't connect to NON-secure VNC servers, which I am sometimes using (usually on Windows machines

If, for some reason, you want to use SSVNC for unencrypted VNC connections, the Easter Egg in SSVNC to by-pass encryption is to use: ```
vnc://hostname:0
``` in the Host: Display entry (and to have it skip the prompts warning you about no encryption use VNC://hostname:0).  See tip #5 in its Help page.

> TightVNC, oddly, doesn't work with x11vnc; this left me with RealVNC.

Yes, I see this in your other post. Thanks for pointing this out.  It appears to be a problem with Windows TightVNC viewer 1.3.9 and x11vnc 0.8.4 and earlier.  Works OK for me on x11vnc 0.9 and later.   For 0.8.4 and earlier try adding the x11vnc option: -rfbversion 3.7

---

