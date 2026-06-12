---
title: "Gnome over HTTPS with x11vnc"
date: 2009-11-24
forum: Desktop Environments
---

### Post by MrMonster on 2009-11-24
I have tried to find a way of accessing a remote Ubuntu 9.10 server on the Internet, for which I have no access to the console at all, while being inside a network that only allows HTTP and HTTPS out (from home I can also use SSH to access it). Since I will need from time to time to use X, I thought x11vnc would be ideal. So far I have had success on a local test-server, but it's not perfect yet. I used the following command:
```
sudo x11vnc -ssl SAVE -rfbport 443 -https -noxdamage -display :0 -usepw -env X11VNC_AVOID_WINDOWS=120 -auth /var/run/gdm/auth-for-gdm-fCjiO4/database -geometry 1024x768
```Firstly, it seems that -geometry only scales the display, but what I would want is that X actually starts with the given resolution, rather then using a higher resolution that is then scaled down by x11vnc.

Secondly, I would like that Gnome only start when I connect to x11vnc (and give the right password), and shuts down automatically when I disconnect (I'm talking about the network error kind of disconnect), to save server resources. Even better would be if x11vnc was started by inetd, saving even more resources.

Thirdly, after many lines of output, the last few lines of x11vnc look like this:
```
...
Java SSL viewer URL:     https://virtual:443/   (single port)
Java SSL viewer URL:     https://virtual:5801/
Java SSL viewer URL:     http://virtual:343/
PORT=443
SSLPORT=443
```I would like that it only use 443, and not 5801 or 343 (even if they are theoretically blocked in the firewall anyway).

Last but not least, this server should actually be a web-server, and having to "sacrifice" HTTPS just to be able to login from work in case of emergency seems a bit much. Would there be some way to get the same effect while getting the HTTPS through Apache first, so that I can still use HTTPS for normal web traffic?

Those are many questions, and I'd be grateful for an answer to any of those questions.

---

### Post by krunge on 2009-11-25
> Firstly, it seems that -geometry only scales the display, but what I would want is that X actually starts with the given resolution, rather then using a higher resolution that is then scaled down by x11vnc.

In its primary operation x11vnc exports an existing X server.  It doesn't start the X server, so it can't control its resolution.  Perhaps you want tightvnc/realvnc 'vncserver' instead?

BTW 'x11vnc -create' (requires the Xvfb package) can emulate vncserver and set the geometry to anything you like (details provided if you go that route.)
> 
Secondly, I would like that Gnome only start when I connect to x11vnc (and give the right password), and shuts down automatically when I disconnect (I'm talking about the network error kind of disconnect), to save server resources. Even better would be if x11vnc was started by inetd, saving even more resources.

Do you mean just GNOME or do you mean the X server?  Only root can stop the  physical Xserver.  Virtial ones: vncserver or x11vnc+Xvfb running as an ordinary user can be stopped by that user.

> I would like that it only use 443, and not 5801 or 343 (even if they are theoretically blocked in the firewall anyway).

I think that will work with x11vnc -ssl running through inetd.

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin](http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin)[/INDENT]

outside of inetd, I don't think you can avoid those ports easily.
> 
Last but not least, this server should actually be a web-server, and having to "sacrifice" HTTPS just to be able to login from work in case of emergency seems a bit much. Would there be some way to get the same effect while getting the HTTPS through Apache first, so that I can still use HTTPS for normal web traffic?

That is tricky.  To the best of my knowledge, apache can't do connection proxying and SSL through the same port.
[INDENT][http://www.karlrunge.com/x11vnc/ssl-portal.html](http://www.karlrunge.com/x11vnc/ssl-portal.html)
[http://www.karlrunge.com/x11vnc/ssl-single-443.html](http://www.karlrunge.com/x11vnc/ssl-single-443.html)[/INDENT]

---

### Post by MrMonster on 2009-12-06
Firstly, thank you for your reply. :) I haven't got back to you yet, as I was trying to get my server online, set up the DNS records, secure the mailserver...

I have read what you said and looked at the links. I have settled for just trying to get the simplest version running, which is without apache or connect_switch. I will try those variants when a real need arises.

So far, I have settled for the following:
```
sudo x11vnc -rfbport 443 -https -noxdamage -svc -loop
```Like that, I can specify the REAL resolution which is nice, also I can use my normal account login, and anyone connecting doesn't get a hint as to which account to use (root cannot log in). The disadvantage, is that I have to type the resolution every time I log in, including "gnome" as windows manager, as I haven't work out how to set this up as default on the server side. But this is a problem I can really live with.

Unfortunately, I want this to run as a real service, meaning in the background, starting when the server boots, and restarting when I logout, or loose connection. I have tried the following in inetd (port = 443):
```
server_args = -inetd -o /var/log/x11vnc.log -rfbport 443 -https -noxdamage -svc -prog /usr/local/bin/x11vnc
```This doesn't seem to have the intended effect.

---

### Post by krunge on 2009-12-06
> So far, I have settled for the following:```
sudo x11vnc -rfbport 443 -https -noxdamage -svc -loop
```Like that, I can specify the REAL resolution which is nice, also I can use my normal account login, and anyone connecting doesn't get a hint as to which account to use (root cannot log in). The disadvantage, is that I have to type the resolution every time I log in, including "gnome" as windows manager, as I haven't work out how to set this up as default on the server side.
It is buried in the '-display WAIT:...' help documentation, but you can supply the FD_GEOM and FD_SESS env. vars to set these (and many others), e.g.:
```

x11vnc -rfbport 443 -http_ssl -svc -loop -env FD_GEOM=800x600 -env FD_SESS=twm

```
> 
Unfortunately, I want this to run as a real service, meaning in the background, starting when the server boots, and restarting when I logout, or loose connection. I have tried the following in inetd (port = 443):


I have this in /etc/inetd.conf on a test machine and it seems to work fine (same behavior as the above command):
```

443 stream  tcp nowait  root  /usr/sbin/tcpd /home/runge/bin/x11vnc -inetd -svc -o /var/tmp/x11vnc-443.log -http_ssl -prog /home/runge/bin/x11vnc -env PATH=/usr/bin:bin -env FD_GEOM=800x600x8 -env FD_SESS=twm

```
BTW, the PATH setting is because some inetd's leave it empty.  x11vnc 0.9.9 will automatically set it to the above and so it won't be needed. The -prog will still be needed since inetd might not set argv[0] to the full path to the program. Let me know if something like that works for you or not.

---

### Post by krunge on 2009-12-06
BTW, I was tricked by your usage of '-https' and used it myself in testing. That will actually work (as we have seen) but more appropriate is '-http_ssl' (related to classes/ssl dir and not a separate https applet download port.)
[INDENT][http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-https](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-https)
[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-http_ssl](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-http_ssl)[/INDENT]
This gets rid of that [https://virtual:5801/](https://virtual:5801/) port you were seeing.

---

### Post by MrMonster on 2009-12-07
Firstly, the "-env FD_GEOM=1024x768 -env FD_SESS=gnome" work like a charm. Thank you. But trying to run it as a service It still fails. My current service definition:

```
cat /etc/xinetd.d/x11vnc
service x11vnc
{
        type            = UNLISTED
        port            = 443
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/local/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -http_ssl -env FD_GEOM=1024x768 -env FD_SESS=gnome -ssltimeout 60 -readtimeout 60 -timeout 60 -noxdamage -svc -prog /usr/local/bin/x11vnc
        disable         = no
}
```And the resulting /var/log/x11vnc.log logfile:

```
07/12/2009 21:47:28 x11vnc version: 0.9.9 lastmod: 2009-11-18  pid: 14791
07/12/2009 21:47:28
07/12/2009 21:47:28 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
07/12/2009 21:47:28
07/12/2009 21:47:28 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
07/12/2009 21:47:28
07/12/2009 21:47:28 Initializing SSL (server connect mode).
07/12/2009 21:47:28 RAND_file_name:
07/12/2009 21:47:28 initialized PRNG with 64 random bytes.
07/12/2009 21:47:28 created  512 bit temporary RSA key: 0.015s
07/12/2009 21:47:28 created 1024 bit temporary RSA key: 0.081s
07/12/2009 21:47:28
07/12/2009 21:47:28 Using SSL Certificate:

-----BEGIN CERTIFICATE-----
...blabla...
-----END CERTIFICATE-----

07/12/2009 21:47:28 using PEM /root/.vnc/certs/server.pem  0.000s
07/12/2009 21:47:28
07/12/2009 21:47:28
07/12/2009 21:47:28 check_httpdir: trying to guess httpdir... /usr/local/bin/x11vnc
07/12/2009 21:47:28 check_httpdir: guessed directory:
07/12/2009 21:47:28    /usr/local/bin/../share/x11vnc/classes/ssl
07/12/2009 21:47:28 http_connections: turning on http service.
07/12/2009 21:47:28 Listening for HTTP connections on TCP port 5800
07/12/2009 21:47:28   URL http://test:5800
07/12/2009 21:47:28 SSL: (inetd) spawning helper process to handle: 192.168.0.3:60135
07/12/2009 21:47:28 SSL: helper for peerport 60135 is pid 14792:
07/12/2009 21:47:28 check_vnc_tls_mode: waited: 0.000017 / 1.40 input: SSL Handshake
07/12/2009 21:47:48 sig: 14, ssl_init[14792] timed out.
07/12/2009 21:47:48 SSL: accept_openssl: cookie from ssl_helper[14792] FAILED. 0

```I have added the "-ssltimeout 60 -readtimeout 60 -timeout 60" because it says it got a timeout, but it carried on happening after maybe 17 seconds, instead of the configured 60.

Doing the same thing from the console, with "-rfbport 443 -https" instead of "-inetd -http_ssl" work perfectly (so far).

---

### Post by MrMonster on 2009-12-07
**All is lost!**  :( 
I was using the non-service version to install some graphic app, and the updater said there was stuff to update, so I told it to go ahead, and now nothing works anymore. I even tried rebooting the server, but in vain.

```
08/12/2009 00:07:44 wait_for_client: unixpw finished.
08/12/2009 00:07:44 wait_for_client: running: env X11VNC_SKIP_DISPLAY='' /bin/sh /tmp/x11vnc-find_display.AxJRBP
08/12/2009 00:07:45 wait_for_client: find display cmd failed
08/12/2009 00:07:45 wait_for_client: running: env USER='username' FD_GEOM='' FD_SESS='' FD_OPTS='' FD_PROG='' FD_XSRV='' FD_CUPS='' FD_ESD='' FD_NAS='' FD_SMB='' FD_TAG='' FD_XDUMMY_NOROOT='' /bin/sh /tmp/x11vnc-find_display.AxJRBP Xvfb
trying N=20 ...
/usr/bin/xauth:  error in locking authority file /home/username/.Xauthority
/usr/bin/xauth:  error in locking authority file /home/username/.Xauthority
/usr/bin/startx /bin/su - username -c /tmp/.cd3756803 -- /usr/bin/Xvfb :20 -screen 0 1280x1024x16 +kb -cc 4 -nolisten tcp -auth /tmp/.xas375629256
/usr/bin/nohup: appending output to `nohup.out'

[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.45" is not allowed to own the service "org.x.config.display20" due to security policies in the configuration file)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
No protocol specified
/usr/bin/xterm Xt error: Can't open display: :20
08/12/2009 00:07:47 unixpw_accept switched to user: username
rm: cannot remove `/tmp/.cd3756803': Operation not permitted

waiting for X server to shut down


08/12/2009 00:07:48 ***************************************
08/12/2009 00:07:48 *** XOpenDisplay failed (:20)

*** x11vnc was unable to open the X DISPLAY: ":20", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:
...
``` ](*,)

---

### Post by krunge on 2009-12-07
> Firstly, the "-env FD_GEOM=1024x768 -env FD_SESS=gnome" work like a charm. Thank you. But trying to run it as a service It still fails. My current service definition:

cat /etc/xinetd.d/x11vnc
...

I have an ubuntu 9.10 (karmic) Virtualbox image that I can test with. I have put in the same xinetd entry as you show above, but I have removed all of the 'timeouts' you included and I changed it to point to the location of my x11vnc binary (x11vnc: 0.9.9 lastmod: 2009-12-07.)

Java applet ssl access all works fine for me.  Once you get your machine fixed we can try to exchange x11vnc.log's (remember to use -oa for appending.)  You can get my email address at my x11vnc site.

---

### Post by krunge on 2009-12-07
> **MrMonster said:**
> **All is lost!**  :( 
I was using the non-service version to install some graphic app, and the updater said there was stuff to update, so I told it to go ahead, and now nothing works anymore.

That sounds awful!  Makes me nervous about upgrading my 9.10 image (although I did it yesterday w/o any problems.)

BTW, some of your DBus and Hal error messages occur in my logs too, but even with those messages it worked for me via xinetd.

It sounds like something important on your system got broken, like libc. Check /var/log/messages if you haven't already.

---

### Post by MrMonster on 2009-12-08
OK, looks like a "User Error". :oops:  I must have somehow replaced the self-built 0.9.9 version with the 0.9.3 version from the Ubuntu repositories. :-s So things are working again. This leaves me with two lesser problems: firstly, the INEDT configuration still doesn't work (will post about that later), and I need something like "make clean" for X/Gnome, so that I can kill all processes, and remove all hidden temporary files that make up for the complete X-Windows system state, when the X client crashes. That is in itself unrelated, and hopefully Google will help...

---

### Post by krunge on 2009-12-08
> I must have somehow replaced the self-built 0.9.9 version with the 0.9.3 version from the Ubuntu repositories. :-s So things are working again. 

Ah, that explains the output you posted and is not as bad as it originally sounded.  Be sure to use the 0.9.9 lastmod: 2009-12-07 I uploaded yesterday (BTW, it is refreshing to meet someone on these forums who can build from a tarball!)
> 
This leaves me with two lesser problems: firstly, the INEDT configuration still doesn't work (will post about that later), 

Yes we can exchange '-oa /var/log/x11vnc.log' log files when you are ready. Send it to me in PM or email if you like.
> 
and I need something like "make clean" for X/Gnome, so that I can kill all processes, and remove all hidden temporary files that make up for the complete X-Windows system state, when the X client crashes. That is in itself unrelated, and hopefully Google will help...
Yeah, your pasted output suggested some stale lock files or files owned by some other user. Good luck.

---

### Post by tehowe on 2011-02-16
I need to do something very similar, though unlike MrMonster I'm not concerned about getting x11vnc as a service just *yet*, at least not until I know I can get this part to work in as simple a form as possible.

Yesterday at the site I wish to make the connection from, I noticed that 443 is open and all other ports were closed - the firewall must have been down temporarily because all ports are stealthed again today. However, the web proxy - let's call it web.company.ca:80 - is operational as always. So my plan is to SSL (or SSH) tunnel through this proxy and/or port 443, using **either the java client on IE or via the portable SSVNC, whichever is easier.** I'm also trying to do it without putting Apache up as suggested here... 

[http://www.karlrunge.com/x11vnc/ssl-portal.html#no-apache](http://www.karlrunge.com/x11vnc/ssl-portal.html#no-apache)

(I will if I need to, I'd have to sift through potential conflicts with my development XAMPP environment though)

Mr. Runge, is there any chance you could help with any of your great secret sauce command line invocations? 

The steps I've taken so far...

**1. **Opened 443 on my router, it now points to 192.168.x.xxx:443

I've used the command line you and MrMonster jointly suggested in my home shell before setting off for work:

> x11vnc -rfbport 443 -http_ssl -svc -loop -env FD_GEOM=1280x720 -env FD_SESS=gnome**2. From IE**
Tried [https://xxx.myvnc.com:443/proxy.vnc](https://xxx.myvnc.com:443/proxy.vnc)
Tried [https://xxx.myvnc.com:443/](https://xxx.myvnc.com:443/)

Is any additional configuration needed to get the java .jar working and sent?

**3. From **(Windows)** SSVNC **
Tried **VNC Host: Display** localhost:0 (also: xxx.myvnc.com:0) **Proxy/Gateway: **web.company.ca:80,xxx.myvnc.com:443

Is this on the right track at all?

Ideally, I'd like to log in with my regular shell password. I feel I'm hitting around the mark here but haven't quite hit on it yet. Could you step us through it please?

---

### Post by krunge on 2011-02-16
> **tehowe said:**
> I need to do something very similar, though unlike MrMonster I'm not concerned about getting x11vnc as a service just *yet*, at least not until I know I can get this part to work in as simple a form as possible.
Please remove '-loop' while testing.  Restart x11vnc manually each test.

Collect x11vnc output into a file (-o option handy) and attach full output to this thread.

Do it for these cases:

[INDENT]1) Web browser going to the 'https://xxx.myvnc.com:443/proxy.vnc'.  Also attach Java console output.

2) Using SSVNC on windows.  Put 'web.company.ca:80' in 'Proxy/Gateway' and put 'xxx.myvnc.com:443' in 'VNC Host-Display'.  Also attach STUNNEL.EXE output.  If that fails, uncheck 'Verify All Certs' and try again and send all the logs for that case too.[/INDENT]

BTW, I think SSVNC will be the easier of the two methods (better chance of success I mean.)

---

### Post by tehowe on 2011-02-17
> **krunge said:**
> Please remove '-loop' while testing.  Restart x11vnc manually each test.

Collect x11vnc output into a file (-o option handy) and attach full output to this thread.

Do it for these cases:
[INDENT]1) Web browser going to the 'https://xxx.myvnc.com:443/proxy.vnc'.  Also attach Java console output.

2) Using SSVNC on windows.  Put 'web.company.ca:80' in 'Proxy/Gateway' and put 'xxx.myvnc.com:443' in 'VNC Host-Display'.  Also attach STUNNEL.EXE output.  If that fails, uncheck 'Verify All Certs' and try again and send all the logs for that case too.[/INDENT]BTW, I think SSVNC will be the easier of the two methods (better chance of success I mean.)

You were right - I don't think the java app was able to find a helper port - it connected, loaded, tried to run but ended up with the red 'x'. Ssvnc worked brilliantly though, that is once I figured out you need to run it with sudo:

```
sudo x11vnc -rfbport 443 -http_ssl -svc -loop -env FD_GEOM=1280x720 -env FD_SESS=gnome
```

Thanks! This rules.

For others browsing this thread, the '-loop' option keeps your x11 server running so that you can reconnect to it after a disconnect.  If you want x11vnc to run as a service, there's more on that in the rest of the thread.  This works very nicely, and ssvnc has the additional advantage over the java applet of being able to scale the tunneled desktop and display it fullscreen. 

One note, for me the FD_GEOM parameter doesn't override the local resolution of the server's X session, so be sure to adjust it with the desktop size applet as required.

---

### Post by krunge on 2011-02-17
> once I figured out you need to run it with sudo:

```
sudo x11vnc -rfbport 443 -http_ssl -svc -loop -env FD_GEOM=1280x720 -env FD_SESS=gnome
```

Yes, to have any program listen on a port below 1024 it needs to run as root.
> 
One note, for me the FD_GEOM parameter doesn't override the local resolution of the server's X session, so be sure to adjust it with the desktop size applet as required.
Are you using this to connect to your existing X session on the physical graphics hardware?   The main idea for the "-svc" mode is to provide terminal services by running the virtual X server Xvfb (requires adding the 'xvfb' package.)  This is multiuser, unix userid/password and does everything in RAM. But when reconnecting it will check if you already have an X session and connect to that (even if it is on the physical graphics hardware, however see the FD_TAG option.)

The point of the previous paragraph is that the FD_GEOM only applies to Xvfb virtual X servers, not the physical one (as you have already indicated.)

---

