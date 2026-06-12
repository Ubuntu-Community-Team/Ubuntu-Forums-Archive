---
title: "mplayer - codecs &amp; plugins"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Branta on 2006-08-09
I have installed maplayer.

[BHhow[/B] do I **install** the necessary **codecs** & **firefox plugins**?

--- Bob ---

---

### Post by etank on 2006-08-09
The instructions on this page should help. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by tcollogne on 2006-08-09
Or you can install automatix and do it the easy way.

You can install automatix using this guide:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by Branta on 2006-08-10
automatix installed fine as did mplayer and others but when I click on a *.wmv file I am told I **need** the **[COLOR="Red"]video codec MS wmv9 (win32)[/COLOR]**.

Using automatix I **installed** '**mplayer and FF plugin**' and '**Multimedia codecs**'

What should I do

--- Bob ---

---

### Post by abu_nawas on 2006-08-10
> **Branta said:**
> automatix installed fine as did mplayer and others but when I click on a *.wmv file I am told I **need** the **[COLOR="Red"]video codec MS wmv9 (win32)[/COLOR]**.

Using automatix I **installed** '**mplayer and FF plugin**' and '**Multimedia codecs**'

What should I do

--- Bob ---
get the essential codecs from the [mplayer page]("http://www.mplayerhq.hu/design7/dload.html") then extract it to /usr/lib/win32

---

### Post by Branta on 2006-08-11
I got the codecs from the [mplayer site]("http://www.mplayerhq.hu/design7/dload.html"), uncompressed and copied them to **/usr/local/lib/codecs** the default directory.

Now mplayer plays *.wmv files.

Thanks everyone.

--- Bob ---

---

