---
title: "Which desktop environment would provide me with a simple grid of applications?"
date: 2014-07-04
forum: Desktop Environments
---

### Post by Roasted on 2014-07-04
This is going to sound a little strange, but basically I have a spare computer here plugged into a monitor. As it stands now, I turn it on and it auto logs in + auto launches Firefox to a custom HTML page. This HTML page pulls in the MJPG feeds from my CCTV network cameras. I'm changing things around a bit. My recordings pull in H264 feed, so the MJPG is basically a viewer. I'd like to get some better FPS on the "surveillance viewer" box, so I'm looking to eliminate the HTML page that serves MJPG and switch to a direct H264 solution. Thing is, as far as I know, you cannot embed a live H264 stream into an HTML file. If it's possible, I'd love to know how.

Until then, I'm trying to figure out how I can set up a grid of auto launch applications. In particular, VLC. I want to launch 4 instances of VLC in a 2x2 grid format where each VLC instance points to its own RTSP instance. I'm hoping that a desktop environment that 'saves' the session would be a fit.

I looked at i3 in a VM. It's an interesting environment, but the lack of session save (and the setup involved) seems tedious (unless that's the 2:30 AM side of me talking).

I don't care what runs on this box. I just want it to log in and auto launch 4 RTSP feeds in 4 different instances of VLC so I would have a 'live viewer' when I'm in my office.

Anybody have any ideas?

---

### Post by TheFu on 2014-07-04
In the old days, we would write a program startup script that placed windows in the Window Manager. So ... how to do that depends on the WM used.  fvwm can do it, but I'd bet that current-gen WMs support this too - like openbox. [https://bbs.archlinux.org/viewtopic.php?id=45618](https://bbs.archlinux.org/viewtopic.php?id=45618) explains.

BTW, I think HTML5 supports h.264 streams with a nearly trivial media tag. I've only used the audio version.
```
<audio controls autobuffer autoplay>
  <source src="uc/fun-music.mp3" />
  Your browser does not support the audio element.
</audio> 
```
Anyway, hope that helps.

---

### Post by Roasted on 2014-07-04
"No video with supported format and MIME type found" when using:

```
<html>
<video width="1280" height="800" controls>
  <source src="http://192.168.1.16:554/live3.sdp" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  <source src="movie.webm" type="video/webm">
  <object data="movie.mp4" width="1280" height="800">
    <embed src="movie.swf" width="1280" height="800">
  </object>
</video> 
</html>
```

Found the above on a different post somewhere that I altered for my settings. I get that no matter what tag I've used that I've found (10+).

---

### Post by TheFu on 2014-07-04
Doesn't it need to be a formal html5 document?

mp4 is a container.  Could it be that the vcodec needs to be specified in the mime?  
Also - why are the other source entries there? Are they valid?

Just some questions - I don't know any answers.  [https://www.rfc-editor.org/rfc/rfc3984.txt](https://www.rfc-editor.org/rfc/rfc3984.txt) might be helpful. There is an h264 type.

---

### Post by Roasted on 2014-07-04
> **TheFu said:**
> Doesn't it need to be a formal html5 document?

mp4 is a container.  Could it be that the vcodec needs to be specified in the mime?  
Also - why are the other source entries there? Are they valid?

Just some questions - I don't know any answers.  [https://www.rfc-editor.org/rfc/rfc3984.txt](https://www.rfc-editor.org/rfc/rfc3984.txt) might be helpful. There is an h264 type.

I have no idea if they are valid. They were in the example so I figured I'd leave them to see. I don't know enough (or anything, really) about any sort of HTML tags to use with H264, so I'm kind of blind firing and testing what I read other users talk about on other forums. I'm just pasting the code into a blank test.html document and seeing what happens in Firefox and Chrome. That's it in a nutshell. :)

---

