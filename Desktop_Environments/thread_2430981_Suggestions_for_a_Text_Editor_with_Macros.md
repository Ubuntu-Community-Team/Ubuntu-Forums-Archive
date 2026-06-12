---
title: "Suggestions for a Text Editor with Macros"
date: 2019-11-10
forum: Desktop Environments
---

### Post by snappa09 on 2019-11-10
For my first Linux experience, I have just loaded Ubuntu onto an old (2012) desktop, and am trying to find apps which will work the way I work.  

Right now, I am looking for a text editor or 'Notes' application, perhaps with some minimal formatting, but most importantly, with macro or scripting which will allow me to move to the end of the file, insert a new line, insert a row of delineation characters, insert a new line, then insert a datestamp or timestamp.  This/these 'macro' would be assigned to a couple of Function keys.  (On Windows, I used a Word file, with macros for the date and timestamp insertions, but it became slow, and the file very large.)  This application should allow multiple open files, with the files in tabs across across the top (or bottom) of the page.  With these multiple files, I will have a pseudo text based organiser, or personal information manager. 

As I am new to Linux, I don't really know what apps are out there.  I have searched but haven't found anything which looks suitable.  The capabilities of many of these applications are not very well explained.

Any suggestions for this 'Editor' or 'Notes' application ?
Thanks.

---

### Post by TheFu on 2019-11-10
There's only 1 editor for any computer system.  vim.  It can do anything you can imagine - except have a menu/GUI.  There are hundreds of thousands of pre-created macros which can be merged into the running environment based on which directory the program runs from.

Using vim does require a completely different way of thinking and you won't be productive using it for weeks.  OTOH, once you learn how it works, you'll never want to use any other editor.

Vim is cross platform. It is available for pretty much any computer.  Every router I've ever touched had a copy of vim installed - and usually no other editor.  This means that vim isn't just handy, it is required knowledge, unless you plan to be an end-user forever.

Lacking the commitment to learn vim for the next 5 yrs (yes, it is THAT capable), something like **geany** or **Atom** are more like traditional Notepad++ editors.

If you want a PIM, there are lots and lots of options.  A local wiki, **gnote**, **BasKet-Notepads** [https://basket-notepads.github.io/screenshots.html](https://basket-notepads.github.io/screenshots.html) , **Zim**, or just use a Markdown editor. Vim has a markdown mode, but so do many editors like geany or atom. [https://alternativeto.net/software/basket/](https://alternativeto.net/software/basket/) has some alternatives.

For GUI stuff, I find that getting a quick overview is easy by viewing a few youtube videos or checking out some screen shots.

BTW, most people avoid learning vim for 6 months to a few years, but eventually come back around and pick it up.  When I was new to Unix, I started with emacs.  Took about 6 months to realize that I kept switching emacs into vi-mode to get anything done.  ;)

Work through the **vimtutor** application for a gentle introduction.  Then sleep on it before deciding.

---

### Post by snappa09 on 2019-11-21
Thanks for your advice Fu.  At the moment I am trialing Zim, which is a graphical text editor.  I'm still learning, so it would be unfair for me to criticise it.  I'll keep your advice in my system.  Thanks again.

---

### Post by uRock on 2019-11-21
Bluefish editor is a good one to try. I use nano for the command line.

---

### Post by jetsam on 2019-11-21
There is only vim.

Vim, and the unfortunate vimless masses.

---

### Post by uRock on 2019-11-21
> **jetsam said:**
> There is only vim.

Vim, and the unfortunate vimless masses.
It's so good they stopped installing it by default.

---

### Post by jetsam on 2019-11-21
Who did, Canonical?  That's just rude...

---

### Post by uRock on 2019-11-21
> **jetsam said:**
> Who did, Canonical?  That's just rude...

It's dated, they say. Every training vid I've seen for the past couple of years has recommended Nano for CLI.

---

### Post by jetsam on 2019-11-21
It's not dated.  Nano?  Nano is fine, if you are a noob.

Vim is industry standard.  Silly corporate decision.

Edit: Manjaro, Ubuntu, Sabayon, OH MY! Manjaro, Ubuntu, Sabayon, OH MY! (to the tune of Lions and Tigers and Bears from T.W.O.OZ.)

---

### Post by uRock on 2019-11-21
Nano is fine for those who don't want to spend the time learning how to VIM. I've used it years ago. I just like Nano more. I personally know it isn't outdated, because TheFu uses it and he wouldn't be using it if it were outdated. We're getting off topic.

---

### Post by jetsam on 2019-11-21
There's no outdated...
I used wordpad again yesterday to format some javascript I copied from Bashing-om's link.

> We're getting off topic.

Correct.  We should be talking about vim.

---

### Post by SeijiSensei on 2019-11-21
I started off with Emacs decades ago and now use [jed]("https://www.jedsoft.org/jed/"), a lightweight editor that defaults to an Emacs-like interface. jed supports both keystroke macros and, for more complicated tasks, ones written in its macro language, [S-lang]("https://www.jedsoft.org/slang/doc/html/slang.html").  Here are some examples: [https://docs.huihoo.com/homepage/dkuhlman/jed_macros.html](https://docs.huihoo.com/homepage/dkuhlman/jed_macros.html)

Like vim and nano, jed is a text-mode editor. It uses control and escape key sequences where you hold down the Ctrl or Esc key and type a letter. However it also has a menu that you can activate by pressing F10.  Recording and playing back keystroke macros is available from F10 > Edit > Key Macros.

jed is in the Ubuntu repositories.

---

### Post by TheFu on 2019-11-21
Picking an editor is a very personal thing.   If you want to start a holy war in any computing forums, just ask "what editor should I use." Part of the Unix culture and has been since the 1980s.  Would you walk into a pub in Manchester and say that M-United sucks? That's how Unix people feel about their editor choice.

I have only one use for nano, gedit, kate, xedit, pico.  
```
sudo apt purge nano gedit kate xedit pico
``` 

;)

**Find what works for you, ignore everyone else.**

---

### Post by uRock on 2019-11-21
> **TheFu said:**
> Picking an editor is a very personal thing. ......<snip>.......
Find what works for you, ignore everyone else.
Yup. I use different editors depending on what I'm working on.

---

### Post by SeijiSensei on 2019-11-21
How about we answer the OP's question rather than engage in a discussion of editors?  As I said, I use jed and know it supports macros.  I don't think nano does. I rarely use kate, but a quick look suggests it doesn't support macros either.

---

### Post by uRock on 2019-11-21
> **SeijiSensei said:**
> How about we answer the OP's question rather than engage in a discussion of editors?  As I said, I use jed and know it supports macros.  I don't think nano does. I rarely use kate, but a quick look suggests it doesn't support macros either.

Because none of the documentation I am reading says that Nano and Bluefish do not offer support for Macros. When I do a search for text editors that support macros, those editors do come up in every article. If those two don't do macros, then I would use VIM.  It appears from post 3 that the OP has found what he/she wants for now.

---

### Post by 0x656b694d on 2019-11-27
I can imagine a use case where you'd create a script that would launch any text editor after appending the date and a delineation to the file with a simple echo command. I mean something like

```
#!/bin/sh
echo ============= >>$1
date >>$1
vim $1
```

For some simple formatting consider using markdown syntax.

Otherwise, LibreOffice Writer supports BASIC macros, like Word does.

---

### Post by catherinepark on 2019-11-29
[COLOR=#333333][FONT=&quot]There have been various problems with the editor for a bit now.  Although it's a good starting point editor, I try few editors and now I use a third party editor with Vivado.  I'm running Notepad++ on my Windows platform and it's integrated nicely with Vivado and offers more bells and whistles than the Vivado editor (macros, etc.) and for the most part is bug free.  Notepad++ will run on Ubuntu as well, my suggestion is to jump to a third party editor.  Good luck[/FONT][/COLOR]

---

### Post by The Cog on 2019-11-29
Zim is a graphical note-taking app - like a personal wiki. No macros that I remember.

---

### Post by TheFu on 2019-11-29
With xdotool, every program has a macro capability. ;)  

Heck, there are other programs that handle nearly infinite macros like AutoKey. There are probably 10 others, not counting automatic testing tools.  Staying native, means it is unlikely your favorite tool will become unsupported.

Part of the Unix philosophy is to build smaller tools that do 1 thing really well AND work with other tools.  This is very different from the Windows way of building stuff - which includes everything + the kitchen sink.

---

