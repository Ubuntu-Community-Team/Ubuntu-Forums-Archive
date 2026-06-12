---
title: "x11vnc as service"
date: 2008-10-29
forum: Desktop Environments
---

### Post by chatuu on 2008-10-29
Well  i instaled x11vnc and configured it as service in /etc/xinetd.d/x11vnc

and in this archive is that 

service x11vnc
{
port = 5900
type = UNLISTED
socket_type = stream
protocol = tcp
wait = no
user = root
server = /usr/bin/x11vnc 
server_args = -inetd -o /var/log/x11vnc.log -httpdir /usr/bin/javateste -display :0 -auth /var/lib/gdm/:0.Xauth -many -rfbauth /root/.vnc/passwd -bg
disable = no
}


BUT, the httpdir when used like this as service is does't work, the java applet does't start... i don't know why, when i simple tipe in terminal 

#x11vnc -httpdir /usr/bin/javateste   

it works fine... why the flag does't work when using as service oc xinet ?

thanks

---

### Post by krunge on 2008-10-29
> **chatuu said:**
> 
service x11vnc
{
port = 5900
type = UNLISTED
socket_type = stream
protocol = tcp
wait = no
user = root
server = /usr/bin/x11vnc 
server_args = -inetd -o /var/log/x11vnc.log -httpdir /usr/bin/javateste -display :0 -auth /var/lib/gdm/:0.Xauth -many -rfbauth /root/.vnc/passwd -bg
disable = no
}

BUT, the httpdir when used like this as service is does't work, the java applet does't start... i don't know why, when i simple tipe in terminal 

#x11vnc -httpdir /usr/bin/javateste   

When you run it this way, in a terminal, it is also listening on port 5800 waiting for your web browser to serve up the java applet to it via HTTP.  When you run it out of xinetd nothing is listening on port 5800.

It might be possible to use the '-display WAIT:cmd=HTTPONCE' to set up a 2nd xinetd entry (i,e, on port 5800) that will only serve the java applet.

In SSL mode, x11vnc can do both out of port 5900, but I don't think it can for non-SSL connections.

---

### Post by krunge on 2008-10-29
> **krunge said:**
> 
It might be possible to use the '-display WAIT:cmd=HTTPONCE' to set up a 2nd xinetd entry (i,e, on port 5800) that will only serve the java applet.

I got this working just now in non-SSL mode.  It is a little tricky because in HTTPONCE mode it has limited info about the ports...

First, add a 2nd xinetd entry, in addition to your 5900 one, that looks like this:
```

service x11vnc_http
{
   port = 5800
   type = UNLISTED
   socket_type = stream
   protocol = tcp
   wait = no
   user = root
   server = /usr/bin/x11vnc
   server_args = -inetd -o /var/log/x11vnc_http.log -httpdir /usr/bin/javateste -display WAIT:cmd=HTTPONCE
   disable = no
}

```
and restart the inetd server.

Make SURE your 'index.vnc' in '/usr/bin/javateste' (why did you put things there??) has a $PARAMS string near the bottom like this:
```

<!-- index.vnc - default html page for Java VNC viewer applet.  On any file
     ending in .vnc, the HTTP server embedded in Xvnc will substitute the
     following variables when preceded by a dollar: USER, DESKTOP, DISPLAY,
     APPLETWIDTH, APPLETHEIGHT, WIDTH, HEIGHT, PORT, PARAMS.  Use two dollar
     signs ($$) to get a dollar sign in the generated html. -->

<HTML>
<TITLE>
$USER's $DESKTOP desktop ($DISPLAY)
</TITLE>
<APPLET CODE=VncViewer.class ARCHIVE=VncViewer.jar
        WIDTH=$APPLETWIDTH HEIGHT=$APPLETHEIGHT>
<param name=PORT value=$PORT>
<param name="Open New Window" value=yes>
$PARAMS
</APPLET>
<BR>
<A href="http://www.tightvnc.com/">www.TightVNC.com</A>
</HTML>

```

If your browser is Windows Internet Exploder, you might need to put $PARAMS before the name=PORT line or get rid of the name=PORT line altogether. You could also hardwire the PORT value to 5900 if you wanted to do that instead.

Then point the browser to URL:  [http://hostname:5800/?PORT=5900](http://hostname:5800/?PORT=5900)

The PORT=5900 gets written into the $PARAMS and so the browser reconnects to 5900 via VNC instead of getting confused about the port number (I think it uses zero).

I hope that works.

BTW, your port 5900 xinetd has some useless x11vnc options (-bg and -many make no sense in inetd mode), use this one instead:

```

service x11vnc
{
   port = 5900
   type = UNLISTED
   socket_type = stream
   protocol = tcp
   wait = no
   user = root
   server = /usr/bin/x11vnc
   server_args = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -rfbauth /root/.vnc/passwd
   disable = no
}

```

---

### Post by djfg on 2009-01-25
well, first of all thanks for the very usefull xinetd solution, at least the first part of it - it works great.

As for the second part - enabling the java client - I seem to have found a better solution, provided that one has a web server installed. 

you should simply host the applet as any other

someone wrote a good tutorial which is posted [[COLOR="Red"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=107503")

greetz :p
Djordje

---

