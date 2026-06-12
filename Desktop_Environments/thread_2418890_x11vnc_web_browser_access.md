---
title: "x11vnc web browser access"
date: 2019-05-13
forum: Desktop Environments
---

### Post by mortz3 on 2019-05-13
I have a Linux embedded device and I'm trying to share the screen to access it remotely through a web browser. I've searched through multiple posts that explain how to do this but I've had no success. At least I was able to access the shared screen using vnc viewer on my Windows machine.


I start the server with this command: x11vnc -display :0 -rfbauth ~/.vnc/passwd -http 
This sets up the screen share, the Java viewer URL is printed ([http://imx6ul-var-dart:5800](http://imx6ul-var-dart:5800)) on PORT=5900. So far so good.


When I open my web browser (chrome) and I type in <remoteIP>:5800 in the URL bar, I get a blank page with a hyperlink "x11vnc site" that opens a new tab to where you would expect ([http://www.karlrunge.com/x11vnc/)](http://www.karlrunge.com/x11vnc/)). Meanwhile, the terminal outputs:
httpd: get ' ' for <remoteIP>
httpd: defaulting to 'index.vnc'
httpd: premature connection close (Once the connection times out ~15seconds)


I tried to use a combination of different command options but nothing that works. 
Any help or pointers would be greatly appreciated!

---

### Post by mortz3 on 2019-05-20
After a lot of research and trial & error, I managed to found a solution. Here's what I did if it is useful to anyone else.

A proxy is required to achieve VNC through a web browser. noVNC ([https://novnc.com/info.html](https://novnc.com/info.html)) runs in any modern browser including with iOS and Android mobile devices by using WebSockets. You only have to clone the noVNC git repo to any directory you want and install the dependencies which come with it. 

After starting the x11vnc server, noVNC is launched with this command ```
./utils/launch.sh --vnc localhost:5900
``` Where localhost can is the remote IP you want to access and 5900 is the port on which x11vnc is running. 

Once x11vnc and noVNC are running, noVNC should output URL that you can access in a web browser to access your shared screen! Note that the client must be on the same network for it to work and the URL should be ```
remoteIP:PORT/vnc_lite.html
``` noVNC also has some options that let you edit this URL.

---

