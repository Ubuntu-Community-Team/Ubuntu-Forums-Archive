---
title: "Firefox -- slow right-click menu"
date: 2006-09-26
forum: Desktop Environments
---

### Post by secdroid on 2006-09-26
Running Dapper X86 with Firefox 1.5.0.7, using extensions: English Language Pack, VideoDownloader, Adblock, Flashblock,  MediaPlayerConnectivity, netcrafttoolbar.

When I right-click the mouse, while pointer positioned over link, menu takes five to eight seconds to pop up.  

Using Opera on same hardware & same sites produces instant right-click menu.

Am I having an extension-related problem with Firefox?  Any other suggestions?

---

### Post by orb9220 on 2006-09-26
Could be extension. Or Java In address bar type: about:plugins and post java versions.

---

### Post by secdroid on 2006-09-27
Java(TM) Plug-in 1.5.0_06-b05
All MIME types enabled.

Also have:
Totem Mozilla Plugin 1.4.**1**
Totem Mozilla Plugin 1.4.**3**
Shockwave Flash 7.0 r68
Helix DNA Plugin

Should I try to remove duplicate Totem Mozilla plugins?  Conflict?

Disabling netcrat toolbar did help speed things up, but it doesn't seem to be the whole solution.

---

### Post by orb9220 on 2006-09-27
No I was thinking it may have been a java issue.

Is there anything new in the right-click menu that is not normally there in default right-click menu?

---

### Post by secdroid on 2006-09-27
> Is there anything new in the right-click menu that is not normally there in default right-click menu?

No.  I just compared the right-click menu to Dapper/Firefox running off LiveCD on another (slower) box.  Menus are identical.  LiveCD Firefox produces instantaneous right-click menu.

I don't know how to reason this out.  I guess I could just start uninstalling extensions & plug-ins, on-by-one and restarting Firefox after each go to see if I can get back to original performance.  If that fails, I could uninstall & reinstall Firefox.  Tedious...

---

### Post by secdroid on 2006-09-27
I asked > Am I having an extension-related problem with Firefox?

Answered my own question & learned a bit about troubleshooting Firefox.

Rather than uninstalling my extensions, I disabled them and restarted Firefox.  (Restart is required for enable/disable to take effect.)

With no extensions enabled, right-click menu was instantaneous.  I enabled extenions and restarted until I was able to reproduce the problem.  Disable one extension and restart proved the point.

Problem extension: MediaPlayerConnectivity 0.7.3 
[https://addons.mozilla.org/firefox/446/]("https://addons.mozilla.org/firefox/446/")
[http://membres.lycos.fr/sethnakht/]("http://membres.lycos.fr/sethnakht/")

Will report issue to extension author.

---

### Post by l.capriotti on 2006-09-27
Gosh! It has been some time I had the same issue, and I finally found the cure here - I was too lazy to test which extension was causing that.

Many tks!

Cheers
Luigi

---

