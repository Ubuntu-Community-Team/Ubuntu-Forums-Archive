---
title: "Forum CSS problem"
date: 2009-05-10
forum: Forum Feedback &amp; Help
---

### Post by lovinglinux on 2009-05-10
Is there a problem with the forums css right now?

The forum is pretty weird here (see attachment).

---

### Post by bapoumba on 2009-05-11
Have you seen it past the time you posted?

---

### Post by lovinglinux on 2009-05-11
> **bapoumba said:**
> Have you seen it past the time you posted?

Yes. It was fixed just a minute or two later. I forgot about posting back here. Thanks.

---

### Post by bapoumba on 2009-05-11
> **lovinglinux said:**
> Yes. It was fixed just a minute or two later. I forgot about posting back here. Thanks.
Okay, no problem :)
Gremlins..

---

### Post by drubin on 2009-05-11
This error is not a "Gremlins" issue but rather the re-write rule on the server.

Any page that isn't valid on the forum returns the forum's index page ie the index.php site. this is fine for all files/urls with in the same folder. ie
ubuntuforums.org/adsfasdfasdfas.php would be valid since the vbulletin install location is still ubuntuforums.org/ and the css is located in ubuntuforums.org/css or the such.

Should your request url be something like ubuntuforums.org/abb/index.php it will look for the css in ubuntuforums.org/abb/css/ (and not find it).

This is a snippet of html from the ubuntuforums.org/abb/index.moo.something Since the paths are relative clientscript/vbulletin_css/ will point to the incorrect place.
[HTML]<!-- CSS Stylesheet -->
<style type="text/css" id="vbulletin_css">
/**
* vBulletin 3.8.1 CSS
* Style: 'CleanV2'; Style ID: 98
*/
@import url("clientscript/vbulletin_css/style-89ac7869-00098.css");
</style>[/HTML]

I don't expect this issue to be fixed. Since I am pretty sure major change to the vbulletion code base.

But if a simple redirect to the correct location(or just the home page) would be possible it would solve some of this issues. 

Or at the very least a "normal" blank error type [404]("http://en.wikipedia.org/wiki/HTTP_404") page :) 

Just my 2cents

---

