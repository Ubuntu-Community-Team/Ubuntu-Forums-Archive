---
title: "New forum layout breaks CODE tags."
date: 2013-04-04
forum: Forum Feedback &amp; Help
---

### Post by CatKiller on 2013-04-04
When browsing the forum on my phone, spaces are added between every letter on text inside CODE tags. It makes it very difficult to read. It behaved properly (aside from not being able to scroll) before the recent theme change.

---

### Post by VinDSL on 2013-04-10
'Code', in the new Ubu Forum threads, is a jumbled mess -- even on a desktop box!

Actually, 'code' looks fine, when previewing it in the editor, but...

The 'code' wraps to the next line (no horizontal scrolling) when submitted/viewed in the threads.

Here's a sample of how 'code' looks in the threads (improperly formatted, e.g text wrapping)...

```
##################################
##  RHYTHMBOX 2 (Experimental)  ##
##################################
${if_running rhythmbox}
${voffset -13}${font DroidSans:bold:size=8}${color4}RHYTHMBOX${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}}${font}${else}${alignc}${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}${font}${endif}${endif}

```

The 'code' sample (above) is virtually unreadable (on Chrome/Chromium) once it's submitted!  

I can only imagine how it looks on a phone.

Compare it to the post preview (properly formatted, e.g. no wrapping)...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-apr-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-apr-2013-2.png")[/INDENT]


Wrapping the 'code' in the threads (no horizontal scrolling) makes it practically unusable...  ;)

---

### Post by VinDSL on 2013-04-10
Test...

* All 3 tags wrap the code!  

Code Tags
```
##################################
##  RHYTHMBOX 2 (Experimental)  ##
##################################
${if_running rhythmbox}
${voffset -13}${font DroidSans:bold:size=8}${color4}RHYTHMBOX${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}}${font}${else}${alignc}${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}${font}${endif}${endif}
```

PHP Tags
[PHP]##################################
##  RHYTHMBOX 2 (Experimental)  ##
##################################
${if_running rhythmbox}
${voffset -13}${font DroidSans:bold:size=8}${color4}RHYTHMBOX${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}}${font}${else}${alignc}${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}${font}${endif}${endif}[/PHP]

HTML Tags
[HTML]##################################
##  RHYTHMBOX 2 (Experimental)  ##
##################################
${if_running rhythmbox}
${voffset -13}${font DroidSans:bold:size=8}${color4}RHYTHMBOX${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}}${font}${else}${alignc}${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}${font}${endif}${endif}[/HTML]

---

### Post by mc4man on 2013-04-11
Vin - firefox is fine, google-chrome/chromium 'mess' up the code boxes with long lines

---

### Post by CharlesA on 2013-04-11
The only one that wraps is the php code.. at least for me. FF 19.0.2 on Win7.

---

### Post by VinDSL on 2013-04-11
> **mc4man said:**
> Vin - firefox is fine, google-chrome/chromium 'mess' up the code boxes with long lines
> **CharlesA said:**
> The only one that wraps is the php code.. at least for me. FF 19.0.2 on Win7.
Yes, mc4man pointed this out in the +1 Forum.

I have four browsers installed in this box:
[LIST=1]
[*]Chromium Canary (Chrome dev-trunk)
[*]Chromium Stable
[*]Opera-Next
[*]Firefox
[/LIST]
Chromium et al. is the only browser having this display problem, but...

It only happens when viewing the resultant post, not when previewing the post in the editor.

If we were to lay blame entirely on buggy browser rendering, wouldn't it happen in both instances?

I'm *thinking* this is a bug in the new Ubu Forum theme.  Why?

If you go to the bottom of this page, and choose "Ubuntu Mobile Style", the 'code' displays correctly.  ;)

---

### Post by VinDSL on 2013-04-11
Okay, I think I figured it out.  :)

All I had to do is go into the .bbcode container (pre.bbcode_code element) and add normal word-wrap.

The .bbcode container is probably inheriting auto word-wrap from some other element, e.g. it's nested.

Here's how it looks with normal word-wrap (mouse pointer shows where I added it)...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-11-apr-2013-4(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-apr-2013-4.png")[/INDENT]

---

### Post by VinDSL on 2013-04-12
I drilled down a little more...

Evidently, the stylesheet responsible for this element, in the new theme, is 'additional.css'.

I judge, all you would have to do is add 'word-wrap:normal' into that stylesheet, and life would be good again.


[INDENT]additional.css (original)[/INDENT]
```
<SNIP>

.bbcode_container div.bbcode_code,.bbcode_container pre.bbcode_code{background-color:#EFEFEF;font-size:14px;overflow:auto}

<SNIP>
```

[INDENT]additional.css (patched)[/INDENT]
```
<SNIP>

.bbcode_container div.bbcode_code,.bbcode_container pre.bbcode_code{background-color:#EFEFEF;font-size:14px;overflow:auto**[COLOR="#0000CD"];word-wrap:normal[/COLOR]**}

<SNIP>
```

webpath:  [http://ubuntuforums.org/clientscript/vbulletin_css/style00117l/additional.css](http://ubuntuforums.org/clientscript/vbulletin_css/style00117l/additional.css)

BTW, is the staging forum still available?

I'd be glad to go over there and test the hack...  ;)

**EDIT**

~cool

Staging forum is still there...

I tested the [noparse]```
whatever
```[/noparse] tags in all of the standard themes, and Chromium didn't display properly with any of them -- even the default VB 4 theme.  However, the patch worked on all of the themes that I tested it against.

Hrm...

Maybe I should be complaining about this upsteam,  on the VB web site.  LoL!  :D

I wonder if they're aware they have a Chromium/Chrome problem...

---

### Post by sandyd on 2013-04-12
> **VinDSL said:**
> I drilled down a little more...

Evidently, the stylesheet responsible for this element, in the new theme, is 'additional.css'.

I judge, all you would have to do is add 'word-wrap:normal' into that stylesheet, and life would be good again.


[INDENT]additional.css (original)[/INDENT]
```
<SNIP>

.bbcode_container div.bbcode_code,.bbcode_container pre.bbcode_code{background-color:#EFEFEF;font-size:14px;overflow:auto}

<SNIP>
```

[INDENT]additional.css (patched)[/INDENT]
```
<SNIP>

.bbcode_container div.bbcode_code,.bbcode_container pre.bbcode_code{background-color:#EFEFEF;font-size:14px;overflow:auto**[COLOR="#0000CD"];word-wrap:normal[/COLOR]**}

<SNIP>
```

webpath:  [http://ubuntuforums.org/clientscript/vbulletin_css/style00117l/additional.css](http://ubuntuforums.org/clientscript/vbulletin_css/style00117l/additional.css)

BTW, is the staging forum still available?

I'd be glad to go over there and test the hack...  ;)

**EDIT**

~cool

Staging forum is still there...

I tested the [noparse]```
whatever
```[/noparse] tags in all of the standard themes, and Chromium didn't display properly with any of them -- even the default VB 4 theme.  However, the patch worked on all of the themes that I tested it against.

Hrm...

Maybe I should be complaining about this upsteam,  on the VB web site.  LoL!  :D

I wonder if they're aware they have a Chromium/Chrome problem...

if you use the "current2103" theme in staging does it still show up
thanks

---

### Post by VinDSL on 2013-04-12
> **sandyd said:**
> if you use the "current2103" theme in staging does it still show up
thanks
Works fine!

I would swear I checked that theme earlier :confused:

Anyway, yes, my test thread is displaying code correctly in Chromium.  ;)

---

### Post by sandyd on 2013-04-14
> **VinDSL said:**
> Works fine!

I would swear I checked that theme earlier :confused:

Anyway, yes, my test thread is displaying code correctly in Chromium.  ;)

I just added it so you didn't see it until now :)

---

### Post by VinDSL on 2013-04-14
> **sandyd said:**
> I just added it so you didn't see it until now :)
Heh!  You fooled_the_chimp.

Any plans to add it here, in the Live forums?!?!?

Kinda lonely, over in Staging...

**EDIT**

Oh, you're a sly one, aren't you?  Fooled_me_twice.  LoL!  :D

I just checked my post(s) on Page-1 and the [NOPARSE][CODE][/NOPARSE] tags are working now;  [NOPARSE][HTML][/NOPARSE] tags, too.

[NOPARSE][PHP][/NOPARSE] tags are still janky, but I don't publish webdev code here, anyway (don't think anybody does).

Thank you!

---

### Post by sandyd on 2013-04-14
> **VinDSL said:**
> Heh!  You fooled_the_chimp.

Any plans to add it here, in the Live forums?!?!?

Kinda lonely, over in Staging...

**EDIT**

Oh, you're a sly one, aren't you?  Fooled_me_twice.  LoL!  :D

I just checked my post(s) on Page-1 and the [NOPARSE][CODE][/NOPARSE] tags are working now;  [NOPARSE][HTML][/NOPARSE] tags, too.

[NOPARSE][PHP][/NOPARSE] tags are still janky, but I don't publish webdev code here, anyway (don't think anybody does).

Thank you!

glad to see that it works ;)

---

### Post by CatKiller on 2013-04-15
> **sandyd said:**
> glad to see that it works ;)

That doesn't really help me much.

---

### Post by VinDSL on 2013-04-15
> **CatKiller said:**
> That doesn't really help me much.
I've found it best to be proactive in these matters.

Are dev tools available for whatever browser you're using, on your phone?  Sometimes ,you can find them in the SDK.

Example:  [http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

I digress.  I stripped the fonts from this SDK, for use in my Conky script.  LoL!  :D

BTW, what phone are you using?  Which OS/version? Which browser, et cetera?

---

### Post by CatKiller on 2013-04-15
The browser is whatever comes with Gingerbread on a Galaxy S. While I'm aware that this is an older phone, there are an absurd number of Froyo and Gingerbread phones out there. And it was fine until the forums got broken.

No offence, but I'm not going to install an SDK to fix the CSS on someone else's site. I'll happily look at stuff but, as I've pointed out, I'm browsing on a phone. Some things are just a pain to do.

---

### Post by VinDSL on 2013-04-15
> **CatKiller said:**
> The browser is whatever comes with Gingerbread on a Galaxy S.
~cool

Well, that narrows it down.

Maybe somebody can go over to the Staging forum, and play around with the new theme.

Are you using the Ubu Mobile Theme (mobile), or the Ubu vB4.x Theme (standard)?

---

### Post by CatKiller on 2013-04-15
The normal theme. I didn't know there was a mobile theme till this thread since the site doesn't default to the mobile theme on mobile devices.

Code boxes work on the mobile theme, but it's fugly.

EDIT: work in the sense of the character spacing is OK. You only get two lines and you can't scroll them, but it's a start.

---

