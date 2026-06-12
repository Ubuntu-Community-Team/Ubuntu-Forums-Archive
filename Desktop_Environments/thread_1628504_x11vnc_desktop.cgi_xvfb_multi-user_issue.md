---
title: "x11vnc desktop.cgi xvfb multi-user issue"
date: 2010-11-22
forum: Desktop Environments
---

### Post by bcarl17 on 2010-11-22
Hello,

I currently have x64 10.10 Xubuntu running on VirtualBox on a Windows 7 machine.  I have set up x11vnc's desktop.cgi script in a  cherokee web server with ssl to connect to the box from anywhere with just a browser.  Everything works fine, as I have tested it from outside the house and was able to easily connect to my desktop session which is set to auto-login.  My friend wanted to test it out also, and I read that the cgi script will create an xvfb session if the user doesn't have a desktop already running.  So I created him an account, logged in through virtualbox to make sure he had a desktop created with icons and such, then logged out and logged back in as myself (the default state of the box)  When I tried to log in as him through the cgi script The Java VNC server opens to the right geometry, however all I get is a black screen with a cursor.  When I checked the logs this is what I got:


(Edited to save space: Full log in next reply)

---

### Post by krunge on 2010-11-22
What user does the webserver run as?  Is it running desktop.cgi as that user (or another one?)  In either case is that user limited somehow by the system to do things?  (I've never used SELINUX, but I see its messages in your output and so I wonder if the user is restricted somehow.)

If you could configure the webserver to run CGI scripts as an ordinary user (I've done this before with apache) it might work...

Since your desktop is already running, on physical display :0, desktop.cgi did not have to start Xvfb, and that seems to be where the problem is.  It will probably fail for your userid too if you log out of the physical display.

---

### Post by bcarl17 on 2010-11-22
Hah, never figured THE Karl Runge would reply :)

The cherokee server is running as www-data
Which is just a default user it created similar to apache's nobody.

Maybe I'll try making www-data the owner of the cgi script and maybe that will help.

Oh and btw: your software and script are great!

---

### Post by bcarl17 on 2010-11-22
So I chown of the cgi script to www-data.
Still no dice, it gave me the same black screen.
I then did a su to www-data and ran x11vnc -create with no errors.
I guess that should mean that the web server can create a xvfb.
Here is the full log from a failed login when another user is logged in:


22/11/2010 19:21:41 passing arg to libvncserver: -rfbport
22/11/2010 19:21:41 passing arg to libvncserver: 43123
22/11/2010 19:21:41 x11vnc version: 0.9.10 lastmod: 2010-04-28  pid: 10017
22/11/2010 19:21:41 
22/11/2010 19:21:41 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
22/11/2010 19:21:41 
22/11/2010 19:21:41 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
22/11/2010 19:21:41 
22/11/2010 19:21:41 Initializing SSL (server connect mode).
22/11/2010 19:21:41 RAND_file_name: /home/magog/.rnd
22/11/2010 19:21:41 initialized PRNG with 1088 random bytes.
22/11/2010 19:21:41 created  512 bit temporary RSA key: 0.003s
22/11/2010 19:21:41 created 1024 bit temporary RSA key: 0.025s
22/11/2010 19:21:41 using PEM /opt/vnc/ssl/server.pem  0.000s
22/11/2010 19:21:41 
22/11/2010 19:21:41 
22/11/2010 19:21:41 Listening for VNC connections on TCP port 43123
22/11/2010 19:21:41 openssl_port: listen on port/sock 43123/3
22/11/2010 19:21:41 openssl_port: listen on port/sock 43123/4 (ipv6)

The SSL VNC desktop is:  raphael:37223
22/11/2010 19:21:41 possible aliases:  raphael:43123, raphael::43123
22/11/2010 19:21:41 
22/11/2010 19:21:45 SSL: accept_openssl(OPENSSL_VNC)
22/11/2010 19:21:45 SSL: spawning helper process to handle: 192.168.1.3:50848
22/11/2010 19:21:45 SSL: helper for peerport 50848 is pid 10025: 
22/11/2010 19:21:45 connect_tcp: trying:   127.0.0.1 20000
22/11/2010 19:21:45 SSL: ssl_init[10025]: 5/5 initialization timeout: 20 secs.
22/11/2010 19:21:45 SSL: ssl_helper[10025]: SSL_accept() succeeded for: 192.168.1.3:50848
22/11/2010 19:21:45 SSL: ssl_helper[10025]: Cipher: TLSv1/SSLv3 RC4-MD5 Proto: TLSv1
22/11/2010 19:21:45 SSL: ssl_helper[10025]: accepted client 192.168.1.3 x509 peer cert is null
22/11/2010 19:21:45 SSL: handshake with helper process[10025] succeeded.
22/11/2010 19:21:45   other clients:
22/11/2010 19:21:45 incr accepted_client=1 for 127.0.0.1:50853  sock=5
22/11/2010 19:21:45 rfbProcessClientProtocolVersion: not a valid RFB client: GET /check.h
22/11/2010 19:21:45 SSL: ssl_xfer[10025]: closing sockets 0, 5, 5
22/11/2010 19:21:45 SSL: ssl_helper[10025]: exit case 7 (ssl_xfer done)
22/11/2010 19:21:45 client progressed=0 in 15/10 0.029283 s
22/11/2010 19:21:45 client_count: 0
22/11/2010 19:21:45 sending SIGTERM to ssl_helper_pid: 10025
22/11/2010 19:21:45 connect_once: invalid password or early disconnect.  0
22/11/2010 19:21:45 connect_once: waiting for next connection.
22/11/2010 19:21:45 Client 192.168.1.3 gone
22/11/2010 19:21:45 Statistics             events    Transmit/ RawEquiv ( saved)
22/11/2010 19:21:45  TOTALS              :      0 |         0/        0 (  0.0%)
22/11/2010 19:21:45 Statistics             events    Received/ RawEquiv ( saved)
22/11/2010 19:21:45  TOTALS              :      0 |         0/        0 (  0.0%)
22/11/2010 19:21:46 SSL: accept_openssl(OPENSSL_VNC)
22/11/2010 19:21:46 SSL: spawning helper process to handle: 192.168.1.3:50849
22/11/2010 19:21:46 SSL: helper for peerport 50849 is pid 10026: 
22/11/2010 19:21:46 connect_tcp: trying:   127.0.0.1 20000
22/11/2010 19:21:46 SSL: ssl_init[10026]: 5/5 initialization timeout: 20 secs.
22/11/2010 19:21:46 SSL: ssl_helper[10026]: SSL_accept() succeeded for: 192.168.1.3:50849
22/11/2010 19:21:46 SSL: ssl_helper[10026]: Cipher: TLSv1/SSLv3 RC4-MD5 Proto: TLSv1
22/11/2010 19:21:46 SSL: ssl_helper[10026]: accepted client 192.168.1.3 x509 peer cert is null
22/11/2010 19:21:46 SSL: handshake with helper process[10026] succeeded.
22/11/2010 19:21:46   other clients:
22/11/2010 19:21:46 incr accepted_client=1 for 127.0.0.1:50854  sock=5
22/11/2010 19:21:46 client progressed=0 in 15/10 0.023484 s
22/11/2010 19:21:46 Client Protocol Version 3.3
22/11/2010 19:21:46 Protocol version sent 3.3, using 3.3
22/11/2010 19:21:46 Using image quality level 6 for client 192.168.1.3
22/11/2010 19:21:46 Enabling X-style cursor updates for client 192.168.1.3
22/11/2010 19:21:46 Enabling full-color cursor updates for client 192.168.1.3
22/11/2010 19:21:46 Enabling cursor position updates for client 192.168.1.3
22/11/2010 19:21:46 Enabling LastRect protocol extension for client 192.168.1.3
22/11/2010 19:21:46 Enabling NewFBSize protocol extension for client 192.168.1.3
22/11/2010 19:21:46 Using tight encoding for client 192.168.1.3
22/11/2010 19:21:46 Pixel format for client 192.168.1.3:
22/11/2010 19:21:46   32 bpp, depth 24, little endian
22/11/2010 19:21:46   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
22/11/2010 19:21:46 no translation needed
22/11/2010 19:21:46 wait_for_client: got client
22/11/2010 19:21:46 client progressed=1 in 0/0 0.000006 s
22/11/2010 19:21:46 client_set_net: 192.168.1.3  0.0040
22/11/2010 19:21:46 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.dT8Nan
xauth:  error in locking authority file /home/magog/.Xauthority
22/11/2010 19:21:46 wait_for_client: find display cmd failed.
22/11/2010 19:21:46 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc-find_display.dT8Nan Xvfb
trying N=20 ...
redir_daemon=
/usr/bin/xauth:  error in locking authority file /home/magog/.Xauthority
/usr/bin/xauth:  error in locking authority file /home/magog/.Xauthority
/usr/bin/xinit /usr/bin/xterm -- /usr/bin/Xvfb :20 -screen 0 1024x768x24 -cc 4 -nolisten tcp -auth /tmp/.xas100829931.DXiy4X 

[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
No protocol specified

waiting for X server to begin accepting connections 22/11/2010 19:21:48 Using X display :20
22/11/2010 19:21:48 rootwin: 0x100 reswin: 0x200001 dpy: 0x1135640
22/11/2010 19:21:48 
22/11/2010 19:21:48 ------------------ USEFUL INFORMATION ------------------
.22/11/2010 19:21:48 X DAMAGE available on display, using it for polling hints.
22/11/2010 19:21:48   To disable this behavior use: '-noxdamage'
22/11/2010 19:21:48 
22/11/2010 19:21:48   Most compositing window managers like 'compiz' or 'beryl'
22/11/2010 19:21:48   cause X DAMAGE to fail, and so you may not see any screen
22/11/2010 19:21:48   updates via VNC.  Either disable 'compiz' (recommended) or
22/11/2010 19:21:48   supply the x11vnc '-noxdamage' command line option.
22/11/2010 19:21:48 
22/11/2010 19:21:48 Wireframing: -wireframe mode is in effect for window moves.
22/11/2010 19:21:48   If this yields undesired behavior (poor response, painting
22/11/2010 19:21:48   errors, etc) it may be disabled:
22/11/2010 19:21:48    - use '-nowf' to disable wireframing completely.
22/11/2010 19:21:48    - use '-nowcr' to disable the Copy Rectangle after the
22/11/2010 19:21:48      moved window is released in the new position.
22/11/2010 19:21:48   Also see the -help entry for tuning parameters.
22/11/2010 19:21:48   You can press 3 Alt_L's (Left "Alt" key) in a row to 
22/11/2010 19:21:48   repaint the screen, also see the -fixscreen option for
22/11/2010 19:21:48   periodic repaints.
22/11/2010 19:21:48 
22/11/2010 19:21:48 XFIXES available on display, resetting cursor mode
22/11/2010 19:21:48   to: '-cursor most'.
22/11/2010 19:21:48   to disable this behavior use: '-cursor arrow'
22/11/2010 19:21:48   or '-noxfixes'.
22/11/2010 19:21:48 using XFIXES for cursor drawing.
22/11/2010 19:21:48 GrabServer control via XTEST.
22/11/2010 19:21:48 
22/11/2010 19:21:48 Scroll Detection: -scrollcopyrect mode is in effect to
22/11/2010 19:21:48   use RECORD extension to try to detect scrolling windows
22/11/2010 19:21:48   (induced by either user keystroke or mouse input).
22/11/2010 19:21:48   If this yields undesired behavior (poor response, painting
22/11/2010 19:21:48   errors, etc) it may be disabled via: '-noscr'
22/11/2010 19:21:48   Also see the -help entry for tuning parameters.
22/11/2010 19:21:48   You can press 3 Alt_L's (Left "Alt" key) in a row to 
22/11/2010 19:21:48   repaint the screen, also see the -fixscreen option for
22/11/2010 19:21:48   periodic repaints.
22/11/2010 19:21:48 
22/11/2010 19:21:48 XKEYBOARD: number of keysyms per keycode 6 is greater
22/11/2010 19:21:48   than 4 and 2 keysyms are mapped above 4.
22/11/2010 19:21:48   Automatically switching to -xkb mode.
22/11/2010 19:21:48   If this makes the key mapping worse you can
22/11/2010 19:21:48   disable it with the "-noxkb" option.
22/11/2010 19:21:48   Also, remember "-remap DEAD" for accenting characters.
22/11/2010 19:21:48 
22/11/2010 19:21:48 X FBPM extension not supported.
Xlib:  extension "DPMS" missing on display ":20.0".
22/11/2010 19:21:48 X display is not capable of DPMS.
22/11/2010 19:21:48 --------------------------------------------------------
22/11/2010 19:21:48 
22/11/2010 19:21:48 Default visual ID: 0x21
22/11/2010 19:21:48 Read initial data from X display into framebuffer.
22/11/2010 19:21:48 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
22/11/2010 19:21:48 rfbNewFramebuffer(0x1123cb0, 0x0, 1024, 768, 8, 1, 4)
22/11/2010 19:21:48 Pixel format for client 192.168.1.3:
22/11/2010 19:21:48   32 bpp, depth 24, little endian
22/11/2010 19:21:48   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
22/11/2010 19:21:48 
22/11/2010 19:21:48 X display :20.0 is 32bpp depth=24 true color
22/11/2010 19:21:48 
22/11/2010 19:21:48 calling setTranslateFunction()...
22/11/2010 19:21:48 Pixel format for client 192.168.1.3:
22/11/2010 19:21:48   32 bpp, depth 24, little endian
22/11/2010 19:21:48   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
22/11/2010 19:21:48 no translation needed
22/11/2010 19:21:48   done.
22/11/2010 19:21:48 TS_REDIR is empty, restarting...
22/11/2010 19:21:48 
22/11/2010 19:21:48 Xinerama is present and active (e.g. multi-head).
22/11/2010 19:21:48 Xinerama: number of sub-screens: 1
22/11/2010 19:21:48 Xinerama: no blackouts needed (only one sub-screen)
22/11/2010 19:21:48 
22/11/2010 19:21:48 fb read rate: 849 MB/sec
22/11/2010 19:21:48 fast read: reset wait  ms to: 10
22/11/2010 19:21:48 fast read: reset defer ms to: 10
22/11/2010 19:21:48 The X server says there are 10 mouse buttons.
22/11/2010 19:21:48 screen setup finished.
22/11/2010 19:21:48 

The SSL VNC desktop is:  raphael:37223
22/11/2010 19:21:48 possible aliases:  raphael:43123, raphael::43123

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)

22/11/2010 19:21:48 Battling with something for -norepeat!! (1 resets left)
22/11/2010 19:21:48 Disabled X server key autorepeat.
22/11/2010 19:21:48   to force back on run: 'xset r on' (2 times)
22/11/2010 19:21:48 created   xdamage object: 0x200024
22/11/2010 19:21:48 Sending rfbEncodingNewFBSize for resize to (1024x768)

No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
.No protocol specified
/usr/bin/xmodmap:  unable to open display ':20'
.
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
.22/11/2010 19:22:34 created selwin: 0x200025
22/11/2010 19:22:34 called initialize_xfixes()
.
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
.22/11/2010 19:23:00 SSL: ssl_xfer[10026]: tv_cutover: 70
No protocol specified
..
(this shows up about 50 more times)
giving up.
/usr/bin/xinit:  Resource temporarily unavailable (errno 11):  unable to connect to X server

waiting for X server to shut down 

/usr/bin/xinit:  Server error.
caught XIO error:
22/11/2010 19:25:49 deleted 32 tile_row polling images.
22/11/2010 19:25:49 SSL: ssl_xfer[10026]: closing sockets 0, 5, 5
22/11/2010 19:25:49 SSL: ssl_helper[10026]: exit case 7 (ssl_xfer done)



(edited to remove No Protocol Specified multiple times to save space)

---

### Post by bcarl17 on 2010-11-22
I also didn't know if I needed to specify a session_type.
Here is my full modified desktop.cgi with my added options and
a elaborate login page:

I also have two configs set in a .conf file that specifies -ssl and the location of my x.509
and a find_free_port that gives it a range of 1000 ports to use.

(edited to a diff)

Here is a diff of your original file and my file.  First file is yours, second is mine.
magog@raphael:~/Downloads$ diff ./desktop.cgi /opt/vnc/cgi-bin/desktop.cgi
364c364
< my $session_types = '';
---
> my $session_types = 'xfce';
388,407c388,478
< <title>x11vnc web access</title>
< <h3>x11vnc web access</h3>
< <form action="$ENV{REQUEST_URI}" method="post">
<  <table border="0">
<   <tr><td colspan=2><h2>Login</h2></td></tr>
<   <tr><td>Username:</td><td>
<   <input type="text" name="username" maxlength="40" value="_USERNAME_">
<   </td></tr>
<   <tr><td>Password:</td><td>
<   <input type="password" name="password" maxlength="50">
<   </td></tr>
<   <tr><td>Geometry:</td><td>
<   <input type="text" name="geometry" maxlength="40" value="_GEOMETRY_">
<   </td></tr>
<   <!-- session -->
<   <tr><td colspan="2" align="right">
<   <input type="submit" name="submit" value="Login">
<   </td></tr>
<  </table>
< </form>
---
> <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
> <html xmlns="http://www.w3.org/1999/xhtml">
> <head>
> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
> <title>Raphael Logon</title>
> <style type="text/css">
> body {
>       font: 100%/1.4 Verdana, Arial, Helvetica, sans-serif;
>       background: #8D7AB4;
>       margin: 0;
>       padding: 0;
>       color: #000;
> }
> ul, ol, dl {
>       padding: 0;
>       margin: 0;
> }
> h1, h2, h3, h4, h5, h6, p {
>       margin-top: 0;
>       padding-right: 15px;
>       padding-left: 15px;
> }
> h1 {
>       text-align: center;
> }
> a img {
>       border: none;
> }
> a:link {
>       color: #42413C;
>       text-decoration: underline;
> }
> a:visited {
>       color: #6E6C64;
>       text-decoration: underline;
> }
> a:hover, a:active, a:focus {
>       text-decoration: none;
> }
> .container {
>       width: 960px;
>       background: #FFF;
>       margin: 0 auto;
> }
> .header {
>       background: #0E133A;
>       font: "Times New Roman", Times, serif;
>       color: #B7BEFF;
>       font-size: 100px;
>       text-align: center;
> }
> .headspace {
>       background: #8D7AB4;
>       height: 15px;
> }
> .content {
>
>       padding: 10px 0;
>       background:  #333;
> }
> .footer {
>       padding: 10px 0;
>       background: #CCC49F;
> }
> </style>
> </head>
> <body>
> <div class="container">
>   <div class="header"><strong>Raphael Logon</strong></div>
>   <div class="headspace"></div>
>   <div class="content">
>     <h1>Welcome sir...  Credentials please...</h1>
>     <form action="$ENV{REQUEST_URI}" method="post">
>     <p style="text-align:center">
>       <label for="username">Username</label>
>       <input type="text" name="username" id="username" value="_USERNAME_" />
>       <br />
>       <label for="password">Password</label>
>       <input type="password" name="password" id="password" />
>       <br />
>       <label for="geometry">Geometry</label>
>       <input type="text" name="geometry" id="geometry" value="_GEOMETRY_"/>
>       <br /><br />
>       <input type="submit" name="submit" value="Login"/>
>       </p>
>     </form>
>   </div>
>   <div class="footer"> </div>
> </div>
> </body>
> </html>
421c492
< x11vnc desktop (_UID_/_VNC_PORT_)
---
> Raphael Desktop (_UID_/_VNC_PORT_)
436d506
< <a href=http://www.karlrunge.com/x11vnc>x11vnc website</a>

---

### Post by krunge on 2010-11-22
This looks like a problem:

xauth: error in locking authority file /home/magog/.Xauthority

check the ownership of that file. It is probably owned by the wrong user.   Please tell me who owns that file. I suggest deleting it. However, it may come back again as the wrong owner and that will be a clue.

I'm trying to remember if I fixed this ownership problem in a later x11vnc (I suggest trying the x11vnc 0.9.13 dev version)

Forgive me, but I don't want to go thru desktop.cgi and look for the differences you made. Why not paste a diff(1) or just paste in your changed lines. And please also edit your post and get rid of the full desktop.cgi (to make this thread more readable in case others come here looking to solve a similar problem.)

Thanks for giving that longer x11vnc output.  The xauth error above is a useful hint.  I think what is happening is the Xvfb X server IS started, but the user's X session (xfce) can't connect to it because of the xauth permissions problem.

Let's see what happens with a clean start where you clear out that .Xauthority file.  Please show 'ls -l' output on it after you try again.  Also look at ps(1) output before retrying to make sure all Xvfb processes are gone. 

Oh, BTW, to switch users x11vnc uses the su(1) program. Be sure your system does not have any restriction on the use of that utility.

---

### Post by bcarl17 on 2010-11-23
Checked ownership of .Xauthority  It was owned by root.
I switched ownership to www-data and magog and was unable to connect.
I rm'd .Xauthority and auto logged in as other user, then tried to connect as magog.  When I did I connected but only got a terminal window in the VNC. Tried startx and here is what happened:
magog@raphael:~$ startx

X: user not authorized to run the X server, aborting.
Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit:  Resource temporarily unavailable (errno 11):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

When i logged in as other user and when to /home/magog .Xauthority was created.
Here was the ls-l:

-rw-------  1 magog magog      215 2010-11-23 10:24 .Xauthority

I then on a whim chown .Xauthority back to root:root and deleted it and rebooted.
Tried to VNC as magog and gave me terminal window again. Startx gave same error.
This time .Xauthority came back being owned by magog again.  So default Ubuntu creates .Xauthority as root, but if you delete it comes back owned by user.

As far as su goes I am able to run su as any user. I su to www-data, and was able to su to magog with proper password with no problems. I can su to any regular user with proper password no problem.

I am using version 0.9.10-1 from ubuntu repositories.  I will work on getting the updated version you recommended and let you know if it works.

---

### Post by bcarl17 on 2010-11-23
I updated x11vnc to 0.9.13-1 from source download on your site.
I purged the install from Synaptic and did a checkinstall on my system and pointed the cgi script to the new file location.

When I log in I get a terminal and no X if I'm not the user logged into the real X.

Here is the x11vnc.log from the session:


magog@raphael:~$ cat x11vnc.log
23/11/2010 12:56:59 passing arg to libvncserver: -rfbport
23/11/2010 12:56:59 passing arg to libvncserver: 43050
23/11/2010 12:56:59 x11vnc version: 0.9.13 lastmod: 2010-11-22  pid: 1700
23/11/2010 12:56:59
23/11/2010 12:56:59 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
23/11/2010 12:56:59
23/11/2010 12:56:59 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
23/11/2010 12:56:59
23/11/2010 12:56:59 Initializing SSL (server connect mode).
23/11/2010 12:56:59 RAND_file_name: /home/magog/.rnd
23/11/2010 12:56:59 initialized PRNG with 1088 random bytes.
23/11/2010 12:56:59 created  512 bit temporary RSA key: 0.019s
23/11/2010 12:56:59 created 1024 bit temporary RSA key: 0.034s
23/11/2010 12:56:59 using PEM /opt/vnc/ssl/server.pem  0.000s
23/11/2010 12:56:59
23/11/2010 12:56:59
23/11/2010 12:56:59 Listening for VNC connections on TCP port 43050
23/11/2010 12:56:59 openssl_port: listen on port/sock 43050/3
23/11/2010 12:56:59 openssl_port: listen on port/sock 43050/4 (ipv6)

The SSL VNC desktop is:  raphael:37150
23/11/2010 12:56:59 possible aliases:  raphael:43050, raphael::43050
23/11/2010 12:56:59
23/11/2010 12:57:07 SSL: accept_openssl(OPENSSL_VNC)
23/11/2010 12:57:07 SSL: spawning helper process to handle: 192.168.1.3:53161
23/11/2010 12:57:07 SSL: helper for peerport 53161 is pid 1708:
23/11/2010 12:57:07 connect_tcp: trying:   127.0.0.1 20000
23/11/2010 12:57:07 SSL: ssl_init[1708]: 5/5 initialization timeout: 20 secs.
23/11/2010 12:57:07 SSL: ssl_helper[1708]: SSL_accept() succeeded for: 192.168.1.3:53161
23/11/2010 12:57:07 SSL: ssl_helper[1708]: Cipher: TLSv1/SSLv3 RC4-MD5 Proto: TLSv1
23/11/2010 12:57:07 SSL: ssl_helper[1708]: accepted client 192.168.1.3 x509 peer cert is null
23/11/2010 12:57:07 SSL: handshake with helper process[1708] succeeded.
23/11/2010 12:57:07   other clients:
23/11/2010 12:57:07 incr accepted_client=1 for 127.0.0.1:57886  sock=5
23/11/2010 12:57:07 rfbProcessClientProtocolVersion: not a valid RFB client: GET /check.h
23/11/2010 12:57:07 SSL: ssl_xfer[1708]: closing sockets 0, 5, 5
23/11/2010 12:57:07 SSL: ssl_helper[1708]: exit case 7 (ssl_xfer done)
23/11/2010 12:57:07 client progressed=0 in 15/10 0.023712 s
23/11/2010 12:57:07 client_count: 0
23/11/2010 12:57:07 sending SIGTERM to ssl_helper_pid: 1708
23/11/2010 12:57:07 connect_once: invalid password or early disconnect.  0
23/11/2010 12:57:07 connect_once: waiting for next connection.
23/11/2010 12:57:07 Client 192.168.1.3 gone
23/11/2010 12:57:07 Statistics             events    Transmit/ RawEquiv ( saved)
23/11/2010 12:57:07  TOTALS              :      0 |         0/        0 (  0.0%)
23/11/2010 12:57:07 Statistics             events    Received/ RawEquiv ( saved)
23/11/2010 12:57:07  TOTALS              :      0 |         0/        0 (  0.0%)
23/11/2010 12:57:07 SSL: accept_openssl(OPENSSL_VNC)
23/11/2010 12:57:07 SSL: spawning helper process to handle: 192.168.1.3:53162
23/11/2010 12:57:07 SSL: helper for peerport 53162 is pid 1709:
23/11/2010 12:57:07 connect_tcp: trying:   127.0.0.1 20000
23/11/2010 12:57:07 SSL: ssl_init[1709]: 5/5 initialization timeout: 20 secs.
23/11/2010 12:57:07 SSL: ssl_helper[1709]: SSL_accept() succeeded for: 192.168.1.3:53162
23/11/2010 12:57:07 SSL: ssl_helper[1709]: Cipher: TLSv1/SSLv3 RC4-MD5 Proto: TLSv1
23/11/2010 12:57:07 SSL: ssl_helper[1709]: accepted client 192.168.1.3 x509 peer cert is null
23/11/2010 12:57:07 SSL: handshake with helper process[1709] succeeded.
23/11/2010 12:57:07   other clients:
23/11/2010 12:57:07 incr accepted_client=1 for 127.0.0.1:57887  sock=5
23/11/2010 12:57:07 client progressed=0 in 15/10 0.023813 s
23/11/2010 12:57:08 Client Protocol Version 3.3
23/11/2010 12:57:08 Protocol version sent 3.3, using 3.3
23/11/2010 12:57:08 Using image quality level 6 for client 192.168.1.3
23/11/2010 12:57:08 Enabling X-style cursor updates for client 192.168.1.3
23/11/2010 12:57:08 Enabling full-color cursor updates for client 192.168.1.3
23/11/2010 12:57:08 Enabling cursor position updates for client 192.168.1.3
23/11/2010 12:57:08 Enabling LastRect protocol extension for client 192.168.1.3
23/11/2010 12:57:08 Enabling NewFBSize protocol extension for client 192.168.1.3
23/11/2010 12:57:08 Using tight encoding for client 192.168.1.3
23/11/2010 12:57:08 Pixel format for client 192.168.1.3:
23/11/2010 12:57:08   32 bpp, depth 24, little endian
23/11/2010 12:57:08   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
23/11/2010 12:57:08 no translation needed
23/11/2010 12:57:08 wait_for_client: got client
23/11/2010 12:57:08 client progressed=1 in 0/0 0.000007 s
23/11/2010 12:57:08 client_set_net: 192.168.1.3  0.0032
23/11/2010 12:57:08 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.Q9qnXA
23/11/2010 12:57:08 wait_for_client: find display cmd failed.
23/11/2010 12:57:08 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc-find_display.Q9qnXA Xvfb
trying N=20 ...
redir_daemon=
/usr/bin/xinit /usr/bin/xterm -- /usr/bin/Xvfb :20 -screen 0 1024x768x24 -cc 4 -nolisten tcp -auth /tmp/.xas178119647.TMewXX

[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
23/11/2010 12:57:10 Using X display :20
23/11/2010 12:57:10 rootwin: 0x100 reswin: 0x600001 dpy: 0x1db0120
23/11/2010 12:57:10
23/11/2010 12:57:10 ------------------ USEFUL INFORMATION ------------------
23/11/2010 12:57:10 X DAMAGE available on display, using it for polling hints.
23/11/2010 12:57:10   To disable this behavior use: '-noxdamage'
23/11/2010 12:57:10
23/11/2010 12:57:10   Most compositing window managers like 'compiz' or 'beryl'
23/11/2010 12:57:10   cause X DAMAGE to fail, and so you may not see any screen
23/11/2010 12:57:10   updates via VNC.  Either disable 'compiz' (recommended) or
23/11/2010 12:57:10   supply the x11vnc '-noxdamage' command line option.
23/11/2010 12:57:10
23/11/2010 12:57:10 Wireframing: -wireframe mode is in effect for window moves.
23/11/2010 12:57:10   If this yields undesired behavior (poor response, painting
23/11/2010 12:57:10   errors, etc) it may be disabled:
23/11/2010 12:57:10    - use '-nowf' to disable wireframing completely.
23/11/2010 12:57:10    - use '-nowcr' to disable the Copy Rectangle after the
23/11/2010 12:57:10      moved window is released in the new position.
23/11/2010 12:57:10   Also see the -help entry for tuning parameters.
23/11/2010 12:57:10   You can press 3 Alt_L's (Left "Alt" key) in a row to
23/11/2010 12:57:10   repaint the screen, also see the -fixscreen option for
23/11/2010 12:57:10   periodic repaints.
23/11/2010 12:57:10
23/11/2010 12:57:10 XFIXES available on display, resetting cursor mode
23/11/2010 12:57:10   to: '-cursor most'.
23/11/2010 12:57:10   to disable this behavior use: '-cursor arrow'
23/11/2010 12:57:10   or '-noxfixes'.
23/11/2010 12:57:10 using XFIXES for cursor drawing.
23/11/2010 12:57:10 GrabServer control via XTEST.
23/11/2010 12:57:10
23/11/2010 12:57:10 Scroll Detection: -scrollcopyrect mode is in effect to
23/11/2010 12:57:10   use RECORD extension to try to detect scrolling windows
23/11/2010 12:57:10   (induced by either user keystroke or mouse input).
23/11/2010 12:57:10   If this yields undesired behavior (poor response, painting
23/11/2010 12:57:10   errors, etc) it may be disabled via: '-noscr'
23/11/2010 12:57:10   Also see the -help entry for tuning parameters.
23/11/2010 12:57:10   You can press 3 Alt_L's (Left "Alt" key) in a row to
23/11/2010 12:57:10   repaint the screen, also see the -fixscreen option for
23/11/2010 12:57:10   periodic repaints.
23/11/2010 12:57:10
23/11/2010 12:57:10 XKEYBOARD: number of keysyms per keycode 6 is greater
23/11/2010 12:57:10   than 4 and 2 keysyms are mapped above 4.
23/11/2010 12:57:10   Automatically switching to -xkb mode.
23/11/2010 12:57:10   If this makes the key mapping worse you can
23/11/2010 12:57:10   disable it with the "-noxkb" option.
23/11/2010 12:57:10   Also, remember "-remap DEAD" for accenting characters.
23/11/2010 12:57:10
23/11/2010 12:57:10 X FBPM extension not supported.
Xlib:  extension "DPMS" missing on display ":20.0".
23/11/2010 12:57:10 X display is not capable of DPMS.
23/11/2010 12:57:10 --------------------------------------------------------
23/11/2010 12:57:10
23/11/2010 12:57:10 Default visual ID: 0x21
23/11/2010 12:57:10 Read initial data from X display into framebuffer.
23/11/2010 12:57:10 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
23/11/2010 12:57:10 rfbNewFramebuffer(0x1d9ed10, 0x0, 1024, 768, 8, 1, 4)
23/11/2010 12:57:10 Pixel format for client 192.168.1.3:
23/11/2010 12:57:10   32 bpp, depth 24, little endian
23/11/2010 12:57:10   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
23/11/2010 12:57:10
23/11/2010 12:57:10 X display :20.0 is 32bpp depth=24 true color
23/11/2010 12:57:10
23/11/2010 12:57:10 calling setTranslateFunction()...
23/11/2010 12:57:10 Pixel format for client 192.168.1.3:
23/11/2010 12:57:10   32 bpp, depth 24, little endian
23/11/2010 12:57:10   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
23/11/2010 12:57:10 no translation needed
23/11/2010 12:57:10   done.
23/11/2010 12:57:10 TS_REDIR is empty, restarting...
23/11/2010 12:57:10
23/11/2010 12:57:10 Xinerama is present and active (e.g. multi-head).
23/11/2010 12:57:10 Xinerama: number of sub-screens: 1
23/11/2010 12:57:10 Xinerama: no blackouts needed (only one sub-screen)
23/11/2010 12:57:10
23/11/2010 12:57:10 fb read rate: 627 MB/sec
23/11/2010 12:57:10 fast read: reset wait  ms to: 10
23/11/2010 12:57:10 fast read: reset defer ms to: 10
23/11/2010 12:57:10 The X server says there are 10 mouse buttons.
23/11/2010 12:57:10 screen setup finished.
23/11/2010 12:57:10

The SSL VNC desktop is:  raphael:37150
23/11/2010 12:57:10 possible aliases:  raphael:43050, raphael::43050

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)

23/11/2010 12:57:10 Battling with something for -norepeat!! (1 resets left)
23/11/2010 12:57:10 Disabled X server key autorepeat.
23/11/2010 12:57:10   to force back on run: 'xset r on' (2 times)
23/11/2010 12:57:10 created   xdamage object: 0x600024
23/11/2010 12:57:10 Sending rfbEncodingNewFBSize for resize to (1024x768)
23/11/2010 12:57:12 copy_tiles: allocating first_line at size 33



Here is the ps-aux while connected to the terminal in VNC:


magog     1595  0.0  0.0  89508  1716 ?        S    12:54   0:00 sshd: magog@pts/0
magog     1596  0.2  0.3  25604  7040 pts/0    Ss   12:54   0:00 -bash
magog     1700  3.0  0.5  72116 10884 ?        S    12:56   0:03 /usr/local/bin/x11vnc -sigpipe ignore:HUP -nopw -rfbport 43050 -passwdfile /home/magog/x11vnc.pw -oa /home/magog/x11vnc.log -create -ssl SAVE -sslonly -env FD_GEOM=1024x768x24 -timeout 75 -ssl /opt/vnc/ssl/server.pem
magog     1709  0.1  0.0  53820  2024 ?        S    12:57   0:00 /usr/local/bin/x11vnc -sigpipe ignore:HUP -nopw -rfbport 43050 -passwdfile /home/magog/x11vnc.pw -oa /home/magog/x11vnc.log -create -ssl SAVE -sslonly -env FD_GEOM=1024x768x24 -timeout 75 -ssl /opt/vnc/ssl/server.pem
magog     1777  0.0  0.0      0     0 ?        Z    12:57   0:00 [sh] <defunct>
magog     2054  0.0  0.0   4148   572 ?        S    12:57   0:00 sh -c /usr/bin/xinit /usr/bin/xterm -- /usr/bin/Xvfb :20 -screen 0 1024x768x24 -cc 4 -nolisten tcp -auth /tmp/.xas178119647.TMewXX
magog     2057  0.0  0.0   4148   564 ?        S    12:57   0:00 sh -c (sleep 150; rm -f /nosuch /tmp/.xas178119647.TMewXX)
magog     2059  0.0  0.0  15704   844 ?        S    12:57   0:00 /usr/bin/xinit /usr/bin/xterm -- /usr/bin/Xvfb :20 -screen 0 1024x768x24 -cc 4 -nolisten tcp -auth /tmp/.xas178119647.TMewXX
magog     2060  0.0  0.0   4148   312 ?        S    12:57   0:00 sh -c (sleep 150; rm -f /nosuch /tmp/.xas178119647.TMewXX)
magog     2062  0.0  0.0   4060   308 ?        S    12:57   0:00 sleep 150
magog     2063  1.9  0.7  69000 15272 ?        S    12:57   0:01 /usr/bin/Xvfb :20 -screen 0 1024x768x24 -cc 4 -nolisten tcp -auth /tmp/.xas178119647.TMewXX
magog     2066  0.0  0.3  62288  6668 ?        S    12:57   0:00 /usr/bin/xterm
magog     2068  0.1  0.1  22640  3988 pts/1    Ss+  12:57   0:00 bash
magog     2100  0.0  0.0  17760  1192 pts/0    R+   12:58   0:00 ps -aux
magog     2101  0.0  0.2  25604  5652 pts/0    D+   12:58   0:00 -bash


When i try to start Xvfb from inside the VNC terminal here is what I get:


magog@raphael:~$ Xvfb

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

magog@raphael:~$ 



Anything else you need to help me debug this let me know.

I can give you an ssh shell on the box if you want to check it out.

---

### Post by krunge on 2010-11-24
I will try to help you later.

I need to test desktop.cgi on my test debian sid system in my basement. It works fine on my debian systems here with apache, but they are a bit too old...

BTW you don't want to type 'Xvfb' in the xterm, you are already in Xvfb!! (that is where the xterm is displaying)  You probably want to type something like 'startxfce' or 'startkde' or 'gnome-session'.  You have installed the one you want, right?

Your ps(1) output looks promising and suggests everything is working except the desktop session.  If you type 'xdpyinfo' in that xterm does it work without errors??

---

### Post by krunge on 2010-11-24
> **krunge said:**
> 
BTW you don't want to type 'Xvfb' in the xterm, you are already in Xvfb!! (that is where the xterm is displaying)  You probably want to type something like 'startxfce' or 'startkde' or 'gnome-session'.

Looking more at a previous post of yours where you typed 'startx' in the terminal. You don't want that either. You already have an X server running (Xvfb, where the xterm terminal is showing.)  You want to start a desktop session from that terminal. 'startxfce' or etc. as I say above.

---

### Post by bcarl17 on 2010-11-24
Got It!

I was using FD_SESS='xfce'

Forgot the 4 on xfce4.

Only issue I got now is it seems kinda unstable, and disconnects every few minutes, perhaps because xfce4 is running on the real X server.  I am going to try installing another lite Windows manager and use that as my Xvfb and see if it makes a diff.  Here is the x11vnc.log for when VNC disconnects:

magog@raphael:~$ cat /home/magog/x11vnc.log
24/11/2010 17:06:44 passing arg to libvncserver: -rfbport
24/11/2010 17:06:44 passing arg to libvncserver: 43115
24/11/2010 17:06:44 x11vnc version: 0.9.13 lastmod: 2010-11-22  pid: 1703
24/11/2010 17:06:44
24/11/2010 17:06:44 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
24/11/2010 17:06:44
24/11/2010 17:06:44 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
24/11/2010 17:06:44
24/11/2010 17:06:44 Initializing SSL (server connect mode).
24/11/2010 17:06:44 RAND_file_name: /home/magog/.rnd
24/11/2010 17:06:44 initialized PRNG with 1088 random bytes.
24/11/2010 17:06:44 created  512 bit temporary RSA key: 0.006s
24/11/2010 17:06:44 created 1024 bit temporary RSA key: 0.044s
24/11/2010 17:06:44 using PEM /opt/vnc/ssl/server.pem  0.000s
24/11/2010 17:06:44
24/11/2010 17:06:44
24/11/2010 17:06:44 Listening for VNC connections on TCP port 43115
24/11/2010 17:06:44 openssl_port: listen on port/sock 43115/3
24/11/2010 17:06:44 openssl_port: listen on port/sock 43115/4 (ipv6)

The SSL VNC desktop is:  raphael:37215
24/11/2010 17:06:44 possible aliases:  raphael:43115, raphael::43115
24/11/2010 17:06:44
24/11/2010 17:06:48 SSL: accept_openssl(OPENSSL_VNC)
24/11/2010 17:06:48 SSL: spawning helper process to handle: 192.168.1.3:51155
24/11/2010 17:06:48 SSL: helper for peerport 51155 is pid 1711:
24/11/2010 17:06:48 connect_tcp: trying:   127.0.0.1 20000
24/11/2010 17:06:48 SSL: ssl_init[1711]: 5/5 initialization timeout: 20 secs.
24/11/2010 17:06:48 SSL: ssl_helper[1711]: SSL_accept() succeeded for: 192.168.1.3:51155
24/11/2010 17:06:48 SSL: ssl_helper[1711]: Cipher: TLSv1/SSLv3 RC4-MD5 Proto: TLSv1
24/11/2010 17:06:48 SSL: ssl_helper[1711]: accepted client 192.168.1.3 x509 peer cert is null
24/11/2010 17:06:48 SSL: handshake with helper process[1711] succeeded.
24/11/2010 17:06:48   other clients:
24/11/2010 17:06:48 incr accepted_client=1 for 127.0.0.1:33977  sock=5
24/11/2010 17:06:48 rfbProcessClientProtocolVersion: not a valid RFB client: GET /check.h
24/11/2010 17:06:48 SSL: ssl_xfer[1711]: closing sockets 0, 5, 5
24/11/2010 17:06:48 SSL: ssl_helper[1711]: exit case 7 (ssl_xfer done)
24/11/2010 17:06:48 client progressed=0 in 15/10 0.027158 s
24/11/2010 17:06:48 client_count: 0
24/11/2010 17:06:48 sending SIGTERM to ssl_helper_pid: 1711
24/11/2010 17:06:48 connect_once: invalid password or early disconnect.  0
24/11/2010 17:06:48 connect_once: waiting for next connection.
24/11/2010 17:06:48 Client 192.168.1.3 gone
24/11/2010 17:06:48 Statistics             events    Transmit/ RawEquiv ( saved)
24/11/2010 17:06:48  TOTALS              :      0 |         0/        0 (  0.0%)
24/11/2010 17:06:48 Statistics             events    Received/ RawEquiv ( saved)
24/11/2010 17:06:48  TOTALS              :      0 |         0/        0 (  0.0%)
24/11/2010 17:06:48 SSL: accept_openssl(OPENSSL_VNC)
24/11/2010 17:06:48 SSL: spawning helper process to handle: 192.168.1.3:51156
24/11/2010 17:06:48 SSL: helper for peerport 51156 is pid 1712:
24/11/2010 17:06:48 connect_tcp: trying:   127.0.0.1 20000
24/11/2010 17:06:48 SSL: ssl_init[1712]: 5/5 initialization timeout: 20 secs.
24/11/2010 17:06:48 SSL: ssl_helper[1712]: SSL_accept() succeeded for: 192.168.1.3:51156
24/11/2010 17:06:48 SSL: ssl_helper[1712]: Cipher: TLSv1/SSLv3 RC4-MD5 Proto: TLSv1
24/11/2010 17:06:48 SSL: ssl_helper[1712]: accepted client 192.168.1.3 x509 peer cert is null
24/11/2010 17:06:48 SSL: handshake with helper process[1712] succeeded.
24/11/2010 17:06:48   other clients:
24/11/2010 17:06:48 incr accepted_client=1 for 127.0.0.1:33978  sock=5
24/11/2010 17:06:48 client progressed=0 in 15/10 0.023515 s
24/11/2010 17:06:49 Client Protocol Version 3.3
24/11/2010 17:06:49 Protocol version sent 3.3, using 3.3
24/11/2010 17:06:49 Using image quality level 6 for client 192.168.1.3
24/11/2010 17:06:49 Enabling X-style cursor updates for client 192.168.1.3
24/11/2010 17:06:49 Enabling full-color cursor updates for client 192.168.1.3
24/11/2010 17:06:49 Enabling cursor position updates for client 192.168.1.3
24/11/2010 17:06:49 Enabling LastRect protocol extension for client 192.168.1.3
24/11/2010 17:06:49 Enabling NewFBSize protocol extension for client 192.168.1.3
24/11/2010 17:06:49 Using tight encoding for client 192.168.1.3
24/11/2010 17:06:49 Pixel format for client 192.168.1.3:
24/11/2010 17:06:49   32 bpp, depth 24, little endian
24/11/2010 17:06:49   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
24/11/2010 17:06:49 no translation needed
24/11/2010 17:06:49 wait_for_client: got client
24/11/2010 17:06:49 client progressed=1 in 0/0 0.000039 s
24/11/2010 17:06:49 client_set_net: 192.168.1.3  0.0057
24/11/2010 17:06:49 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.yRPplR
24/11/2010 17:06:49 wait_for_client: find display cmd failed.
24/11/2010 17:06:49 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc-find_display.yRPplR Xvfb
trying N=20 ...
redir_daemon=
/usr/bin/xinit /usr/bin/startxfce4 -- /usr/bin/Xvfb :20 -screen 0 1024x768x24 -cc 4 -nolisten tcp -auth /tmp/.xas178428370.GppSmG

[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
/usr/bin/startxfce4: X server already running on display :20
<stdin>:1: error: invalid preprocessing directive #Those
<stdin>:2: error: invalid preprocessing directive #or
<stdin>:3: error: invalid preprocessing directive #Xft
<stdin>:4: error: invalid preprocessing directive #Xft
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
xrdb:  "Xft.antialias" on line 47 overrides entry on line 11
xrdb:  "Xft.hinting" on line 48 overrides entry on line 13
xrdb:  "Xft.rgba" on line 49 overrides entry on line 12
xrdb:  "Xft.hintstyle" on line 50 overrides entry on line 14
Agent pid 2078
xfdesktop[2101]: starting up

(polkit-gnome-authentication-agent-1:2109): polkit-gnome-1-WARNING **: Unable to determine the session we are in: Remote Exception invoking org.freedesktop.ConsoleKit.Manager.GetSessionForUnixProcess() on /org/freedesktop/ConsoleKit/Manager at name org.freedesktop.ConsoleKit: org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to find session for cookie org.freedesktop.ConsoleKit.Manager.GeneralError Unable%20to%20find%20session%20for%20cookie
GNOME_KEYRING_CONTROL=/tmp/keyring-O37BHR
SSH_AUTH_SOCK=/tmp/keyring-O37BHR/ssh
GNOME_KEYRING_PID=2121
GNOME_KEYRING_CONTROL=/tmp/keyring-O37BHR
SSH_AUTH_SOCK=/tmp/keyring-O37BHR/ssh

** (nm-applet:2111): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service.
  Error: (9) Connection ":1.40" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file

GNOME_KEYRING_CONTROL=/tmp/keyring-O37BHR
SSH_AUTH_SOCK=/tmp/keyring-O37BHR/ssh
24/11/2010 17:06:50 Using X display :20
24/11/2010 17:06:50 rootwin: 0x100 reswin: 0x2200001 dpy: 0x1387730
24/11/2010 17:06:50
24/11/2010 17:06:50 ------------------ USEFUL INFORMATION ------------------
24/11/2010 17:06:50 X DAMAGE available on display, using it for polling hints.
24/11/2010 17:06:50   To disable this behavior use: '-noxdamage'
24/11/2010 17:06:50
24/11/2010 17:06:50   Most compositing window managers like 'compiz' or 'beryl'
24/11/2010 17:06:50   cause X DAMAGE to fail, and so you may not see any screen
24/11/2010 17:06:50   updates via VNC.  Either disable 'compiz' (recommended) or
24/11/2010 17:06:50   supply the x11vnc '-noxdamage' command line option.
24/11/2010 17:06:50
24/11/2010 17:06:50 Wireframing: -wireframe mode is in effect for window moves.
24/11/2010 17:06:50   If this yields undesired behavior (poor response, painting
24/11/2010 17:06:50   errors, etc) it may be disabled:
24/11/2010 17:06:50    - use '-nowf' to disable wireframing completely.
24/11/2010 17:06:50    - use '-nowcr' to disable the Copy Rectangle after the
24/11/2010 17:06:50      moved window is released in the new position.
24/11/2010 17:06:50   Also see the -help entry for tuning parameters.
24/11/2010 17:06:50   You can press 3 Alt_L's (Left "Alt" key) in a row to
24/11/2010 17:06:50   repaint the screen, also see the -fixscreen option for
24/11/2010 17:06:50   periodic repaints.
24/11/2010 17:06:50
24/11/2010 17:06:50 XFIXES available on display, resetting cursor mode
24/11/2010 17:06:50   to: '-cursor most'.
24/11/2010 17:06:50   to disable this behavior use: '-cursor arrow'
24/11/2010 17:06:50   or '-noxfixes'.
24/11/2010 17:06:50 using XFIXES for cursor drawing.
24/11/2010 17:06:50 GrabServer control via XTEST.
24/11/2010 17:06:50
24/11/2010 17:06:50 Scroll Detection: -scrollcopyrect mode is in effect to
24/11/2010 17:06:50   use RECORD extension to try to detect scrolling windows
24/11/2010 17:06:50   (induced by either user keystroke or mouse input).
24/11/2010 17:06:50   If this yields undesired behavior (poor response, painting
24/11/2010 17:06:50   errors, etc) it may be disabled via: '-noscr'
24/11/2010 17:06:50   Also see the -help entry for tuning parameters.
24/11/2010 17:06:50   You can press 3 Alt_L's (Left "Alt" key) in a row to
24/11/2010 17:06:50   repaint the screen, also see the -fixscreen option for
24/11/2010 17:06:50   periodic repaints.
24/11/2010 17:06:50
24/11/2010 17:06:50 XKEYBOARD: number of keysyms per keycode 6 is greater
24/11/2010 17:06:50   than 4 and 2 keysyms are mapped above 4.
24/11/2010 17:06:50   Automatically switching to -xkb mode.
24/11/2010 17:06:50   If this makes the key mapping worse you can
24/11/2010 17:06:50   disable it with the "-noxkb" option.
24/11/2010 17:06:50   Also, remember "-remap DEAD" for accenting characters.
24/11/2010 17:06:50
24/11/2010 17:06:50 X FBPM extension not supported.
Xlib:  extension "DPMS" missing on display ":20.0".
24/11/2010 17:06:50 X display is not capable of DPMS.
24/11/2010 17:06:50 --------------------------------------------------------
24/11/2010 17:06:50
24/11/2010 17:06:50 Default visual ID: 0x21
24/11/2010 17:06:51 Read initial data from X display into framebuffer.
24/11/2010 17:06:51 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
24/11/2010 17:06:51 rfbNewFramebuffer(0x1375d60, 0x0, 1024, 768, 8, 1, 4)
24/11/2010 17:06:51 Pixel format for client 192.168.1.3:
24/11/2010 17:06:51   32 bpp, depth 24, little endian
24/11/2010 17:06:51   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
24/11/2010 17:06:51
24/11/2010 17:06:51 X display :20.0 is 32bpp depth=24 true color
24/11/2010 17:06:51
24/11/2010 17:06:51 calling setTranslateFunction()...
24/11/2010 17:06:51 Pixel format for client 192.168.1.3:
24/11/2010 17:06:51   32 bpp, depth 24, little endian
24/11/2010 17:06:51   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
24/11/2010 17:06:51 no translation needed
24/11/2010 17:06:51   done.
24/11/2010 17:06:51 TS_REDIR is empty, restarting...
24/11/2010 17:06:51
24/11/2010 17:06:51 Xinerama is present and active (e.g. multi-head).
24/11/2010 17:06:51 Xinerama: number of sub-screens: 1
24/11/2010 17:06:51 Xinerama: no blackouts needed (only one sub-screen)
24/11/2010 17:06:51
24/11/2010 17:06:51 fb read rate: 264 MB/sec
24/11/2010 17:06:51 fast read: reset wait  ms to: 10
24/11/2010 17:06:51 fast read: reset defer ms to: 10
24/11/2010 17:06:51 The X server says there are 10 mouse buttons.
24/11/2010 17:06:51 screen setup finished.
24/11/2010 17:06:51

The SSL VNC desktop is:  raphael:37215
24/11/2010 17:06:51 possible aliases:  raphael:43115, raphael::43115

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)

system-config-printer-applet: failed to start NewPrinterNotification service
24/11/2010 17:06:51 Battling with something for -norepeat!! (1 resets left)
24/11/2010 17:06:51 Disabled X server key autorepeat.
24/11/2010 17:06:51   to force back on run: 'xset r on' (2 times)
24/11/2010 17:06:51 created   xdamage object: 0x2200024
24/11/2010 17:06:51 Sending rfbEncodingNewFBSize for resize to (1024x768)
24/11/2010 17:06:51 copy_tiles: allocating first_line at size 33

(xfce4-cpugraph-plugin:2202): Gtk-CRITICAL **: IA__gtk_container_set_border_width: assertion `GTK_IS_CONTAINER (container)' failed
24/11/2010 17:06:52 client 2 network rate 12.1 KB/sec (2176.7 eff KB/sec)
24/11/2010 17:06:52 client 2 latency:  43.8 ms
24/11/2010 17:06:52 dt1: 3.4223, dt2: 0.0771 dt3: 0.0438 bytes: 42243
24/11/2010 17:06:52 link_rate: LR_DIALUP - 43 ms, 12 KB/s
** (update-notifier:2125): DEBUG: aptdaemon on bus: 0
24/11/2010 17:06:59 created selwin: 0x2200025
24/11/2010 17:06:59 called initialize_xfixes()
24/11/2010 17:07:58 SSL: ssl_xfer[1712]: tv_cutover: 70
xfce4-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.

(xfdesktop:2101): libxfcegui4-WARNING **: ICE I/O Error

(xfdesktop:2101): libxfcegui4-WARNING **: Disconnected from session manager.
xfwm4: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.
xfce4-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.
xfdesktop: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.
Thunar: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.

(xfce4-settings-helper:2157): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-settings-helper:2157): libxfcegui4-WARNING **: Disconnected from session manager.
xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.
Agent pid 2078 killed
/usr/bin/xinit:  connection to X server lost.

waiting for X server to shut down caught XIO error:
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :20.0.
24/11/2010 17:08:41 deleted 32 tile_row polling images.
24/11/2010 17:08:41 SSL: ssl_xfer[1712]: closing sockets 0, 5, 5
24/11/2010 17:08:41 SSL: ssl_helper[1712]: exit case 7 (ssl_xfer done)

---

### Post by krunge on 2010-11-24
> Got It! I was using FD_SESS='xfce' Forgot the 4 on xfce4.

Good! It looked like you were doing something wrong like that but I couldn't check.
> 
Only issue I got now is it seems kinda unstable, and disconnects every few minutes, perhaps because xfce4 is running on the real X server.  I am going to try installing another lite Windows manager and use that as my Xvfb and see if it makes a diff.

Please use twm.  That will be the acid test that x11vnc is doing everything it should be.

---

