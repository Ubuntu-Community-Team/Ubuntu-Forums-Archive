---
title: "need gui text editor with syntax highlighting"
date: 2008-12-27
forum: General Help
---

### Post by oubaas on 2008-12-27
Hello folks,
I've spent most of the last two days looking for a text editor that I can use to edit industrial robot programs. In windows I've used UltraEdit or Notepad++, and can't seem to find what I'm looking for. I've now some time to break away from windows completely but I'm getting nowhere fast.:(
I don't need a compiler, the robots do that for me after I've send code over with FTP.

Have looked at Scite,Bluefish,Vim,LeafPad, Scribes, Gedit, Jedit etc. Need something that I can add syntax highlighting to without spending a week doing it, and without having to hack one of the existing builtin languages.

Something that can open more than one file in tabs like Gedit would be nice too, and have a tree/project view on the side.

My install started life as Xubuntu 8.04 but by now I've bits of everything except KDE. I would REALLY love to be able to boot out windows.

Anybody else out there done this?
Thanks

---

### Post by RHTopics on 2008-12-27
I have you looked at Geany?  I believe it may fit your requirements.

Link to their FAQs:

[http://www.geany.org/Documentation/FAQ#QQuestions5](http://www.geany.org/Documentation/FAQ#QQuestions5)

---

### Post by Dr Small on 2008-12-27
Medit supports syntax highlighting and tabs. I have it installed, but rarely use it since I mostly use vim.

---

### Post by sedawk on 2008-12-27
You can check at [www.winehq.com's](www.winehq.com's) Application Database
if you can run your favorite version of UltraEdit with Wine,
so you can use your "old" editor with linux.

Have you thought about using an IDE like Eclipse?
They come with editors that can do syntax highlighting too.

---

### Post by jerome1232 on 2008-12-27
--edit--

funny I replied to the wrong thread but kind of the same subject yet I see you've already rejected my suggestions so I'm taking them away.

---

### Post by todak on 2008-12-28
Install **kate** from the repositories. It will do everything you need.

---

### Post by binbash on 2008-12-28
gedit also does that however you may need a plugin

---

### Post by c1rcu17 on 2008-12-28
try out gvim. its in the repositories.

---

### Post by Sorivenul on 2008-12-28
+1 for Geany. It does everything I want it to and more, all with a simple interface, and has an impressive array of languages with syntax highlighting built in. It takes the cake as far as all-around ease goes, IMO. The syntax highlighting feature in Vi(m) is easy to turn on, just search the forums.

The languages you use most would be of help, as specific editors may also work best for specific languages: Code::Blocks or Anjuta for C/C++, SPE or Eric4 for Python, Eclipse or NetBeans for Java.

For more specific needs, you may want to check out the Programming Talk subforum, and read the Sticky threads there.

---

### Post by kerry_s on 2008-12-28
never mine, i missed the tabs and side tree part.

---

### Post by hyper_ch on 2008-12-28
kate
emacs
vim
vi

---

### Post by oubaas on 2008-12-31
Thanks to all for the input,
and to clarify this better, my question should have been for a text editor to which I can ***easily add a language definition***.
(For the benefit of anyone else with the same problem)

Have spoken to IDM and was informed that they are porting UltraEdit to Linux, beta testing to begin in early 2009.

Kate presently appears to be the bet bet, but I've yet to get it to use the .xml file that I've written and highlight the new syntax.
Will keep plugging away. The docs I find seem to be more of a reminder for someone who knows how to do it than for someone starting from scratch.

---

### Post by hyper_ch on 2008-12-31
you also maight want to have a a look at jEdit. I discovered that one the other day as I needed a free editor on Windows that support sftp and other stuff. By default it has not many features but there's a plethora of plugins.

Buffered tabs and ftp are "my most important" ones that I used. However I did not have a look at the linux version of it yet.

It's in the repos and plugins can be, at least on windows, directly from within of jedit be downloaded.

---

