---
title: "How to fully modify fonts in OS and applications"
date: 2012-08-02
forum: Desktop Environments
---

### Post by gipsyshadow on 2012-08-02
Hi all,

I am a newbie to linux and this is my first post in this forum, so I hope you'll forgive me for my ignorance...and my very bad english too :D
I've installed Lubuntu 12.04 on an old acer notebook with 1.6GHz intel processor, 512MB ram, intel chipset and graphical board integrated.

Well, switching from windows to this desktop I've noticed system fonts were very blurry because of the anti-aliasing. So I went to Preferences -> Customise feel and look -> Font and I disabled antialias and chose full option for hinting, getting a nice result for me. The problem is that the web pages opened in Chromium web browser remained with antialias fonts, while the fonts in tabs, url, bookmarks had been corrected with my new OS preferences!

I've googled a little bit and I discovered this is a shared problem for linux users. In particular I've found these interesting discussions:
- [Ugly font rendering on linux]("http://code.google.com/p/chromium/issues/detail?id=13185")
- [font rendering (hingint? anti-aliasing?) problem on linux]("http://code.google.com/p/chromium/issues/detail?id=70262#c2")
where the last posts in the 1st one redirect to a probable troubleshooting found in the 2nd one, but they talk about Debian and Fedora, so I'd want to ask to experts if that workaround could be run in Lubuntu too and, if yes, how to do it for a very newbie.
There's only one diffecence beetwen my problem and their: it happens to me for firefox too while they say firefox fonts are ok.

Can you please help me?

Thank you :)

---

### Post by gipsyshadow on 2012-08-11
Hi, just wanted to inform that workaround ran perfectly :)

Just open (with leafpad or gedit) */home/[name]/.fonts.conf* file and edit these 2 words:

```
<edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
```
-> change hintslight to **hintfull**

```
<edit mode="assign" name="antialias" >
   <bool>true</bool>
```
-> change true to **false**

Note that the 2nd one is the fundamental change.

Now I can see non-anti-aliased font in Firefox. I've uninstalled chromium but I guess it's the same for it too.

Hope this help, :guitar:

---

