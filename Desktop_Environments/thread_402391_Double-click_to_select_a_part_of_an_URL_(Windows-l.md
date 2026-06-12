---
title: "Double-click to select a part of an URL (Windows-like behavior)"
date: 2007-04-05
forum: Desktop Environments
---

### Post by kag on 2007-04-05
I'm not sure if this is a Firefox setting or a Gnome setting, but for example let's say the address of the page loaded in Firefox is [http://www.example.com/directory/file.html](http://www.example.com/directory/file.html). 

In Windows, double-clicking the "directory" word in the address bar would only hightlight that word. In Ubuntu, it selects the whole address. Is there a way to change this?

---

### Post by kevmartin on 2007-04-05
Yes, I'm curious about this too as it's something that bugs me a bit (same thing also happens whenever I have to use IE for various reasons, as it too selects the whole URL).  It's for a long time been a favourite feature of Firefox for me, so was disappointed to find it missing in Linux FF when I recently started the switch.

There seem to be little inconsistencies like this between Linux and Windows versions of Firefox.  Another is whether links open in new tabs etc, when the link is predefined to open in a new window.  I like all links of this type to open in new tabs, not in new windows.  Without this I'd frequently end up with 50+ separate windows. I'd rather open a new window for each major task I'm doing (with a right-click, open in new window), and have tabs within it for the various windows I need related to it.  The switch from Firefox 1.5 ro 2.x helped this in some ways, but there are differences between the Windows and Linux versions (unfortunately I'm stuck with dual boot and spending half of my time in each roughly right now).

---

### Post by kag on 2007-04-11
No one?

---

### Post by awells527 on 2007-04-12
I just got used to selecting the text by dragging the mouse.

> Another is whether links open in new tabs etc, when the link is predefined to open in a new window. I like all links of this type to open in new tabs, not in new windows....

You look like you need [this extension]("https://addons.mozilla.org/en-US/firefox/addon/158")

---

### Post by kevmartin on 2007-04-12
> **awells527 said:**
> I just got used to selecting the text by dragging the mouse.



You look like you need [this extension]("https://addons.mozilla.org/en-US/firefox/addon/158")

Thanks I'll check it out :)

---

### Post by kag on 2007-07-13
Any fresh ideas?

---

### Post by kevmartin on 2007-07-14
Nope - I gave up and am still getting used to it.  I tried the recommended extension and it was no help to me either unfortunately.

---

### Post by kag on 2007-07-17
In Dapper Drake, I did not have the new window problem. Since I installed Feisty, I've been getting this also. Kind of annoying.

---

### Post by kag on 2007-10-27
I'm bumping my old thread, I still haven't found a way to do this.

---

### Post by prowlett on 2007-12-08
This has been annoying me for a while and I've just done a clean install on this machine so thought I would have another look for a solution while my files copied over. Both for a double-click selecting only the URL part but also I tend to Alt-D or Ctrl-L to get into the address bar then Ctrl-cursor through the URL to get to the bit I want to edit or Ctrl-backspace to remove bits from the end of the URL. Firefox in Ubuntu (and IE in Windows, but not Firefox in Windows!) causes these to select (or jump, or delete) the whole URL not just part. The following fixes all this.

Thanks to this page: [http://ramikayyali.com/archives/2006/02/19/fffixes](http://ramikayyali.com/archives/2006/02/19/fffixes) I have discovered that in about:config (type about:config into the address bar), setting layout.word_select.stop_at_punctuation to true means the URL parts are considered separately.

---

### Post by Percolator on 2008-01-03
"layout.word_select.stop_at_punctuation" Was just what I was looking for.... for quite a while actually. FF felt like IE but now no more. Thanks!

---

### Post by kag on 2008-02-29
Wow thanks!!! Exactly what I was looking for!!!

---

