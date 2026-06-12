---
title: "Firefox 2 on Dapper font and Flash audio problem"
date: 2007-06-17
forum: Desktop Effects &amp; Customization
---

### Post by cpudney on 2007-06-17
G'day,

So, I decided to upgrade from [Firefox v1.5 to v2.0 using ubuntuzilla]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2007/06/upgrading-to-firefox2-using-ubuntuzilla.html").

Everything went smoothly except for two **minor** issues:
[LIST=1]
[*]the fonts in web-pages rendered in Firefox 2.0 don't appear to be as smooth as they were iin Firefox 1.5
[*]audio in the Flash plug-in doesn't work if another audio application, e.g. Rhythmbox, is open.  I need to close all audio applications and then restart Firefox to get audio from the Flash plug-in, e.g. youtube.com video player.  This certainly wasn't the case with Firefox 1.5.
[/LIST]
Has anyone else noticed these problems?  Any suggested fixes.

Thanks,
Chris.

---

### Post by cpudney on 2007-06-24
G'day,

I managed to [solve the audio problem I was having with the Flash plugin in Firefox 2]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2007/06/flash-audio-problems-in-firefox-2.html") :)

The fix was fairly simple. I had libflashplayer.so in my .mozilla/plugins directory. This was being used by Firefox 2 for the application/x-shockwave-flash MIME type in preference to Shockwave Flash v9.0 (flashplugin-nonfree package) :redface:

After removing libflashplayer.so and flashplayer.xpt from my .mozilla/plugins directory audio playback works perfectly in the Flash plugin in Firefox 2.

Chris.

---

### Post by nanotube on 2007-06-26
> **cpudney said:**
> G'day,

I managed to [solve the audio problem I was having with the Flash plugin in Firefox 2]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2007/06/flash-audio-problems-in-firefox-2.html") :)

The fix was fairly simple. I had libflashplayer.so in my .mozilla/plugins directory. This was being used by Firefox 2 for the application/x-shockwave-flash MIME type in preference to Shockwave Flash v9.0 (flashplugin-nonfree package) :redface:

After removing libflashplayer.so and flashplayer.xpt from my .mozilla/plugins directory audio playback works perfectly in the Flash plugin in Firefox 2.

Chris.

thanks for the post. i'll add this to the ubuntuzilla faq/knowledgebase. :)

---

