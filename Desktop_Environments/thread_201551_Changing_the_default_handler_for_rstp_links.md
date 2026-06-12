---
title: "Changing the default handler for rstp: links"
date: 2006-06-22
forum: Desktop Environments
---

### Post by mssever on 2006-06-22
I'm trying to view a video on c-span.org that is published in RealMedia format, using the rstp protocol. Totem is unable to play the file, and the folks at c-span, in all their wisdom :roll: decided to make all the links call Javascript functions. I don't really feel like sifting through source code to find the URL of every video I want to watch. How can I set up Firefox (or is this a Gnome issue?) to launch RealPlayer instead of Totem to play these files?  I can't find a setting anywhere. ](*,)

---

### Post by mssever on 2006-06-22
Any ideas?

---

### Post by bionnaki on 2006-06-22
install realplay

sudo apt-get install realplay

---

### Post by mssever on 2006-06-22
I already did that, but the installer didn't set my system up correctly.

---

### Post by mssever on 2006-06-22
Clarification:

When I tried to install realplayer from Synaptic, I got the following error:"realplayer: Depends: xlibs  but it is not installable." So I downloaded and installed RealPlayer directly from real.com. But it didn't setup the rstp: links.

<rant>While I appreciate the push for user friendly programs--such as in Gnome and Firefox, all that user-friendliness is useless if it means hiding essential options, such as changing handlers</rant>

---

### Post by mssever on 2006-06-22
OK... I asked on the [Helix Community forum]("https://helixcommunity.org/forum/forum.php?thread_id=2661&forum_id=7") and got the following answer:
>                      1. Open up Firefox and type "about:config" sans the quotes in the address bar of your browser.

2. Right click in the window below the filter bar, and select New and then select String

3. Enter "network.protocol-handler.app.rtsp" sans the quotes and click ok. In the next text box, type the full path to your RealPlayer application and click ok.

4. Restart firefox and rtsp streams accessed from within firefox should now bring up RealPlayer. 
Hope this helps someone.

---

### Post by mssever on 2006-09-03
I recently discovered a better way of doing this:
[LIST=1]
[*]Open up gconf-editor
[*]Drill down to /desktop/gnome/url-handlers/rstp (create it if necessary)
[*]Set the command key to [FONT=Courier New]realplay "%s"[/FONT]
[*]If you created the rstp entry, add the following keys, as well: enabled (boolean, checked); needs_terminal (boolean, unchecked)[/LIST]

---

### Post by JohnnyVW on 2007-02-10
> **mssever said:**
> OK... I asked on the [Helix Community forum]("https://helixcommunity.org/forum/forum.php?thread_id=2661&forum_id=7") and got the following answer:
 
Hope this helps someone.

Hey mssever!

Thanks for the tip!  I was trying to watch C-Span this morning myself and discovered that it didn't work anymore.  It wanted to start Totem.  Totem doesn't work.  I uninstalled Totem and got the error you talked about.  

I went to "about:config" in Firefox and fixed it there.  Works like a charm!  Thanks!

---

